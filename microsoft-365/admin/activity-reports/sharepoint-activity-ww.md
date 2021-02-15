---
title: Rapports Microsoft 365 dans le Centre d’administration - Activité SharePoint
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
description: Obtenez le rapport d’utilisation des activités SharePoint pour connaître l’activité de chaque utilisateur SharePoint, le nombre de fichiers partagés et l’utilisation du stockage.
ms.openlocfilehash: 1d4b288fed9e15139c92bc7e43795393d03ba2fb
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48649833"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-activity"></a>Rapports Microsoft 365 dans le Centre d’administration - Activité SharePoint

En tant qu’administrateur Microsoft  365, le tableau de bord Rapports vous présente la vue d’ensemble de l’activité sur différents produits de votre organisation. Il vous permet d'explorer pour obtenir des informations plus précises sur les activités spécifiques de chaque produit. Consultez les [rapports d’activité dans le Centre d’administration Microsoft 365.](activity-reports.md)
  
Par exemple, vous pouvez comprendre l'activité de chaque utilisateur titulaire d'une licence d'utilisation de SharePoint en examinant son interaction avec les fichiers. Cela vous aide également à comprendre le niveau de la collaboration en examinant le nombre de fichiers partagés.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, Teams Service, Teams Communications ou Skype Entreprise pour voir les rapports. 
 
## <a name="how-do-i-get-to-the-to-the-sharepoint-activity-report"></a>Comment accéder au rapport d'activité de SharePoint ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. Dans la page d’accueil du tableau de bord, cliquez sur **le** bouton Afficher plus sur la carte SharePoint.
  
## <a name="interpret-the-sharepoint-activity-report"></a>Interpréter le rapport d’activité SharePoint

Vous pouvez afficher les activités dans le rapport SharePoint en choisissant **l’onglet** Activité.<br/>![Rapports Microsoft 365 - Rapport d’activité Microsoft SharePoint.](../../media/5a0a96f-0e4f-4fb9-8baa-3262275b3d1f.png)

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Rapport d’activité SharePoint : choisir des colonnes](../../media/3c396cd1-9701-4712-8eaa-eb7bba702aa8.png)

Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant **le** lien Exporter. Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. 
  
|Item|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|Nom d’utilisateur  <br/> |Adresse de messagerie de l’utilisateur qui a effectué l’activité sur le site SharePoint.  <br/> |
|Date de la dernière activité (UTC)  <br/> |Date à laquelle une activité de fichier a été effectuée au plus tard ou à laquelle une page a été visitée pour la plage de dates sélectionnée. Pour voir l'activité qui s'est produite à une date spécifique, sélectionnez celle-ci directement dans le graphique.  <br/> |
|Fichiers consultables ou modifiés  <br/> |Nombre de fichiers téléchargés, téléchargés, modifiés ou visionés par l’utilisateur.   <br/> |
|Fichiers synchronisés  <br/> |Nombre de fichiers qui ont été synchronisés à partir de l’appareil local d’un utilisateur vers le site SharePoint. <br/> |
|Fichiers partagés en interne  <br/> | Nombre de fichiers partagés avec des utilisateurs au sein de l’organisation ou avec des utilisateurs au sein de groupes (qui peuvent inclure des utilisateurs externes).  <br/> |
|Fichiers partagés en externe  <br/> |Nombre de fichiers partagés avec des utilisateurs extérieurs à l’organisation. <br/>|
|Pages visitées  <br/> |Visites de pages uniques par l’utilisateur. <br/>|
|Deleted  <br/> | Cela indique que la licence de l’utilisateur a été supprimée.  <br/>  **REMARQUE :** L’activité d’un utilisateur supprimé s’affiche toujours dans le rapport tant qu’il a été titulaire d’une licence à un moment ou un autre pendant la période sélectionnée. La colonne Supprimé permet de voir que, si l'utilisateur n'est peut-être plus actif, il a été pris en compte dans les données du rapport.  <br/> |
|Date de suppression  <br/> |Date à laquelle la licence de l’utilisateur a été supprimée. <br/>|
|Produit affecté  <br/> |Produits Microsoft 365 sous licence pour l’utilisateur.|
|||