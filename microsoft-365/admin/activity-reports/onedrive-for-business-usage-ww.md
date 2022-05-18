---
title: rapports d’utilisation Microsoft 365 OneDrive Entreprise
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
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
ms.openlocfilehash: d195a521fba9dc82867821e27414d125dca09c61
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467271"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-usage"></a>rapports Microsoft 365 dans le Centre d’administration - utilisation OneDrive Entreprise

Le tableau de bord Microsoft 365 Rapports vous montre la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, la carte OneDrive du tableau de bord offre une vue d'ensemble de ce que vous apporte OneDrive Entreprise en termes de nombre total de fichiers et d'espace de stockage utilisé au sein de votre organisation. Vous pouvez l'explorer pour connaître les tendances des comptes OneDrive actifs, le nombre de fichiers avec lesquels les utilisateurs interagissent ainsi que l'espace de stockage utilisé. Elle vous fournit également des détails pour chaque utilisateur OneDrive.

## <a name="how-do-i-get-to-the-onedrive-usage-report"></a>Comment faire accéder au rapport d’utilisation OneDrive ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** sur la carte OneDrive.
  
## <a name="interpret-the-onedrive-usage-report"></a>Interpréter le rapport Utilisation de OneDrive

Vous pouvez afficher l’utilisation dans le rapport OneDrive en choisissant l’onglet **Utilisation**.<br/>![Microsoft 365 rapports - rapport d’utilisation Microsoft OneDrive.](../../media/3cdaf2fb-1817-479b-a0e1-2afa228690cf.png)

**Sélectionnez Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.  <br/> ![OneDrive rapport d’utilisation : choisissez des colonnes.](../../media/9ee80f25-cfe3-411d-8e31-08f1507d18c1.png)

Vous pouvez également exporter les données du rapport dans un fichier Excel .csv en sélectionnant le lien **Exporter**. Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. 

Le **rapport d’utilisation OneDrive Entreprise** peut être consulté pour les tendances des 7 derniers jours, 30 jours, 90 jours ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).
  
|Élément|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|URL  <br/> |Adresse web du OneDrive de l’utilisateur. <br/> |
|Deleted  <br/> |État de suppression du OneDrive. La suppression effective des comptes prend au minimum 7 jours.  <br/> |
|Propriétaire  <br/> |Nom d’utilisateur de l’administrateur principal du OneDrive.   <br/> |
|Nom principal du propriétaire  <br/> |Adresse e-mail du propriétaire du OneDrive. <br/> |
|Date de la dernière activité (UTC)  <br/> | Date la plus récente à laquelle une activité de fichier a été effectuée dans le OneDrive. Si le OneDrive ne présente aucune activité de fichier, la valeur sera vide.  <br/> |
|Fichiers  <br/> |Nombre de fichiers dans le OneDrive. <br/>|
|Fichiers actifs  <br/> | Nombre de fichiers actifs dans la période.<br/> REMARQUE : Si des fichiers ont été supprimés pendant la période spécifiée pour le rapport, le nombre de fichiers actifs affichés dans le rapport peut être supérieur au nombre actuel de fichiers dans le OneDrive. >  Les utilisateurs supprimés continueront d'apparaître dans les rapports pendant 180 jours.  <br/> |
|Stockage utilisé (Mo)  <br/> |Quantité de stockage utilisée par le OneDrive en Mo. |
|||
   
> [!NOTE]
> Le rapport inclut uniquement les utilisateurs disposant d’une licence OneDrive Entreprise valide.
