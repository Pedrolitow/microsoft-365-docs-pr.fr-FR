---
title: Comment le SPF (Sender Policy Framework) empêche l’usurpation d’identité
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 3aff33c5-1416-4867-a23b-e0c0c5b4d2be
ms.collection:
- m365-security
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment Microsoft 365 utilise l’enregistrement TXT (Sender Policy Framework) (SPF) dans DNS pour s’assurer que les systèmes de messagerie de destination approuvent les messages envoyés à partir de votre domaine personnalisé.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: e72f3c12078f355617e84b19265f585ef2376377
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68625014"
---
# <a name="how-microsoft-365-uses-sender-policy-framework-spf-to-prevent-spoofing"></a>Comment Microsoft 365 utilise SPF (Sender Policy Framework) pour éviter l’usurpation

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 **Résumé:** Cet article décrit comment Microsoft 365 utilise l’enregistrement TXT (Sender Policy Framework) (SPF) dans DNS pour s’assurer que les systèmes de messagerie de destination approuvent les messages envoyés à partir de votre domaine personnalisé. Cela s’applique aux messages sortants envoyés à partir de Microsoft 365. Les messages envoyés de Microsoft 365 à un destinataire dans Microsoft 365 passent toujours SPF.

An SPF TXT record is a DNS record that helps prevent spoofing and phishing by verifying the domain name from which email messages are sent. SPF validates the origin of email messages by verifying the IP address of the sender against the alleged owner of the sending domain.

> [!NOTE]
> SPF record types were deprecated by the Internet Engineering Task Force (IETF) in 2014. Instead, ensure that you use TXT records in DNS to publish your SPF information. The rest of this article uses the term SPF TXT record for clarity.

Les administrateurs de domaine publient des informations SPF dans les enregistrements TXT au sein du système DNS. Les informations SPF identifient les serveurs de messagerie sortants autorisés. Les systèmes de messagerie électronique de destination vérifient que les messages proviennent de serveurs de messagerie sortants autorisés. Si vous êtes déjà familiarisé avec SPF ou si vous disposez d’un déploiement simple, et que vous avez simplement besoin de savoir ce qu’il faut inclure dans votre enregistrement TXT SPF dans DNS pour Microsoft 365, vous pouvez accéder à [Configurer SPF dans Microsoft 365 pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Si vous n’avez pas de déploiement entièrement hébergé dans Microsoft 365, ou si vous souhaitez plus d’informations sur le fonctionnement de SPF ou sur la résolution des problèmes de SPF pour Microsoft 365, continuez à lire.

> [!NOTE]
> Auparavant, vous deviez ajouter un autre enregistrement TXT SPF à votre domaine personnalisé si vous utilisiez également SharePoint Online. Cela n'est plus nécessaire. Ce changement doit réduire le risque que les messages de notification SharePoint Online terminent dans le dossier Courrier indésirable. Vous n’avez pas besoin d’apporter des modifications immédiatement, mais si vous recevez l’erreur « Trop de recherches », modifiez votre enregistrement TXT SPF comme décrit dans [Configurer SPF dans Microsoft 365 pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md).

## <a name="how-spf-works-to-prevent-spoofing-and-phishing-in-microsoft-365"></a>Fonctionnement de SPF pour empêcher l’usurpation d’identité et le hameçonnage dans Microsoft 365
<a name="HowSPFWorks"> </a>

SPF détermine si un expéditeur est autorisé à envoyer des messages au nom d'un domaine. Si l’expéditeur n’est pas autorisé à le faire, c’est-à-dire, si l’e-mail échoue, la vérification SPF sur le serveur de réception, la stratégie de courrier indésirable configurée sur ce serveur détermine ce qu’il faut faire avec le message.

Chaque enregistrement TXT SPF contient trois parties : la déclaration qu’il s’agit d’un enregistrement TXT SPF, les adresses IP autorisées à envoyer des messages à partir de votre domaine et les domaines externes qui peuvent être envoyés au nom de votre domaine, et une règle d’application. Ces trois éléments sont obligatoires pour un enregistrement TXT SPF valide. Cet article décrit la façon dont vous formez votre enregistrement TXT SPF et fournit les meilleures pratiques pour utiliser les services dans Microsoft 365. Des liens vers des instructions sur l’utilisation de votre bureau d’enregistrement de domaine pour publier votre enregistrement dans DNS sont également disponibles.

### <a name="spf-basics-ip-addresses-allowed-to-send-from-your-custom-domain"></a>Concepts de base SPF : adresses IP autorisées à envoyer des messages à partir de votre domaine personnalisé
<a name="SPFBasicsIPaddresses"> </a>

Examinez la syntaxe de base pour une règle SPF :

v=spf1 \<IP\> \<enforcement rule\>

Par exemple, supposons que la règle SPF suivante existe pour contoso.com :

v=spf1 \<IP address #1\> \<IP address #2\> \<IP address #3\> \<enforcement rule\>

Dans cet exemple, la règle SPF demande au serveur de messagerie de réception d'accepter uniquement les messages provenant de ces adresses IP pour le domaine contoso.com :

- Adresse IP 1

- Adresse IP 2

- Adresse IP 3

This SPF rule tells the receiving email server that if a message comes from contoso.com, but not from one of these three IP addresses, the receiving server should apply the enforcement rule to the message. The enforcement rule is usually one of these options:

- **Hard fail.** Mark the message with 'hard fail' in the message envelope and then follow the receiving server's configured spam policy for this type of message.

- **Échec partiel.** Marquez « échec partiel » dans l'enveloppe du message. En règle générale, les serveurs de messagerie sont configurés pour remettre ce type de message. La plupart des utilisateurs finaux ne voient pas cette marque.

- **Neutre.** Ne faites rien, autrement dit, ne marquez pas l’enveloppe du message. Il est réservé à des fins de test et rarement utilisé.

The following examples show how SPF works in different situations. In these examples, contoso.com is the sender and woodgrovebank.com is the receiver.

### <a name="example-1-email-authentication-of-a-message-sent-directly-from-sender-to-receiver"></a>Exemple 1 : authentification de messagerie d’un message envoyé directement de l’expéditeur au destinataire
<a name="spfExample1"> </a>

SPF fonctionne de manière optimale lorsque le chemin entre l'expéditeur et le destinataire est direct, par exemple :

![Diagramme illustrant comment SPF authentifie le courrier électronique lorsqu'il est envoyé directement d'un serveur à l'autre.](../../media/835c20a7-ed4c-49c4-91fe-b8ebb3e452a1.jpg)

Quand woodgrovebank.com reçoit le message, si l'adresse IP 1 se trouve dans l'enregistrement TXT SPF pour contoso.com, le message passe la vérification SPF et est authentifié.

### <a name="example-2-spoofed-sender-address-fails-the-spf-check"></a>Exemple 2 : l’adresse d’expéditeur falsifiée ne passe pas la vérification SPF
<a name="spfExample2"> </a>

Supposons qu'un auteur de hameçonnage trouve un moyen d'usurper contoso.com :

![Diagramme illustrant la façon dont SPF authentifie le courrier électronique envoyé à partir d'un serveur falsifié.](../../media/235dac3d-cdc5-466e-86e0-37b5979de198.jpg)

Étant donné que l’adresse IP n°12 n’est pas dans l’enregistrement TXT SPF de contoso.com, le message échoue à la vérification SPF et le destinataire peut choisir de le marquer comme courrier indésirable.

### <a name="example-3-spf-and-forwarded-messages"></a>Exemple 3 : messages transférés et SPF
<a name="spfExample3"> </a>

One drawback of SPF is that it doesn't work when an email has been forwarded. For example, suppose the user at woodgrovebank.com has set up a forwarding rule to send all email to an outlook.com account:

![Diagramme indiquant comment SPF ne peut pas authentifier le courrier électronique lorsque le message est transféré.](../../media/6e92acd6-463e-4a1b-8327-fb1cf861f356.jpg)

Le message passe à l’origine la vérification SPF à woodgrovebank.com, mais il échoue à la vérification SPF à outlook.com, car IP #25 n’est pas dans l’enregistrement TXT SPF de contoso.com. Outlook.com peut ensuite marquer le message comme courrier indésirable. Pour contourner ce problème, utilisez SPF avec d’autres méthodes d’authentification par e-mail telles que DKIM et DMARC.

### <a name="spf-basics-including-third-party-domains-that-can-send-mail-on-behalf-of-your-domain"></a>Concepts de base SPF : intégration de domaines tiers pouvant envoyer des messages au nom de votre domaine
<a name="SPFBasicsIncludes"> </a>

En plus des adresses IP, vous pouvez également configurer votre enregistrement TXT SPF pour inclure des domaines en tant qu'expéditeurs. Ces domaines sont ajoutés à l'enregistrement TXT SPF comme des instructions « Include ». Par exemple, contoso.com souhaiterez peut-être inclure toutes les adresses IP des serveurs de messagerie à partir de contoso.net et de contoso.org, qu’il possède également. Pour ce faire, contoso.com publie un enregistrement TXT SPF qui ressemble à ceci :

```text
v=spf1 include:contoso.net include:contoso.org -all
```

Lorsque le serveur de réception voit cet enregistrement dans DNS, il effectue également une recherche DNS sur l’enregistrement TXT SPF pour contoso.net, puis pour contoso.org. S’il trouve une autre instruction Include dans les enregistrements pour contoso.net ou contoso.org, il les suit également. Afin d’empêcher le refus d’attaque de service, le nombre maximal de recherches DNS pour un seul message est de 10. Chaque instruction Include représente une recherche DNS supplémentaire. Si un message dépasse la limite de 10, le message échoue lors de la vérification SPF. Une fois qu’un message atteint cette limite, selon la façon dont le serveur de réception est configuré, l’expéditeur peut obtenir un message indiquant que le message a généré « trop de recherches » ou que le « nombre maximal de sauts pour le message a été dépassé » (ce qui peut se produire lorsque la boucle de recherche et dépasse le délai d’expiration DNS). Pour obtenir des conseils sur la façon d’éviter cela, consultez [Résolution des problèmes : Meilleures pratiques pour SPF dans Microsoft 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="requirements-for-your-spf-txt-record-and-microsoft-365"></a>Configuration requise pour votre enregistrement TXT SPF et Microsoft 365
<a name="SPFReqsinO365"> </a>

Si vous configurez le courrier lorsque vous configurez Microsoft 365, vous avez déjà créé un enregistrement TXT SPF qui identifie les serveurs de messagerie Microsoft comme une source légitime de courrier pour votre domaine. Cet enregistrement ressemble probablement à ce qui suit :

```text
v=spf1 include:spf.protection.outlook.com -all
```

Si vous êtes un client entièrement hébergé, c’est-à-dire que vous n’avez pas de serveurs de messagerie locaux qui envoient des messages sortants, il s’agit du seul enregistrement TXT SPF que vous devez publier pour Office 365.

Si vous disposez d’un déploiement hybride (c’est-à-dire que vous avez des boîtes aux lettres locales et d’autres hébergées dans Microsoft 365), ou si vous êtes un client autonome Exchange Online Protection (EOP) (autrement dit, votre organisation utilise EOP pour protéger vos boîtes aux lettres locales), vous devez ajouter l’adresse IP sortante de chacun de vos serveurs de messagerie de périphérie locaux à l’enregistrement TXT SPF dans DNS.

## <a name="form-your-spf-txt-record-for-microsoft-365"></a>Former votre enregistrement TXT SPF pour Microsoft 365
<a name="FormYourSPF"> </a>

Utilisez les informations de syntaxe de cet article afin de formuler l'enregistrement TXT SPF pour votre domaine personnalisé. Bien qu'il existe des options de syntaxe qui ne sont pas mentionnées ici, il s'agit des options les plus fréquemment utilisées. Une fois que vous avez formé votre enregistrement, vous devez mettre à jour l’enregistrement auprès de votre registraire de domaine.

Pour plus d’informations sur les domaines que vous devez inclure pour Microsoft 365, consultez [les enregistrements DNS externes requis pour SPF](../../enterprise/external-domain-name-system-records.md). Utilisez les [instructions pas à pas](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md#add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online) pour mettre à jour les enregistrements SPF (TXT) dans votre bureau d'enregistrement de domaines.

### <a name="spf-txt-record-syntax-for-microsoft-365"></a>Syntaxe d’enregistrement TXT SPF pour Microsoft 365
<a name="SPFSyntaxO365"> </a>

Un enregistrement TXT SPF standard pour Microsoft 365 a la syntaxe suivante :

```text
v=spf1 [<ip4>|<ip6>:<IP address>] [include:<domain name>] <enforcement rule>
```

Par exemple :

```text
v=spf1 ip4:192.168.0.1 ip4:192.168.0.2 include:spf.protection.outlook.com -all
```

où :

- **v=spf1** est obligatoire. Cet élément définit l'enregistrement TXT en tant qu'enregistrement TXT SPF.

- **ip4** indique que vous utilisez des adresses IP version 4. **ip6** indique que vous utilisez des adresses IP version 6. Si vous utilisez des adresses IP IPv6, remplacez **ip4** par **ip6** dans les exemples de cet article. Vous pouvez également spécifier des plages d'adresses IP à l'aide de la notation CIDR, par exemple **ip4:192.168.0.1/26**.

- _IP address_ est l'adresse IP à ajouter à l'enregistrement TXT SPF. En règle générale, il s'agit de l'adresse IP du serveur de messagerie sortant pour votre organisation. Vous pouvez répertorier plusieurs serveurs de messagerie sortants. Pour plus d’informations, consultez [Exemple : Enregistrement TXT SPF pour plusieurs serveurs de messagerie locaux sortants et Microsoft 365](how-office-365-uses-spf-to-prevent-spoofing.md#ExampleSPFMultipleMailServerO365).

- _domain name_ est le domaine que vous souhaitez ajouter en tant qu'expéditeur légitime. Pour obtenir la liste des noms de domaine que vous devez inclure pour Microsoft 365, consultez [les enregistrements DNS externes requis pour SPF](../../enterprise/external-domain-name-system-records.md).

- La règle de mise en œuvre est généralement l'une des règles suivantes :

  - -all

    Indique un échec sévère. Si vous connaissez toutes les adresses IP autorisées pour votre domaine, répertoriez-les dans l’enregistrement TXT SPF et utilisez le qualificateur -all (échec dur). En outre, si vous utilisez uniquement SPF, c’est-à-dire que vous n’utilisez pas DMARC ou DKIM, vous devez utiliser le qualificateur -all. Nous vous recommandons de toujours utiliser ce qualificateur.

  - ~all

    Indique un échec partiel. Si vous n'êtes pas sûr de disposer de la liste complète des adresses IP, utilisez le qualificateur ~all (échec partiel). En outre, si vous utilisez DMARC avec p=quarantine ou p=reject, vous pouvez utiliser ~all. Dans le cas contraire, utilisez -all.

  - ?all

    Indique un résultat neutre. Il est utilisé lors des essais SPF. Nous vous déconseillons d’utiliser ce qualificateur dans votre déploiement en direct.

### <a name="example-spf-txt-record-to-use-when-all-of-your-mail-is-sent-by-microsoft-365"></a>Exemple : enregistrement TXT SPF à utiliser lorsque tout votre courrier est envoyé par Microsoft 365
<a name="ExampleSPFNoSP"> </a>

Si tout votre courrier est envoyé par Microsoft 365, utilisez-le dans votre enregistrement TXT SPF :

```text
v=spf1 include:spf.protection.outlook.com -all
```

### <a name="example-spf-txt-record-for-a-hybrid-scenario-with-one-on-premises-exchange-server-and-microsoft-365"></a>Exemple : enregistrement TXT SPF pour un scénario hybride avec un Exchange Server local et Microsoft 365
<a name="ExampleSPFHybridOneExchangeServer"> </a>

Dans un environnement hybride, si l'adresse IP du serveur Exchange local est 192.168.0.1, afin de définir la règle de mise en œuvre SPF sur échec sévère, formez l'enregistrement TXT SPF comme suit :

```text
v=spf1 ip4:192.168.0.1 include:spf.protection.outlook.com -all
```

### <a name="example-spf-txt-record-for-multiple-outbound-on-premises-mail-servers-and-microsoft-365"></a>Exemple : enregistrement TXT SPF pour plusieurs serveurs de messagerie locaux sortants et Microsoft 365
<a name="ExampleSPFMultipleMailServerO365"> </a>

If you have multiple outbound mail servers, include the IP address for each mail server in the SPF TXT record and separate each IP address with a space followed by an "ip4:" statement. For example:

```text
v=spf1 ip4:192.168.0.1 ip4:192.168.0.2 ip4:192.168.0.3 include:spf.protection.outlook.com -all
```

## <a name="next-steps-set-up-spf-for-microsoft-365"></a>Étapes suivantes : Configurer SPF pour Microsoft 365
<a name="SPFNextSteps"> </a>

Une fois que vous avez formulé votre enregistrement TXT SPF, suivez les étapes de [configuration de SPF dans Microsoft 365 pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md) de l’ajouter à votre domaine.

Bien que SPF soit conçu pour empêcher l’usurpation d’identité, il existe des techniques d’usurpation d’identité contre lesquelles SPF ne peut pas se protéger. Pour vous protéger contre ces éléments, une fois que vous avez configuré SPF, vous devez également configurer DKIM et DMARC pour Microsoft 365. Pour commencer, consultez [Utiliser DKIM pour valider les e-mails sortants envoyés à partir de votre domaine personnalisé dans Microsoft 365](use-dkim-to-validate-outbound-email.md). Ensuite, consultez la rubrique [Utiliser DMARC pour valider les e-mails dans Microsoft 365](use-dmarc-to-validate-email.md).

## <a name="troubleshooting-best-practices-for-spf-in-microsoft-365"></a>Résolution des problèmes : Meilleures pratiques pour SPF dans Microsoft 365
<a name="SPFTroubleshoot"> </a>

You can only create one SPF TXT record for your custom domain. Creating multiple records causes a round robin situation and SPF will fail. To avoid this, you can create separate records for each subdomain. For example, create one record for contoso.com and another record for bulkmail.contoso.com.

Si un e-mail provoque plus de 10 recherches DNS avant sa remise, le serveur de messagerie de réception répond avec une erreur permanente, également appelée  _permerreur_, et provoque l’échec de la vérification SPF. Le serveur de réception peut également répondre avec une notification d'échec de remise qui contient une erreur semblable à celles-ci :

- Le message a dépassé le nombre de sauts.

- Le message a demandé trop de recherches.

## <a name="avoiding-the-too-many-lookups-error-when-you-use-third-party-domains-with-microsoft-365"></a>Éviter l’erreur « trop de recherches » lorsque vous utilisez des domaines tiers avec Microsoft 365
<a name="SPFTroubleshoot"> </a>

Some SPF TXT records for third-party domains direct the receiving server to perform a large number of DNS lookups. For example, at the time of this writing, Salesforce.com contains 5 include statements in its record:

```text
v=spf1 include:_spf.google.com
include:_spfblock.salesforce.com
include:_qa.salesforce.com
include:_spfblock1.salesforce.com
include:spf.mandrillapp.com mx ~all
```

To avoid the error, you can implement a policy where anyone sending bulk email, for example, has to use a subdomain specifically for this purpose. You then define a different SPF TXT record for the subdomain that includes the bulk email.

 In some cases, like the salesforce.com example, you have to use the domain in your SPF TXT record, but in other cases, the third-party may have already created a subdomain for you to use for this purpose. For example, exacttarget.com has created a subdomain that you need to use for your SPF TXT record:

```text
cust-spf.exacttarget.com
```

Lorsque vous incluez des domaines tiers dans votre enregistrement TXT SPF, vous devez vérifier auprès du tiers le domaine ou le sous-domaine à utiliser pour éviter d’atteindre la limite de 10 recherches.

## <a name="how-to-view-your-current-spf-txt-record-and-determine-the-number-of-lookups-that-it-requires"></a>Comment afficher votre enregistrement TXT SPF et déterminer le nombre de recherches nécessaires
<a name="SPFTroubleshoot"> </a>

Vous pouvez utiliser nslookup pour afficher vos enregistrements DNS, y compris votre enregistrement TXT SPF. Vous pouvez utiliser de nombreux outils en ligne gratuits pour afficher le contenu de votre enregistrement TXT SPF. En consultant votre enregistrement TXT SPF et en suivant la chaîne d'instructions Include et de redirections, vous pouvez déterminer le nombre de recherches DNS dont l'enregistrement a besoin. Certains outils en ligne peuvent même compter et afficher ces recherches pour vous. Le suivi de ce nombre permet d’empêcher les messages envoyés par votre organisation de déclencher une erreur permanente, appelée erreur de perm, à partir du serveur de réception.

## <a name="for-more-information"></a>Pour plus d'informations
<a name="SPFTroubleshoot"> </a>

Vous avez besoin d’aide pour ajouter l’enregistrement TXT SPF ? Lisez l’article [Créer des enregistrements DNS dans n’importe quel fournisseur d’hébergement DNS pour Microsoft 365 pour](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md#add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online) obtenir des informations détaillées sur l’utilisation de Sender Policy Framework avec votre domaine personnalisé dans Microsoft 365. [Les en-têtes de messages anti-courrier indésirable](anti-spam-message-headers.md) incluent les champs de syntaxe et d’en-tête utilisés par Microsoft 365 pour les vérifications SPF.
