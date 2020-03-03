---
title: Rapports Microsoft 365 dans le centre d’administration-activité SharePoint
ms.author: pebaum
author: pebaum
manager: pamgreen
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
- SPO160
- BSA160
ms.assetid: a91c958f-1279-499d-9959-12f0de08dc8f
description: Obtenir le rapport d’utilisation des activités SharePoint pour savoir quelle est l’activité de chaque utilisateur SharePoint, le nombre de fichiers partagés et l’utilisation du stockage.
ms.openlocfilehash: df025d41a2c570761fd59e228eebb277c922e06e
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42353425"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-activity"></a>Rapports Microsoft 365 dans le centre d’administration-activité SharePoint

En tant qu’administrateur Microsoft 365, le tableau de bord **rapports** vous montre l’activité vue d’ensemble des différents produits de votre organisation. Il vous permet d'explorer pour obtenir des informations plus précises sur les activités spécifiques de chaque produit. Consultez les [rapports d’activité dans le centre d’administration Microsoft 365](activity-reports.md).
  
Par exemple, vous pouvez comprendre l'activité de chaque utilisateur titulaire d'une licence d'utilisation de SharePoint en examinant son interaction avec les fichiers. Cela vous aide également à comprendre le niveau de la collaboration en examinant le nombre de fichiers partagés.
  
> [!NOTE]
> Certaines fonctionnalités sont introduites progressivement. Il se peut donc que cette fonctionnalité n'apparaisse pas ou soit différente de ce qui est décrit dans les articles d'aide. Mais ne vous inquiétez pas. Si vous ne la voyez pas encore, elle sera bientôt disponible. 
  
Si vous voulez connaître le volume d'activité sur chaque site SharePoint et l'utilisation du stockage, consultez le [Rapport Utilisation du site SharePoint](sharepoint-site-usage.md).
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint ou Skype entreprise pour afficher des rapports. 
 
## <a name="how-do-i-get-to-the-to-the-sharepoint-activity-report"></a>Comment accéder au rapport d'activité de SharePoint ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la liste déroulante **Sélectionner un rapport** , sélectionnez **activité** **SharePoint** \> .
  
## <a name="interpreting-the-sharepoint-activity-report"></a>Interprétation du rapport d'activité de SharePoint

Vous pouvez voir l'activité de SharePoint en examinant les vues **Fichiers** et **Utilisateurs**.<br/> ![SharePoint Activity Report](../../media/96ee85af-f213-499b-9e2b-22912bd0b8c2.png)
  
|||
|:-----|:-----|
|1.  <br/> |Le **rapport d'activité de SharePoint** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours après la date actuelle (pas la date de génération du rapport).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement les 24 à 48 heures.  <br/> |
|3.  <br/> |La vue **Fichiers** affiche les numéros uniques des utilisateurs sous licence qui interagissent avec des fichiers stockés sur des sites SharePoint.  <br/> |
|4.  <br/> |La vue **Pages** indique le nombre de pages uniques consultées par les utilisateurs.  <br/> |
|5.  <br/> |La vue **Utilisateurs** affiche la tendance du nombre d'utilisateurs actifs. Un utilisateur est considéré comme actif s'il a eu une activité de fichier (enregistrer, synchroniser, modifier ou partager) ou consulté une page au cours de la période spécifiée.  <br/> Remarque : une activité de fichier peut se produire plusieurs fois pour un seul fichier, mais ne comptera qu’en tant que fichier actif. Par exemple, si vous enregistrez et synchronisez le même fichier plusieurs fois sur une période de temps spécifiée, cette activité ne compte que pour un seul fichier actif et un seul fichier synchronisé dans les données.           |
|6.  <br/> | Sur le graphique **Fichiers**, l'axe Y indique le nombre de fichiers qu'un utilisateur a enregistrés, synchronisés, modifiés ou partagés.  <br/>  Sur le graphique **Utilisateurs**, l'axe Y indique le nombre d'utilisateurs qui ont interagi avec un fichier (enregistré, synchronisé, modifié ou partagé) sur un site.  <br/>  Sur le graphique **Pages**, l'axe X représente le nombre de pages uniques consultées par les utilisateurs.  <br/>  L'axe X sur tous les graphiques représente la plage de dates sélectionnée pour ce rapport particulier.  <br/> |
|7.  <br/> |Vous pouvez filtrer la série que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique **fichiers** , sélectionnez **visionné ou modifié**, **synchronisé**, **partagé en interne**ou partagé en **externe** pour afficher uniquement les informations relatives à chacun d’eux. Cette sélection ne modifie nullement les informations figurant dans le tableau grille.  <br/> |
|8.  <br/> | Le tableau montre une répartition des activités au niveau du site.  <br/>  <br/> **Username** est l’adresse de messagerie de l’utilisateur qui a effectué l’activité sur le site SharePoint.  <br/> **Date de dernière activité (UTC)** indique la dernière date à laquelle une activité a été effectuée sur un fichier ou une page a été consultée dans la plage de dates sélectionnée. Pour voir l'activité qui s'est produite à une date spécifique, sélectionnez celle-ci directement dans le graphique.  <br/> ![Sélection d’une date spécifique dans le graphique](../../media/29e54c4b-8dc2-4ed8-9367-1f66f2988fac.png) <br/> Cette opération filtre le tableau pour afficher les données d’activité des fichiers uniquement pour les utilisateurs ayant effectué l’activité à ce jour spécifique.  <br/>  **Fichiers consultés ou modifiés** indique le nombre de fichiers chargés, téléchargés, modifiés ou consultés par l'utilisateur.  <br/>  **Fichiers synchronisés** indique le nombre de fichiers qui ont été synchronisés à partir de l’appareil local d’un utilisateur sur le site SharePoint.  <br/>  Les **fichiers partagés en interne** sont le nombre de fichiers qui ont été partagés avec des utilisateurs au sein de l’organisation ou avec des utilisateurs appartenant à des groupes (qui peuvent inclure des utilisateurs externes).  <br/>  **Fichiers partagés en externe** indique le nombre fichiers qui ont été partagés avec des utilisateurs extérieurs à l'organisation.  <br/>  Les **pages visitées** sont les visites de pages uniques par l’utilisateur.  <br/>  **Supprimé** indique que la licence de l'utilisateur a été supprimée.  <br/>  **Remarque :** L’activité d’un utilisateur supprimé continuera de s’afficher dans le rapport tant qu’il était titulaire d’une licence à un moment donné au cours de la période sélectionnée. La colonne Supprimé permet de voir que, si l'utilisateur n'est peut-être plus actif, il a été pris en compte dans les données du rapport.  <br/> **Date de suppression** indique la date à laquelle la licence de l'utilisateur a été supprimée.  <br/>  Le **produit affecté** est les produits Microsoft 365 qui sont sous licence pour l’utilisateur.  <br/> |
|9.  <br/> |Sélectionnez l' **** icône ![gérer les colonnes gérer](../../media/13d2e536-de88-4db3-80c7-7a3a57298eb4.png) les colonnes pour ajouter ou supprimer des colonnes dans le rapport.  <br/> |
|10.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier. csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2 000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   

