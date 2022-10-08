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
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Découvrez comment obtenir le rapport d’utilisation des applications Microsoft Teams et obtenir des insights sur l’activité de l’application Teams dans votre organisation.
ms.openlocfilehash: 4306ab0c0617bfbba9336991d93305f4b68798d6
ms.sourcegitcommit: 99b174a8d431092b3cf7d650593248671297fd91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68300588"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-apps-usage-reports"></a>Rapports Microsoft 365 dans le Centre d’administration - Rapports d’utilisation des applications Microsoft Teams

Le tableau de bord Rapports Microsoft 365 affiche la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md). Dans le **rapport d’utilisation des applications Microsoft Teams**, vous pouvez obtenir des insights sur l’activité des applications Teams dans votre organisation. Cet article explique comment accéder au rapport et afficher et interpréter les différentes métriques du rapport. 

Vous pouvez utiliser ce rapport pour comprendre qui installe/utilise des applications, et approfondir les connaissances au niveau par application et par utilisateur.

## <a name="whats-in-the-report"></a>Ce qui se trouve dans le rapport

Le rapport d’utilisation des applications Teams est disponible dans le Centre d'administration Microsoft 365 et les données sont fournies par le biais de deux rapports distincts :

**Utilisation des applications** : ce rapport vous aide à répondre :
- Combien d’applications les utilisateurs de votre environnement sont-ils installés ? 
- Combien d’applications ont au moins un utilisateur actif dans votre environnement ? 
- Combien d’applications sont utilisées par la plateforme (Windows, Mac, Web ou mobile) ? 
- Combien d’utilisateurs actifs et d’équipes actives utilisent l’application ?

**Activité de l’utilisateur** : ce rapport vous aide à répondre : 
- Combien d’utilisateurs de votre environnement ont installé au moins une application ? 
- Combien d’utilisateurs de votre environnement ont utilisé au moins une application ? 
- Combien d’utilisateurs utilisent une application sur plusieurs plateformes (Windows, Mac, Web, etc.) ? 
- Combien d’applications chaque utilisateur a-t-il utilisées ?

## <a name="how-to-get-to-the-microsoft-teams-apps-usage-report"></a>Comment accéder au rapport d’utilisation des applications Microsoft Teams

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** sur la carte d’activité des applications Microsoft Teams.

    :::image type="content" source="../../media/teams-apps-tile.png" alt-text="Application Microsoft Teams.":::

## <a name="considerations"></a>Considérations

- L’affichage des données d’utilisation/d’installation d’une application nouvellement publiée peut prendre environ cinq jours. Les données d’un jour donné s’affichent dans les 48 heures. Par exemple, les données du 10 janvier doivent apparaître dans le rapport vers le 12 janvier.  

- La date de début de toutes les métriques d’installation est octobre 2021. Seules les applications installées après cette date sont comptabilisées. 

- Les ID d’application dans ce rapport sont les ID d’application externes (manifestes). Pour plus d’informations sur la façon de lier cet ID à une application dans l’expérience Gérer les applications dans Teams Administration Center, consultez [Gérer les stratégies d’installation des applications dans Microsoft Teams](/microsoftteams/teams-app-setup-policies#install-apps.md). 

- Vous pouvez exporter les données de rapport dans un fichier Excel .csv en sélectionnant le lien Exporter. Cette opération exporte des données pour tous les utilisateurs/applications et vous permet d’effectuer un tri et un filtrage simples pour une analyse plus approfondie. 


## <a name="exploring-the-report---app-usage-tab"></a>Exploration du rapport - Onglet Utilisation des applications

Vous pouvez afficher **l’utilisation de** l’application dans le rapport d’utilisation des applications Teams en choisissant l’onglet **Utilisation des applications** . <br/>

:::image type="content" source="../../media/teams-apps-usage-tab.png" alt-text="Activité des utilisateurs Teams." lightbox="../../media/teams-apps-usage-tab.png":::

En haut du rapport, vous verrez trois graphiques décrivant les tendances inter-applications au sein de votre organisation.

- Applications installées
- Applications utilisées
- Plateforme

Vous pouvez filtrer tous les graphiques selon le sélecteur d’intervalle de temps en haut à droite. 

:::image type="content" source="../../media/teams-apps-usage-filter.png" alt-text="Filtre de temps d’utilisation des applications Microsoft Teams.":::

### <a name="apps-installed"></a>Applications installées
Ce graphique affiche le nombre total d’installations d’applications au sein de votre organisation jusqu’à chaque date au cours de la période sélectionnée. Par exemple, si vous sélectionnez le 28 janvier 2022, le graphique affiche le nombre total d’installations entre octobre 2021 et le 28 janvier 2022. 

:::image type="content" source="../../media/apps-installed.png" alt-text="Applications Microsoft Teams installées.":::

### <a name="apps-used"></a>Applications utilisées
Ce graphique affiche le nombre d’applications utilisées dans votre organisation à chaque date de la période sélectionnée. Par exemple, si vous sélectionnez le 28 janvier, le graphique affiche le nombre total d’applications utilisées le 28 janvier.

:::image type="content" source="../../media/apps-used.png" alt-text="Applications Microsoft Teams utilisées.":::
  
### <a name="platform"></a>Plateforme 
Ce graphique affiche le nombre d’applications utilisées au sein de votre organisation par plateforme pour la période sélectionnée. Les plateformes disponibles sont Windows, Mac, Mobile (sur iOS et Android) et web.

:::image type="content" source="../../media/platform.png" alt-text="Plateforme Microsoft Teams.":::

### <a name="apps-usage-details-table"></a>Tableau des détails de l’utilisation des applications

Ce tableau affiche l’affichage par application avec les métriques suivantes pour chaque application. Un sous-ensemble des colonnes de métriques est inclus par défaut, et vous pouvez sélectionner/modifier la liste de colonnes en cliquant sur **Choisir des colonnes**"** en haut à droite.

:::image type="content" source="../../media/apps-usage-details.png" alt-text="Détails de l’utilisation des applications." lightbox="../../media/apps-usage-details.png":::

|**Métrique**|**Définition**|**Inclus par défaut ?**|
|:-----|:-----|:-----|
|||
|ID de l’application   <br/> |Identificateur d’application externe présent dans le manifeste de l’application.     <br/> |Oui |
|Dernière date utilisée    <br/> |Date à laquelle cette application a été utilisée pour la dernière fois par toute personne de votre organisation.   <br/> |Oui |
|Teams utilisant cette application   <br/> |Nombre d’équipes Teams distinctes qui ont au moins un utilisateur qui utilise cette application.   <br/> |Oui |
|Utilisateurs utilisant cette application    <br/> |Nombre d’utilisateurs distincts de votre organisation qui utilisent cette application.   <br/> |Oui |
|Utilisé sur Windows    <br/> | Cela indique si cette application a été utilisée sur Windows par au moins un utilisateur de votre organisation.  <br/> |Oui |
|Utilisé sur mobile  <br/> |Cela indique si cette application a été utilisée sur Mobile par au moins un utilisateur de votre organisation. <br/> |Oui |
|Utilisé sur le web   <br/> | Cela indique si cette application a été utilisée sur le web par au moins un utilisateur de votre organisation.  <br/> |Oui |
|Utilisé sur Mac <br/> |Nombre de réunions ad hoc organisées par un utilisateur pendant la période spécifiée. <br/>|Non |
|Nom de l'application  <br/> |Nom de cette application tel qu’il est présent dans le manifeste de l’application.   <br/>|Non |
|Éditeur  <br/> |Éditeur de cette application tel qu’il est présent dans le manifeste de l’application. Cette option est disponible uniquement pour les applications publiées sur le Windows Store global.  <br/>|Non |
|||

## <a name="exploring-the-report---teams-apps-usage-user-activity-tab"></a>Exploration du rapport - Onglet Activité utilisateur utilisation des applications Teams

Vous pouvez afficher **l’activité utilisateur** dans le rapport d’utilisation des applications Teams en choisissant l’onglet **Activité utilisateur** . <br/>

:::image type="content" source="../../media/teams-apps-user-activity.png" alt-text="Activité de l’utilisateur Microsoft Teams." lightbox="../../media/teams-apps-user-activity.png":::

En haut du rapport, vous verrez trois graphiques décrivant les tendances inter-applications au sein de votre organisation.

- Utilisateurs qui ont installé des applications
- Utilisateur ayant utilisé des applications
- Plateforme

Vous pouvez filtrer tous les graphiques selon le sélecteur d’intervalle de temps en haut à droite. 

:::image type="content" source="../../media/teams-apps-usage-filter.png" alt-text="Filtre de temps d’activité des utilisateurs Microsoft Teams.":::

### <a name="users-who-have-installed-apps"></a>Utilisateurs qui ont installé des applications
Ce graphique affiche le nombre total d’utilisateurs uniques qui ont installé une application jusqu’à chaque date au cours de la période sélectionnée. Par exemple, si vous sélectionnez le 28 janvier 2022, le graphique affiche le nombre total d’utilisateurs entre octobre 2021 et le 28 janvier 2022.  

:::image type="content" source="../../media/users-who-installed-apps.png" alt-text="Microsoft Teams apps Users who have installed apps chart.":::

### <a name="user-who-have-used-apps"></a>Utilisateur ayant utilisé des applications
Ce graphique affiche le nombre d’utilisateurs uniques qui ont utilisé n’importe quelle application à chaque date au cours de la période sélectionnée. Par exemple, si vous sélectionnez le 28 janvier, le graphique affiche le nombre total d’utilisateurs le 28 janvier.  

:::image type="content" source="../../media/users-who-used-apps.png" alt-text="Microsoft Teams apps Users who have used apps chart.":::

### <a name="platform"></a>Plateforme 
Ce graphique affiche le nombre d’applications utilisées au sein de votre organisation par plateforme pour la période sélectionnée. Les plateformes disponibles sont Windows, Mac, Mobile (sur iOS et Android) et web.  

:::image type="content" source="../../media/user-activity-platform.png" alt-text="Plateforme d’activité utilisateur d’utilisation de Microsoft Teams.":::
  
### <a name="user-activity-details-table"></a>Tableau des détails de l’activité utilisateur

Ce tableau affiche l’affichage par utilisateur avec les métriques suivantes pour chaque application. Un sous-ensemble des colonnes de métriques est inclus par défaut, et vous pouvez sélectionner/modifier la liste de colonnes en cliquant sur **Choisir des colonnes** en haut à droite. 

:::image type="content" source="../../media/user-activity-details.png" alt-text="Détails de l’activité de l’utilisateur." lightbox="../../media/user-activity-details.png":::

|**Métrique**|**Définition**|**Inclus par défaut ?**|
|:-----|:-----|:-----|
||||
|Nom d'utilisateur    <br/> |Nom d’utilisateur d’un utilisateur unique. La valeur est masquée par défaut.  <br/> |Oui |
|Applications installées     <br/> |Nombre d’applications uniques (dans le Store et personnalisées) que l’utilisateur a installées.   <br/> |Oui |
|Applications utilisées    <br/> |Nombre d’applications uniques (dans le Store et personnalisées) que l’utilisateur a ouvertes et/ou utilisées.    <br/> |Oui |
|Applications utilisées dans une équipe     <br/> |Nombre d’applications uniques (dans le Store et personnalisées) que l’utilisateur a ouvertes et/ou utilisées dans une équipe Teams.   <br/> |Oui |
|Utilisé sur Windows    <br/> | Cela indique si cet utilisateur a utilisé une application sur Windows.  <br/> |Oui |
|Utilisé sur mobile  <br/> |Cela indique si cet utilisateur a utilisé une application sur Mobile (iOS ou Android). <br/> |Oui |
|Utilisé sur le web   <br/> | Cela indique si cet utilisateur a utilisé une application sur le web.   <br/> |Oui |
|Utilisé sur Mac <br/> |Cela indique si cet utilisateur a utilisé une application sur Mac.  <br/>|Non |
|||

## <a name="managing-apps-in-the-teams-admin-center"></a>Gestion des applications dans le Centre de Administration Teams

Pour plus d’informations sur la gestion de vos applications Teams, consultez [À propos des applications dans Microsoft Teams](/microsoftteams/deploy-apps-microsoft-teams-landing-page.md).

Pour lier une application de ce rapport à l’expérience Gérer les applications dans Teams Administration Center, vous pouvez utiliser les éléments suivants :

- Nom de l'application
- ID d’application externe

Les ID d’application externes sont équivalents à l’ID de la page Gérer les applications pour les applications du Store. Pour les applications personnalisées, pour afficher l’ID d’application externe dans la page Gérer les applications, suivez les instructions sur [gérer les stratégies d’installation des applications dans Microsoft Teams](/microsoftteams/teams-app-setup-policies) pour ajouter la colonne dans les paramètres de colonne. Vous pouvez également l’afficher sur la page de détails de l’application pour une application personnalisée

 