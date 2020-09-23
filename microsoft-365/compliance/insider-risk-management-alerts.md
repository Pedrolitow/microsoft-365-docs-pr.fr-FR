---
title: Alertes de gestion des risques internes
description: En savoir plus sur les alertes de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, Insider Risk, gestion des risques, conformité
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

Les alertes de gestion des risques internes sont automatiquement générées par les indicateurs de risque définis dans les stratégies de gestion des risques internes. Ces alertes donnent aux analystes et aux enquêteurs de conformité une vue d’ensemble de l’état de risque actuel et permettent à votre organisation de trier et de prendre des mesures pour les risques détectés. Par défaut, les stratégies génèrent une certaine quantité d’alertes de gravité faible, moyenne et élevée, mais vous pouvez [augmenter ou diminuer le volume des alertes](insider-risk-management-settings.md#alert-volume) en fonction de vos besoins. En outre, vous pouvez configurer le [seuil d’alerte pour les indicateurs de stratégie](insider-risk-management-settings.md#indicator-level-settings-preview) lors de la création d’une stratégie à l’aide de l’Assistant stratégie.

## <a name="alert-dashboard"></a>Tableau de bord d’alerte

Le tableau de **bord des alertes** sur les risques Insiders vous permet d’afficher et d’agir sur les alertes générées par des stratégies de risque initiées. Chaque widget de rapport affiche les informations des 30 derniers jours.

- **Alertes à réviser**: le nombre total d’alertes nécessitant une révision et un triage sont répertoriés, y compris une ventilation par gravité d’alerte.
- **Alertes ouvertes au cours des 30 derniers jours**: nombre total d’alertes créées par des correspondances de stratégie au cours des 30 derniers jours, triées par niveau de gravité d’alerte élevé, moyen et faible.
- **Temps moyen de résolution des alertes**: Résumé des statistiques d’alerte utiles :
    - Délai moyen de résolution des alertes de gravité élevée, indiqué en heures, jours ou mois.
    - Délai moyen de résolution des alertes de gravité moyenne, indiqué en heures, jours ou mois.
    - Délai moyen de résolution des alertes de faible gravité, indiqué en heures, jours ou mois.

![Tableau de bord d’alerte de gestion des risques Insiders](../media/insider-risk-alerts-dashboard.png)

>[!NOTE]
>La gestion des risques internes utilise la limitation d’alertes intégrée pour vous aider à protéger et optimiser vos examens de risque et réviser l’expérience. Cette limitation empêche les problèmes qui peuvent entraîner une surcharge d’alertes de stratégie, telles que la configuration incorrecte des connecteurs de données ou des stratégies DLP. Par conséquent, il peut y avoir un retard dans l'affichage de nouvelles alertes pour un utilisateur.

## <a name="alert-status-and-severity"></a>État de l’alerte et gravité

Vous pouvez trier les alertes dans l’un des États suivants :

- **Confirmation**: une alerte a été confirmée et affectée à un cas nouveau ou existant.
- **Ignoré**: une alerte est rejetée comme bénigne dans le processus de triage.
- **Révision requise**: une nouvelle alerte dans laquelle les actions de triage n’ont pas encore été effectuées.
- **Résolu**: alerte faisant partie d’un cas fermé et résolu.

Les scores de risque d’alerte sont calculés automatiquement à partir de plusieurs indicateurs d’activité de risque. Ces indicateurs incluent le type d’activité de risque, le nombre et la fréquence de l’occurrence d’activité, l’historique de l’activité des risques de l’utilisateur et l’ajout de risques d’activité susceptibles d’aggraver la gravité de l’activité. Le score de risque d'alerte détermine l'affectation programmatique d'un niveau de gravité du risque pour chaque alerte et ne peut être personnalisé. Si les alertes ne sont pas triées et que les activités de risque continuent de s’accumuler sur l’alerte, le niveau de gravité des risques peut augmenter. Les analystes et les enquêteurs de risques peuvent utiliser la gravité des risques d’alerte pour faciliter le tri des alertes conformément aux normes et stratégies de risque de votre organisation.

Les niveaux de gravité des risques d’alerte sont les suivants :

- **Gravité élevée**: les activités et indicateurs de l’alerte posent des risques significatifs. Les activités de risque associées sont graves, répétitives et se rattachent fortement à d’autres facteurs de risque significatifs.
- **Gravité moyenne**: les activités et indicateurs de l’alerte posent un risque modéré. Les activités de risque associées sont modérées, fréquentes et présentent une corrélation avec d’autres facteurs de risque.
- **Faible gravité**: les activités et indicateurs de l’alerte posent un risque mineur. Les activités de risque associées sont mineures, plus rares et ne sont pas liées à d’autres facteurs de risque significatifs.

## <a name="filter-alerts-on-the-alert-dashboard"></a>Filtrer les alertes dans le tableau de bord d’alerte

Selon le nombre et le type de stratégies de gestion des risques internes actif au sein de votre organisation, il peut être difficile de réviser une grande file d’alertes. L’utilisation de filtres d’alerte permet aux analystes et aux enquêteurs de trier les alertes en fonction de plusieurs attributs. Pour filtrer les alertes dans le **tableau de bord alertes**, sélectionnez le contrôle de **filtre** . Vous pouvez filtrer les alertes par un ou plusieurs attributs :

- **État**: sélectionnez une ou plusieurs valeurs d’État pour filtrer la liste des alertes. Les options sont *Confirmé*, *Fermé*, *Révision requise*et *Résolu*.
- **Gravité**: sélectionnez un ou plusieurs niveaux de gravité des risques d’alerte pour filtrer la liste des alertes. Les options disponibles sont *Élevée*, *Moyenne*et *Faible*.
- **Heure détectée**: sélectionnez les dates de début et de fin de la date de création de l’alerte.
- **Stratégie**: sélectionnez une ou plusieurs stratégies pour filtrer les alertes générées par les stratégies sélectionnées.

## <a name="search-alerts-on-the-alert-dashboard"></a>Alertes de recherche dans le tableau de bord d’alerte

Pour rechercher le nom d’une alerte pour un mot spécifique, sélectionnez la commande**Recherche** et tapez le mot à rechercher. Les résultats de la recherche affichent une alerte de stratégie contenant le mot défini dans la recherche.

## <a name="triage-alerts"></a>Alertes de triage

Pour trier une alerte de risque d’initié, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **alertes** .
2. Dans le **tableau de bord alertes**, sélectionnez l’alerte à trier.
3. Dans le **volet Détails des alertes**, vous pouvez passer en revue les onglets suivants et trier l’alerte :
    - **Résumé**: cet onglet contient des informations générales sur l’alerte et vous permet de confirmer l’alerte et de créer un nouvel incident ou de faire disparaître l’alerte. Elle inclut l’état actuel de l’alerte et le niveau de gravité des risques d’alerte, dont la taille est *élevée*, *moyenne*ou *faible*. Le niveau de gravité peut augmenter ou diminuer au fil du temps si l’alerte n’est pas en cours de triage.
        - **Qu’est-il advenu**: affiche les trois principales activités et stratégies de risques lors de la période d’évaluation de l’activité, y compris le type de violation associé à l’activité.
        - **Détails**de l’utilisateur : affiche des informations générales sur l’utilisateur affecté à l’alerte. Si l’anonymisation est activée, les champs nom d’utilisateur, adresse de messagerie, alias et organisation sont anonymes.
        - **Détails**de l’alerte : inclut le laps de temps écoulé depuis que l’alerte a été générée, les stratégies qui ont généré l’alerte sont répertoriées et l’incident généré à partir de l’alerte est répertorié. Pour les nouvelles alertes, le champ **case** affiche aucun.
        - **Contenu détecté**: inclut le contenu associé aux activités de risque pour l’alerte et résume les événements d’activité par domaines clés. La sélection d’un lien activité ouvre l’Explorateur d’activités et affiche des détails supplémentaires sur l’activité.
    - **Activité**de l’utilisateur : cet onglet affiche l’historique des activités de l’utilisateur associé à l’alerte. Cet historique inclut d’autres alertes et activités liées aux indicateurs de risque définis dans le modèle affecté à la stratégie pour cette alerte. Cet historique permet aux analystes et aux investigateurs de risque de factoriser tout comportement à risque passé pour l’employé dans le cadre du processus de triage.
    - **Actions**: les actions suivantes sont disponibles pour chaque alerte :
        - **Ouvrir le mode développé**: ouvre le tableau de bord de l' **Explorateur d’activités** .
        - **Confirm and Create case**: utilisez cette action pour confirmer et créer une nouvelle demande de devis pour toutes les alertes associées à un utilisateur. Cette action modifie automatiquement le statut de l’alerte sur *confirmé*.
        - **Ignorer l’alerte**: utilisez cette action pour faire disparaître l’alerte. Cette action modifie l’état de l’alerte en *résolu*.

## <a name="activity-explorer-preview"></a>Explorateur d’activités (aperçu)

>[!NOTE]
>L’Explorateur d’activités est disponible dans la zone de gestion des alertes pour les utilisateurs qui déclenchent des événements une fois que cette fonctionnalité est disponible dans votre organisation.

L’Explorateur d’activités fournit aux enquêteurs et analystes de risques un outil d’analyse complet qui fournit des informations détaillées sur les alertes. Avec l’Explorateur d’activités, les relecteurs peuvent rapidement consulter une chronologie de l’activité dangereuse détectée et identifier et filtrer toutes les activités liées aux risques associées aux alertes. Pour filtrer les alertes dans l’Explorateur d’activités, sélectionnez le contrôle de filtre. Vous pouvez filtrer les alertes par un ou plusieurs attributs figurant dans le volet d’informations de l’alerte. Activity Explorer prend également en charge les colonnes personnalisables pour aider les enquêteurs et les analystes à orienter le tableau de bord sur les informations les plus importantes pour eux.

![Vue d’ensemble de l’activité de gestion des risques Insiders](../media/insider-risk-management-activity-explorer.png)

Pour utiliser l' **Explorateur d’activités**, procédez comme suit :

1. Dans le centre de conformité Microsoft 365, accédez à **gestion des risques internes** et sélectionnez l’onglet **alertes** .
2. Dans le **tableau de bord alertes**, sélectionnez l’alerte à trier.
3. Dans le **volet Détails des alertes**, sélectionnez **ouvrir le mode étendu**.
4. Sur la page de l’alerte sélectionnée, sélectionnez l’onglet **Explorateur d’activités** .

Lors de l’examen des activités dans l’Explorateur d’activités, les investigateurs et les analystes peuvent sélectionner une activité spécifique et ouvrir le volet des détails de l’activité. Le volet affiche des informations détaillées sur l’activité que les enquêteurs et les analystes peuvent utiliser lors du processus de triage des alertes. Les informations détaillées peuvent fournir un contexte pour l’alerte et aider à identifier l’étendue complète de l’activité de risque qui a déclenché l’alerte.

![Détails de l’Explorateur d’activités de gestion des risques Insiders](../media/insider-risk-management-activity-explorer-details.png)

## <a name="create-a-case-for-an-alert"></a>Créer un cas pour une alerte

Lorsque l’alerte est vérifiée et triée, vous pouvez créer un nouveau cas afin d’examiner l’activité de risque. Pour créer un cas pour une alerte, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **alertes** .
2. Dans le **tableau de bord alertes**, sélectionnez l’alerte à vérifier et créez une nouvelle demande de devis.
3. Dans le **volet d’informations alertes**, sélectionnez **actions**:  >  **confirmer les alertes & créer un cas**.
4. Dans la boîte de dialogue **confirmer l’alerte et créer un cas de risque Insider** , entrez un nom pour le cas, sélectionnez les utilisateurs à ajouter en tant que collaborateurs et ajoutez des commentaires, le cas échéant. Les commentaires sont automatiquement ajoutés à l’incident sous la forme d’une note de cas.
5. Sélectionnez **créer un cas** pour créer une nouvelle demande de devis ou cliquez sur **Annuler** pour fermer la boîte de dialogue sans créer de cas.

Une fois le cas créé, les enquêteurs et les analystes peuvent gérer et agir sur le cas. Pour plus d’informations, consultez l’article relatif à un [cas de gestion des risques inSided](insider-risk-management-cases.md) .
