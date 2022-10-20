---
title: Enregistrements DNS externes pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 10/14/2022
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- scotvorg
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: Liste de références des enregistrements système de nom de domaine externe à utiliser lorsque vous planifiez d’un déploiement Office 365.
ms.openlocfilehash: d81ae7c1633e4860fa3c3528f87216150b435993
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68630619"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Enregistrements DNS externes pour Office 365

![Domain.](../media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)

**Want to see a customized list of DNS records for your Office 365 organization?** You can [find the info you need to create Office 365 DNS records](../admin/get-help-with-domains/information-for-dns-records.md) for your domain in Office 365.

**Need step-by-step help to add these records at your domain's DNS host, such as GoDaddy or eNom?** [Find links to step-by-step instructions for many popular DNS hosts](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**Sticking around to use the reference list for your own custom deployment?** The below list should be used as a reference for your custom Office 365 deployment. You will need to select which records apply to your organization and fill in the appropriate values.

**Retournez sur**[ planification réseau et optimisation des performances pour Office 365](./network-planning-and-performance.md).

Often the SPF and MX records are the hardest to figure out. We've updated our SPF records guidance at the end of this article. The important thing to remember is that _you can only have a single SPF record for your domain_. You can have multiple MX records; however, that can cause problems for mail delivery. Having a single MX record that directs email to one mail system removes many potential problems.

The sections below are organized by service in Office 365. To see a customized list of the Office 365 DNS records for your domain, sign in to Office 365 and [Gather the information you need to create Office 365 DNS records](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).

## <a name="external-dns-records-required-for-office-365-core-services"></a>Enregistrements DNS externes requis pour Office 365 (services principaux) :
<a name="BKMK_ReqdCore"> </a>

L’enregistrement TXT est nécessaire pour prouver que vous êtes propriétaire du domaine et qu’il est requis pour tous les clients.

L’enregistrement CNAME est uniquement requis pour les clients utilisant [Office 365 géré par 21Vianet](/microsoft-365/admin/services-in-china/services-in-china). Il garantit qu'Office 365 peut diriger les postes de travail pour s'authentifier avec la plateforme d'identité appropriée.

|Enregistrement DNS|Objectif|Valeur à utiliser|S’applique à|
|---|---|---|---|
|**TXT** <br/> **(Vérification du domaine)**|Used by Office 365 to verify only that you own your domain. It doesn't affect anything else.|**Hôte :** @ (ou de certains fournisseurs d’hébergement DNS, votre nom de domaine) <br/> **Valeur TXT :** _une chaîne de texte fournie par_ Office 365 <br/> L’Assistant de **configuration de domaine** Office 365 fournit les valeurs à utiliser pour créer cet enregistrement.|Tous les clients|
|**CNAME** <br/> **(Suite)**|Utilisé par Office 365 pour diriger l’authentification vers la plateforme d’identités appropriée. [Plus d’informations](../admin/services-in-china/purpose-of-cname.md?viewFallbackFrom=o365-worldwide) <br/> **Remarque** cette CNAME s’applique uniquement à Office 365 géré par 21Vianet. S’il est présent et que votre Office 365 n’est pas géré par 21Vianet, les utilisateurs de votre domaine personnalisé obtiennent une erreur « *un domaine personnalisé* n’est pas dans notre système » et ne peuvent pas activer leur licence Office 365. [Plus d’informations](/office365/servicedescriptions/office-365-platform-service-description/office-365-operated-by-21vianet) |**Alias :** msoID <br/> **Cible :** clientconfig.partner.microsoftonline-p.net.cn| Clients 21Vianet uniquement|

## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Enregistrements DNS externes requis pour la messagerie électronique dans Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Email in Office 365 requires several different records. The three primary records that all customers should use are the Autodiscover, MX, and SPF records.

- **L’enregistrement de découverte automatique** permet aux ordinateurs clients de rechercher automatiquement Exchange et de configurer correctement le client.

- **The MX record** tells other mail systems where to send email for your domain. **Note:** When you change your email to Office 365, by updating your domain's MX record, ALL email sent to that domain will start coming to Office 365.
Do you just want to switch a few email addresses to Office 365? You can [Pilot Office 365 with a few email addresses on your custom domain](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **The TXT record for SPF** is used by recipient email systems to validate that the server sending your email is one that you approve. This helps prevent problems like email spoofing and phishing. See the [External DNS records required for SPF](external-domain-name-system-records.md#BKMK_SPFrecords) in this article to help you understand what to include in your record.

Les clients email qui utilisent la fédération Exchange auront un enregistrement CNAME et TXT supplémentaire en bas de tableau.

|Enregistrement DNS|Objectif|Valeur à utiliser|
|---|---|---|
|**CNAME** <br/> **(Exchange Online)**|Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for users.|**Alias :** autodiscover <br/> **Cible :** autodiscover.outlook.com|
|**MX** <br/> **(Exchange Online)**|Envoie le courrier entrant pour votre domaine vers le service Exchange Online dans Office 365. <br/> **Remarque :** une fois le courrier électronique envoyé vers Exchange Online, vous devez supprimer les enregistrements MX qui pointent vers votre ancien système. |**Domaine :** par exemple, contoso.com <br/> **Serveur de courrier cible :**\<MX token\>.mail.protection.outlook.com <br/> **Valeur de temps de vie (TTL) :** 3600 <br/> **Préférence/priorité :** Inférieur à d’autres enregistrements MX (cela garantit que le courrier est remis à Exchange Online) : par exemple, 1 ou « faible » <br/> Trouvez votre \<MX token\> en procédant comme suit : <br/> Connectez-vous à Office 365, accédez à administrateur Office 365 \> domaines. <br/> Dans la colonne Action pour votre domaine, sélectionnez Corriger les problèmes. <br/> Dans la section Enregistrements MX, sélectionnez Que faut-il corriger ? <br/> Suivez les instructions de cette page pour mettre à jour votre enregistrement MX. <br/> [Quelle est la priorité MX ?](../admin/setup/domains-faq.yml)|
|**SPF (TXT)** <br/> **(Exchange Online)**|Helps to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.|[Enregistrements DNS externes requis pour SPF](external-domain-name-system-records.md#BKMK_SPFrecords)|
|**TXT** <br/> **(Fédération Exchange)**|Utilisé pour la fédération Exchange en cas de déploiement hybride.|**Enregistrement TXT 1 :** par exemple, contoso.com et texte associé personnalisé, texte de hachage de vérification de domaine associé généré de façon personnalisée (par exemple, Y96nu89138789315669824) <br/> **Enregistrement TXT 2 :** par exemple, exchangedelegation.contoso.com et le texte de hachage de vérification de domaine associé personnalisé (par exemple, Y3259071352452626169)|
|**CNAME** <br/> **(Fédération Exchange)**|Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service when your company is using Exchange federation. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for your users.|**Alias :** par exemple, Autodiscover.service.contoso.com <br/> **Cible :** autodiscover.outlook.com|

## <a name="external-dns-records-required-for-teams-and-skype-for-business-online"></a>Enregistrements DNS externes requis pour Teams et Skype Entreprise Online
<a name="BKMK_ReqdCore"> </a>

Il existe des étapes spécifiques à suivre lorsque vous utilisez [des URL Office 365 et des plages d’adresses IP](urls-and-ip-address-ranges.md) pour vous assurer que votre réseau est correctement configuré.

Ces enregistrements DNS s’appliquent à Teams, Skype Entreprise Online ou les deux comme indiqué.

|Enregistrement DNS|Objectif|Valeur à utiliser|
|---|---|---|
|**SRV** <br/> **(Teams et Skype Entreprise Online)**|Permet à votre domaine Office 365 de partager des fonctionnalités de messagerie instantanée avec des clients externes en activant la fédération SIP.|**Service** : sipfederationtls <br/> **Protocole :** TCP <br/> **Priorité :** 100 <br/> **Poids :** 1 <br/> **Port :** 5061 <br/> **Cible** : sipfed.online.lync.com <br/> **Remarque :** si le pare-feu ou le serveur proxy bloque les recherches SRV sur un DNS externe, vous devez ajouter cet enregistrement à l'enregistrement DNS interne. |
|**SRV** <br/> **(Teams et Skype Entreprise Online)**|Requis par Teams et Skype Entreprise Online pour communiquer entre Skype Entreprise localement, Teams et Skype Entreprise intercloud (par exemple, entre Office 365 @ _sipfed.online.lync.com_ et Office 365 géré par 21Vianet @ _sipfed.online.partner.lync.cn_ ou les clouds du gouvernement des États-Unis).<br/>Obligatoire en mode Teams uniquement et hybride. En mode Teams uniquement, il pointe vers les serveurs edge en ligne (par exemple _, sipfed.online.lync.com_) tandis qu’en mode hybride, il pointe vers des serveurs edge locaux (par exemple _, sipfed.\<domain>_).|**Service** : sipfederationtls <br/> **Protocole :** TCP <br/> **Priorité :** 100 <br/> **Poids :** 1 <br/> **Port :** 5061 <br/> **Cible :** _sipfederationtls.tcp.\<domain> <br/> **Remarque :** si le pare-feu ou le serveur proxy bloque les recherches SRV sur un DNS externe, vous devez ajouter cet enregistrement à l'enregistrement DNS interne. |
|**SRV** <br/> **(Teams et Skype Entreprise Online)**|Requis par Skype Entreprise client Windows Desktop et les téléphones Skype Entreprise pour la connexion. Il peut être nécessaire pour les locataires Teams uniquement qui utilisent Skype Entreprise les téléphones en ligne pour Teams et qui doivent pointer vers des serveurs edge en ligne (par exemple _, sip.online.lync.com_). <br/>Il est nécessaire aux locataires hybrides de prendre en charge leurs clients et téléphones Windows Desktop qui se connectent à des déploiements locaux (par exemple _, sip.\<domain>_).|**Cible :** _sip._tls.\<domain>|
|**CNAME** <br/> **(Teams et Skype Entreprise Online)**|Requis par le client de bureau Skype Entreprise pour les clients Windows, Mac et web, ainsi que par Réunion Skype Application (SMA) pour se connecter. <br/>Également utilisées par les applets de commande PowerShell qui utilisent toujours Skype Entreprise infrastructure En ligne pour la gestion. Par conséquent, elle est également nécessaire pour les locataires Teams uniquement et hybrides.|**Cible :**  lyncdiscover.\<domain>|
|**SRV** <br/> **(Skype Entreprise Online)**|Requis par Skype Entreprise pour coordonner le flux d’informations entre les clients Lync.|**Service :** sip <br/> **Protocole :** TLS <br/> **Priorité :** 100 <br/> **Poids :** 1 <br/> **Port :** 443 <br/> **Cible :** sipdir.online.lync.com|
|**CNAME** <br/> **(Skype Entreprise Online)**|Requis par le client de bureau Lync pour localiser le service Skype Entreprise Online et se connecter.|**Alias :** sip <br/> **Cible :** sipdir.online.lync.com|
|**CNAME** <br/> **(Skype Entreprise Online)**|Requis par le client mobile Lync pour vous aider à trouver le service Skype Entreprise Online et à vous connecter.|**Alias :** lyncdiscover <br/> **Cible :** webdir.online.lync.com|

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Enregistrements DNS externes requis pour authentification unique Office 365
<a name="BKMK_ReqdCore"> </a>

|Enregistrement DNS|Objectif|Valeur à utiliser|
|---|---|---|
|**Hôte (A)**|Used for single sign-on (SSO). It provides the endpoint for your off-premises users (and on-premises users, if you like) to connect to your Active Directory Federation Services (AD FS) federation server proxies or load-balanced virtual IP (VIP).|**Cible :** par exemple, sts.contoso.com|

## <a name="external-dns-records-required-for-spf"></a>Enregistrements DNS externes requis pour SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against. In order to protect against these, once you have set up SPF, you should also configure DKIM and DMARC for Office 365. To get started, see [Use DKIM to validate outbound email sent from your domain in Office 365](../security/office-365-security/use-dkim-to-validate-outbound-email.md). Next, see [Use DMARC to validate email in Office 365](../security/office-365-security/use-dmarc-to-validate-email.md).

SPF records are TXT records that help to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.

You can only have one SPF record (that is, a TXT record that defines SPF) for your domain. That single record can have a few different inclusions but the total DNS lookups that result can't be more than 10 (this helps prevent denial of service attacks). See the table and other examples below to help you create or update the right SPF record values for your environment.

### <a name="structure-of-an-spf-record"></a>Structure d'un enregistrement SPF

All SPF records contain three parts: the declaration that it is an SPF record, the domains, and IP addresses that should be sending email, and an enforcement rule. You need all three in a valid SPF record. Here's an example of a common SPF record for Office 365 when you use only Exchange Online email:

``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

An email system that receives an email from your domain looks at the SPF record, and if the email server that sent the message was an Office 365 server, the message is accepted. If the server that sent the message was your old mail system or a malicious system on the Internet, for example, the SPF check might fail and the message wouldn't be delivered. Checks like this help to prevent spoofing and phishing messages.

### <a name="choose-the-spf-record-structure-you-need"></a>Choisir la structure d’enregistrement SPF dont vous avez besoin

Pour les scénarios où vous n’utilisez pas seulement les emails Exchange Online pour Office 365 (par exemple, lorsque vous utilisez le courrier électronique en provenance de SharePoint Online), utilisez le tableau suivant pour déterminer les éléments à inclure dans la valeur de l’enregistrement.

> [!NOTE]
> If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md). You can also learn much more about how SPF works with Office 365 by reading [How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing](../security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing.md).

|Nombre|Si vous utilisez...|Objectif|Ajoutez ceci|
|---|---|---|---|
|1|Tous les systèmes de courrier (obligatoire)|Tous les enregistrements SPF commencent par cette valeur|v=spf1|
|2|Exchange Online (courant)|Utilisez uniquement avec Exchange Online|include:spf.protection.outlook.com|
|3|Un système de messagerie tiers (moins courant)||Incluez :\<email system like mail.contoso.com\>|
|4|Le système de messagerie du site (moins courant)|À utiliser si vous avez recours à Exchange Online Protection ou Exchange Online et un autre système de messagerie|IP4 : \<0.0.0.0\> <br/> ip6 : \< : : \> <br/> Incluez : \<mail.contoso.com\> <br/> La valeur entre crochets (\<\>) doit être les autres systèmes de messagerie chargés d’envoyer les emails pour votre domaine.|
|5|Tous les systèmes de courrier (obligatoire)||-all|

### <a name="example-adding-to-an-existing-spf-record"></a>Exemple : Ajout à un enregistrement SPF existant
<a name="bkmk_addtospf"> </a>

If you already have an SPF record, you'll need to add or update values for Office 365. For example, say your existing SPF record for contoso.com is this:

``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

Now you're updating your SPF record for Office 365. You'll edit your current record so you have an SPF record that includes the values that you need. For Office 365, "spf.protection.outlook.com".

Correct :

``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

Incorrect :

``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>Autres exemples de valeurs SPF standard
<a name="bkmk_addtospf"> </a>

If you are using the full Office 365 suite and are using MailChimp to send marketing emails on your behalf, your SPF record at contoso.com might look like the following, which uses rows 1, 3, and 5 from the table above. Remember, rows 1 and 5 are required.

``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

Sinon, si vous avez une configuration Exchange hybride où le courrier électronique a été envoyé à la fois à partir d’Office 365 et du système de messagerie du site, votre enregistrement SPF sur contoso.com peut se présenter comme ceci :

``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

These are some common examples that can help you adapt your existing SPF record when you add your domain to Office 365 for email. If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md).

Voici un lien que vous pouvez utiliser pour revenir : <https://aka.ms/o365edns>
