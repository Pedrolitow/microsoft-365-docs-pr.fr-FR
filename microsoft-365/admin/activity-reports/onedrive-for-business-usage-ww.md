---
title: Rapports Microsoft 365 dans le centre d’administration-utilisation de OneDrive entreprise
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: 'Obtenez le rapport d’utilisation de OneDrive entreprise à connaître sur le nombre total de fichiers et de stockage utilisés dans votre organisation. '
ms.openlocfilehash: 3855c7d06d202ee4d0590fcf5b8ca758d8120133
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48649806"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-usage"></a>Rapports Microsoft 365 dans le centre d’administration-utilisation de OneDrive entreprise

Le tableau de bord **rapports** Microsoft 365 affiche une vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, la carte OneDrive du tableau de bord offre une vue d'ensemble de ce que vous apporte OneDrive Entreprise en termes de nombre total de fichiers et d'espace de stockage utilisé au sein de votre organisation. Vous pouvez l'explorer pour connaître les tendances des comptes OneDrive actifs, le nombre de fichiers avec lesquels les utilisateurs interagissent ainsi que l'espace de stockage utilisé. Elle vous fournit également des détails pour chaque utilisateur OneDrive.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, teams, Team communications ou Skype entreprise pour afficher des rapports.  
 
## <a name="how-do-i-get-to-the-onedrive-activity-report"></a>Comment accéder au Rapport Activité OneDrive ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. À partir de la page d’accueil du tableau de bord, cliquez sur le bouton **afficher plus** sur la carte OneDrive.
  
## <a name="interpret-the-onedrive-usage-report"></a>Interpréter le rapport Utilisation de OneDrive

Vous pouvez afficher l’utilisation dans le rapport OneDrive en sélectionnant l’onglet **utilisation** .<br/>![Rapports Microsoft 365-rapport d’utilisation de Microsoft OneDrive.](../../media/3cdaf2fb-1817-479b-a0e1-2afa228690cf.png)

Sélectionnez **choisir les colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Rapport d’utilisation de OneDrive-choisir les colonnes](../../media/9ee80f25-cfe3-411d-8e31-08f1507d18c1.png)

Vous pouvez également exporter les données du rapport dans un fichier. csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. 
  
|Item|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|URL  <br/> |Adresse Web du OneDrive de l’utilisateur. <br/> |
|Deleted  <br/> |État de suppression de OneDrive. La suppression effective des comptes prend au minimum 7 jours.  <br/> |
|Propriétaire  <br/> |Nom d’utilisateur de l’administrateur principal de OneDrive.   <br/> |
|Nom de principal du propriétaire  <br/> |Adresse de messagerie du propriétaire du OneDrive. <br/> |
|Date de la dernière activité (UTC)  <br/> | Dernière date à laquelle une activité de fichier a été effectuée dans OneDrive. Si le OneDrive ne présente aucune activité de fichier, la valeur sera vide.  <br/> |
|Fichiers  <br/> |Nombre de fichiers dans OneDrive. <br/>|
|Fichiers actifs  <br/> | Nombre de fichiers actifs pendant la période de temps.<br/> Remarque : si des fichiers ont été supprimés pendant la période spécifiée pour le rapport, le nombre de fichiers actifs affichés dans le rapport peut être supérieur au nombre actuel de fichiers dans OneDrive. >  Les utilisateurs supprimés continueront d'apparaître dans les rapports pendant 180 jours.  <br/> |
|Stockage utilisé (Mo)  <br/> |Quantité de stockage utilisée par OneDrive en Mo. |
|||