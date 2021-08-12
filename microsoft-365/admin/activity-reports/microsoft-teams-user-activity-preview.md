---
title: Rapports Microsoft 365 dans le Centre d’administration - Activité des utilisateurs Microsoft Teams
ms.author: kwekua
author: kwekua
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
description: Découvrez comment obtenir le rapport d Microsoft Teams’activité de l’utilisateur et obtenir des informations sur l Teams de votre organisation.
ms.openlocfilehash: 945cc48b442a521a0e755e5bebf4b5a36b7eccfb696b3506a793eba0ae5de647
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53797737"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Rapports Microsoft 365 dans le Centre d’administration - Activité des utilisateurs Microsoft Teams

Le tableau de bord Microsoft 365 **rapports de** gestion des données vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez la rubrique [Présentation des rapports](activity-reports.md). Dans le rapport Activité de l'utilisateur sur Microsoft Teams, vous pouvez obtenir des informations sur l'activité dans Microsoft Teams au sein de votre organisation.
  
> [!NOTE]
> Vous devez être administrateur général, lecteur général ou lecteur de rapports dans Microsoft 365 ou administrateur Exchange, SharePoint, service Teams, Teams Communications ou administrateur Skype Entreprise pour consulter les rapports.  
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Accéder au rapport Activité de l'utilisateur sur Microsoft Teams

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Dans la page d’accueil  du tableau de bord, cliquez sur le bouton Afficher plus sur la Microsoft Teams’activité.

## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Interpréter le rapport Activité de l'utilisateur sur Microsoft Teams

Vous pouvez afficher l’activité de l’utilisateur dans Teams rapport en choisissant l’onglet **Activité de l’utilisateur.** <br/>![Microsoft 365 rapports : Microsoft Teams l’activité de l’utilisateur.](../../media/1011877f-3cf0-4417-9447-91d0b2312aab.png)

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Teams user activity report - choose columns](../../media/6d3c013e-2c5e-4d66-bb41-998aa4bd1c20.png)

Vous pouvez également exporter les données du rapport dans un Excel .csv en sélectionnant **le** lien Exporter. Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. Le format exporté pour l’heure  **audio,** l’heure **vidéo** et le partage d’écran suit le format de durée ISO8601.

Le rapport **Activité de l'utilisateur sur Microsoft Teams** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).

Pour garantir la qualité des données, nous apportons quotidiennement des vérifications de validation des données au cours des trois derniers jours et nous remplissons les lacunes détectées. Vous remarquerez peut-être des différences dans les données historiques au cours du processus.

|Item|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|Nom d'utilisateur  <br/> |Adresse e-mail de l’utilisateur. Vous pouvez afficher l'adresse de courrier réelle ou rendre ce champ anonyme.   <br/> |
|Messages de canal   <br/> |Nombre de messages uniques publiés par l’utilisateur dans une conversation d’équipe pendant la période spécifiée.  <br/> |
|Messages de conversation   <br/> |Nombre de messages uniques publiés par l’utilisateur dans une conversation privée pendant la période spécifiée.  <br/> |
|Nombre total de réunions   <br/> |Nombre de réunions en ligne à qui l’utilisateur a participé pendant la période spécifiée.  <br/> |
|Appels 1:1   <br/> | Nombre d’appels de 1:1 que l’utilisateur a participé pendant la période spécifiée.  <br/> |
|Date de la dernière activité (UTC)  <br/> |Date à laquelle l’utilisateur a participé à une activité Microsoft Teams de travail.<br/> |
|Réunions ayant participé ad hoc   <br/> | Nombre de réunions ad hoc à qui un utilisateur a participé pendant la période spécifiée.  <br/> |
|Réunions organisées ad hoc <br/> |Nombre de réunions ad hoc qu’un utilisateur a organisées pendant la période spécifiée. <br/>|
|Nombre total de réunions organisées  <br/> |Somme des réunions ponctuelles, périodiques, ad hoc et non classifiées qu’un utilisateur a organisées pendant la période spécifiée.  <br/> |
|Nombre total de réunions participées  <br/> |Somme des réunions ponctuelles, périodiques, ad hoc et non classifiées d’un utilisateur au cours de la période spécifiée.  <br/> |
|Réunions organisées en une seule fois  <br/> |Nombre de réunions programmées à une seule heure qu’un utilisateur a organisées pendant la période spécifiée.  <br/> |
|Réunions organisées périodiques  <br/> |Nombre de réunions périodiques qu’un utilisateur a organisées pendant la période spécifiée.  <br/> |
|Participations prévues à une seule fois  <br/> |Nombre de réunions prévues à une seule heure pour un utilisateur au cours de la période spécifiée.  <br/> |
|Réunions ayant participé à des réunions périodiques  <br/> |Nombre de réunions périodiques pendant la période spécifiée.  <br/> |
|Est titulaire d’une licence  <br/> |Sélectionné si l’utilisateur est titulaire d’une licence d’utilisation Teams. <br/>|
|Autre activité  <br/>|L’utilisateur est actif, mais a effectué d’autres activités que les types d’actions exposés proposés dans le rapport (envoi ou réponse aux messages de canal et aux messages de conversation, planification ou participation à des appels et réunions en une fois). Exemples d’actions : lorsqu’un utilisateur modifie l’état Teams ou le message d’état Teams ou ouvre un billet de message de canal, mais ne répond pas.  <br/>|
|réunions non classifiées <br/>|Celui qui ne peut pas être classé comme planning, périodique ou ad hoc. Leur nombre est court et ne peuvent principalement pas être identifiés en raison d’informations de télémétrie falsifiées. |
|||