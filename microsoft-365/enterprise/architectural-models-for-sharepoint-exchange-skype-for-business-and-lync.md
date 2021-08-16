---
title: Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 05/16/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
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
description: Obtenez des affiches qui décrivent les modèles architecturaux, le déploiement et les options de plateforme pour SharePoint, Exchange, Skype Entreprise et Lync.
ms.openlocfilehash: 98558c20c66a808e93cd866b2f676b5f78fde3c1
ms.sourcegitcommit: e269371de759a1a747c9f292775463aa11415f25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58356443"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync

Les affiches de cet article décrivent les modèles architecturaux et les options de déploiement pour SharePoint, Exchange, Skype Entreprise et Lync. Ils fournissent également des informations de conception pour le déploiement de SharePoint dans Microsoft Azure.
  
En utilisant Microsoft 365, vous pouvez fournir des services de collaboration et de communication familiers via le cloud. À quelques exceptions près, l’expérience utilisateur reste la même, que vous tenez à jour un déploiement local ou que vous utilisiez Microsoft 365. 

Cette expérience utilisateur unifiée complique la décision d’où placer chaque charge de travail. Elle pose également des questions :
  
- Comment choisir une plateforme pour les charges de travail individuelles ?
    
- Est-il judicieux de conserver tous les services en local ?
    
- Dans quel scénario un déploiement hybride est-il approprié ?
    
- Comment Azure s’intègre-t-il à l’image ?
    
- Quelles configurations des charges de travail Office serveur sont-ils prise en charge par Azure ?
    
> [!TIP]
> La plupart des affiches de cet article sont disponibles dans plusieurs langues. Les langues disponibles sont le chinois, l’anglais, le français, l’allemand, l’italien, le japonais, le coréen, le portugais, le russe et l’espagnol. Pour télécharger une affiche dans l’une de ces langues, sous l’image miniature de l’affiche, sélectionnez **Plus de langues.**
  
Faites-nous savoir ce que vous en pensez ! Écrivez-nous à l’adresse [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
Utilisez les liens suivants pour obtenir les affiches dont vous avez besoin :
  
- **Modèles architecturaux**: utilisez ces ressources pour déterminer la plateforme et la configuration idéales pour SharePoint 2016 et Skype Entreprise 2015.
    
  - [Modèles architecturaux Microsoft SharePoint 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [SharePoint Bases de données Server 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Modèles architecturaux Microsoft Skype Entreprise 2015](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Plateforme**: utilisez ces ressources pour déterminer votre plateforme et votre configuration idéales pour SharePoint 2013, Exchange 2013 et Lync 2013.
    
  - [SharePoint de plateforme 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Exchange de plateforme 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Options de plateforme Lync 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **SharePoint Server 2013** dans Azure : utilisez ces affiches informatiques pour concevoir et configurer des charges de travail SharePoint Server 2013 dans les services d’infrastructure Azure.
    
  - [Sites Internet dans Azure utilisant SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Exemple de conception : sites Internet dans Azure SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [SharePoint récupération d’urgence vers Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Affiches des modèles architecturaux

Les affiches pour SharePoint 2016 et Skype Entreprise 2015 permettent de comparer les méthodes de déploiement dans un format facile à imprimer. Les affiches listent toutes les options de configuration ou de plateforme. Elles fournissent les informations suivantes pour chaque option :
  
- **Vue d’ensemble**: bref résumé de la plateforme, y compris un diagramme conceptuel.
    
- **Idéal pour**: scénarios courants qui conviennent parfaitement à la plateforme.
    
- **Conditions requises** pour les licences : licences dont vous avez besoin pour le déploiement.
    
- **Tâches d’architecture**: décisions que vous devez prendre en tant qu’architecte.
    
- **Tâches ou responsabilités des** professionnel de l’it : responsabilités quotidiennes que votre personnel de l’équipe it doit planifier.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-server-2016-architectural-models"></a>Modèles architecturaux Microsoft SharePoint Server 2016

|Item|Description|
|---|---|
|[![Miniature de l’affiche SharePoint modèles architecturaux server 2016.](../media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| [Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=52650)|Cette affiche décrit les configurations SharePoint Online, Azure et SharePoint sur site que les décideurs d’entreprise et les architectes de solutions doivent connaître. <br/><br/> - **SharePoint Online (SaaS)**: utiliser SharePoint via un modèle d’abonnement SaaS (Software as a Service). <br/> - **SharePoint hybride**: déplacez vos sites SharePoint applications vers le cloud à votre rythme. <br/> - **SharePoint Azure (IaaS)**: étendez votre environnement local à Azure et déployez des serveurs SharePoint 2016. (Ce modèle est recommandé pour les environnements de haute disponibilité ou de récupération d’urgence et les environnements de développement/test.) <br/> - **SharePoint local**: planifiez, déployez, conservez et personnalisez votre environnement SharePoint dans un centre de données que vous conservez.|
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>Bases de données SharePoint Server 2016

|Item|Description|
|---|---|
|[![Miniature de l’affiche SharePoint bases de données Server 2016.](../media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| [Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=55041)|Cette affiche informatique est une référence rapide pour SharePoint bases de données Server 2016. Vous verrez les détails de chaque base de données : <br/><br/> -Taille <br/> - Conseils mise à l’échelle <br/> - Modèles d’E/S <br/> - Conditions requises : <br/><br/>  La première page affiche les bases SharePoint système et les applications de service qui ont plusieurs bases de données. La deuxième page affiche toutes les applications de service qui ont des bases de données uniques. <br/><br/>  Pour plus d’informations, voir types et descriptions de base de [données dans SharePoint Server 2016.](/SharePoint/technical-reference/database-types-and-descriptions)|
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Modèles architecturaux Microsoft Skype Entreprise 2015

|Item|Description|
|---|---|
|[![Miniature de l’affiche Skype Entreprise modèles architecturaux.](../media/132288c0-6ae4-4394-88ab-b57dae367714.png)](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| [Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=55022)|Cette affiche décrit Skype Entreprise online, local, hybride et PBX (Cloud Private Branch Exchange). Il décrit également l’intégration avec les configurations Exchange et SharePoint que les décideurs d’entreprise et les architectes de solutions doivent connaître. <br/><br/> L’affiche est destinée aux professionnels de l’informatique afin de sensibiliser les professionnels de l’informatique aux modèles architecturaux fondamentaux via lesquels Skype Entreprise Online et Skype Entreprise en local peuvent être consommés. <br/><br/>Commencez par la configuration qui correspond le mieux aux besoins et plans de votre organisation. Envisagez et utilisez d’autres configurations selon vos besoins. Par exemple, vous pouvez envisager l’intégration avec Exchange et SharePoint ou une solution qui tire parti de l’offre PBX cloud de Microsoft.|
   
## <a name="platform-options-posters"></a>Affiches des options de plateforme

Les affiches pour SharePoint 2013, Exchange 2013 et Lync 2013 permettent de comparer les méthodes de déploiement en un coup d’œil. Chaque affiche répertorie toutes les configurations ou options de plateforme. Il fournit les informations suivantes pour chaque option :
  
- **Vue d’ensemble**: bref résumé de la plateforme, y compris un diagramme conceptuel.
    
- **Idéal pour**: scénarios courants qui conviennent parfaitement à la plateforme.
    
- **Conditions requises** pour les licences : licences dont vous avez besoin pour le déploiement.
    
- **Tâches d’architecture**: décisions que vous devez prendre en tant qu’architecte.
    
- **Tâches ou responsabilités des** professionnel de l’it : responsabilités quotidiennes que votre personnel de l’équipe it doit planifier.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>Options de plateforme SharePoint 2013

|Item|Description|
|---|---|
|[![Image miniature de l’SharePoint Options de plateforme 2013.](../media/SP-PlatformOptions.jpg)](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=40332)|Pour les décideurs d’entreprise et les architectes, cette affiche présente les options de plateforme pour SharePoint 2013, SharePoint en Microsoft 365, un déploiement hybride local avec Microsoft 365, Azure et des déploiements locaux uniquement. Il inclut une vue d’ensemble de chaque architecture, des recommandations, des exigences de licence et des listes de tâches architecte et de professionnel de l’it pour chaque plateforme. L’affiche présente plusieurs solutions SharePoint sur Azure.|
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Options de plateforme Exchange 2013

|Item|Description|
|---|---|
|[![Image miniature de l’affiche Exchange Options de plateforme.](../media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=42676)|Pour les décideurs d’entreprise et les architectes, cette affiche décrit les options de plateforme pour Exchange 2013. Les clients peuvent choisir parmi Exchange Online avec des Microsoft 365, des Exchange hybrides, Exchange Server en local et des Exchange. L’affiche détaille chaque option architecturale, y compris les scénarios idéaux pour chacune d’elles, les exigences de licence et les responsabilités des professionnel de l’information.|
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Options de plateforme Lync 2013

|Item|Description|
|---|---|
|[![Image miniature de l’affiche Options de plateforme Lync 2013.](../media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=41677)|Pour les décideurs d’entreprise et les architectes, cette affiche décrit les options de plateforme pour Lync 2013. Les clients peuvent choisir entre Lync Online Microsoft 365, Lync hybride, Lync Server local et Lync hébergé. L’affiche détaille chaque option architecturale, y compris les scénarios idéaux pour chacune d’elles, les exigences de licence et les responsabilités des professionnel de l’information.|
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>Affiches des solutions SharePoint dans Azure

Les affiches informatiques SharePoint dans Azure montrent des solutions Azure qui utilisent SharePoint Server 2013.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Sites Internet dans Microsoft Azure’aide SharePoint Server 2013

|Item|Description|
|---|---|
|[![Image des sites Internet dans Azure à l’aide SharePoint Server 2013.](../media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=41992)|Cette affiche décrit les activités de conception clés et l’architecture recommandée pour les sites internet dans Azure.  <br/><br/> Pour plus d’informations, voir les articles suivants:  <br/><br/> - [Sites Internet dans Azure utilisant SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Architectures Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="DesignSampleInternetSites"> </a>
### <a name="internet-sites-in-azure-for-sharepoint-2013"></a>Sites Internet dans Azure pour SharePoint 2013

|Item|Description|
|---|---|
|[![Image des sites Internet dans Microsoft Azure affiche SharePoint Server 2013.](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=41991)|Utilisez cet exemple de conception comme point de départ pour votre propre architecture d’un site internet dans Azure à l’aide de SharePoint Server 2013. <br/><br/> Pour plus d’informations, voir les articles suivants:  <br/><br/> - [Sites Internet dans Azure utilisant SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Architectures Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>Récupération d’urgence SharePoint vers Microsoft Azure

|Item|Description|
|---|---|
|[![Image de l’affiche pour la SharePoint récupération d’urgence à Azure.](../media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| [Autres langues](https://www.microsoft.com/download/details.aspx?id=41993)|Cette affiche présente les principes d’architecture pour un environnement de récupération d’urgence dans Azure. <br/><br/> Pour plus d’informations, voir les articles suivants :  <br/><br/> - [SharePoint Récupération d’urgence de Serveur 2013 dans Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [Architectures Azure pour SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
## <a name="see-also"></a>Voir aussi

- [Centre de solutions et d'architecture Microsoft 365](../solutions/index.yml)
  
- [Modèles d’architecture cloud Microsoft](../solutions/cloud-architecture-models.md)
  
- [Microsoft 365 guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
  
- [Solutions hybrides](hybrid-solutions.md)