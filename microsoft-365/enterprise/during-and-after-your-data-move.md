---
title: Pendant et après le déplacement de vos données
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.collection: SPO_Content
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
f1.keywords:
- NOCSH
description: Les déplacements de données sont des opérations de base qui se produisent lorsque Microsoft déplace les services et les données associées de votre client vers une nouvelle géo de centres de données.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 14563a695e5c092f9bddfbdfdcb758f90cea32c0
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50929419"
---
# <a name="during-and-after-your-data-move"></a>Pendant et après le déplacement de vos données

Les déplacements de données sont des opérations principales n'ayant que peu d'impact sur les utilisateurs finals. Aucune action de votre part n'est requise lorsque Microsoft déplace chaque service et les données associées pour votre client vers une nouvelle zone géographique de centres de données. Le transfert de données et la validation se déroulent en arrière-plan à l'avance, et n'ont qu'une incidence minimale sur les utilisateurs.
  
> [!NOTE]
> Le déplacement se produit à différents moments pour chaque service. Par conséquent, vous ne verrez pas la description des fonctionnalités réduites pour chaque service au même moment. 
  
Regardez le Centre de messages Microsoft 365 pour confirmer que les déplacements pour chaque service de conversation Exchange Online, SharePoint Online et Teams sont terminés. Comme indiqué dans le tableau ci-dessous, il faut jusqu’à 24 mois après la fin de la période d’inscription pour effectuer des déplacements de données client essentielles au repos vers la nouvelle géo de centres de données.   

|**Clients dont le pays d’inscription est**|**Tous les déplacements terminés d'ici le**|
|:-----|:-----|
|Australie, Nouvelle-Zélande, Fidji  <br/> |1er juillet 2022  <br/> |
|Japon  <br/> |1er juillet 2022  <br/> |
|Inde  <br/> |1er juillet 2022  <br/> |
|Canada  <br/> |1er juillet 2022  <br/> |
|Corée du Sud  <br/> |1er juillet 2022  <br/> |
|Royaume-Uni  <br/> |1er juillet 2022  <br/> |
|France  <br/> |1er juillet 2022  <br/> |
|Émirats arabes unis  <br/> |1er juillet 2022  <br/> |
|Afrique du Sud  <br/> |1er juillet 2022  <br/> |
|Suisse, Liechtenstein  <br/> |1er juillet 2022  <br/> |
|Norvège  <br/> |1er novembre 2022  <br/> |
|Allemagne  <br/> |1er mai 2023  <br/> |
|Brésil  <br/> |1er juin 2023  <br/> |

## <a name="exchange-online"></a>Exchange Online

Comme le déplacement de chaque utilisateur vers la nouvelle zone géographique de centres de données pour un seul client prend du temps, certains utilisateurs seront encore dans l’ancienne zone géographique de centres de données pendant le déplacement, tandis que d’autres seront dans la nouvelle. Cela signifie que certaines fonctionnalités qui impliquent l’accès à plusieurs boîtes aux lettres peuvent ne pas fonctionner entièrement pendant une période du processus de déplacement, qui peut durer plusieurs semaines. Ces fonctionnalités sont décrites dans les sections suivantes.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Ouvrez « Dossier partagé » dans Outlook Web Access 

Certains utilisateurs ouvrent un dossier de messagerie partagé à partir d'une autre boîte aux lettres (sur laquelle l'utilisateur a des autorisations en lecture ou en écriture) dans Outlook Web Access à l'aide de la fonctionnalité « Dossier partagé ». Le tableau suivant indique comment fonctionne l'accès aux dossiers partagés au cours d'un déplacement de boîte aux lettres. Notez que les utilisateurs disposant d'autorisations complètes sur une boîte aux lettres partagée peuvent ouvrir la boîte aux lettres à l'aide d'Outlook Web Access lors du déplacement. 
  
|**Configuration**|**Description**|
|:-----|:-----|
|L'utilisateur dispose d'autorisations de dossier de boîte aux lettres sur une autre boîte aux lettres  <br/> |Potentiellement limité.  <br/> Si l'utilisateur A et la boîte aux lettres B ne se trouvent pas dans la même zone géographique lors du déplacement de client, l'utilisateur A ne peut pas ouvrir le dossier la boîte aux lettres B dans Outlook Web Access s'il n'a de droit d'accès que pour un dossier spécifique de la boîte aux lettres B.  <br/> Pour ajouter un dossier partagé, cliquez avec le bouton droit de la souris sur le nom d'utilisateur dans le volet de navigation gauche, puis sélectionnez **Ajouter un dossier partagé**.  <br/> |
|Utilisateur disposant de droits d’accès complets sur une autre boîte aux lettres  <br/> |Entièrement pris en charge  <br/> Si l’utilisateur A dispose de l’autorisation « Accès total » pour la boîte aux lettres B, l’utilisateur A peut cliquer sur le dossier partagé dans le panneau de navigation gauche de Outlook Web Access pour ouvrir une fenêtre affichant la boîte aux lettres B.  Un utilisateur peut ouvrir une boîte aux lettres partagée à l’Outlook Web Access pendant le déplacement sans aucun impact négatif. La limitation s’applique uniquement au partage au niveau du dossier dans une boîte aux lettres.           |
  
## <a name="sharepoint-online"></a>SharePoint Online

Lors du déplacement de SharePoint Online, les données des services suivants sont également déplacées :
  
- OneDrive Entreprise
    
- Services vidéo Microsoft 365
    
- Office dans un navigateur
    
- Applications Microsoft 365 pour les grandes entreprises
    
- Visio Pro pour Microsoft 365
    
Une fois que nous aurons déplacé vos données SharePoint Online, vous pourrez éventuellement observer certains des effets suivants.
  
### <a name="microsoft-365-video-services"></a>Services vidéo Microsoft 365

- Le déplacement de vidéos prend plus de temps que le déplacement d'autres contenus dans SharePoint Online.
    
- Une fois le contenu de SharePoint Online déplacé, vous ne pourrez pas lire les vidéos pendant une certaine période.
    
- Nous supprimons les copies transcodées du centre de données précédent et les transcodons à nouveau dans le nouveau centre de données.
    
### <a name="search"></a>Recherche

Dans le cadre du déplacement de vos données SharePoint Online, nous migrons vos paramètres de recherche et d'index vers un nouvel emplacement. Jusqu'à la **fin** du déplacement de vos données SharePoint Online, nous continuons de desservir vos utilisateurs depuis l'index situé dans l'emplacement d'origine. Dans le nouvel emplacement, la fonction recherche démarre automatiquement une analyse de votre contenu une fois le déplacement de vos données SharePoint Online terminé. À ce moment-là, nous desservirons vos utilisateurs depuis l'index migré. Les modifications apportées à votre contenu après la migration ne sont pas prises en compte dans l'index migré tant que l'analyse ne les a pas récupérées. La plupart des clients ne remarquent pas que les résultats proposent des contenus moins récents immédiatement après la migration de leurs données SharePoint Online, mais certains peuvent s'en apercevoir au cours des 24-48 premières heures d'utilisation. 
  
Les fonctionnalités de recherche suivantes sont concernées :
  
- Résultats de la recherche et composants WebPart de recherche : Les résultats n’incluent pas les modifications qui se sont produites après la migration jusqu’à ce que l’analyse les ait récupérées. 
    
- Delve : Delve n'inclut pas les modifications qui se sont produites après la migration jusqu'à ce que l'analyse les ait récupérées.
    
- Rapports de popularité et de recherche pour le site : le nombre de rapports Excel situés dans le nouvel emplacement prend uniquement en compte le nombre de rapports migrés et de rapports d'utilisation exécutés après le déplacement de vos données SharePoint Online. Le nombre de rapports existant pendant la période de transition est perdu et ne peut pas être récupéré. Cette période correspond généralement à quelques jours. Certains clients peuvent constater des pertes plus courtes ou plus longues.
    
- Portail vidéo : les nombres et les statistiques de vue dépendent des statistiques des rapports Excel. Par conséquent, ils sont perdus pendant le même nombre de jours que les rapports Excel.
    
- eDiscovery (découverte électronique) : Les éléments modifiés au cours de la migration ne sont pas affichés avant que l’analyse n’ait récupéré les modifications.
    
- Protection contre la perte de données (DLP) : Les politiques ne sont pas appliquées sur les éléments qui changent avant que l’analyse n’ait récupéré les modifications.

## <a name="microsoft-teams"></a>Microsoft Teams

Outre Exchange Online, SharePoint Online et OneDrive Entreprise, Microsoft migre les données du service de conversation Teams vers le centre de données local.

- Messages de conversation Teams, y compris les messages privés et les messages de canal.
- Images Teams utilisées dans les conversations.

Les fichiers Teams sont stockés dans SharePoint Online et les fichiers de conversation Teams sont stockés dans OneDrive Entreprise. La messagerie vocale, le calendrier, l’historique des conversation et les contacts sont stockés dans Exchange Online. Dans de nombreux cas, Exchange Online, SharePoint Online et OneDrive Entreprise sont déjà utilisés par le client dans la région du centre de données local et font également partie du programme de migration Microsoft 365 pour les pays clients éligibles.

## <a name="skype-for-business"></a>Skype Entreprise

Les déplacements Skype Entreprise ne sont plus disponibles.  [Skype Entreprise Online sera retiré](/lifecycle/announcements/skype-for-business-online-retirement) le 31 juillet 2021. Après cette période, le service n’est plus accessible. 
  
## <a name="related-topics"></a>Rubriques connexes 
 
[Procédure de demande d’un déplacement de données](request-your-data-move.md)
    
[FAQ général relatif au déplacement de données](data-move-faq.md)
  
[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Services Azure par région](https://azure.microsoft.com/regions/)