---
title: "Centre d'administration Microsoft 365 activité project "
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
description: Découvrez comment obtenir le rapport d’activité du projet et obtenir des insights sur l’activité project dans votre organisation.
ms.openlocfilehash: ebefa83918fa8bf31069981488baad4c7a71b365
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68722723"
---
# <a name="microsoft-365-reports-in-the-admin-center---project-activity"></a>Rapports Microsoft 365 dans le Centre d’administration - Activité du projet

Le tableau de bord Rapports Microsoft 365 vous montre la vue d’ensemble de l’activité dans les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md).

Dans le **rapport d’activité project**, vous pouvez comprendre l’activité de chaque utilisateur autorisé à utiliser Microsoft Project en examinant son interaction avec Project. Il vous aide également à comprendre le niveau de collaboration en cours en examinant le nombre de projets visités et les tâches créées ou modifiées.

## <a name="how-to-get-to-the-project-activity-report"></a>Comment accéder au rapport d’activité du projet

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** sur la carte Projet.

## <a name="interpret-the-project-activity-report"></a>Interpréter le rapport d’activité du projet

Vous pouvez utiliser ce rapport pour voir l’activité et l’utilisation de Project dans votre environnement. Ce rapport contient quatre graphiques récapitulatives :  <br/>![Rapports Microsoft 365 - Activité du projet.](../../media/project-activity.png)

- **Utilisateurs actifs** : affiche les utilisateurs actifs quotidiens sur chaque jour au fil du temps. Actuellement, cela inclut uniquement Project pour le web et client de bureau Project Online.
- **Utilisateurs actifs (par client)** : affiche les utilisateurs actifs quotidiens de chaque jour au fil du temps, répartis par client (Project pour le web ou client de bureau Project Online).
- **Activité du projet** : affiche le nombre de sessions quotidiennes de Project au fil du temps, pour chaque client (Project pour le web et client de bureau Project Online).
- **Activité de** tâche : affiche le nombre quotidien de tâches créées ou modifiées au fil du temps dans Project pour le web

Le rapport comporte également une table qui montre l’activité de chaque utilisateur de projet dans votre environnement.

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes de la table.

![Rapport d’activité du projet : choisissez des colonnes.](../../media/project-activity-columns.png)

Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie.

Le rapport **d’activité du projet** peut être consulté pour connaître les tendances des 7 derniers jours, 30 jours, 90 jours ou 180 jours. Si vous sélectionnez un jour particulier dans le rapport, la table de données par utilisateur est mise à jour en conséquence pour afficher l’utilisation des utilisateurs ce jour-là. Toutefois, cette fonctionnalité fonctionne uniquement pendant les 28 derniers jours.

### <a name="privacy-settings-impact-on-the-dashboard"></a>Impact des paramètres de confidentialité sur le tableau de bord

Si les utilisateurs ou les administrateurs ont défini leurs paramètres de confidentialité sur **Ni**, nous n’avons pas de métriques précises pour le graphique **d’activités du projet** pour le client de bureau Project Online. Les nombres affichés seront sous-numérotés. Pour plus d’informations sur les paramètres de confidentialité, consultez [Utiliser les paramètres de stratégie pour gérer les contrôles de confidentialité pour Applications Microsoft 365 pour les grandes entreprises](/deployoffice/privacy/manage-privacy-controls.md).

## <a name="user-activity-table"></a>Table d’activité utilisateur

Voici les définitions de chaque métrique dans la table d’activité de l’utilisateur.

|Élément|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|Nom d'utilisateur|Nom principal de l’utilisateur.|
|Nom d’affichage|Nom complet de l’utilisateur.|
|Date de la dernière activité|Date la plus récente à laquelle l’utilisateur de cette ligne avait une activité dans Project, y compris l’une des activités dans les rapports de synthèse.|
|Projets visités (Bureau)|Nombre de projets ouverts par l’utilisateur dans le client de bureau Project Online pendant l’intervalle de temps sélectionné en haut à droite de la page.|
|Projets visités (Web)| Nombre de tâches créées par l’utilisateur dans Project pour le web pendant l’intervalle de temps sélectionné en haut à droite de la page.|
|Tâches créées (Web)|Nombre de tâches créées par l’utilisateur dans Project pour le web pendant l’intervalle de temps sélectionné en haut à droite de la page.|
|Tâches modifiées (Web)|Nombre de tâches modifiées par l’utilisateur dans Project pour le web pendant l’intervalle de temps sélectionné en haut à droite de la page.|
|Other|Cette valeur est true si l’utilisateur a effectué une activité dans client de bureau Project Online ou dans Project pour le web (qui n’est pas couvert par les autres colonnes) dans l’intervalle de temps sélectionné en haut à droite de la page. Si ce n’est pas le cas de l’utilisateur, cette valeur est false.|
