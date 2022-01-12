---
title: 'Microsoft 365 rapports dans le Centre d’administration : OneDrive Entreprise’utilisation'
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
description: 'Obtenez le OneDrive Entreprise d’utilisation de l’ordinateur pour connaître le nombre total de fichiers et de stockage utilisés au sein de votre organisation. '
ms.openlocfilehash: 3a7cf36be7d0ae12acf1a1ad6d9ace8a83afc2bd
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61918214"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-usage"></a>Microsoft 365 rapports dans le Centre d’administration : OneDrive Entreprise’utilisation

Le tableau Microsoft 365 de rapports d’entreprise vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, la carte OneDrive du tableau de bord offre une vue d'ensemble de ce que vous apporte OneDrive Entreprise en termes de nombre total de fichiers et d'espace de stockage utilisé au sein de votre organisation. Vous pouvez l'explorer pour connaître les tendances des comptes OneDrive actifs, le nombre de fichiers avec lesquels les utilisateurs interagissent ainsi que l'espace de stockage utilisé. Elle vous fournit également des détails pour chaque utilisateur OneDrive.

## <a name="how-do-i-get-to-the-onedrive-usage-report"></a>Comment puis-je obtenir le rapport d OneDrive d’utilisation de l’ordinateur ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. Dans la page d’accueil du tableau de bord, cliquez sur **le** bouton Afficher plus sur OneDrive carte.
  
## <a name="interpret-the-onedrive-usage-report"></a>Interpréter le rapport Utilisation de OneDrive

Vous pouvez afficher l’utilisation dans le rapport OneDrive en choisissant **l’onglet** Utilisation.<br/>![Microsoft 365 rapports d’Microsoft OneDrive d’utilisation.](../../media/3cdaf2fb-1817-479b-a0e1-2afa228690cf.png)

Sélectionnez **Sélectionner des colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![OneDrive d’utilisation : choisissez des colonnes.](../../media/9ee80f25-cfe3-411d-8e31-08f1507d18c1.png)

Vous pouvez également exporter les données du rapport dans un Excel .csv en sélectionnant le lien **Exporter.** Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. 

Le **rapport OneDrive Entreprise’utilisation** des données peut être pris en compte pour les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date du jour (et non la date à laquelle le rapport a été généré).
  
|Item|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|URL  <br/> |Adresse web de l’utilisateur OneDrive. <br/> |
|Deleted  <br/> |État de suppression du OneDrive. La suppression effective des comptes prend au minimum 7 jours.  <br/> |
|Propriétaire  <br/> |Nom d’utilisateur de l’administrateur principal du OneDrive.   <br/> |
|Nom principal du propriétaire  <br/> |Adresse de messagerie du propriétaire du OneDrive. <br/> |
|Date de la dernière activité (UTC)  <br/> | Date à laquelle une activité de fichier a été effectuée au plus tard dans le OneDrive. Si le OneDrive ne présente aucune activité de fichier, la valeur sera vide.  <br/> |
|Fichiers  <br/> |Nombre de fichiers dans la OneDrive. <br/>|
|Fichiers actifs  <br/> | Nombre de fichiers actifs au cours de la période.<br/> REMARQUE : si des fichiers ont été supprimés pendant la période spécifiée pour le rapport, le nombre de fichiers actifs affichés dans le rapport peut être supérieur au nombre actuel de fichiers dans le OneDrive. >  Les utilisateurs supprimés continueront d'apparaître dans les rapports pendant 180 jours.  <br/> |
|Stockage utilisé (Mo)  <br/> |Quantité de stockage que le OneDrive utilise en Mo. |
|||
   
> [!NOTE]
> Le rapport inclut uniquement les utilisateurs qui ont une licence OneDrive Entreprise valide.
