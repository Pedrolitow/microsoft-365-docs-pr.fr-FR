---
title: Examiner les activités de gestion des risques internes
description: En savoir plus sur l’examen des activités de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, risque interne, gestion des risques, conformité
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
ms.openlocfilehash: b53b67433bea08e20b082f555c26d41edce55daa
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783334"
---
# <a name="investigate-insider-risk-management-activities"></a>Examiner les activités de gestion des risques internes

L’examen des activités des utilisateurs à risque est une première étape importante dans la réduction des risques internes pour votre organisation. Ces risques peuvent être des activités qui génèrent des alertes à partir de stratégies de gestion des risques internes, ou des risques liés à des activités détectées par des stratégies, mais qui ne créent pas immédiatement une alerte de gestion des risques internes pour les utilisateurs. Vous pouvez examiner ces types d’activités à l’aide des **rapports d’activité utilisateur (préversion)** ou du **tableau de bord Alerte**.

## <a name="user-activity-reports-preview"></a>Rapports d’activité utilisateur (préversion)

Les rapports d’activité utilisateur vous permettent d’examiner les activités de certains utilisateurs pendant une période définie sans avoir à les affecter temporairement ou explicitement à une stratégie de gestion des risques internes. Dans la plupart des scénarios de gestion des risques internes, les utilisateurs sont explicitement définis dans les stratégies, et ils peuvent avoir des alertes de stratégie (en fonction du déclenchement d’événements) et des scores de risque associés aux activités. Toutefois, dans certains scénarios, vous souhaiterez peut-être examiner les activités des utilisateurs qui ne sont pas explicitement définis dans une stratégie. Ces activités peuvent être destinées aux utilisateurs auxquels vous avez reçu un conseil sur l’utilisateur et les activités potentiellement risquées, ou aux utilisateurs qui n’ont généralement pas besoin d’être affectés à une stratégie de gestion des risques internes.

Une fois que vous avez configuré des indicateurs dans la page de gestion des risques internes **Paramètres**, l’activité utilisateur est détectée pour l’activité à risque associée aux indicateurs sélectionnés. Vous n’avez pas besoin de configurer une stratégie pour que les rapports d’activité utilisateur détectent et signalent les activités à risque par les utilisateurs de votre organisation. Les activités incluses dans les rapports d’activité utilisateur ne nécessitent pas de déclenchement d’événements pour que les activités soient affichées. Cette configuration signifie que toutes les activités détectées pour l’utilisateur sont disponibles pour révision, qu’il ait un événement déclencheur ou qu’il crée une alerte. Les rapports sont créés par utilisateur et peuvent inclure toutes les activités pour une période personnalisée de 90 jours. Plusieurs rapports pour le même utilisateur ne sont pas pris en charge.

Après avoir examiné les activités d’un utilisateur, les enquêteurs peuvent ignorer les activités individuelles comme étant bénignes, partager ou envoyer par e-mail un lien vers le rapport avec d’autres enquêteurs, ou choisir d’affecter temporairement ou explicitement l’utilisateur à une stratégie de gestion des risques internes. Les utilisateurs doivent être affectés au groupe de *rôles Insider Risk Management Investigators* pour afficher la page **Rapports d’activité des utilisateurs** .  

![Vue d’ensemble du rapport d’activité des utilisateurs de gestion des risques internes.](../media/insider-risk-user-activity-report-overview.png)

Vous pouvez commencer en sélectionnant **Gérer les rapports** dans la section **Examiner l’activité des utilisateurs** dans la page **Vue d’ensemble** de la gestion des risques internes. Pour afficher les activités d’un utilisateur, sélectionnez d’abord **Créer un rapport d’activité utilisateur** et renseignez les champs suivants dans le volet **Nouveau rapport d’activité utilisateur** :

- **Utilisateur** : rechercher un utilisateur par nom ou adresse e-mail
- **Date de début** : utilisez le contrôle calendrier pour sélectionner la date de début des activités de l’utilisateur.
- **Date de fin** : utilisez le contrôle calendrier pour sélectionner la date de fin des activités de l’utilisateur. La date de fin sélectionnée doit être supérieure à deux jours après la date de début sélectionnée et ne doit pas dépasser 90 jours à partir de la date de début sélectionnée.
Les nouveaux rapports prennent généralement jusqu’à 10 heures avant d’être examinés. Lorsque le rapport est prêt, le *rapport est prêt* dans la colonne **État** de la page Rapport d’activité utilisateur. Sélectionnez l’utilisateur pour afficher le rapport détaillé :

![Rapport d’activité des utilisateurs de gestion des risques internes.](../media/insider-risk-user-activity-report.png)

Le **rapport d’activité utilisateur** de l’utilisateur sélectionné contient les onglets **Activité de l’utilisateur** et **Explorateur d’activités** :

- **Activité de l’utilisateur** : utilisez cette vue de graphique pour examiner les activités et afficher les activités potentielles qui se produisent dans des séquences. Cet onglet est structuré pour permettre un examen rapide d’un cas, y compris une chronologie historique de toutes les activités, les détails de l’activité, le score de risque actuel pour l’utilisateur dans le cas, la séquence d’événements à risque et les contrôles de filtrage pour faciliter les efforts d’investigation.
- **Explorateur d’activités** : **l’onglet Explorateur d’activités** fournit aux enquêteurs des risques un outil analytique complet qui fournit des informations détaillées sur les activités. Avec l’Explorateur d’activités, les réviseurs peuvent rapidement passer en revue une chronologie des activités à risque détectées et identifier et filtrer toutes les activités à risque associées aux alertes. Pour en savoir plus sur l’utilisation de l’Explorateur d’activités, consultez la section *Explorateur d’activités* plus loin dans cet article.

## <a name="alert-dashboard"></a>Tableau de bord d’alerte

Les alertes de gestion des risques internes sont automatiquement générées par les indicateurs de risque définis dans les stratégies de gestion des risques internes. Ces alertes donnent aux analystes et aux enquêteurs de conformité une vue d’ensemble de l’état de risque actuel et permettent à votre organisation de trier et de prendre des mesures pour les risques détectés. Par défaut, les stratégies génèrent une certaine quantité d’alertes de gravité faible, moyenne et élevée, mais vous pouvez [augmenter ou diminuer le volume d’alertes](insider-risk-management-settings.md#alert-volume) en fonction de vos besoins. En outre, vous pouvez configurer le [seuil d’alerte pour les indicateurs de stratégie](insider-risk-management-settings.md#indicator-level-settings-preview) lors de la création d’une stratégie avec l’outil de création de stratégie.

Consultez la [vidéo sur l’expérience de triage des alertes de gestion des risques internes](https://www.youtube.com/watch?v=KgmpxBLJLPI) pour obtenir une vue d’ensemble de la façon dont les alertes fournissent des détails, du contexte et du contenu connexe pour l’activité à risque et comment rendre votre processus d’enquête plus efficace.

Le **tableau de bord Des alertes** à risque interne vous permet d’afficher et d’agir sur les alertes générées par les stratégies de risque interne. Chaque widget de rapport affiche des informations pour les 30 derniers jours.

- **Nombre total d’alertes qui doivent être examinées** : le nombre total d’alertes nécessitant une révision et un triage sont répertoriés, y compris une répartition par gravité d’alerte.
- **Ouvrir des alertes au cours des 30 derniers jours** : nombre total d’alertes créées par la stratégie correspond au cours des 30 derniers jours, triées par niveaux de gravité d’alerte élevés, moyens et faibles.
- **Temps moyen de résolution des alertes** : récapitulatif des statistiques d’alerte utiles :
  - Délai moyen de résolution des alertes de gravité élevée, indiqué en heures, jours ou mois.
  - Délai moyen de résolution des alertes de gravité moyenne, indiqué en heures, jours ou mois.
  - Délai moyen de résolution des alertes de faible gravité, indiqué en heures, jours ou mois.

![Tableau de bord des alertes de gestion des risques internes.](../media/insider-risk-alerts-dashboard.png)

> [!NOTE]
> La gestion des risques internes utilise la limitation d’alertes intégrée pour vous aider à protéger et optimiser vos examens de risque et réviser l’expérience. Cette limitation empêche les problèmes qui peuvent entraîner une surcharge d’alertes de stratégie, telles que la configuration incorrecte des connecteurs de données ou des stratégies DLP. Par conséquent, il peut y avoir un retard dans l'affichage de nouvelles alertes pour un utilisateur.

## <a name="alert-status-and-severity"></a>État de l’alerte et gravité

Vous pouvez trier les alertes dans l’un des états suivants :

- **Confirmé** : alerte confirmée et affectée à un cas nouveau ou existant.
- **Ignoré :** une alerte ignorée comme étant sans gravité dans le processus de triage. Vous pouvez fournir une raison pour le rejet de l’alerte et inclure des notes qui sont disponibles dans l’historique des alertes de l’utilisateur pour fournir un contexte supplémentaire pour une référence ultérieure ou pour d’autres réviseurs. Ces raisons peuvent aller des activités attendues, des événements non impactants, en réduisant simplement le nombre d’activités d’alerte pour l’utilisateur ou en raison des notes d’alerte. Les choix de classification de raison incluent *l’activité est attendue pour cet utilisateur*, *l’activité est suffisamment importante pour que j’examine plus en détail*, et *les alertes pour cet utilisateur contiennent trop d’activité*.
- **Révision des besoins** : nouvelle alerte où les actions de triage n’ont pas encore été effectuées.
- **Résolu** : alerte qui fait partie d’un cas fermé et résolu.

Les scores de risque d’alerte sont automatiquement calculés à partir de plusieurs indicateurs d’activité de risque. Ces indicateurs incluent le type d’activité à risque, le nombre et la fréquence de l’occurrence de l’activité, l’historique de l’activité à risque des utilisateurs et l’ajout de risques d’activité susceptibles d’accroître la gravité de l’activité. Le score de risque d’alerte détermine l’affectation par programme d’un niveau de gravité de risque pour chaque alerte et ne peut pas être personnalisé. Si les alertes restent non triées et que les activités à risque continuent de s’accumuler dans l’alerte, le niveau de gravité du risque peut augmenter. Les analystes et les enquêteurs des risques peuvent utiliser la gravité des risques d’alerte pour faciliter le triage des alertes conformément aux stratégies et normes de risque de votre organisation.

Les niveaux de gravité des risques d’alerte sont les suivants :

- **Gravité élevée** : les activités et les indicateurs de l’alerte présentent des risques significatifs. Les activités à risque associées sont sérieuses, répétitives et se fondent fortement sur d’autres facteurs de risque importants.
- **Gravité moyenne** : les activités et les indicateurs de l’alerte présentent un risque modéré. Les activités de risque associées sont modérées, fréquentes et présentent une corrélation avec d’autres facteurs de risque.
- **Gravité faible** : les activités et les indicateurs de l’alerte présentent un risque mineur. Les activités à risque associées sont mineures, plus peu fréquentes et ne se fondent pas sur d’autres facteurs de risque significatifs.

## <a name="filter-alerts-on-the-alert-dashboard"></a>Filtrer les alertes dans le tableau de bord Des alertes

Selon le nombre et le type de stratégies de gestion des risques internes actif au sein de votre organisation, il peut être difficile de réviser une grande file d’alertes. L’utilisation de filtres d’alerte peut aider les analystes et les enquêteurs à trier les alertes par plusieurs attributs. Pour filtrer les alertes dans le **tableau de bord Alertes**, sélectionnez le contrôle **Filtre** . Vous pouvez filtrer les alertes par un ou plusieurs attributs :

- **État** : sélectionnez une ou plusieurs valeurs d’état pour filtrer la liste d’alertes. Les options sont *Confirmé*, *Fermé*, *Révision requise* et *Résolu*.
- **Gravité** : sélectionnez un ou plusieurs niveaux de gravité de risque d’alerte pour filtrer la liste d’alertes. Les options disponibles sont *Élevée*, *Moyenne* et *Faible*.
- **Heure détectée** : sélectionnez les dates de début et de fin de la création de l’alerte. Ce filtre recherche les alertes comprises entre 00:00 UTC à la date de début et UTC 00:00 à la date de fin. Pour filtrer les alertes pour un jour spécifique, entrez la date du jour dans le champ **Date de début** et la date du jour suivant dans le champ **Date de fin** .
- **Stratégie** : sélectionnez une ou plusieurs stratégies pour filtrer les alertes générées par les stratégies sélectionnées.
- **Facteurs de risque** : sélectionnez l’un des facteurs de risque supplémentaires pour filtrer la liste d’alertes. Les options sont *les activités d’exfiltration cumulative*, *les activités incluent le contenu prioritaire*, *les activités de séquence* et *les activités incluent les domaines non autorisés*.

## <a name="search-alerts-on-the-alert-dashboard"></a>Rechercher des alertes dans le tableau de bord Des alertes

Pour rechercher le nom d’une alerte pour un mot spécifique, sélectionnez la commande **Recherche** et tapez le mot à rechercher. Les résultats de la recherche affichent une alerte de stratégie contenant le mot défini dans la recherche.

## <a name="dismiss-multiple-alerts-preview"></a>Ignorer plusieurs alertes (préversion)

Cela peut aider à gagner du temps de triage pour que les analystes et les enquêteurs ignorent immédiatement plusieurs alertes à la fois. L’option **de barre de commandes Ignorer les alertes** vous permet de sélectionner une ou plusieurs alertes avec un état *de révision des besoins* sur le tableau de bord et d’ignorer rapidement ces alertes comme étant bénignes selon les besoins dans votre processus de triage. Vous pouvez sélectionner jusqu’à 400 alertes à ignorer à la fois.

Pour ignorer une alerte de risque interne, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **la gestion des risques internes** et sélectionnez l’onglet **Alertes**.
2. Dans le **tableau de bord Alertes**, sélectionnez l’alerte (ou les alertes) avec un état de *révision des besoins* que vous souhaitez ignorer.
3. Dans la barre de commandes Alertes, sélectionnez **Ignorer les alertes**.
4. Dans le volet **Ignorer les détails des alertes** , vous pouvez consulter les détails de l’utilisateur et de la stratégie associés aux alertes sélectionnées.
5. Sélectionnez **Ignorer les alertes** pour résoudre les alertes comme étant sans gravité ou sélectionnez **Annuler** pour fermer le volet d’informations sans ignorer les alertes.

## <a name="triage-alerts"></a>Trier les alertes

Pour trier une alerte de risque interne, effectuez les étapes suivantes :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **la gestion des risques internes** et sélectionnez l’onglet **Alertes**.
2. Dans le **tableau de bord Alertes**, sélectionnez l’alerte à trier.
3. Dans la page **détails** de l’alerte, vous pouvez consulter les informations relatives à l’alerte. Vous pouvez confirmer l’alerte et créer un cas, confirmer l’alerte et l’ajouter à un cas existant, ou ignorer l’alerte. Cette page inclut également l’état actuel de l’alerte et le niveau de gravité du risque d’alerte, répertoriés comme élevé, moyen ou faible. Le niveau de gravité peut augmenter ou diminuer au fil du temps si l’alerte n’est pas triée.

Pour plus d’informations sur l’alerte, utilisez les sections et onglets suivants de la page de détails de l’alerte :

### <a name="headersummary-section"></a>Section En-tête/Résumé

Cette section contient des informations générales sur l’utilisateur et l’alerte. Ces informations sont disponibles pour le contexte tout en examinant des informations détaillées sur l’activité détectée incluse dans l’alerte pour l’utilisateur :

- **Activité qui a généré cette alerte** : affiche l’activité à risque supérieur et la correspondance de stratégie pendant la période d’évaluation de l’activité qui a conduit à la génération de l’alerte.
- **Événement de déclenchement** : affiche l’événement de déclenchement le plus récent qui a invité la stratégie à commencer à attribuer des scores de risque à l’activité de l’utilisateur.
- **Profil utilisateur** : affiche des informations générales sur l’utilisateur affecté à l’alerte. Si l’anonymisation est activée, les champs nom d’utilisateur, adresse e-mail, alias et organisation sont rendus anonymes.
- **Historique des alertes** utilisateur : affiche une liste d’alertes pour l’utilisateur au cours des 30 derniers jours. Inclut un lien permettant d’afficher l’historique complet des alertes pour l’utilisateur.

### <a name="all-risk-factors"></a>Tous les facteurs de risque

Cet onglet ouvre le résumé des facteurs de risque pour l’activité d’alerte de l’utilisateur. Les facteurs de risque peuvent vous aider à déterminer le niveau de risque de l’activité de cet utilisateur pendant votre examen. Les facteurs de risque incluent des résumés pour :

- **Principales activités d’exfiltration** : affiche les activités d’exfiltration avec le nombre ou les événements les plus élevés pour l’alerte.
- **Activités d’exfiltration cumulatives** : affiche les événements associés aux activités d’exfiltration cumulatives.
- **Séquences d’activités** : affiche les activités détectées associées aux séquences de risque.
- **Activité inhabituelle pour cet utilisateur** : affiche les activités pour l’utilisateur considérées comme inhabituelles et un écart par rapport à leurs activités habituelles.
- **Contenu de priorité** : affiche les activités associées au contenu prioritaire.
- **Domaines non autorisés** : affiche les activités pour les événements associés à des domaines non autorisés.
- **Accès aux enregistrements** d’intégrité : affiche les activités pour les événements associés à l’accès aux enregistrements d’intégrité.

Avec ces filtres, vous verrez uniquement les alertes avec ces facteurs de risque, mais l’activité qui a généré une alerte peut ne pas faire partie de ces catégories. Par exemple, une alerte contenant des activités de séquence peut avoir été générée simplement parce que l’utilisateur a copié un fichier sur un périphérique USB.

### <a name="content-detected"></a>Contenu détecté

La section de l’onglet **Tous les facteurs de risque** inclut le contenu associé aux activités à risque pour l’alerte et récapitule les événements d’activité par zones clés. La sélection d’un lien d’activité ouvre l’Explorateur d’activités et affiche plus de détails sur l’activité.

### <a name="activity-explorer"></a>Explorateur d’activités

Cet onglet ouvre l’Explorateur d’activités. Pour plus d’informations, consultez la section Explorateur d’activités de cet article.

### <a name="user-activity"></a>Activité utilisateur

Le graphique **d’activité utilisateur** est l’un des outils les plus puissants pour l’analyse des risques internes et l’examen des alertes et des cas dans la solution de gestion des risques internes. Cet onglet est structuré pour permettre un examen rapide de toutes les activités d’un utilisateur, y compris une chronologie historique de toutes les alertes, des détails d’alerte, le score de risque actuel pour l’utilisateur et la séquence d’événements à risque.  

![Activité des utilisateurs de gestion des risques internes.](../media/insider-risk-user-activities.png)

1. **Filtres de temps** : par défaut, les trois derniers mois d’activités affichés dans le graphique d’activité utilisateur. Vous pouvez facilement filtrer l’affichage du graphique en sélectionnant les onglets *6 Mois*, *3 Mois* ou *1 Mois* dans le graphique en bulles.
2. **Activité et détails des alertes de risque** : les activités à risque sont affichées visuellement sous forme de bulles colorées dans le graphique d’activité utilisateur. Les bulles sont créées pour différentes catégories de risques et. Sélectionnez une bulle pour afficher les détails de chaque activité à risque. Les détails sont les suivants :
    - **Date** de l’activité de risque.
    - Catégorie **d’activité de risque**. Par exemple, *des e-mails avec des pièces jointes envoyées en dehors de l’organisation* ou des *fichiers téléchargés à partir de SharePoint Online*.
    - **Score de risque** pour l’alerte. Ce score correspond au score numérique du niveau de gravité des risques d’alerte.
    - Nombre d’événements associés à l’alerte. Des liens vers chaque fichier ou e-mail associé à l’activité à risque sont également disponibles.
3. **Filtres et tri (préversion)** :
    - **Catégorie de risque** : Filtrer les activités selon les catégories de risque suivantes : *Activités avec des scores de risque > 15 (sauf dans une séquence)* et *activités de séquence*.
    - **Type d’activité** : Filtrez les activités selon les types suivants : *Accès*, *Suppression*, *Collection*, *Exfiltration*, *Infiltration*, *Obfuscation* et *Sécurité*.
    - **Trier par** : répertorie les activités de chronologie par *date ou* *score de risque*.
4. **Séquence de risques (préversion)** : l’ordre chronologique des activités à risque est un aspect important de l’examen des risques et l’identification de ces activités connexes est un élément important de l’évaluation du risque global pour votre organisation. Les activités d’alerte associées sont affichées avec des lignes de connexion pour souligner que ces activités sont associées à une zone de risque plus grande. Cette vue des activités peut aider les enquêteurs à « connecter les points » littéralement aux activités à risque qui auraient pu être considérées comme des événements isolés ou ponctuels. Sélectionnez une bulle dans la séquence pour afficher les détails de toutes les activités à risque associées. Les détails sont les suivants :

    - **Nom** de la séquence.
    - **Plage de dates** ou **de dates** de la séquence.
    - **Score de risque** pour la séquence. Ce score est le score numérique pour la séquence des niveaux de gravité de risque d’alerte combinés pour chaque activité associée dans la séquence.
    - **Nombre d’événements associés à chaque alerte dans la séquence**. Des liens vers chaque fichier ou e-mail associé à chaque activité à risque sont également disponibles.
    - **Afficher les activités dans l’ordre**. Affiche la séquence sous la forme d’une ligne de surbrillance sur le graphique en bulles et développe les détails de l’alerte pour afficher toutes les alertes associées dans la séquence.

5. **Légende de l’activité à risque** : en bas du graphique d’activité utilisateur, une légende codée en couleurs vous permet de déterminer rapidement la catégorie de risque pour chaque alerte.
6. **Chronologie de l’activité** de risque : la chronologie complète de toutes les alertes de risque associées au cas est répertoriée, y compris tous les détails disponibles dans la bulle d’alerte correspondante.
7. **Actions de cas** : les options de résolution du cas se trouvent dans la barre d’outils de l’action de cas. Lors de l’affichage dans un cas, vous pouvez résoudre un cas, envoyer une notification par e-mail à l’utilisateur ou faire remonter le cas pour une enquête sur les données ou l’utilisateur.

## <a name="activity-explorer"></a>Explorateur d’activités

> [!NOTE]
> L’Explorateur d’activités est disponible dans la zone de gestion des alertes pour les utilisateurs qui ont déclenché des événements une fois cette fonctionnalité disponible dans votre organisation.

L’Explorateur d’activités fournit aux enquêteurs et aux analystes des risques un outil analytique complet qui fournit des informations détaillées sur les alertes. Avec l’Explorateur d’activités, les réviseurs peuvent rapidement passer en revue une chronologie des activités à risque détectées et identifier et filtrer toutes les activités à risque associées aux alertes. 

Pour filtrer les alertes sur l’Explorateur d’activités pour les informations de colonne, sélectionnez le contrôle Filtre. Vous pouvez filtrer les alertes par un ou plusieurs attributs répertoriés dans le volet d’informations de l’alerte. L’Explorateur d’activités prend également en charge les colonnes personnalisables pour aider les enquêteurs et les analystes à concentrer le tableau de bord sur les informations les plus importantes pour eux.

Utilisez l’étendue d’activité et les filtres d’insights sur les risques pour afficher et trier les activités et les insights pour les zones suivantes.

- **Filtres d’étendue d’activité** : filtre toutes les activités notées pour l’utilisateur.
  - Toutes les activités notées pour cet utilisateur
  - Activité notée uniquement dans cette alerte

- **Filtres de facteur** de risque : filtre l’activité du facteur de risque applicable à toutes les stratégies qui attribuent des scores de risque. Cela inclut toutes les activités pour toutes les stratégies pour les utilisateurs dans l’étendue.
  - Activité inhabituelle
  - Inclut des événements avec un contenu prioritaire
  - Inclut des événements avec un domaine non autorisé
  - Activités de séquence
  - Activités d’exfiltration cumulatives
  - Activités d’accès aux enregistrements d’intégrité

![Vue d’ensemble de l’Explorateur d’activités de gestion des risques internes.](../media/insider-risk-activity-explorer.png)

Pour utiliser **l’Explorateur d’activités**, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **la gestion des risques internes** et sélectionnez l’onglet **Alertes**.
2. Dans le **tableau de bord Alertes**, sélectionnez l’alerte à trier.
3. Dans le **volet Détails des alertes**, sélectionnez **Ouvrir la vue développée**.
4. Dans la page de l’alerte sélectionnée, sélectionnez l’onglet **Explorateur d’activités** .

Lors de l’examen des activités dans l’Explorateur d’activités, les enquêteurs et les analystes peuvent sélectionner une activité spécifique et ouvrir le volet détails de l’activité. Le volet affiche des informations détaillées sur l’activité que les enquêteurs et les analystes peuvent utiliser pendant le processus de triage des alertes. Des informations détaillées peuvent fournir un contexte pour l’alerte et faciliter l’identification de l’étendue complète de l’activité à risque qui a déclenché l’alerte.

Lorsque vous sélectionnez les événements d’une activité dans la chronologie de l’activité, le nombre d’activités affichées dans l’explorateur peut ne pas correspondre au nombre d’événements d’activité répertoriés dans la chronologie. Voici quelques exemples de raisons pour lesquelles cette différence peut se produire :

- **Détection d’exfiltration cumulative** : la détection d’exfiltration cumulative analyse les journaux des événements, mais applique un modèle qui inclut la dé-duplication d’activités similaires pour calculer le risque d’exfiltration cumulée. En outre, il peut également y avoir une différence dans le nombre d’activités affichées dans l’Explorateur d’activités si vous avez apporté des modifications à votre stratégie ou paramètres existants. Par exemple, si vous modifiez des domaines autorisés/non autorisés ou ajoutez de nouvelles exclusions de type de fichier après qu’une stratégie a été créée et que des correspondances d’activité se sont produites, les activités de détection d’exfiltration cumulatives diffèrent des résultats avant que la stratégie ou les paramètres changent. Les totaux d’activité de détection d’exfiltration cumulées sont basés sur la configuration de la stratégie et des paramètres au moment du calcul et n’incluent pas les activités antérieures aux modifications de stratégie et de paramètres
- **E-mails envoyés à des destinataires externes** : l’activité pour les e-mails envoyés aux destinataires externes se voit attribuer un score de risque en fonction du nombre d’e-mails envoyés, ce qui peut ne pas correspondre aux journaux des événements d’activité.

![Détails de l’Explorateur d’activités de gestion des risques internes.](../media/insider-risk-activity-explorer-details.png)

## <a name="create-a-case-for-an-alert"></a>Créer un cas pour une alerte

À mesure que l’alerte est examinée et triée, vous pouvez créer un cas pour examiner plus en détail l’activité à risque. Pour créer un cas d’alerte, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **la gestion des risques internes** et sélectionnez l’onglet **Alertes**.
2. Dans le **tableau de bord Alertes**, sélectionnez l’alerte pour laquelle vous souhaitez confirmer et créer un cas.
3. Dans le **volet Détails des alertes**, sélectionnez **Alertes ActionsConfirm** >  **& créer un cas**.
4. Dans la boîte de dialogue **Confirmer l’alerte et créer un cas de risque interne** , entrez un nom pour le cas, sélectionnez les utilisateurs à ajouter en tant que contributeurs et ajoutez des commentaires le cas échéant. Les commentaires sont automatiquement ajoutés au cas en tant que note de cas.
5. Sélectionnez **Créer un cas** pour créer un cas ou sélectionnez **Annuler** pour fermer la boîte de dialogue sans créer de cas.

Une fois le cas créé, les enquêteurs et les analystes peuvent gérer et agir sur le cas. Pour plus d’informations, consultez l’article [sur la gestion des risques internes](insider-risk-management-cases.md) .

## <a name="retention-and-item-limits"></a>Limites de rétention et d’élément

À mesure que les alertes de gestion des risques internes vieillissent, leur valeur pour réduire l’activité à risque diminue pour la plupart des organisations. À l’inverse, les cas actifs et les artefacts associés (alertes, insights, activités) sont toujours utiles aux organisations et ne doivent pas avoir de date d’expiration automatique. Cela inclut toutes les alertes et artefacts futurs dans un état actif pour tout utilisateur associé à un cas actif.

Pour réduire le nombre d’éléments plus anciens qui fournissent une valeur actuelle limitée, la conservation et les limites suivantes s’appliquent aux alertes de gestion des risques internes, aux cas et aux rapports d’activité des utilisateurs :

|Item|Rétention/limite|
|---|---|
|Alertes avec l’état de révision des besoins|120 jours après la création de l’alerte, puis supprimé automatiquement|
|Cas actifs (et artefacts associés)|Rétention indéfinie, jamais expirer|
|Cas résolus (et artefacts associés)|120 jours à partir de la résolution de cas, puis supprimé automatiquement|
|Nombre maximal de cas actifs|100|
|Rapports d’activités utilisateur|120 jours après la détection d’activité, puis supprimé automatiquement|

## <a name="get-help-managing-your-insider-risk-alert-queue"></a>Obtenir de l’aide sur la gestion de votre file d’attente d’alertes de risque interne

L’examen, l’examen et l’action sur les alertes de risque interne sont des éléments importants de la réduction des risques internes au sein de votre organisation. Prendre rapidement des mesures pour réduire l’impact de ces risques peut potentiellement vous faire gagner du temps, de l’argent et des conséquences réglementaires ou juridiques pour votre organisation. Dans ce processus de correction, la première étape de l’examen des alertes peut sembler la tâche la plus difficile pour de nombreux analystes et enquêteurs. Selon votre situation, vous pouvez être confronté à des obstacles mineurs lors de l’action sur les alertes de risque interne. Passez en revue les recommandations suivantes et découvrez comment optimiser le processus de révision des alertes.

### <a name="too-many-alerts-to-review"></a>Trop d’alertes à examiner

Être submergé par le nombre d’alertes générées par vos stratégies de gestion des risques internes peut être frustrant. Le nombre d’alertes peut être résolu rapidement à l’aide d’étapes simples, en fonction des types de volume d’alertes que vous recevez. Vous recevez peut-être trop d’alertes valides ou vous avez trop d’alertes obsolètes à faible risque. Envisagez d’effectuer les actions suivantes :

- **Ajustez vos stratégies de risque interne** : la sélection et la configuration de la stratégie de risque interne correcte sont la méthode la plus simple pour traiter le type et le volume d’alertes. En commençant par le [modèle de stratégie](insider-risk-management-policies.md#policy-templates) approprié, vous pouvez concentrer les types d’activités et d’alertes à risque que vous verrez. Les autres facteurs susceptibles d’avoir un impact sur le volume d’alertes sont la taille de l’utilisateur et des groupes dans l’étendue, ainsi que le contenu et [les canaux qui sont hiérarchisés](insider-risk-management-policies.md#prioritize-content-in-policies). Envisagez d’ajuster les stratégies pour affiner ces domaines à ce qui est le plus important pour votre organisation.
- **Modifiez vos paramètres de risque interne : les paramètres** de risque Insider incluent une grande variété d’options de configuration qui peuvent avoir un impact sur le volume et les types d’alertes que vous recevrez. Ces paramètres incluent les [paramètres des indicateurs de stratégie](insider-risk-management-settings.md#indicators), [des seuils d’indicateurs](insider-risk-management-settings.md#indicator-level-settings-preview) et [des périodes de stratégie](insider-risk-management-settings.md#policy-timeframes). Envisagez de configurer des options de [détection intelligente](insider-risk-management-settings.md#intelligent-detections) pour exclure des types de fichiers spécifiques, de définir des seuils minimaux avant que vos stratégies ne signalent les alertes d’activité et de remplacer la configuration du volume d’alerte par un paramètre inférieur.
- **Suppression en bloc des alertes le cas échéant** : cela peut vous aider à gagner du temps de triage pour que vos analystes et vos enquêteurs [ignorent immédiatement plusieurs alertes](insider-risk-management-activities.md#dismiss-multiple-alerts-preview) à la fois. Vous pouvez sélectionner jusqu’à 400 alertes à ignorer à la fois.

### <a name="not-familiar-with-the-alert-triage-process"></a>Non familiarisé avec le processus de triage des alertes

L’examen et l’action sur les alertes dans la gestion des risques internes sont simples :

1. **Consultez le [tableau de bord Des](insider-risk-management-activities.md#alert-dashboard) alertes pour les alertes avec l’état Révision des besoins**. [Filtrez](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) par *état* d’alerte si nécessaire pour vous aider à localiser ces types d’alertes.
2. **Commencez par les alertes avec la gravité la plus élevée**. [Filtrez](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) par *gravité* d’alerte si nécessaire pour vous aider à localiser ces types d’alertes.
3. **Sélectionnez une alerte pour découvrir plus d’informations et examiner les détails de l’alerte**. Si nécessaire, utilisez [l’Explorateur d’activités](insider-risk-management-activities.md#activity-explorer) pour passer en revue une chronologie du comportement à risque associé et identifier toutes les activités à risque pour l’alerte.
4. **Agir sur l’alerte**. Vous pouvez soit confirmer et [créer un cas](insider-risk-management-activities.md#create-a-case-for-an-alert) pour l’alerte, soit ignorer et résoudre l’alerte.

### <a name="resource-constraints-in-my-organization"></a>Contraintes de ressources dans mon organisation

Les utilisateurs du milieu de travail moderne ont souvent une grande variété de responsabilités et de demandes sur leur temps. Vous pouvez effectuer plusieurs actions pour résoudre les contraintes de ressources :

- **Concentrez d’abord les efforts des analystes et des enquêteurs sur les alertes à risque le plus élevé**. Selon vos stratégies, vous pouvez capturer des activités et générer des alertes avec différents degrés d’impact potentiel sur vos efforts d’atténuation des risques. [Filtrez les alertes](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) par gravité et *hiérarchisez* les alertes de gravité élevée.
- **Affecter des utilisateurs en tant qu’analystes et enquêteurs**. Le fait d’affecter le bon utilisateur aux rôles appropriés est une partie importante du processus de révision des alertes de risque interne. Vérifiez que vous avez affecté les utilisateurs appropriés aux *groupes de rôles Analystes de gestion des risques internes* et *Enquêteurs de gestion des risques internes* .  
- **Utilisez des fonctionnalités de risque interne automatisé pour vous aider à découvrir les activités à risque le plus élevé**. Les fonctionnalités de [détection de séquence](insider-risk-management-policies.md#sequence-detection-preview) de gestion des risques internes et de [détection d’exfiltration cumulative](insider-risk-management-policies.md#cumulative-exfiltration-detection-preview) peuvent vous aider à découvrir rapidement les risques plus difficiles à détecter dans votre organisation. Envisagez d’affiner vos [boosters de score de risque](insider-risk-management-settings.md#indicators), [les exclusions de type de fichier](insider-risk-management-settings.md#file-type-exclusions), [les domaines](insider-risk-management-settings.md#domains) et les [paramètres de seuil d’indicateur](insider-risk-management-settings.md#indicator-level-settings-preview) minimum pour vos stratégies.
