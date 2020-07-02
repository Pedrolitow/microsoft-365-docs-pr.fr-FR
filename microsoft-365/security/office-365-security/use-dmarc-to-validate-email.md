---
title: Utiliser DMARC pour valider les e-mails
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 4a05898c-b8e4-4eab-bd70-ee912e349737
ms.collection:
- M365-security-compliance
description: Découvrez comment configurer DMARC (Domain-based Message Authentication, Reporting, and Conformance) pour valider les messages envoyés à partir de votre organisation.
ms.openlocfilehash: adc213ec5c47184f997a812425e53a61d7ac2da3
ms.sourcegitcommit: 0650da0e54a2b484a3156b3aabe44397fbb38e00
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "45016320"
---
# <a name="use-dmarc-to-validate-email"></a>Utiliser DMARC pour valider les e-mails

Domain-based Message Authentication, Reporting, and Conformance ([DMARC](https://dmarc.org)) utilise SPF (Sender Policy Framework) et DKIM (DomainKeys Identified Mail) pour authentifier les expéditeurs d'e-mails et faire en sorte que les systèmes de messagerie de destination acceptent les messages envoyés depuis votre domaine comme fiables. L’implémentation de DMARC avec SPF et DKIM fournit une protection supplémentaire contre l’usurpation et les courriers de hameçonnage. DMARC permet aux systèmes de messagerie de réception de déterminer ce qu’ils doivent faire des messages envoyés à partir de votre domaine qui sont rejetés par les contrôles de SPF ou de DKIM.

> [!TIP]
> Visitez le catalogue [Association de sécurité intelligente de Microsoft (MISA)](https://www.microsoft.com/misapartnercatalog) pour afficher les fournisseurs tiers proposant des rapports DMARC pour Microsoft 365.

## <a name="how-do-spf-and-dmarc-work-together-to-protect-email-in-microsoft-365"></a>Comment SPF et DMARC fonctionnent-ils ensemble pour protéger les messages électroniques dans Microsoft 365 ?

 Un message électronique peut contenir plusieurs adresses d’origine (ou d’expéditeur). Ces adresses sont utilisées à des fins différentes. Par exemple, prenez les adresses suivantes :

- **Adresse « Mail From »**  : indique l'expéditeur et l'emplacement où envoyer les notifications de retour en cas de problèmes avec la remise du message, telles que les notifications d'échec de remise. Elle apparaît dans la partie d’enveloppe d’un e-mail et n’est généralement pas affichée par l’application de messagerie. Elle est parfois appelée adresse 5321.MailFrom ou adresse de chemin inverse.

- **Adresse « From »**  : l’adresse affichée comme adresse d’origine par votre application de messagerie. Cette adresse indique l’auteur de l’e-mail. Autrement dit, elle indique la boîte aux lettres de la personne ou du système responsable de la rédaction du message. Elle est parfois appelée adresse 5322.From.

SPF uses a DNS TXT record to provide a list of authorized sending IP addresses for a given domain. Normally, SPF checks are only performed against the 5321.MailFrom address. This means that the 5322.From address is not authenticated when you use SPF by itself. This allows for a scenario where a user can receive a message which passes an SPF check but has a spoofed 5322.From sender address. For example, consider this SMTP transcript:

```text
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

If you configured SPF, then the receiving server performs a check against the Mail from address phish@phishing.contoso.com. If the message came from a valid source for the domain phishing.contoso.com then the SPF check passes. Since the email client only displays the From address, the user sees that this message came from security@woodgrovebank.com. With SPF alone, the validity of woodgrovebank.com was never authenticated.

When you use DMARC, the receiving server also performs a check against the From address. In the example above, if there is a DMARC TXT record in place for woodgrovebank.com, then the check against the From address fails.

## <a name="what-is-a-dmarc-txt-record"></a>Qu’est-ce qu’un enregistrement TXT DMARC ?

Like the DNS records for SPF, the record for DMARC is a DNS text (TXT) record that helps prevent spoofing and phishing. You publish DMARC TXT records in DNS. DMARC TXT records validate the origin of email messages by verifying the IP address of an email's author against the alleged owner of the sending domain. The DMARC TXT record identifies authorized outbound email servers. Destination email systems can then verify that messages they receive originate from authorized outbound email servers.

Un enregistrement TXT DMARC de Microsoft se présente comme suit :

```text
_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.agari.com; ruf=mailto:d@ruf.agari.com; fo=1"
```

Microsoft envoie ses rapports DMARC à [Agari](https://agari.com), un système tiers. Agari collecte et analyse les rapports DMARC. Visitez le catalogue [Association de sécurité intelligente de Microsoft (MISA)](https://www.microsoft.com/misapartnercatalog) pour afficher les fournisseurs tiers proposant des rapports DMARC pour Microsoft 365.

## <a name="implement-dmarc-for-inbound-mail"></a>Mettre en œuvre DMARC pour les messages entrants

You don't have to do a thing to set up DMARC for mail that you receive in Microsoft 365. We've taken care of everything for you. If you want to learn what happens to mail that fails to pass our DMARC checks, see [How Microsoft 365 handles inbound email that fails DMARC](#how-microsoft-365-handles-inbound-email-that-fails-dmarc).

## <a name="implement-dmarc-for-outbound-mail-from-microsoft-365"></a>Mettre en œuvre DMARC pour les messages sortants de Microsoft 365

If you use Microsoft 365 but you aren't using a custom domain, that is, you use onmicrosoft.com, you don't need to do anything else to configure or implement DMARC for your organization. SPF is already set up for you and Microsoft 365 automatically generates a DKIM signature for your outgoing mail. For more information about this signature, see [Default behavior for DKIM and Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

 If you have a custom domain or you are using on-premises Exchange servers in addition to Microsoft 365, you need to manually implement DMARC for your outbound mail. Implementing DMARC for your custom domain includes these steps:

- [Étape 1 : déterminer les sources de messagerie valides pour votre domaine](#step-1-identify-valid-sources-of-mail-for-your-domain)

- [Étape 2 : configurer SPF pour votre domaine](#step-2-set-up-spf-for-your-domain)

- [Étape 3 : configurer DKIM pour votre domaine personnalisé](#step-3-set-up-dkim-for-your-custom-domain)

- [Étape 4 : créer l’enregistrement TXT DMARC pour votre domaine](#step-4-form-the-dmarc-txt-record-for-your-domain)

### <a name="step-1-identify-valid-sources-of-mail-for-your-domain"></a>Étape 1 : déterminer les sources de messagerie valides pour votre domaine

If you have already set up SPF then you have already gone through this exercise. However, for DMARC, there are additional considerations. When identifying sources of mail for your domain there are two questions you need to answer:

- Quelles adresses IP envoient des messages à partir de mon domaine ?

- Pour les messages envoyés par des tiers de ma part, les domaines 5321.MailFrom et 5322.From correspondront-ils ?

### <a name="step-2-set-up-spf-for-your-domain"></a>Étape 2 : configurer SPF pour votre domaine

Maintenant que vous avez une liste de tous vos expéditeurs valides, vous pouvez suivre les étapes pour [configurer SPF pour empêcher l’usurpation d'](set-up-spf-in-office-365-to-help-prevent-spoofing.md).

Par exemple, en supposant que contoso.com envoie du courrier depuis Exchange Online, un serveur Exchange local dont l'adresse IP est 192.168.0.1 et une application web dont l'adresse IP est 192.168.100.100, l'enregistrement TXT SPF ressemblerait à ceci :

```text
contoso.com  IN  TXT  " v=spf1 ip4:192.168.0.1 ip4:192.168.100.100 include:spf.protection.outlook.com -all"
```

Pour obtenir les meilleurs résultats, vérifiez que votre enregistrement TXT SPF tienne compte des expéditeurs tiers.

### <a name="step-3-set-up-dkim-for-your-custom-domain"></a>Étape 3 : configurer DKIM pour votre domaine personnalisé

Once you have set up SPF, you need to set up DKIM. DKIM lets you add a digital signature to email messages in the message header. If you do not set up DKIM and instead allow Microsoft 365 to use the default DKIM configuration for your domain, DMARC may fail. This is because the default DKIM configuration uses your initial onmicrosoft.com domain as the 5322.From address, not your custom domain. This forces a mismatch between the 5321.MailFrom and the 5322.From addresses in all email sent from your domain.

If you have third-party senders that send mail on your behalf and the mail they send has mismatched 5321.MailFrom and 5322.From addresses, DMARC will fail for that email. To avoid this, you need to set up DKIM for your domain specifically with that third-party sender. This allows Microsoft 365 to authenticate email from this 3rd-party service. However, it also allows others, for example, Yahoo, Gmail, and Comcast, to verify email sent to them by the third-party as if it was email sent by you. This is beneficial because it allows your customers to build trust with your domain no matter where their mailbox is located, and at the same time Microsoft 365 won't mark a message as spam due to spoofing because it passes authentication checks for your domain.

Pour obtenir des instructions sur la configuration de DKIM pour votre domaine, y compris sur la façon de configurer DKIM pour les expéditeurs tiers pour leur permettre d'usurper votre domaine, consultez [Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé](use-dkim-to-validate-outbound-email.md).

### <a name="step-4-form-the-dmarc-txt-record-for-your-domain"></a>Étape 4 : créer l’enregistrement TXT DMARC pour votre domaine

Although there are other syntax options that are not mentioned here, these are the most commonly used options for Microsoft 365. Form the DMARC TXT record for your domain in the format:

```text
_dmarc.domain  TTL  IN  TXT  "v=DMARC1; p=policy; pct=100"
```

où :

- *domain* est le domaine que vous souhaitez protéger. Par défaut, l’enregistrement protège le courrier issu du domaine et de tous ses sous-domaines. Par exemple, si vous spécifiez \_dmarc.contoso.com, DMARC protège le courrier issu de ce domaine et tous ses sous-domaines, par exemple housewares.contoso.com ou plumbing.contoso.com.

- *TTL* should always be the equivalent of one hour. The unit used for TTL, either hours (1 hour), minutes (60 minutes), or seconds (3600 seconds), will vary depending on the registrar for your domain.

- *pct=100* indique que cette règle doit être utilisée pour 100 % des e-mails.

- *policy* specifies what policy you want the receiving server to follow if DMARC fails. You can set the policy to none, quarantine, or reject.

Pour plus d'informations sur les options à utiliser, familiarisez-vous avec les concepts de la section [Meilleures pratiques pour la mise en œuvre de DMARC dans Microsoft 365](#best-practices-for-implementing-dmarc-in-microsoft-365).

Exemples :

- Stratégie définie sur none (Aucune)

    ```text
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=none"
    ```

- Stratégie définie sur quarantine (Mettre en quarantaine)

    ```text
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=quarantine"
    ```

- Stratégie définie sur reject (Rejeter)

    ```text
    _dmarc.contoso.com  3600 IN  TXT  "v=DMARC1; p=reject"
    ```

Once you have formed your record, you need to update the record at your domain registrar. For instructions on adding the DMARC TXT record to your DNS records for Microsoft 365, see [Create DNS records for Microsoft 365 when you manage your DNS records](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider).

## <a name="best-practices-for-implementing-dmarc-in-microsoft-365"></a>Meilleures pratiques pour la mise en œuvre de DMARC dans Microsoft 365

You can implement DMARC gradually without impacting the rest of your mail flow. Create and implement a roll out plan that follows these steps. Do each of these steps first with a sub-domain, then other sub-domains, and finally with the top-level domain in your organization before moving on to the next step.

1. Contrôlez les effets de l’implémentation DMARC

    Start with a simple monitoring-mode record for a sub-domain or domain that requests that DMARC receivers send you statistics about messages that they see using that domain. A monitoring-mode record is a DMARC TXT record that has its policy set to none (p=none). Many companies publish a DMARC TXT record with p=none because they are unsure about how much email they may lose by publishing a more restrictive DMARC policy.

    You can do this even before you've implemented SPF or DKIM in your messaging infrastructure. However, you won't be able to effectively quarantine or reject mail by using DMARC until you also implement SPF and DKIM. As you introduce SPF and DKIM, the reports generated through DMARC will provide the numbers and sources of messages that pass these checks, and those that don't. You can easily see how much of your legitimate traffic is or isn't covered by them, and troubleshoot any problems. You'll also begin to see how many fraudulent messages are being sent, and from where.

2. Demandez que les systèmes de messagerie externes mettent en quarantaine le courrier qui échoue aux vérifications de DMARC

    When you believe that all or most of your legitimate traffic is protected by SPF and DKIM, and you understand the impact of implementing DMARC, you can implement a quarantine policy. A quarantine policy is a DMARC TXT record that has its policy set to quarantine (p=quarantine). By doing this, you are asking DMARC receivers to put messages from your domain that fail DMARC into the local equivalent of a spam folder instead of your customers' inboxes.

3. Demandez que les systèmes de messagerie externes n’acceptent pas les messages qui échouent aux vérifications de DMARC

    The final step is implementing a reject policy. A reject policy is a DMARC TXT record that has its policy set to reject (p=reject). When you do this, you're asking DMARC receivers not to accept messages that fail the DMARC checks.

## <a name="how-microsoft-365-handles-outbound-email-that-fails-dmarc"></a>Gestion des messages électroniques sortants qui échouent aux vérifications de DMARC dans Microsoft 365

Si un message sortant issu de Microsoft 365 échoue aux vérifications de DMARC et que vous avez défini la stratégie sur p=quarantine (mise en quarantaine) ou p=reject (rejet), le message est routé via le [pool de remise à risque plus élevé pour les messages sortants](high-risk-delivery-pool-for-outbound-messages.md). Les e-mails sortants ne sont pas écrasés.

If you publish a DMARC reject policy (p=reject), no other customer in Microsoft 365 can spoof your domain because messages will not be able to pass SPF or DKIM for your domain when relaying a message outbound through the service. However, if you do publish a DMARC reject policy but don't have all of your email authenticated through Microsoft 365, some of it may be marked as spam for inbound email (as described above), or it will be rejected if you do not publish SPF and try to relay it outbound through the service. This happens, for example, if you forget to include some of the IP addresses for servers and apps that send mail on behalf of your domain when you form your DMARC TXT record.

## <a name="how-microsoft-365-handles-inbound-email-that-fails-dmarc"></a>Gestion des messages électroniques entrants qui échouent aux vérifications de DMARC dans Microsoft 365

Si la stratégie DMARC du serveur expéditeur est `p=reject`, EOP marque le message comme du courrier indésirable au lieu de le rejeter. En d’autres termes, pour les messages entrants, Microsoft 365 traite `p=reject` et `p=quarantine` de la même façon. Les administrateurs peuvent définir l’action à effectuer sur les messages classés comme usurpation d’identité dans la stratégie [anti-hameçonnage](set-up-anti-phishing-policies.md).

Microsoft 365 est configuré de cette façon, car certains messages légitimes peuvent échouer aux vérifications de DMARC. Cela peut être le cas, par exemple, si un message est envoyé à une liste de diffusion qui le relaie ensuite à tous ses participants. Si Microsoft 365 rejette ces e-mails, les destinataires peuvent perdre des messages légitimes sans avoir aucun moyen de les récupérer. C’est pourquoi, avec cette configuration, ces messages sont toujours refusés par DMARC, mais, au lieu d’être rejetés, ils sont marqués comme courrier indésirable. Si nécessaire, les utilisateurs peuvent toujours accéder à ces messages dans leur boîte de réception via les méthodes suivantes :

- Les utilisateurs ajoutent individuellement des expéditeurs approuvés à l’aide de leur client de messagerie.

- Les administrateurs peuvent mettre à jour les rapports de [veille contre l’usurpation d’identité](learn-about-spoof-intelligence.md) pour autoriser l’usurpation.

- Les administrateurs créent une règle de flux de messagerie Exchange (également appelée règle de transport) pour tous les utilisateurs qui autorise la transmission des messages de ces expéditeurs particuliers.

Si vous souhaitez en savoir plus, consultez la page [Créer des listes d’expéditeurs approuvés](create-safe-sender-lists-in-office-365.md).

## <a name="how-microsoft-365-utilizes-authenticated-received-chain-arc"></a>Comment Microsoft 365 utilise une chaîne reçue authentifiée (ARC)

Toutes les boîtes aux lettres hébergées dans Microsoft 365 tirent désormais parti d’ARC avec une meilleure remise des messages et une protection renforcée contre l’usurpation d’identité. ARC conserve les résultats d’authentification de courrier de tous les intermédiaires participants, ou sauts, lorsqu’un e-mail est acheminé du serveur d’origine vers la boîte aux lettres du destinataire. Avant ARC, les modifications effectuées par les intermédiaires dans le routage d’e-mails, telles que les règles de transfert ou les signatures automatiques, pourraient entraîner des échecs DMARC au moment où les e-mails atteignent la boîte aux lettres du destinataire. Avec ARC, la conservation de chiffrement des résultats d’authentification permet à Microsoft 365 de vérifier l’authenticité de l’expéditeur d’un e-mail.

Microsoft 365 utilise actuellement ARC pour vérifier les résultats de l’authentification lorsque Microsoft est le scellant ARC, mais envisagez d’ajouter une prise en charge pour les scellants ARC tiers à l’avenir.

## <a name="troubleshooting-your-dmarc-implementation"></a>Résolution des problèmes d’implémentation de DMARC

Si EOP n'est pas la première entrée des enregistrements MX de votre domaine, les stratégies de DMARC en cas d'échec aux vérifications ne seront pas appliquées pour votre domaine.

Si vous êtes un client et que l’enregistrement MX principal de votre domaine ne pointe pas vers EOP, vous ne bénéficiez pas de la protection de DMARC. Par exemple, DMARC ne fonctionne pas si l’enregistrement MX pointe vers votre serveur de messagerie local et que les e-mails sont ensuite acheminés vers EOP à l’aide d’un connecteur. Dans ce cas de figure, le domaine de réception est l’un de vos domaines d’accepté, mais EOP n’est pas l’enregistrement MX principal. Par exemple, supposons que l’enregistrement MX de contoso.com pointe vers contoso.com lui-même et que EOP soit utilisé comme enregistrement MX secondaire. L’enregistrement MX de contoso.com se présente alors comme suit :

```text
contoso.com     3600   IN  MX  0  mail.contoso.com
contoso.com     3600   IN  MX  10 contoso-com.mail.protection.outlook.com
```

L’ensemble ou la majorité des messages électroniques seront d’abord acheminés vers mail.contoso.com, puisqu’il s’agit de l’enregistrement MX principal, avant d’être acheminés vers Exchange Online Protection. Dans certains cas, EOP n’est même pas présent dans la liste des enregistrements MX et des connecteurs sont simplement mis en place pour acheminer les messages électroniques. Il n’est pas nécessaire que EOP soit la première entrée de la validation DMARC à effectuer. Il s’agit simplement d’assurer la validation, car il est impossible de s’assurer que tous les serveurs locaux/non-Office 365 effectuent des vérifications DMARC.  DMARC est éligible pour être appliqué au domaine d’un client (et non au serveur) lorsque vous configurez l’enregistrement DMARC TXT, mais il revient au serveur de réception d’effectuer réellement l’application.  Si vous configurez EOP comme serveur de réception, la fonction EOP procède à l’application DMARC.

:::image type="content" source="../../media/Tp_DMARCTroublehoot.png" alt-text="Un graphique de dépannage pour DMARC, fourni par Daniel Mande":::

## <a name="for-more-information"></a>Pour plus d'informations

Want more information about DMARC? These resources can help.

- [En-têtes de messages anti-courrier indésirable](anti-spam-message-headers.md) comprend la syntaxe et les champs d'en-tête utilisés par Microsoft 365 pour les vérifications DMARC.

- Consultez la [série de formations sur DMARC](https://www.m3aawg.org/activities/training/dmarc-training-series) de M <sup>3</sup>AAWG (Messaging, Malware, Mobile Anti-Abuse Working Group).

- Utilisez la liste de vérification proposée par [dmarcian](https://space.dmarcian.com/deployment/).

- Accédez directement à la source à l'adresse [DMARC.org](https://dmarc.org).

## <a name="see-also"></a>Voir aussi

[Comment Microsoft 365 utilise SPF (Sender Policy Framework) pour éviter l’usurpation](how-office-365-uses-spf-to-prevent-spoofing.md)

[Configurer SPF dans Microsoft 365 pour empêcher l’usurpation](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

[Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé dans Microsoft 365](use-dkim-to-validate-outbound-email.md)
