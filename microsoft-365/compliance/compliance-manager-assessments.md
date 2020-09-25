---
title: Créer et gérer des évaluations dans le gestionnaire de conformité Microsoft
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
description: Créez des évaluations dans le gestionnaire de conformité Microsoft pour vous aider à répondre aux exigences des réglementations et des certifications importantes pour votre organisation.
ms.openlocfilehash: d09103f58be3a5fa39b57ca35da411e8046aace5
ms.sourcegitcommit: 61d7284b412d0f7bbd8bbb2225c2e6324f86b717
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "48262289"
---
# <a name="build-and-manage-assessments-in-compliance-manager"></a>Créer et gérer des évaluations dans le gestionnaire de conformité

**Dans cet article :** Découvrez comment personnaliser le gestionnaire de conformité pour votre organisation en créant et en gérant des **évaluations**. Cet article vous explique comment créer des évaluations, comment les organiser en **groupes**, utiliser des **contrôles**, accepter des **mises à jour**et exporter des **rapports**d’évaluation.

> [!IMPORTANT]
> Les évaluations disponibles pour votre organisation dépendent de votre contrat de licence. [Passez en revue les détails](https://go.microsoft.com/fwlink/?linkid=2132371).

## <a name="introduction-to-assessments"></a>Introduction aux évaluations

Le gestionnaire de conformité vous aide à gérer la conformité avec les évaluations des règlements et des certifications qui s’appliquent à votre organisation. Les évaluations sont des regroupements de contrôles à partir d’un règlement, d’une norme ou d’une stratégie spécifique. Le gestionnaire de conformité facilite le suivi de votre conformité en fournissant des évaluations prédéfinies qui couvrent un grand nombre de réglementations et de certifications régionales et régionales.

Chaque évaluation est créée à partir d’un [modèle d’évaluation](compliance-manager-templates.md). Les modèles servent d’infrastructure contenant les contrôles nécessaires, les actions d’amélioration et les actions Microsoft pour terminer l’évaluation. La configuration des évaluations les plus pertinentes pour votre organisation peut vous aider à mettre en œuvre des stratégies et des procédures opérationnelles pour limiter le risque de conformité.

Toutes vos évaluations sont répertoriées sur la page évaluations. En savoir plus sur [la façon de filtrer votre vue de vos évaluations et d’interpréter les États d’État](compliance-manager-setup.md#assessments-page).

## <a name="data-protection-baseline-default-assessment"></a>Évaluation par défaut de la base de données de protection des données

Pour vous aider, Microsoft fournit une évaluation **par défaut** dans le gestionnaire de conformité pour la **base de données de protection des données Microsoft 365**. Cette évaluation de la configuration de référence dispose d’un ensemble de contrôles pour les réglementations et normes clés en matière de protection des données et de gouvernance des données générales. Cette ligne de base présente principalement des éléments d’Institut CSF (Institut national de normes et technologie Cybersecurity Framework) et ISO (Organisation internationale de normalisation), ainsi que de FedRAMP (Federal Risk and Authorization Management Program) et RGPD (règlement général sur la protection des données de l’Union européenne).

Cette évaluation est utilisée pour calculer votre score de conformité initial la première fois que vous accédez au gestionnaire de conformité, avant de configurer d’autres évaluations. Le gestionnaire de conformité collecte les signaux initiaux de vos solutions Microsoft 365. Vous verrez en un clin d’œil comment votre organisation est en fonction des normes et des réglementations clés en matière de protection des données, et découvrez les actions d’amélioration suggérées à entreprendre.

Le gestionnaire de conformité devient plus utile lorsque vous créez et gérez vos propres évaluations afin de répondre aux besoins spécifiques de votre organisation.

## <a name="assessment-creation-overview"></a>Vue d’ensemble de la création d’évaluation

Vous pouvez configurer les évaluations de trois façons :

1. [Utilisez une évaluation prédéfinie](#use-a-pre-built-assessment).
2. [Étendez une évaluation prédéfinie pour répondre à vos besoins](#extend-a-pre-built-assessment).
3. [Créez votre propre évaluation personnalisée](#create-your-own-custom-assessment).

> [!NOTE]
> Seuls les utilisateurs qui détiennent un rôle d’administrateur général ou de gestionnaire de conformité peuvent créer et modifier des évaluations. En savoir plus sur [les rôles et les autorisations](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

**Utiliser une évaluation prédéfinie**

Lancer votre parcours de conformité en choisissant une évaluation déjà configurée par le gestionnaire de conformité. Nous proposons un large éventail de [modèles](compliance-manager-templates.md) de réglementations et de certifications qui s’alignent sur des secteurs, des régions et des normes de protection des données courantes, telles que RGPD et ISO 27001. Les modèles contiennent les contrôles et les actions d’amélioration pour vous aider à répondre aux exigences d’une certification particulière. Vous serez invité à choisir un modèle lorsque vous commencerez à [créer une évaluation](#use-a-pre-built-assessment).

**Étendre une évaluation prédéfinie pour répondre à vos besoins**

Vous pouvez modifier une évaluation du gestionnaire de conformité — un processus appelé « extension ») en ajoutant vos propres contrôles et actions pour mieux répondre aux besoins de votre organisation. Par exemple, si vous avez généralement besoin de vous conformer à HIPAA mais que vous avez besoin de contrôles de sécurité ou de protection des données supplémentaires, vous pouvez étendre notre modèle HIPAA en y ajoutant vos propres contrôles. Consultez les instructions relatives à l' [extension d’une évaluation](#extend-a-pre-built-assessment)prédéfinie.

**Créer votre propre évaluation personnalisée**

Vous pouvez créer votre propre évaluation entièrement à partir de rien pour suivre précisément les besoins de votre organisation. Pour créer votre propre évaluation, vous devez d’abord créer votre propre modèle pour l’évaluation dans le gestionnaire de conformité. Consultez les instructions pour [créer votre propre évaluation personnalisée](#create-your-own-custom-assessment).

## <a name="understand-groups-before-creating-assessments"></a>Comprendre les groupes avant de créer des évaluations

Avant de créer ou de modifier des évaluations, il est important de comprendre le fonctionnement des groupes. Lorsque vous créez une évaluation, vous devez l’attribuer à un groupe pendant le processus. C’est pourquoi nous vous recommandons de planifier une stratégie de regroupement pour vos évaluations avant de créer des évaluations.

### <a name="what-are-groups"></a>Qu’est-ce qu’un groupe

Les groupes sont des conteneurs qui vous permettent d’organiser des évaluations. Vous pouvez regrouper les évaluations de manière logique, par année ou par réglementation, ou en fonction des divisions ou des régions de votre organisation. Vous trouverez ci-dessous des exemples de deux groupes et de leurs évaluations sous-jacentes :

- **FFIEC est l’évaluation 2020**
  - FFIEC EST
- **Évaluation de la sécurité et de la confidentialité des données**
  - ISO 27001:2013
  - ISO 27018:2014

Lorsque deux évaluations différentes dans le même groupe partagent des actions d’amélioration gérées par vous-même, toutes les mises à jour apportées aux détails de l’implémentation ou à l’état d’une action sont automatiquement synchronisées avec la même action dans toute autre évaluation du groupe. Cette synchronisation vous permet d’implémenter une action d’amélioration et de répondre à plusieurs exigences dans plusieurs réglementations.

### <a name="how-to-create-a-group"></a>Procédure de création d’un groupe

Vous créez un groupe au cours du processus de [création d’une nouvelle évaluation](#to-create-an-assessment).

Les groupes ne peuvent pas être créés en tant qu’entités autonomes. Un groupe doit contenir au moins une évaluation. Pour créer un groupe, vous devez d’abord créer une évaluation à placer dans le groupe.

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

## <a name="use-a-pre-built-assessment"></a>Utiliser une évaluation prédéfinie

Il existe deux points de départ pour la création d’une évaluation à partir d’un modèle gestionnaire de conformité.

Vous pouvez commencer le processus à partir de votre page évaluations en sélectionnant le bouton **Ajouter une évaluation** , puis en parcourant l’Assistant de création d’évaluation. Les étapes de ce processus sont les suivantes.

Vous pouvez également démarrer à partir de la page des modèles d’évaluation en recherchant le modèle de votre choix et en le sélectionnant dans la liste pour obtenir la page de détails correspondante. Sur la page Détails du modèle, sélectionnez **créer une évaluation**. Vous devez ensuite entrer l’Assistant avec votre modèle déjà sélectionné.

### <a name="to-create-an-assessment"></a>Pour créer une évaluation

1. Identifiez le groupe auquel vous affecterez votre évaluation ou préparez-vous à en créer un nouveau pour cette évaluation. [En savoir plus sur les groupes](#understand-groups-before-creating-assessments).  

2. Accédez à votre page **évaluations** dans le gestionnaire de conformité et sélectionnez **Ajouter une évaluation**. Un assistant d’évaluation apparaît dans un grand volet flyout.

3. **Sélectionnez un modèle**: choisissez un modèle qui servira de base à votre évaluation. Sélectionnez la case d’option en regard du modèle choisi, puis sélectionnez **suivant**.

4. **Nom et groupe :** Entrez un nom pour votre évaluation dans le champ nom de l' **évaluation** . Les noms d’évaluation doivent être uniques au sein des groupes. Si le nom de votre évaluation correspond au nom d’une autre évaluation dans un groupe donné, vous recevrez un message d’erreur vous demandant de créer un autre nom.

5. Affectez votre évaluation à un groupe. Vous pouvez :
    - Sélectionnez **utiliser un groupe existant** pour l’affecter à un groupe que vous avez déjà créé ; des
    - Sélectionnez **créer un groupe** pour créer un groupe et lui attribuer cette évaluation :
        - Déterminez un nom pour votre groupe et entrez-le dans le champ sous la case d’option.
        - Vous pouvez **copier des données à partir d’un groupe existant**, comme des détails sur l’implémentation et des tests, en sélectionnant les cases appropriées.

    Lorsque vous avez terminé, sélectionnez **suivant**.

6. **Vérifiez et terminez :** Le dernier écran de l’Assistant indique le modèle, le nom et le groupe choisis pour l’évaluation. Vous pouvez modifier ces paramètres à partir des liens de l’écran, ce qui vous permet de revenir aux étapes pertinentes de l’Assistant. Lorsque vous êtes prêt, sélectionnez **créer une évaluation**.

7. L’écran suivant confirme que vous avez bien créé votre nouvelle évaluation. Sélectionnez **Terminer** pour fermer l’Assistant, et la page des détails de votre nouvelle évaluation s’affichera à l’écran.

Si vous voyez un écran échec de l' **évaluation** après avoir sélectionné **créer une évaluation**, sélectionnez **Réessayer** pour recréer votre évaluation.

Vous pouvez modifier le nom de votre évaluation une fois qu’elle a été créée en cliquant sur le bouton **modifier le nom** dans le coin supérieur droit de la [page de détails](#monitor-assessment-progress-and-controls)de l’évaluation.

## <a name="extend-a-pre-built-assessment"></a>Étendre une évaluation prédéfinie

Vous pouvez modifier une évaluation prédéfinie en ajoutant vos propres contrôles et les actions d’amélioration au modèle de l’évaluation. Ce processus est appelé « extension d’un modèle Microsoft » dans le gestionnaire de conformité. Lorsque vous étendez le modèle d’une évaluation, il reçoit les mises à jour publiées par Microsoft, qui peuvent se produire lorsqu’il y a des modifications apportées à la réglementation ou au produit concerné (consultez la rubrique [acceptation de mises à jour pour les évaluations](#accepting-updates-to-assessments)).

Vous effectuerez ce processus en commençant sur la page des **modèles d’évaluation** plutôt que sur votre page **évaluations** .

**Avant de commencer**

Pour vous préparer à ce processus, vous devez d’abord assembler une feuille de calcul Excel spécialement mise en forme pour importer les données de modèle nécessaires. Il existe des exigences spéciales pour les [fichiers Excel mis en forme](compliance-manager-templates.md#formatting-your-template-data-with-excel) utilisés dans le processus de poste. Consultez ces points supplémentaires pour éviter les erreurs dans le processus d’importation :

- Votre feuille de calcul ne doit contenir que les actions et les contrôles que vous souhaitez ajouter à l’évaluation. 
- La feuille de calcul ne peut pas contenir les contrôles ou les actions qui existent déjà dans l’évaluation que vous souhaitez modifier.
- Envisagez d’inclure « extension » dans le titre de votre modèle, par exemple, « RGPD – [nom de votre société] ». Cela permet d’identifier plus facilement dans la liste de votre page de **modèles d’évaluation** , comme distinct du modèle standard fourni par Microsoft ou d’un modèle personnalisé avec un nom similaire.

Une fois votre feuille de calcul mise en forme, suivez les étapes ci-dessous.

**Étapes de l’extension d’un modèle gestionnaire de conformité**

1. Accédez à la page **modèles d’évaluation** et sélectionnez **créer un nouveau modèle**. Un assistant de création de modèle s’ouvre.

2. Choisissez le type de modèle que vous souhaitez créer. Dans ce cas, sélectionnez **étendre un modèle Microsoft**, puis **Sélectionnez**.

3. Un volet flyout de sélection de modèle apparaît sur le côté droit de l’écran. Utiliser la **recherche** pour appliquer des filtres pour localiser le modèle de votre choix

4. Une fois que vous avez trouvé votre modèle, sélectionnez la case d’option à gauche de son nom, puis sélectionnez **Enregistrer**.

5. L’écran suivant affiche le modèle que vous avez sélectionné. Si ce n’est pas le cas, sélectionnez **suivant**. (Si ce n’est pas le cas, sélectionnez **un autre modèle pour le** choisir de nouveau.)

6. Dans l’écran **Télécharger un fichier** , sélectionnez **Parcourir** pour trouver et charger votre fichier Excel mis en forme contenant toutes les données de modèle requises.

7. S’il n’y a aucun problème avec votre fichier, l’écran suivant indique le nom du fichier téléchargé. Sélectionnez **suivant** pour continuer (si vous devez modifier le fichier, sélectionnez **Télécharger un autre fichier**).

    - En cas de problème avec votre fichier, un message d’erreur en haut explique ce qui est incorrect. Vous devrez corriger et télécharger de nouveau votre fichier. Des erreurs se produisent si votre feuille de calcul est mise en forme de manière incorrecte ou s’il existe des informations non valides dans certains champs.
 
8. L’écran **vérifier et terminer** indique le nombre d’actions et de contrôles d’amélioration, ainsi que le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, sélectionnez **suivant**. (Si vous avez besoin d’effectuer des modifications, sélectionnez **Télécharger un autre fichier**.)

9. Le dernier écran confirme qu’un nouveau modèle a été créé. Sélectionnez **terminé** pour quitter l’Assistant.

10. Vous arrivez sur la page des détails de votre nouveau modèle. À partir de là, vous pouvez créer votre évaluation en sélectionnant **créer une évaluation**. Pour obtenir des instructions, commencez à l’étape #4 dans les [instructions de création d’évaluation ci-dessus](#to-create-an-assessment).

## <a name="create-your-own-custom-assessment"></a>Créer votre propre évaluation personnalisée

La création d’une évaluation personnalisée dans le gestionnaire de conformité requiert la création de votre propre modèle. Pour créer votre propre modèle, vous devez d’abord assembler une feuille de calcul Excel mise en forme pour importer les données de modèle nécessaires. Elle vous permet également de décider du moment où vous allez créer votre évaluation lors de sa création (en savoir plus sur les [groupes](#what-are-groups)).

**Suivez les étapes ci-dessous pour créer votre évaluation personnalisée :**

1. **Mettez en forme votre fichier Excel.** Commencez par mettre en forme les données de votre modèle dans une feuille de calcul Excel à l’aide de [ces instructions](compliance-manager-templates.md#formatting-your-template-data-with-excel).

2. **Créez votre modèle** en suivant [ces instructions](compliance-manager-templates.md#create-a-new-template).

3. **Créez votre évaluation** à partir du modèle. Vous pouvez commencer en ouvrant la page de détails du modèle et en sélectionnant **créer une évaluation**, ou accédez à votre page **évaluations** et sélectionnez **créer une évaluation**.

4. Un assistant de création d’évaluation apparaît dans un grand volet flyout. À partir de là, vous pouvez suivre les conseils en commençant à l’étape #3 des [instructions de création d’évaluation](#to-create-an-assessment), à l’aide de votre nouveau modèle personnalisé pour votre évaluation.

## <a name="delete-an-assessment"></a>Supprimer une évaluation

La suppression d’une évaluation le supprime de la liste sur votre page évaluations. Notez les points importants à prendre en compte lors de la suppression des évaluations :

- **La suppression d’une évaluation est définitive ; vous ne pouvez pas la récupérer.** Si vous souhaitez réutiliser la même évaluation, vous devez la recréer.
- Si les actions d’amélioration de l’évaluation n’apparaissent dans aucune autre évaluation, elles seront supprimées lors de la suppression de l’évaluation.
- Nous vous recommandons d' [exporter un rapport](#export-an-assessment-report) de l’évaluation avant de la supprimer définitivement.

Pour supprimer une évaluation, suivez les étapes ci-dessous :

1. Dans la page **évaluations** , sélectionnez l’évaluation que vous souhaitez supprimer pour ouvrir la page des détails de l’évaluation.

2. Sélectionnez **Supprimer l’évaluation** dans le coin supérieur droit de l’écran.

3. Une fenêtre s’affiche pour vous demander de confirmer la suppression définitive de l’évaluation. Sélectionnez **Supprimer l’évaluation** pour fermer la fenêtre. Vous obtiendrez une fenêtre de confirmation indiquant que votre évaluation a été supprimée du gestionnaire de conformité.

Si vous supprimez la seule évaluation d’un groupe, ce groupe est également supprimé du gestionnaire de conformité.

> [!NOTE]
> Vous ne pouvez pas supprimer toutes vos évaluations. Les organisations ont besoin d’au moins une évaluation pour le gestionnaire de conformité pour fonctionner correctement. Si l’évaluation que vous souhaitez supprimer est la seule, ajoutez une autre évaluation avant de supprimer l’autre évaluation.

## <a name="monitor-assessment-progress-and-controls"></a>Surveiller la progression et les contrôles de l’évaluation

Chaque évaluation comporte une page de détails qui donne un aperçu rapide de votre progression dans la réalisation de l’évaluation. La page affiche la progression de l’exécution des contrôles, ainsi que l’état de test des actions d’amélioration clés de ces contrôles.

### <a name="overview-tab"></a>Onglet vue d’ensemble

L’onglet vue d’ensemble contient un graphique indiquant votre pourcentage d’achèvement de l’évaluation. Ce graphique contient une répartition des points à partir des actions que vous possédez et des points à partir des actions appartenant à Microsoft, afin que vous puissiez voir le nombre de points supplémentaires dont vous avez besoin pour effectuer l’évaluation.

Les actions d’amélioration clés pour les contrôles de l’évaluation sont répertoriées dans l’ordre d’impact le plus élevé possible pour gagner des points. Le graphique associé décrit l’état de test agrégé de vos actions d’amélioration afin que vous puissiez rapidement évaluer ce qui a été testé et ce qui doit être encore fait.

Pour accéder aux actions d’amélioration individuelles, accédez à l’onglet **contrôles** ou à l’onglet **actions d’amélioration** .

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

### <a name="your-improvement-actions-tab"></a>Onglet actions d’amélioration

L’onglet de vos actions d’amélioration répertorie tous les contrôles dans l’évaluation gérée par votre organisation. La barre d’état décrit l’état de test agrégé de vos actions d’amélioration dans l’évaluation afin que vous puissiez rapidement évaluer ce qui a été testé et ce qui doit être encore fait. Sous la barre est la liste complète des actions d’amélioration et des détails clés, notamment : état du test, nombre de points potentiels et acquis, réglementations et normes associées, solution applicable, type d’action et famille de contrôle. En savoir plus sur [la façon dont les actions contribuent à votre score de conformité](compliance-score-calculation.md#action-types-and-points).

Sélectionnez une action d’amélioration pour afficher sa page détails, puis cliquez sur le lien **lancer maintenant** pour ouvrir la solution.

### <a name="microsoft-actions-tab"></a>Onglet actions Microsoft

L’onglet actions de Microsoft répertorie toutes les actions de l’évaluation qui sont gérées par Microsoft. La liste présente les détails des actions clés, notamment : état du test, points qui contribuent à votre score de conformité global, aux réglementations et normes associées, à la solution applicable, au type d’action et à la famille de contrôle. Sélectionnez une action d’amélioration pour afficher la page de détails correspondante.

En savoir plus sur [la façon dont les contrôles et les actions d’amélioration sont suivies et évaluées.](compliance-score-calculation.md)

## <a name="accepting-updates-to-assessments"></a>Acceptation des mises à jour des évaluations

Lorsqu’une mise à jour est disponible pour une évaluation, une notification s’affiche et vous pouvez accepter la mise à jour ou la reporter pour une date ultérieure.

### <a name="what-causes-an-update"></a>Qu’est-ce qui provoque une mise à jour ?

Une mise à jour de l’évaluation se produit lorsqu’il existe des modifications de modèle sous-jacentes qui influent sur le score. Les modifications peuvent impliquer le réglage du mappage de contrôle ou d’autres recommandations basées sur les modifications réglementaires ou les modifications apportées aux produits. Les mises à jour de l’évaluation peuvent provenir de votre organisation (par exemple, lorsqu’un [modèle personnalisé est modifié](compliance-manager-templates.md#modify-a-template)), ainsi que de Microsoft.

Si Microsoft met à jour un modèle de gestionnaire de conformité que vous avez étendu, votre évaluation héritera de ces mises à jour une fois que vous les aurez acceptées. Votre évaluation conservera les attributs supplémentaires que vous avez appliqués à l’évaluation lors de son extension.

Les évaluations personnalisées que vous créez ne reçoivent pas de mises à jour de modèle de Microsoft. Les évaluations personnalisées peuvent recevoir des mises à jour des actions d’amélioration, mais toutes les mises à jour Microsoft pour contrôler le mappage entre les évaluations et les actions d’amélioration ne s’appliquent pas aux modèles personnalisés.

> [!NOTE]
> Les mises à jour des évaluations s’appliquent uniquement au niveau du groupe. Si vous avez deux évaluations créées à partir du même modèle qui existent dans deux groupes différents, chaque évaluation aura une notification de mise à jour en attente et vous devrez accepter la mise à jour pour chaque évaluation dans son groupe respectif individuellement.

#### <a name="where-youll-see-assessment-update-notifications"></a>Où se trouvent les notifications de mise à jour de l’évaluation

La page Détails de l’évaluation affiche également une étiquette de **mise à jour en attente** en regard de l’évaluation avec une mise à jour. Sélectionnez cette évaluation pour accéder à la page de détails correspondante.

Un message dans la partie supérieure de la page Détails de l’évaluation indique qu’une mise à jour est disponible pour cette évaluation. Sélectionnez le bouton **examiner la mise à jour** dans la bannière pour examiner les modifications spécifiques et accepter ou différer la mise à jour.

La page Détails de l’évaluation peut également répertorier les actions d’amélioration qui ont une étiquette de **mise à jour en attente** en regard de celles-ci. Ces mises à jour concernent des modifications spécifiques apportées aux actions d’amélioration elles-mêmes et doivent être acceptées séparément. Consultez [acceptation de mises à jour pour les actions d’amélioration](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) pour en savoir plus.

#### <a name="review-update-to-accept-or-defer"></a>Examiner la mise à jour pour accepter ou reporter

Une fois que vous avez sélectionné **examiner la mise à jour** dans la page Détails de l’évaluation, un volet flyout s’affiche sur le côté droit de l’écran. Le volet flyout fournit les détails clés ci-dessous sur la mise à jour en attente :

- Le titre du modèle
- Source de la mise à jour (Microsoft, votre organisation ou un utilisateur spécifique)
- Date de création de la mise à jour
- Vue d’ensemble de la mise à jour
- Des détails spécifiques sur les modifications, dont l’impact sur votre score de conformité, la progression de l’évaluation et le nombre spécifique de modifications apportées aux actions et contrôles d’amélioration.

En sélectionnant le lien **modèle mis à jour** , vous téléchargez un fichier Excel contenant des données de contrôle pour la version du modèle avec les mises à jour en attente. La sélection du lien **modèle actif** télécharge un fichier du modèle existant sans les modifications.

Pour accepter la mise à jour et effectuer les modifications apportées à votre évaluation, sélectionnez **accepter la mise à jour**. Les modifications acceptées sont permanentes.

Si vous sélectionnez **Annuler**, la mise à jour ne sera pas appliquée à l’évaluation. Toutefois, vous continuerez de voir la notification de **mise à jour en attente** jusqu’à ce que vous acceptiez la mise à jour.

**Pourquoi est-il recommandé d’accepter les mises à jour ?**

En acceptant les mises à jour, vous disposez des instructions les plus à jour sur l’utilisation des solutions et l’exécution des actions d’amélioration appropriées pour vous aider à répondre aux exigences de la certification à la main.

**Pourquoi reporter une mise à jour ?**

Si vous êtes en train d’effectuer une évaluation, vous souhaiterez peut-être vous assurer que vous avez terminé de travailler dessus avant d’accepter une mise à jour de l’évaluation qui pourrait perturber le mappage de contrôle. Vous pouvez reporter la mise à jour ultérieurement en sélectionnant **Annuler** dans le volet de sélection de mise à jour de révision.

## <a name="export-an-assessment-report"></a>Exporter un rapport d’évaluation

Vous pouvez exporter une évaluation vers un fichier Excel pour les parties prenantes en conformité dans votre organisation ou pour les auditeurs et régulateurs externes. Sur la page Détails de l’évaluation, sélectionnez le bouton **générer le rapport** dans la partie supérieure de la page, qui crée un fichier Excel que vous pouvez enregistrer et partager.

Le rapport est une capture instantanée de l’évaluation à compter de la date et de l’heure de l’exportation. Elle contient les détails des contrôles gérés par vous-même et par Microsoft, y compris l’état de l’implémentation, la date de test et les résultats des tests.