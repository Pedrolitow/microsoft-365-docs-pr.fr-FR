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
ms.openlocfilehash: f33ea4cfe9323121f928e9a07247167c9d536721
ms.sourcegitcommit: d09eb780dc41a01796eb8137fbe9267231af6746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2022
ms.locfileid: "67388416"
---
# <a name="use-dmarc-to-validate-email"></a>Utiliser DMARC pour valider les e-mails

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Domain-based Message Authentication, Reporting, and Conformance ([DMARC](https://dmarc.org)) fonctionne avec Sender Policy Framework (SPF) et DomainKeys Identified Mail (DKIM) pour authentifier les expéditeurs de courrier.

DMARC garantit que les systèmes de messagerie de destination font confiance aux messages envoyés depuis votre domaine. L’utilisation de DMARC avec SPF et DKIM offre aux organisations une meilleure protection contre l’usurpation d’identité et le phishing. DMARC aide les systèmes de réception de messagerie à décider quoi faire avec les messages de votre domaine qui échouent aux vérifications SPF ou DKIM.

> [!TIP]
> Visitez le catalogue [Association de sécurité intelligente de Microsoft (MISA)](https://www.microsoft.com/misapartnercatalog) pour afficher les fournisseurs tiers proposant des rapports DMARC pour Microsoft 365.

## <a name="how-do-spf-and-dmarc-work-together-to-protect-email-in-microsoft-365"></a>Comment SPF et DMARC fonctionnent-ils ensemble pour protéger les messages électroniques dans Microsoft 365 ?

 Un message électronique peut contenir plusieurs adresses d’origine (ou d’expéditeur). Ces adresses sont utilisées à des fins différentes. Par exemple, prenez les adresses suivantes :

- **Adresse "Mail From"** : Identifie l’expéditeur et indique où envoyer les avis de retour en cas de problème avec la livraison du message (comme les avis de non-livraison). L’*Adresse de messagerie* apparaît dans la partie enveloppe d’un e-mail et n’est pas affichée par votre application de messagerie. Elle est parfois appelée *adresse 5321.MailFrom* ou *adresse de chemin inverse*.

- **Adresse « From »**  : l’adresse affichée comme adresse d’origine par votre application de messagerie. L’*Adresse de l’expéditeur* identifie l’auteur de l’e-mail. Autrement dit, elle indique la boîte aux lettres de la personne ou du système responsable de la rédaction du message. *Adresse de provenance* est parfois appelée l’*adresse 5322.From*.

SPF utilise un enregistrement DNS TXT pour répertorier les adresses IP d’envoi autorisées pour un domaine donné. En règle générale, les vérifications SPF sont uniquement effectuées pour l'adresse 5321.MailFrom. L’adresse 5322.From n’est pas authentifiée lorsque vous utilisez SPF seul, ce qui permet un scénario dans lequel un utilisateur reçoit un message qui a réussi les contrôles SPF mais qui a une adresse d’expéditeur 5322.From usurpée. Prenez par exemple, la transcription SMTP suivante :

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
S: Please click the following link to verify that Microsoft has the right information for your account.
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

Si vous avez configuré SPF, le serveur de réception effectue une vérification par rapport au courrier de l’adresse phish@phishing.contoso.com. Si le message provenait d’une source valide pour le domaine phishing.contoso.com, la vérification SPF réussit. Étant donné que le client de messagerie n’affiche que l’adresse De, l’utilisateur voit que ce message provient de security@woodgrovebank.com. Avec SPF seul, la validité de l'adresse woodgrovebank.com n'a jamais été authentifiée.

Lorsque vous utilisez DMARC, le serveur de réception effectue aussi une vérification sur l'adresse From. Dans l’exemple ci-dessus, s’il existe un enregistrement DMARC TXT pour woodgrovebank.com, la vérification par rapport à l’adresse De échoue.

## <a name="what-is-a-dmarc-txt-record"></a>Qu’est-ce qu’un enregistrement TXT DMARC ?

À l'instar des enregistrements DNS pour SPF, l'enregistrement pour DMARC est un enregistrement DNS au format texte (TXT) qui empêche l'usurpation d'identité et le hameçonnage. Vous publiez les enregistrements TXT DMARC dans le système DNS. Les enregistrements TXT DMARC valident l'origine des messages électroniques en comparant l'adresse IP de l'auteur de l'e-mail à celle du prétendu propriétaire du domaine d'expédition. L'enregistrement TXT DMARC identifie les serveurs de messagerie sortants autorisés. Les systèmes de messagerie électronique de destination peuvent alors vérifier si les messages reçus proviennent de serveurs de messagerie sortants autorisés.

Un enregistrement TXT DMARC de Microsoft se présente comme suit :

```console
_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.contoso.com; ruf=mailto:d@ruf.contoso.com; fo=1"
```

Pour d’autres fournisseurs tiers qui proposent des rapports DMARC Microsoft 365, visitez le [catalogue MISA.](https://www.microsoft.com/misapartnercatalog?IntegratedProducts=DMARCReportingforOffice365)

## <a name="set-up-dmarc-for-inbound-mail"></a>Configurer DMARC pour les messages entrants

Vous n’avez rien à faire pour configurer DMARC pour les messages que vous recevez dans Microsoft 365. Tout est pris en charge. Si vous voulez découvrir ce qui se passe pour le courrier électronique rejeté par nos vérifications DMARC, reportez-vous à la section [Gestion des messages électroniques entrants qui échouent aux vérifications de DMARC dans Microsoft 365](#how-microsoft-365-handles-inbound-email-that-fails-dmarc).

## <a name="set-up-dmarc-for-outbound-mail-from-microsoft-365"></a>Configurer DMARC pour les messages sortants de Microsoft 365

Si vous utilisez Microsoft 365, mais pas un domaine personnalisé (vous utilisez onmicrosoft.com), SPF est déjà configuré pour vous et Microsoft 365 génère automatiquement une signature DKIM pour vos messages sortants. Pour plus d'informations sur cette signature, voir [Comportement par défaut pour DKIM et Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior). Afin de configurer DMARC pour votre organisation, vous devez [Former l’enregistrement DMARC TXT](#step-4-form-the-dmarc-txt-record-for-your-domain) pour le domaine onmicrosoft.com et le publier sur DNS via [Centre d'administration Office 365](https://admin.microsoft.com) > Paramètres > Domaines > cliquez sur le domaine onmicrosoft.com > Ajouter un enregistrement.

 Si vous avez un domaine personnalisé ou utilisez des serveurs Exchange sur site avec Microsoft 365, vous devez configurer manuellement DMARC pour votre courrier sortant. La configuration de DMARC pour votre domaine personnalisé comprend les étapes suivantes :

- [Étape 1 : déterminer les sources de messagerie valides pour votre domaine](#step-1-identify-valid-sources-of-mail-for-your-domain)

- [Étape 2 : configurer SPF pour votre domaine](#step-2-set-up-spf-for-your-domain)

- [Étape 3 : configurer DKIM pour votre domaine personnalisé](#step-3-set-up-dkim-for-your-custom-domain)

- [Étape 4 : créer l’enregistrement TXT DMARC pour votre domaine](#step-4-form-the-dmarc-txt-record-for-your-domain)

### <a name="step-1-identify-valid-sources-of-mail-for-your-domain"></a>Étape 1 : déterminer les sources de messagerie valides pour votre domaine

Si vous avez déjà configuré SPF, vous avez déjà effectué cet exercice. Il y a d’autres considérations pour DMARC. Lorsque vous identifiez les sources de messagerie pour votre domaine, répondez à ces deux questions :

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

Une fois que vous avez configuré SPF, vous devez configurer DKIM. DKIM vous permet d'ajouter une signature numérique aux messages électroniques dans l'en-tête du message. Si vous ne configurez pas DKIM et autorisez à la place Microsoft 365 à utiliser la configuration DKIM par défaut pour votre domaine, DMARC peut échouer. Cet échec peut se produire car la configuration DKIM par défaut utilise votre domaine *onmicrosoft.com* d’origine comme adresse *5321.MailFrom*, et non comme domaine *personnalisé* . Cela crée une incompatibilité entre les adresses *5321.MailFrom* et *5322.From* dans tous les e-mails envoyés depuis votre domaine.

Si des expéditeurs tiers envoient des messages en votre nom et que les adresses 5321.MailFrom et 5322.From de ces messages ne correspondent pas, DMARC rejettera ce message électronique. Pour éviter ce problème, vous devez configurer DKIM en définissant spécifiquement cet expéditeur tiers pour votre domaine. Cela permet à Microsoft 365 d'authentifier les messages envoyés par ce service tiers. Toutefois, cela autorise également d'autres entités, par exemple, Yahoo, Gmail et Comcast, à vérifier le courrier électronique qui leur est envoyé par le tiers comme s'il s'agissait de messages envoyés par vous-même. C'est un avantage, car, d'un côté, cela renforce la confiance que les clients peuvent avoir en votre domaine, quel que soit l'endroit où se trouvent leurs boîtes aux lettres et, de l'autre, Microsoft 365 ne marquera pas un message comme spam pour cause d'usurpation d'identité, car cet e-mail aura été accepté par les vérifications d'authentification pour votre domaine.

Pour obtenir des instructions sur la configuration de DKIM pour votre domaine, y compris sur la façon de configurer DKIM pour les expéditeurs tiers pour leur permettre d'usurper votre domaine, consultez [Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé](use-dkim-to-validate-outbound-email.md).

### <a name="step-4-form-the-dmarc-txt-record-for-your-domain"></a>Étape 4 : créer l’enregistrement TXT DMARC pour votre domaine

Bien qu’il existe d’autres options de syntaxe qui ne sont pas mentionnées ici, ce sont les options les plus couramment utilisées pour Microsoft 365. Créez l’enregistrement TXT DMARC pour votre domaine au format suivant :

```console
_dmarc.domain  TTL  IN  TXT  "v=DMARC1; p=policy; pct=100"
```

Où :

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

Une fois que vous avez formé votre enregistrement, vous devez mettre à jour l’enregistrement auprès de votre registraire de domaine.

## <a name="dmarc-mail-public-preview-feature"></a>Courrier DMARC (fonctionnalité d'évaluation publique)

> [!CAUTION]
> Les courriers ne sont pas nécessairement envoyés quotidiennement, et le rapport lui-même peut changer pendant la préversion publique. Les courriels du rapport global DMARC peuvent être attendus des comptes des consommateurs (tels que les comptes hotmail.com, outlook.com ou live.com).

Dans cet exemple d’enregistrement TXT DMARC : , vous pouvez voir l’adresse rua, dans ce cas, traitée par la société `dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.agari.com; ruf=mailto:d@ruf.agari.com; fo=1"` tierce Agari.  Cette adresse permet d’envoyer des « commentaires agrégés » aux besoins d’analyse et de générer un rapport.

> [!TIP]
> Visitez le [catalogue MISA](https://www.microsoft.com/misapartnercatalog) pour afficher davantage de fournisseurs tiers offrant des rapports DMARC pour Microsoft 365. Pour plus d’informations sur les adresses DMARC « rua », voir [ « Authentification de message, rapports et conformité basée sur un domaine » de l’organisation IETF](https://datatracker.ietf.org/doc/html/rfc7489).

## <a name="best-practices-for-implementing-dmarc-in-microsoft-365"></a>Meilleures pratiques pour la mise en œuvre de DMARC dans Microsoft 365

Vous pouvez implémenter DMARC progressivement sans que cela n’ait de répercussions sur le reste de votre flux de messagerie. Créez et mettez en œuvre un plan de déploiement qui suit la procédure ci-dessous. Effectuez d’abord chaque étape avec un sous-domaine, puis avec d’autres, et enfin avec le domaine de niveau supérieur de votre organisation avant de passer à l’étape suivante.

1. Contrôlez les effets de l’implémentation DMARC

    Commencez avec un simple enregistrement en mode surveillance pour un sous-domaine ou un domaine qui requiert que les récepteurs DMARC vous envoient des statistiques sur les messages qu'ils voient pour ce domaine. Un enregistrement en mode surveillance est un enregistrement TXT DMARC dont la stratégie est définie sur Aucune (p=none). De nombreuses entreprises publient un enregistrement DMARC TXT avec p=none car elles ne sont pas sûres de la quantité d’e-mails qu’elles risquent de perdre en publiant une stratégie DMARC plus restrictive.

    Vous pouvez effectuer cette opération avant même d'avoir mis en œuvre SPF ou DKIM dans votre infrastructure de messagerie. Toutefois, vous ne pourrez pas mettre en quarantaine ou refuser des messages à l'aide de DMARC jusqu'à ce que vous implémentiez également SPF et DKIM. Au fur et à mesure que vous introduisez SPF et DKIM, les rapports générés via DMARC indiqueront le nombre et les sources des messages qui réussissent ces contrôles, par rapport à ceux qui ne le font pas. Vous pouvez facilement déterminer la part de votre trafic légitime qui est ou non couverte par ces catégories et résoudre les problèmes. Vous commencerez également à voir combien de messages frauduleux sont envoyés et d’où ils sont envoyés.

2. Demandez que les systèmes de messagerie externes mettent en quarantaine le courrier qui échoue aux vérifications de DMARC

    Lorsque vous pensez que tout ou partie de votre trafic légitime est protégé par SPF et DKIM, et que vous connaissez les répercussions de l'implémentation de DMARC, vous pouvez implémenter une stratégie de mise en quarantaine. Une stratégie de mise en quarantaine est un enregistrement TXT DMARC dont la stratégie est définie de manière à effectuer une mise en quarantaine (p=quarantine). En faisant cela, vous demandez aux récepteurs DMARC de placer les messages de votre domaine qui échouent DMARC dans l’équivalent local d’un dossier de spam au lieu des boîtes de réception de vos clients.

3. Demandez que les systèmes de messagerie externes n’acceptent pas les messages qui échouent aux vérifications de DMARC

    L'étape finale consiste à mettre en œuvre une stratégie de rejet. Une stratégie de rejet est un enregistrement TXT DMARC dont la stratégie est définie de manière à effectuer un rejet (p=reject). Lorsque vous effectuez cette opération, vous demandez aux récepteurs DMARC ne pas accepter les messages qui échouent aux tests DMARC.

4. Comment configurer DMARC pour le sous-domaine ?

   DMARC est implémenté en publiant une stratégie en tant qu’enregistrement TXT dans DNS et est hiérarchique (par exemple, une stratégie publiée pour contoso.com s’appliquera à sub.domain.contonos.com sauf si une stratégie différente est explicitement définie pour le sous-domaine). Cela est utile car les organisations peuvent spécifier un plus petit nombre d’enregistrements DMARC de haut niveau pour une couverture plus large. Veillez à configurer des enregistrements DMARC de sous-domaine explicites lorsque vous ne souhaitez pas que les sous-domaines héritent de l’enregistrement DMARC du domaine de premier niveau.

   En outre, vous pouvez ajouter une stratégie de type caractère générique pour DMARC lorsque les sous-domaines ne doivent pas envoyer de message électronique, en ajoutant la valeur `sp=reject`. Par exemple :

   ```text
   _dmarc.contoso.com. TXT "v=DMARC1; p=reject; sp=reject; ruf=mailto:authfail@contoso.com; rua=mailto:aggrep@contoso.com"
   ```

## <a name="how-microsoft-365-handles-outbound-email-that-fails-dmarc"></a>Gestion des messages électroniques sortants qui échouent aux vérifications de DMARC dans Microsoft 365

Si un message sortant issu de Microsoft 365 échoue aux vérifications de DMARC et que vous avez défini la stratégie sur p=quarantine (mise en quarantaine) ou p=reject (rejet), le message est routé via le [pool de remise à risque plus élevé pour les messages sortants](high-risk-delivery-pool-for-outbound-messages.md). Il n’y a pas de remplacement pour les e-mails sortants.

Si vous publiez une stratégie de rejet DMARC (p=reject), aucun autre client dans Microsoft 365 ne peut usurper votre domaine, car les messages ne pourront pas passer SPF ou DKIM pour votre domaine lors du relais d’un message sortant via le service. Toutefois, si vous publiez une stratégie de rejet DMARC mais que tous vos e-mails ne sont pas authentifiés via Microsoft 365, certains d’entre eux peuvent être marqués comme spam pour les e-mails entrants (comme décrit ci-dessus), ou ils seront rejetés si vous ne publiez pas SPF et essayez de les relayer via le service. Cela peut se produire, par exemple, si vous avez oublié d’inclure les adresses IP de certains serveurs et de certaines applications qui envoient des messages au nom de votre domaine lorsque vous avez créé votre enregistrement TXT DMARC.

## <a name="how-microsoft-365-handles-inbound-email-that-fails-dmarc"></a>Gestion des messages électroniques entrants qui échouent aux vérifications de DMARC dans Microsoft 365

Si la politique de DMARC du serveur d'envoi est `p=reject`, [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) marque le message comme étant un spoof au lieu de le rejeter. En d’autres termes, pour les messages entrants, Microsoft 365 traite `p=reject` et `p=quarantine` de la même façon. Les administrateurs peuvent définir l’action à effectuer sur les messages classés comme usurpation d’identité dans la stratégie [anti-hameçonnage](set-up-anti-phishing-policies.md).

Microsoft 365 est configuré de cette façon, car certains messages légitimes peuvent échouer aux vérifications de DMARC. Par exemple, un message peut échouer DMARC s’il est envoyé à une liste de diffusion qui relaie ensuite le message à tous les participants de la liste. Si Microsoft 365 rejette ces e-mails, les destinataires peuvent perdre des messages légitimes sans avoir aucun moyen de les récupérer. Au lieu de cela, ces messages échoueront toujours DMARC mais ils seront marqués comme spam et non rejetés. Si nécessaire, les utilisateurs peuvent toujours accéder à ces messages dans leur boîte de réception via les méthodes suivantes :

- Les utilisateurs ajoutent individuellement des expéditeurs approuvés à l’aide de leur client de messagerie.

- Les administrateurs peuvent utiliser l’[Informations sur la veille contre l’usurpation d’identité](learn-about-spoof-intelligence.md) ou la [Liste verte/rouge du client](manage-tenant-allow-block-list.md) pour autoriser les messages provenant de l’expéditeur usurpé.

- Les administrateurs créent une règle de flux de messagerie Exchange (également appelée règle de transport) pour tous les utilisateurs qui autorise la transmission des messages de ces expéditeurs particuliers.

Si vous souhaitez en savoir plus, consultez la page [Créer des listes d’expéditeurs approuvés](create-safe-sender-lists-in-office-365.md).

## <a name="how-microsoft-365-utilizes-authenticated-received-chain-arc"></a>Comment Microsoft 365 utilise une chaîne reçue authentifiée (ARC)

Toutes les boîtes aux lettres hébergées dans Microsoft 365 tirent désormais parti d’ARC avec une meilleure remise des messages et une protection renforcée contre l’usurpation d’identité. ARC conserve les résultats d’authentification de courrier de tous les intermédiaires participants, ou sauts, lorsqu’un e-mail est acheminé du serveur d’origine vers la boîte aux lettres du destinataire. Avant ARC, les modifications effectuées par les intermédiaires dans le routage d’e-mails, telles que les règles de transfert ou les signatures automatiques, pourraient entraîner des échecs DMARC au moment où les e-mails atteignent la boîte aux lettres du destinataire. Avec ARC, la conservation de chiffrement des résultats d’authentification permet à Microsoft 365 de vérifier l’authenticité de l’expéditeur d’un e-mail.

Microsoft 365 utilise actuellement ARC pour vérifier les résultats de l’authentification lorsque Microsoft est le scellant ARC, mais envisagez d’ajouter une prise en charge pour les scellants ARC tiers à l’avenir.

## <a name="troubleshooting-your-dmarc-implementation"></a>Résolution des problèmes d’implémentation de DMARC

Si vous avez configuré les enregistrements MX de votre domaine où EOP n’est pas la première entrée, les échecs DMARC ne seront pas appliqués pour votre domaine.

Si vous êtes un client et que l’enregistrement MX principal de votre domaine ne pointe pas vers EOP, vous ne bénéficierez pas des avantages de DMARC. Par exemple, DMARC ne fonctionne pas si l’enregistrement MX pointe vers votre serveur de messagerie local et que les e-mails sont ensuite acheminés vers EOP à l’aide d’un connecteur. Dans ce scénario, le domaine de réception est l’un de vos domaines acceptés, mais EOP n’est pas le MX principal. Par exemple, supposons que l’enregistrement MX de contoso.com pointe vers contoso.com lui-même et que EOP soit utilisé comme enregistrement MX secondaire. L’enregistrement MX de contoso.com se présente alors comme suit :

```console
contoso.com     3600   IN  MX  0  mail.contoso.com
contoso.com     3600   IN  MX  10 contoso-com.mail.protection.outlook.com
```

L’ensemble ou la majorité des messages électroniques seront d’abord acheminés vers mail.contoso.com, puisqu’il s’agit de l’enregistrement MX principal, avant d’être acheminés vers Exchange Online Protection. Dans certains cas, EOP n’est même pas présent dans la liste des enregistrements MX et des connecteurs sont simplement mis en place pour acheminer les messages électroniques. EOP ne doit pas nécessairement être la première entrée pour que la validation DMARC soit effectuée. Il garantit simplement la validation, pour être certain que tous les serveurs locaux/non-O365 feront des vérifications DMARC.  DMARC est éligible pour être appliqué pour le domaine d’un client (pas le serveur) lorsque vous configurez l’enregistrement DMARC TXT, mais c’est au serveur de réception de faire réellement l’application.  Si vous configurez EOP comme serveur de réception, la fonction EOP procède à l’application DMARC.

:::image type="content" source="../../media/Tp_DMARCTroublehoot.png" alt-text="Graphique de résolution des problèmes pour DMARC" lightbox="../../media/Tp_DMARCTroublehoot.png":::

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

[Utilisez des expéditeurs ARC de confiance pour les flux de messagerie légitimes](/microsoft-365/security/office-365-security/use-arc-exceptions-to-mark-trusted-arc-senders?view=o365-21vianet&preserve-view=true)
