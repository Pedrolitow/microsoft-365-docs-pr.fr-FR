---
title: Tableau de bord Utilisateurs de la gestion des risques internes
description: En savoir plus sur le tableau de bord Utilisateurs de la gestion des risques internes dans Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, risque interne, gestion des risques, conformité
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
ms.openlocfilehash: 14c0d5127f4b370d78b54512d8780d1cc7dfbf67
ms.sourcegitcommit: 221212fff9737e0ea386755deb8fed62ae9c254b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2022
ms.locfileid: "66787647"
---
# <a name="insider-risk-management-users-dashboard"></a>Tableau de bord Utilisateurs de la gestion des risques internes

Le **tableau de bord Utilisateurs** est un outil important dans le flux de travail de gestion des risques internes et aide les enquêteurs et les analystes à mieux comprendre les activités à risque. Ce tableau de bord offre des vues et des fonctionnalités de gestion pour répondre aux besoins administratifs entre la création de stratégies de gestion des risques internes et la gestion des cas de gestion des risques internes.

Une fois les utilisateurs ajoutés aux stratégies de gestion des risques internes, les processus en arrière-plan évaluent automatiquement les activités des [utilisateurs pour déclencher des indicateurs](insider-risk-management-settings.md#indicators). Une fois les indicateurs de déclenchement présents, les activités utilisateur se voient attribuer des scores de risque. Certaines de ces activités peuvent entraîner une alerte de risque interne, mais certaines activités peuvent ne pas atteindre un niveau de score de risque minimal et une alerte de risque interne n’est pas créée. Le **tableau de bord Utilisateurs** vous permet d’afficher les utilisateurs avec ces types d’indicateurs et les scores de risque, ainsi que les utilisateurs qui ont des alertes de risque internes actives.

En savoir plus sur la façon dont le tableau de bord Utilisateurs affiche les utilisateurs dans les scénarios suivants :

- Utilisateurs avec des alertes de stratégie de risque interne actives
- Utilisateurs avec événements déclencheurs
- Utilisateurs ajoutés temporairement aux stratégies

## <a name="users-with-active-insider-risk-policy-alerts"></a>Utilisateurs avec des alertes de stratégie de risque interne actives

Le **tableau de bord Utilisateurs** affiche automatiquement tous les utilisateurs avec des alertes de stratégie de risque interne actives. Ces utilisateurs avec des alertes ont à la fois un indicateur de déclenchement et un score de risque d’activité qui répond aux exigences de création d’une alerte de risque interne. Les activités de ces utilisateurs sont affichées en sélectionnant l’utilisateur dans le **tableau de bord Utilisateurs** et en accédant à **l’onglet Activité de l’utilisateur** .

## <a name="users-with-triggering-events"></a>Utilisateurs avec événements déclencheurs

Le **tableau de bord Utilisateurs** affiche automatiquement tous les utilisateurs ayant déclenché des événements, mais qui n’ont pas de score de risque d’activité qui créerait une alerte de risque interne. Par exemple, un utilisateur avec une date de démission signalée s’affiche, car cette activité est un événement déclencheur, mais n’est pas une activité qui a un score de risque. Les activités de ces utilisateurs sont affichées en sélectionnant l’utilisateur dans le **tableau de bord Utilisateurs** et en accédant à **l’onglet Activité de l’utilisateur** .

## <a name="users-added-temporarily-to-policies"></a>Utilisateurs ajoutés temporairement aux stratégies

Le **tableau de bord Utilisateurs** inclut les utilisateurs ajoutés aux stratégies de gestion des risques internes après un événement inhabituel en dehors du flux de travail de gestion des risques internes. L’ajout temporaire d’utilisateurs (à partir du tableau de bord Stratégies) est également un moyen de commencer à noter l’activité des utilisateurs pour une stratégie de gestion des risques internes pour tester la stratégie, même si un connecteur requis n’est pas configuré.

Lorsqu’un utilisateur est ajouté manuellement à une stratégie, les activités utilisateur des 90 derniers jours sont notées et ajoutées à la chronologie de **l’activité utilisateur** . Par exemple, un utilisateur n’est pas actuellement affecté à des scores de risque pour une stratégie de risque interne et l’utilisateur a des activités de fuite de données signalées au service juridique de votre organisation. Le service juridique vous recommande de configurer de nouvelles exigences de détection à court terme pour l’utilisateur. Vous pouvez affecter temporairement l’utilisateur à votre stratégie de *fuites de données* pour une durée désignée (fenêtre d’activation). Tous les utilisateurs ajoutés temporairement sont **affichés dans le tableau de bord Utilisateurs** , car les exigences en matière d’événements de déclenchement sont levées.

> [!NOTE]
> L’apparition de nouveaux utilisateurs ajoutés manuellement dans le tableau de **bord Utilisateurs** peut prendre plusieurs heures. L’affichage des activités des 90 jours précédents de ces utilisateurs peut prendre jusqu’à 24 heures. Pour afficher les activités des utilisateurs ajoutés manuellement, sélectionnez l’utilisateur dans le **tableau de bord Utilisateurs** et ouvrez **l’onglet Activité utilisateur** dans le volet d’informations.

L’utilisateur est automatiquement supprimé du **tableau de bord Utilisateurs** et le scoring s’arrête lorsque l’heure définie dans la **fenêtre Activation** expire si :

- l’utilisateur n’a pas d’événements déclencheurs supplémentaires ou d’alertes de stratégie de risque interne, et
- si la durée de la **fenêtre d’activation** définie manuellement est supérieure à la durée de la **fenêtre d’activation** de stratégie globale.

Le paramètre **de fenêtre d’activation** avec la durée la plus longue remplace toujours le paramètre de **fenêtre d’activation** par une durée plus courte. Par exemple, vous avez configuré la **fenêtre Activation** sous l’onglet Périodes de stratégie globale dans les **paramètres** globaux de gestion des risques internes pendant 15 jours, qui est automatiquement appliqué à toutes vos stratégies de risque interne.

Vous ajoutez temporairement un utilisateur à votre stratégie de risque interne *des fuites de données* et définissez 30 jours comme **fenêtre d’activation** pour cet utilisateur. Le paramètre de **fenêtre d’activation** globale de 15 jours est remplacé en définissant le paramètre de **fenêtre d’activation** de 30 jours pour l’utilisateur ajouté temporairement. L’utilisateur ajouté temporairement reste dans le **tableau de bord Utilisateurs** et est dans l’étendue de la stratégie pendant 30 jours.

Dans le scénario inverse où le paramètre de **fenêtre d’activation** globale est plus long que le paramètre de **fenêtre d’activation** défini pour un utilisateur ajouté temporairement, le paramètre de **fenêtre d’activation** globale remplace le paramètre de **fenêtre d’activation** pour l’utilisateur ajouté temporairement. L’utilisateur ajouté temporairement reste dans le **tableau de bord Utilisateurs** et est inclus dans l’étendue de la stratégie pour le nombre de jours définis dans les paramètres de la **fenêtre d’activation** globale.

## <a name="view-user-information-on-the-users-dashboard"></a>Afficher les informations utilisateur sur le tableau de bord Utilisateurs

Chaque utilisateur affiché dans le **tableau de bord Utilisateurs** contient les informations suivantes :

- **Utilisateurs** : nom d’utilisateur d’un utilisateur. Ce champ est anonyme si le paramètre d’anonymisation global pour la gestion des risques internes est activé.
- **Niveau de risque** : niveau de risque calculé actuel de l’utilisateur. Ce score est calculé toutes les 24 heures et utilise les scores de risque d’alerte de toutes les alertes actives associées à l’utilisateur. Pour les utilisateurs avec uniquement des indicateurs de déclenchement, le niveau de risque est égal à zéro.
- **Alertes actives** : nombre d’alertes actives pour toutes les stratégies.
- **Violations confirmées** : nombre de cas résolus comme *violation de stratégie confirmée* pour l’utilisateur.
- **Cas** : cas actif actuel pour l’utilisateur.

Pour localiser rapidement un utilisateur spécifique, utilisez **La recherche** en haut à droite du tableau de bord utilisateur. Lorsque vous recherchez des utilisateurs, vous devez utiliser le nom d’utilisateur principal (UPN). Par exemple, lorsque vous recherchez un utilisateur nommé « Tiara Hidayah » qui a un UPN « thidayah » dans votre organisation, vous entrez « thidayah » ou une partie de l’UPN dans **Search**.

![Tableau de bord des utilisateurs de gestion des risques internes.](../media/insider-risk-users-dashboard.png)

> [!NOTE]
> Le nombre d’utilisateurs affichés dans le **tableau de bord Utilisateurs** peut être limité dans certains cas, en fonction du volume d’alertes actives et des stratégies correspondantes. Les utilisateurs avec des alertes actives sont affichés dans le **tableau de bord Utilisateurs** à mesure que les alertes sont générées, et il peut y avoir de rares cas où le nombre maximal d’utilisateurs affichés est atteint. Si cette limite se produit, les utilisateurs avec des alertes actives qui ne sont pas affichées sont **ajoutés au tableau de bord Utilisateurs** à mesure que les alertes utilisateur existantes sont triées.

## <a name="view-user-details"></a>Afficher les détails de l’utilisateur

Pour afficher plus de détails sur l’activité à risque d’un utilisateur, ouvrez le volet Détails de l’utilisateur en double-cliquant sur un utilisateur dans le **tableau de bord Utilisateurs**. Dans le volet d’informations, vous pouvez afficher les informations suivantes :

- **Onglet Profil utilisateur**
  - **Nom et titre** : nom et titre de position de l’utilisateur à partir d’Azure Active Directory. Ces champs utilisateur sont anonymes ou vides si le paramètre d’anonymisation global pour la gestion des risques internes est activé.
  - **E-mail de** l’utilisateur : adresse e-mail de l’utilisateur.
  - **Alias** : alias réseau de l’utilisateur.
  - **Organisation ou service** : organisation ou service de l’utilisateur.

- **Onglet Activité de l’utilisateur**
  - **Historique de l’activité utilisateur récente** : répertorie à la fois les indicateurs de déclenchement et les indicateurs de risque interne pour les activités utilisateur jusqu’aux 180 derniers jours. Toutes les activités pertinentes pour les indicateurs de risque interne sont également notées, bien que les activités puissent ou non avoir généré une alerte de risque interne. Le déclenchement d’exemples d’indicateurs peut être une date de démission ou la dernière date de travail planifiée pour l’utilisateur. Les indicateurs de risque interne sont des activités déterminées pour avoir un élément de risque et sont définies dans les stratégies dans lesquelles l’utilisateur est inclus. Les activités d’événement et de risque sont répertoriées avec l’élément le plus récent répertorié en premier.

## <a name="remove-users-from-in-scope-assignment-to-policies"></a>Supprimer des utilisateurs de l’affectation dans l’étendue aux stratégies

Dans certains scénarios, vous devez cesser d’attribuer des scores de risque à l’activité d’un utilisateur dans les stratégies de gestion des risques internes. Utilisez **Supprimer les utilisateurs** sur la page **du tableau de bord Utilisateurs** pour arrêter d’attribuer des scores de risque pour un ou plusieurs utilisateurs de toutes les stratégies de gestion des risques internes pour lesquelles ils sont actuellement dans l’étendue. Cette action ne supprime pas les utilisateurs de l’attribution de stratégie globale (lorsque vous ajoutez des utilisateurs ou des groupes à une configuration de stratégie), mais supprime simplement les utilisateurs du traitement actif par les stratégies après les événements de déclenchement actuels. Si les utilisateurs ont un autre événement déclencheur à l’avenir, les scores de risque des stratégies commenceront automatiquement à être attribués à nouveau aux utilisateurs. Les alertes ou cas existants pour cet utilisateur ne seront pas supprimés.

> [!NOTE]
> La suppression d’un utilisateur d’une stratégie peut prendre plusieurs minutes. Une fois l’opération terminée, l’utilisateur n’est plus répertorié sur la page Utilisateurs. Si l’utilisateur supprimé a des alertes ou des cas actifs, l’utilisateur reste sur la page Utilisateurs et les détails de l’utilisateur indiquent qu’il n’est plus dans l’étendue d’une stratégie.

Pour supprimer manuellement les utilisateurs de l’état dans l’étendue dans toutes les stratégies de gestion des risques internes, effectuez les étapes suivantes :

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **La gestion des risques internes** et sélectionnez l’onglet **Utilisateurs**.
2. Dans le **tableau de bord Utilisateurs**, sélectionnez l’utilisateur ou les utilisateurs que vous souhaitez supprimer de l’étendue dans les stratégies de gestion des risques internes.
3. Sélectionnez **Supprimer les utilisateurs**.
4. Dans le volet **Supprimer l’utilisateur** , **sélectionnez Supprimer** ou **Annuler** pour ignorer les modifications et fermer la boîte de dialogue.
5. Sélectionnez **Supprimer** dans le volet de confirmation pour supprimer l’utilisateur.

## <a name="run-automated-tasks-with-power-automate-flows-for-a-user"></a>Exécuter des tâches automatisées avec des flux Power Automate pour un utilisateur

À l’aide des flux Power Automate recommandés, les enquêteurs et les analystes des risques peuvent rapidement prendre des mesures pour :

- Avertir les utilisateurs lorsqu’ils sont ajoutés à une stratégie de risque interne

Pour exécuter, gérer ou créer des flux Power Automate pour un utilisateur de gestion des risques internes :

1. Sélectionnez **Automatiser** dans la barre d’outils action utilisateur.
2. Choisissez le flux Power Automate à exécuter, puis sélectionnez **Exécuter le flux**.
3. Une fois le flux terminé, sélectionnez **Terminé**.

Pour en savoir plus sur les flux Power Automate pour la gestion des risques internes, consultez [Prise en main des paramètres de gestion des risques internes](insider-risk-management-settings.md#power-automate-flows-preview).
