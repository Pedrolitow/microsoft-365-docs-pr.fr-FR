---
title: Personnaliser le score de conformité Microsoft avec les évaluations
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Concevez la personnalisation du score de conformité Microsoft en créant des évaluations pour vous aider à gérer la conformité de votre organisation.
ms.openlocfilehash: 8b27267461e226a6db2173158d2d35238c0d5a5e
ms.sourcegitcommit: 8595cb9ffe0ca5556080f24224182381e1d880de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "45035629"
---
# <a name="customize-compliance-score-preview-with-assessments"></a>Personnaliser le score de conformité (aperçu) avec les évaluations

**Dans cet article :** Découvrez comment personnaliser le score de conformité en paramétrant les **évaluations**prêtes à l’emploi. Découvrez comment modifier le **modèle** pour une évaluation et créer vos propres évaluations personnalisées pour répondre aux besoins de votre organisation. Cet article explique également comment organiser les évaluations en **groupes**, utiliser des **contrôles**et exporter des **rapports**d’évaluation.

## <a name="introduction-to-assessments"></a>Introduction aux évaluations

Le score de conformité vous aide à gérer la conformité avec les évaluations des règlements et des certifications qui s’appliquent à votre organisation. Les évaluations sont des regroupements de contrôles à partir d’un règlement, d’une norme ou d’une stratégie spécifique. Le score de conformité facilite le suivi de votre conformité grâce à des évaluations prêtes à l’emploi qui couvrent une variété de réglementations et de certifications régionales et régionales.

Chaque évaluation est créée à partir d’un modèle, qui sert d’infrastructure contenant les contrôles et les actions d’amélioration nécessaires à l’exécution de l’évaluation. La configuration des évaluations les plus pertinentes pour votre organisation permet de s’assurer que vous mettez en œuvre des stratégies et des procédures opérationnelles qui peuvent limiter votre risque de conformité.

Toutes vos évaluations sont répertoriées sur la page évaluations. [En savoir plus](compliance-score-setup.md#assessments-page) sur la façon de filtrer votre vue de vos évaluations et d’interpréter les États d’État.

## <a name="data-protection-baseline-default-assessment"></a>Évaluation par défaut de la base de données de protection des données

Pour vous aider, Microsoft fournit une évaluation **par défaut** dans le score de conformité qui contient la base de données de protection des données Microsoft 365. Cette configuration de référence est un ensemble de contrôles qui inclut des normes et des réglementations clés pour la protection des données et la gouvernance générale des données. Cette ligne de base présente principalement des éléments d’Institut CSF (Institut national de normes et technologie Cybersecurity Framework) et ISO (Organisation internationale de normalisation), ainsi que de FedRAMP (Federal Risk and Authorization Management Program) et RGPD (règlement général sur la protection des données de l’Union européenne).

Cette évaluation est utilisée pour calculer votre score initial la première fois que vous êtes le score de conformité, avant de configurer d’autres évaluations. Le score de conformité collecte les signaux initiaux de vos solutions Microsoft 365. Vous verrez en un clin d’œil comment votre organisation est en fonction des normes et des réglementations clés en matière de protection des données, et découvrez les actions d’amélioration suggérées à entreprendre.

Étant donné que chaque organisation a des besoins spécifiques, le score de conformité repose sur la configuration et la gestion de vos propres évaluations afin de réduire et réduire le risque le plus complet possible.

## <a name="assessment-creation-overview"></a>Vue d’ensemble de la création d’évaluation

Vous pouvez configurer les évaluations de trois façons :

1. Choisissez une évaluation prête à utiliser.
2. Modifier le [modèle d’une évaluation](compliance-score-templates.md) en fonction de vos besoins.
3. Créez votre propre évaluation personnalisée.

Les utilisateurs doivent être titulaires d’un rôle d’administrateur général, d’administrateur de conformité, d’administrateur de données de conformité ou d’administrateur de sécurité afin de créer ou de modifier des évaluations. En savoir plus sur [les rôles et les autorisations](compliance-score-setup.md#set-user-permissions-and-assign-roles).

> [!NOTE]
> Toutes les évaluations créées ou modifiées dans le score de conformité seront également reflétées dans le gestionnaire de conformité. En savoir plus sur la [relation entre le score de conformité et le gestionnaire de conformité](compliance-score.md#relationship-to-compliance-manager).

### <a name="ready-to-use-assessments"></a>Prêt à utiliser les évaluations

Lancer votre parcours de conformité en choisissant parmi les [modèles](compliance-score-templates.md) de la sélection du score de conformité pour la création d’évaluations. Les modèles contiennent les contrôles et les actions d’amélioration nécessaires pour chaque évaluation particulière. Modèles du score de conformité les règlements et les certifications s’alignent sur des secteurs, des régions et des normes de protection des données courantes, telles que RGPD et ISO 27001.

**Pour configurer une évaluation**, choisissez l’un des modèles lorsque vous commencez [à générer l’évaluation à partir de l’Assistant](#create-an-assessment).

### <a name="modify-the-template-of-an-assessment"></a>Modifier le modèle d’une évaluation

Vous pouvez modifier les modèles de score de conformité pour les évaluations afin de mieux répondre aux besoins de votre organisation. Par exemple, si vous avez généralement besoin de vous conformer à HIPAA mais que vous avez besoin de contrôles de sécurité ou de protection des données supplémentaires, vous pouvez utiliser notre modèle HIPAA et ajouter vos propres champs personnalisés pour créer une nouvelle évaluation qui surveille votre progression de la manière dont vous avez besoin. Lors de la préversion publique, vous devez accéder au gestionnaire de conformité pour modifier les modèles.

**Pour modifier le modèle d’une évaluation**, suivez les instructions ci-dessous :

1. Affichez la liste des [modèles](compliance-score-templates.md) disponibles dans score de conformité pour déterminer celle que vous souhaitez modifier.
2. Consultez les [instructions du gestionnaire de conformité pour personnaliser un modèle à l’aide du processus d’extension](working-with-compliance-manager.md#customize-a-template-through-the-extension-process).
3. Une fois que vous avez créé votre modèle et que vous l’avez importé dans le gestionnaire de conformité, vous pouvez créer votre nouvelle évaluation dans le score de conformité. Suivez le processus de création de votre évaluation à l’aide de l' [Assistant de création d’évaluation](#create-an-assessment).

> [!NOTE]
> En savoir plus sur la [relation entre le score de conformité et le gestionnaire de conformité lors de](compliance-score.md#relationship-to-compliance-manager) la préversion publique.

### <a name="create-your-own-custom-assessment"></a>Créer votre propre évaluation personnalisée

Vous pouvez créer votre propre évaluation entièrement à partir de rien pour suivre précisément les besoins de votre organisation. Comme avec le processus de modification décrit ci-dessus, la création de votre propre évaluation exige que vous créez d’abord votre propre modèle pour l’évaluation dans le gestionnaire de conformité.

**Pour créer votre propre évaluation personnalisée**, suivez les instructions suivantes :

1. Découvrez comment [créer votre propre modèle dans le gestionnaire de conformité](working-with-compliance-manager.md#create-your-own-template-and-import-it-into-compliance-manager).
2. Une fois que vous avez créé votre modèle et que vous l’avez importé dans le gestionnaire de conformité, vous pouvez créer votre nouvelle évaluation dans le score de conformité. Suivez le processus de création de votre évaluation à l’aide de l' [Assistant de création d’évaluation](#create-an-assessment).

## <a name="understand-groups-before-creating-assessments"></a>Comprendre les groupes avant de créer des évaluations

Avant de créer ou de modifier des évaluations, il est important de comprendre le fonctionnement des groupes. Lorsque vous créez une évaluation, vous devez l’affecter à un groupe pendant ce processus. Nous vous recommandons donc de planifier une stratégie de regroupement pour vos évaluations avant de créer des évaluations.

### <a name="what-are-groups"></a>Qu’est-ce qu’un groupe

Les groupes sont des conteneurs qui vous permettent d’organiser des évaluations. Vous pouvez regrouper les évaluations de manière logique, par année ou par réglementation, ou en fonction des divisions ou des régions de votre organisation. Vous trouverez ci-dessous des exemples de deux groupes et de leurs évaluations sous-jacentes :

- **FFIEC est une évaluation 2020**
  - Office 365 + FFIEC est
  - Intune + FFIEC est
- **Évaluation de la sécurité et de la confidentialité des données**
  - Office 365 + ISO 27001:2013
  - Office 365 + ISO 27018:2014

Lorsque deux évaluations différentes dans le même groupe partagent des actions d’amélioration gérées par vous-même, toutes les mises à jour apportées aux détails de l’implémentation ou à l’état d’une action sont automatiquement synchronisées avec la même action dans toute autre évaluation du groupe. Cette synchronisation vous permet d’implémenter une action d’amélioration et de répondre à plusieurs exigences dans plusieurs réglementations.

### <a name="how-to-create-a-group"></a>Procédure de création d’un groupe

Vous créez un groupe au cours du processus de [création d’une nouvelle évaluation](#create-an-assessment).

Les groupes ne peuvent pas être créés en tant qu’entités autonomes ; un groupe doit contenir au moins une évaluation. Pour créer un groupe, vous devez d’abord créer une évaluation à placer dans le groupe.

### <a name="what-to-know-when-working-with-groups"></a>Éléments à connaître lors de l’utilisation de groupes

- Les noms de groupe doivent être uniques au sein de votre organisation.
- Les groupes n’ont pas de propriétés de sécurité. Toutes les autorisations sont associées à des évaluations.
- Une fois que vous avez ajouté une évaluation à un groupe, le regroupement ne peut pas être modifié.
- Les contrôles d’évaluation associés dans différentes évaluations au sein du même groupe sont automatiquement mis à jour lorsque vous avez terminé.
- Si vous ajoutez une nouvelle évaluation à un groupe existant, les informations courantes des évaluations de ce groupe sont copiées dans la nouvelle évaluation.
- Les groupes peuvent contenir des évaluations pour la même certification ou la même réglementation, mais chaque groupe ne peut contenir qu’une seule évaluation pour une paire de certification de produit spécifique. Par exemple, un groupe ne peut pas contenir deux évaluations pour Office 365 et l’infrastructure NIST. Un groupe peut contenir plusieurs évaluations pour le même produit uniquement si la certification ou la réglementation correspondante est différente.
- La suppression d’une évaluation rompt la relation entre cette évaluation et le groupe.
- Les groupes ne peuvent pas être supprimés.
- Lorsqu’une modification est apportée à une amélioration qui apparaît dans plusieurs groupes, cette modification est reflétée dans toutes les instances de cette action d’amélioration.

## <a name="create-an-assessment"></a>Créer une évaluation

Pour créer une évaluation dans le score de conformité, suivez les étapes ci-dessous :

1. Dans la page évaluations, sélectionnez **Ajouter une évaluation**. Un assistant d’évaluation apparaît dans un grand volet flyout.

2. **Sélectionnez un modèle :** Choisissez un modèle qui servira de base à votre évaluation. Vous pouvez choisir un modèle prêt à utiliser ou un modèle que vous avez modifié ou créé. Sélectionnez la case d’option en regard du modèle choisi, puis sélectionnez **suivant**.

> [!NOTE]
> Consultez [les instructions relatives à la création et à la modification des modèles](working-with-compliance-manager.md#templates), un processus géré dans le gestionnaire de conformité.

3. **Nom et groupe :** Entrez un nom pour votre évaluation dans le champ nom de l' **évaluation** . Les noms d’évaluation doivent être uniques au sein des groupes. Si le nom de votre évaluation correspond au nom d’une autre évaluation dans un groupe donné, vous recevrez un message d’erreur vous demandant de créer un autre nom.

4. Affectez votre évaluation à un groupe. Vous pouvez :
    - Sélectionnez **utiliser un groupe existant** pour l’affecter à un groupe que vous avez déjà créé ; des
    - Sélectionnez **créer un groupe** pour créer un groupe et lui affecter cette évaluation. Déterminez un nom pour votre groupe et entrez-le dans le champ sous la case d’option.

5. **Vérifiez et terminez :** Le dernier écran de l’Assistant indique le modèle, le nom et le groupe choisis pour l’évaluation. Vous pouvez modifier ces paramètres à partir des liens de l’écran, ce qui vous permet de revenir aux étapes pertinentes de l’Assistant. Une fois que vous êtes satisfait des paramètres, sélectionnez **créer une évaluation**.

6. L’écran suivant confirme que vous avez bien créé votre nouvelle évaluation. Sélectionnez **Terminer** pour fermer l’Assistant, et la page des détails de votre nouvelle évaluation s’affichera à l’écran.

Si vous voyez un écran échec de l' **évaluation** après avoir sélectionné **créer une évaluation**, sélectionnez **Réessayer** pour recréer votre évaluation.

## <a name="delete-an-assessment"></a>Supprimer une évaluation

La suppression d’une évaluation le supprime de la liste sur votre page évaluations. **La suppression d’une évaluation est définitive ; vous ne pouvez pas la récupérer.** Si vous souhaitez réutiliser la même évaluation, elle doit être recréée de toutes pièces. Si les actions d’amélioration de l’évaluation ne s’affichent pas dans une autre évaluation, elles seront supprimées lors de la suppression de l’évaluation. Nous vous recommandons d’exporter un rapport de l’évaluation avant de la supprimer définitivement.

Pour supprimer une évaluation, suivez les étapes ci-dessous :

1. Dans la page évaluations, sélectionnez l’évaluation que vous souhaitez supprimer pour ouvrir la page des détails de l’évaluation.
2. Sélectionnez **Supprimer l’évaluation** dans le coin supérieur droit de l’écran.
3. Une fenêtre s’affiche pour vous demander de confirmer la suppression définitive de l’évaluation. Sélectionnez **Supprimer l’évaluation** pour fermer la fenêtre. Vous obtiendrez une fenêtre de confirmation indiquant que votre évaluation a été supprimée du score de conformité.

Si vous supprimez la seule évaluation d’un groupe, ce groupe est également supprimé du score de conformité.

## <a name="monitor-assessment-progress-and-controls"></a>Surveiller la progression et les contrôles de l’évaluation

Chaque évaluation comporte une page de détails qui donne un aperçu rapide de votre progression dans la réalisation de l’évaluation. La page affiche la progression de l’exécution des contrôles, ainsi que l’état de test des actions d’amélioration clés de ces contrôles.

### <a name="overview-tab"></a>Onglet vue d’ensemble

L’onglet vue d’ensemble contient un graphique indiquant votre pourcentage d’achèvement de l’évaluation. Ce graphique contient une répartition des points à partir des actions que vous possédez et des points à partir des actions appartenant à Microsoft, afin que vous puissiez voir le nombre de points supplémentaires dont vous avez besoin pour effectuer l’évaluation.

Les actions d’amélioration clés pour les contrôles de l’évaluation sont répertoriées dans l’ordre d’impact le plus élevé possible pour gagner des points. Le graphique associé décrit l’état de test agrégé de vos actions d’amélioration afin que vous puissiez rapidement évaluer ce qui a été testé et ce qui doit être encore fait.

Pour accéder aux actions d’amélioration individuelles, accédez à l’onglet contrôles.

### <a name="controls-tab"></a>Onglet Contrôles

L’onglet contrôles affiche des informations détaillées sur chaque contrôle mappé à l’évaluation. Un graphique de répartition de l' **État du contrôle** indique l’état des contrôles par famille, ce qui vous permet de voir d’un coup d’œil les regroupements de contrôles nécessitant une attention particulière.

Sous le graphique, un tableau répertorie des informations détaillées sur chaque contrôle au sein de l’évaluation. Les contrôles sont regroupés par famille de contrôles. Développez chaque nom de famille pour révéler les contrôles qu’elle contient. Les informations indiquées pour chaque contrôle sont les suivantes :

- **Titre du contrôle**
- **État**: indique l’état de test des actions d’amélioration dans le contrôle. 
    - **Transmis** : toutes les actions d’amélioration ont un état de test « passé », ou au moins un est passé et le reste est « hors de portée »
    -  **Échec** : au moins une action d’amélioration a un état de test « échec »
    - **Aucun** : toutes les actions d’amélioration n’ont pas été testées
    - **Hors de portée** : toutes les actions d’amélioration sont hors de portée pour cette évaluation
    - **En cours** -les actions d’amélioration ont un État autre que ceux répertoriés ci-dessus, qui peuvent inclure « en cours », « crédit partiel » ou « non détecté »
- **ID de contrôle**: numéro d’identification du contrôle, affecté par sa réglementation, son standard ou sa stratégie correspondante
- **Points atteints**: nombre de points gagnés en effectuant des actions, en dehors du nombre total de points réalisables 
- **Vos actions**: le nombre d’actions terminées sur le nombre total d’actions à effectuer
- **Actions Microsoft**: nombre d’actions exécutées par Microsoft 

Pour afficher les détails d’un contrôle, sélectionnez-le à partir de sa ligne dans le tableau. La page Détails du contrôle affiche un graphique indiquant l’état de test des actions au sein de ce contrôle. Un tableau sous le graphique présente les actions d’amélioration clés pour ce contrôle.

Sélectionnez une action d’amélioration dans la liste pour accéder à la page de détails de l’action d’amélioration. Les pages de détails indiquent l’état du test, les notes de mise en œuvre et le lancement dans la solution recommandée.

#### <a name="learn-more"></a>Si vous souhaitez en savoir plus
[Comprendre comment les contrôles et les actions d’amélioration sont suivis et évalués par le score de conformité.](compliance-score-methodology.md)

## <a name="export-an-assessment-report"></a>Exporter un rapport d’évaluation

Vous pouvez exporter une évaluation vers un fichier Excel pour les parties prenantes en conformité dans votre organisation ou pour les auditeurs et régulateurs externes en [suivant ces instructions](working-with-compliance-manager.md#reports). Vous devez visiter le gestionnaire de conformité pour exporter le rapport.

Le rapport est une capture instantanée de l’évaluation à compter de la date et de l’heure de l’exportation. Elle contient les détails des contrôles gérés par vous-même et par Microsoft, y compris l’état de l’implémentation, la date de test, les résultats des tests et les liens vers les documents de preuve téléchargés.