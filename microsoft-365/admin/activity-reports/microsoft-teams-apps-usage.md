---
title: Centre d'administration Microsoft 365 rapports d’utilisation des applications Teams
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- Tier2
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Découvrez comment obtenir le rapport d’utilisation des applications Microsoft Teams et obtenir des insights sur l’activité des applications Teams dans votre organisation.
ms.openlocfilehash: f2135a4fd6fbb8b61406855c1f773187c1d5f794
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68723032"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-apps-usage-reports"></a>Rapports Microsoft 365 dans le centre d’administration - Rapports d’utilisation des applications Microsoft Teams

Le tableau de bord Rapports Microsoft 365 vous montre la vue d’ensemble de l’activité dans les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md). Dans le **rapport d’utilisation de l’application Microsoft Teams**, vous pouvez obtenir des insights sur l’activité des applications Teams dans votre organisation. Cet article explique comment accéder au rapport, afficher et interpréter les différentes métriques dans le rapport. 

Vous pouvez utiliser ce rapport pour comprendre qui installe/utilise des applications, et pour en savoir plus sur chaque application et par utilisateur.

## <a name="whats-in-the-report"></a>Qu’y a-t-il dans le rapport ?

Le rapport d’utilisation de l’application Teams est disponible dans le Centre d'administration Microsoft 365 et les données sont fournies par le biais de deux rapports distincts :

**Utilisation de l’application** : ce rapport vous aide à répondre aux questions suivantes :
- Combien d’applications ont des utilisateurs dans votre environnement installés ? 
- Combien d’applications ont au moins un utilisateur actif dans votre environnement ? 
- Combien d’applications sont utilisées par la plateforme (Windows, Mac, Web ou mobile) ? 
- Combien d’utilisateurs actifs et d’équipes actives utilisent l’application ?

**Activité de l’utilisateur** : ce rapport vous aide à répondre aux questions suivantes : 
- Combien d’utilisateurs dans votre environnement ont installé au moins une application ? 
- Combien d’utilisateurs dans votre environnement ont utilisé au moins une application ? 
- Combien d’utilisateurs utilisent une application sur plusieurs plateformes (Windows, Mac, Web, etc.) ? 
- Combien d’applications chaque utilisateur a-t-il utilisé ?

## <a name="how-to-get-to-the-microsoft-teams-apps-usage-report"></a>Comment accéder au rapport d’utilisation des applications Microsoft Teams

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** sur la carte d’activité des applications Microsoft Teams.

    :::image type="content" source="../../media/teams-apps-tile.png" alt-text="Application Microsoft Teams.":::

## <a name="considerations"></a>Considérations

- Les données d’utilisation/d’installation d’une application nouvellement publiée peuvent prendre environ cinq jours pour apparaître dans le rapport. Les données d’un jour donné s’affichent dans les 48 heures. Par exemple, les données du 10 janvier doivent apparaître dans le rapport vers le 12 janvier.  

- La date de début de toutes les métriques d’installation est octobre 2021. Seules les applications installées après cette date seront comptabilisées. 

- Les ID d’application dans ce rapport sont les ID d’application externes (manifeste). Pour plus d’informations sur la façon de lier cet ID à une application dans l’expérience Gérer les applications dans teams Administration Center, consultez [Gérer les stratégies de configuration des applications dans Microsoft Teams](/microsoftteams/teams-app-setup-policies#install-apps.md). 

- Vous pouvez exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien Exporter. Cela exporte des données pour tous les utilisateurs/applications et vous permet d’effectuer un tri et un filtrage simples pour une analyse plus approfondie. 


## <a name="exploring-the-report---app-usage-tab"></a>Exploration du rapport - Onglet Utilisation de l’application

Vous pouvez afficher **l’utilisation de l’application** dans le rapport d’utilisation de l’application Teams en choisissant l’onglet **Utilisation des applications** . <br/>

:::image type="content" source="../../media/teams-apps-usage-tab.png" alt-text="Activité des utilisateurs Teams." lightbox="../../media/teams-apps-usage-tab.png":::

En haut du rapport, vous verrez trois graphiques décrivant les tendances inter-applications au sein de votre organisation.

- Applications installées
- Applications utilisées
- Plateforme

Vous pouvez filtrer tous les graphiques en fonction du sélecteur d’intervalles de temps en haut à droite. 

:::image type="content" source="../../media/teams-apps-usage-filter.png" alt-text="Filtre de temps d’utilisation des applications Microsoft Teams.":::

### <a name="apps-installed"></a>Applications installées
Ce graphique montre le nombre total d’installations d’applications au sein de votre organisation jusqu’à chaque date au cours de la période sélectionnée. Par exemple, si vous sélectionnez 28 janvier 2022, le graphique affiche le nombre total d’installations entre octobre 2021 et 28 janvier 2022. 

:::image type="content" source="../../media/apps-installed.png" alt-text="Applications Microsoft Teams installées.":::

### <a name="apps-used"></a>Applications utilisées
Ce graphique montre le nombre d’applications utilisées dans votre organisation à chaque date de la période sélectionnée. Par exemple, si vous sélectionnez 28 janvier, le graphique affiche le nombre total d’applications utilisées le 28 janvier.

:::image type="content" source="../../media/apps-used.png" alt-text="Applications Microsoft Teams utilisées.":::
  
### <a name="platform"></a>Plateforme 
Ce graphique montre le nombre d’applications utilisées dans votre organisation par plateforme pour la période sélectionnée. Les plateformes disponibles sont Windows, Mac, Mobile (sur iOS et Android) et Web.

:::image type="content" source="../../media/platform.png" alt-text="Plateforme Microsoft Teams.":::

### <a name="apps-usage-details-table"></a>Tableau des détails de l’utilisation des applications

Ce tableau présente la vue par application avec les métriques suivantes pour chaque application. Un sous-ensemble des colonnes de métriques est inclus par défaut, et vous pouvez sélectionner/modifier la liste des colonnes en cliquant sur **Choisir des colonnes**"** en haut à droite.

:::image type="content" source="../../media/apps-usage-details.png" alt-text="Détails de l’utilisation des applications." lightbox="../../media/apps-usage-details.png":::

|**Métrique**|**Définition**|**Inclus par défaut ?**|
|:-----|:-----|:-----|
|||
|ID de l’application   <br/> |Identificateur d’application externe présent dans le manifeste de l’application.     <br/> |Oui |
|Date de la dernière utilisation    <br/> |Date à laquelle cette application a été utilisée pour la dernière fois par toute personne de votre organisation.   <br/> |Oui |
|Teams utilisant cette application   <br/> |Nombre d’équipes Teams distinctes qui ont au moins un utilisateur utilisant cette application.   <br/> |Oui |
|Utilisateurs utilisant cette application    <br/> |Nombre d’utilisateurs distincts de votre organisation qui utilisent cette application.   <br/> |Oui |
|Utilisé sur Windows    <br/> | Cela indique si cette application a été utilisée sur Windows par au moins un utilisateur de votre organisation.  <br/> |Oui |
|Utilisé sur mobile  <br/> |Cela indique si cette application a été utilisée sur mobile par au moins un utilisateur de votre organisation. <br/> |Oui |
|Utilisé sur le web   <br/> | Cela indique si cette application a été utilisée sur le web par au moins un utilisateur de votre organisation.  <br/> |Oui |
|Utilisé sur Mac <br/> |Nombre de réunions ad hoc qu’un utilisateur a organisées pendant la période spécifiée. <br/>|Non |
|Nom de l'application  <br/> |Nom de cette application tel qu’il figure dans le manifeste de l’application.   <br/>|Non |
|Éditeur  <br/> |L’éditeur de cette application tel qu’il est présent dans le manifeste de l’application. Cette option est uniquement disponible pour les applications publiées sur le Store global.  <br/>|Non |
|||

## <a name="exploring-the-report---teams-apps-usage-user-activity-tab"></a>Exploration du rapport - Onglet Activité utilisateur de l’utilisation des applications Teams

Vous pouvez afficher **l’activité des utilisateurs** dans le rapport d’utilisation de l’application Teams en choisissant **l’onglet Activité de l’utilisateur** . <br/>

:::image type="content" source="../../media/teams-apps-user-activity.png" alt-text="Activité des utilisateurs Microsoft Teams." lightbox="../../media/teams-apps-user-activity.png":::

En haut du rapport, vous verrez trois graphiques décrivant les tendances inter-applications au sein de votre organisation.

- Utilisateurs qui ont installé des applications
- Utilisateur ayant utilisé des applications
- Plateforme

Vous pouvez filtrer tous les graphiques en fonction du sélecteur d’intervalles de temps en haut à droite. 

:::image type="content" source="../../media/teams-apps-usage-filter.png" alt-text="Filtre de temps d’activité de l’utilisateur Microsoft Teams.":::

### <a name="users-who-have-installed-apps"></a>Utilisateurs qui ont installé des applications
Ce graphique montre le nombre total d’utilisateurs uniques qui ont installé une application jusqu’à chaque date au cours de la période sélectionnée. Par exemple, si vous sélectionnez 28 janvier 2022, le graphique affiche le nombre total d’utilisateurs entre octobre 2021 et le 28 janvier 2022.  

:::image type="content" source="../../media/users-who-installed-apps.png" alt-text="Graphique des applications Microsoft Teams Utilisateurs qui ont installé des applications.":::

### <a name="user-who-have-used-apps"></a>Utilisateur ayant utilisé des applications
Ce graphique indique le nombre d’utilisateurs uniques qui ont utilisé une application à chaque date au cours de la période sélectionnée. Par exemple, si vous sélectionnez 28 janvier, le graphique affiche le nombre total d’utilisateurs le 28 janvier.  

:::image type="content" source="../../media/users-who-used-apps.png" alt-text="Graphique des applications Microsoft Teams Utilisateurs qui ont utilisé des applications.":::

### <a name="platform"></a>Plateforme 
Ce graphique montre le nombre d’applications utilisées dans votre organisation par plateforme pour la période sélectionnée. Les plateformes disponibles sont Windows, Mac, Mobile (sur iOS et Android) et Web.  

:::image type="content" source="../../media/user-activity-platform.png" alt-text="Plateforme d’activité utilisateur d’utilisation de Microsoft Teams.":::
  
### <a name="user-activity-details-table"></a>Tableau des détails de l’activité utilisateur

Ce tableau affiche une vue par utilisateur avec les métriques suivantes pour chaque application. Un sous-ensemble des colonnes de métriques est inclus par défaut, et vous pouvez sélectionner/modifier la liste des colonnes en cliquant sur **Choisir des colonnes** en haut à droite. 

:::image type="content" source="../../media/user-activity-details.png" alt-text="Détails de l’activité de l’utilisateur." lightbox="../../media/user-activity-details.png":::

|**Métrique**|**Définition**|**Inclus par défaut ?**|
|:-----|:-----|:-----|
||||
|Nom d'utilisateur    <br/> |Nom d’utilisateur d’un utilisateur unique. La valeur est masquée par défaut.  <br/> |Oui |
|Applications installées     <br/> |Nombre d’applications uniques (dans le Windows Store et personnalisées) que l’utilisateur a installées.   <br/> |Oui |
|Applications utilisées    <br/> |Nombre d’applications uniques (dans le Windows Store et personnalisées) que l’utilisateur a ouvertes et/ou utilisées.    <br/> |Oui |
|Applications utilisées dans une équipe     <br/> |Nombre d’applications uniques (dans le Store et personnalisées) que l’utilisateur a ouvertes et/ou utilisées dans une équipe Teams.   <br/> |Oui |
|Utilisé sur Windows    <br/> | Cela indique si cet utilisateur a utilisé une application sur Windows.  <br/> |Oui |
|Utilisé sur mobile  <br/> |Cela indique si cet utilisateur a utilisé une application sur mobile (iOS ou Android). <br/> |Oui |
|Utilisé sur le web   <br/> | Cela indique si cet utilisateur a utilisé une application sur le web.   <br/> |Oui |
|Utilisé sur Mac <br/> |Cela indique si cet utilisateur a utilisé une application sur Mac.  <br/>|Non |
|||

## <a name="managing-apps-in-the-teams-admin-center"></a>Gestion des applications dans le Centre Administration Teams

Pour plus d’informations sur la gestion de vos applications Teams, consultez [À propos des applications dans Microsoft Teams](/microsoftteams/deploy-apps-microsoft-teams-landing-page.md).

Pour lier une application de ce rapport à l’expérience Gérer les applications dans teams Administration Center, vous pouvez utiliser les éléments suivants :

- Nom de l'application
- ID d’application externe

Les ID d’application externes sont équivalents à l’ID dans la page Gérer les applications pour les applications du Windows Store. Pour les applications personnalisées, pour afficher l’ID d’application externe dans la page Gérer les applications, suivez les instructions sur [Gérer les stratégies de configuration des applications dans Microsoft Teams](/microsoftteams/teams-app-setup-policies) pour ajouter la colonne dans les paramètres de colonne. Vous pouvez également l’afficher sur la page des détails de l’application pour une application personnalisée

 