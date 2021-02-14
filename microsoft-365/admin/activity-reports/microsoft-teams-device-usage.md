---
title: Utilisation de l’appareil Microsoft Teams
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
- MST160
- MET150
- MOE150
ms.assetid: 917b3e1d-203e-4439-8539-634e80196687
description: Obtenir des informations sur les applications Microsoft Teams utilisées dans votre organisation en obtenant le rapport d’utilisation des applications Microsoft Teams à partir de Rapports Microsoft 365.
ms.openlocfilehash: 9c96f4fce962b49081cc93ff802b1e2bc250ec98
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47949107"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-device-usage"></a>Rapports Microsoft 365 dans le Centre d’administration - Utilisation des appareils Microsoft Teams

Le tableau de  bord Rapports Microsoft 365 vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez la rubrique [Présentation des rapports](activity-reports.md). Dans le rapport Utilisation des applications Microsoft Teams, vous pouvez obtenir des informations sur les applications Microsoft Teams utilisées dans votre organisation.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, Teams Service, Teams Communications ou Skype Entreprise pour voir les rapports.  
 
## <a name="how-to-get-to-the-microsoft-teams-app-usage-report"></a>Accéder au rapport Utilisation des applications Microsoft Teams

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la **drop-down Sélectionner un rapport,** sélectionnez **Utilisation des appareils Microsoft Teams.** \> 
  
## <a name="interpret-the-microsoft-teams-app-usage-report"></a>Interpréter le rapport Utilisation des applications Microsoft Teams

Les graphiques **Utilisateurs** et **Distribution** donnent un aperçu de l'utilisation des applications Microsoft Teams. 
  
![Rapports Microsoft 365 - Utilisation des applications Microsoft Teams](../../media/de35c4de-76b4-4109-a806-66774665499b.png)
  
|Item|Description|
|:-----|:-----|
|1.  <br/> |Le rapport **Utilisation de Microsoft Teams sur des appareils** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement jusqu’aux 24 à 48 dernières heures.  <br/> |
|3.  <br/> |L'affichage **Utilisateurs** indique le nombre d'utilisateurs uniques quotidiens par application.  <br/> |
|4.  <br/> |L'affichage **Distribution** indique le nombre d'utilisateurs uniques par application sur la période sélectionnée.  <br/> |
|5.  <br/> | Dans le graphique **Utilisateurs**, l'axe Y indique le nombre d'utilisateurs par application.  <br/>  Dans le graphique **Distribution**, l'axe Y indique le nombre d'utilisateurs de l'application spécifiée.  <br/>  L'axe X représente la plage de dates sélectionnée pour ce rapport particulier.  <br/> |
|6.  <br/> |Vous pouvez filtrer les séries que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique **Utilisateurs,** sélectionnez **Windows,** **Mac,** **Appels,** **Web,** **Téléphone Android** ou **Windows Phone** pour voir uniquement les informations relatives à chacun d’eux. Cette sélection ne modifie nullement les informations figurant dans le tableau grille.  <br/> ![Vous pouvez filtrer les graphiques d’utilisation des applications Microsoft Teams en sélectionnant le type d’application.](../../media/64ee1cb1-ca80-4964-8234-7fc671135c3d.png)|
|7.  <br/> | La liste des groupes affichée est déterminée par l'ensemble de tous les groupes qui ont existé (non supprimés) dans l'intervalle de temps de création de rapports (180 jours) le plus large. Le nombre d'activités varie en fonction de la date choisie.  <br/> REMARQUE : vous ne verrez peut-être pas tous les éléments de la liste ci-dessous dans les colonnes tant que vous ne les avez pas ajoutés.<br/> **Nom d'utilisateur** indique l'adresse de courrier de l'utilisateur. Vous pouvez afficher l'adresse de courrier réelle ou rendre ce champ anonyme.  <br/> **Date de la dernière activité (UTC)** indique la dernière date à laquelle l'utilisateur a participé à une activité Microsoft Teams dans une application.  <br/> **Supprimé** indique si l'équipe est supprimée. Si l'équipe est supprimée, mais qu'elle a connu une activité dans la période du rapport, elle apparaît dans la grille avec l'option Supprimé définie sur true.  <br/> **Date de suppression** représente la date à laquelle l'équipe a été supprimée.  <br/> L'option **Windows** est activée si l'utilisateur a été actif dans une application Windows pendant la période spécifiée.  <br/> L'option **Mac** est activée si l'utilisateur a été actif dans une application Mac pendant la période spécifiée.  <br/> L'option **Web** est activée si l'utilisateur a été actif dans une application web pendant la période spécifiée.  <br/> L'option **iOS** est activée si l'utilisateur a été actif dans une application iOS pendant la période spécifiée.  <br/> L'option **Téléphone Android** est activée si l'utilisateur a été actif dans une application pour téléphone Android pendant la période spécifiée.  <br/> L'option **Windows Phone** est activée si l'utilisateur a été actif dans une application pour Windows Phone pendant la période spécifiée.  <br/>  Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **Comment puis-je masquer les détails** au niveau de l’utilisateur ? dans les rapports d’activité du Centre d’administration [Microsoft 365.](activity-reports.md)  <br/> |
|8.  <br/> |Sélectionnez **Colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Teams uapp usage report - choose columns](../../media/333f3077-696d-4829-b0a7-1046b3822222.png)|
|9.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter.** Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   
  

