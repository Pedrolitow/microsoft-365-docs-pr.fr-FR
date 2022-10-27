---
title: Centre d'administration Microsoft 365 rapports d’activité utilisateur Teams
ms.author: camillepack
author: camillepack
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Découvrez comment obtenir le rapport d’activité utilisateur Microsoft Teams et obtenir des insights sur l’activité Teams dans votre organisation.
ms.openlocfilehash: 290f280f0ffb0d4961949f46486b0c8cce84f213
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68722943"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Rapports Microsoft 365 dans le Centre d’administration - Activité des utilisateurs Microsoft Teams

Le tableau de bord Rapports Microsoft 365 vous montre la vue d’ensemble de l’activité dans les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez la rubrique [Présentation des rapports](activity-reports.md). Dans le rapport Activité de l'utilisateur sur Microsoft Teams, vous pouvez obtenir des informations sur l'activité dans Microsoft Teams au sein de votre organisation.
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Accéder au rapport Activité de l'utilisateur sur Microsoft Teams

1. Dans le Centre d’administration, accédez aux **Rapports**, puis sélectionnez **Utilisation**.

2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** de la carte d’activité Microsoft Teams.

## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Interpréter le rapport Activité de l'utilisateur sur Microsoft Teams

Vous pouvez afficher l’activité de l’utilisateur dans le rapport Teams en choisissant l’onglet **Activité de l’utilisateur** . <br/>![Rapports Microsoft 365 - Activité des utilisateurs Microsoft Teams.](../../media/user-activity-charts.png)

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.  

![Rapport d’activité utilisateur Teams : choisissez des colonnes.](../../media/user-activity-columns.png)

Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Le format exporté pour **l’heure audio**, **l’heure vidéo** et le **temps de partage d’écran** suit le format de durée ISO8601.

Le rapport **Activité de l'utilisateur sur Microsoft Teams** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, la table affiche les données pendant jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).

Pour garantir la qualité des données, nous effectuons des vérifications quotidiennes de validation des données au cours des trois derniers jours et nous comblerons les lacunes détectées. Vous remarquerez peut-être des différences dans les données historiques pendant le processus.

|Élément|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|Nom d'utilisateur  <br/> |Adresse e-mail de l’utilisateur. Vous pouvez afficher l'adresse de courrier réelle ou rendre ce champ anonyme.   <br/> |
|Nom du locataire  <br/> |Nom d’un locataire interne ou externe auquel appartient un utilisateur.   <br/> <br/> Si un utilisateur appartient à un locataire externe, les métriques de données correspondantes (par exemple, messages de publication, messages de réponse, etc.) sont calculées en fonction de leurs interactions dans les canaux partagés du locataire de l’administrateur. Les interactions effectuées par l’utilisateur dans son propre locataire (en dehors des canaux partagés du locataire donné) ne sont pas prises en compte pour le rapport d’utilisation de l’administrateur d’un locataire donné.  |
|Est externe   <br/> |Indique si l’utilisateur est un utilisateur externe ou non.   <br/> |
|Noms de locataire de canal partagé   <br/> |Noms des locataires internes ou externes des canaux partagés auxquels l’utilisateur a participé.   <br/> |
|Messages de canal   <br/> |Nombre de messages uniques que l’utilisateur a publiés dans une conversation d’équipe pendant la période spécifiée. Cela inclut les publications et les réponses d’origine.   <br/> |
|Posts   <br/> |Nombre de messages postés dans tous les canaux pendant la période spécifiée. Une publication est le message d’origine dans une conversation d’équipe.<br/> |
|Replies   <br/> |Nombre de messages ayant répondu dans tous les canaux pendant la période spécifiée. <br/> |
|Messages urgents    <br/> |Nombre de messages urgents pendant la période spécifiée. <br/> |
|Messages de conversation   <br/> |Nombre de messages uniques que l’utilisateur a publiés dans une conversation privée pendant la période spécifiée.  <br/> |
|Nombre total de réunions   <br/> |Nombre de réunions en ligne auxquelles l’utilisateur a participé au cours de la période spécifiée.  <br/> |
|Appels 1:1   <br/> | Nombre d’appels 1:1 auxquels l’utilisateur a participé pendant la période spécifiée.  <br/> |
|Date de la dernière activité (UTC)  <br/> |Date de la dernière participation de l’utilisateur à une activité Microsoft Teams.<br/> |
|Réunions ont participé ad hoc   <br/> | Nombre de réunions ad hoc auxquelles un utilisateur a participé pendant la période spécifiée.  <br/> |
|Réunions organisées ad hoc <br/> |Nombre de réunions ad hoc qu’un utilisateur a organisées pendant la période spécifiée. <br/>|
|Nombre total de réunions organisées  <br/> |Somme des réunions planifiées, périodiques, ad hoc et non classifiées qu’un utilisateur a organisées pendant la période spécifiée.  <br/> |
|Nombre total de réunions qui ont participé  <br/> |Somme des réunions planifiées, périodiques, ad hoc et non classifiées auxquelles un utilisateur a participé pendant la période spécifiée.  <br/> |
|Réunions organisées ponctuellement  <br/> |Nombre de réunions planifiées une fois qu’un utilisateur a organisées pendant la période spécifiée.  <br/> |
|Réunions organisées périodiquement planifiées  <br/> |Nombre de réunions périodiques qu’un utilisateur a organisées pendant la période spécifiée.  <br/> |
|Réunions y ont participé planifiées une seule fois  <br/> |Nombre de réunions planifiées ponctuelles auxquelles un utilisateur a participé pendant la période spécifiée.  <br/> |
|Réunions planifiées périodiques ont participé  <br/> |Nombre de réunions périodiques auxquelles un utilisateur a participé pendant la période spécifiée.  <br/> |
|Est sous licence  <br/> |Sélectionné si l’utilisateur dispose d’une licence pour utiliser Teams. <br/>|
|Autre activité  <br/>|L’utilisateur est actif, mais il a effectué d’autres activités que les types d’actions exposés proposés dans le rapport (envoi ou réponse à des messages de canal et messages de conversation, planification ou participation à des appels et réunions 1:1). Les exemples d’actions sont lorsqu’un utilisateur change l’état de Teams ou le message d’état Teams ou ouvre une publication de message de canal, mais ne répond pas.  <br/>|


## <a name="make-the-user-specific-data-anonymous"></a>Rendre les données spécifiques à l’utilisateur anonymes

Pour que les données du rapport d’activité utilisateur Teams soient anonymes, vous devez être administrateur général. Cela masque les informations d’identification (à l’aide de hachages MD5), telles que le nom d’affichage, l’e-mail et l’ID d’objet Azure Active Directory dans le rapport et leur exportation.

1. Dans Centre d'administration Microsoft 365, accédez à **Paramètres Paramètres** > **Paramètres de l’organisation**, puis sous l’onglet **Services**, choisissez **Rapports**.

2. Sélectionnez **Rapports**, puis **afficher les identificateurs anonymes**. Ce paramètre est appliqué aux rapports d’utilisation dans Centre d'administration Microsoft 365 et dans le centre d’administration Teams.

3. Sélectionnez **Enregistrer les modifications**.

## <a name="related-content"></a>Contenu associé

[Rapport d’utilisation des périphériques de Microsoft Teams](../activity-reports/microsoft-teams-device-usage-preview.md)

[Rapport d’activité d’utilisation de Microsoft Teams](../activity-reports/microsoft-teams-usage-activity.md) 
