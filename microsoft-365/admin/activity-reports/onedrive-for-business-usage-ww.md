---
title: Rapports d’utilisation de Microsoft 365 OneDrive Entreprise
f1.keywords:
- NOCSH
ms.author: camillepack
author: camillepack
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Obtenez le rapport d’utilisation OneDrive Entreprise pour en savoir plus sur le nombre total de fichiers et de stockage utilisés au sein de votre organisation.
ms.openlocfilehash: 5a1afc447d90e0da811d051c2fe56b36f6c641d4
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68196026"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-usage"></a>Rapports Microsoft 365 dans le Centre d’administration - utilisation OneDrive Entreprise

Le tableau de bord Rapports Microsoft 365 affiche la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md).
  
For example, the OneDrive card on the dashboard gives you a high-level view of the value you are getting from OneDrive for Business in terms of the total number of files and storage used across your organization. You can then drill into it to understand the trends of active OneDrive accounts, how many files are users interacting with as well as the storage used. It also gives you details for each user's OneDrive.

## <a name="how-do-i-get-to-the-onedrive-usage-report"></a>Comment faire accéder au rapport d’utilisation de OneDrive ?

1. Dans le centre d’administration, accédez aux **rapports**, puis sélectionnez **Utilisation**. 
2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** sur la carte OneDrive.
  
## <a name="interpret-the-onedrive-usage-report"></a>Interpréter le rapport Utilisation de OneDrive

Vous pouvez afficher l’utilisation dans le rapport OneDrive en choisissant l’onglet **Utilisation** .

![Rapports Microsoft 365 - Rapport d’utilisation de Microsoft OneDrive.](../../media/3cdaf2fb-1817-479b-a0e1-2afa228690cf.png)

**Sélectionnez Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.  

![Rapport d’utilisation de OneDrive : choisissez des colonnes.](../../media/9ee80f25-cfe3-411d-8e31-08f1507d18c1.png)

Vous pouvez également exporter les données du rapport dans un fichier Excel .csv en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. 

Le **rapport d’utilisation OneDrive Entreprise** peut être consulté pour les tendances des 7 derniers jours, 30 jours, 90 jours ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).
  
|Élément|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|URL  <br/> |Adresse web du OneDrive de l’utilisateur. <br/> |
|Deleted  <br/> |État de suppression de OneDrive. La suppression effective des comptes prend au minimum 7 jours.  <br/> |
|Propriétaire  <br/> |Nom d’utilisateur de l’administrateur principal de OneDrive.   <br/> |
|Nom principal du propriétaire  <br/> |Adresse e-mail du propriétaire de OneDrive. <br/> |
|Date de la dernière activité (UTC)  <br/> | Date la plus récente à laquelle une activité de fichier a été effectuée dans OneDrive. Si le OneDrive ne présente aucune activité de fichier, la valeur sera vide.  <br/> |
|Fichiers  <br/> |Nombre de fichiers dans OneDrive. <br/>|
|Fichiers actifs  <br/> | Nombre de fichiers actifs dans la période.<br/> REMARQUE : Si des fichiers ont été supprimés pendant la période spécifiée pour le rapport, le nombre de fichiers actifs affichés dans le rapport peut être supérieur au nombre actuel de fichiers dans OneDrive. >  Les utilisateurs supprimés continueront d'apparaître dans les rapports pendant 180 jours.  <br/> |
|Stockage utilisé (Mo)  <br/> |Quantité de stockage utilisée par OneDrive en Mo. |
|||
   
> [!NOTE]
> Le rapport inclut uniquement les utilisateurs disposant d’une licence OneDrive Entreprise valide.
