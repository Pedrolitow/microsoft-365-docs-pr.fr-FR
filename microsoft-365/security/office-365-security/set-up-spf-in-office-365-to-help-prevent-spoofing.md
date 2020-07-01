---
title: Configurer SPF pour empêcher l’usurpation
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 71373291-83d2-466f-86ea-fc61493743a6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment mettre à jour un enregistrement DNS (service de nom de domaine) afin que vous puissiez utiliser SPF (Sender Policy Framework) avec votre domaine personnalisé dans Office 365.
ms.openlocfilehash: 93356799967932813252e7db27e7ac796e46cbc6
ms.sourcegitcommit: c43ebb915fa0eb7eb720b21b62c0d1e58e7cde3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "44936936"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>Configurer SPF pour empêcher l’usurpation

 **Summary:** This article describes how to update a Domain Name Service (DNS) record so that you can use Sender Policy Framework (SPF) with your custom domain in Office 365. Using SPF helps to validate outbound email sent from your custom domain.

In order to use a custom domain, Office 365 requires that you add a Sender Policy Framework (SPF) TXT record to your DNS record to help prevent spoofing. SPF identifies which mail servers are allowed to send mail on your behalf. Basically, SPF, along with DKIM, DMARC, and other technologies supported by Office 365, help prevent spoofing and phishing. SPF is added as a TXT record that is used by DNS to identify which mail servers can send mail on behalf of your custom domain. Recipient mail systems refer to the SPF TXT record to determine whether a message from your custom domain comes from an authorized messaging server.

For example, let's say that your custom domain contoso.com uses Office 365. You add an SPF TXT record that lists the Office 365 messaging servers as legitimate mail servers for your domain. When the receiving messaging server gets a message from joe@contoso.com, the server looks up the SPF TXT record for contoso.com and finds out whether the message is valid. If the receiving server finds out that the message comes from a server other than the Office 365 messaging servers listed in the SPF record, the receiving mail server can choose to reject the message as spam.

Also, if your custom domain does not have an SPF TXT record, some receiving servers may reject the message outright. This is because the receiving server cannot validate that the message comes from an authorized messaging server.

If you've already set up mail for Office 365, then you have already included Microsoft's messaging servers in DNS as an SPF TXT record. However, there are some cases where you may need to update your SPF TXT record in DNS. For example:

- Previously, you had to add a different SPF TXT record to your custom domain if you were using SharePoint Online. This is no longer required. This change should reduce the risk of SharePoint Online notification messages ending up in the Junk Email folder. Update your SPF TXT record if you are hitting the 10 lookup limit and receiving errors that say things like, "exceeded the lookup limit" and "too many hops".

- Vous avez un environnement hybride avec Office 365 et Exchange en local.

- Vous avez l’intention de configurer DKIM et DMARC (recommandé).

## <a name="updating-your-spf-txt-record-for-office-365"></a>Mise à jour de votre enregistrement TXT SPF pour Office 365

Before you update the TXT record in DNS, you need to gather some information and determine the format of the record. This will help prevent you from generating DNS errors. For advanced examples and a more detailed discussion about supported SPF syntax, see [How SPF works to prevent spoofing and phishing in Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

Collectez les informations ci-dessous :

- The current SPF TXT record for your custom domain. For instructions, see [Gather the information you need to create Office 365 DNS records](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/information-for-dns-records).

- External IP addresses of all on-premises messaging servers. For example, **131.107.2.200**.

- Domain names to use for all third-party domains that you need to include in your SPF TXT record. Some bulk mail providers have set up subdomains to use for their customers. For example, the company MailChimp has set up **servers.mcsv.net**.

- Determine what enforcement rule you want to use for your SPF TXT record. We recommend **-all**. For detailed information about other syntax options, see [SPF TXT record syntax for Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365).

### <a name="to-add-or-update-your-spf-txt-record"></a>Pour ajouter ou mettre à jour votre enregistrement TXT SPF

1. Assurez-vous que vous connaissez la syntaxe SPF du tableau suivant.

   ||**Si vous utilisez...**|**Courant pour les utilisateurs ?**|**Ajoutez l'élément suivant...**|
   |:-----|:-----|:-----|:-----|
   |1|Un système de messagerie (obligatoire)|Common. All SPF TXT records start with this value|v=spf1|
   |2|Exchange Online|Courant|include:spf.protection.outlook.com|
   |3|Exchange Online dédié uniquement|Non courant|ip4:23.103.224.0/19 ip4:206.191.224.0/19 ip4:40.103.0.0/16 include:spf.protection.outlook.com|
   |4|Office 365 Germany, Microsoft Cloud Germany uniquement|Non courant|include:spf.protection.outlook.de|
   |5|Système de messagerie tiers|Non courant|Incluez : \<domain name\>  <br/> Où <nom du domaine> est le nom de domaine du système de messagerie tiers.|
   |6|On-premises mail system. For example, Exchange Online Protection plus another mail system|Non courant| Utilisez l’un des éléments suivants pour chaque système de messagerie supplémentaire : <br> IP4 : \<_IP address_\>  <br/>  ip6 : \<_IP address_\>  <br/>  Incluez : \<_domain name_\>  <br/>  Où la valeur de l’élément \<_IP address_\> est l’adresse IP de l’autre système de messagerie et \<_domain name_\> correspond au nom de domaine de l’autre système de messagerie qui envoie un message au nom de votre domaine.|
   |7|Un système de messagerie (obligatoire)|Common. All SPF TXT records end with this value|\<_enforcement rule_\>  <br/> This can be one of several values. We recommend that you use **-all**.|

2. Si vous ne l’avez pas encore fait, créez votre enregistrement TXT SPF à l’aide de la syntaxe du tableau :

   Par exemple, si vous êtes entièrement hébergé par Office 365, ce qui signifie que vous n’avez aucun serveur de messagerie local, votre enregistrement TXT SPF inclut les lignes 1, 2 et 7 et se présente comme suit :

   `v=spf1 include:spf.protection.outlook.com -all`

   Il s’agit de l’enregistrement TXT SPF le plus courant. Cet enregistrement fonctionne pratiquement dans tous les cas, peu importe que votre centre de données Microsoft se trouve aux États-Unis, en Europe (y compris en Allemagne) ou dans une autre région.

   However, if you have purchased Office 365 Germany, part of Microsoft Cloud Germany, you should use the include statement from line 4 instead of line 2. For example, if you are fully-hosted in Office 365 Germany, that is, you have no on-premises mail servers, your SPF TXT record would include rows 1, 4, and 7 and would look like this:

   `v=spf1 include:spf.protection.outlook.de -all`

   Si vous avez déjà effectué un déploiement dans Office 365, que vous avez configuré les enregistrements TXT SPF de votre domaine personnalisé et que vous effectuez une migration vers Office 365 Germany, vous devez mettre à jour votre enregistrement TXT SPF. Pour ce faire, remplacez **include:spf.protection.outlook.com** par **include.spf.protection.outlook.de**.

3. Une fois que vous avez formulé votre enregistrement TXT SPF, vous devez mettre à jour l'enregistrement dans le système DNS. Vous ne pouvez avoir qu'un seul enregistrement TXT SPF pour un domaine. Si un enregistrement TXT SPF existe, au lieu d'ajouter un nouvel enregistrement, vous devez mettre à jour l'enregistrement existant. Accédez à [Créer des enregistrements DNS pour Office 365](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider), puis cliquez sur le lien correspondant à votre hôte DNS.

4. Testez votre enregistrement TXT SPF.

## <a name="more-information-about-spf"></a>En savoir plus sur SPF

Pour obtenir des exemples avancés, des informations plus détaillées sur la syntaxe SPF prise en charge, l’usurpation, la résolution des problèmes et la façon dont Office 365 prend en charge SPF, voir la section [Fonctionnement de SPF pour éviter l’usurpation et le hameçonnage dans Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

## <a name="next-steps-after-you-set-up-spf-for-office-365"></a>Étapes suivantes : après avoir configuré SPF pour Office 365

Having trouble with your SPF TXT record? Read [Troubleshooting: Best practices for SPF in Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

 SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against. In order to protect against these, once you have set up SPF, you should also configure DKIM and DMARC for Office 365. To get started, see [Use DKIM to validate outbound email sent from your custom domain in Office 365](use-dkim-to-validate-outbound-email.md). Next, see [Use DMARC to validate email in Office 365](use-dmarc-to-validate-email.md).
