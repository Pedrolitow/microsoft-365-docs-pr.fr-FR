---
title: Alertes de gestion des risques internes
description: En savoir plus sur les alertes de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, risques internes, gestion des risques, conformité
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
ms.openlocfilehash: 602571e5cbd3132209382ca2e2a3d8941ea8ab2e
ms.sourcegitcommit: e5ac81132cc5fd248350627a3cc7b3c640f53b6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48208825"
---
# <a name="insider-risk-management-alerts"></a>Alertes de gestion des risques internes

Les alertes de gestion des risques internes sont automatiquement générées par les indicateurs de risque définis dans les stratégies de gestion des risques internes. Ces alertes donnent aux analystes et aux enquêteurs de conformité une vue d’ensemble de l’état de risque actuel et permettent à votre organisation de trier et de prendre des mesures pour les risques détectés. Par défaut, les stratégies génèrent une certaine quantité d’alertes de gravité faible, moyenne et élevée, mais vous pouvez augmenter ou diminuer le [volume](insider-risk-management-settings.md#alert-volume) d’alertes en fonction de vos besoins. En outre, vous pouvez configurer le seuil d’alerte pour les indicateurs de stratégie [lors](insider-risk-management-settings.md#indicator-level-settings-preview) de la création d’une stratégie avec l’Assistant Stratégie.

## <a name="alert-dashboard"></a>Tableau de bord d’alerte

Le tableau de **bord** d’alerte des risques internes vous permet d’afficher et d’agir sur les alertes générées par les stratégies de risque internes. Chaque widget de rapport affiche des informations pour les 30 derniers jours.

- **Alertes à réviser**: le nombre total d’alertes devant être revue et triée est répertorié, y compris une répartition par gravité de l’alerte.
- Ouvrez les alertes au cours des **30** derniers jours : nombre total d’alertes créées par les correspondances de stratégie au cours des 30 derniers jours, triées par niveaux de gravité d’alerte élevé, moyen et faible.
- **Durée moyenne de résolution des alertes**: résumé des statistiques d’alerte utiles :
    - Délai moyen de résolution des alertes de gravité élevée, indiqué en heures, jours ou mois.
    - Délai moyen de résolution des alertes de gravité moyenne, indiqué en heures, jours ou mois.
    - Délai moyen de résolution des alertes de faible gravité, indiqué en heures, jours ou mois.

![Tableau de bord des alertes de gestion des risques internes](../media/insider-risk-alerts-dashboard.png)

>[!NOTE]
>La gestion des risques internes utilise la limitation d’alertes intégrée pour vous aider à protéger et optimiser vos examens de risque et réviser l’expérience. Cette limitation empêche les problèmes qui peuvent entraîner une surcharge d’alertes de stratégie, telles que la configuration incorrecte des connecteurs de données ou des stratégies DLP. Par conséquent, il peut y avoir un retard dans l'affichage de nouvelles alertes pour un utilisateur.

## <a name="alert-status-and-severity"></a>État de l’alerte et gravité

Vous pouvez trier les alertes dans l’un des états suivants :

- **Confirmé :** alerte confirmée et affectée à un cas nouveau ou existant.
- **Dismissed**: une alerte rejetée comme étant anodin dans le processus de triage.
- **Doit être revue**: nouvelle alerte dans laquelle des actions de tri n’ont pas encore été prises.
- **Résolu :** alerte qui fait partie d’un cas fermé et résolu.

Les scores de risque d’alerte sont automatiquement calculés à partir de plusieurs indicateurs d’activité de risque. Ces indicateurs incluent le type d’activité à risque, le nombre et la fréquence de l’occurrence de l’activité, l’historique de l’activité de risque utilisateur et l’ajout de risques d’activité qui peuvent renforcer la gravité de l’activité. Le score de risque d'alerte détermine l'affectation programmatique d'un niveau de gravité du risque pour chaque alerte et ne peut être personnalisé. Si les alertes restent non récupérables et que les activités de risque continuent à s’accumuler à l’alerte, le niveau de gravité du risque peut augmenter. Les analystes et enquêteurs de risque peuvent utiliser la gravité des risques d’alerte pour vous aider à trier les alertes conformément aux stratégies et normes de risque de votre organisation.

Les niveaux de gravité des risques d’alerte sont :

- **Gravité élevée :** les activités et les indicateurs de l’alerte présentent un risque important. Les activités de risque associées sont graves, répétitives et essentielles à d’autres facteurs de risque importants.
- **Gravité moyenne :** les activités et les indicateurs de l’alerte présentent un risque modéré. Les activités de risque associées sont modérées, fréquentes et présentent une corrélation avec d’autres facteurs de risque.
- **Faible gravité :** les activités et les indicateurs de l’alerte présentent un risque mineur. Les activités de risque associées sont mineures, plus rares et ne sont pas liées à d’autres facteurs de risque importants.

## <a name="filter-alerts-on-the-alert-dashboard"></a>Filtrer les alertes dans le tableau de bord d’alerte

Selon le nombre et le type de stratégies de gestion des risques internes actif au sein de votre organisation, il peut être difficile de réviser une grande file d’alertes. L’utilisation de filtres d’alerte permet aux analystes et aux enquêteurs de trier les alertes par plusieurs attributs. Pour filtrer les alertes dans le tableau de bord **Alertes,** sélectionnez **le contrôle** Filtre. Vous pouvez filtrer les alertes par un ou plusieurs attributs :

- **État**: sélectionnez une ou plusieurs valeurs d’état pour filtrer la liste d’alertes. Les options sont *Confirmé*, *Fermé*, *Révision requise* et *Résolu*.
- **Gravité : sélectionnez** un ou plusieurs niveaux de gravité des risques d’alerte pour filtrer la liste d’alertes. Les options disponibles sont *Élevée*, *Moyenne* et *Faible*.
- **Heure détectée :** sélectionnez les dates de début et de fin de la création de l’alerte.
- **Stratégie**: sélectionnez une ou plusieurs stratégies pour filtrer les alertes générées par les stratégies sélectionnées.

## <a name="search-alerts-on-the-alert-dashboard"></a>Alertes de recherche dans le tableau de bord d’alerte

Pour rechercher le nom d’une alerte pour un mot spécifique, sélectionnez la commande **Recherche** et tapez le mot à rechercher. Les résultats de la recherche affichent une alerte de stratégie contenant le mot défini dans la recherche.

## <a name="triage-alerts"></a>Alertes de triage

Pour trier une alerte de risque interne, effectuer les étapes suivantes :

1. Dans le Centre de conformité [Microsoft 365,](https://compliance.microsoft.com)allez à **La** gestion des risques internes et sélectionnez **l’onglet Alertes.**
2. Dans le tableau **de bord Alertes,** sélectionnez l’alerte que vous souhaitez trier.
3. Dans le **volet d’informations Alertes,** vous pouvez passer en revue les onglets suivants et trier l’alerte :
    - **Résumé :** Cet onglet contient des informations générales sur l’alerte et vous permet de confirmer l’alerte et de créer un nouveau cas ou vous permet d’ignorer l’alerte. Il inclut l’état actuel de l’alerte et le niveau de gravité du risque d’alerte, répertorié comme *élevé,* *moyen* ou *faible*. Le niveau de gravité peut augmenter ou diminuer au fil du temps si l’alerte n’est pas triée.
        - **Ce qui s’est** passé : affiche les trois principales activités de risque et les correspondances de stratégie pendant la période d’évaluation de l’activité, y compris le type de violation associé à l’activité.
        - **Détails utilisateur :** affiche des informations générales sur l’utilisateur affecté à l’alerte. Si l’anonymisation est activée, le nom d’utilisateur, l’adresse e-mail, l’alias et les champs de l’organisation sont rendus anonymes.
        - **Détails de** l’alerte : inclut la durée depuis que l’alerte a été générée, les stratégies qui ont généré l’alerte sont répertoriées et le cas généré à partir de l’alerte est répertorié. Pour les nouvelles alertes, le **champ Case** affiche Aucune.
        - **Contenu détecté : inclut** le contenu associé aux activités de risque pour l’alerte et récapitule les événements d’activité par zones clés. La sélection d’un lien d’activité ouvre l’Explorateur d’activités et affiche des détails supplémentaires sur l’activité.
    - **Activité de l’utilisateur**: cet onglet affiche l’historique des activités de l’utilisateur associé à l’alerte. Cet historique inclut d’autres alertes et activités liées aux indicateurs de risque définis dans le modèle affecté à la stratégie pour cette alerte. Cet historique permet aux analystes et enquêteurs de risques de prendre en compte tout comportement à risque passé pour l’employé dans le cadre du processus de triage.
    - **Actions**: les actions suivantes sont disponibles pour chaque alerte :
        - **Vue étendue ouverte :** ouvre le tableau de bord de **l’Explorateur d’activités.**
        - **Confirmez et créez un cas**: utilisez cette action pour confirmer et créer un nouveau cas pour toutes les alertes associées à un utilisateur. Cette action modifie automatiquement l’état de l’alerte *sur Confirmé.*
        - **Ignorer l’alerte**: utilisez cette action pour ignorer l’alerte. Cette action modifie l’état de l’alerte *sur Résolu.*

## <a name="activity-explorer-preview"></a>Explorateur d’activités (aperçu)

>[!NOTE]
>L’Explorateur d’activités est disponible dans la zone de gestion des alertes pour les utilisateurs ayant déclenché des événements une fois que cette fonctionnalité est disponible dans votre organisation.

L’Explorateur d’activités fournit aux enquêteurs et aux analystes des risques un outil analytique complet qui fournit des informations détaillées sur les alertes. Avec l’Explorateur d’activités, les réviseurs peuvent rapidement passer en revue une chronologie des activités à risque détectées et identifier et filtrer toutes les activités à risque associées aux alertes. Pour filtrer les alertes dans l’Explorateur d’activités, sélectionnez le contrôle Filtre. Vous pouvez filtrer les alertes par un ou plusieurs attributs répertoriés dans le volet d’informations de l’alerte. L’Explorateur d’activités prend également en charge les colonnes personnalisables pour aider les enquêteurs et les analystes à concentrer le tableau de bord sur les informations les plus importantes pour eux.

![Vue d’ensemble de l’Explorateur d’activités de gestion des risques internes](../media/insider-risk-management-activity-explorer.png)

Pour utiliser **l’Explorateur d’activités,** complétez les étapes suivantes :

1. Dans le Centre de conformité Microsoft  365, sélectionnez l’onglet **Alertes** sur la gestion des risques internes.
2. Dans le tableau **de bord Alertes,** sélectionnez l’alerte que vous souhaitez trier.
3. Dans le **volet Détails des alertes,** **sélectionnez Ouvrir en vue étendue.**
4. Dans la page de l’alerte sélectionnée, sélectionnez l’onglet **Explorateur d’activités.**

Lors de l’examen des activités dans l’Explorateur d’activités, les enquêteurs et les analystes peuvent sélectionner une activité spécifique et ouvrir le volet d’informations sur l’activité. Le volet affiche des informations détaillées sur l’activité que les enquêteurs et les analystes peuvent utiliser pendant le processus de tri des alertes. Les informations détaillées peuvent fournir un contexte pour l’alerte et vous aider à identifier l’étendue complète de l’activité de risque ayant déclenché l’alerte.

![Détails de l’explorateur des activités de gestion des risques internes](../media/insider-risk-management-activity-explorer-details.png)

## <a name="create-a-case-for-an-alert"></a>Créer un cas pour une alerte

Lorsque l’alerte est examinée et triée, vous pouvez créer un cas pour examiner plus en détail l’activité de risque. Pour créer un cas pour une alerte, suivez les étapes suivantes :

1. Dans le Centre de conformité [Microsoft 365,](https://compliance.microsoft.com)allez à **La** gestion des risques internes et sélectionnez **l’onglet Alertes.**
2. Dans le **tableau de bord Alertes,** sélectionnez l’alerte pour qui vous souhaitez confirmer et créer un cas.
3. Dans le **volet d’informations Alertes,** sélectionnez **Actions** Confirmer les  >  **alertes & créer un cas.**
4. Dans la **boîte de** dialogue Confirmer l’alerte et créer un cas de risque interne, entrez un nom pour le cas, sélectionnez les utilisateurs à ajouter en tant que contributeurs et ajoutez des commentaires le cas échéant. Les commentaires sont automatiquement ajoutés au cas en tant que note de cas.
5. Sélectionnez **Créer un cas** pour  créer un cas ou annuler pour fermer la boîte de dialogue sans créer de cas.

Une fois le cas créé, les enquêteurs et les analystes peuvent gérer le cas et agir sur celui-ci. Pour plus [d’informations, voir](insider-risk-management-cases.md) l’article sur la gestion des risques internes.
