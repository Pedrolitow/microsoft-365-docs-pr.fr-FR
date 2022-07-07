---
title: Centre d'administration Microsoft 365 rapports d’activité SharePoint
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
description: Obtenez le rapport d’utilisation de l’activité SharePoint pour en savoir plus sur les interactions de fichiers utilisateur sous licence SharePoint, le nombre de fichiers partagés et l’utilisation du stockage.
ms.openlocfilehash: 4c330c45d3d6a0c906c3ad7e1b4d2391e3be4697
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2022
ms.locfileid: "66662615"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-activity"></a>Rapports Microsoft 365 dans le Centre d’administration - Activité SharePoint

En tant qu’administrateur Microsoft 365, le tableau de bord Rapports vous présente la vue d’ensemble de l’activité sur différents produits de votre organisation. Il vous permet d'explorer pour obtenir des informations plus précises sur les activités spécifiques de chaque produit. Consultez les [rapports d’activité dans le Centre d'administration Microsoft 365](activity-reports.md).
  
Par exemple, vous pouvez comprendre l'activité de chaque utilisateur titulaire d'une licence d'utilisation de SharePoint en examinant son interaction avec les fichiers. Cela vous aide également à comprendre le niveau de la collaboration en examinant le nombre de fichiers partagés.
  
## <a name="how-do-i-get-to-the-sharepoint-activity-report"></a>Comment faire accéder au rapport d’activité SharePoint ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** sur la carte SharePoint.
  
## <a name="interpret-the-sharepoint-activity-report"></a>Interpréter le rapport d’activité SharePoint

Vous pouvez afficher les activités dans le rapport SharePoint en choisissant l’onglet **Activité** .<br/>![Rapports Microsoft 365 - Rapport d’activité Microsoft SharePoint.](../../media/5a0a96f-0e4f-4fb9-8baa-3262275b3d1f.png)

**Sélectionnez Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport. 

![Rapport d’activité SharePoint : choisissez des colonnes.](../../media/3c396cd1-9701-4712-8eaa-eb7bba702aa8.png)

Vous pouvez également exporter les données du rapport dans un fichier Excel .csv en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie.  

Le rapport **d’activité SharePoint** peut être consulté pour connaître les tendances des 7 derniers jours, 30 jours, 90 ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).
  
|Item|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|Nom d’utilisateur  <br/> |Adresse e-mail de l’utilisateur qui a effectué l’activité sur le site SharePoint.  <br/> |
|Date de la dernière activité (UTC)  <br/> |Date la plus récente à laquelle une activité de fichier a été effectuée ou une page a été visitée pour la plage de dates sélectionnée. Pour voir l'activité qui s'est produite à une date spécifique, sélectionnez celle-ci directement dans le graphique.  <br/> |
|Fichiers affichés ou modifiés  <br/> |Nombre de fichiers que l’utilisateur a chargés, téléchargés, modifiés ou consultés.   <br/> |
|Fichiers synchronisés  <br/> |Nombre de fichiers qui ont été synchronisés entre l’appareil local d’un utilisateur et le site SharePoint. <br/> |
|Fichiers partagés en interne  <br/> | Nombre de fichiers qui ont été partagés avec des utilisateurs au sein de l’organisation ou avec des utilisateurs au sein de groupes (qui peuvent inclure des utilisateurs externes).  <br/> |
|Fichiers partagés en externe  <br/> |Nombre de fichiers qui ont été partagés avec des utilisateurs extérieurs à l’organisation. <br/>|
|Pages visitées  <br/> |Visites de pages uniques par l’utilisateur. <br/>|
|Deleted  <br/> | Cela indique que la licence de l’utilisateur a été supprimée.  <br/>  **NOTE:** L’activité d’un utilisateur supprimé s’affiche toujours dans le rapport tant qu’il a été titulaire d’une licence à un moment donné pendant la période sélectionnée. La colonne Supprimé permet de voir que, si l'utilisateur n'est peut-être plus actif, il a été pris en compte dans les données du rapport.  <br/> |
|Date de suppression  <br/> |Date à laquelle la licence de l’utilisateur a été supprimée. <br/>|
|Produit affecté  <br/> |Produits Microsoft 365 qui sont concédés sous licence à l’utilisateur.|
|||