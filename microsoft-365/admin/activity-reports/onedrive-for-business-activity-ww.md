---
title: 'Microsoft 365 Rapports dans le Centre d’administration : OneDrive Entreprise activité'
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Obtenez le OneDrive d’utilisation de votre organisation et connaissez l’activité de chaque utilisateur OneDrive, le nombre de fichiers partagés et l’utilisation du stockage.
ms.openlocfilehash: e9eee9ed45d397cc976c446f5fe7ceae06567b41
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60553063"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-activity"></a>Microsoft 365 Rapports dans le Centre d’administration : OneDrive Entreprise activité

Le tableau de bord Microsoft 365 **rapports de** gestion des données vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer des rapports au niveau de chaque produit afin d'obtenir des informations plus précises sur les activités au sein de chaque produit. Consultez [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, vous pouvez comprendre l'activité de chaque utilisateur titulaire d'une licence d'utilisation de OneDrive en examinant son interaction avec les fichiers sur OneDrive. Cela vous aide également à comprendre le niveau de la collaboration en examinant le nombre de fichiers partagés.

## <a name="how-do-i-get-to-the-onedrive-activity-report"></a>Comment accéder au Rapport Activité OneDrive ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. Dans la page d’accueil du tableau de bord, cliquez sur **le** bouton Afficher plus sur OneDrive carte.
  
## <a name="interpret-the-onedrive-for-business-activity-report"></a>Interpréter le rapport Activité OneDrive Entreprise

Vous pouvez afficher les activités dans le rapport OneDrive en choisissant **l’onglet** Activité.<br/>![Microsoft 365 rapports d’activité Microsoft OneDrive rapports d’activité.](../../media/c89df0b0-2611-4acf-9ef7-17cedf7977be.png)

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![OneDrive d’activité : choisissez des colonnes.](../../media/252f311f-ffde-4e5a-9158-2b822bf86964.png)

Vous pouvez également exporter les données du rapport dans un Excel .csv en sélectionnant **le** lien Exporter. Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.

Le rapport **Activité OneDrive Entreprise** peut être consulté pour connaître les tendances des derniers 7, 30 , 90 ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).
  
|Item|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|Nom d’utilisateur  <br/> |Nom d’utilisateur du propriétaire du compte OneDrive client.  <br/> |
|Date de la dernière activité (UTC)  <br/> |Date la plus récente à laquelle une activité de fichier a été effectuée sur le compte OneDrive pour la plage de dates sélectionnée. . Pour voir l'activité qui s'est produite à une date spécifique, sélectionnez celle-ci directement dans le graphique.  <br/> |
|Fichiers consultables ou modifiés  <br/> |Nombre de fichiers téléchargés, téléchargés, modifiés ou visionés par l’utilisateur.   <br/> |
|Fichiers synchronisés  <br/> |Nombre de fichiers qui ont été synchronisés à partir de l’appareil local d’un utilisateur avec OneDrive compte. <br/> |
|Fichiers partagés en interne  <br/> | Nombre de fichiers partagés avec des utilisateurs au sein de l’organisation ou avec des utilisateurs au sein de groupes (qui peuvent inclure des utilisateurs externes).  <br/> |
|Fichiers partagés en externe  <br/> |Nombre de fichiers partagés avec des utilisateurs extérieurs à l’organisation. <br/>|
|Deleted  <br/> | Cela indique que la licence de l’utilisateur a été supprimée.  <br/> REMARQUE : l’activité d’un utilisateur supprimé s’affiche toujours dans un rapport tant qu’il a été titulaire d’une licence à un moment ou un autre pendant la période sélectionnée. La colonne **Supprimé** permet de voir que, si l'utilisateur n'est peut-être plus actif, il a été pris en compte dans les données du rapport.  <br/> |
|Date de suppression  <br/> |Date à laquelle la licence de l’utilisateur a été supprimée. <br/>|
|Produit affecté  <br/> |Les Microsoft 365 qui sont sous licence pour l’utilisateur.|
|||