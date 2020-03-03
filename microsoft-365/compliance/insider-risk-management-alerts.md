---
title: Alertes de gestion des risques internes
description: En savoir plus sur les alertes de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, Insider Risk, gestion des risques, conformité
localization_priority: Normal
ms.prod: Microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 74e84fc00e5fe633f0d70315cea9ad1329e2f639
ms.sourcegitcommit: 9224a7a5886c0c5fa0bc12bd9f7234a0eba90023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42372012"
---
# <a name="insider-risk-management-alerts"></a>Alertes de gestion des risques internes

Les alertes de gestion des risques initiés sont automatiquement générées par les indicateurs de risque définis dans les stratégies de gestion des risques internes. Ces alertes donnent aux analystes de conformité un aperçu de l’état actuel des risques et permettent à votre organisation de trier et de prendre des mesures pour les risques découverts.

## <a name="alert-dashboard"></a>Tableau de bord d’alerte

Le tableau de **bord des alertes** sur les risques Insiders vous permet d’afficher et d’effectuer des actions sur les alertes générées par des stratégies de risque initiées. Chaque widget de rapport affiche les informations des 30 derniers jours.

- **Alertes à réviser**: le nombre total d’alertes nécessitant une révision et un triage sont répertoriés, y compris une ventilation par gravité d’alerte.
- **Alertes ouvertes au cours des 30 derniers jours**: nombre total d’alertes créées par des correspondances de stratégie au cours des 30 derniers jours, triées par niveau de gravité d’alerte élevé, moyen et faible.
- **Temps moyen de résolution des alertes**: Résumé des statistiques d’alerte utiles :
    - Durée moyenne de résolution des alertes à gravité élevée, indiquées en heures, jours ou mois.
    - Durée moyenne de résolution des alertes de gravité moyenne, en heures, jours ou mois.
    - Durée moyenne de résolution des alertes à faible gravité, indiquées en heures, jours ou mois.

![Tableau de bord d’alerte de gestion des risques Insiders](../media/insider-risk-alerts-dashboard.png)

>[!NOTE]
>La gestion des risques internes utilise la limitation des alertes intégrée pour protéger et optimiser votre expérience d’examen et de révision des risques. Cette limitation protège contre les problèmes susceptibles d’entraîner une surcharge des alertes de stratégie, telles que des connecteurs de données mal configurés ou des stratégies DLP. Par conséquent, l’affichage des nouvelles alertes pour un utilisateur peut prendre un certain temps.

## <a name="alert-status-and-severity"></a>État et gravité de l’alerte

Vous pouvez trier les alertes dans l’un des États suivants :

- **Confirmation**: une alerte a été confirmée et affectée à un cas nouveau ou existant.
- **Ignoré**: une alerte est rejetée comme bénigne dans le processus de triage.
- **Révision requise**: une nouvelle alerte dans laquelle les actions de triage n’ont pas encore été effectuées.
- **Résolu**: alerte faisant partie d’un cas fermé et résolu.

Les scores de risque d’alerte sont automatiquement calculés à partir de plusieurs attributs d’activité de risque. Ces attributs incluent le type d’activité de risque, le nombre et la fréquence de l’occurrence d’activité, l’historique de l’activité des risques de l’utilisateur et l’ajout de risques d’activité susceptibles d’aggraver la gravité de l’activité. Le score de risque d’alerte dirige l’affectation programmatique d’un niveau de gravité de risque pour chaque alerte et ne peut pas être personnalisée. Si les alertes ne sont pas triées et que les activités de risque continuent de s’accumuler sur l’alerte, le niveau de gravité des risques peut augmenter. Les analystes et les enquêteurs de risques peuvent utiliser la gravité des risques d’alerte pour faciliter le tri des alertes conformément aux normes et stratégies de risque de votre organisation.

Les niveaux de gravité des risques d’alerte sont les suivants :

- **Gravité élevée**: l’activité et les indicateurs de l’alerte posent des risques significatifs. Les activités de risque associées sont graves, répétitives et se rattachent fortement à d’autres facteurs de risque significatifs.
- **Gravité moyenne**: l’activité et les indicateurs de l’alerte posent un risque modéré. Les activités de risque associées sont modérées, fréquentes et ont une corrélation avec d’autres facteurs de risque.
- **Faible gravité**: l’activité et les indicateurs de l’alerte constituent un risque mineur. Les activités de risque associées sont mineures, plus rares et ne sont pas liées à d’autres facteurs de risque significatifs.

## <a name="filter-alerts"></a>Alertes de filtre

Selon le nombre et le type de stratégies de gestion des risques Insider actives au sein de votre organisation, il peut s’avérer difficile de vérifier une file d’attente volumineuse. L’utilisation de filtres d’alerte permet aux analystes et aux enquêteurs de trier les alertes en fonction de plusieurs attributs. Pour filtrer les alertes dans le tableau de bord alertes, sélectionnez le contrôle de **filtre** . Vous pouvez filtrer les alertes par un ou plusieurs attributs :

- **État**: sélectionnez une ou plusieurs valeurs d’État pour filtrer la liste des alertes. Les options sont *confirmées*, *ignorées*, *révision requise*et *résolues*.
- **Gravité**: sélectionnez un ou plusieurs niveaux de gravité des risques d’alerte pour filtrer la liste des alertes. Les options sont *élevé*, *moyen*et *faible*.
- **Heure détectée**: sélectionnez les dates de début et de fin de la date de création de l’alerte.
- **Stratégie**: sélectionnez une ou plusieurs stratégies pour filtrer les alertes générées par les stratégies sélectionnées.

## <a name="search-alerts"></a>Alertes de recherche

Pour rechercher le nom d’une alerte pour un mot spécifique, sélectionnez le contrôle de **recherche** et tapez le mot à rechercher. Les résultats de la recherche affichent toute alerte de stratégie contenant le mot défini dans la recherche.

## <a name="triage-alerts"></a>Alertes de triage

Pour trier une alerte de risque d’initié, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **alertes** .
2. Dans le **tableau de bord alertes**, sélectionnez l’alerte à trier.
3. Dans le **volet Détails des alertes**, vous pouvez passer en revue les onglets suivants et trier l’alerte :
    - **Vue d’ensemble**: cet onglet contient des informations générales sur l’alerte et vous permet de la confirmer et de créer une nouvelle demande de devis, ou de la faire disparaître.
        - **État**: état de l’alerte.
        - **Heure de détection**: durée écoulée depuis la génération de l’alerte.
        - **Correspondances de stratégie**: les stratégies qui ont généré l’alerte sont répertoriées. Chaque stratégie est indiquée sous la forme d’un lien vers les détails de la stratégie.
        - **Gravité**: niveau de gravité des risques d’alerte actuel, *élevé*, *moyen*ou *faible*. Le niveau de gravité peut augmenter ou diminuer au fil du temps si l’alerte n’est pas en cours de triage.
        - **Cas**: si confirmé, la casse générée à partir de l’alerte est indiquée. Pour les nouvelles alertes, le champ case a une valeur *None* .
    - **Activité**de l’utilisateur : cet onglet affiche l’historique des activités de l’utilisateur associé à l’alerte. Cet historique inclut d’autres alertes et activités d’événements liées aux indicateurs de risque définis dans le modèle affecté à la stratégie pour cette alerte. Cet historique permet aux analystes et aux investigateurs de risque de factoriser tout comportement à risque passé pour l’employé dans le cadre du processus de triage.
    - **Profil utilisateur**: cet onglet affiche les informations générales sur l’employé affecté à l’alerte.
    - **Confirmer et créer un cas**: visible sur tous les onglets, utilisez ce bouton pour confirmer et créer un nouveau cas. Cela change automatiquement le statut de l’alerte en *confirmé*.
    - **Faire disparaître**: visible sur tous les onglets, utilisez ce bouton pour faire disparaître l’alerte. L’état de l’alerte devient *résolu*.

## <a name="create-a-case-for-an-alert"></a>Créer un cas pour une alerte

Une fois qu’une alerte a été vérifiée et triée, vous pouvez créer un nouveau cas afin d’examiner l’activité de risque. Pour créer un cas pour une alerte, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **alertes** .
2. Dans le **tableau de bord alertes**, sélectionnez l’alerte à vérifier et créez une nouvelle demande de devis.
3. Dans le **volet d’informations alertes**, sélectionnez **confirmer et créer un cas**.
4. Dans la boîte de dialogue **confirmer l’alerte et créer un cas de risque Insider** , entrez un nom pour le cas, sélectionnez les utilisateurs à ajouter en tant que collaborateurs et ajoutez des commentaires, le cas échéant. Les commentaires sont automatiquement ajoutés à l’incident sous la forme d’une note de cas.
5. Sélectionnez **créer un cas** pour créer une nouvelle demande de devis ou cliquez sur **Annuler** pour fermer la boîte de dialogue sans créer de cas.
