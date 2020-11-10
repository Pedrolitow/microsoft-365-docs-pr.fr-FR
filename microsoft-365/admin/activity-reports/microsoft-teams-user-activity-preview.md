---
title: Rapports Microsoft 365 dans le centre d’administration-activité de l’utilisateur Microsoft teams
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
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
description: Découvrez comment obtenir le rapport d’activité de l’utilisateur de Microsoft teams et obtenir des informations sur l’activité de teams dans votre organisation.
ms.openlocfilehash: b85f073a2916b646a5a03e62913de44b410ca058
ms.sourcegitcommit: 82d8be71c5861a501ac62a774b306a3fc1d4e627
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "48988469"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Rapports Microsoft 365 dans le centre d’administration-activité de l’utilisateur Microsoft teams

Le tableau de bord **rapports** Microsoft 365 affiche une vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez la rubrique [Présentation des rapports](activity-reports.md). Dans le rapport Activité de l'utilisateur sur Microsoft Teams, vous pouvez obtenir des informations sur l'activité dans Microsoft Teams au sein de votre organisation.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, teams, Team communications ou Skype entreprise pour afficher des rapports.  
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Accéder au rapport Activité de l'utilisateur sur Microsoft Teams

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. À partir de la page d’accueil du tableau de bord, cliquez sur le bouton **afficher plus** sur la fiche d’activité Microsoft Teams.

## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Interpréter le rapport Activité de l'utilisateur sur Microsoft Teams

Vous pouvez afficher l’activité de l’utilisateur dans le rapport teams en sélectionnant l’onglet activité de l' **utilisateur** . <br/>![Rapports Microsoft 365-activité de l’utilisateur Microsoft Teams.](../../media/1011877f-3cf0-4417-9447-91d0b2312aab.png)

Sélectionnez **choisir les colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Teams user activity report - choose columns](../../media/a1513028-cf09-4186-93a6-8a203cd22475.png)

Vous pouvez également exporter les données du rapport dans un fichier. csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. Le format exporté pour l’heure **audio** , l’heure **vidéo** et le **partage d’écran** suit le format de durée ISO8601.

|Item|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|Nom d'utilisateur  <br/> |Adresse e-mail de l’utilisateur. Vous pouvez afficher l'adresse de courrier réelle ou rendre ce champ anonyme.   <br/> |
|Messages de canal   <br/> |Nombre de messages uniques publiés par l’utilisateur dans une conversation d’équipe pendant la période spécifiée.  <br/> |
|Messages de conversation   <br/> |Nombre de messages uniques publiés par l’utilisateur dans une conversation privée pendant la période spécifiée.  <br/> |
|Nombre total de réunions   <br/> |Nombre de réunions en ligne auxquelles l’utilisateur a participé pendant la période spécifiée.  <br/> |
|1:1 appels   <br/> | Nombre d’appels de 1:1 auxquels l’utilisateur a participé pendant la période spécifiée.  <br/> |
|Date de la dernière activité (UTC)  <br/> |Dernière date à laquelle l’utilisateur a participé à une activité Microsoft Teams.<br/> |
|Les réunions ont participé à la adhoc   <br/> | Nombre de réunions non planifiées sur le calendrier auquel l’utilisateur a participé pendant la période spécifiée.  <br/> |
|Réunions organisées ad hoc <br/> |Nombre de réunions non planifiées dans le calendrier que l’utilisateur a organisées pendant la période spécifiée. <br/>|
|Réunions organisées planifiées  <br/> |Nombre de réunions planifiées qu’un utilisateur a organisé pendant la période spécifiée.  <br/> |
|Est sous licence |Sélectionné si l’utilisateur est titulaire d’une licence pour utiliser Teams.|
|Autres activités|L’utilisateur est actif mais a effectué d’autres activités que les types d’actions exposés dans le rapport (envoi ou réponse à des messages de canal et de conversation, planification ou participation à des appels et réunions 1:1). Exemples d’actions lorsqu’un utilisateur modifie l’état de teams ou le message d’État teams ou ouvre un message de canal, mais ne répond pas. |
|||