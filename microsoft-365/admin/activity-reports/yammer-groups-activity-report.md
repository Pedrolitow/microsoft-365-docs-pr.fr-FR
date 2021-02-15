---
title: Rapports Microsoft 365 dans le Centre d’administration - Rapport Yammer’activité des groupes
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 94dd92ec-ea73-43c6-b51f-2a11fd78aa31
description: Obtenez le Yammer d’activité des groupes de travail pour connaître le nombre de groupes Yammer créés et utilisés dans votre organisation, ainsi que leur activité.
ms.openlocfilehash: 4e579fdf6a62dafc3f9a6b58d098d9094e62226b
ms.sourcegitcommit: c51de5e1a4cb9c4a7a9854a4226b32453d9e73e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "48779192"
---
# <a name="microsoft-365-reports-in-the-admin-center---yammer-groups-activity-report"></a>Rapports Microsoft 365 dans le Centre d’administration - Rapport Yammer’activité des groupes

Le tableau de  bord Rapports Microsoft 365 vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md). Dans le rapport d'activité des groupes Yammer, vous pouvez obtenir des informations sur l'activité des groupes Yammer de votre organisation et voir combien de groupes Yammer sont créés et utilisés.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, Teams Service, Teams Communications ou Skype Entreprise pour voir les rapports.  

## <a name="how-to-get-to-the-yammer-groups-activity-report"></a>Comment accéder au rapport d'activité des groupes Yammer

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la **down select a report,** select **Yammer** \> **Groups activity**.
  
## <a name="interpret-the-yammer-groups-activity-report"></a>Interpréter le rapport d'activité des groupes Yammer

Vous pouvez visualiser l'activité des groupes Yammer en examinant les graphiques **Groupes** et **Activité**.<br/>![Yammer groups activity chart](../../media/4ba4ea03-2f74-4d86-8c63-2b18477c9769.png)
  
|Item|Description|
|:-----|:-----|
|1.  <br/> |Le rapport **Activité des groupes Yammer** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures. <br/> |
|3.  <br/> |L'affichage **Groupes** indique le nombre total de groupes qui ont existé et combien ont connu des activités de conversation de groupe.  <br/> |
|4.  <br/> |L'affichage **Activité** indique le nombre de messages Yammer publiés, lus et aimés dans des groupes.  <br/> |
|5.  <br/> | Sur le graphique **Groupes**, l'axe Y représente le nombre total de groupes ou le nombre de groupes actifs.  <br/>  Sur le graphique **Activité**, l'axe Y représente le nombre d'activités spécifiées pour les groupes Yammer.  <br/>  L'axe X sur les trois graphiques représente la plage de dates sélectionnée pour ce rapport en particulier.  <br/> |
|6.  <br/> |Vous pouvez filtrer les séries que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique **Groupes,** sélectionnez **Total** ou Total **actif** et Icônes Active pour voir uniquement les informations ![ associées à chacune ](../../media/8eebd496-5955-4419-8d53-5f3ba1ad1c88.png) d’elles.   Cette sélection ne modifie nullement les informations figurant dans le tableau grille.  <br/> |
|7.  <br/> | La liste des groupes à afficher est déterminée par l'ensemble de tous les groupes qui ont existé (non supprimés) dans l'intervalle de temps de création de rapports (180 jours) le plus large. Le nombre d'activités (messages reçus) varie en fonction de la date choisie.  <br/> REMARQUE : vous ne verrez peut-être pas tous les éléments de la liste ci-dessous dans les colonnes tant que vous ne les avez pas ajoutés.<br/>**Nom du groupe** correspond au nom du groupe.  <br/> **Administrateur de groupe** correspond au nom de l'administrateur ou du propriétaire du groupe.  <br/> **Supprimé** est le nombre de groupes Yammer supprimés. Si le groupe est supprimé, mais qu'il a connu une activité dans la période du rapport, il apparaît dans la grille avec cet indicateur défini sur true.  <br/> **Type** correspond au type de groupe, public ou privé.  <br/> **Connecté à Office 365** indique si le groupe Yammer est également un groupe Microsoft 365.  <br/> **La date de la** dernière activité est la date à laquelle un message a été lu, publié ou aimé par le groupe.  <br/> **Membres** correspond au nombre de membres du groupe.  <br/> **Publié** correspond au nombre de messages publiés dans le groupe Yammer pendant la période couverte par le rapport.  <br/> **Lu** correspond au nombre de conversations lues dans le groupe Yammer pendant la période couverte par le rapport.  <br/> **Aimé** correspond au nombre de messages aimés dans le groupe Yammer pendant la période couverte par le rapport. <br/> **Le nom du** réseau est le nom complet du réseau à qui appartient le groupe. <br/>  Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **Comment puis-je masquer les détails** au niveau de l’utilisateur ? dans rapports d’activité dans le Centre d’administration [Microsoft 365.](activity-reports.md)  <br/> |
|8.  <br/> |Sélectionnez **Colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Yammer groups activity - choose columns](../../media/c56c807f-fbc0-4d37-8bd3-e779bd0606a7.png)|
|9.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter.** Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   

