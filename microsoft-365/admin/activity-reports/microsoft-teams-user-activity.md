---
title: Rapports Microsoft 365 dans le Centre d’administration - Activité des utilisateurs de Microsoft Teams
ms.author: kwekua
author: kwekua
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
description: Découvrez comment obtenir le rapport d’activité des utilisateurs de Microsoft Teams et obtenir des informations sur l’activité de Teams dans votre organisation.
ms.openlocfilehash: 1f45cd380813a843ad54e6552578941a9741138e
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579601"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Rapports Microsoft 365 dans le Centre d’administration - Activité des utilisateurs de Microsoft Teams

Le tableau de  bord Rapports Microsoft 365 vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez la rubrique [Présentation des rapports](activity-reports.md). Dans le rapport Activité de l'utilisateur sur Microsoft Teams, vous pouvez obtenir des informations sur l'activité dans Microsoft Teams au sein de votre organisation.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, Teams Service, Teams Communications ou Skype Entreprise pour voir les rapports.  
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Accéder au rapport Activité de l'utilisateur sur Microsoft Teams

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la **drop-down Sélectionner un rapport,** sélectionnez **Activité de** \> **l’utilisateur** Microsoft Teams.
  
## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Interpréter le rapport Activité de l'utilisateur sur Microsoft Teams

Vous pouvez visualiser l'activité d'un utilisateur sur Microsoft Teams en examinant les graphiques **Activité** et **Utilisateurs**.<br/>![Rapports Microsoft 365 - Activité des utilisateurs de Microsoft Teams.](../../media/40359f81-25f7-416d-bb1e-37289133ef6b.png)
  
|Élément|Description|
|:-----|:-----|
|1.  <br/> |Le rapport **Activité de l'utilisateur sur Microsoft Teams** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures.  <br/> |
|3.  <br/> |Pour garantir la qualité des données, nous apportons quotidiennement des vérifications de validation des données au cours des cinq derniers jours et nous remplissons les lacunes détectées. Vous remarquerez peut-être des différences dans les données historiques au cours du processus.  <br/> |
|4.  <br/> |L'affichage **Activité** indique le nombre d'activités sur Microsoft Teams par type d'activité. Les types d'activités correspondent au nombre de messages de conversation d'équipe, de messages de conversation privée, d'appels ou de réunions.  <br/> |
|5.  <br/> |L'affichage **Utilisateurs** indique le nombre d'utilisateurs par type d'activité. Les types d'activités correspondent au nombre de messages de conversation d'équipe, de messages de conversation privée, d'appels ou de réunions.  <br/> |
|6.  <br/> | Dans le **graphique d’activité,** l’axe Y est le nombre d’activités spécifiées.  <br/>  Dans le **graphique Fichiers,** l’axe Y indique le nombre d’utilisateurs participant à des conversations d’équipe, des conversations privées, des appels ou des réunions.  <br/>  L’axe X des graphiques est la plage de dates sélectionnée pour le rapport spécifique.  <br/> |
|7.  <br/> |Vous pouvez filtrer les séries que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique **d’activité,** sélectionnez **Messages** de canal, **Messages** de conversation, **Appels** ou **Réunions** pour voir uniquement les informations relatives à chacun d’eux. Cette sélection ne modifie nullement les informations figurant dans le tableau grille.  <br/> ![Filtrer les graphiques d’activité De Microsoft Teams](../../media/c819c4ea-6e9a-4411-a0dd-9f800d64ce38.png)|
|8.  <br/> | La liste des groupes affichée est déterminée par l'ensemble de tous les groupes qui ont existé (non supprimés) dans l'intervalle de temps de création de rapports (180 jours) le plus large. Le nombre d'activités varie en fonction de la date choisie.  <br/> REMARQUE : vous ne verrez peut-être pas tous les éléments de la liste ci-dessous dans les colonnes tant que vous ne les avez pas ajoutés.<br/>**Nom d'utilisateur** indique l'adresse de courrier de l'utilisateur. Vous pouvez afficher l'adresse de courrier réelle ou rendre ce champ anonyme.  <br/> **Date de la dernière activité (UTC)** indique la dernière date à laquelle l'utilisateur a participé à une activité sur Microsoft Teams.  <br/> **Messages de canal** indique le nombre de messages uniques que l'utilisateur a publié dans une conversation d'équipe pendant la période spécifiée.  <br/> **Messages de conversation** indique le nombre de messages uniques que l'utilisateur a publié dans une conversation privée pendant la période spécifiée.  <br/> **Appels** indique le nombre d'appels auxquels l'utilisateur a participé pendant la période spécifiée.  <br/> **Réunions** indique le nombre de réunions en ligne auxquelles l'utilisateur a participé pendant la période spécifiée.  <br/> **Autres activités** indique le nombre d'autres activités d'équipe effectuées par l'utilisateur.  <br/> **Supprimé** indique si l'équipe est supprimée. Si l'équipe est supprimée, mais qu'elle a connu une activité dans la période du rapport, elle apparaît dans la grille avec l'option Supprimé définie sur true.  <br/> **Date de suppression** représente la date à laquelle l'équipe a été supprimée.  <br/> **Produit attribué** indique la liste des produits attribués à l'utilisateur.  <br/>  Si les stratégies de votre organisation vous empêchent d’afficher les rapports où les informations utilisateur sont identifiables, vous pouvez modifier le paramètre de confidentialité de tous ces rapports. Consultez la section **Comment puis-je masquer les détails** au niveau de l’utilisateur ? dans les rapports d’activité du Centre d’administration [Microsoft 365.](activity-reports.md)  <br/> |
|9.  <br/> |Sélectionnez **Colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Teams user activity report - choose columns](../../media/eb5fbcee-e371-4d36-a0c6-fa54732311ec.png)|
|10.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter.** Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   

