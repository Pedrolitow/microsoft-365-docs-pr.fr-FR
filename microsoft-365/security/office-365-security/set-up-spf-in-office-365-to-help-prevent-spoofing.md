---
title: Configurer SPF pour empêcher l’usurpation
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/21/2019
audience: ITPro
ms.topic: how-to
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 71373291-83d2-466f-86ea-fc61493743a6
ms.collection:
- m365-security
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment mettre à jour un enregistrement DNS (service de nom de domaine) afin que vous puissiez utiliser SPF (Sender Policy Framework) avec votre domaine personnalisé dans Office 365.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 506e23b7dd3441da49fdd48b6772eb280caafd70
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68072214"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>Configurer SPF pour empêcher l’usurpation

- [Conditions préalables](#prerequisites)
- [Ajouter ou mettre à jour votre enregistrement TXT SPF](#create-or-update-your-spf-txt-record)
- [Comment gérer les sous-domaines ?](#how-to-handle-subdomains)
- [Résolution des problèmes SPF](#troubleshooting-spf)

<!--
[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Applies to**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 and plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
-->

Cet article vous explique comment mettre à jour un enregistrement DNS (Domain Name Service) afin que vous puissiez utiliser l’authentification de messagerie SPF (Sender Policy Framework) avec votre domaine personnalisé dans Office 365.

Le SPF permet de *valider* les messages sortants envoyés à partir de votre domaine personnalisé (provenant de la personne qui la dit). Il s’agit d’une première étape de la configuration des méthodes d’authentification complètes recommandées pour le courrier électronique de SPF, [DKIM](use-dkim-to-validate-outbound-email.md)et [DMARC](use-dmarc-to-validate-email.md).

- [Conditions préalables](#prerequisites)
- [Ajouter ou mettre à jour votre enregistrement TXT SPF](#create-or-update-your-spf-txt-record)
  - [Comment gérer les sous-domaines ?](#how-to-handle-subdomains)
- [Comment fonctionne l’authentification de messagerie SPF ?](#what-does-spf-email-authentication-actually-do)
  - [Résolution des problèmes SPF](#troubleshooting-spf)
- [En savoir plus sur SPF](#more-information-about-spf)

## <a name="prerequisites"></a>Configuration requise

> [!IMPORTANT]
> Si vous êtes une **petite entreprise** ou que vous ne connaissez pas les adresses IP ou la configuration DNS, appelez votre bureau d’enregistrement de domaines Internet (par exemple GoDaddy, Bluehost, web.com) et demander de l’aide sur la *configuration DNS de SPF* (et toute autre méthode d’authentification des e-mails) . <p> **Si vous n'utilisez pas d'URL personnalisé** (et que l’URL utilisée pour Office 365 se termine par **onmicrosoft.com**), SPF a déjà été installé pour vous dans le service Office 365.

C’est parti !

L’enregistrement TXT SPF pour Office 365 sera effectué dans le DNS externe pour tous les domaines ou sous-domaines personnalisés. Vous avez besoin d’informations pour effectuer l’enregistrement. Collectez les informations ci-dessous :

- The SPF TXT record for your custom domain, if one exists. For instructions, see [Gather the information you need to create Office 365 DNS records](../../admin/get-help-with-domains/information-for-dns-records.md).

- Go to your messaging server(s) and find out the External IP addresses (needed from all on-premises messaging servers). For example, **131.107.2.200**.

- Domain names to use for all third-party domains that you need to include in your SPF TXT record. Some bulk mail providers have set up subdomains to use for their customers. For example, the company MailChimp has set up **servers.mcsv.net**.

- Figure out what enforcement rule you want to use for your SPF TXT record. The **-all** rule is recommended. For detailed information about other syntax options, see [SPF TXT record syntax for Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365).

> [!IMPORTANT]
> Afin d'utiliser un domaine personnalisé, Office 365 exige que vous ajoutiez un enregistrement TXT SPF (Sender Policy Framework) à votre enregistrement DNS pour éviter l'usurpation.

## <a name="create-or-update-your-spf-txt-record"></a>Ajouter ou mettre à jour votre enregistrement TXT SPF

1. Assurez-vous que vous connaissez la syntaxe SPF du tableau suivant.

    |Élément|Si vous utilisez...|Courant pour les utilisateurs ?|Ajoutez l’élément suivant...|
    |---|---|---|---|
    |1|Un système de messagerie (obligatoire)|Common. All SPF TXT records start with this value|`v=spf1`|
    |2|Exchange Online|Courant|`include:spf.protection.outlook.com`|
    |3|Exchange Online dédié uniquement|Non courant|`ip4:23.103.224.0/19` <br> `ip4:206.191.224.0/19` <br> `ip4:40.103.0.0/16` <br> `include:spf.protection.outlook.com`|
    |4|Office 365 Germany, Microsoft Cloud Germany uniquement|Non courant|`include:spf.protection.outlook.de`|
    |5|Système de messagerie tiers|Non courant|`include:<domain_name>` <p> \<domain_name\> est le domaine du système de messagerie tiers.|
    |6|On-premises email system. For example, Exchange Online Protection plus another email system|Non courant|Utilisez l’un des éléments suivants pour chaque système de messagerie supplémentaire : <p> `ip4:<IP_address>` <br> `ip6:<IP_address>` <br> `include:<domain_name>` <p> \<IP_address\> et \<domain_name\> sont l’adresse IP et le domaine de l’autre système de messagerie qui envoie des e-mails au nom de votre domaine.|
    |7 |Un système de messagerie (obligatoire)|Common. All SPF TXT records end with this value|`<enforcement rule>` <p> This can be one of several values. We recommend the value `-all`.|

2. Si vous ne l’avez pas encore fait, créez votre enregistrement TXT SPF à l’aide de la syntaxe du tableau.

   Par exemple, si vous êtes entièrement hébergé par Office 365, ce qui signifie que vous n’avez aucun serveur de messagerie local, votre enregistrement TXT SPF inclut les lignes 1, 2 et 7 et se présente comme suit :

   ```text
   v=spf1 include:spf.protection.outlook.com -all
   ```

   **The example above is the most common SPF TXT record**. This record works for just about everyone, regardless of whether your Microsoft datacenter is located in the United States, or in Europe (including Germany), or in another location.

   However, if you bought Office 365 Germany, part of Microsoft Cloud Germany, you should use the include statement from line 4 instead of line 2. For example, if you are hosted entirely in Office 365 Germany, that is, you have no on-premises mail servers, your SPF TXT record would include rows 1, 4, and 7 and would look like this:

   ```text
   v=spf1 include:spf.protection.outlook.de -all
   ```

   If you're already deployed in Office 365 and have set up your SPF TXT records for your custom domain, and you're migrating to Office 365 Germany, you need to update your SPF TXT record. To do this, change `include:spf.protection.outlook.com` to `include:spf.protection.outlook.de`.

3. Once you have formed your SPF TXT record, you need to update the record in DNS. **You can only have one SPF TXT record for a domain.** If an SPF TXT record exists, instead of adding a new record, you need to update the existing record. Go to [Create DNS records for Office 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md), and then select the link for your DNS host.

4. Testez votre enregistrement TXT SPF.

## <a name="how-to-handle-subdomains"></a>Comment gérer les sous-domaines ?

Il est important de noter que *vous devez créer un enregistrement distinct pour chaque sous-domaine, car les sous-domaines n’héritent pas de l’enregistrement SPF de leur domaine de premier niveau*.

A wildcard SPF record (`*.`) is required for every domain and subdomain to prevent attackers from sending email claiming to be from non-existent subdomains. For example:

```text
*.subdomain.contoso.com. IN TXT "v=spf1 -all"
```

## <a name="troubleshooting-spf"></a>Résolution des problèmes SPF

Having trouble with your SPF TXT record? Read [Troubleshooting: Best practices for SPF in Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="what-does-spf-email-authentication-actually-do"></a>Comment fonctionne l’authentification de messagerie SPF ?

SPF identifies which mail servers are allowed to send mail on your behalf. Basically, SPF, along with DKIM, DMARC, and other technologies supported by Office 365, help prevent spoofing and phishing. SPF is added as a TXT record that is used by DNS to identify which mail servers can send mail on behalf of your custom domain. Recipient mail systems refer to the SPF TXT record to determine whether a message from your custom domain comes from an authorized messaging server.

For example, let's say that your custom domain contoso.com uses Office 365. You add an SPF TXT record that lists the Office 365 messaging servers as legitimate mail servers for your domain. When the receiving messaging server gets a message from joe@contoso.com, the server looks up the SPF TXT record for contoso.com and finds out whether the message is valid. If the receiving server finds out that the message comes from a server other than the Office 365 messaging servers listed in the SPF record, the receiving mail server can choose to reject the message as spam.

Also, if your custom domain does not have an SPF TXT record, some receiving servers may reject the message outright. This is because the receiving server cannot validate that the message comes from an authorized messaging server.

If you've already set up mail for Office 365, then you have already included Microsoft's messaging servers in DNS as an SPF TXT record. However, there are some cases where you may need to update your SPF TXT record in DNS. For example:

- Previously, you had to add a different SPF TXT record to your custom domain if you were using SharePoint Online. This is no longer required. This change should reduce the risk of SharePoint Online notification messages ending up in the Junk Email folder. Update your SPF TXT record if you are hitting the 10 lookup limit and receiving errors that say things like, "exceeded the lookup limit" and "too many hops".

- Vous avez un environnement hybride avec Office 365 et Exchange en local.

- Vous avez l’intention de configurer DKIM et DMARC (recommandé).

## <a name="more-information-about-spf"></a>En savoir plus sur SPF

Pour obtenir des exemples avancés, des informations plus détaillées sur la syntaxe SPF prise en charge, l’usurpation, la résolution des problèmes et la façon dont Office 365 prend en charge SPF, voir la section [Fonctionnement de SPF pour éviter l’usurpation et le hameçonnage dans Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

## <a name="next-steps-dkim-and-dmarc"></a>Étapes suivantes : DKIM et DMARC

 SPF est conçu pour lutter contre l’usurpation, mais il existe des techniques d’usurpation contre lesquelles SPF ne peut rien faire. Pour vous protéger contre ces techniques, une fois que vous avez configuré SPF, vous devez également configurer DKIM et DMARC pour Office 365.

L’objectif de l’authentification de messagerie [**DKIM**](use-dkim-to-validate-outbound-email.md) est de prouver que le contenu du courrier n’a pas été falsifié.

L’objectif de l’authentification de messagerie [**DMARC**](use-dmarc-to-validate-email.md) est de vérifier que les informations SPF et DKIM correspondent à l’adresse de l’expéditeur.

 Si vous souhaitez obtenir des exemples avancés et des informations plus détaillées sur la syntaxe SPF prise en charge, consultez l’article [Fonctionnement de SPF contre l’usurpation et l’hameçonnage dans Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

[Utiliser des expéditeurs ARC approuvés pour les flux de messagerie légitimes](/microsoft-365/security/office-365-security/use-arc-exceptions-to-mark-trusted-arc-senders)

*Sélectionnez « Cette page » sous « Commentaires » si vous avez des commentaires sur cette documentation.*
