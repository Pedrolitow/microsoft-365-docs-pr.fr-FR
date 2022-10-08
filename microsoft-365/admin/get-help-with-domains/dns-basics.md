---
title: Principes de base
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- scotvorg
- highpri
- M365-subscription-management
- Adm_O365
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- MET150
- MOE150
- GEA150
- BSA160
ms.assetid: 854b6b2b-0255-4089-8019-b765cff70377
ROBOTS: NOINDEX
description: Le système de nom de domaine mappe les noms d’hôtes de l’ordinateur vers les adresses IP et comprendre les informations de base du bureau d'enregistrement de domaines et du DNS peut vous aider à gérer des domaines.
ms.openlocfilehash: d2399c7e5fa739fe36d4893db8653d0e70d92bcb
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68166656"
---
# <a name="dns-basics"></a>Principes de base

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
::: moniker range="o365-worldwide"

Domain names, like contoso.com, are managed by using a worldwide system of domain registrars and databases. The Domain Name System (DNS) provides a mapping between human-readable computer hostnames and the IP addresses used by networking equipment. An understanding of DNS and domain registrar basics can help you manage domains.

## <a name="watch-domains--dns-an-overview"></a>À regarder : Domaines et DNS : vue d’ensemble
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/c005f2a4-90ad-46fe-b1ab-90f41f2a9d53?autoplay=false]
  
::: moniker-end

::: moniker range="o365-21vianet"

Domain names, like contoso.com, are managed by using a worldwide system of domain registrars and databases. The Domain Name System (DNS) provides a mapping between human-readable computer hostnames and the IP addresses used by networking equipment. An understanding of DNS and domain registrar basics will help admins manage domains.
  
::: moniker-end

## <a name="what-are-domain-names"></a>Que sont les noms de domaine ?

Domain names are used in URLs and email addresses, and they have different levels. For example, mail.contoso.com is a domain name with the following three levels:
  
- **.com** est le domaine de premier niveau. 
    
- **contoso** est le domaine de second niveau. 
    
- **mail** est le domaine de troisième niveau. 
    
Why use a third-level domain? You might want to have different domain names for marketing or a blog. For example, blog.contoso.com. You typically add a second-level domain, like contoso.com, to use with Microsoft but you can also use third-level domains if you like.
  
Découvrez ce que vous pouvez faire avec les domaines pour chaque type d'offre dans la [description du service des plateforme Microsoft 365 et Office 365](/office365/servicedescriptions/office-365-platform-service-description/domains).
  
## <a name="understand-dns-record-types"></a>Comprendre les types d’enregistrements DNS

DNS records stored at a DNS host for your domain are used to direct traffic for your domain. The following table describes frequently used DNS records and how they're used.
  
|**Enregistrement de serveur de noms**|**Identifie quels serveurs de noms sont les serveurs de noms de référence pour un domaine. Lorsque vous modifiez ces serveurs pour votre domaine, vous modifiez l'endroit où vos enregistrements DNS sont gérés et l'endroit où le système DNS recherche des informations sur les serveurs de courrier, etc. Microsoft a ses propres serveurs de noms. Vous pouvez également décider de continuer à utiliser les serveurs de noms déjà configurés avec votre domaine.**|
|:-----|:-----|
|Enregistrement A (enregistrement d’adresse)  <br/> |Associe un nom de domaine à une adresse IP.  <br/> |
|Enregistrement CNAME (alias ou canonique)  <br/> |Redirects one domain to another in the DNS system. When a name server looks up a domain and finds that it has a CNAME record, the server replaces the first domain name with the CNAME, and then looks up the new name.  <br/> |
|Enregistrement MX (serveur de courrier)  <br/> |Points to where your email should be sent. It also has a priority field so that you can send mail to different servers in a priority order.  <br/> |
|Enregistrement SPF (Sender Policy Framework)  <br/> |Enregistrement TXT qui empêche l’usurpation d’adresse de courrier et le hameçonnage.  <br/> |
|Enregistrement SRV (enregistrement de service)  <br/> |Used by Skype for Business Online and Exchange Online to coordinate the flow of information between Microsoft services. For example, the SRV records are required to see presence in Outlook Web App, and to use Skype for Business Online, Skype, or other instant messaging tools with people in other companies.  <br/> |
|TTL (durée de vie)  <br/> |Durée pendant laquelle un serveur de noms conserve un enregistrement DNS avant que le serveur ne recherche une version mise à jour.  <br/> |
   
## <a name="how-does-dns-work"></a>Fonctionnement du système DNS

Part of setting up your domain with a cloud service like Microsoft 365 includes changing or adding [DNS records](dns-basics.md) for the domain. These changes are required because of how the Internet works with the DNS, Domain Name System, and domain names, to know where to send or find things, like email and websites. 
  
The Internet is set up to use DNS, or Domain Name System, which lets us use familiar names, like contoso.com, to locate specific Internet locations that are actually, under the covers, labeled with hard-to-remember numbers called IP (Internet Protocol) addresses. IP addresses look something like 70.42.241.42, so you can see it's much easier to use a domain name to identify locations like email hosts and websites.
  
So that's the short answer: DNS records tell the Internet where to send email (like joe@contoso.com) or find websites (like www.contoso.com) that use your domain name. When you put the right information into the right DNS records for your domain, the DNS system routes everything correctly so your email, for example, arrives in Microsoft 365 instead of somewhere else.
  
A domain's DNS records can be helpful in other ways, too. For example, Exchange checks a DNS record that lets Outlook automatically set up a connection to the right Exchange server.
  
### <a name="dns-records-help-the-internet-send-email-to-the-right-place"></a>Les enregistrements DNS aident Internet à envoyer les courriers électroniques à l’emplacement approprié

As you read above, DNS essentially directs traffic around the Internet, mapping friendly domain names to those hard-to-remember IP addresses. One DNS record, called the MX record, is specifically for sending email to the right host.
  
DNS records are like a database of information about your domain. The records and their values are kept in something called a zone file, which includes a list of each record for your domain and what its value is. Domain registrars and other DNS hosting companies provide a UI on their websites so you can edit the records in your domain's zone file. And that's where you update the MX record for your domain, to send email messages to Microsoft 365.
  
 *When you change your email to Microsoft 365, by updating your domain's MX record in the next step, ALL email sent to that domain will start coming to Microsoft 365.*  If other people use your domain for email, you must set up Microsoft 365 mailboxes for each of those people. 
  
Sound complicated? Well, it can be, but we walk you through each step in the Microsoft domain setup.
  
### <a name="dns-tells-the-internet-where-to-look-for-websites-too"></a>Le DNS indique également à Internet où trouver les sites web

When you type in a website address, for example, www.contoso.com, the Internet first checks with one of the DNS servers for something called a name server (NS) record for (in this case) contoso.com. The NS record tells the Internet where it should look for the zone file that has all the other DNS record values for that domain. There are lots of DNS servers, all connected to each other. The servers work together to keep track of all registered domain names, which have to be unique, and where the domain's zone files are.
  
::: moniker range="o365-worldwide"

Let's say that the NS record for contoso.com says "godaddy.com." Now the Internet knows that GoDaddy.com is where to look for the zone file listing all the other DNS records for contoso.com. Those DNS records include the MX record that says where to send emails for contoso.com and other records. If the MX record has a value that says (but in technical terms) "send email to Microsoft 365," that's where all the email messages sent to a contoso.com email address (like joe@contoso.com) will be sent. Then, as long as there's a mailbox called "joe" at that location, the email will be delivered.

::: moniker-end

::: moniker range="o365-21vianet"

Let's say that the NS record for contoso.com says "hichina.com." Now the Internet knows that hichina.com is where to look for the zone file listing all the other DNS records for contoso.com. Those DNS records include the MX record that says where to send emails for contoso.com and other records. If the MX record has a value that says (but in technical terms) "send email to Microsoft 365," that's where all the email messages sent to a contoso.com email address (like joe@contoso.com) will be sent. Then, as long as there's a mailbox called "joe" at that location, the email will be delivered.

::: moniker-end

The actual values that you must enter for all of this to work with Microsoft 365 are listed for you when you're setting up your domain, in the domain setup steps. If you're doing the set up manually, you copy and paste the values into the correct DNS records (MX record, CNAME records, and so on) at your DNS host, which might be your domain registrar but doesn't have to be.
  
::: moniker range="o365-worldwide"

Why might your domain's zone file be somewhere besides at your domain registrar? Well, you might register your domain name at a domain registrar like GoDaddy, but your DNS records might be managed somewhere else, at a separate DNS hosting company or a web hosting company. The NS records for your domain store that information so all the DNS servers know where to look.

::: moniker-end

::: moniker range="o365-21vianet"

Why might your domain's zone file be somewhere besides at your domain registrar? Well, you might register your domain name at a domain registrar like HiChina, but your DNS records might be managed somewhere else, at a separate DNS hosting company or a web hosting company. The NS records for your domain store that information so all the DNS servers know where to look.

::: moniker-end

::: moniker range="o365-worldwide"
## <a name="why-add-a-domain-in-microsoft-365"></a>Pourquoi ajouter un domaine dans Microsoft 365 ?


Adding a custom domain, like fourthcoffee.com, to Microsoft 365 lets you use a shorter, more familiar email address and userID with the service. You're [given a domain to use](../setup/domains-faq.yml) when you sign up for a Microsoft 365 account, but it includes "onmicrosoft.com." Many people prefer to add their organization or business domain if they plan to use Microsoft 365 for email. 
  
> [!NOTE]
> Si vous souhaitez simplement télécharger et utiliser les applications Microsoft, tels que Word ou Outlook, vous n’avez pas besoin d’ajouter un domaine :[installez Office sur votre PC ou Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658). 
  
Vous pouvez utiliser votre nom de domaine dans Microsoft 365 avec votre courrier, votre site web public et votre adresse de messagerie instantanée.
  
- **Email:** Your domain name lets you customize your email, so you can use a shorter, easier-to-remember address than [the initial onmicrosoft.com email address](../setup/domains-faq.yml) that comes with your account. So instead of joe@contoso.onmicrosoft.com, the email address (which is also the work account that you use to sign in to Microsoft 365) could be joe@contoso.com. 
    
- **Site web :** si vous avez un abonnement Microsoft 365 incluant un site web public SharePoint Online (désormais indisponible à l'achat), une adresse initiale telle que contoso-public.sharepoint.com est fournie avec votre site web public. Si vous configurez votre site web pour votre entreprise, vous pouvez utiliser un nom de domaine personnalisé pour renommer l'adresse du site web (par exemple, www.contoso.com). 
    
- **Messagerie instantanée :** votre adresse Skype Entreprise Online peut également être personnalisée pour utiliser votre nom de domaine, afin que les personnes de votre organisation puissent se contacter sur Skype Entreprise Online en utilisant une adresse plus courte et plus facile à mémoriser (telle que joe@contoso.com). 
    
::: moniker-end

## <a name="the-dns-records-required-for-microsoft-365"></a>Les enregistrements DNS sont obligatoires pour Microsoft 365

There are a number of DNS records required for Microsoft 365 to work with your domain. In addition to setting up your domain's MX record so email will be sent to Microsoft 365, there are records to help with tasks like making sure Outlook can automatically connect to the right Exchange server, setting up instant messaging, and helping to prevent spam email.
  
You can [find a list of values](information-for-dns-records.md) to set up your domain. They're included right in the <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Microsoft 365 admin center</a>. 
  
Or, if you're planning a deployment, you may want to review a list of all the DNS records required for Microsoft 365, what their function is, and example values. Check out [External Domain Name System records for Microsoft 365](../../enterprise/external-domain-name-system-records.md).
  
## <a name="next-steps"></a>Étapes suivantes

Consultez les rubriques suivantes : 
  
- Not sure where your domain is registered? [Get help finding your domain registrar.](find-your-domain-registrar.md)
- Découvrez la [raison pour laquelle vous devez suivre les étapes de l'Assistant](../setup/add-domain.md) avant de pouvoir utiliser votre domaine avec Microsoft 365.

## <a name="related-content"></a>Contenu associé

[FAQ sur les domaines](../setup/domains-faq.yml) (article)\
[Rechercher et corriger les problèmes, y compris de messagerie, après avoir ajouté votre domaine ou des enregistrements DNS](find-and-fix-issues.md) (article)\
[Gérer des domaines](/admin) (page de lien)