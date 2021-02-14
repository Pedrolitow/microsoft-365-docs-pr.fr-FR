---
title: Rapports Microsoft 365 dans le Centre d’administration - Activité OneDrive Entreprise
ms.author: pebaum
author: pebaum
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- SPO_Content
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
- ODB150
- ODB160
ms.assetid: 8bbe4bf8-221b-46d6-99a5-2fb3c8ef9353
description: Obtenez le rapport d’utilisation de OneDrive pour votre organisation et connaissez l’activité de chaque utilisateur OneDrive, le nombre de fichiers partagés et l’utilisation du stockage.
ms.openlocfilehash: dd5ac1c52d2226b12c75dc92c3407012251a90da
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47948924"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-activity"></a>Rapports Microsoft 365 dans le Centre d’administration - Activité OneDrive Entreprise

Le tableau de  bord Rapports Microsoft 365 vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer des rapports au niveau de chaque produit afin d'obtenir des informations plus précises sur les activités au sein de chaque produit. Consultez [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, vous pouvez comprendre l'activité de chaque utilisateur titulaire d'une licence d'utilisation de OneDrive en examinant son interaction avec les fichiers sur OneDrive. Cela vous aide également à comprendre le niveau de la collaboration en examinant le nombre de fichiers partagés.
  
> [!NOTE]
> Certaines fonctionnalités sont introduites progressivement. Il est donc possible que cette fonctionnalité spécifique n'apparaisse pas ou soit différente de ce que décrivent les articles d'aide. Mais ne vous inquiétez pas, elle sera bientôt disponible. 
  
Si vous voulez connaître le volume d'activité et l'utilisation du stockage sur chaque compte OneDrive, consultez le [Rapport Utilisation de OneDrive](onedrive-for-business-usage.md).
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, Teams Service, Teams Communications ou Skype Entreprise pour voir les rapports.  
 
## <a name="how-do-i-get-to-the-onedrive-activity-report"></a>Comment accéder au Rapport Activité OneDrive ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la **drop-down Sélectionner un** rapport, sélectionnez Activité **OneDrive.** \> 
  
## <a name="interpret-the-onedrive-for-business-activity-report"></a>Interpréter le rapport Activité OneDrive Entreprise

Vous pouvez suivre l'activité sur OneDrive Entreprise en examinant les vues **Fichiers** et **Utilisateurs**. 
  
![OneDrive Activity Report](../../media/316b2a03-8e42-447c-aae8-080813eebe84.png)
  
|Item|Description|
|:-----|:-----|
|1.  <br/> |Le rapport **Activité OneDrive Entreprise** peut être consulté pour connaître les tendances des derniers 7, 30 , 90 ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement jusqu’aux 24 à 48 dernières heures. <br/>|
|3.  <br/> |La vue **Fichiers** affiche les numéros uniques des utilisateurs sous licence qui interagissent avec des fichiers stockés sur un compte OneDrive.  <br/> |
|4.  <br/> |La vue **Utilisateurs** affiche la tendance du nombre d'utilisateurs actifs de OneDrive. Un utilisateur est considéré comme actif s'il a eu une activité de fichier (enregistrer, synchroniser, modifier ou partager) au cours de la période spécifiée.  <br/> REMARQUE : une activité de fichier peut se produire plusieurs fois pour un seul fichier, mais ne compte qu’en tant que fichier actif. Par exemple, si vous enregistrez et synchronisez le même fichier plusieurs fois au cours d'une période spécifiée, cette activité ne compte que pour un seul fichier actif et un seul fichier synchronisé dans les données.           |
|5.  <br/> | Sur le graphique **Fichiers**, l'axe Y représente le nombre de fichiers enregistrés, synchronisés, modifiés ou partagés par un utilisateur.  <br/>  Sur le graphique **Utilisateurs**, l'axe Y indique le nombre d'utilisateurs qui ont interagi avec un fichier (enregistré, synchronisé, modifié ou partagé) sur un compte OneDrive.  <br/>  L'axe X sur tous les graphiques représente la plage de dates sélectionnée pour ce rapport particulier.  <br/> |
|6.  <br/> |Vous pouvez filtrer les séries que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique **Fichiers,** sélectionnez **Afficher,** Modifier ou Synchronisé pour afficher uniquement les informations relatives à chacun d’eux.  La modification de cette sélection ne modifie pas les informations du tableau grille.  <br/> |
|7.  <br/> | Le tableau présente une répartition des données au niveau utilisateur. Vous pouvez ajouter ou supprimer des colonnes.   <br/>  **Le nom** d’utilisateur est le nom d’utilisateur du propriétaire du compte OneDrive.  <br/> **Date de dernière activité (UTC)** indique la dernière date à laquelle une activité de fichier a été effectuée sur le compte OneDrive dans la plage de dates sélectionnée. Pour voir l'activité qui s'est produite à une date spécifique, sélectionnez celle-ci directement dans le graphique.  <br/> ![Sélectionner une date spécifique dans le graphique](../../media/29e54c4b-8dc2-4ed8-9367-1f66f2988fac.png)  <br/>  Cela permet de filtrer le tableau pour afficher les données d’activité des fichiers uniquement pour les utilisateurs qui ont effectué l’activité ce jour-là.  <br/> **Fichiers consultés ou modifiés** indique le nombre de fichiers chargés, téléchargés, modifiés ou consultés par l'utilisateur.  <br/> **Fichiers synchronisés** indique le nombre de fichiers qui ont été synchronisés à partir de l'appareil local d'un utilisateur sur le compte OneDrive.  <br/> **Les fichiers partagés en interne** sont le nombre de fichiers qui ont été partagés avec des utilisateurs au sein de l’organisation ou avec des utilisateurs au sein de groupes (qui peuvent inclure des utilisateurs externes).  <br/> **Fichiers partagés en externe** indique le nombre fichiers qui ont été partagés avec des utilisateurs extérieurs à l'organisation.  <br/> **Supprimé** indique que la licence de l'utilisateur a été supprimée.  <br/> REMARQUE : l’activité d’un utilisateur supprimé s’affiche toujours dans un rapport tant qu’il a été titulaire d’une licence à un moment ou un autre pendant la période sélectionnée. La colonne **Supprimé** permet de voir que, si l'utilisateur n'est peut-être plus actif, il a été pris en compte dans les données du rapport.<br/>**Date de suppression** indique la date à laquelle la licence de l'utilisateur a été supprimée.  <br/> **Le produit affecté** est les produits Microsoft 365 qui sont sous licence pour l’utilisateur.  <br/>  Si les stratégies de votre organisation vous empêchent d’afficher les rapports où les informations utilisateur sont identifiables, vous pouvez modifier le paramètre de confidentialité de tous ces rapports. Consultez la section **Comment puis-je masquer les détails** au niveau de l’utilisateur ? dans les rapports d’activité du Centre d’administration [Microsoft 365.](activity-reports.md)  <br/> |
|8.  <br/> |Sélectionnez **l’icône Gérer les colonnes** ![ Gérer les ](../../media/13d2e536-de88-4db3-80c7-7a3a57298eb4.png) colonnes pour ajouter ou supprimer des colonnes dans le rapport.  <br/> |
|9.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter.** Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   

