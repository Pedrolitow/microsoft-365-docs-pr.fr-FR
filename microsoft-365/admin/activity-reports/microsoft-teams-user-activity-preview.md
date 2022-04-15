---
title: Centre d'administration Microsoft 365 Teams rapports d’activité utilisateur
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Découvrez comment obtenir le rapport d’activité de l’utilisateur Microsoft Teams et obtenir des insights sur l’activité Teams dans votre organisation.
ms.openlocfilehash: cbd9bdb73dc69da5e36e0fb9c3ff2ff15b5269a4
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882261"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Rapports Microsoft 365 dans le Centre d’administration - Activité des utilisateurs Microsoft Teams

Le tableau de bord Microsoft 365 Rapports vous montre la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez la rubrique [Présentation des rapports](activity-reports.md). Dans le rapport Activité de l'utilisateur sur Microsoft Teams, vous pouvez obtenir des informations sur l'activité dans Microsoft Teams au sein de votre organisation.
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Accéder au rapport Activité de l'utilisateur sur Microsoft Teams

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** sur la carte d’activité Microsoft Teams.

## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Interpréter le rapport Activité de l'utilisateur sur Microsoft Teams

Vous pouvez afficher l’activité de l’utilisateur dans le rapport Teams en choisissant l’onglet **Activité de l’utilisateur**. <br/>![Microsoft 365 rapports : Microsoft Teams l’activité des utilisateurs.](../../media/user-activity-charts.png)

**Sélectionnez Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.  <br/> ![Teams rapport d’activité utilisateur : choisissez des colonnes.](../../media/user-activity-columns.png)

Vous pouvez également exporter les données du rapport dans un fichier Excel .csv en sélectionnant le lien **Exporter**. Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. Le format exporté pour **le temps audio**, **le temps vidéo** et le **temps de partage d’écran** suit le format de durée ISO8601.

Le rapport **Activité de l'utilisateur sur Microsoft Teams** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).

Pour garantir la qualité des données, nous effectuons des vérifications quotidiennes de validation des données au cours des trois derniers jours et nous comblerons les lacunes détectées. Vous remarquerez peut-être des différences dans les données historiques pendant le processus.

|Item|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|Nom d'utilisateur  <br/> |Adresse e-mail de l’utilisateur. Vous pouvez afficher l'adresse de courrier réelle ou rendre ce champ anonyme.   <br/> |
|Nom du locataire  <br/> |Nom d’un locataire interne ou externe auquel appartient un utilisateur.   <br/> <br/> Si un utilisateur appartient à un locataire externe, les métriques de données correspondantes (par exemple, les messages postaux, les messages de réponse, etc.) sont calculées en fonction de leurs interactions dans les canaux partagés du locataire de l’administrateur. Les interactions effectuées par l’utilisateur dans son propre locataire (en dehors des canaux partagés du locataire donné) ne sont pas prises en compte pour le rapport d’utilisation administrateur d’un locataire donné.  |
|Noms des locataires de canal partagé   <br/> |Noms des locataires internes ou externes des canaux partagés auxquels l’utilisateur a participé.   <br/> |
|Messages de canal   <br/> |Nombre de messages uniques que l’utilisateur a publiés dans une conversation d’équipe pendant la période spécifiée.  <br/> |
|Posts   <br/> |Nombre de messages postaux dans tous les canaux pendant la période spécifiée <br/> |
|Replies   <br/> |Nombre de messages répondus dans tous les canaux pendant la période spécifiée. <br/> |
|Messages urgents    <br/> |Nombre de messages urgents pendant la période spécifiée. <br/> |
|Messages de conversation   <br/> |Nombre de messages uniques que l’utilisateur a publiés dans une conversation privée pendant la période spécifiée.  <br/> |
|Nombre total de réunions   <br/> |Nombre de réunions en ligne auxquelles l’utilisateur a participé pendant la période spécifiée.  <br/> |
|Appels 1:1   <br/> | Nombre d’appels 1:1 auxquels l’utilisateur a participé pendant la période spécifiée.  <br/> |
|Date de la dernière activité (UTC)  <br/> |Dernière date à laquelle l’utilisateur a participé à une activité de Microsoft Teams.<br/> |
|Les réunions ont participé ad hoc   <br/> | Nombre de réunions ad hoc aux laquelle un utilisateur a participé pendant la période spécifiée.  <br/> |
|Réunions organisées ad hoc <br/> |Nombre de réunions ad hoc organisées par un utilisateur pendant la période spécifiée. <br/>|
|Nombre total de réunions organisées  <br/> |Somme des réunions ponctuelles planifiées, périodiques, ad hoc et non classifiées qu’un utilisateur a organisées pendant la période spécifiée.  <br/> |
|Nombre total de réunions participantes  <br/> |Somme des réunions planifiées, périodiques, ad hoc et non classifiées à laquelle un utilisateur a participé pendant la période spécifiée.  <br/> |
|Réunions organisées en une seule fois  <br/> |Nombre de réunions planifiées uniques qu’un utilisateur a organisées pendant la période spécifiée.  <br/> |
|Réunions organisées périodiquement  <br/> |Nombre de réunions périodiques organisées par un utilisateur pendant la période spécifiée.  <br/> |
|Les réunions ont participé à des réunions planifiées à usage unique  <br/> |Nombre de réunions planifiées uniques aux laquelle un utilisateur a participé pendant la période spécifiée.  <br/> |
|Les réunions ont participé à des réunions périodiques planifiées  <br/> |Nombre de réunions périodiques aux laquelle un utilisateur a participé pendant la période spécifiée.  <br/> |
|Est titulaire d’une licence  <br/> |Sélectionné si l’utilisateur dispose d’une licence pour utiliser Teams. <br/>|
|Autre activité  <br/>|L’utilisateur est actif, mais a effectué d’autres activités que les types d’actions exposés proposés dans le rapport (envoi ou réponse à des messages de canal et des messages de conversation, planification ou participation à des appels et réunions 1:1). Des exemples d’actions sont lorsqu’un utilisateur modifie l’état Teams ou le message d’état Teams ou ouvre un message de canal, mais ne répond pas.  <br/>|


## <a name="make-the-user-specific-data-anonymous"></a>Rendre les données spécifiques à l’utilisateur anonymes

Pour rendre les données dans Teams rapport d’activité utilisateur anonyme, vous devez être administrateur général. Cela masque les informations d’identification (à l’aide de hachages MD5) telles que le nom d’affichage, l’e-mail et l’ID d’objet Azure Active Directory dans le rapport et leur exportation.

1. Dans Centre d'administration Microsoft 365, accédez à **l’Paramètres Paramètres** >  **Org** et, sous l’onglet **Services**, sélectionnez **Rapports**.

2. Sélectionnez **Rapports**, puis choisissez **d’afficher les identificateurs anonymes**. Ce paramètre est appliqué aux rapports d’utilisation dans Centre d'administration Microsoft 365 et au Centre d’administration Teams.

3. Sélectionnez **Enregistrer les modifications**.


## <a name="see-also"></a>Voir aussi
[Rapport d’utilisation des périphériques de Microsoft Teams](../activity-reports/microsoft-teams-device-usage-preview.md)

[rapport d’activité d’utilisation Microsoft Teams](../activity-reports/microsoft-teams-usage-activity.md) 
