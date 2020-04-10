---
title: Notions DNS de base
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
search.appverid:
- MET150
- MOE150
- GEA150
- BSA160
ms.assetid: 854b6b2b-0255-4089-8019-b765cff70377
ROBOTS: NOINDEX
description: En savoir davantage sur les domaines et les enregistrements DNS associés pour vous aider à gérer vos domaines Office 365.
ms.openlocfilehash: 4fd41102193a9e630ed04a9d1fb2e196dc94486b
ms.sourcegitcommit: 4a34b48584071e0c43c920bb35025e34cb4f5d15
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "43210467"
---
# <a name="dns-basics"></a>Principes de base

 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
::: moniker range="o365-worldwide"

Les noms de domaine, tels que contoso.com, sont gérés à l'aide d'un système mondial de bureaux d'enregistrement de domaines et de bases de données. Le système DNS (Domain Name System) fournit un mappage entre les noms d'hôtes d'ordinateurs lisibles et les adresses IP utilisées par l'équipement réseau. Comprendre les concepts de base de DNS et des bureaux d'enregistrement de domaines peut vous aider à gérer les domaines dans Office 365.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/c005f2a4-90ad-46fe-b1ab-90f41f2a9d53?autoplay=false]
  
::: moniker-end

::: moniker range="o365-germany"

Les noms de domaine, tels que contoso.com, sont gérés à l'aide d'un système mondial de bureaux d'enregistrement de domaines et de bases de données. Le système DNS (Domain Name System) fournit un mappage entre les noms d'hôtes d'ordinateurs lisibles et les adresses IP utilisées par l'équipement réseau. Comprendre les concepts de base de DNS et des bureaux d'enregistrement de domaines peut vous aider à gérer les domaines dans Office 365.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/c005f2a4-90ad-46fe-b1ab-90f41f2a9d53?autoplay=false]
  
::: moniker-end

::: moniker range="o365-21vianet"

Les noms de domaine, tels que contoso.com, sont gérés à l'aide d'un système mondial de bureaux d'enregistrement de domaines et de bases de données. Le système DNS (Domain Name System) fournit un mappage entre les noms d'hôtes d'ordinateurs lisibles et les adresses IP utilisées par l'équipement réseau. Les informations de base sur le DNS et le bureau d’enregistrement de domaines permettront aux administrateurs de gérer les domaines gérés par 21Vianet dans Office 365.
  
::: moniker-end

## <a name="what-are-domain-names"></a>Que sont les noms de domaine ?

Les noms de domaine sont utilisés dans les URL et adresses de messagerie. Ils présentent différents niveaux. Par exemple, le nom de domaine mail.contoso.com comporte les trois niveaux suivants :
  
- **.com** est le domaine de premier niveau. 
    
- **contoso** est le domaine de second niveau. 
    
- **mail** est le domaine de troisième niveau. 
    
Pourquoi utiliser un domaine de troisième niveau ? Vous pouvez utiliser différents noms de domaine pour un blog ou dans une démarche marketing (par exemple, blog.contoso.com). Vous ajoutez généralement un domaine de second niveau tel que contoso.com, pour l'utiliser avec Office 365, mais vous pouvez également utiliser des domaines de troisième niveau si vous le souhaitez.
  
Découvrez ce que vous pouvez faire avec les domaines pour chaque type d'offre dans la [description du service Office 365 pour les domaines](https://go.microsoft.com/fwlink/?LinkId=402693).
  
## <a name="understand-dns-record-types"></a>Comprendre les types d’enregistrements DNS

Les enregistrements DNS stockés auprès d'un hôte DNS pour votre domaine permettent de diriger le trafic pour votre domaine. Le tableau suivant décrit les enregistrements DNS fréquemment utilisés et leur utilisation avec Office 365.
  
|**Enregistrement de serveur de noms**|**Identifie quels serveurs de noms sont les serveurs de noms de référence pour un domaine. Lorsque vous modifiez ces serveurs pour votre domaine, vous modifiez l'endroit où vos enregistrements DNS sont gérés et l'endroit où le système DNS recherche des informations sur les serveurs de courrier, etc. Office 365 a ses propres serveurs de noms. Vous pouvez également décider de continuer à utiliser les serveurs de noms déjà configurés avec votre domaine.**|
|:-----|:-----|
|Enregistrement A (enregistrement d’adresse)  <br/> |Associe un nom de domaine à une adresse IP.  <br/> |
|Enregistrement CNAME (alias ou canonique)  <br/> |Redirige un domaine vers un autre dans le système DNS. Quand un serveur de noms recherche un domaine et trouve un enregistrement CNAME, il remplace le premier nom de domaine par le CNAME, puis recherche le nouveau nom.  <br/> |
|Enregistrement MX (serveur de courrier)  <br/> |Pointe vers l’endroit où vos courriers électroniques doivent être envoyés. Comporte également un champ de priorité pour vous permettre d’envoyer le courrier vers différents serveurs dans un ordre de priorité.  <br/> |
|Enregistrement SPF (Sender Policy Framework)  <br/> |Enregistrement TXT qui empêche l’usurpation d’adresse de courrier et le hameçonnage.  <br/> |
|Enregistrement SRV (enregistrement de service)  <br/> |Utilisé par Skype Entreprise Online et Exchange Online pour coordonner le flux des informations circulant entre les services Office 365. Par exemple, les enregistrements SRV sont requis pour voir les informations de présence dans Outlook Web App et pour utiliser Skype Entreprise Online, Skype ou d'autres outils de messagerie instantanée avec des utilisateurs dans d'autres sociétés.  <br/> |
|TTL (durée de vie)  <br/> |Durée pendant laquelle un serveur de noms conserve un enregistrement DNS avant que le serveur ne recherche une version mise à jour.  <br/> |
   
## <a name="how-does-dns-work"></a>Fonctionnement du système DNS

La modification ou l’ajout d’[enregistrements DNS](dns-basics.md) pour votre domaine fait partie du processus de configuration de votre domaine avec un service cloud tel qu’Office 365. Ces modifications sont requises en raison du fonctionnement d’Internet avec DNS (Domain Name System) et les noms de domaine, pour déterminer l’emplacement auquel vous voulez envoyer ou rechercher des éléments, tels que des messages électroniques et des sites web. 
  
Internet est configuré pour utiliser DNS (Domain Name System). Celui-ci permet d'utiliser des noms familiers (par exemple, contoso.com) pour localiser des emplacements spécifiques sur Internet désignés en réalité par des nombres difficiles à mémoriser appelés adresses IP (Internet Protocol). 70.42.241.42 est un exemple d'adresse IP. Vous constatez donc qu'il est plus facile d'utiliser un nom de domaine pour identifier les emplacements tels que les hôtes de courrier et les sites web.
  
En bref, les enregistrements DNS indiquent à Internet l’emplacement auquel envoyer un message électronique (par exemple, joe@contoso.com) ou trouver des sites web (par exemple, www.contoso.com) qui utilisent votre nom de domaine. Lorsque vous placez les informations appropriées dans les enregistrements DNS correspondants pour votre domaine, le système DNS achemine tout le contenu correctement et votre courrier électronique, par exemple, est réceptionné dans Office 365 plutôt qu’ailleurs.
  
Les enregistrements DNS d’un domaine peuvent être utiles de d’autres façons. Par exemple, Exchange vérifie un enregistrement DNS qui permet à Outlook de configurer automatiquement une connexion au serveur Exchange correct.
  
### <a name="dns-records-help-the-internet-send-email-to-the-right-place"></a>Les enregistrements DNS aident Internet à envoyer les courriers électroniques à l’emplacement approprié

Comme indiqué plus haut, DNS dirige principalement le trafic sur Internet, en mappant des noms de domaine conviviaux avec des adresses IP difficiles à mémoriser. Un enregistrement DNS appelé enregistrement MX est spécifiquement conçu pour envoyer des courriers électroniques à l’hôte approprié. 
  
Les enregistrements DNS sont semblables à une base de données des informations sur votre domaine. Les enregistrements et leurs valeurs sont conservés dans un fichier de zone. Celui-ci inclut une liste des enregistrements pour votre domaine et de leurs valeurs. Les bureaux d'enregistrement de domaines et les autres entreprises d'hébergement DNS fournissent une interface utilisateur sur leurs sites web pour vous permettre de modifier les enregistrements dans le fichier de zone de votre domaine. Il s'agit de l'emplacement dans lequel vous mettez à jour l'enregistrement MX de votre domaine pour envoyer des messages électroniques à Office 365.
  
 *Lorsque vous transférez votre courrier vers Office 365, en mettant à jour l'enregistrement MX de votre domaine à l'étape suivante, les messages envoyés à ce domaine commenceront à arriver dans Office 365.*  Si d'autres personnes utilisent votre domaine pour le courrier électronique, vous devez configurer des boîtes aux lettres Office 365 pour chacune de ces personnes. 
  
Cela vous semble compliqué ? Même si cela peut l’être, vous êtes guidé dans les différentes étape de la configuration d’un domaine dans Office 365.
  
### <a name="dns-tells-the-internet-where-to-look-for-websites-too"></a>Le DNS indique également à Internet où trouver les sites web

Lorsque vous tapez une adresse de site web (par exemple, www.contoso.com), Internet commence par rechercher auprès de l'un des serveurs DNS l'enregistrement de serveur de noms pour contoso.com (dans le cas présent). L'enregistrement de serveur de noms indique à Internet où rechercher le fichier de zone qui contient toutes les autres valeurs d'enregistrement DNS pour ce domaine. Il y a de nombreux serveurs DNS, tous connectés les uns aux autres. Les serveurs fonctionnent conjointement pour suivre tous les noms de domaine enregistrés, lesquels doivent être uniques et se trouver au même emplacement que les fichiers de zone du domaine.
  
::: moniker range="o365-worldwide"

Admettons que l'enregistrement de serveur de nom pour contoso.com indique « godaddy.com ». Internet saura désormais qu'il faut rechercher dans GoDaddy.com pour trouver le fichier de zone recensant les autres enregistrements DNS pour contoso.com. Ces enregistrements DNS comprennent un enregistrement MX qui indique où envoyer les courriers électroniques pour contoso.com ainsi que d'autres enregistrements. Si l'enregistrement MX comprend une valeur qui indique (en termes techniques) « envoyer un courrier électronique à Office 365 », les courriers électroniques envoyés vers une adresse contoso.com (comme joe@contoso.com) y seront tous redirigés. Ensuite, dès lors qu'une boîte aux lettres nommée « Joe » se trouve à cet emplacement, le message sera remis.

::: moniker-end

::: moniker range="o365-germany"

Admettons que l'enregistrement de serveur de nom pour contoso.com indique « godaddy.com ». Internet saura désormais qu'il faut rechercher dans GoDaddy.com pour trouver le fichier de zone recensant les autres enregistrements DNS pour contoso.com. Ces enregistrements DNS comprennent un enregistrement MX qui indique où envoyer les courriers électroniques pour contoso.com ainsi que d'autres enregistrements. Si l'enregistrement MX comprend une valeur qui indique (en termes techniques) « envoyer un courrier électronique à Office 365 », les courriers électroniques envoyés vers une adresse contoso.com (comme joe@contoso.com) y seront tous redirigés. Ensuite, dès lors qu'une boîte aux lettres nommée « Joe » se trouve à cet emplacement, le message sera remis.

::: moniker-end

::: moniker range="o365-21vianet"

Supposons que l’enregistrement NS pour contoso.com mentionne « hichina.com ». Internet saura désormais qu’il faut rechercher dans hichina.com pour trouver le fichier de zone recensant les autres enregistrements DNS pour contoso.com. Ces enregistrements DNS comprennent un enregistrement MX qui indique où envoyer les courriers électroniques pour contoso.com ainsi que d'autres enregistrements. Si l'enregistrement MX comprend une valeur qui indique (en termes techniques) « envoyer un courrier électronique à Office 365 », les courriers électroniques envoyés vers une adresse contoso.com (comme joe@contoso.com) y seront tous redirigés. Ensuite, dès lors qu'une boîte aux lettres nommée « Joe » se trouve à cet emplacement, le message sera remis.

::: moniker-end

Les valeurs réelles que vous devez entrer pour que tout cela fonctionne avec Office 365 sont répertoriées automatiquement lorsque vous définissez votre domaine, dans le cadre de la configuration des domaines. Si vous effectuez les étapes de configuration manuellement, vous copiez et collez les valeurs dans les enregistrements DNS corrects (enregistrement MX, enregistrements CNAME, etc.) au niveau de votre hôte DNS, lequel peut éventuellement être votre bureau d’enregistrement de domaines.
  
::: moniker range="o365-worldwide"

Pour quelle raison le fichier de zone de votre domaine peut-il être stocké ailleurs qu'au niveau de votre bureau d'enregistrement de domaines ? Vous pouvez enregistrer votre nom de domaine auprès d'un bureau d'enregistrement de domaines tel que GoDaddy, mais vos enregistrements DNS peuvent être gérés par un autre fournisseur d'hébergement DNS ou d'hébergement web. Les enregistrements de serveur de noms pour votre domaine stockent ces informations afin que tous les serveurs DNS identifient l'emplacement dans lequel rechercher.

::: moniker-end

::: moniker range="o365-germany"

Pour quelle raison le fichier de zone de votre domaine peut-il être stocké ailleurs qu'au niveau de votre bureau d'enregistrement de domaines ? Vous pouvez enregistrer votre nom de domaine auprès d'un bureau d'enregistrement de domaines tel que GoDaddy, mais vos enregistrements DNS peuvent être gérés par un autre fournisseur d'hébergement DNS ou d'hébergement web. Les enregistrements de serveur de noms pour votre domaine stockent ces informations afin que tous les serveurs DNS identifient l'emplacement dans lequel rechercher.

::: moniker-end

::: moniker range="o365-21vianet"

Pourquoi le fichier de zone de votre domaine peut-il se trouver autre part que sur votre bureau d’enregistrement de domaines ? Vous pouvez enregistrer votre nom de domaine auprès d’un bureau d’enregistrement de domaines tel que HiChina, mais il est possible que vos enregistrements DNS soient gérés ailleurs, auprès d’une société d’hébergement DNS distincte ou d’une société d’hébergement web. Les enregistrements DNS pour votre domaine stockent ces informations pour que tous les serveurs DNS sachent où rechercher.

::: moniker-end

> [!NOTE]
> Si vous avez configuré votre domaine dans Office 365 de telle sorte qu’[Office 365 configure et gère vos enregistrements DNS](../setup/domains-faq.md#how-does-office-365-manage-my-dns-records) automatiquement dans le cadre de l’installation, vous devez [modifier la gestion des enregistrements DNS vers Office 365](../setup/domains-faq.md#change-dns-management-to-office-365). 
 

::: moniker range="o365-worldwide"
## <a name="why-add-a-domain-in-office-365"></a>Pourquoi ajouter un domaine dans Office 365 ?


L'ajout d'un domaine personnalisé, tel que fourthcoffee.com, à Office 365 vous permet d'utiliser une adresse de courrier plus courte et plus conviviale, et un identifiant d'utilisateur avec le service. [Un domaine vous est octroyé](https://support.office.com/article/b9fc3018-8844-43f3-8db1-1b3a8e9cfd5a.aspx) lorsque vous vous inscrivez pour bénéficier d'un compte Office 365. Celui-ci inclut toutefois « onmicrosoft.com ». Les entreprises ou organisations préfèrent souvent ajouter leur domaine dans le cadre de l'utilisation d'Office 365 pour le courrier électronique. 
  
> [!NOTE]
> Si vous souhaitez simplement télécharger et utiliser les applications Office 365, tels que Word ou Outlook, vous n’avez pas besoin d’ajouter un domaine :[installez Office sur votre PC ou Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658.aspx). 
  
Vous pouvez utiliser votre nom de domaine dans Office 365 avec votre courrier, votre site web public et votre adresse de messagerie instantanée.
  
- **Courrier électronique :** votre nom de domaine vous permet de personnaliser vos adresses de courrier électronique. Vous pouvez ainsi utiliser une adresse plus courte et plus facile à retenir que [l'adresse onmicrosoft.com initiale](https://support.office.com/article/b9fc3018-8844-43f3-8db1-1b3a8e9cfd5a.aspx) fournie avec votre compte. Par exemple, au lieu de maurice@contoso.onmicrosoft.com, vous pouvez utiliser l'adresse de courrier (qui est aussi l'compte professionnel à utiliser pour se connecter à Office 365) maurice@contoso.com. 
    
- **Site web :** si vous avez un abonnement Office 365 incluant un site web public SharePoint Online (désormais indisponible à l'achat), une adresse initiale telle que contoso-public.sharepoint.com est fournie avec votre site web public. Si vous configurez votre site web pour votre entreprise, vous pouvez utiliser un nom de domaine personnalisé pour renommer l'adresse du site web (par exemple, www.contoso.com). 
    
- **Messagerie instantanée :** votre adresse Skype Entreprise Online peut également être personnalisée pour utiliser votre nom de domaine, afin que les personnes de votre organisation puissent se contacter sur Skype Entreprise Online en utilisant une adresse plus courte et plus facile à mémoriser (telle que joe@contoso.com). 
    
::: moniker-end

::: moniker range="o365-germany"
## <a name="why-add-a-domain-in-office-365"></a>Pourquoi ajouter un domaine dans Office 365 ?


L'ajout d'un domaine personnalisé, tel que fourthcoffee.com, à Office 365 vous permet d'utiliser une adresse de courrier plus courte et plus conviviale, et un identifiant d'utilisateur avec le service. [Un domaine vous est octroyé](https://support.office.com/article/b9fc3018-8844-43f3-8db1-1b3a8e9cfd5a.aspx) lorsque vous vous inscrivez pour bénéficier d'un compte Office 365. Celui-ci inclut toutefois « onmicrosoft.com ». Les entreprises ou organisations préfèrent souvent ajouter leur domaine dans le cadre de l'utilisation d'Office 365 pour le courrier électronique. 
  
> [!NOTE]
> Si vous souhaitez simplement télécharger et utiliser les applications Office 365, tels que Word ou Outlook, vous n’avez pas besoin d’ajouter un domaine :[installez Office sur votre PC ou Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658.aspx). 
  
Vous pouvez utiliser votre nom de domaine dans Office 365 avec votre courrier, votre site web public et votre adresse de messagerie instantanée.
  
- **Courrier électronique :** votre nom de domaine vous permet de personnaliser vos adresses de courrier électronique. Vous pouvez ainsi utiliser une adresse plus courte et plus facile à retenir que [l'adresse onmicrosoft.com initiale](https://support.office.com/article/b9fc3018-8844-43f3-8db1-1b3a8e9cfd5a.aspx) fournie avec votre compte. Par exemple, au lieu de maurice@contoso.onmicrosoft.com, vous pouvez utiliser l'adresse de courrier (qui est aussi l'compte professionnel à utiliser pour se connecter à Office 365) maurice@contoso.com. 
    
- **Site web :** si vous avez un abonnement Office 365 incluant un site web public SharePoint Online (désormais indisponible à l'achat), une adresse initiale telle que contoso-public.sharepoint.com est fournie avec votre site web public. Si vous configurez votre site web pour votre entreprise, vous pouvez utiliser un nom de domaine personnalisé pour renommer l'adresse du site web (par exemple, www.contoso.com). 
    
- **Messagerie instantanée :** votre adresse Skype Entreprise Online peut également être personnalisée pour utiliser votre nom de domaine, afin que les personnes de votre organisation puissent se contacter sur Skype Entreprise Online en utilisant une adresse plus courte et plus facile à mémoriser (telle que joe@contoso.com). 
    
::: moniker-end

## <a name="the-dns-records-required-for-office-365"></a>Les enregistrements DNS sont obligatoires pour Office 365

Plusieurs enregistrements DNS sont requis pour permettre à Office 365 de fonctionner avec votre domaine. En plus de configurer l'enregistrement MX de votre domaine de sorte que le courrier électronique soit envoyé à Office 365, des enregistrements permettent de s'assurer qu'Outlook peut se connecter automatiquement au serveur Exchange approprié, de configurer la messagerie instantanée et d'éviter le courrier indésirable.
  
Vous pouvez [consulter une liste de valeurs](information-for-dns-records.md) pour configurer votre domaine. Celles-ci sont incluses directement dans le portail Office 365. 
  
Ou, si vous envisagez de procéder à un déploiement, vous pouvez consulter la liste des enregistrements DNS requis pour Office 365 avec leur fonction et des valeurs d'exemple. Consultez les [Enregistrements DNS externes pour Office 365](https://support.office.com/article/c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0).
  
## <a name="how-can-i-learn-more"></a>Pour en savoir plus

Consultez les rubriques suivantes : 
  
- Vous ne savez pas si votre domaine est enregistré ? [Obtenir de l'aide pour rechercher votre bureau d'enregistrement de domaines](find-your-domain-registrar.md).
    
- Découvrez la [raison pour laquelle vous devez suivre les étapes de l'Assistant](../setup/add-domain.md) avant de pouvoir utiliser votre domaine avec Office 365. 
    

