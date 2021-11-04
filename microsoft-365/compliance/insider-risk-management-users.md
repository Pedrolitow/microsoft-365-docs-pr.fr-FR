---
title: Tableau de bord Utilisateurs de la gestion des risques internes
description: En savoir plus sur le tableau de bord Utilisateurs de la gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 59cfde5027e1dbee8ae4ed4d8a0494e1fd5c11c5
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2021
ms.locfileid: "60787105"
---
# <a name="insider-risk-management-users-dashboard"></a>Tableau de bord Utilisateurs de la gestion des risques internes

Le tableau **de bord Utilisateurs** est un outil important dans le flux de travail de gestion des risques internes et permet aux enquêteurs et aux analystes de mieux comprendre les activités de risque. Ce tableau de bord offre des vues et des fonctionnalités de gestion pour répondre aux besoins administratifs entre la création de stratégies de gestion des risques internes et la gestion des cas de gestion des risques internes.

Une fois que les utilisateurs sont ajoutés aux stratégies de gestion des risques internes, les processus en arrière-plan évaluent automatiquement les activités des utilisateurs pour déclencher [des indicateurs.](insider-risk-management-settings.md#indicators) Une fois les indicateurs déclenchés présents, les activités des utilisateurs se voit attribuer des scores de risque. Certaines de ces activités peuvent entraîner une alerte de risque interne, mais certaines activités peuvent ne pas répondre à un niveau de score de risque minimal et une alerte de risque interne ne sera pas créée. Le **tableau de bord Utilisateurs** vous permet d’afficher les utilisateurs avec ces types d’indicateurs et de scores de risque, ainsi que les utilisateurs qui ont des alertes de risque internes actives.

En savoir plus sur la façon dont le tableau de bord Utilisateurs affiche les utilisateurs dans les scénarios suivants :

- Utilisateurs avec des alertes de stratégie de risque internes actives
- Utilisateurs avec déclenchement d’événements
- Utilisateurs ajoutés temporairement aux stratégies

## <a name="users-with-active-insider-risk-policy-alerts"></a>Utilisateurs avec des alertes de stratégie de risque internes actives

Le tableau **de bord Utilisateurs** affiche automatiquement tous les utilisateurs avec des alertes de stratégie de risque internes actives. Ces utilisateurs avec des alertes ont à la fois un indicateur de déclenchement et un score de risque d’activité qui répond aux exigences de création d’une alerte de risque interne. Pour afficher les activités de ces utilisateurs,  sélectionnez l’utilisateur dans le tableau de bord Utilisateurs et naviguez jusqu’à l’onglet **Activité de l’utilisateur.**

## <a name="users-with-triggering-events"></a>Utilisateurs avec déclenchement d’événements

Le **tableau de bord Utilisateurs** affiche automatiquement tous les utilisateurs avec des événements déclencheurs, mais qui n’ont pas de score de risque d’activité qui créerait une alerte de risque interne. Par exemple, un utilisateur avec une date de clôture signalée s’affiche, car cette activité est un événement déclencheur, mais n’est pas une activité qui présente un score de risque. Pour afficher les activités de ces utilisateurs,  sélectionnez l’utilisateur dans le tableau de bord Utilisateurs et naviguez jusqu’à l’onglet **Activité de l’utilisateur.**

## <a name="users-added-temporarily-to-policies"></a>Utilisateurs ajoutés temporairement aux stratégies

Le tableau **de bord Utilisateurs inclut** les utilisateurs ajoutés aux stratégies de gestion des risques internes après un événement inhabituel en dehors du flux de travail de gestion des risques internes. L’ajout temporaire d’utilisateurs (à partir du tableau de bord Stratégies) est également un moyen de commencer à marquer l’activité des utilisateurs pour une stratégie de gestion des risques internes pour tester la stratégie, même si aucun connecteur requis n’est configuré.

Lorsqu’un utilisateur est ajouté manuellement à une stratégie, les activités de l’utilisateur pour les 90 jours précédents sont marqués et ajoutés à la chronologie **d’activité** de l’utilisateur. Par exemple, aucun score de risque n’est actuellement attribué à un utilisateur pour une stratégie de risque interne et les activités de fuite de données sont signalées au service juridique de votre organisation. Le service juridique recommande de configurer de nouvelles exigences de surveillance à court terme pour l’utilisateur. Vous pouvez affecter temporairement l’utilisateur à votre stratégie de fuite *de* données pour une durée donnée (fenêtre d’activation). Tous les utilisateurs ajoutés temporairement sont affichés dans le tableau de bord Utilisateurs car le déclenchement des exigences d’événement est annulé. 

> [!NOTE]
> L’affichage des nouveaux utilisateurs ajoutés manuellement dans le tableau de bord Utilisateurs peut prendre plusieurs **heures.** L’affichage des activités des 90 jours précédents de ces utilisateurs peut prendre jusqu’à 24 heures. Pour afficher les activités des utilisateurs ajoutés  manuellement, sélectionnez l’utilisateur dans le tableau de bord Utilisateurs et ouvrez l’onglet Activité de l’utilisateur dans le volet d’informations. 

L’utilisateur est automatiquement supprimé  du tableau de bord Utilisateurs et le score s’arrête lorsque l’heure définie dans la fenêtre **Activation** expire si :

- l’utilisateur n’a pas d’autres événements déclencheurs ou alertes de stratégie de risque interne, et
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

Pour localiser rapidement un utilisateur spécifique, utilisez **la** recherche en haut à droite du tableau de bord de l’utilisateur. Lorsque vous recherchez des utilisateurs, vous devez utiliser le nom d’utilisateur principal (UPN). Par exemple, lorsque vous recherchez un utilisateur nommé « Tiara Hidayah » dont l’UPN est « thidayah » dans votre organisation, vous entrez « thidayah » ou une partie de l’UPN dans la **recherche.**

![Tableau de bord utilisateurs de gestion des risques internes.](../media/insider-risk-users-dashboard.png)

> [!NOTE]
> Le nombre d’utilisateurs  affichés dans le tableau de bord Utilisateurs peut être limité dans certains cas, en fonction du volume d’alertes actives et des stratégies correspondantes. Les utilisateurs avec des alertes actives sont affichés dans le tableau de bord Utilisateurs lorsque les alertes sont générées, et il peut y avoir de rares cas où le nombre maximal d’utilisateurs affichés est atteint.  Si cette limite se produit, les utilisateurs avec des alertes  actives qui ne sont pas affichées sont ajoutés au tableau de bord Utilisateurs à mesure que les alertes utilisateur existantes sont triées.

## <a name="view-user-details"></a>Afficher les détails de l’utilisateur

Pour afficher plus de détails sur l’activité de risque pour un utilisateur, ouvrez le volet d’informations utilisateur en double-cliquant sur un utilisateur dans le tableau de bord **Utilisateurs.** Dans le volet d’informations, vous pouvez afficher les informations suivantes :

- **Onglet Profil** utilisateur
  - **Nom et titre**: le nom et le titre de position de l’utilisateur à partir Azure Active Directory. Ces champs utilisateur seront rendus anonymes ou vides si le paramètre d’anonymisation global pour la gestion des risques internes est activé.
  - **Courrier électronique de** l’utilisateur : adresse de messagerie de l’utilisateur.
  - **Alias**: alias réseau de l’utilisateur.
  - **Organisation ou service :** l’organisation ou le service de l’utilisateur.

- **Onglet Activité de l’utilisateur**
  - **Historique des activités récentes des utilisateurs**: répertorie les indicateurs de déclenchement et les indicateurs de risque interne pour les activités des utilisateurs jusqu’aux 180 derniers jours. Toutes les activités pertinentes pour les indicateurs de risque internes sont également notés, même si les activités peuvent ou non avoir généré une alerte de risque interne. Le déclenchement d’exemples d’indicateurs peut être une date de départ ou la dernière date de travail prévue pour l’utilisateur. Les indicateurs de risque internes sont des activités déterminées comme étant à risque et définies dans les stratégies dans qui l’utilisateur est inclus. Les activités d’événement et de risque sont répertoriées avec l’élément le plus récent répertorié en premier.

## <a name="remove-users-from-in-scope-assignment-to-policies"></a>Supprimer des utilisateurs de l’attribution dans l’étendue aux stratégies

Il peut y avoir des scénarios où vous devez arrêter d’affecter des scores de risque à l’activité d’un utilisateur dans les stratégies de gestion des risques internes. Utilisez **Supprimer des utilisateurs** dans la **page** Tableau de bord Utilisateurs pour arrêter d’attribuer des scores de risque à un ou plusieurs utilisateurs de toutes les stratégies de gestion des risques internes pour qui ils sont actuellement dans l’étendue. Cette action ne supprime pas les utilisateurs de l’attribution de stratégie globale (lorsque vous ajoutez des utilisateurs ou des groupes à une configuration de stratégie), mais supprime simplement les utilisateurs du traitement actif par les stratégies après le déclenchement actuel des événements. Si les utilisateurs ont un autre événement déclencheur à l’avenir, les scores de risque des stratégies commenceront automatiquement à être attribués aux utilisateurs à nouveau. Les alertes ou les cas existants pour cet utilisateur ne seront pas supprimés.

> [!NOTE]
> La suppression d’un utilisateur d’une stratégie peut prendre plusieurs minutes. Une fois terminé, l’utilisateur n’est plus répertorié dans la page Utilisateurs. Si l’utilisateur supprimé a des alertes ou des cas actifs, il reste sur la page Utilisateurs et les détails de l’utilisateur indiquent qu’il n’est plus dans l’étendue d’une stratégie.

Pour supprimer manuellement les utilisateurs de l’état dans l’étendue dans toutes les stratégies de gestion des risques internes, effectuer les étapes suivantes :

1. Dans la <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centre de conformité Microsoft 365,</a>allez à **La** Gestion des risques internes et sélectionnez **l’onglet** Utilisateurs.
2. Dans le tableau **de bord Utilisateurs,** sélectionnez l’utilisateur ou les utilisateurs que vous souhaitez supprimer de l’étendue des stratégies de gestion des risques internes.
3. Sélectionnez **Supprimer des utilisateurs.**
4. Dans le **volet Supprimer l’utilisateur,** **sélectionnez Supprimer** ou **Annuler** pour ignorer les modifications et fermer la boîte de dialogue.
5. Sélectionnez **Supprimer** dans le volet de confirmation pour supprimer l’utilisateur.

## <a name="run-automated-tasks-with-power-automate-flows-for-a-user"></a>Exécuter des tâches automatisées avec Power Automate flux pour un utilisateur

À l’aide des flux Power Automate recommandés, les enquêteurs de risque et les analystes peuvent rapidement prendre des mesures pour :

- Avertir les utilisateurs lorsqu’ils sont ajoutés à une stratégie de risque interne

Pour exécuter, gérer ou créer des flux Power Automate pour un utilisateur de gestion des risques internes :

1. Sélectionnez **Automatiser dans la** barre d’outils Action de l’utilisateur.
2. Choisissez le flux Power Automate à exécuter, puis sélectionnez **Exécuter le flux.**
3. Une fois le flux terminé, sélectionnez **Terminé.**

Pour en savoir plus sur les Power Automate pour la gestion des risques internes, voir Prise en charge des paramètres de [gestion des risques internes.](insider-risk-management-settings.md#power-automate-flows-preview)
