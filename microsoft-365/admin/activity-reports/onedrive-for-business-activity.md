---
title: Rapports Microsoft 365 dans le centre d’administration-activité OneDrive entreprise
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
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
- ODB150
- ODB160
ms.assetid: 8bbe4bf8-221b-46d6-99a5-2fb3c8ef9353
description: Obtenir le rapport d’utilisation de OneDrive pour votre organisation et connaître l’activité de chaque utilisateur OneDrive, le nombre de fichiers partagés et l’utilisation du stockage.
ms.openlocfilehash: 2c755a9a5cf2f2085ec02029387a884f38aecb53
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42239505"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-activity"></a>Rapports Microsoft 365 dans le centre d’administration-activité OneDrive entreprise

Le tableau de bord **rapports** Microsoft 365 affiche une vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer des rapports au niveau de chaque produit afin d'obtenir des informations plus précises sur les activités au sein de chaque produit. Consultez [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, vous pouvez comprendre l'activité de chaque utilisateur titulaire d'une licence d'utilisation de OneDrive en examinant son interaction avec les fichiers sur OneDrive. Cela vous aide également à comprendre le niveau de la collaboration en examinant le nombre de fichiers partagés.
  
> [!NOTE]
> Certaines fonctionnalités sont introduites progressivement. Il est donc possible que cette fonctionnalité spécifique n'apparaisse pas ou soit différente de ce que décrivent les articles d'aide. Mais ne vous inquiétez pas, elle sera bientôt disponible. 
  
Si vous voulez connaître le volume d'activité et l'utilisation du stockage sur chaque compte OneDrive, consultez le [Rapport Utilisation de OneDrive](onedrive-for-business-usage.md).
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint ou Skype entreprise pour afficher des rapports. 
 
## <a name="how-do-i-get-to-the-onedrive-activity-report"></a>Comment accéder au Rapport Activité OneDrive ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la liste déroulante **Sélectionner un rapport** , sélectionnez **activité** **OneDrive** \> .
  
## <a name="interpret-the-onedrive-for-business-activity-report"></a>Interpréter le rapport Activité OneDrive Entreprise

Vous pouvez suivre l'activité sur OneDrive Entreprise en examinant les vues **Fichiers** et **Utilisateurs**. 
  
![OneDrive Activity Report](../media/316b2a03-8e42-447c-aae8-080813eebe84.png)
  
|||
|:-----|:-----|
|1.  <br/> |Le rapport **Activité OneDrive Entreprise** peut être consulté pour connaître les tendances des derniers 7, 30 , 90 ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours après la date actuelle (pas la date de génération du rapport).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement les 24 à 48 heures. <br/>|
|3.  <br/> |La vue **Fichiers** affiche les numéros uniques des utilisateurs sous licence qui interagissent avec des fichiers stockés sur un compte OneDrive.  <br/> |
|4.  <br/> |La vue **Utilisateurs** affiche la tendance du nombre d'utilisateurs actifs de OneDrive. Un utilisateur est considéré comme actif s'il a eu une activité de fichier (enregistrer, synchroniser, modifier ou partager) au cours de la période spécifiée.  <br/> Remarque : une activité de fichier peut se produire plusieurs fois pour un seul fichier, mais seulement comme un seul fichier actif. Par exemple, si vous enregistrez et synchronisez le même fichier plusieurs fois au cours d'une période spécifiée, cette activité ne compte que pour un seul fichier actif et un seul fichier synchronisé dans les données.           |
|5.  <br/> | Sur le graphique **Fichiers**, l'axe Y représente le nombre de fichiers enregistrés, synchronisés, modifiés ou partagés par un utilisateur.  <br/>  Sur le graphique **Utilisateurs**, l'axe Y indique le nombre d'utilisateurs qui ont interagi avec un fichier (enregistré, synchronisé, modifié ou partagé) sur un compte OneDrive.  <br/>  L'axe X sur tous les graphiques représente la plage de dates sélectionnée pour ce rapport particulier.  <br/> |
|6.  <br/> |Vous pouvez filtrer la série que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique **fichiers** , sélectionnez **visionné ou modifié** ou **synchronisé** pour afficher uniquement les informations relatives à chacun d’eux. La modification de cette sélection ne modifie pas les informations du tableau grille.  <br/> |
|7.  <br/> | Le tableau présente une répartition des données au niveau utilisateur. Vous pouvez ajouter ou supprimer des colonnes.   <br/>  **Username** est le nom d’utilisateur du propriétaire du compte OneDrive.  <br/> **Date de dernière activité (UTC)** indique la dernière date à laquelle une activité de fichier a été effectuée sur le compte OneDrive dans la plage de dates sélectionnée. Pour voir l'activité qui s'est produite à une date spécifique, sélectionnez celle-ci directement dans le graphique.  <br/> ![Sélection d’une date spécifique dans le graphique](../media/29e54c4b-8dc2-4ed8-9367-1f66f2988fac.png)  <br/>  Cette opération filtre le tableau pour afficher les données d’activité des fichiers uniquement pour les utilisateurs ayant effectué l’activité à ce jour spécifique.  <br/> **Fichiers consultés ou modifiés** indique le nombre de fichiers chargés, téléchargés, modifiés ou consultés par l'utilisateur.  <br/> **Fichiers synchronisés** indique le nombre de fichiers qui ont été synchronisés à partir de l'appareil local d'un utilisateur sur le compte OneDrive.  <br/> Les **fichiers partagés en interne** sont le nombre de fichiers qui ont été partagés avec des utilisateurs au sein de l’organisation ou avec des utilisateurs au sein de groupes (qui peuvent inclure des utilisateurs externes).  <br/> **Fichiers partagés en externe** indique le nombre fichiers qui ont été partagés avec des utilisateurs extérieurs à l'organisation.  <br/> **Supprimé** indique que la licence de l'utilisateur a été supprimée.  <br/> Remarque : l’activité d’un utilisateur supprimé reste affichée dans un rapport tant qu’il a été concédé sous licence à un moment donné au cours de la période sélectionnée. La colonne **Supprimé** permet de voir que, si l'utilisateur n'est peut-être plus actif, il a été pris en compte dans les données du rapport.<br/>**Date de suppression** indique la date à laquelle la licence de l'utilisateur a été supprimée.  <br/> Le **produit affecté** est les produits Microsoft 365 qui sont sous licence pour l’utilisateur.  <br/>  Si les stratégies de votre organisation vous empêchent d’afficher des rapports où les informations utilisateur sont identifiables, vous pouvez modifier le paramètre de confidentialité de tous ces rapports. Consultez la section **comment masquer les détails au niveau de l’utilisateur ?** dans les [rapports d’activité du centre d’administration 365 de Microsoft](activity-reports.md).  <br/> |
|8.  <br/> |Sélectionnez l' **** icône ![gérer les colonnes gérer](../media/13d2e536-de88-4db3-80c7-7a3a57298eb4.png) les colonnes pour ajouter ou supprimer des colonnes dans le rapport.  <br/> |
|9.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier. csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   

