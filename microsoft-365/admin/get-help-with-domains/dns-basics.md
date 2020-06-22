---
title: Principes de base
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
- GEA150
- BSA160
ms.assetid: 854b6b2b-0255-4089-8019-b765cff70377
ROBOTS: NOINDEX
description: En savoir davantage sur les domaines et les enregistrements DNS associés pour vous aider à gérer vos domaines.
ms.openlocfilehash: 3a3a03c408d480b5d4678fde25c8830e063b1310
ms.sourcegitcommit: 659adf65d88ee44f643c471e6202396f1ffb6576
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44780180"
---
# <a name="dns-basics"></a>Principes de base

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
::: moniker range="o365-worldwide"

Domain names, like contoso.com, are managed by using a worldwide system of domain registrars and databases. The Domain Name System (DNS) provides a mapping between human-readable computer hostnames and the IP addresses used by networking equipment. An understanding of DNS and domain registrar basics can help you manage domains.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/c005f2a4-90ad-46fe-b1ab-90f41f2a9d53?autoplay=false]
  
::: moniker-end

::: moniker range="o365-germany"

Domain names, like contoso.com, are managed by using a worldwide system of domain registrars and databases. The Domain Name System (DNS) provides a mapping between human-readable computer hostnames and the IP addresses used by networking equipment. An understanding of DNS and domain registrar basics can help you manage domains in Office 365.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/c005f2a4-90ad-46fe-b1ab-90f41f2a9d53?autoplay=false]
  
::: moniker-end

::: moniker range="o365-21vianet"

Les noms de domaine, tels que contoso.com, sont gérés à l'aide d'un système mondial de bureaux d'enregistrement de domaines et de bases de données. Le système DNS (Domain Name System) fournit un mappage entre les noms d'hôtes d'ordinateurs lisibles et les adresses IP utilisées par l'équipement réseau. Les informations de base sur le DNS et le bureau d’enregistrement de domaines permettront aux administrateurs de gérer les domaines gérés par 21Vianet dans Office 365.
  
::: moniker-end

## <a name="what-are-domain-names"></a>Que sont les noms de domaine ?

Domain names are used in URLs and email addresses, and they have different levels. For example, mail.contoso.com is a domain name with the following three levels:
  
- **.com** est le domaine de premier niveau. 
    
- **contoso** est le domaine de second niveau. 
    
- **mail** est le domaine de troisième niveau. 
    
Why use a third-level domain? You might want to have different domain names for marketing or a blog. For example, blog.contoso.com. You typically add a second-level domain, like contoso.com, to use with Office 365 but you can also use third-level domains if you like.
  
Découvrez ce que vous pouvez faire avec les domaines pour chaque type d'offre dans la [description du service Office 365 pour les domaines](https://go.microsoft.com/fwlink/?LinkId=402693).
  
## <a name="understand-dns-record-types"></a>Comprendre les types d’enregistrements DNS

DNS records stored at a DNS host for your domain are used to direct traffic for your domain. The following table describes frequently used DNS records and how they're used with Office 365.
  
|**Enregistrement de serveur de noms**|**Identifie quels serveurs de noms sont les serveurs de noms de référence pour un domaine. Lorsque vous modifiez ces serveurs pour votre domaine, vous modifiez l'endroit où vos enregistrements DNS sont gérés et l'endroit où le système DNS recherche des informations sur les serveurs de courrier, etc. Office 365 a ses propres serveurs de noms. Vous pouvez également décider de continuer à utiliser les serveurs de noms déjà configurés avec votre domaine.**|
|:-----|:-----|
|Enregistrement A (enregistrement d’adresse)  <br/> |Associe un nom de domaine à une adresse IP.  <br/> |
|Enregistrement CNAME (alias ou canonique)  <br/> |Redirects one domain to another in the DNS system. When a name server looks up a domain and finds that it has a CNAME record, the server replaces the first domain name with the CNAME, and then looks up the new name.  <br/> |
|Enregistrement MX (serveur de courrier)  <br/> |Points to where your email should be sent. It also has a priority field so that you can send mail to different servers in a priority order.  <br/> |
|Enregistrement SPF (Sender Policy Framework)  <br/> |Enregistrement TXT qui empêche l’usurpation d’adresse de courrier et le hameçonnage.  <br/> |
|Enregistrement SRV (enregistrement de service)  <br/> |Used by Skype for Business Online and Exchange Online to coordinate the flow of information between Office 365 services. For example, the SRV records are required to see presence in Outlook Web App, and to use Skype for Business Online, Skype, or other instant messaging tools with people in other companies.  <br/> |
|TTL (durée de vie)  <br/> |Durée pendant laquelle un serveur de noms conserve un enregistrement DNS avant que le serveur ne recherche une version mise à jour.  <br/> |
   
## <a name="how-does-dns-work"></a>Fonctionnement du système DNS

Part of setting up your domain with a cloud service like Office 365 includes changing or adding [DNS records](dns-basics.md) for the domain. These changes are required because of how the Internet works with the DNS, Domain Name System, and domain names, to know where to send or find things, like email and websites. 
  
The Internet is set up to use DNS, or Domain Name System, which lets us use familiar names, like contoso.com, to locate specific Internet locations that are actually, under the covers, labeled with hard-to-remember numbers called IP (Internet Protocol) addresses. IP addresses look something like 70.42.241.42, so you can see it's much easier to use a domain name to identify locations like email hosts and websites.
  
So that's the short answer: DNS records tell the Internet where to send email (like joe@contoso.com) or find websites (like www.contoso.com) that use your domain name. When you put the right information into the right DNS records for your domain, the DNS system routes everything correctly so your email, for example, arrives in Office 365 instead of somewhere else.
  
A domain's DNS records can be helpful in other ways, too. For example, Exchange checks a DNS record that lets Outlook automatically set up a connection to the right Exchange server.
  
### <a name="dns-records-help-the-internet-send-email-to-the-right-place"></a>Les enregistrements DNS aident Internet à envoyer les courriers électroniques à l’emplacement approprié

As you read above, DNS essentially directs traffic around the Internet, mapping friendly domain names to those hard-to-remember IP addresses. One DNS record, called the MX record, is specifically for sending email to the right host.
  
DNS records are like a database of information about your domain. The records and their values are kept in something called a zone file, which includes a list of each record for your domain and what its value is. Domain registrars and other DNS hosting companies provide a UI on their websites so you can edit the records in your domain's zone file. And that's where you update the MX record for your domain, to send email messages to Office 365.
  
 *When you change your email to Office 365, by updating your domain's MX record in the next step, ALL email sent to that domain will start coming to Office 365.*  If other people use your domain for email, you must set up Office 365 mailboxes for each of those people. 
  
Sound complicated? Well, it can be, but we walk you through each step in the Office 365 domain setup.
  
### <a name="dns-tells-the-internet-where-to-look-for-websites-too"></a>Le DNS indique également à Internet où trouver les sites web

When you type in a website address, for example, www.contoso.com, the Internet first checks with one of the DNS servers for something called a name server (NS) record for (in this case) contoso.com. The NS record tells the Internet where it should look for the zone file that has all the other DNS record values for that domain. There are lots of DNS servers, all connected to each other. The servers work together to keep track of all registered domain names, which have to be unique, and where the domain's zone files are.
  
::: moniker range="o365-worldwide"

Let's say that the NS record for contoso.com says "godaddy.com." Now the Internet knows that GoDaddy.com is where to look for the zone file listing all the other DNS records for contoso.com. Those DNS records include the MX record that says where to send emails for contoso.com and other records. If the MX record has a value that says (but in technical terms) "send email to Office 365," that's where all the email messages sent to a contoso.com email address (like joe@contoso.com) will be sent. Then, as long as there's a mailbox called "joe" at that location, the email will be delivered.

::: moniker-end

::: moniker range="o365-germany"

Let's say that the NS record for contoso.com says "godaddy.com." Now the Internet knows that GoDaddy.com is where to look for the zone file listing all the other DNS records for contoso.com. Those DNS records include the MX record that says where to send emails for contoso.com and other records. If the MX record has a value that says (but in technical terms) "send email to Office 365," that's where all the email messages sent to a contoso.com email address (like joe@contoso.com) will be sent. Then, as long as there's a mailbox called "joe" at that location, the email will be delivered.

::: moniker-end

::: moniker range="o365-21vianet"

Supposons que l’enregistrement NS pour contoso.com mentionne « hichina.com ». Internet saura désormais qu’il faut rechercher dans hichina.com pour trouver le fichier de zone recensant les autres enregistrements DNS pour contoso.com. Ces enregistrements DNS comprennent un enregistrement MX qui indique où envoyer les courriers électroniques pour contoso.com ainsi que d'autres enregistrements. Si l'enregistrement MX comprend une valeur qui indique (en termes techniques) « envoyer un courrier électronique à Office 365 », les courriers électroniques envoyés vers une adresse contoso.com (comme joe@contoso.com) y seront tous redirigés. Ensuite, dès lors qu'une boîte aux lettres nommée « Joe » se trouve à cet emplacement, le message sera remis.

::: moniker-end

The actual values that you must enter for all of this to work with Office 365 are listed for you when you're setting up your domain, in the domain setup steps. If you're doing the set up manually, you copy and paste the values into the correct DNS records (MX record, CNAME records, and so on) at your DNS host, which might be your domain registrar but doesn't have to be.
  
::: moniker range="o365-worldwide"

Why might your domain's zone file be somewhere besides at your domain registrar? Well, you might register your domain name at a domain registrar like GoDaddy, but your DNS records might be managed somewhere else, at a separate DNS hosting company or a web hosting company. The NS records for your domain store that information so all the DNS servers know where to look.

::: moniker-end

::: moniker range="o365-germany"

Why might your domain's zone file be somewhere besides at your domain registrar? Well, you might register your domain name at a domain registrar like GoDaddy, but your DNS records might be managed somewhere else, at a separate DNS hosting company or a web hosting company. The NS records for your domain store that information so all the DNS servers know where to look.

::: moniker-end

::: moniker range="o365-21vianet"

Pourquoi le fichier de zone de votre domaine peut-il se trouver autre part que sur votre bureau d’enregistrement de domaines ? Vous pouvez enregistrer votre nom de domaine auprès d’un bureau d’enregistrement de domaines tel que HiChina, mais il est possible que vos enregistrements DNS soient gérés ailleurs, auprès d’une société d’hébergement DNS distincte ou d’une société d’hébergement web. Les enregistrements DNS pour votre domaine stockent ces informations pour que tous les serveurs DNS sachent où rechercher.

::: moniker-end

> [!NOTE]
> Si vous avez configuré votre domaine dans Office 365 de telle sorte que [Microsoft configure et gère vos enregistrements DNS](../setup/domains-faq.md#how-does-office-365-manage-my-dns-records) automatiquement dans le cadre de l’installation, vous devez [modifier la gestion des enregistrements DNS vers Office 365](../setup/domains-faq.md#change-dns-management-to-office-365). 
 

::: moniker range="o365-worldwide"
## <a name="why-add-a-domain-in-office-365"></a>Pourquoi ajouter un domaine dans Office 365 ?


Adding a custom domain, like fourthcoffee.com, to Office 365 lets you use a shorter, more familiar email address and userID with the service. You're [given a domain to use](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq) when you sign up for a Office 365 account, but it includes "onmicrosoft.com." Many people prefer to add their organization or business domain if they plan to use Office 365 for email. 
  
> [!NOTE]
> Si vous souhaitez simplement télécharger et utiliser les applications Microsoft, tels que Word ou Outlook, vous n’avez pas besoin d’ajouter un domaine :[installez Office sur votre PC ou Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658). 
  
Vous pouvez utiliser votre nom de domaine dans Office 365 avec votre courrier, votre site web public et votre adresse de messagerie instantanée.
  
- **Email:** Your domain name lets you customize your email, so you can use a shorter, easier-to-remember address than [the initial onmicrosoft.com email address](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq) that comes with your account. So instead of joe@contoso.onmicrosoft.com, the email address (which is also the work account that you use to sign in to Office 365) could be joe@contoso.com. 
    
- **Site web :** si vous avez un abonnement Microsoft 365 incluant un site web public SharePoint Online (désormais indisponible à l'achat), une adresse initiale telle que contoso-public.sharepoint.com est fournie avec votre site web public. Si vous configurez votre site web pour votre entreprise, vous pouvez utiliser un nom de domaine personnalisé pour renommer l'adresse du site web (par exemple, www.contoso.com). 
    
- **Messagerie instantanée :** votre adresse Skype Entreprise Online peut également être personnalisée pour utiliser votre nom de domaine, afin que les personnes de votre organisation puissent se contacter sur Skype Entreprise Online en utilisant une adresse plus courte et plus facile à mémoriser (telle que joe@contoso.com). 
    
::: moniker-end

::: moniker range="o365-germany"
## <a name="why-add-a-domain-in-office-365"></a>Pourquoi ajouter un domaine dans Office 365 ?


Adding a custom domain, like fourthcoffee.com, to Office 365 lets you use a shorter, more familiar email address and userID with the service. You're [given a domain to use](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq) when you sign up for a Office 365 account, but it includes "onmicrosoft.com." Many people prefer to add their organization or business domain if they plan to use Office 365 for email. 
  
> [!NOTE]
> Si vous souhaitez simplement télécharger et utiliser les applications Office 365, tels que Word ou Outlook, vous n’avez pas besoin d’ajouter un domaine :[installez Office sur votre PC ou Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658). 
  
Vous pouvez utiliser votre nom de domaine dans Office 365 avec votre courrier, votre site web public et votre adresse de messagerie instantanée.
  
- **Email:** Your domain name lets you customize your email, so you can use a shorter, easier-to-remember address than [the initial onmicrosoft.com email address](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq) that comes with your account. So instead of joe@contoso.onmicrosoft.com, the email address (which is also the work account that you use to sign in to Office 365) could be joe@contoso.com. 
    
- **Site web :** si vous avez un abonnement incluant un site web public SharePoint Online (désormais indisponible à l'achat), une adresse initiale telle que contoso-public.sharepoint.com est fournie avec votre site web public. Si vous configurez votre site web pour votre entreprise, vous pouvez utiliser un nom de domaine personnalisé pour renommer l'adresse du site web (par exemple, www.contoso.com). 
    
- **Messagerie instantanée :** votre adresse Skype Entreprise Online peut également être personnalisée pour utiliser votre nom de domaine, afin que les personnes de votre organisation puissent se contacter sur Skype Entreprise Online en utilisant une adresse plus courte et plus facile à mémoriser (telle que joe@contoso.com). 
    
::: moniker-end

## <a name="the-dns-records-required-for-office-365"></a>Les enregistrements DNS sont obligatoires pour Office 365

There are a number of DNS records required for Office 365 to work with your domain. In addition to setting up your domain's MX record so email will be sent to Office 365, there are records to help with tasks like making sure Outlook can automatically connect to the right Exchange server, setting up instant messaging, and helping to prevent spam email.
  
You can [find a list of values](information-for-dns-records.md) to set up your domain. They're included right in the Microsoft 365 admin center. 
  
Ou, si vous envisagez de procéder à un déploiement, vous pouvez consulter la liste des enregistrements DNS requis pour Office 365 avec leur fonction et des valeurs d'exemple. Consultez les [Enregistrements DNS externes pour Office 365](https://docs.microsoft.com/office365/enterprise/external-domain-name-system-records).
  
## <a name="how-can-i-learn-more"></a>Pour en savoir plus

Consultez les rubriques suivantes : 
  
- Vous ne savez pas si votre domaine est enregistré ? [Obtenir de l'aide pour rechercher votre bureau d'enregistrement de domaines](find-your-domain-registrar.md).
    
- Découvrez la [raison pour laquelle vous devez suivre les étapes de l'Assistant](../setup/add-domain.md) avant de pouvoir utiliser votre domaine avec Office 365. 
    

