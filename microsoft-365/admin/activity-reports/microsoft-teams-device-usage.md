---
title: Rapports Office 365 dans le centre d’administration-utilisation de l’appareil Microsoft teams
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
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
ms.assetid: 917b3e1d-203e-4439-8539-634e80196687
description: Obtenez des informations sur les applications Microsoft teams utilisées dans votre organisation en obtenant le rapport d’utilisation des applications Microsoft teams à partir des rapports Office 365.
ms.openlocfilehash: b0937e4366f1b10b0908ee8764986f2ded2999ec
ms.sourcegitcommit: 2b626a7924b4be08f6eb21181453b778e6fde418
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "43046962"
---
# <a name="office-365-reports-in-the-admin-center---microsoft-teams-device-usage"></a>Rapports Office 365 dans le centre d’administration-utilisation de l’appareil Microsoft teams

Le tableau de bord **rapports** Office 365 affiche une vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez la rubrique [Présentation des rapports](activity-reports.md). Dans le rapport Utilisation des applications Microsoft Teams, vous pouvez obtenir des informations sur les applications Microsoft Teams utilisées dans votre organisation.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, teams, Team communications ou Skype entreprise pour afficher des rapports.  
 
## <a name="how-to-get-to-the-microsoft-teams-app-usage-report"></a>Accéder au rapport Utilisation des applications Microsoft Teams

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la liste déroulante **Sélectionner un rapport** , sélectionnez **utilisation de l’appareil** **Microsoft teams** \> .
  
## <a name="interpret-the-microsoft-teams-app-usage-report"></a>Interpréter le rapport Utilisation des applications Microsoft Teams

Les graphiques **Utilisateurs** et **Distribution** donnent un aperçu de l'utilisation des applications Microsoft Teams. 
  
![Office 365 reports - Microsoft Teams app usage](../../media/de35c4de-76b4-4109-a806-66774665499b.png)
  
|||
|:-----|:-----|
|1.  <br/> |Le rapport **Utilisation de Microsoft Teams sur des appareils** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours après la date actuelle (pas la date de génération du rapport).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement les 24 à 48 heures.  <br/> |
|3.  <br/> |L'affichage **Utilisateurs** indique le nombre d'utilisateurs uniques quotidiens par application.  <br/> |
|4.  <br/> |L'affichage **Distribution** indique le nombre d'utilisateurs uniques par application sur la période sélectionnée.  <br/> |
|5.  <br/> | Dans le graphique **Utilisateurs**, l'axe Y indique le nombre d'utilisateurs par application.  <br/>  Dans le graphique **Distribution**, l'axe Y indique le nombre d'utilisateurs de l'application spécifiée.  <br/>  L'axe X représente la plage de dates sélectionnée pour ce rapport particulier.  <br/> |
|6.  <br/> |Vous pouvez filtrer la série que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, sur le graphique **utilisateurs** , sélectionnez **Windows**, **Mac**, **appels**, **Web**, **téléphone Android**ou **Windows Phone** pour afficher uniquement les informations relatives à chacun d’eux. Cette sélection ne modifie nullement les informations figurant dans le tableau grille.  <br/> ![Vous pouvez filtrer les graphiques d’utilisation de l’application Microsoft teams en sélectionnant le type d’application.](../../media/64ee1cb1-ca80-4964-8234-7fc671135c3d.png)|
|7.  <br/> | La liste des groupes affichée est déterminée par l'ensemble de tous les groupes qui ont existé (non supprimés) dans l'intervalle de temps de création de rapports (180 jours) le plus large. Le nombre d'activités varie en fonction de la date choisie.  <br/> Remarque : vous pouvez ne pas voir tous les éléments de la liste ci-dessous dans les colonnes jusqu’à ce que vous les ajoutiez.<br/> **Nom d'utilisateur** indique l'adresse de courrier de l'utilisateur. Vous pouvez afficher l'adresse de courrier réelle ou rendre ce champ anonyme.  <br/> **Date de la dernière activité (UTC)** indique la dernière date à laquelle l'utilisateur a participé à une activité Microsoft Teams dans une application.  <br/> **Supprimé** indique si l'équipe est supprimée. Si l'équipe est supprimée, mais qu'elle a connu une activité dans la période du rapport, elle apparaît dans la grille avec l'option Supprimé définie sur true.  <br/> **Date de suppression** représente la date à laquelle l'équipe a été supprimée.  <br/> L'option **Windows** est activée si l'utilisateur a été actif dans une application Windows pendant la période spécifiée.  <br/> L'option **Mac** est activée si l'utilisateur a été actif dans une application Mac pendant la période spécifiée.  <br/> L'option **Web** est activée si l'utilisateur a été actif dans une application web pendant la période spécifiée.  <br/> L'option **iOS** est activée si l'utilisateur a été actif dans une application iOS pendant la période spécifiée.  <br/> L'option **Téléphone Android** est activée si l'utilisateur a été actif dans une application pour téléphone Android pendant la période spécifiée.  <br/> L'option **Windows Phone** est activée si l'utilisateur a été actif dans une application pour Windows Phone pendant la période spécifiée.  <br/>  Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **comment masquer les détails au niveau de l’utilisateur ?** dans les [rapports d’activité du centre d’administration 365 de Microsoft](activity-reports.md).  <br/> |
|8.  <br/> |Sélectionnez **colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Teams uapp usage report - choose columns](../../media/333f3077-696d-4829-b0a7-1046b3822222.png)|
|9.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier. csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   
  

