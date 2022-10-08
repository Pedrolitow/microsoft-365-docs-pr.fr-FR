---
title: Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/16/2018
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
search.appverid:
- MET150
description: Obtenez des affiches informatiques qui décrivent les modèles architecturaux, le déploiement et les options de plateforme pour SharePoint, Exchange, Skype Entreprise et Lync.
ms.openlocfilehash: de9e3346c8956ba3a809e4931b4302706753adb3
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68198644"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync

Les affiches informatiques de cet article décrivent les modèles architecturaux et les options de déploiement pour SharePoint, Exchange, Skype Entreprise et Lync. Ils fournissent également des informations de conception pour le déploiement de SharePoint dans Microsoft Azure.
  
À l’aide de Microsoft 365, vous pouvez fournir des services de collaboration et de communication familiers via le cloud. À quelques exceptions près, l’expérience utilisateur reste la même que vous gériez un déploiement local ou que vous utilisiez Microsoft 365. 

Cette expérience utilisateur unifiée complique la décision d’emplacement de chaque charge de travail. Il soulève également des questions :
  
- Comment choisir une plateforme pour des charges de travail individuelles ?
    
- Est-il judicieux de conserver tous les services en local ?
    
- Dans quel scénario un déploiement hybride est-il approprié ?
    
- Comment Azure s’intègre-t-il à l’image ?
    
- Quelles sont les configurations des charges de travail de serveur Office support Azure ?
    
> [!TIP]
> La plupart des affiches de cet article sont disponibles en plusieurs langues. Les langues disponibles sont le chinois, l’anglais, l’Français, l’allemand, l’italien, le japonais, le coréen, le portugais, le russe et l’espagnol. Pour télécharger une affiche dans l’une de ces langues, sous l’image miniature de l’affiche, sélectionnez **Plus de langues**.
  
Dites-nous ce que vous en pensez ! Envoyez-nous un courrier électronique à l'adresse [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
Utilisez les liens suivants pour obtenir les affiches dont vous avez besoin :
  
- **Modèles architecturaux** : utilisez ces ressources pour déterminer votre plateforme et configuration idéales pour SharePoint 2016 et Skype Entreprise 2015.
    
  - [Modèles architecturaux Microsoft SharePoint 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [Bases de données SharePoint Server 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Modèles architecturaux Microsoft Skype Entreprise 2015](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Plateforme** : utilisez ces ressources pour déterminer votre plateforme et configuration idéales pour SharePoint 2013, Exchange 2013 et Lync 2013.
    
  - [Options de plateforme SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Options de plateforme Exchange 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Options de plateforme Lync 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **SharePoint Server 2013 dans Azure** : utilisez ces affiches informatiques pour concevoir et configurer des charges de travail SharePoint Server 2013 dans les services d’infrastructure Azure.
    
  - [Sites Internet dans Azure à l’aide de SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Exemple de conception : sites Internet dans Azure pour SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [Récupération d’urgence SharePoint vers Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Affiches des modèles architecturaux

Les affiches informatiques pour SharePoint 2016 et Skype Entreprise 2015 permettent de comparer les méthodes de déploiement dans un format facile à imprimer. Les affiches répertorient toutes les options de configuration ou de plateforme. Elles fournissent les informations suivantes pour chaque option :
  
- **Vue d’ensemble** : bref résumé de la plateforme, y compris un diagramme conceptuel.
    
- **Idéal pour** : scénarios courants qui sont idéalement adaptés à la plateforme.
    
- **Conditions de licence** : les licences dont vous avez besoin pour le déploiement.
    
- **Tâches d’architecture** : les décisions que vous devez prendre en tant qu’architecte.
    
- **Tâches ou responsabilités des professionnels de l’informatique** : responsabilités quotidiennes que votre personnel informatique doit planifier.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-server-2016-architectural-models"></a>Modèles architecturaux Microsoft SharePoint Server 2016

|Élément|Description|
|---|---|
|[![Miniature de l’affiche Modèles architecturaux SharePoint Server 2016.](../media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| [Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=52650)|Cette affiche informatique décrit les configurations locales SharePoint Online, Azure et SharePoint que les décideurs d’entreprise et les architectes de solutions doivent connaître. <br/><br/> - **SharePoint Online (SaaS)** : consommez SharePoint via un modèle d’abonnement SaaS (Software as a Service). <br/> - **SharePoint hybride** : déplacez vos sites et applications SharePoint vers le cloud à votre propre rythme. <br/> - **SharePoint dans Azure (IaaS)** : étendez votre environnement local dans Azure et déployez des serveurs SharePoint 2016. (Ce modèle est recommandé pour les environnements de haute disponibilité ou de récupération d’urgence et les environnements de développement/test.) <br/> - **SharePoint local** : planifiez, déployez, gérez et personnalisez votre environnement SharePoint dans un centre de données que vous gérez.|
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>Bases de données SharePoint Server 2016

|Élément|Description|
|---|---|
|[![Miniature de l’affiche Bases de données SharePoint Server 2016.](../media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| [Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=55041)|Cette affiche informatique est une référence rapide pour les bases de données SharePoint Server 2016. Vous verrez des détails pour chaque base de données : <br/><br/> -Taille <br/> - Conseils mise à l’échelle <br/> - Modèles d’E/S <br/> - Conditions requises : <br/><br/>  La première page montre les bases de données système SharePoint et les applications de service qui ont plusieurs bases de données. La deuxième page affiche toutes les applications de service qui ont des bases de données uniques. <br/><br/>  Pour plus d’informations, consultez [les types de base de données et les descriptions dans SharePoint Server 2016](/SharePoint/technical-reference/database-types-and-descriptions).|
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Modèles architecturaux Microsoft Skype Entreprise 2015

|Élément|Description|
|---|---|
|[![Miniature de l’affiche Skype Entreprise Modèles architecturaux.](../media/132288c0-6ae4-4394-88ab-b57dae367714.png)](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| [Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=55022)|Cette affiche décrit Skype Entreprise exchange de succursales privées (PBX) en ligne, locale, hybride et cloud. Il décrit également l’intégration aux configurations Exchange et SharePoint que les décideurs d’entreprise et les architectes de solutions doivent connaître. <br/><br/> L’affiche est destinée aux professionnels de l’informatique afin de sensibiliser les professionnels de l’informatique aux modèles architecturaux fondamentaux grâce auxquels Skype Entreprise Online et Skype Entreprise localement peuvent être consommés. <br/><br/>Commencez par la configuration qui convient le mieux aux besoins et aux plans de votre organisation. Envisagez et utilisez d’autres configurations en fonction des besoins. Par exemple, vous souhaiterez peut-être envisager l’intégration à Exchange et SharePoint, ou une solution qui tire parti de l’offre MICROSOFT CLOUD PBX.|
   
## <a name="platform-options-posters"></a>Affiches des options de plateforme

Les affiches informatiques pour SharePoint 2013, Exchange 2013 et Lync 2013 permettent de comparer les méthodes de déploiement en un clin d’œil. Chaque affiche répertorie toutes les configurations ou options de plateforme. Il fournit les informations suivantes pour chaque option :
  
- **Vue d’ensemble** : bref résumé de la plateforme, y compris un diagramme conceptuel.
    
- **Idéal pour** : scénarios courants qui sont idéalement adaptés à la plateforme.
    
- **Conditions de licence** : les licences dont vous avez besoin pour le déploiement.
    
- **Tâches d’architecture** : les décisions que vous devez prendre en tant qu’architecte.
    
- **Tâches ou responsabilités des professionnels de l’informatique** : responsabilités quotidiennes que votre personnel informatique doit planifier.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>Options de plateforme SharePoint 2013

|Élément|Description|
|---|---|
|[![Image miniature de l’affiche Options de la plateforme SharePoint 2013.](../media/SP-PlatformOptions.jpg)](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=40332)|Pour les décideurs et les architectes d’entreprise, cette affiche présente les options de plateforme pour SharePoint 2013, SharePoint dans Microsoft 365, hybride local avec Microsoft 365, Azure et les déploiements locaux uniquement. Il inclut une vue d’ensemble de chaque architecture, recommandations, exigences de licence et listes de tâches d’architecte et de professionnels de l’informatique pour chaque plateforme. L’affiche met en évidence plusieurs solutions SharePoint sur Azure.|
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Options de plateforme Exchange 2013

|Élément|Description|
|---|---|
|[![Image miniature de l’affiche Options de la plateforme Exchange.](../media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=42676)|Pour les décideurs d’entreprise et les architectes, cette affiche décrit les options de plateforme pour Exchange 2013. Les clients peuvent choisir parmi Exchange Online avec Microsoft 365, Exchange hybride, Exchange Server local et Exchange hébergé. L’affiche détaille chaque option architecturale, y compris les scénarios idéaux pour chacune d’elles, les exigences de licence et les responsabilités des professionnels de l’informatique.|
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Options de plateforme Lync 2013

|Élément|Description|
|---|---|
|[![Image miniature de l’affiche Lync 2013 Platform Options.](../media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=41677)|Pour les décideurs d’entreprise et les architectes, cette affiche décrit les options de plateforme pour Lync 2013. Les clients peuvent choisir entre Lync Online avec Microsoft 365, Lync hybride, Lync Server local et Lync hébergé. L’affiche informatique détaille chaque option architecturale, y compris les scénarios idéaux pour chacune d’elles, les exigences de licence et les responsabilités des professionnels de l’informatique.|
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>Affiches des solutions SharePoint dans Azure

Les affiches informatiques pour SharePoint dans Azure montrent les solutions Basées sur Azure qui utilisent SharePoint Server 2013.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Sites Internet dans Microsoft Azure à l’aide de SharePoint Server 2013

|Élément|Description|
|---|---|
|[![Image des sites Internet dans Azure à l’aide de l’affiche SharePoint Server 2013.](../media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=41992)|Cette affiche présente les principales activités de conception et l’architecture recommandée pour les sites accessibles sur Internet dans Azure.  <br/><br/> Si vous souhaitez en savoir plus, consultez les articles suivants :  <br/><br/> - [Sites Internet dans Azure à l’aide de SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Architectures Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="DesignSampleInternetSites"> </a>
### <a name="internet-sites-in-azure-for-sharepoint-2013"></a>Sites Internet dans Azure pour SharePoint 2013

|Élément|Description|
|---|---|
|[![Image des sites Internet dans l’affiche Microsoft Azure pour SharePoint Server 2013.](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=41991)|Utilisez cet exemple de conception comme point de départ pour votre propre architecture d’un site accessible sur Internet dans Azure à l’aide de SharePoint Server 2013. <br/><br/> Si vous souhaitez en savoir plus, consultez les articles suivants :  <br/><br/> - [Sites Internet dans Azure à l’aide de SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Architectures Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>Récupération d’urgence SharePoint vers Microsoft Azure

|Élément|Description|
|---|---|
|[![Image de l’affiche du processus de récupération d’urgence SharePoint sur Azure.](../media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=41993)|Cette affiche présente les principes d’architecture pour un environnement de récupération d’urgence dans Azure. <br/><br/> Pour plus d’informations, voir les articles suivants :  <br/><br/> - [Récupération d’urgence sharePoint Server 2013 dans Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [Architectures Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
## <a name="see-also"></a>Voir aussi

- [Centre de solutions et d'architecture Microsoft 365](../solutions/index.yml)
  
- [Modèles d’architecture cloud Microsoft](../solutions/cloud-architecture-models.md)
  
- [Guides de laboratoire de test Microsoft 365](m365-enterprise-test-lab-guides.md)
  
- [Solutions hybrides](hybrid-solutions.md)