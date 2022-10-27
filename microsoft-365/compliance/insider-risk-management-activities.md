---
title: Examiner les activités de gestion des risques internes
description: En savoir plus sur les activités de gestion des risques internes dans Microsoft Purview
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
ms.openlocfilehash: e35809f3cf95bd9995c21b638e5a4c1fef8027df
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68734910"
---
# <a name="investigate-insider-risk-management-activities"></a>Examiner les activités de gestion des risques internes

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

L’examen des activités potentiellement risquées des utilisateurs est une première étape importante pour réduire les risques internes pour votre organisation. Ces risques peuvent être des activités qui génèrent des alertes à partir de stratégies de gestion des risques internes. Ils peuvent également être des risques liés aux activités liées à la conformité qui sont détectés par les stratégies, mais qui ne créent pas immédiatement des alertes de gestion des risques internes pour les utilisateurs. Vous pouvez examiner ces types d’activités à l’aide des **rapports d’activité utilisateur (préversion)** ou avec le **tableau de bord Alerte**.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="user-activity-reports"></a>Rapports d'activité des utilisateurs

Les rapports d’activité utilisateur vous permettent d’examiner les activités potentiellement risquées (pour des utilisateurs spécifiques et pour une période définie) sans avoir à affecter ces activités, temporairement ou explicitement, à une stratégie de gestion des risques internes. Dans la plupart des scénarios de gestion des risques internes, les utilisateurs sont explicitement définis dans les stratégies et peuvent avoir des alertes de stratégie (en fonction du déclenchement d’événements) et des scores de risque associés aux activités. Toutefois, dans certains scénarios, vous pouvez examiner les activités des utilisateurs qui ne sont pas explicitement définies dans une stratégie. Ces activités peuvent être destinées aux utilisateurs dont vous avez reçu un conseil sur l’utilisateur et les activités potentiellement risquées, ou aux utilisateurs qui n’ont généralement pas besoin d’être affectés à une stratégie de gestion des risques internes.

Une fois que vous avez configuré des indicateurs dans la page **Paramètres** de gestion des risques internes, l’activité utilisateur est détectée pour les activités potentiellement à risque associées aux indicateurs sélectionnés. Cette configuration signifie que toutes les activités détectées pour les utilisateurs sont disponibles pour révision, qu’elle ait un événement déclencheur ou qu’elle crée une alerte. Les rapports sont créés par utilisateur et peuvent inclure toutes les activités pour une période personnalisée de 90 jours. Plusieurs rapports pour le même utilisateur ne sont pas pris en charge.

Après avoir examiné les activités potentiellement risquées, les enquêteurs peuvent ignorer les activités d’un utilisateur individuel comme étant sans gravité. Ils peuvent également partager ou envoyer par e-mail un lien vers le rapport avec d’autres enquêteurs, ou choisir d’affecter des utilisateurs (temporairement ou explicitement) à une stratégie de gestion des risques internes. Les utilisateurs doivent être affectés au groupe de rôles *Enquêteurs de gestion des risques internes* pour afficher la page **Rapports d’activité des utilisateurs** .  

![Vue d’ensemble du rapport d’activité utilisateur de gestion des risques internes.](../media/insider-risk-user-activity-report-overview.png)

Pour commencer, sélectionnez **Gérer les rapports** dans la section **Examiner l’activité des utilisateurs** de la page **Vue d’ensemble** de la gestion des risques internes. 

Pour afficher les activités d’un utilisateur, sélectionnez **d’abord Créer un rapport d’activité utilisateur** et renseignez les champs suivants dans le volet **Nouveau rapport d’activité utilisateur** :

- **Utilisateur** : recherchez un utilisateur par nom ou adresse e-mail.
- **Date de début** : utilisez le contrôle calendrier pour sélectionner la date de début des activités de l’utilisateur.
- **Date de fin** : utilisez le contrôle calendrier pour sélectionner la date de fin des activités de l’utilisateur. La date de fin sélectionnée doit être supérieure à deux jours après la date de début sélectionnée et pas plus de 90 jours à partir de la date de début sélectionnée.
 
Les nouveaux rapports prennent généralement jusqu’à 10 heures avant d’être prêts à être examinés. Lorsque le rapport est prêt, le *rapport est prêt* dans la colonne **État** de la page Rapport d’activité utilisateur. Sélectionnez l’utilisateur pour afficher le rapport détaillé :

![Rapport d’activité utilisateur sur la gestion des risques internes](../media/insider-risk-user-activity-report.png)

Le **rapport d’activité de** l’utilisateur pour l’utilisateur sélectionné contient les onglets **Activité de l’utilisateur**, **Explorateur d’activités** et **Preuve d’investigation (préversion)** :

- **Activité de l’utilisateur** : utilisez cette vue de graphique pour examiner les activités potentiellement risquées et afficher les activités potentiellement associées qui se produisent par séquences. Cet onglet est structuré pour permettre une révision rapide d’un cas, y compris une chronologie historique de toutes les activités, les détails de l’activité, le score de risque actuel pour l’utilisateur dans le cas, la séquence d’événements à risque et les contrôles de filtrage pour faciliter les efforts d’investigation.
- **Explorateur d’activités** : cet onglet fournit aux enquêteurs des risques un outil d’analyse complet qui fournit des informations détaillées sur les activités. Avec l’Explorateur d’activités, les réviseurs peuvent rapidement passer en revue une chronologie des activités à risque détectées et identifier et filtrer toutes les activités potentiellement à risque associées aux alertes. Pour en savoir plus sur l’utilisation de l’Explorateur d’activités, consultez la section *Explorateur d’activités* plus loin dans cet article.

## <a name="alert-dashboard"></a>Tableau de bord d’alerte

Les alertes de gestion des risques internes sont générées automatiquement par des indicateurs de risque définis dans les stratégies de gestion des risques internes. Ces alertes donnent aux analystes de conformité et aux enquêteurs une vue d’ensemble de l’état actuel des risques et permettent à votre organisation de trier et de prendre des mesures pour les risques potentiels découverts. Par défaut, les stratégies génèrent un certain nombre d’alertes de gravité faible, moyenne et élevée, mais vous pouvez [augmenter ou diminuer le volume d’alertes](insider-risk-management-settings.md#alert-volume) en fonction de vos besoins. En outre, vous pouvez configurer le [seuil d’alerte pour les indicateurs de stratégie](insider-risk-management-settings.md#indicator-level-settings-preview) lors de la création d’une stratégie avec l’outil de création de stratégie.

Regardez la vidéo Expérience de [triage des alertes de gestion des risques](https://www.youtube.com/watch?v=KgmpxBLJLPI) internes pour obtenir une vue d’ensemble de la façon dont les alertes fournissent des détails, du contexte et du contenu associé pour les activités à risque, et comment rendre votre processus d’investigation plus efficace.

Le **tableau de bord Alerte** de risque interne vous permet d’afficher et d’agir sur les alertes générées par les stratégies de risque interne. Chaque widget de rapport affiche des informations pour les 30 derniers jours.

- **Nombre total d’alertes nécessitant une révision** : le nombre total d’alertes nécessitant une révision et un tri sont répertoriées, y compris une répartition par gravité d’alerte.
- **Alertes ouvertes au cours des 30 derniers jours** : nombre total d’alertes créées par la stratégie correspond au cours des 30 derniers jours, triées par niveau de gravité d’alerte élevé, moyen et faible.
- **Temps moyen de résolution des alertes** : résumé des statistiques d’alerte utiles :
  - Délai moyen de résolution des alertes de gravité élevée, indiqué en heures, jours ou mois.
  - Délai moyen de résolution des alertes de gravité moyenne, indiqué en heures, jours ou mois.
  - Délai moyen de résolution des alertes de faible gravité, indiqué en heures, jours ou mois.

![Tableau de bord des alertes de gestion des risques internes](../media/insider-risk-alerts-dashboard.png)

> [!NOTE]
> La gestion des risques internes utilise la limitation d’alertes intégrée pour vous aider à protéger et optimiser vos examens de risque et réviser l’expérience. Cette limitation protège contre les problèmes susceptibles d’entraîner une surcharge d’alertes de stratégie, telles que des connecteurs de données mal configurés ou des stratégies de protection contre la perte de données. Par conséquent, il peut y avoir un retard dans l'affichage de nouvelles alertes pour un utilisateur.

## <a name="alert-status-and-severity"></a>État de l’alerte et gravité

Vous pouvez trier les alertes dans l’un des états suivants :

- **Confirmé** : alerte confirmée et affectée à un cas nouveau ou existant.
- **Ignoré : alerte ignorée** comme étant sans gravité dans le processus de triage. Vous pouvez fournir une raison pour le rejet de l’alerte et inclure des notes qui sont disponibles dans l’historique des alertes de l’utilisateur afin de fournir un contexte supplémentaire pour une référence ultérieure ou pour d’autres réviseurs. Les raisons peuvent être des activités attendues, des événements sans impact, simplement la réduction du nombre d’activités d’alerte pour l’utilisateur ou une raison liée aux notes d’alerte. Les choix de classification des motifs incluent *l’activité est attendue pour cet utilisateur*, *l’activité est suffisamment percutante pour que j’examine plus en détail* et *les alertes pour cet utilisateur contiennent trop d’activité*.
- **Révision requise** : nouvelle alerte dans laquelle les actions de triage n’ont pas encore été effectuées.
- **Résolu** : alerte qui fait partie d’un cas fermé et résolu.

Les scores de risque d’alerte sont automatiquement calculés à partir de plusieurs indicateurs d’activité à risque. Ces indicateurs incluent le type d’activité à risque, le nombre et la fréquence de l’occurrence de l’activité, l’historique de l’activité à risque des utilisateurs et l’ajout de risques d’activité susceptibles d’accroître la gravité de l’activité potentiellement à risque. Le score de risque d’alerte détermine l’attribution par programme d’un niveau de gravité de risque pour chaque alerte et ne peut pas être personnalisé. Si les alertes restent nontriées et que les activités à risque continuent de s’accumuler dans l’alerte, le niveau de gravité du risque peut augmenter. Les analystes des risques et les enquêteurs peuvent utiliser la gravité des risques d’alerte pour aider à trier les alertes conformément aux stratégies et normes de risque de votre organisation.

Les niveaux de gravité des risques d’alerte sont les suivants :

- **Gravité élevée** : les activités et indicateurs potentiellement à risque de l’alerte posent un risque significatif. Les activités à risque associées sont graves, répétitives et étroitement liées à d’autres facteurs de risque importants.
- **Gravité moyenne** : les activités potentiellement risquées et les indicateurs de l’alerte posent un risque modéré. Les activités de risque associées sont modérées, fréquentes et présentent une corrélation avec d’autres facteurs de risque.
- **Gravité faible** : les activités potentiellement risquées et les indicateurs de l’alerte posent un risque mineur. Les activités à risque associées sont mineures, plus peu fréquentes et ne sont pas associées à d’autres facteurs de risque importants.

## <a name="filter-alerts-on-the-alert-dashboard"></a>Filtrer les alertes dans le tableau de bord Alerte

Selon le nombre et le type de stratégies de gestion des risques internes actif au sein de votre organisation, il peut être difficile de réviser une grande file d’alertes. L’utilisation de filtres d’alerte peut aider les analystes et les enquêteurs à trier les alertes selon plusieurs attributs. 

Pour filtrer les alertes dans le **tableau de bord Alertes**, sélectionnez le contrôle **Filtrer** . Vous pouvez filtrer les alertes par un ou plusieurs attributs :

- **État** : sélectionnez une ou plusieurs valeurs d’état pour filtrer la liste des alertes. Les options sont *Confirmé*, *Fermé*, *Révision requise* et *Résolu*.
- **Gravité** : sélectionnez un ou plusieurs niveaux de gravité de risque d’alerte pour filtrer la liste des alertes Les options sont *Élevé*, *Moyen* et *Faible*.
- **Heure détectée** : sélectionnez les dates de début et de fin de la création de l’alerte. Ce filtre recherche les alertes entre UTC 00:00 à la date de début et UTC 00:00 à la date de fin. Pour filtrer les alertes d’un jour spécifique, entrez la date du jour dans le champ **Date de début** et la date du jour suivant dans le champ **Date de fin** .
- **Stratégie** : sélectionnez une ou plusieurs stratégies pour filtrer les alertes générées par les stratégies sélectionnées.
- **Facteurs de risque** : sélectionnez l’un des autres facteurs de risque pour filtrer la liste des alertes. Les options sont *Activités d’exfiltration cumulatives*, *Activités incluent le contenu prioritaire*, *Activités de séquence* et *Activités incluent des domaines non autorisés*.

## <a name="search-alerts-on-the-alert-dashboard"></a>Rechercher des alertes dans le tableau de bord Alerte

Pour rechercher le nom d’une alerte pour un mot spécifique, sélectionnez la commande **Recherche** et tapez le mot à rechercher. Les résultats de la recherche affichent une alerte de stratégie contenant le mot défini dans la recherche.

## <a name="dismiss-multiple-alerts-preview"></a>Ignorer plusieurs alertes (préversion)

Cela peut permettre aux analystes et aux enquêteurs d’ignorer immédiatement plusieurs alertes à la fois. L’option Ignorer la barre **de commandes des alertes** vous permet de sélectionner une ou plusieurs alertes avec l’état *Besoin de révision* dans le tableau de bord et d’ignorer rapidement ces alertes comme étant sans gravité, le cas échéant, dans votre processus de triage. Vous pouvez sélectionner jusqu’à 400 alertes à ignorer simultanément.

Pour ignorer une alerte de risque interne, procédez comme suit :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Alertes**.
2. Dans le **tableau de bord Alertes**, sélectionnez l’alerte (ou les alertes) dont l’état *De révision nécessite* que vous souhaitez ignorer.
3. Dans la barre de commandes Alertes, sélectionnez **Ignorer les alertes**.
4. Dans le volet **de détails Ignorer les alertes** , vous pouvez passer en revue les détails de l’utilisateur et de la stratégie associés aux alertes sélectionnées.
5. Sélectionnez **Ignorer les alertes** pour résoudre les alertes comme étant sans gravité ou sélectionnez **Annuler** pour fermer le volet d’informations sans ignorer les alertes.

## <a name="triage-alerts"></a>Triage des alertes

Pour trier une alerte de risque interne, procédez comme suit :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Alertes**.
2. Dans le **tableau de bord Alertes**, sélectionnez l’alerte que vous souhaitez trier.
3. Dans la page **détails de l’alerte** , vous pouvez consulter les informations relatives à l’alerte. Vous pouvez confirmer l’alerte et créer un cas, confirmer l’alerte et l’ajouter à un cas existant, ou ignorer l’alerte. Cette page inclut également l’état actuel de l’alerte et le niveau de gravité de risque de l’alerte, répertorié comme Élevé, Moyen ou Faible. Le niveau de gravité peut augmenter ou diminuer au fil du temps si l’alerte n’est pas triée.

Pour plus d’informations sur l’alerte, utilisez les sections et onglets suivants sur la page de détails de l’alerte :

### <a name="headersummary-section"></a>Section En-tête/Résumé

Cette section contient des informations générales sur l’utilisateur et l’alerte. Ces informations sont disponibles pour le contexte lors de l’examen d’informations détaillées sur l’activité de gestion des risques détectée incluse dans l’alerte pour l’utilisateur :

- **Activité qui a généré cette alerte** : affiche l’activité potentiellement risquée et la correspondance de stratégie la plus haute pendant la période d’évaluation de l’activité qui a conduit à la génération de l’alerte.
- **Événement déclencheur** : affiche l’événement déclencheur le plus récent qui a invité la stratégie à commencer à attribuer des scores de risque à l’activité de l’utilisateur. Si vous avez configuré [l’intégration avec la conformité des communications](/microsoft-365/compliance/communication-compliance-policies#integration-with-insider-risk-management-preview) pour *les fuites de données par des utilisateurs mécontents ou les* violations de stratégie de *sécurité par des stratégies d’utilisateurs mécontents* , l’événement de déclenchement de ces alertes sera limité à l’activité de conformité des communications.
- **Profil utilisateur** : affiche des informations générales sur l’utilisateur affecté à l’alerte. Si l’anonymisation est activée, le nom d’utilisateur, l’adresse e-mail, l’alias et les champs d’organisation sont rendus anonymes.
- **Historique des alertes utilisateur** : affiche une liste d’alertes pour l’utilisateur au cours des 30 derniers jours. Inclut un lien permettant d’afficher l’historique complet des alertes de l’utilisateur.

Les alertes générées à partir de stratégies limitées aux seules activités qui incluent du [contenu prioritaire](/microsoft-365/compliance/insider-risk-management-policies#prioritize-content-in-policies) incluent l’option *Seule l’activité avec du contenu prioritaire a été notée pour cette notification d’alerte* dans cette section.

### <a name="all-risk-factors"></a>Tous les facteurs de risque

Cet onglet ouvre le résumé des facteurs de risque pour l’activité d’alerte de l’utilisateur. Les facteurs de risque peuvent vous aider à déterminer à quel point l’activité de gestion des risques de cet utilisateur est risquée pendant votre révision. Les facteurs de risque incluent des résumés pour :

- **Principales activités d’exfiltration** : affiche les activités d’exfiltration avec le nombre ou les événements les plus élevés pour l’alerte.
- **Activités d’exfiltration cumulatives** : affiche les événements associés aux activités d’exfiltration cumulatives.
- **Séquences d’activités** : affiche les activités potentiellement risquées détectées associées aux séquences de risques.
- **Activité inhabituelle pour cet utilisateur** : affiche des activités spécifiques pour l’utilisateur qui sont considérées comme potentiellement risquées, car elles sont inhabituelles et en rupture avec leurs activités typiques.
- **Contenu prioritaire** : affiche les activités potentiellement risquées associées au contenu prioritaire.
- **Domaines non autorisés** : affiche les activités potentiellement risquées pour les événements associés à des domaines non autorisés.
- **Accès aux enregistrements d’intégrité** : affiche les activités potentiellement risquées pour les événements associés à l’accès aux enregistrements d’intégrité.
- **Utilisation risquée du navigateur** : affiche les activités potentiellement risquées pour les événements associés à la navigation vers des sites web potentiellement inappropriés.

Avec ces filtres, vous verrez uniquement les alertes avec les facteurs de risque ci-dessus, mais l’activité qui a généré une alerte peut ne pas appartenir à l’une de ces catégories. Par exemple, une alerte contenant des activités de séquence peut avoir été générée simplement parce que l’utilisateur a copié un fichier sur un périphérique USB.

### <a name="content-detected"></a>Contenu détecté

La section de l’onglet **Tous les facteurs de risque** inclut le contenu associé aux activités à risque pour l’alerte et résume les événements d’activité par domaines clés. La sélection d’un lien d’activité ouvre l’Explorateur d’activités et affiche plus de détails sur l’activité.

### <a name="activity-explorer"></a>Explorateur d’activités

Cet onglet ouvre l’Explorateur d’activités. Pour plus d’informations, consultez la section Explorateur d’activités de cet article.

### <a name="user-activity"></a>Activité utilisateur

Le graphique **d’activité utilisateur** est l’un des outils les plus puissants pour l’analyse des risques internes et l’investigation des alertes et des cas dans la solution de gestion des risques internes. Cet onglet est structuré pour permettre une révision rapide de toutes les activités d’un utilisateur, y compris une chronologie historique de toutes les alertes, les détails de l’alerte, le score de risque actuel pour l’utilisateur et la séquence d’événements à risque.

![Activité des utilisateurs de gestion des risques internes](../media/insider-risk-user-activities.png)

1. **Filtres de temps** : par défaut, les trois derniers mois d’activités potentiellement risquées s’affichent dans le graphique d’activités de l’utilisateur. Vous pouvez facilement filtrer l’affichage graphique en sélectionnant les onglets *6 mois*, *3 mois* ou *1 mois* sur le graphique en bulles.
2. **Activité d’alerte à risque et détails** : les activités potentiellement risquées sont visuellement affichées sous forme de bulles colorées dans le graphique d’activité de l’utilisateur. Des bulles sont créées pour différentes catégories de risques et. Sélectionnez une bulle pour afficher les détails de chaque activité potentiellement risquée. Les détails sont les suivants :
    - **Date** de l’activité de risque.
    - Catégorie **d’activité à risque**. Par exemple, *Email avec des pièces jointes envoyées en dehors de l’organisation* ou des *fichiers téléchargés à partir de SharePoint Online*.
    - **Score de risque** pour l’alerte. Ce score correspond au score numérique du niveau de gravité des risques d’alerte.
    - Nombre d’événements associés à l’alerte. Des liens vers chaque fichier ou e-mail associé à l’activité à risque sont également disponibles.
3. **Filtres et tri (préversion)** :
    - **Catégorie de** risque : Filtrez les activités selon les catégories de risque suivantes : *Activités avec des scores de risque > 15 (sauf dans une séquence)* et *Activités de séquence*.
    - **Type d’activité** : Filtrez les activités selon les types suivants : *Accès*, *Suppression*, *Collection*, *Exfiltration*, *Infiltration*, *Obfuscation* et *Sécurité*.
    - **Trier par** : répertoriez la chronologie des activités potentiellement *risquées par Date de survenue* ou *Score de risque*.
4. **Séquence de risques** : l’ordre chronologique des activités potentiellement risquées est un aspect important de l’examen des risques et l’identification de ces activités associées est une partie importante de l’évaluation du risque global pour votre organisation. Les activités d’alerte associées sont affichées avec des lignes de connexion pour mettre en évidence que ces activités sont associées à une zone de risque plus grande. Les séquences sont également identifiées dans cette vue par une icône positionnée au-dessus des activités de séquence par rapport au score de risque pour la séquence. Pointez sur l’icône pour voir la date et l’heure de l’activité à risque associée à cette séquence. Cette vue des activités peut aider les enquêteurs littéralement à « connecter les points » pour les activités à risque qui auraient pu être vues comme des événements isolés ou ponctuels. Sélectionnez l’icône ou une bulle dans la séquence pour afficher les détails de toutes les activités à risque associées. Les détails sont les suivants :

    - **Nom** de la séquence.
    - **Date** ou **Plage de dates** de la séquence.
    - **Score de risque** pour la séquence. Ce score est le score numérique de la séquence des niveaux de gravité de risque d’alerte combinés pour chaque activité associée dans la séquence.
    - **Nombre d’événements associés à chaque alerte dans la séquence**. Des liens vers chaque fichier ou e-mail associé à chaque activité potentiellement à risque sont également disponibles.
    - **Afficher les activités dans l’ordre**. Affiche la séquence sous la forme d’une ligne de mise en surbrillance sur le graphique en bulles et développe les détails de l’alerte pour afficher toutes les alertes associées dans la séquence.

5. **Légende de l’activité à risque** : en bas du graphique d’activité utilisateur, une légende codée en couleur vous permet de déterminer rapidement la catégorie de risque pour chaque alerte.
6. **Chronologie des activités à risque** : la chronologie complète de toutes les alertes à risque associées au cas est répertoriée, y compris tous les détails disponibles dans la bulle d’alerte correspondante.
7. **Actions de** cas : les options de résolution du cas se trouvent dans la barre d’outils d’action de cas. Lors de l’affichage dans un cas, vous pouvez résoudre un cas, envoyer une notification par e-mail à l’utilisateur ou remonter le cas pour une enquête sur les données ou l’utilisateur.

## <a name="activity-explorer"></a>Explorateur d’activités

> [!NOTE]
> L’Explorateur d’activités est disponible dans la zone de gestion des alertes pour les utilisateurs ayant déclenché des événements une fois cette fonctionnalité disponible dans votre organisation.

L’Explorateur d’activités fournit aux enquêteurs et aux analystes des risques un outil d’analyse complet qui fournit des informations détaillées sur les alertes. Avec l’Explorateur d’activités, les réviseurs peuvent rapidement passer en revue une chronologie des activités potentiellement à risque détectées et identifier et filtrer toutes les activités à risque associées aux alertes. 

Pour filtrer les alertes sur l’Explorateur d’activités pour les informations de colonne, sélectionnez le contrôle Filtrer. Vous pouvez filtrer les alertes par un ou plusieurs attributs répertoriés dans le volet d’informations de l’alerte. L’Explorateur d’activités prend également en charge les colonnes personnalisables pour aider les enquêteurs et les analystes à concentrer le tableau de bord sur les informations les plus importantes pour eux.

Utilisez les *filtres Étendue de* l’activité et *Informations sur les risques* pour afficher et trier les activités et les insights pour les zones suivantes.

- **Filtres d’étendue d’activité** : filtre toutes les activités notées pour l’utilisateur.
  - Toutes les activités notées pour cet utilisateur
  - Activité notée uniquement dans cette alerte

- **Filtres de facteurs** de risque : filtres pour l’activité des facteurs de risque applicables à toutes les stratégies affectant des scores de risque Cela inclut toutes les activités de toutes les stratégies pour les utilisateurs dans l’étendue.
  - Activité inhabituelle
  - Inclut des événements avec du contenu prioritaire
  - Inclut des événements avec un domaine non autorisé
  - Activités de séquence
  - Activités d’exfiltration cumulatives
  - Activités d’accès aux enregistrements d’intégrité
  - Utilisation risquée du navigateur

![Vue d’ensemble de l’explorateur d’activités de gestion des risques internes](../media/insider-risk-activity-explorer.png)

Pour utiliser **l’Explorateur d’activités**, procédez comme suit :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Alertes**.
2. Dans le **tableau de bord Alertes**, sélectionnez l’alerte que vous souhaitez trier.
3. Dans le **volet de détails Alertes**, sélectionnez **Ouvrir la vue développée**.
4. Dans la page de l’alerte sélectionnée, sélectionnez l’onglet **Explorateur d’activités** .

Lors de l’examen des activités dans l’Explorateur d’activités, les enquêteurs et les analystes peuvent sélectionner une activité spécifique et ouvrir le volet détails de l’activité. Le volet affiche des informations détaillées sur l’activité que les enquêteurs et les analystes peuvent utiliser pendant le processus de triage des alertes. Des informations détaillées peuvent fournir un contexte pour l’alerte et aider à identifier l’étendue complète de l’activité à risque qui a déclenché l’alerte.

Lorsque vous sélectionnez les événements d’une activité dans la chronologie d’activité, le nombre d’activités affichées dans l’explorateur peut ne pas correspondre au nombre d’événements d’activité répertoriés dans la chronologie. Voici quelques exemples de raisons pour lesquelles cette différence peut se produire :

- **Détection d’exfiltration cumulative** : la détection d’exfiltration cumulative analyse les journaux des événements, mais applique un modèle qui inclut la dédoublement d’activités similaires pour calculer le risque d’exfiltration cumulé. En outre, il peut également y avoir une différence dans le nombre d’activités potentiellement risquées affichées dans l’Explorateur d’activités si vous avez apporté des modifications à votre stratégie ou à vos paramètres existants. Par exemple, si vous modifiez des domaines autorisés/non autorisés ou ajoutez de nouvelles exclusions de type de fichier après la création d’une stratégie et que des correspondances d’activité potentiellement à risque se sont produites, les activités de détection d’exfiltration cumulatives diffèrent des résultats avant que la stratégie ou les paramètres ne changent. Les totaux des activités de détection d’exfiltration cumulative sont basés sur la configuration de la stratégie et des paramètres au moment du calcul et n’incluent pas les activités avant les modifications de la stratégie et des paramètres
- **E-mails aux destinataires externes** : une activité potentiellement risquée pour les e-mails envoyés à des destinataires externes se voit attribuer un score de risque basé sur le nombre d’e-mails envoyés, qui peut ne pas correspondre aux journaux des événements d’activité.

![Détails de l’explorateur d’activités de gestion des risques internes.](../media/insider-risk-activity-explorer-details.png)

## <a name="create-a-case-for-an-alert"></a>Créer un cas pour une alerte

À mesure que l’alerte est examinée et triée, vous pouvez créer un cas pour examiner plus en détail l’activité potentiellement risquée. Pour créer un cas pour une alerte, procédez comme suit :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Alertes**.
2. Dans le **tableau de bord Alertes**, sélectionnez l’alerte pour laquelle vous souhaitez confirmer et créez un cas.
3. Dans le **volet Détails des alertes**, sélectionnez **Actions** > **Confirmer les alertes & créer un cas**.
4. Dans la boîte de **dialogue Confirmer l’alerte et créer un cas de risque interne** , entrez un nom pour le cas, sélectionnez les utilisateurs à ajouter en tant que contributeurs et ajoutez des commentaires le cas échéant. Les commentaires sont automatiquement ajoutés au cas en tant que note de cas.
5. Sélectionnez **Créer un cas** pour créer un cas ou **annuler** pour fermer la boîte de dialogue sans créer de cas.

Une fois le cas créé, les enquêteurs et les analystes peuvent gérer et agir sur le cas. Pour plus d’informations, consultez l’article [Cas de gestion des risques internes](insider-risk-management-cases.md) .

## <a name="retention-and-item-limits"></a>Limites de rétention et d’élément

À mesure que les alertes de gestion des risques internes vieillissent, leur valeur pour réduire les activités potentiellement risquées diminue pour la plupart des organisations. À l’inverse, les cas actifs et les artefacts associés (alertes, insights, activités) sont toujours précieux pour les organisations et ne doivent pas avoir de date d’expiration automatique. Cela inclut toutes les alertes et artefacts futurs dans un état actif pour tout utilisateur associé à un cas actif.

Pour réduire le nombre d’éléments plus anciens qui fournissent une valeur actuelle limitée, la rétention et les limites suivantes s’appliquent aux alertes, cas et rapports utilisateur de gestion des risques internes :

|**Élément**|**Rétention/limite**|
|:-------|:------------------|
|Alertes avec l’état de révision Des besoins|120 jours après la création de l’alerte, puis automatiquement supprimée|
|Cas actifs (et artefacts associés)|Rétention indéfinie, n’expire jamais|
|Cas résolus (et artefacts associés)|120 jours à partir de la résolution du cas, puis supprimé automatiquement|
|Nombre maximal de cas actifs|100|
|Rapports d’activités utilisateur|120 jours après la détection d’activité, puis automatiquement supprimé|

## <a name="get-help-managing-your-insider-risk-alert-queue"></a>Obtenir de l’aide sur la gestion de votre file d’attente d’alerte de risque interne

L’examen, l’examen et l’action sur les alertes internes potentiellement risquées sont des éléments importants de la réduction des risques internes dans votre organisation. Prendre rapidement des mesures pour réduire l’impact de ces risques peut potentiellement faire gagner du temps, de l’argent et des conséquences réglementaires ou juridiques pour votre organisation. Dans ce processus de correction, la première étape de l’examen des alertes peut sembler la tâche la plus difficile pour de nombreux analystes et enquêteurs. Selon vos circonstances, vous pouvez rencontrer des obstacles mineurs lorsque vous agissez sur des alertes internes potentiellement risquées. Passez en revue les recommandations suivantes et découvrez comment optimiser le processus de révision des alertes.

### <a name="too-many-alerts-to-review"></a>Trop d’alertes à examiner

Être submergé par le nombre d’alertes produites par vos stratégies de gestion des risques internes peut être frustrant. Le nombre d’alertes peut être traité rapidement par des étapes simples, en fonction des types de volume d’alertes que vous recevez. Vous recevez peut-être trop d’alertes valides ou trop d’alertes obsolètes à faible risque. Envisagez d’effectuer les actions suivantes :

- **Ajuster vos stratégies de risque interne** : la sélection et la configuration de la stratégie de risque interne appropriée est la méthode la plus simple pour traiter le type et le volume des alertes. Le fait de commencer par le [modèle de stratégie](insider-risk-management-policies.md#policy-templates) approprié permet de concentrer les types d’activités à risque et d’alertes que vous verrez. Les autres facteurs susceptibles d’avoir un impact sur le volume des alertes sont la taille de l’utilisateur et des groupes dans l’étendue, ainsi que le contenu et [les canaux qui sont hiérarchisés](insider-risk-management-policies.md#prioritize-content-in-policies). Envisagez d’ajuster les stratégies pour affiner ces domaines en fonction de ce qui est le plus important pour votre organisation.
- **Modifiez vos paramètres de risque interne** : les paramètres de risque interne incluent un large éventail d’options de configuration qui peuvent avoir un impact sur le volume et les types d’alertes que vous recevrez. Il s’agit notamment des paramètres pour les [indicateurs de stratégie](insider-risk-management-settings.md#indicators), [les seuils d’indicateur](insider-risk-management-settings.md#indicator-level-settings-preview) et [les délais de stratégie](insider-risk-management-settings.md#policy-timeframes). Envisagez de configurer des options de [détection intelligente pour](insider-risk-management-settings.md#intelligent-detections) exclure des types de fichiers et des types d’informations sensibles spécifiques, définir des seuils minimaux avant que les alertes d’activité ne soient signalées par vos stratégies et modifier la configuration du volume d’alerte par un paramètre inférieur.
- **Activer la personnalisation des alertes inline (préversion)** : l’activation de la [personnalisation des alertes inline](/microsoft-365/compliance/insider-risk-management-settings#inline-alert-customization-preview) permet aux analystes et aux enquêteurs de modifier rapidement les stratégies lors de l’examen des alertes. Ils peuvent mettre à jour les seuils de détection d’activité avec les recommandations de Microsoft, configurer des seuils personnalisés ou choisir d’ignorer le type d’activité qui a créé l’alerte. Si cette option n’est pas activée, seuls les utilisateurs affectés au groupe *de rôles Gestion des risques internes* peuvent utiliser la personnalisation des alertes inline.
- **Suppression en bloc des alertes le cas échéant** : cela peut vous aider à gagner du temps de tri pour que vos analystes et enquêteurs [ignorent immédiatement plusieurs alertes](insider-risk-management-activities.md#dismiss-multiple-alerts-preview) à la fois. Vous pouvez sélectionner jusqu’à 400 alertes à ignorer simultanément.

### <a name="not-familiar-with-the-alert-triage-process"></a>Pas familiarisé avec le processus de triage des alertes

L’examen et l’action des alertes dans la gestion des risques internes sont simples :

1. **Passez en [revue le tableau de bord d’alerte](insider-risk-management-activities.md#alert-dashboard) pour les alertes avec l’état Révision des besoins**. [Filtrez](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) par *état* d’alerte si nécessaire pour vous aider à localiser ces types d’alertes.
2. **Commencez par les alertes avec la gravité la plus élevée**. [Filtrez](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) par *gravité* d’alerte si nécessaire pour vous aider à localiser ces types d’alertes.
3. **Sélectionnez une alerte pour découvrir plus d’informations et passer en revue les détails de l’alerte**. Si nécessaire, utilisez [l’Explorateur](insider-risk-management-activities.md#activity-explorer) d’activités pour passer en revue une chronologie du comportement potentiellement risqué associé et identifier toutes les activités à risque pour l’alerte.
4. **Agir sur l’alerte**. Vous pouvez confirmer et [créer un cas](insider-risk-management-activities.md#create-a-case-for-an-alert) pour l’alerte ou ignorer et résoudre l’alerte.

### <a name="resource-constraints-in-my-organization"></a>Contraintes de ressources dans mon organisation

Les utilisateurs de l’espace de travail moderne ont souvent une grande variété de responsabilités et de demandes sur leur temps. Vous pouvez effectuer plusieurs actions pour résoudre les contraintes de ressources :

- **Concentrez d’abord les efforts de l’analyste et de l’enquêteur sur les alertes à risque le plus élevé**. Selon vos stratégies, vous pouvez capturer les activités des utilisateurs et générer des alertes avec différents degrés d’impact potentiel sur vos efforts d’atténuation des risques. [Filtrez les alertes](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) par gravité et hiérarchisez les alertes *de gravité élevée* .
- **Affecter des utilisateurs en tant qu’analystes et enquêteurs**. Le fait que l’utilisateur approprié soit affecté aux rôles appropriés est une partie importante du processus de révision des alertes de risque interne. Vérifiez que vous avez affecté les utilisateurs appropriés aux groupes de rôles *Analystes de gestion des risques internes et Enquêteurs* en *gestion des risques internes* .  
- **Utilisez les fonctionnalités automatisées de risque interne pour vous aider à découvrir les activités à risque le plus élevé**. La détection des [séquences](insider-risk-management-policies.md#sequence-detection-preview) de gestion des risques internes et les fonctionnalités [de détection cumulative de l’exfiltration](insider-risk-management-policies.md#cumulative-exfiltration-detection-preview) peuvent vous aider à détecter rapidement les risques plus difficiles dans votre organisation. Envisagez de peaufiner vos [boosters de score de risque](insider-risk-management-settings.md#indicators), [la détection de l’activité](insider-risk-management-settings.md#file-activity-detection) des fichiers, les [domaines](insider-risk-management-settings.md#domains) et [les paramètres de seuil d’indicateur](insider-risk-management-settings.md#indicator-level-settings-preview) minimal pour vos stratégies.
