---
title: Examiner les activités de gestion des risques internes
description: En savoir plus sur l’étude des activités de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, risques internes, gestion des risques, conformité
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
ms.openlocfilehash: 5f52b9391940204e53af03aaee3d5776da67b219
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2021
ms.locfileid: "60334541"
---
# <a name="investigate-insider-risk-management-activities"></a>Examiner les activités de gestion des risques internes

L’étude des activités des utilisateurs à risque est une première étape importante pour réduire les risques internes pour votre organisation. Ces risques peuvent être des activités qui génèrent des alertes à partir de stratégies de gestion des risques internes ou des risques d’activités détectées par des stratégies, mais qui ne créent pas immédiatement une alerte de gestion des risques internes pour les utilisateurs. Vous pouvez examiner ces types d’activités à l’aide des rapports d’activité de l’utilisateur **(aperçu)** ou du tableau de bord **d’alerte.**

## <a name="user-activity-reports-preview"></a>Rapports d’activité utilisateur (aperçu)

Les rapports d’activité des utilisateurs vous permettent d’examiner les activités de certains utilisateurs pendant une période définie sans avoir à les affecter temporairement ou explicitement à une stratégie de gestion des risques internes. Dans la plupart des scénarios de gestion des risques internes, les utilisateurs sont explicitement définis dans des stratégies et peuvent avoir des alertes de stratégie (selon le déclenchement d’événements) et des scores de risque associés aux activités. Toutefois, dans certains scénarios, vous pouvez examiner les activités des utilisateurs qui ne sont pas explicitement définis dans une stratégie. Ces activités peuvent être pour les utilisateurs pour qui vous avez reçu un conseil sur l’utilisateur et les activités potentiellement risquées, ou les utilisateurs qui n’ont généralement pas besoin d’être affectés à une stratégie de gestion des risques internes.

Une fois que vous avez configuré les indicateurs sur la page de gestion des risques internes **Paramètres,** l’activité des utilisateurs est détectée pour les activités risquées associées aux indicateurs sélectionnés. Il n’est pas nécessaire de configurer une stratégie pour les rapports d’activité des utilisateurs afin de détecter et signaler les activités risquées par les utilisateurs de votre organisation. Les activités incluses dans les rapports d’activité des utilisateurs ne nécessitent pas de déclenchement d’événements pour que les activités soient affichées. Cette configuration signifie que toutes les activités détectées pour l’utilisateur sont disponibles pour révision, qu’elle ait un événement déclencheur ou qu’elle crée une alerte. Les rapports sont créés par utilisateur et peuvent inclure toutes les activités pour une période personnalisée de 90 jours. Plusieurs rapports pour le même utilisateur ne sont pas pris en charge.

Après avoir examiné les activités d’un utilisateur, les enquêteurs peuvent ignorer les activités individuelles comme étant anodins, partager ou envoyer par courrier électronique un lien vers le rapport avec d’autres enquêteurs, ou choisir d’affecter temporairement ou explicitement l’utilisateur à une stratégie de gestion des risques internes. Les utilisateurs doivent être affectés au groupe de *rôles Enquêteurs* de gestion des risques internes pour afficher la page Rapports **d’activité des utilisateurs.**  

![Vue d’ensemble du rapport d’activité des utilisateurs de gestion des risques internes.](../media/insider-risk-user-activity-report-overview.png)

Vous pouvez commencer en sélectionnant **Gérer** les rapports dans la **section** Examiner l’activité des utilisateurs dans la page Vue d’ensemble de la gestion des risques **internes.** Pour afficher les activités d’un utilisateur, sélectionnez d’abord Créer un rapport d’activité utilisateur et complétez les champs suivants dans le volet Nouveau rapport d’activité **de l’utilisateur** : 

- **Utilisateur**: rechercher un utilisateur par nom ou adresse e-mail
- **Date de début**: utilisez le contrôle calendrier pour sélectionner la date de début des activités de l’utilisateur.
- **Date de fin**: utilisez le contrôle calendrier pour sélectionner la date de fin des activités de l’utilisateur. La date de fin sélectionnée doit être supérieure à deux jours après la date de début sélectionnée et pas plus de 90 jours à partir de la date de début sélectionnée.
Les nouveaux rapports prennent généralement jusqu’à 10 heures avant d’être prêts pour révision. Lorsque le rapport est prêt,  le rapport est prêt dans la colonne **État** de la page Rapport d’activité de l’utilisateur. Sélectionnez l’utilisateur pour afficher le rapport détaillé :

![Rapport d’activité utilisateur de gestion des risques internes.](../media/insider-risk-user-activity-report.png)

Le **rapport d’activité de** l’utilisateur sélectionné contient les onglets Activité de l’utilisateur et Explorateur  **d’activités** :

- **Activité utilisateur**: utilisez cette vue de graphique pour examiner les activités et afficher les activités potentielles qui se produisent par séquences. Cet onglet est structuré pour permettre un examen rapide d’un cas, y compris une chronologie historique de toutes les activités, les détails de l’activité, le score de risque actuel pour l’utilisateur dans le cas, la séquence d’événements de risque et les contrôles de filtrage pour faciliter les recherches.
- **Explorateur d’activités**: **l’onglet Explorateur** d’activités fournit aux enquêteurs des risques un outil analytique complet qui fournit des informations détaillées sur les activités. Avec l’Explorateur d’activités, les réviseurs peuvent rapidement passer en revue une chronologie des activités à risque détectées et identifier et filtrer toutes les activités à risque associées aux alertes. Pour en savoir plus sur l’utilisation de l’Explorateur d’activités, consultez la *section* Explorateur d’activités plus loin dans cet article.

## <a name="alert-dashboard"></a>Tableau de bord d’alerte

Les alertes de gestion des risques internes sont automatiquement générées par les indicateurs de risque définis dans les stratégies de gestion des risques internes. Ces alertes donnent aux analystes et aux enquêteurs de conformité une vue d’ensemble de l’état de risque actuel et permettent à votre organisation de trier et de prendre des mesures pour les risques détectés. Par défaut, les stratégies génèrent une certaine quantité d’alertes de gravité faible, moyenne et élevée, mais vous pouvez augmenter ou diminuer le [volume](insider-risk-management-settings.md#alert-volume) d’alertes en fonction de vos besoins. En outre, vous pouvez configurer le seuil d’alerte pour les indicateurs de stratégie [lors](insider-risk-management-settings.md#indicator-level-settings-preview) de la création d’une stratégie avec l’outil de création de stratégie.

Consultez la vidéo Expérience de triage des [alertes](https://www.youtube.com/watch?v=KgmpxBLJLPI) de gestion des risques internes pour obtenir une vue d’ensemble de la façon dont les alertes fournissent des détails, du contexte et du contenu associé pour les activités risquées et comment rendre votre processus d’examen plus efficace.

Le tableau de **bord** des alertes de risques internes vous permet d’afficher et d’agir sur les alertes générées par les stratégies de risque internes. Chaque widget de rapport affiche des informations pour les 30 derniers jours.

- **Nombre total d’alertes** qui doivent être revue : le nombre total d’alertes devant être revue et triée sont répertoriés, y compris une répartition par gravité de l’alerte.
- Ouvrez les alertes au cours des **30** derniers jours : nombre total d’alertes créées par les correspondances de stratégie au cours des 30 derniers jours, triées par niveaux de gravité d’alerte élevé, moyen et faible.
- **Durée moyenne de résolution des alertes**: résumé des statistiques d’alerte utiles :
  - Délai moyen de résolution des alertes de gravité élevée, indiqué en heures, jours ou mois.
  - Délai moyen de résolution des alertes de gravité moyenne, indiqué en heures, jours ou mois.
  - Délai moyen de résolution des alertes de faible gravité, indiqué en heures, jours ou mois.

![Tableau de bord d’alerte de gestion des risques internes.](../media/insider-risk-alerts-dashboard.png)

> [!NOTE]
> La gestion des risques internes utilise la limitation d’alertes intégrée pour vous aider à protéger et optimiser vos examens de risque et réviser l’expérience. Cette limitation empêche les problèmes qui peuvent entraîner une surcharge d’alertes de stratégie, telles que la configuration incorrecte des connecteurs de données ou des stratégies DLP. Par conséquent, il peut y avoir un retard dans l'affichage de nouvelles alertes pour un utilisateur.

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
- **Heure détectée :** sélectionnez les dates de début et de fin de la création de l’alerte. Ce filtre recherche les alertes entre 00:00 UTC à la date de début et 00:00 UTC à la date de fin. Pour filtrer les alertes pour un jour spécifique, entrez la date du jour dans le champ **Date** de début et la date du jour suivant dans le champ **Date de** fin.
- **Stratégie**: sélectionnez une ou plusieurs stratégies pour filtrer les alertes générées par les stratégies sélectionnées.

## <a name="search-alerts-on-the-alert-dashboard"></a>Alertes de recherche dans le tableau de bord d’alerte

Pour rechercher le nom d’une alerte pour un mot spécifique, sélectionnez la commande **Recherche** et tapez le mot à rechercher. Les résultats de la recherche affichent une alerte de stratégie contenant le mot défini dans la recherche.

## <a name="dismiss-multiple-alerts-preview"></a>Ignorer plusieurs alertes (aperçu)

Cela peut permettre aux analystes et aux enquêteurs de faire disparaître immédiatement plusieurs alertes à la fois. L’option Ignorer la barre de commandes **alertes** vous  permet de sélectionner une ou plusieurs alertes avec l’état Révision des besoins dans le tableau de bord et de faire disparaître rapidement ces alertes comme étant anodins selon le cas dans votre processus de tri. Vous pouvez sélectionner jusqu’à 400 alertes à ignorer en même temps.

Pour ignorer une alerte de risque interne, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)allez à **La** Gestion des risques internes et sélectionnez **l’onglet Alertes.**
2. Dans le tableau **de bord Alertes,** sélectionnez  l’alerte (ou les alertes) avec l’état De révision des besoins que vous souhaitez ignorer.
3. Dans la barre de commandes Alertes, sélectionnez **Ignorer les alertes.**
4. Dans le volet Détails Ignorer les **alertes,** vous pouvez passer en revue les détails de l’utilisateur et de la stratégie associés aux alertes sélectionnées.
5. Sélectionnez **Ignorer les alertes** pour résoudre les alertes comme étant anodins ou sélectionnez **Annuler** pour fermer le volet d’informations sans ignorer les alertes.

## <a name="triage-alerts"></a>Alertes de triage

Pour trier une alerte de risque interne, effectuer les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)allez à **La** Gestion des risques internes et sélectionnez **l’onglet Alertes.**
2. Dans le tableau **de bord Alertes,** sélectionnez l’alerte que vous souhaitez trier.
3. Dans la **page** des détails de l’alerte, vous pouvez passer en revue les informations sur l’alerte et vous pouvez confirmer l’alerte et créer un nouveau cas, confirmer l’alerte et l’ajouter à un cas existant, ou pour ignorer l’alerte. Cette page inclut également l’état actuel de l’alerte et le niveau de gravité du risque d’alerte, répertorié comme élevé, moyen ou faible. Le niveau de gravité peut augmenter ou diminuer au fil du temps si l’alerte n’est pas triée.

    Les onglets de la page **détails de l’alerte** fournissent plus d’informations pour l’alerte :
    - **Résumé :** Cet onglet contient des informations générales sur l’alerte.
        - **Quel a été l’événement** déclencheur ? : affiche l’événement déclencheur le plus récent qui a invité la stratégie à commencer à affecter des scores de risque à l’activité de l’utilisateur.
        - **Activité qui a généré cette** alerte : affiche l’activité à risque le plus élevé et la correspondance de stratégie pendant la période d’évaluation de l’activité qui a conduit à la générer.
        - **Informations sur les risques pour l’activité dans cette alerte**: affiche le nombre d’informations sur les risques pour l’alerte. Voici quelques exemples si l’alerte contient des activités de séquence, un risque d’activité d’exfiltration cumulée, une activité qui inclut des événements avec des domaines nonallés, une activité qui inclut des événements avec un contenu prioritaire ou des activités inhabituelles pour l’utilisateur.
        - **Détails utilisateur :** affiche des informations générales sur l’utilisateur affecté à l’alerte. Si l’anonymisation est activée, le nom d’utilisateur, l’adresse e-mail, l’alias et les champs de l’organisation sont rendus anonymes.
        - **Détails de** l’alerte : inclut la durée depuis que l’alerte a été générée, les stratégies qui ont généré l’alerte sont répertoriées et le cas généré à partir de l’alerte est répertorié. Pour les nouvelles alertes, le **champ Case** affiche Aucune.
        - **Contenu détecté : inclut** le contenu associé aux activités à risque pour l’alerte et récapitule les événements d’activité par zones clés. La sélection d’un lien d’activité ouvre l’Explorateur d’activités et affiche plus de détails sur l’activité.
    - **Explorateur d’activités**: cet onglet ouvre **l’Explorateur d’activités.** Pour plus d’informations, voir la section suivante de cet article.

## <a name="activity-explorer"></a>Explorateur d’activités

> [!NOTE]
> L’Explorateur d’activités est disponible dans la zone de gestion des alertes pour les utilisateurs ayant déclenché des événements une fois que cette fonctionnalité est disponible dans votre organisation.

L’Explorateur d’activités fournit aux enquêteurs et aux analystes des risques un outil analytique complet qui fournit des informations détaillées sur les alertes. Avec l’Explorateur d’activités, les réviseurs peuvent rapidement passer en revue une chronologie des activités à risque détectées et identifier et filtrer toutes les activités à risque associées aux alertes. 

Pour filtrer les alertes dans l’Explorateur d’activités pour obtenir des informations sur les colonnes, sélectionnez le contrôle Filtre. Vous pouvez filtrer les alertes par un ou plusieurs attributs répertoriés dans le volet d’informations de l’alerte. L’Explorateur d’activités prend également en charge les colonnes personnalisables pour aider les enquêteurs et les analystes à concentrer le tableau de bord sur les informations les plus importantes pour eux.

Utilisez les filtres d’étendue activité et d’informations sur les risques pour afficher et trier les activités et les informations pour les domaines suivants.

- **Filtres d’étendue d’activité**: filtre toutes les activités scored pour l’utilisateur.
    - Toutes les activités scored pour cet utilisateur
    - Activité uniquement avec note dans cette alerte

- **Filtres d’informations sur les risques**: filtres d’activité applicables à toutes les stratégies qui attribuent des scores de risque.
    - Activités d’exfiltration cumulatives
    - Inclut un événement avec un contenu prioritaire
    - Inclut un événement avec un domaine nonallifié
    - Activités de séquence
    - Activité inhabituelle

![Vue d’ensemble de l’Explorateur d’activités de gestion des risques internes.](../media/insider-risk-activity-explorer.png)

Pour utiliser **l’Explorateur d’activités,** complétez les étapes suivantes :

1. Dans la Centre de conformité Microsoft 365, **sélectionnez** l’onglet **Alertes** sur la gestion des risques internes.
2. Dans le tableau **de bord Alertes,** sélectionnez l’alerte que vous souhaitez trier.
3. Dans le **volet Détails des alertes,** **sélectionnez Ouvrir en vue étendue.**
4. Dans la page de l’alerte sélectionnée, sélectionnez l’onglet **Explorateur d’activités.**

Lors de l’examen des activités dans l’Explorateur d’activités, les enquêteurs et les analystes peuvent sélectionner une activité spécifique et ouvrir le volet d’informations sur l’activité. Le volet affiche des informations détaillées sur l’activité que les enquêteurs et les analystes peuvent utiliser pendant le processus de tri des alertes. Les informations détaillées peuvent fournir un contexte pour l’alerte et vous aider à identifier l’étendue complète de l’activité de risque ayant déclenché l’alerte.

Lorsque vous sélectionnez les événements d’une activité dans la chronologie de l’activité, le nombre d’activités affichées dans l’explorateur peut ne pas correspondre au nombre d’événements d’activité répertoriés dans la chronologie. Voici quelques exemples de la raison pour laquelle cette différence peut se produire :

- **Détection d’exfiltration** cumulative : la détection d’exfiltration cumulative analyse les journaux des événements, mais applique un modèle qui inclut la déplicatation d’activités similaires pour calculer le risque d’exfiltration cumulé. En outre, il peut également y avoir une différence dans le nombre d’activités affichées dans l’Explorateur d’activités si vous avez apporté des modifications à votre stratégie ou paramètres existants. Par exemple, si vous modifiez des domaines autorisés/non autorisés ou ajoutez de nouvelles exclusions de types de fichiers après la création d’une stratégie et l’établissement de correspondances d’activité, les activités de détection d’exfiltration cumulatives diffèrent des résultats avant la modification de la stratégie ou des paramètres. Les totaux cumulés de l’activité de détection d’exfiltration sont basés sur la configuration de la stratégie et des paramètres au moment du calcul et n’incluent pas les activités antérieures à la stratégie et aux modifications de paramètres
- **Courriers électroniques envoyés** à des destinataires externes : un score de risque est attribué à l’activité des courriers électroniques envoyés à des destinataires externes en fonction du nombre d’e-mails envoyés, ce qui peut ne pas correspondre aux journaux des événements d’activité.

![Détails de l’explorateur des activités de gestion des risques internes.](../media/insider-risk-activity-explorer-details.png)

## <a name="create-a-case-for-an-alert"></a>Créer un cas pour une alerte

Lorsque l’alerte est examinée et triée, vous pouvez créer un cas pour examiner plus en détail l’activité de risque. Pour créer un cas pour une alerte, suivez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)allez à **La** Gestion des risques internes et sélectionnez **l’onglet Alertes.**
2. Dans le **tableau de bord Alertes,** sélectionnez l’alerte pour qui vous souhaitez confirmer et créer un cas.
3. Dans le **volet d’informations Alertes,** sélectionnez **Actions** Confirmer les  >  **alertes & créer un cas.**
4. Dans la **boîte de** dialogue Confirmer l’alerte et créer un cas de risque interne, entrez un nom pour le cas, sélectionnez les utilisateurs à ajouter en tant que contributeurs et ajoutez des commentaires le cas échéant. Les commentaires sont automatiquement ajoutés au cas en tant que note de cas.
5. Sélectionnez **Créer un cas** pour  créer un cas ou annuler pour fermer la boîte de dialogue sans créer de cas.

Une fois le cas créé, les enquêteurs et les analystes peuvent gérer le cas et agir sur celui-ci. Pour plus d’informations, consultez l’article sur la gestion des [risques internes.](insider-risk-management-cases.md)

## <a name="get-help-managing-your-insider-risk-alert-queue"></a>Obtenir de l’aide pour gérer votre file d’attente d’alertes de risques internes

L’examen, l’examen et l’action sur les alertes de risques internes sont des éléments importants de la réduction des risques internes dans votre organisation. Une action rapide pour réduire l’impact de ces risques peut potentiellement faire gagner du temps, de l’argent et des conséquences réglementaires ou juridiques pour votre organisation. Dans ce processus de correction, la première étape de la révision des alertes peut sembler la tâche la plus difficile pour de nombreux analystes et enquêteurs. Selon vos circonstances, vous pouvez être confronté à des obstacles mineurs lors de l’action sur les alertes de risques internes. Examinez les recommandations suivantes et découvrez comment optimiser le processus de révision des alertes.

### <a name="too-many-alerts-to-review"></a>Trop d’alertes à réviser

Être submergé par le nombre d’alertes produites par vos stratégies de gestion des risques internes peut être frustrant. Le nombre d’alertes peut être traité rapidement en plusieurs étapes simples, en fonction des types de volume d’alertes que vous recevez. Il se peut que vous receviez trop d’alertes valides ou que vous en receviez trop. Envisagez d’agir comme suit :

- **Ajustez vos stratégies** de risques internes : la sélection et la configuration de la stratégie de risque interne correcte est la méthode la plus simple pour traiter le type et le volume des alertes. En commençant par le modèle [de stratégie approprié,](insider-risk-management-policies.md#policy-templates) vous pouvez vous concentrer sur les types d’activités à risque et d’alertes que vous verrez. Les autres facteurs qui peuvent avoir un impact sur le volume des alertes sont la taille de l’utilisateur et des groupes dans l’étendue, ainsi que le contenu et les canaux qui sont classés [par ordre de priorité.](insider-risk-management-policies.md#prioritize-content-in-policies) Envisagez d’ajuster les stratégies pour affiner ces domaines sur ce qui est le plus important pour votre organisation.
- **Modifier vos paramètres de** risques internes : les paramètres des risques internes incluent un large éventail d’options de configuration qui peuvent avoir un impact sur le volume et les types d’alertes que vous recevrez. Il s’agit notamment des [paramètres des indicateurs de stratégie,](insider-risk-management-settings.md#indicators)des [seuils d’indicateurs](insider-risk-management-settings.md#indicator-level-settings-preview)et des délais [de stratégie.](insider-risk-management-settings.md#policy-timeframes) Envisagez de configurer des options de détection intelligente pour exclure des types de fichiers [spécifiques,](insider-risk-management-settings.md#intelligent-detections) définir des seuils minimaux avant que les alertes d’activité soient signalées par vos stratégies et modifier la configuration du volume d’alertes à un paramètre inférieur.
- **Suppression en bloc** d’alertes le cas échéant : cela peut permettre à vos analystes et enquêteurs de faire immédiatement disparaître plusieurs [alertes](insider-risk-management-activities.md#dismiss-multiple-alerts-preview) en même temps. Vous pouvez sélectionner jusqu’à 400 alertes à ignorer en même temps.

### <a name="not-familiar-with-the-alert-triage-process"></a>Peu familiarisé avec le processus de tri des alertes

L’investigation et l’action sur les alertes dans la gestion des risques internes sont simples :

1. **Examinez le tableau [de bord d’alerte](insider-risk-management-activities.md#alert-dashboard) pour les alertes dont l’état est Révision des besoins.** [Filtrez](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) par état *d’alerte* si nécessaire pour vous aider à localiser ces types d’alertes.
2. **Commencez par les alertes avec la gravité la plus élevée.** [Filtrez](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) par gravité *d’alerte si* nécessaire pour vous aider à localiser ces types d’alertes.
3. **Sélectionnez une alerte pour découvrir plus d’informations et passer en revue les détails de l’alerte.** Si nécessaire, utilisez [l’Explorateur d’activités](insider-risk-management-activities.md#activity-explorer) pour passer en revue une chronologie du comportement à risque associé et identifier toutes les activités à risque de l’alerte.
4. **Agir sur l’alerte**. Vous pouvez confirmer et créer [un cas pour](insider-risk-management-activities.md#create-a-case-for-an-alert) l’alerte ou ignorer et résoudre l’alerte.

### <a name="resource-constraints-in-my-organization"></a>Contraintes de ressources dans mon organisation

Les utilisateurs de l’espace de travail moderne ont souvent un large éventail de responsabilités et de demandes sur leur temps. Vous pouvez prendre plusieurs mesures pour vous aider à résoudre les contraintes de ressources :

- **Concentrez d’abord les efforts de l’analyste et des enquêteurs sur les alertes à risque le plus élevé.** Selon vos stratégies, vous pouvez capturer des activités et générer des alertes avec différents degrés d’impact potentiel sur vos efforts de prévention des risques. [Filtrez les alertes](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) par gravité et hiérarchisez *les alertes de gravité* élevée.
- **Affectez des utilisateurs en tant qu’analystes et enquêteurs.** Le fait que l’utilisateur approprié soit affecté aux rôles appropriés est une partie importante du processus de révision des alertes de risque internes. Assurez-vous que vous avez affecté les utilisateurs appropriés aux groupes de rôles *Analystes* de gestion des risques internes et *Enquêteurs* de gestion des risques internes.  
- **Utilisez les fonctionnalités de risques internes automatisées pour découvrir les activités** à risque le plus élevé. La détection de [séquences de](insider-risk-management-policies.md#sequence-detection-preview) gestion des risques internes et les fonctionnalités de détection [d’exfiltration](insider-risk-management-policies.md#cumulative-exfiltration-detection-preview) cumulée peuvent vous aider à découvrir rapidement les risques plus difficiles à trouver dans votre organisation. Pensez à affiner vos scores de [risque,](insider-risk-management-settings.md#indicators)les [exclusions](insider-risk-management-settings.md#file-type-exclusions)de types de fichiers, les domaines et les [paramètres](insider-risk-management-settings.md#domains-preview)de seuil d’indicateur minimum pour vos stratégies. [](insider-risk-management-settings.md#indicator-level-settings-preview)
