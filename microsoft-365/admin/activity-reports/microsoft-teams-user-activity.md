---
title: Rapports Microsoft 365 dans le centre d’administration-activité de l’utilisateur Microsoft teams
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
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
ms.assetid: 07f67fc4-c0a4-4d3f-ad20-f40c7f6db524
description: Découvrez comment obtenir le rapport d’activité de l’utilisateur de Microsoft teams et obtenir des informations sur l’activité de teams dans votre organisation.
ms.openlocfilehash: 59fdeec9979b939524279d938e97baf6993d3cb0
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44387668"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Rapports Microsoft 365 dans le centre d’administration-activité de l’utilisateur Microsoft teams

Le tableau de bord **rapports** Microsoft 365 affiche une vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez la rubrique [Présentation des rapports](activity-reports.md). Dans le rapport Activité de l'utilisateur sur Microsoft Teams, vous pouvez obtenir des informations sur l'activité dans Microsoft Teams au sein de votre organisation.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, teams, Team communications ou Skype entreprise pour afficher des rapports.  
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Accéder au rapport Activité de l'utilisateur sur Microsoft Teams

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la liste déroulante **Sélectionner un rapport** , sélectionnez activité de l’utilisateur **Microsoft teams** \> **User activity**.
  
## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Interpréter le rapport Activité de l'utilisateur sur Microsoft Teams

Vous pouvez visualiser l'activité d'un utilisateur sur Microsoft Teams en examinant les graphiques **Activité** et **Utilisateurs**.<br/>![Rapports Microsoft 365-activité de l’utilisateur Microsoft Teams.](../../media/40359f81-25f7-416d-bb1e-37289133ef6b.png)
  
|||
|:-----|:-----|
|1.  <br/> |Le rapport **Activité de l'utilisateur sur Microsoft Teams** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours après la date actuelle (pas la date de génération du rapport).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement les 24 à 48 heures.  <br/> |
|3.  <br/> |L'affichage **Activité** indique le nombre d'activités sur Microsoft Teams par type d'activité. Les types d'activités correspondent au nombre de messages de conversation d'équipe, de messages de conversation privée, d'appels ou de réunions.  <br/> |
|4.  <br/> |L'affichage **Utilisateurs** indique le nombre d'utilisateurs par type d'activité. Les types d'activités correspondent au nombre de messages de conversation d'équipe, de messages de conversation privée, d'appels ou de réunions.  <br/> |
|5.  <br/> | Dans le graphique **Activité**, l'axe Y est le nombre d'activités spécifiées.  <br/>  Dans le graphique **Fichiers**, l'axe Y indique le nombre d'utilisateurs participant aux conversations d'équipe, aux conversations privées, aux appels ou aux réunions.  <br/>  L'axe X représente la plage de dates sélectionnée pour ce rapport particulier.  <br/> |
|6.  <br/> |Vous pouvez filtrer la série que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique **activité** , sélectionnez **messages de canal**, **messages de conversation**, **appels**ou **réunions** pour afficher uniquement les informations relatives à chacun d’eux. Cette sélection ne modifie nullement les informations figurant dans le tableau grille.  <br/> ![Filtrer les graphiques d’activité de Microsoft teams](../../media/c819c4ea-6e9a-4411-a0dd-9f800d64ce38.png)|
|7.  <br/> | La liste des groupes affichée est déterminée par l'ensemble de tous les groupes qui ont existé (non supprimés) dans l'intervalle de temps de création de rapports (180 jours) le plus large. Le nombre d'activités varie en fonction de la date choisie.  <br/> Remarque : vous pouvez ne pas voir tous les éléments de la liste ci-dessous dans les colonnes jusqu’à ce que vous les ajoutiez.<br/>**Nom d'utilisateur** indique l'adresse de courrier de l'utilisateur. Vous pouvez afficher l'adresse de courrier réelle ou rendre ce champ anonyme.  <br/> **Date de la dernière activité (UTC)** indique la dernière date à laquelle l'utilisateur a participé à une activité sur Microsoft Teams.  <br/> **Messages de canal** indique le nombre de messages uniques que l'utilisateur a publié dans une conversation d'équipe pendant la période spécifiée.  <br/> **Messages de conversation** indique le nombre de messages uniques que l'utilisateur a publié dans une conversation privée pendant la période spécifiée.  <br/> **Appels** indique le nombre d'appels auxquels l'utilisateur a participé pendant la période spécifiée.  <br/> **Réunions** indique le nombre de réunions en ligne auxquelles l'utilisateur a participé pendant la période spécifiée.  <br/> **Autres activités** indique le nombre d'autres activités d'équipe effectuées par l'utilisateur.  <br/> **Supprimé** indique si l'équipe est supprimée. Si l'équipe est supprimée, mais qu'elle a connu une activité dans la période du rapport, elle apparaît dans la grille avec l'option Supprimé définie sur true.  <br/> **Date de suppression** représente la date à laquelle l'équipe a été supprimée.  <br/> **Produit attribué** indique la liste des produits attribués à l'utilisateur.  <br/>  Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **comment masquer les détails au niveau de l’utilisateur ?** dans les [rapports d’activité du centre d’administration 365 de Microsoft](activity-reports.md).  <br/> |
|8.  <br/> |Sélectionnez **colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Teams user activity report - choose columns](../../media/eb5fbcee-e371-4d36-a0c6-fa54732311ec.png)|
|9.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier. csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   

