---
title: Utiliser DMARC pour valider les e-mails et les étapes de configuration
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/10/2021
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 4a05898c-b8e4-4eab-bd70-ee912e349737
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Découvrez comment configurer DMARC (Domain-based Message Authentication, Reporting, and Conformance) pour valider les messages envoyés à partir de votre organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 242c0e7573c9f5c61ba23b8a99ed27793ea58019
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60208948"
---
# <a name="use-dmarc-to-validate-email"></a>Utiliser DMARC pour valider les e-mails

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Domain-based Message Authentication, Reporting, and Conformance ([DMARC](https://dmarc.org)) utilise SPF (Sender Policy Framework) et DKIM (DomainKeys Identified Mail) pour authentifier les expéditeurs d'e-mails et faire en sorte que les systèmes de messagerie de destination acceptent les messages envoyés depuis votre domaine comme fiables. L'implémentation de DMARC avec SPF et DKIM fournit une protection supplémentaire contre l'usurpation et les courriers de hameçonnage. DMARC permet aux systèmes de messagerie de réception de déterminer ce qu'ils doivent faire des messages envoyés à partir de votre domaine qui sont rejetés par les contrôles de SPF ou de DKIM.

> [!TIP]
> Visitez le catalogue [Association de sécurité intelligente de Microsoft (MISA)](https://www.microsoft.com/misapartnercatalog) pour afficher les fournisseurs tiers proposant des rapports DMARC pour Microsoft 365.

## <a name="how-do-spf-and-dmarc-work-together-to-protect-email-in-microsoft-365"></a>Comment SPF et DMARC fonctionnent-ils ensemble pour protéger les messages électroniques dans Microsoft 365 ?

 Un message électronique peut contenir plusieurs adresses d’origine (ou d’expéditeur). Ces adresses sont utilisées à des fins différentes. Par exemple, prenez les adresses suivantes :

- **Adresse « Mail From » :** indique l'expéditeur et l'emplacement où envoyer les notifications de retour en cas de problèmes avec la remise du message, telles que les notifications d'échec de remise. Elle apparaît dans la partie d'enveloppe d'un e-mail et n'est généralement pas affichée par l'application de messagerie. Elle est parfois appelée adresse 5321.MailFrom ou adresse de chemin inverse.

- **Adresse « From » :** adresse affichée comme adresse d'expédition par votre application de messagerie. Elle indique l'auteur de l'e-mail, à savoir la boîte aux lettres de la personne ou le système responsable de la rédaction du message. Elle est parfois appelée adresse 5322.From.

SPF utilise un enregistrement TXT DNS pour fournir la liste des adresses IP d'envoi autorisées pour un domaine donné. En règle générale, les vérifications SPF sont uniquement effectuées pour l'adresse 5321.MailFrom. Cela signifie que l'adresse 5322.From n'est pas authentifiée lorsque vous utilisez uniquement SPF. Vous pouvez ainsi vous retrouver dans le cas de figure où un utilisateur reçoit un message qui a été accepté par la vérification SPF mais possède une adresse d'expéditeur 5322.From usurpée. Prenez par exemple, la transcription SMTP suivante :

```console
S: Helo woodgrovebank.com
S: Mail from: phish@phishing.contoso.com
S: Rcpt to: astobes@tailspintoys.com
S: data
S: To: "Andrew Stobes" <astobes@tailspintoys.com>
S: From: "Woodgrove Bank Security" <security@woodgrovebank.com>
S: Subject: Woodgrove Bank - Action required
S:
S: Greetings User,
S:
S: We need to verify your banking details.
S: Please click the following link to verify that we have the right information for your account.
S:
S: https://short.url/woodgrovebank/updateaccount/12-121.aspx
S:
S: Thank you,
S: Woodgrove Bank
S: .
```

Dans cette transcription, les adresses de l’expéditeur sont les suivantes :

- Adresse « Mail from » (5321.MailFrom) : phish@phishing.contoso.com

- Adresse From (5322.From) : security@woodgrovebank.com

Si vous avez configuré SPF, le serveur de réception effectue une vérification sur l’adresse Mail from phish@phishing.contoso.com. Si l’e-mail provenait d’une source valide pour le domaine phishing.contoso.com, le contrôle SPF accepte le message. Étant donné que le client de messagerie affiche uniquement l’adresse From, l’utilisateur voit que ce message provenait de security@woodgrovebank.com. Avec SPF seul, la validité de l’adresse woodgrovebank.com n’a jamais été authentifiée.

Lorsque vous utilisez DMARC, le serveur de réception effectue aussi une vérification sur l’adresse From. Dans l’exemple ci-dessus, s’il existe un enregistrement TXT DMARC pour woodgrovebank.com, la vérification de l’adresse de provenance rejette celle-ci.

## <a name="what-is-a-dmarc-txt-record"></a>Qu’est-ce qu’un enregistrement TXT DMARC ?

À l'instar des enregistrements DNS pour SPF, l'enregistrement pour DMARC est un enregistrement DNS au format texte (TXT) qui empêche l'usurpation d'identité et le hameçonnage. Vous publiez les enregistrements TXT DMARC dans le système DNS. Les enregistrements TXT DMARC valident l'origine des messages électroniques en comparant l'adresse IP de l'auteur de l'e-mail à celle du prétendu propriétaire du domaine d'expédition. L'enregistrement TXT DMARC identifie les serveurs de messagerie sortants autorisés. Les systèmes de messagerie électronique de destination peuvent alors vérifier si les messages reçus proviennent de serveurs de messagerie sortants autorisés.

Un enregistrement TXT DMARC de Microsoft se présente comme suit :

```console
_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.agari.com; ruf=mailto:d@ruf.agari.com; fo=1"
```

Microsoft envoie ses rapports DMARC à [Agari](https://agari.com), un système tiers. Agari collecte et analyse les rapports DMARC. Visitez le catalogue [Association de sécurité intelligente de Microsoft (MISA)](https://www.microsoft.com/misapartnercatalog) pour afficher les fournisseurs tiers proposant des rapports DMARC pour Microsoft 365.

## <a name="set-up-dmarc-for-inbound-mail"></a>Configurer DMARC pour les messages entrants

Vous n’avez rien à faire pour configurer DMARC pour les messages que vous recevez dans Microsoft 365. Nous nous sommes occupés de tout. Si vous voulez découvrir ce qui se passe pour le courrier électronique rejeté par nos vérifications DMARC, reportez-vous à la section [Gestion des messages électroniques entrants qui échouent aux vérifications de DMARC dans Microsoft 365](#how-microsoft-365-handles-inbound-email-that-fails-dmarc).

## <a name="set-up-dmarc-for-outbound-mail-from-microsoft-365"></a>Configurer DMARC pour les messages sortants de Microsoft 365

Si vous utilisez Microsoft 365, mais pas un domaine personnalisé, c'est-à-dire que vous utilisez onmicrosoft.com, il vous suffit de configurer ou de mettre en œuvre DMARC pour votre organisation. SPF est déjà configuré pour vous et Microsoft 365 génère automatiquement une signature DKIM pour vos messages sortants. Pour plus d'informations sur cette signature, voir [Comportement par défaut pour DKIM et Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

 Si vous avez un domaine personnalisé ou utilisez des serveurs Exchange locaux en plus de Microsoft 365, vous devez implémenter manuellement DMARC pour vos messages sortants. La mise en œuvre de DMARC pour votre domaine personnalisé comporte les étapes suivantes :

- [Étape 1 : déterminer les sources de messagerie valides pour votre domaine](#step-1-identify-valid-sources-of-mail-for-your-domain)

- [Étape 2 : configurer SPF pour votre domaine](#step-2-set-up-spf-for-your-domain)

- [Étape 3 : configurer DKIM pour votre domaine personnalisé](#step-3-set-up-dkim-for-your-custom-domain)

- [Étape 4 : créer l’enregistrement TXT DMARC pour votre domaine](#step-4-form-the-dmarc-txt-record-for-your-domain)

### <a name="step-1-identify-valid-sources-of-mail-for-your-domain"></a>Étape 1 : déterminer les sources de messagerie valides pour votre domaine

Si vous avez déjà configuré SPF, vous connaissez déjà la procédure. Toutefois, il existe des considérations supplémentaires pour DMARC. Lorsque vous déterminez les sources de messagerie pour votre domaine, il existe deux questions auxquelles vous devez répondre :

- Quelles adresses IP envoient des messages à partir de mon domaine ?

- Pour les messages envoyés par des tiers de ma part, les domaines 5321.MailFrom et 5322.From correspondront-ils ?

### <a name="step-2-set-up-spf-for-your-domain"></a>Étape 2 : configurer SPF pour votre domaine

Maintenant que vous avez une liste de tous vos expéditeurs valides, vous pouvez suivre les étapes pour [configurer SPF pour empêcher l’usurpation d'](set-up-spf-in-office-365-to-help-prevent-spoofing.md).

Par exemple, en supposant que contoso.com envoie du courrier depuis Exchange Online, un serveur Exchange local dont l'adresse IP est 192.168.0.1 et une application web dont l'adresse IP est 192.168.100.100, l'enregistrement TXT SPF ressemblerait à ceci :

```console
contoso.com  IN  TXT  " v=spf1 ip4:192.168.0.1 ip4:192.168.100.100 include:spf.protection.outlook.com -all"
```

Pour obtenir les meilleurs résultats, vérifiez que votre enregistrement TXT SPF tienne compte des expéditeurs tiers.

### <a name="step-3-set-up-dkim-for-your-custom-domain"></a>Étape 3 : configurer DKIM pour votre domaine personnalisé

Une fois que vous avez configuré SPF, vous devez configurer DKIM. DKIM vous permet d'ajouter une signature numérique aux messages électroniques dans l'en-tête du message. Si vous ne configurez pas DKIM et que vous autorisez Microsoft 365 à utiliser la configuration par défaut pour votre domaine à la place, DMARC risque de rejeter les messages. En effet, la configuration par défaut de DKIM utilise votre domaine onmicrosoft.com en tant qu'adresse 5322.From, et non votre domaine personnalisé. Cela crée de fait une différence entre les adresses 5321.MailFrom et 5322.From dans tous les messages envoyés à partir de votre domaine.

Si des expéditeurs tiers envoient des messages en votre nom et que les adresses 5321.MailFrom et 5322.From de ces messages ne correspondent pas, DMARC rejettera ce message électronique. Pour éviter ce problème, vous devez configurer DKIM en définissant spécifiquement cet expéditeur tiers pour votre domaine. Cela permet à Microsoft 365 d'authentifier les messages envoyés par ce service tiers. Toutefois, cela autorise également d'autres entités, par exemple, Yahoo, Gmail et Comcast, à vérifier le courrier électronique qui leur est envoyé par le tiers comme s'il s'agissait de messages envoyés par vous-même. C'est un avantage, car, d'un côté, cela renforce la confiance que les clients peuvent avoir en votre domaine, quel que soit l'endroit où se trouvent leurs boîtes aux lettres et, de l'autre, Microsoft 365 ne marquera pas un message comme spam pour cause d'usurpation d'identité, car cet e-mail aura été accepté par les vérifications d'authentification pour votre domaine.

Pour obtenir des instructions sur la configuration de DKIM pour votre domaine, y compris sur la façon de configurer DKIM pour les expéditeurs tiers pour leur permettre d'usurper votre domaine, consultez [Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé](use-dkim-to-validate-outbound-email.md).

### <a name="step-4-form-the-dmarc-txt-record-for-your-domain"></a>Étape 4 : créer l’enregistrement TXT DMARC pour votre domaine

Bien qu’il existe des options de syntaxe qui ne sont pas mentionnées ici, voici les options les plus fréquemment utilisées pour Microsoft 365. Créez l’enregistrement TXT DMARC pour votre domaine au format suivant :

```console
_dmarc.domain  TTL  IN  TXT  "v=DMARC1; p=policy; pct=100"
```

où :

- *domain* est le domaine que vous souhaitez protéger. Par défaut, l’enregistrement protège le courrier issu du domaine et de tous ses sous-domaines. Par exemple, si vous spécifiez \_dmarc.contoso.com, DMARC protège le courrier issu de ce domaine et tous ses sous-domaines, par exemple housewares.contoso.com ou plumbing.contoso.com.

- La valeur *TTL* doit toujours être équivalente à une heure. L’unité utilisée pour TTL, que ce soit les heures (1 heure), les minutes (60 minutes) ou les secondes (3 600 secondes), varie selon le bureau d’enregistrement de votre domaine.

- *pct=100* indique que cette règle doit être utilisée pour 100 % des e-mails.

- *policy* indique la stratégie que vous souhaitez que le serveur de réception suive si un message est rejeté par DMARC. Vous pouvez définir la stratégie sur none (Aucune), quarantine (Mettre en quarantaine) ou reject (Rejeter).

Pour plus d'informations sur les options à utiliser, familiarisez-vous avec les concepts de la section [Meilleures pratiques pour la mise en œuvre de DMARC dans Microsoft 365](#best-practices-for-implementing-dmarc-in-microsoft-365).

Exemples :

- Stratégie définie sur none (Aucune)

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=none"
    ```

- Stratégie définie sur quarantine (Mettre en quarantaine)

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=quarantine"
    ```

- Stratégie définie sur reject (Rejeter)

    ```console
    _dmarc.contoso.com  3600 IN  TXT  "v=DMARC1; p=reject"
    ```

Une fois que vous avez créé votre enregistrement, vous devez le mettre à jour auprès de votre bureau d’enregistrement de domaine.

## <a name="dmarc-mail-public-preview-feature"></a>Courrier DMARC (fonctionnalité d'évaluation publique)
> [!CAUTION]
> Les courriers ne sont pas nécessairement envoyés quotidiennement, et le rapport lui-même peut changer pendant la préversion publique.  Les courriels du rapport global DMARC peuvent être attendus des comptes des consommateurs (tels que les comptes hotmail.com, outlook.com ou live.com).

Dans cet exemple, l’enregistrement TXT DMARC **_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.agari.com; ruf=mailto:d@ruf.agari.com; fo=1"** vous pouvez voir l’adresse *rua*, dans ce cas, traitée par l’entreprise tierce Ari. Cette adresse permet d’envoyer des « commentaires agrégés » aux besoins d’analyse et de générer un rapport.

> [!TIP]
> Visitez le catalogue [Association de sécurité intelligente de Microsoft (MISA)](https://www.microsoft.com/misapartnercatalog) pour afficher les fournisseurs tiers proposant des rapports DMARC pour Microsoft 365. Pour plus d’informations sur les adresses DMARC « rua », voir [ « Authentification de message, rapports et conformité basée sur un domaine » de l’organisation IETF](https://datatracker.ietf.org/doc/html/rfc7489).

## <a name="best-practices-for-implementing-dmarc-in-microsoft-365"></a>Meilleures pratiques pour la mise en œuvre de DMARC dans Microsoft 365

Vous pouvez implémenter DMARC progressivement sans que cela n’ait de répercussions sur le reste de votre flux de messagerie. Créez et mettez en œuvre un plan de déploiement qui suit la procédure ci-dessous. Effectuez d’abord chaque étape avec un sous-domaine, puis avec d’autres, et enfin avec le domaine de niveau supérieur de votre organisation avant de passer à l’étape suivante.

1. Contrôlez les effets de l’implémentation DMARC

    Commencez avec un simple enregistrement en mode surveillance pour un sous-domaine ou un domaine qui requiert que les récepteurs DMARC vous envoient des statistiques sur les messages qu'ils voient pour ce domaine. Un enregistrement en mode surveillance est un enregistrement TXT DMARC dont la stratégie est définie sur Aucune (p=none). De nombreuses sociétés publient un enregistrement TXT DMARC avec p=none, car elles ne savent pas exactement la quantité de messages qu'elles risquent de perdre en publiant une stratégie DMARC plus restrictive.

    Vous pouvez effectuer cette opération avant même d'avoir mis en œuvre SPF ou DKIM dans votre infrastructure de messagerie. Toutefois, vous ne pourrez pas mettre en quarantaine ou refuser des messages à l'aide de DMARC jusqu'à ce que vous implémentiez également SPF et DKIM. Lorsque vous mettrez en place SPF et DKIM, les rapports générés via DMARC fourniront le nombre et la source des messages qui sont acceptés par ces contrôles, ainsi que de ceux qui sont refusés. Vous pouvez facilement déterminer la part de votre trafic légitime qui est ou non couverte par ces catégories et résoudre les problèmes. Vous commencerez aussi à voir le nombre de messages frauduleux envoyés, ainsi que leur source.

2. Demandez que les systèmes de messagerie externes mettent en quarantaine le courrier qui échoue aux vérifications de DMARC

    Lorsque vous pensez que tout ou partie de votre trafic légitime est protégé par SPF et DKIM, et que vous connaissez les répercussions de l'implémentation de DMARC, vous pouvez implémenter une stratégie de mise en quarantaine. Une stratégie de mise en quarantaine est un enregistrement TXT DMARC dont la stratégie est définie de manière à effectuer une mise en quarantaine (p=quarantine). Ce faisant, vous demandez aux récepteurs DMARC de placer les messages issus de votre domaine qui sont refusés par DMARC dans l'équivalent local d'un dossier de courrier indésirable plutôt que dans la boîte de réception de vos clients.

3. Demandez que les systèmes de messagerie externes n’acceptent pas les messages qui échouent aux vérifications de DMARC

    L'étape finale consiste à mettre en œuvre une stratégie de rejet. Une stratégie de rejet est un enregistrement TXT DMARC dont la stratégie est définie de manière à effectuer un rejet (p=reject). Lorsque vous effectuez cette opération, vous demandez aux récepteurs DMARC ne pas accepter les messages qui échouent aux tests DMARC.

4. Comment configurer DMARC pour le sous-domaine ?

   DMARC est exécuté en publiant une stratégie sous la forme d’un enregistrement TXT dans DNS et est hiérarchique (par exemple, une stratégie publiée pour contoso.com s’appliquera au sous-domaine.contonos.com, sauf si une stratégie différente est définie de manière explicite pour le sous-domaine). Cela est utile car les organisations peuvent spécifier un plus petit nombre d’enregistrements DMARC de haut niveau pour une couverture plus large. Veillez à configurer avec attention les enregistrements DMARC de sous-domaines explicites où vous ne voulez pas que les sous-domaines héritent de l’enregistrement DMARC du domaine de niveau supérieur.

   En outre, vous pouvez ajouter une stratégie de type caractère générique pour DMARC lorsque les sous-domaines ne doivent pas envoyer de message électronique, en ajoutant la valeur `sp=reject`. Par exemple :

   ```text
   _dmarc.contoso.com. TXT "v=DMARC1; p=reject; sp=reject; ruf=mailto:authfail@contoso.com; rua=mailto:aggrep@contoso.com"
   ```

## <a name="how-microsoft-365-handles-outbound-email-that-fails-dmarc"></a>Gestion des messages électroniques sortants qui échouent aux vérifications de DMARC dans Microsoft 365

Si un message sortant issu de Microsoft 365 échoue aux vérifications de DMARC et que vous avez défini la stratégie sur p=quarantine (mise en quarantaine) ou p=reject (rejet), le message est routé via le [pool de remise à risque plus élevé pour les messages sortants](high-risk-delivery-pool-for-outbound-messages.md).

Si vous publiez une stratégie de rejet DMARC (p=reject), aucun autre client dans Microsoft 365 ne peut usurper votre domaine, car les messages ne seront pas en mesure de passer les vérifications SPF ou DKIM pour votre domaine lorsqu'un message sortant sera relayé via le service. En revanche, si vous publiez une stratégie de rejet DMARC mais que tous vos messages électroniques ne sont pas authentifiés via Microsoft 365, une partie de ceux-ci peuvent être marqués comme courrier indésirable pour les e-mails entrants (comme décrit ci-dessus), ou ils seront refusés si vous ne publiez pas SPF et que vous essayez de les relayer dans le sens sortant via le service. Cela peut se produire, par exemple, si vous avez oublié d'inclure les adresses IP de certains serveurs et de certaines applications qui envoient des messages au nom de votre domaine lorsque vous avez créé votre enregistrement TXT DMARC.

## <a name="how-microsoft-365-handles-inbound-email-that-fails-dmarc"></a>Gestion des messages électroniques entrants qui échouent aux vérifications de DMARC dans Microsoft 365

Si la politique de DMARC du serveur d'envoi est `p=reject`, [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) marque le message comme étant un spoof au lieu de le rejeter. En d’autres termes, pour les messages entrants, Microsoft 365 traite `p=reject` et `p=quarantine` de la même façon. Les administrateurs peuvent définir l’action à effectuer sur les messages classés comme usurpation d’identité dans la stratégie [anti-hameçonnage](set-up-anti-phishing-policies.md).

Microsoft 365 est configuré de cette façon, car certains messages légitimes peuvent échouer aux vérifications de DMARC. Cela peut être le cas, par exemple, si un message est envoyé à une liste de diffusion qui le relaie ensuite à tous ses participants. Si Microsoft 365 rejette ces e-mails, les destinataires peuvent perdre des messages légitimes sans avoir aucun moyen de les récupérer. C'est pourquoi, avec cette configuration, ces messages sont toujours refusés par DMARC, mais, au lieu d'être rejetés, ils sont marqués comme courrier indésirable. Si nécessaire, les utilisateurs peuvent toujours accéder à ces messages dans leur boîte de réception via les méthodes suivantes :

- Les utilisateurs ajoutent individuellement des expéditeurs approuvés à l’aide de leur client de messagerie.

- Les administrateurs peuvent utiliser l’[Informations sur la veille contre l’usurpation d’identité](learn-about-spoof-intelligence.md) ou la [Liste verte/rouge du client](tenant-allow-block-list.md) pour autoriser les messages provenant de l’expéditeur usurpé.

- Les administrateurs créent une règle de flux de messagerie Exchange (également appelée règle de transport) pour tous les utilisateurs qui autorise la transmission des messages de ces expéditeurs particuliers.

Si vous souhaitez en savoir plus, consultez la page [Créer des listes d’expéditeurs approuvés](create-safe-sender-lists-in-office-365.md).

## <a name="how-microsoft-365-utilizes-authenticated-received-chain-arc"></a>Comment Microsoft 365 utilise une chaîne reçue authentifiée (ARC)

Toutes les boîtes aux lettres hébergées dans Microsoft 365 tirent désormais parti d’ARC avec une meilleure remise des messages et une protection renforcée contre l’usurpation d’identité. ARC conserve les résultats d’authentification de courrier de tous les intermédiaires participants, ou sauts, lorsqu’un e-mail est acheminé du serveur d’origine vers la boîte aux lettres du destinataire. Avant ARC, les modifications effectuées par les intermédiaires dans le routage d’e-mails, telles que les règles de transfert ou les signatures automatiques, pourraient entraîner des échecs DMARC au moment où les e-mails atteignent la boîte aux lettres du destinataire. Avec ARC, la conservation de chiffrement des résultats d’authentification permet à Microsoft 365 de vérifier l’authenticité de l’expéditeur d’un e-mail.

Microsoft 365 utilise actuellement ARC pour vérifier les résultats de l’authentification lorsque Microsoft est le scellant ARC, mais envisagez d’ajouter une prise en charge pour les scellants ARC tiers à l’avenir.

## <a name="troubleshooting-your-dmarc-implementation"></a>Résolution des problèmes d’implémentation de DMARC

Si EOP n'est pas la première entrée des enregistrements MX de votre domaine, les stratégies de DMARC en cas d'échec aux vérifications ne seront pas appliquées pour votre domaine.

Si vous êtes un client et que l’enregistrement MX principal de votre domaine ne pointe pas vers EOP, vous ne bénéficiez pas de la protection de DMARC. Par exemple, DMARC ne fonctionne pas si l’enregistrement MX pointe vers votre serveur de messagerie local et que les e-mails sont ensuite acheminés vers EOP à l’aide d’un connecteur. Dans ce cas de figure, le domaine de réception est l’un de vos domaines d’accepté, mais EOP n’est pas l’enregistrement MX principal. Par exemple, supposons que l’enregistrement MX de contoso.com pointe vers contoso.com lui-même et que EOP soit utilisé comme enregistrement MX secondaire. L’enregistrement MX de contoso.com se présente alors comme suit :

```console
contoso.com     3600   IN  MX  0  mail.contoso.com
contoso.com     3600   IN  MX  10 contoso-com.mail.protection.outlook.com
```

L’ensemble ou la majorité des messages électroniques seront d’abord acheminés vers mail.contoso.com, puisqu’il s’agit de l’enregistrement MX principal, avant d’être acheminés vers Exchange Online Protection. Dans certains cas, EOP n’est même pas présent dans la liste des enregistrements MX et des connecteurs sont simplement mis en place pour acheminer les messages électroniques. Il n’est pas nécessaire que EOP soit la première entrée de la validation DMARC à effectuer. Il s’agit simplement d’assurer la validation, car il est impossible de s’assurer que tous les serveurs locaux/non-Office 365 effectuent des vérifications DMARC.  DMARC est éligible pour être appliqué au domaine d’un client (et non au serveur) lorsque vous configurez l’enregistrement DMARC TXT, mais il revient au serveur de réception d’effectuer réellement l’application.  Si vous configurez EOP comme serveur de réception, la fonction EOP procède à l’application DMARC.

:::image type="content" source="../../media/Tp_DMARCTroublehoot.png" alt-text="Un graphique de dépannage pour DMARC, fourni par Daniel Mande" lightbox="../../media/Tp_DMARCTroublehoot.png":::

## <a name="for-more-information"></a>Pour plus d'informations

Vous voulez plus d’informations sur DMARC ? Ces ressources peuvent vous aider.

- [En-têtes de messages anti-courrier indésirable](anti-spam-message-headers.md) comprend la syntaxe et les champs d'en-tête utilisés par Microsoft 365 pour les vérifications DMARC.

- Consultez la [série de formations sur DMARC](https://www.m3aawg.org/activities/training/dmarc-training-series) de M<sup>3</sup>AAWG (Messaging, Malware, Mobile Anti-Abuse Working Group).

- Utilisez la liste de vérification proposée par [dmarcian](https://space.dmarcian.com/deployment/).

- Accédez directement à la source à l'adresse [DMARC.org](https://dmarc.org).

## <a name="see-also"></a>Voir aussi

[Comment Microsoft 365 utilise SPF (Sender Policy Framework) pour éviter l’usurpation](how-office-365-uses-spf-to-prevent-spoofing.md)

[**Configurer SPF dans Microsoft 365 pour empêcher l’usurpation**](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

[**Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé dans Microsoft 365**](use-dkim-to-validate-outbound-email.md)
