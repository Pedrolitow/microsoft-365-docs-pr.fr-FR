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
ms.collection:
- tier1
- purview-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: b4a428d3d6151c2ae1e252ec792c8a1658bd67f0
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68718323"
---
# <a name="insider-risk-management-users-dashboard"></a>Tableau de bord Utilisateurs de la gestion des risques internes

> [!IMPORTANT]
> Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Le **tableau de bord Utilisateurs** est un outil important dans le flux de travail de gestion des risques internes et aide les enquêteurs et les analystes à mieux comprendre les activités à risque. Ce tableau de bord offre des vues et des fonctionnalités de gestion pour répondre aux besoins administratifs entre la création de stratégies de gestion des risques internes et la gestion des cas de gestion des risques internes.

Une fois les utilisateurs ajoutés aux stratégies de gestion des risques internes, les processus en arrière-plan évaluent automatiquement les activités des utilisateurs pour [déclencher des indicateurs](insider-risk-management-settings.md#indicators). Une fois les indicateurs de déclenchement présents, les activités des utilisateurs se voient attribuer des scores de risque. Certaines de ces activités peuvent entraîner une alerte de risque interne, mais certaines activités peuvent ne pas atteindre un niveau de score de risque minimal et une alerte de risque interne n’est pas créée. Le **tableau de bord Utilisateurs** vous permet d’afficher les utilisateurs avec ces types d’indicateurs et de scores de risque, ainsi que les utilisateurs qui ont des alertes de risque internes actives.

En savoir plus sur la façon dont le tableau de bord Utilisateurs affiche les utilisateurs dans les scénarios suivants :

- Utilisateurs avec des alertes de stratégie de risque interne active
- Utilisateurs avec des événements déclencheurs
- Utilisateurs ajoutés temporairement aux stratégies

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="users-with-active-insider-risk-policy-alerts"></a>Utilisateurs avec des alertes de stratégie de risque interne active

Le **tableau de bord Utilisateurs** affiche automatiquement tous les utilisateurs avec des alertes de stratégie de risque interne actives. Ces utilisateurs avec des alertes ont à la fois un indicateur déclencheur et un score de risque d’activité qui répond aux exigences de création d’une alerte de risque interne. Les activités de ces utilisateurs sont consultées en sélectionnant l’utilisateur dans le **tableau de bord Utilisateurs** et en accédant à **l’onglet Activité de l’utilisateur** .

## <a name="users-with-triggering-events"></a>Utilisateurs avec des événements déclencheurs

Le **tableau de bord Utilisateurs** affiche automatiquement tous les utilisateurs avec des événements déclencheurs, mais qui n’ont pas de score de risque d’activité qui créerait une alerte de risque interne. Par exemple, un utilisateur avec une date de démission signalée s’affiche, car cette activité est un événement déclencheur, mais n’est pas une activité qui a un score de risque. Les activités de ces utilisateurs sont consultées en sélectionnant l’utilisateur dans le **tableau de bord Utilisateurs** et en accédant à **l’onglet Activité de l’utilisateur** .

## <a name="users-added-temporarily-to-policies"></a>Utilisateurs ajoutés temporairement aux stratégies

Le **tableau de bord Utilisateurs** inclut les utilisateurs ajoutés aux stratégies de gestion des risques internes après un événement inhabituel en dehors du workflow de gestion des risques internes. L’ajout temporaire d’utilisateurs (à partir du tableau de bord Stratégies) est également un moyen de commencer à évaluer l’activité des utilisateurs pour une stratégie de gestion des risques internes pour tester la stratégie, même si un connecteur requis n’est pas configuré.

Lorsqu’un utilisateur est ajouté manuellement à une stratégie, les activités de l’utilisateur au cours des 90 derniers jours sont notées et ajoutées à la chronologie des **activités de l’utilisateur** . Par exemple, vous avez un utilisateur qui ne se voit pas attribuer de scores de risque pour une stratégie de risque interne et que l’utilisateur a des activités de fuite de données signalées au service juridique de votre organisation. Le service juridique vous recommande de configurer de nouvelles exigences de détection à court terme pour l’utilisateur. Vous pouvez affecter temporairement l’utilisateur à votre stratégie *de fuites de données* pendant une durée désignée (fenêtre d’activation). Tous les utilisateurs ajoutés temporairement sont affichés dans le **tableau de bord Utilisateurs** , car les exigences relatives aux événements de déclenchement sont annulées.

> [!NOTE]
> Plusieurs heures peuvent être nécessaires pour que les nouveaux utilisateurs ajoutés manuellement s’affichent dans le **tableau de bord Utilisateurs**. L’affichage des activités des 90 jours précédents de ces utilisateurs peut prendre jusqu’à 24 heures. Pour afficher les activités des utilisateurs ajoutés manuellement, sélectionnez l’utilisateur dans le **tableau de bord Utilisateurs** et ouvrez **l’onglet Activité de l’utilisateur** dans le volet d’informations.

L’utilisateur est automatiquement supprimé du **tableau de bord Utilisateurs** et le scoring s’arrête lorsque le temps défini dans la **fenêtre Activation** expire si :

- l’utilisateur n’a pas d’événements déclencheurs supplémentaires ou d’alertes de stratégie de risque interne, et
- si la durée de la **fenêtre d’activation** définie manuellement est supérieure à la durée de la **fenêtre d’activation** de stratégie globale.

Le paramètre **de fenêtre Activation** avec la durée la plus longue remplace toujours le paramètre **de fenêtre Activation** par une durée plus courte. Par exemple, vous avez configuré la **fenêtre Activation** sous l’onglet **Délais de** stratégie globale dans les paramètres globaux de gestion des risques internes pendant 15 jours, qui est automatiquement appliquée à toutes vos stratégies de risque interne.

Vous ajoutez temporairement un utilisateur à votre stratégie de risque interne *fuites de données* et définissez 30 jours comme **fenêtre d’activation** pour cet utilisateur. Le paramètre de **fenêtre d’activation** global de 15 jours est remplacé par la définition de la **fenêtre d’activation** de 30 jours pour l’utilisateur temporairement ajouté. L’utilisateur temporairement ajouté restera dans le **tableau de bord Utilisateurs** et sera dans l’étendue de la stratégie pendant 30 jours.

Dans le scénario opposé, où le paramètre de **fenêtre d’activation** globale est plus long que le paramètre de **fenêtre Activation** défini pour un utilisateur temporairement ajouté, le paramètre de **fenêtre d’activation** globale remplace le paramètre **de fenêtre Activation** pour l’utilisateur temporairement ajouté. L’utilisateur temporairement ajouté restera dans le **tableau de bord Utilisateurs** et sera dans l’étendue de la stratégie pour le nombre de jours défini dans les paramètres globaux **de la fenêtre Activation** .

## <a name="view-user-information-on-the-users-dashboard"></a>Afficher les informations utilisateur dans le tableau de bord Utilisateurs

Chaque utilisateur affiché dans le **tableau de bord Utilisateurs** contient les informations suivantes :

- **Utilisateurs** : nom d’utilisateur d’un utilisateur. Ce champ est anonyme si le paramètre d’anonymisation globale pour la gestion des risques internes est activé.
- **Niveau de risque** : niveau de risque calculé actuel de l’utilisateur. Ce score est calculé toutes les 24 heures et utilise les scores de risque d’alerte de toutes les alertes actives associées à l’utilisateur. Pour les utilisateurs disposant uniquement d’indicateurs de déclenchement, le niveau de risque est égal à zéro.
- **Alertes actives** : nombre d’alertes actives pour toutes les stratégies.
- **Violations confirmées** : nombre de cas résolus en tant que *violation de stratégie confirmée* pour l’utilisateur.
- **Cas** : cas actif actuel pour l’utilisateur.

Pour localiser rapidement un utilisateur spécifique, utilisez **La recherche** en haut à droite du tableau de bord Utilisateurs. Lorsque vous recherchez des utilisateurs, vous devez utiliser le nom d’utilisateur principal (UPN). Par exemple, lors de la recherche d’un utilisateur nommé « Tiara Hidayah » dont l’UPN est « thidayah » dans votre organisation, vous devez entrer « thidayah » ou une partie de l’UPN dans **La recherche**.

![Tableau de bord des utilisateurs de la gestion des risques internes](../media/insider-risk-users-dashboard.png)

> [!NOTE]
> Le nombre d’utilisateurs affichés dans le **tableau de bord Utilisateurs** peut être limité dans certains cas, en fonction du volume d’alertes actives et des stratégies correspondantes. Les utilisateurs avec des alertes actives sont affichés dans le **tableau de bord Utilisateurs** au fur et à mesure que les alertes sont générées, et il peut y avoir de rares cas où le nombre maximal d’utilisateurs affichés est atteint. Si cette limite se produit, les utilisateurs avec des alertes actives qui ne sont pas affichées sont ajoutés au **tableau de bord Utilisateurs** à mesure que les alertes utilisateur existantes sont triées.

## <a name="view-user-details"></a>Afficher les détails de l’utilisateur

Pour afficher plus de détails sur l’activité à risque d’un utilisateur, ouvrez le volet d’informations utilisateur en double-cliquant sur un utilisateur dans le **tableau de bord Utilisateurs**. Dans le volet d’informations, vous pouvez afficher les informations suivantes :

- **Onglet Profil utilisateur**
  - **Nom et titre** : nom et poste de l’utilisateur à partir d’Azure Active Directory. Ces champs utilisateur seront rendus anonymes ou vides si le paramètre d’anonymisation globale pour la gestion des risques internes est activé.
  - **Adresse e-mail de** l’utilisateur : Email adresse de l’utilisateur.
  - **Alias** : alias réseau pour l’utilisateur.
  - **Organisation ou service** : organisation ou service pour l’utilisateur.

- **Onglet Activité de l’utilisateur**
  - **Historique des activités récentes des utilisateurs** : répertorie les indicateurs déclencheurs et les indicateurs de risque interne pour les activités à risque jusqu’aux 90 derniers jours. Toutes les activités à risque pertinentes pour les indicateurs de risque interne sont également notées, bien que les activités aient ou non généré une alerte de risque interne. Les exemples d’indicateurs déclencheurs peuvent être une date de démission ou la dernière date de travail planifiée pour l’utilisateur. Les indicateurs de risque interne sont des activités déterminées comme ayant un élément de risque, qui peut potentiellement entraîner un incident de sécurité, et sont définies dans les stratégies dans lesquelles l’utilisateur est inclus. Les activités d’événement et de risque sont répertoriées avec l’élément le plus récent répertorié en premier.

## <a name="remove-users-from-in-scope-assignment-to-policies"></a>Supprimer des utilisateurs de l’affectation dans l’étendue aux stratégies

Il peut y avoir des scénarios où vous devez arrêter d’attribuer des scores de risque aux utilisateurs dans les stratégies de gestion des risques internes. Utilisez **Supprimer des utilisateurs** dans la page **du tableau de bord Utilisateurs** pour arrêter d’attribuer des scores de risque à un ou plusieurs utilisateurs de toutes les stratégies de gestion des risques internes pour lesquelles ils sont actuellement dans l’étendue. Cette action ne supprime pas les utilisateurs de l’attribution de stratégie globale (lorsque vous ajoutez des utilisateurs ou des groupes à une configuration de stratégie), mais supprime simplement les utilisateurs du traitement actif par les stratégies après les événements de déclenchement actuels. Si les utilisateurs ont un autre événement déclencheur à l’avenir, les scores de risque des stratégies commencent automatiquement à être attribués aux utilisateurs. Les alertes ou les cas existants pour cet utilisateur ne seront pas supprimés.

> [!NOTE]
> La suppression d’un utilisateur d’une stratégie peut prendre plusieurs minutes. Une fois l’opération terminée, l’utilisateur n’est plus répertorié dans la page Utilisateurs. Si l’utilisateur supprimé a des alertes ou des cas actifs, l’utilisateur reste sur la page Utilisateurs et les détails de l’utilisateur indiquent qu’il n’est plus dans l’étendue d’une stratégie.

Pour supprimer manuellement des utilisateurs de l’état dans l’étendue dans toutes les stratégies de gestion des risques internes, procédez comme suit :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Utilisateurs**.
2. Dans le **tableau de bord Utilisateurs**, sélectionnez le ou les utilisateurs que vous souhaitez supprimer dans l’étendue des stratégies de gestion des risques internes.
3. Sélectionnez **Supprimer les utilisateurs**.
4. Dans le volet **Supprimer l’utilisateur** , sélectionnez **Supprimer** ou **Annuler** pour ignorer les modifications et fermer la boîte de dialogue.
5. Sélectionnez **Supprimer** dans le volet de confirmation pour supprimer l’utilisateur.

## <a name="run-automated-tasks-with-power-automate-flows-for-a-user"></a>Exécuter des tâches automatisées avec des flux Power Automate pour un utilisateur

À l’aide des flux Power Automate recommandés, les enquêteurs et les analystes des risques peuvent rapidement prendre des mesures pour avertir les utilisateurs lorsqu’ils sont ajoutés à une stratégie de risque interne.

Pour exécuter, gérer et créer des flux Power Automate pour les utilisateurs de gestion des risques internes :

1. Sélectionnez **Automatiser** dans la barre d’outils d’action de l’utilisateur.
2. Choisissez le flux Power Automate à exécuter, puis sélectionnez **Exécuter le flux**.
3. Une fois le flux terminé, sélectionnez **Terminé**.

Pour en savoir plus sur les flux Power Automate pour la gestion des risques internes, consultez [Prise en main des paramètres de gestion des risques internes](insider-risk-management-settings.md#power-automate-flows-preview).
