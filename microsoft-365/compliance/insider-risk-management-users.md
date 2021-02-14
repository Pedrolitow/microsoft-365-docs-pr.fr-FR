---
title: Tableau de bord Utilisateurs de la gestion des risques internes
description: En savoir plus sur le tableau de bord Utilisateurs de la gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 224221950104b5dee6a6e8f179db34ee6fad014e
ms.sourcegitcommit: e5ac81132cc5fd248350627a3cc7b3c640f53b6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48208770"
---
# <a name="insider-risk-management-users-dashboard"></a>Tableau de bord Utilisateurs de la gestion des risques internes

Le tableau **de bord Utilisateurs** est un outil important dans le flux de travail de gestion des risques internes et permet aux enquêteurs et aux analystes de mieux comprendre les activités de risque. Ce tableau de bord offre des vues et des fonctionnalités de gestion pour répondre aux besoins administratifs entre la création de stratégies de gestion des risques internes et la gestion des cas de gestion des risques internes.

Une fois que les utilisateurs sont ajoutés aux stratégies de gestion des risques internes, les processus en arrière-plan évaluent automatiquement les activités des utilisateurs pour déclencher [des indicateurs.](insider-risk-management-settings.md#indicators) Une fois les indicateurs déclenchés présents, les activités des utilisateurs se voit attribuer des scores de risque. Certaines de ces activités peuvent entraîner une alerte de risque interne, mais certaines activités peuvent ne pas répondre à un niveau de score de risque minimal et une alerte de risque interne ne sera pas créée. Le **tableau de bord Utilisateurs** vous permet d’afficher les utilisateurs avec ces types d’indicateurs et de scores de risque, ainsi que les utilisateurs qui ont des alertes de risque internes actives.

En outre, dans certains scénarios, vous devrez ajouter temporairement des utilisateurs aux stratégies de risques internes après qu’un événement inhabituel a été signalé en dehors du flux de travail de gestion des risques internes. Le **tableau de** bord Utilisateurs vous permet d’ajouter manuellement un utilisateur à une stratégie de risque interne pour une durée spécifique et de contourner la nécessité pour un utilisateur d’avoir un indicateur de déclenchement. Ces utilisateurs sont toujours affichés dans le tableau de bord Utilisateurs lorsqu’ils sont activement affectés à une stratégie.

En savoir plus sur la façon dont le tableau de bord Utilisateurs affiche les utilisateurs dans les scénarios suivants :

- Utilisateurs du tableau de bord avec des alertes de stratégie de risque interne actives
- Utilisateurs de tableau de bord avec indicateurs de déclenchement
- Utilisateurs du tableau de bord ajoutés temporairement aux stratégies

## <a name="dashboard-users-with-active-insider-risk-policy-alerts"></a>Utilisateurs du tableau de bord avec des alertes de stratégie de risque interne actives

Le tableau **de bord Utilisateurs** affiche automatiquement tous les utilisateurs avec des alertes de stratégie de risque internes actives. Ces utilisateurs avec des alertes ont à la fois un indicateur de déclenchement et un score de risque d’activité qui répond aux exigences de création d’une alerte de risque interne. Pour afficher les activités de ces utilisateurs,  sélectionnez l’utilisateur dans le tableau de bord Utilisateurs et naviguez jusqu’à l’onglet **Activité de l’utilisateur.**

## <a name="dashboard-users-with-triggering-indicators"></a>Utilisateurs de tableau de bord avec indicateurs de déclenchement

Le **tableau de bord Utilisateurs** affiche automatiquement tous les utilisateurs avec des indicateurs de déclenchement, mais qui n’ont pas de score de risque d’activité qui créerait une alerte de risque interne. Par exemple, un utilisateur avec une date de rendez-vous signalée s’affiche, car cet événement est un indicateur déclencheur, mais n’est pas une activité qui présente un score de risque. Pour afficher les activités de ces utilisateurs,  sélectionnez l’utilisateur dans le tableau de bord Utilisateurs et naviguez jusqu’à l’onglet **Activité de l’utilisateur.**

## <a name="dashboard-users-added-temporarily-to-policies"></a>Utilisateurs du tableau de bord ajoutés temporairement aux stratégies

Le **tableau de bord Utilisateurs** vous permet d’ajouter temporairement des utilisateurs à une stratégie de gestion des risques internes existante après un événement inhabituel en dehors du flux de travail de gestion des risques internes. L’ajout temporaire d’utilisateurs est également un moyen d’ajouter des utilisateurs à une stratégie de gestion des risques internes pour tester la stratégie, même si un connecteur requis n’est pas configuré.

Lorsqu’un utilisateur est ajouté manuellement à une stratégie, les activités de l’utilisateur des 90 jours précédents sont note et ajoutées à la chronologie **d’activité** de l’utilisateur. Par exemple, vous avez un utilisateur qui n’est pas dans l’étendue d’une stratégie de risque interne et l’utilisateur a des activités de fuite de données signalées au service juridique de votre organisation. Le service juridique vous recommande de configurer de nouvelles exigences de surveillance à court terme pour l’utilisateur. Vous pouvez affecter temporairement l’utilisateur à votre stratégie de fuite *de* données pour une durée donnée (fenêtre d’activation). Tous les utilisateurs ajoutés temporairement sont affichés dans le tableau de bord Utilisateurs, car les exigences d’indicateur de déclenchement sont annulées. 

>[!NOTE]
>L’affichage des nouveaux utilisateurs ajoutés manuellement dans le tableau de bord Utilisateurs peut prendre plusieurs **heures.** L’affichage des activités des 90 derniers jours de ces utilisateurs peut prendre jusqu’à 24 heures. Pour afficher les activités des utilisateurs ajoutés  manuellement, sélectionnez l’utilisateur dans le tableau de bord Utilisateurs et ouvrez l’onglet Activité de l’utilisateur dans le volet d’informations. 

L’utilisateur est automatiquement supprimé de la  stratégie Insider et du tableau de bord Utilisateurs lorsque l’heure définie dans la fenêtre **Activation** expire si :

- l’utilisateur n’a pas d’indicateurs de déclenchement ou d’alertes de stratégie de risque interne, et
- si la durée de la fenêtre **Activation** définie manuellement est plus longue que la durée de la fenêtre Activation de **stratégie** globale. 

Le **paramètre de la fenêtre Activation** dont la durée est la plus longue remplace toujours le paramètre de la fenêtre **Activation** avec une durée plus courte. Par exemple, vous avez configuré la fenêtre **Activation** sous l’onglet Délais de stratégie globale dans les paramètres globaux de gestion des risques internes pendant 15 jours, qui est automatiquement appliquée à toutes vos **stratégies** de risque internes. 

Vous ajoutez temporairement un utilisateur à votre stratégie de risques internes de *fuites* de données et définissez 30 jours comme fenêtre **d’activation** pour cet utilisateur. Le paramètre global de la fenêtre **Activation** de 15 jours est remplacé par la définition du paramètre de fenêtre **Activation** de 30 jours pour l’utilisateur ajouté temporairement. L’utilisateur ajouté temporairement reste  dans le tableau de bord Utilisateurs et reste dans l’étendue de la stratégie pendant 30 jours.

Dans le scénario inverse  où le paramètre  de la fenêtre Activation globale est plus long que le paramètre de fenêtre Activation défini pour un utilisateur ajouté temporairement, le paramètre de fenêtre **Activation** globale remplacerait le paramètre de fenêtre **Activation** pour l’utilisateur ajouté temporairement. L’utilisateur ajouté temporairement reste  dans le tableau de bord Utilisateurs et reste dans l’étendue de la stratégie pendant le nombre de jours défini dans les paramètres globaux de la fenêtre **Activation.**

## <a name="view-user-information-on-the-users-dashboard"></a>Afficher les informations utilisateur dans le tableau de bord Utilisateurs

Chaque utilisateur affiché dans le tableau de bord **Utilisateurs** dispose des informations suivantes :

- **Utilisateurs**: nom d’utilisateur d’un utilisateur. Ce champ est anonymisé si le paramètre d’anonymisation global pour la gestion des risques internes est activé.
- **Niveau de risque**: niveau de risque calculé actuel de l’utilisateur. Ce score est calculé toutes les 24 heures et utilise les scores de risque d’alerte de toutes les alertes actives associées à l’utilisateur. Pour les utilisateurs avec uniquement des indicateurs de déclenchement, le niveau de risque est zéro.
- **Alertes actives**: nombre d’alertes actives pour toutes les stratégies.
- **Violations confirmées**: nombre de cas résolus comme *violation* de stratégie confirmée pour l’utilisateur.
- **Cas**: cas actif actuel pour l’utilisateur.

![Tableau de bord utilisateurs de gestion des risques internes](../media/insider-risk-users-dashboard.png)

>[!NOTE]
>Le nombre d’utilisateurs  affichés dans le tableau de bord Utilisateurs peut être limité dans certains cas, en fonction du volume d’alertes actives et des stratégies correspondantes. Les utilisateurs avec des alertes actives sont affichés dans le tableau de bord Utilisateurs lorsque les alertes sont générées, et il peut y avoir de rares cas où le nombre maximal d’utilisateurs affichés est atteint.  Si cela se produit, les utilisateurs avec des alertes  actives qui ne sont pas affichées sont ajoutés au tableau de bord Utilisateurs à mesure que les alertes utilisateur existantes sont triées.

## <a name="view-user-details"></a>Afficher les détails de l’utilisateur

Pour afficher plus de détails sur l’activité de risque pour un utilisateur, ouvrez le volet d’informations utilisateur en double-cliquant sur un utilisateur dans le tableau de bord **Utilisateurs.** Dans le volet d’informations, vous pouvez afficher les informations suivantes :

- **Onglet Profil** utilisateur
    - **Nom et titre**: nom et titre de position de l’utilisateur à partir d’Azure Active Directory. Ces champs utilisateur seront rendus anonymes ou vides si le paramètre d’anonymisation global pour la gestion des risques internes est activé.
    - **Courrier électronique de** l’utilisateur : adresse de messagerie de l’utilisateur.
    - **Alias**: alias réseau de l’utilisateur.
    - **Organisation ou service :** l’organisation ou le service de l’utilisateur.

- **Onglet Activité de l’utilisateur**
    - **Historique des activités récentes des utilisateurs**: répertorie les indicateurs de déclenchement et les indicateurs de risque interne pour les activités des utilisateurs jusqu’aux 180 derniers jours. Toutes les activités pertinentes pour les indicateurs de risque internes sont également notés, même si les activités peuvent ou non avoir généré une alerte de risque interne. Le déclenchement d’exemples d’indicateurs peut être une date de départ ou la dernière date de travail prévue pour l’utilisateur. Les indicateurs de risque internes sont des activités déterminées comme étant à risque et définies dans les stratégies dans qui l’utilisateur est inclus. Les activités d’événement et de risque sont répertoriées avec l’élément le plus récent répertorié en premier.

## <a name="temporarily-add-a-user-to-a-policy"></a>Ajouter temporairement un utilisateur à une stratégie

Pour ajouter temporairement un utilisateur à une stratégie de  gestion des risques internes, vous devez utiliser l’onglet Utilisateurs de la **solution** de gestion des risques internes dans le Centre de conformité Microsoft 365. Les utilisateurs ont ajouté le contournement manuel des exigences d’indicateur déclenchant la stratégie à ajouter et sont affichés dans le tableau de bord **Utilisateurs**. Pour ajouter définitivement un utilisateur à une stratégie de gestion des risques internes, vous allez utiliser l’Assistant Stratégie.

Pour ajouter un utilisateur à une stratégie de risque interne existante, vous pouvez effectuer les étapes suivantes :

1. Dans le [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)allez à **La** gestion des risques internes et sélectionnez **l’onglet** Utilisateurs.
2. Sélectionnez **Ajouter un utilisateur à une stratégie dans** la barre d’outils.
3. Dans la **boîte de dialogue Ajouter un nouvel** utilisateur, commencez à taper un nom d’utilisateur dans le **champ** Utilisateur. Sélectionnez l’utilisateur que vous souhaitez ajouter à une stratégie.
4. Sélectionnez la flèche de la zone **Stratégie** pour afficher les stratégies de gestion des risques internes configurées. Sélectionnez la stratégie à ajouter à l’utilisateur.
5. Utilisez le **contrôle curseur de** la fenêtre Activation pour définir la durée pendant combien de temps l’utilisateur est inclus dans une stratégie et affiché dans le tableau de bord Utilisateurs. Le temps que vous spécifiez détermine la durée pendant combien de temps la stratégie est active pour cet utilisateur et démarre lorsque la première alerte est générée ou qu’un indicateur de déclenchement (comme une correspondance de stratégie DLP) est détecté. La plage de la fenêtre **Activation est** de 5 à 30 jours.
6. Sélectionnez **Ajouter,** **puis Confirmez** pour ajouter l’utilisateur à la stratégie.

>[!NOTE]
>L’affichage des nouveaux utilisateurs ajoutés manuellement dans le tableau de bord Utilisateurs peut prendre plusieurs **heures.** L’affichage des activités des 90 derniers jours de ces utilisateurs peut prendre jusqu’à 24 heures. Pour afficher les activités des utilisateurs ajoutés  manuellement, sélectionnez l’utilisateur dans le tableau de bord Utilisateurs et ouvrez l’onglet Activité de l’utilisateur dans le volet d’informations. 

## <a name="run-automated-tasks-with-power-automate-flows-for-a-user"></a>Exécuter des tâches automatisées avec des flux Power Automate pour un utilisateur

À l’aide des flux Power Automate recommandés, les enquêteurs de risque et les analystes peuvent rapidement prendre des mesures pour :

- Avertir les utilisateurs lorsqu’ils sont ajoutés à une stratégie de risque interne

Pour exécuter, gérer ou créer des flux Power Automate pour un utilisateur de gestion des risques internes :

1. Sélectionnez **Automatiser dans la** barre d’outils Action de l’utilisateur.
2. Choisissez le flux Power Automate à exécuter, puis sélectionnez **Exécuter le flux.**
3. Une fois le flux terminé, sélectionnez **Terminé.**

Pour en savoir plus sur les flux Power Automate pour la gestion des risques internes, voir Prise en charge des paramètres de [gestion des risques internes.](insider-risk-management-settings.md#power-automate-flows-preview)
