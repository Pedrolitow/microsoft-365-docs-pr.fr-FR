---
title: Tableau de bord des utilisateurs de gestion des risques Insiders
description: En savoir plus sur le tableau de bord des utilisateurs de gestion des risques Insiders dans Microsoft 365
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
# <a name="insider-risk-management-users-dashboard"></a>Tableau de bord des utilisateurs de gestion des risques Insiders

Le **tableau de bord utilisateurs** est un outil important dans le flux de travail de gestion des risques inSided et permet aux enquêteurs et analystes de mieux comprendre les activités liées aux risques. Ce tableau de bord offre des vues et des fonctionnalités de gestion pour répondre aux besoins administratifs entre la création de stratégies de gestion des risques internes et la gestion des cas d’Insider.

Une fois que les utilisateurs sont ajoutés aux stratégies de gestion des risques internes, les processus d’arrière-plan évaluent automatiquement les activités des utilisateurs pour [déclencher des indicateurs](insider-risk-management-settings.md#indicators). Une fois les indicateurs déclenchés, les résultats sont affectés aux activités de l’utilisateur. Certaines de ces activités peuvent entraîner une alerte d’Insider, mais certaines activités ne peuvent pas atteindre un niveau de risque minimal et une alerte de risque Insider n’est pas créée. Le **tableau de bord utilisateurs** vous permet d’afficher les utilisateurs avec ces types d’indicateurs et de scores de risques, ainsi que les utilisateurs qui ont des alertes de risque active Insider.

En outre, il peut y avoir des scénarios où vous devez ajouter temporairement des utilisateurs à des stratégies de risque internes après qu’un événement inhabituel est signalé en dehors du flux de travail de gestion des risques inSided. Le **tableau de bord utilisateurs** vous permet d’ajouter manuellement un utilisateur à une stratégie de risque d’initié pendant une période de temps spécifique et de contourner la nécessité pour qu’un utilisateur ait un indicateur déclencheur. Ces utilisateurs sont toujours affichés dans le tableau de bord utilisateurs lorsqu’ils sont affectés activement à une stratégie.

En savoir plus sur la façon dont le tableau de bord des utilisateurs affiche les utilisateurs dans les scénarios suivants :

- Les utilisateurs de tableau de bord avec des alertes de stratégie de risque active Insider
- Utilisateurs de tableau de bord avec indicateurs de déclenchement
- Utilisateurs de tableau de bord ajoutés temporairement à des stratégies

## <a name="dashboard-users-with-active-insider-risk-policy-alerts"></a>Les utilisateurs de tableau de bord avec des alertes de stratégie de risque active Insider

Le **tableau de bord utilisateurs** affiche automatiquement tous les utilisateurs ayant des alertes de stratégie de risque active Insider. Ces utilisateurs ayant des alertes ont à la fois un indicateur de déclenchement et une note de risque d’activité qui satisfont aux exigences de création d’une alerte de risque d’initié. Les activités de ces utilisateurs sont affichées en sélectionnant l’utilisateur dans le **tableau de bord utilisateurs** et en accédant à l’onglet **activité utilisateur** .

## <a name="dashboard-users-with-triggering-indicators"></a>Utilisateurs de tableau de bord avec indicateurs de déclenchement

Le **tableau de bord utilisateurs** affiche automatiquement tous les utilisateurs qui déclenchent des indicateurs, mais qui n’ont pas de score de risque d’activité qui crée une alerte de risque d’initié. Par exemple, un utilisateur avec une date de départ signalée est affiché car cet événement est un indicateur déclencheur, mais n’est pas une activité présentant un score de risque. Les activités de ces utilisateurs sont affichées en sélectionnant l’utilisateur dans le **tableau de bord utilisateurs** et en accédant à l’onglet **activité utilisateur** .

## <a name="dashboard-users-added-temporarily-to-policies"></a>Utilisateurs de tableau de bord ajoutés temporairement à des stratégies

Le **tableau de bord utilisateurs** vous permet d’ajouter temporairement des utilisateurs à une stratégie de gestion des risques initiés existante après un événement inhabituel en dehors du flux de travail de gestion des risques Insiders. L’ajout temporaire d’utilisateurs est également un moyen d’ajouter des utilisateurs à une stratégie de gestion des risques inSided pour tester la stratégie, même si un connecteur requis n’est pas configuré.

Lorsqu’un utilisateur est ajouté manuellement à une stratégie, les activités de l’utilisateur pour les 90 jours précédents sont évaluées et ajoutées à la chronologie des activités de l' **utilisateur** . Par exemple, vous avez un utilisateur qui n’est pas actuellement inclus dans une stratégie de risque d’initié et que l’utilisateur a communiqué des activités de fuites de données au service juridique de votre organisation. Le service juridique recommande de configurer de nouvelles exigences de surveillance à court terme pour l’utilisateur. Vous pouvez affecter temporairement l’utilisateur à votre stratégie de *fuite de données* pour une durée définie (fenêtre d’activation). Tous les utilisateurs ajoutés temporairement sont affichés dans le **tableau de bord utilisateurs** car les exigences d’indicateur de déclenchement sont annulées.

>[!NOTE]
>L’affichage des nouveaux utilisateurs ajoutés manuellement dans le **tableau de bord utilisateurs**peut prendre plusieurs heures. L’affichage des activités pour les 90 jours précédents pour ces utilisateurs peut prendre jusqu’à 24 heures. Pour afficher les activités des utilisateurs ajoutés manuellement, sélectionnez l’utilisateur dans le **tableau de bord utilisateurs** et ouvrez l’onglet **activité utilisateur** dans le volet d’informations.

L’utilisateur est automatiquement supprimé de la stratégie d’initié et du **tableau de bord utilisateurs** lorsque le temps défini dans la **fenêtre d’activation** expire si :

- l’utilisateur n’a pas d’indicateurs de déclenchement ni d’alertes de stratégie de risque d’initié et
- Si la durée de la **fenêtre d’activation** manuellement définie est supérieure à la durée de la fenêtre d' **activation** de stratégie globale. 

Le paramètre de **fenêtre d’activation** avec la durée la plus longue remplace toujours le paramètre de **fenêtre d’activation** avec une durée plus courte. Par exemple, vous avez configuré la **fenêtre activation** sous l’onglet durées globales des **stratégies** dans les paramètres globaux de gestion des risques initiaux pendant 15 jours, qui est automatiquement appliqué à toutes vos stratégies de risque d’initié. 

Vous ajoutez provisoirement un utilisateur à votre stratégie de risque de *fuite de données* et définissez 30 jours comme **fenêtre d’activation** pour cet utilisateur. Le paramètre de la **fenêtre d’activation** globale de 15 jours est remplacé en définissant le paramètre de la **fenêtre d’activation** de 30 jours pour l’utilisateur ajouté temporairement. L’utilisateur ajouté temporairement restera dans le **tableau de bord utilisateurs** et sera dans l’étendue de la stratégie pendant 30 jours.

Dans le scénario opposé où le paramètre de la **fenêtre d’activation** globale est plus long que le paramètre de **fenêtre d’activation** défini pour un utilisateur ajouté temporairement, le paramètre de la fenêtre d' **activation** globale remplace le paramètre de **fenêtre d’activation** de l’utilisateur ajouté temporairement. L’utilisateur ajouté temporairement reste dans le **tableau de bord utilisateurs** et se trouve dans l’étendue de la stratégie pour le nombre de jours défini dans les paramètres de la **fenêtre d’activation** globale.

## <a name="view-user-information-on-the-users-dashboard"></a>Afficher les informations utilisateur dans le tableau de bord utilisateurs

Chaque utilisateur affiché dans le **tableau de bord utilisateurs** comporte les informations suivantes :

- **Users**: nom d’utilisateur d’un utilisateur. Ce champ est rendu anonyme si le paramètre d’anonymisation global est activé pour la gestion des risques initiés.
- **Niveau de risque**: niveau de risque calculé actuel de l’utilisateur. Ce score est calculé toutes les 24 heures et utilise les scores de risque d’alerte de toutes les alertes actives associées à l’utilisateur. Pour les utilisateurs avec des indicateurs de déclenchement uniquement, le niveau de risque est égal à zéro.
- **Alertes actives**: nombre d’alertes actives pour toutes les stratégies.
- **Violations confirmées**: nombre de cas résolus comme *violation de stratégie confirmée* pour l’utilisateur.
- **Cas**: dossier actif actuel de l’utilisateur.

![Tableau de bord des utilisateurs de gestion des risques Insiders](../media/insider-risk-users-dashboard.png)

>[!NOTE]
>Le nombre d’utilisateurs affichés dans le **tableau de bord utilisateurs** peut être limité dans certains cas, en fonction du volume des alertes actives et des stratégies de correspondance. Les utilisateurs ayant des alertes actives sont affichés dans le **tableau de bord utilisateurs** lorsque les alertes sont générées, et il peut arriver que le nombre maximal d’utilisateurs affichés soit atteint. Dans ce cas, les utilisateurs ayant des alertes actives qui ne sont pas affichées seront ajoutés au **tableau de bord utilisateurs** lorsque les alertes utilisateur existantes seront triées.

## <a name="view-user-details"></a>Afficher les détails de l’utilisateur

Pour afficher plus de détails sur l’activité des risques pour un utilisateur, ouvrez le volet Détails de l’utilisateur en double-cliquant sur un utilisateur dans le **tableau de bord utilisateurs**. Dans le volet d’informations, vous pouvez afficher les informations suivantes :

- Onglet **profil utilisateur**
    - **Nom et titre**: nom et poste pour l’utilisateur à partir d’Azure Active Directory. Ces champs utilisateur seront rendus anonymes ou vides si le paramètre de paramétrage d’anonymisation global est activé pour la gestion des risques initiés.
    - Adresse de messagerie de l' **utilisateur**: adresse de messagerie de l’utilisateur.
    - **Alias**: alias réseau de l’utilisateur.
    - **Organisation ou service**: organisation ou service de l’utilisateur.

- Onglet **activité utilisateur**
    - **Historique des activités des utilisateurs récents**: répertorie les indicateurs de déclenchement et les indicateurs de risque internes pour les activités de l’utilisateur jusqu’aux 180 derniers jours. Toutes les activités relatives aux indicateurs de risque d’initiés sont également évaluées, bien que les activités puissent avoir généré ou non une alerte de risque d’initié. Le déclenchement d’exemples d’indicateurs peut être une date de départ ou la dernière date de travail prévue pour l’utilisateur. Les indicateurs de risque internes sont des activités déterminées comme ayant un élément de risque et sont définies dans des stratégies auxquelles l’utilisateur est inclus. Les activités liées aux événements et aux risques sont répertoriées avec l’élément le plus récent répertorié en premier.

## <a name="temporarily-add-a-user-to-a-policy"></a>Ajouter temporairement un utilisateur à une stratégie

Pour ajouter temporairement un utilisateur à une stratégie de gestion des risques Insiders, utilisez l’onglet **utilisateurs** de la solution de **gestion des risques inSided** dans le centre de conformité Microsoft 365. Les utilisateurs ajoutent manuellement le déclenchement des exigences d’indicateur pour la stratégie à laquelle ils sont ajoutés et s’affichent dans le **tableau de bord utilisateurs**. Pour ajouter définitivement un utilisateur à une stratégie de gestion des risques Insiders, vous allez utiliser l’Assistant stratégie.

Procédez comme suit pour ajouter un utilisateur à une stratégie d’Insider existante :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **utilisateurs** .
2. Sélectionnez **Ajouter un utilisateur à une stratégie** dans la barre d’outils.
3. Dans la boîte de dialogue **Ajouter un nouvel utilisateur** , commencez à taper un nom d’utilisateur dans le champ **utilisateur** . Sélectionnez l’utilisateur que vous souhaitez ajouter à une stratégie.
4. Sélectionnez la flèche déroulante pour le champ de **stratégie** afin d’afficher les stratégies de gestion des risques d’Insider configurées. Sélectionnez la stratégie à laquelle ajouter l’utilisateur.
5. Utilisez le contrôle Slider de la **fenêtre d’activation** pour définir la durée pendant laquelle l’utilisateur est inclus dans une stratégie et affiché dans le tableau de bord utilisateurs. L’heure que vous spécifiez détermine la durée pendant laquelle la stratégie est active pour cet utilisateur et démarre lorsque la première alerte est générée ou qu’un indicateur déclencheur (comme une correspondance de stratégie DLP) est détecté. La plage de la **fenêtre d’activation** est comprise entre 5 et 30 jours.
6. Sélectionnez **Ajouter** , puis **confirmez** l’ajout de l’utilisateur à la stratégie.

>[!NOTE]
>L’affichage des nouveaux utilisateurs ajoutés manuellement dans le **tableau de bord utilisateurs**peut prendre plusieurs heures. L’affichage des activités pour les 90 jours précédents pour ces utilisateurs peut prendre jusqu’à 24 heures. Pour afficher les activités des utilisateurs ajoutés manuellement, sélectionnez l’utilisateur dans le **tableau de bord utilisateurs** et ouvrez l’onglet **activité utilisateur** dans le volet d’informations.

## <a name="run-automated-tasks-with-power-automate-flows-for-a-user"></a>Exécuter des tâches automatisées avec Power automate des flux pour un utilisateur

À l’aide des flux recommandés d’automate d’énergie, les investigateurs de risque et les analystes peuvent rapidement prendre les mesures suivantes :

- Avertir les utilisateurs lorsqu’ils sont ajoutés à une stratégie de risque Insider

Pour exécuter, gérer ou créer des flux automatiques d’alimentation pour un utilisateur de gestion des risques inSided :

1. Sélectionnez **automatiser** dans la barre d’outils action de l’utilisateur.
2. Choisissez le flux d’alimentation automatique à exécuter, puis sélectionnez **exécuter le flux**.
3. Une fois le flux terminé, sélectionnez **terminé**.

Pour en savoir plus sur la gestion de l’alimentation automatisée des flux pour la gestion des risques initiés, voir [Getting Started with Insider Risk Management Settings](insider-risk-management-settings.md#power-automate-flows-preview).
