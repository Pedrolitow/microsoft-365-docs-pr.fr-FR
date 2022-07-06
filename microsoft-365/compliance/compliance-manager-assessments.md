---
title: Créer et gérer des évaluations dans le Gestionnaire de conformité Microsoft Purview
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Créez des évaluations dans le Gestionnaire de conformité Microsoft Purview pour vous aider à répondre aux exigences des réglementations et des certifications qui sont importantes pour votre organisation.
ms.openlocfilehash: 6eeb77e1e5d6adea3489764626910e63ce443a2d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633562"
---
# <a name="build-and-manage-assessments-in-compliance-manager"></a>Créer et gérer des évaluations dans le Gestionnaire de conformité

**Dans cet article :** Découvrez comment personnaliser le Gestionnaire de conformité pour votre organisation en créant et en gérant **des évaluations**. Cet article vous guide tout au long de la création d’évaluations, de leur organisation en **groupes**, de l’utilisation **des contrôles**, de l’acceptation des **mises à jour** et de l’exportation des **rapports** d’évaluation.

## <a name="introduction-to-assessments"></a>Présentation des évaluations

Le Gestionnaire de conformité vous aide à créer des évaluations qui évaluent votre conformité aux réglementations sectorielles et régionales qui s’appliquent à votre organisation. Les évaluations sont basées sur le framework des modèles d’évaluation, qui contiennent les contrôles nécessaires, les actions d’amélioration et, le cas échéant, les actions Microsoft pour terminer l’évaluation. La configuration des évaluations les plus pertinentes pour votre organisation peut vous aider à implémenter des stratégies et des procédures opérationnelles pour limiter vos risques de conformité.

Toutes vos évaluations sont répertoriées sous l’onglet Évaluations du Gestionnaire de conformité. En savoir plus sur [la façon de filtrer votre vue de vos évaluations et d’interpréter les états d’état](compliance-manager-setup.md#assessments-page).

> [!IMPORTANT]
> Les modèles disponibles pour votre organisation pour la génération d’évaluations dépendent de votre contrat de licence. [Passez en revue les détails des licences](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="data-protection-baseline-default-assessment"></a>Évaluation par défaut de la base de référence de protection des données

Pour vous aider à démarrer, Microsoft fournit une évaluation **par défaut** dans le Gestionnaire de conformité pour la **base de référence de protection des données Microsoft 365**. Cette évaluation de référence comporte un ensemble de contrôles pour les réglementations et normes clés pour la protection des données et la gouvernance générale des données. Cette base de référence tire principalement des éléments du NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) et de l’ISO (Organisation internationale pour la normalisation), ainsi que du FedRAMP (Federal Risk and Authorization Management Program) et du RGPD (Règlement général sur la protection des données de l’Union européenne).

Cette évaluation est utilisée pour calculer votre score de conformité initial la première fois que vous accédez au Gestionnaire de conformité, avant de configurer d’autres évaluations. Le Gestionnaire de conformité collecte les signaux initiaux de vos solutions Microsoft 365. Vous verrez en un coup d’œil les performances de votre organisation par rapport aux principales normes et réglementations de protection des données, et vous verrez les suggestions de mesures d’amélioration à prendre.

Le Gestionnaire de conformité devient plus utile à mesure que vous générez et gérez vos propres évaluations pour répondre aux besoins particuliers de votre organisation.

## <a name="understand-groups-before-creating-assessments"></a>Comprendre les groupes avant de créer des évaluations

Lorsque vous créez une évaluation, vous devez l’affecter à un groupe. Les groupes sont des conteneurs qui vous permettent d’organiser des évaluations d’une manière logique pour vous, par exemple par année ou par règlement, ou en fonction des divisions ou zones géographiques de votre organisation. C’est pourquoi nous vous recommandons de planifier une stratégie de regroupement avant de créer des évaluations.

Voici des exemples de deux groupes et de leurs évaluations sous-jacentes :

- **Évaluation DE L’IS FFIEC 2020**
  - FFIEC EST
- **Évaluations de la sécurité et de la confidentialité des données**
  - ISO 27001:2013
  - ISO 27018:2014

Différentes évaluations au sein d’un groupe ou de groupes peuvent partager des actions d’amélioration. Les actions d’amélioration peuvent être des modifications que vous apportez dans les solutions techniques mappées à votre locataire, comme l’activation de l’authentification à deux facteurs ou les actions non techniques que vous effectuez en dehors du système, comme l’instauration d’une nouvelle stratégie de lieu de travail. Toutes les mises à jour des détails ou de l’état que vous apportez à une action d’amélioration technique seront récupérées par les évaluations de tous les groupes. Les mises à jour des actions d’amélioration non techniques sont reconnues par les évaluations au sein du groupe dans lequel vous les appliquez. Cela vous permet d’implémenter une action d’amélioration et de répondre simultanément à plusieurs exigences.

### <a name="create-a-group"></a>Créer un groupe

Vous pouvez créer un groupe lors de la création d’une évaluation. Les groupes ne peuvent pas être créés en tant qu’entités autonomes.

### <a name="what-to-know-when-working-with-groups"></a>Ce qu’il faut savoir lors de l’utilisation de groupes

- Un groupe doit contenir au moins une évaluation.
- Les noms de groupes doivent être uniques au sein de votre organisation.
- Les groupes n’ont pas de propriétés de sécurité. Toutes les autorisations sont associées aux évaluations.
- Une fois que vous avez ajouté une évaluation à un groupe, le regroupement ne peut pas être modifié.
- Si vous ajoutez une nouvelle évaluation à un groupe existant, les informations courantes des évaluations de ce groupe sont copiées dans la nouvelle évaluation.
- Les contrôles d’évaluation associés dans différentes évaluations au sein du même groupe sont automatiquement mis à jour une fois terminés.
- Les groupes peuvent contenir des évaluations pour la même certification ou réglementation, mais chaque groupe ne peut contenir qu’une seule évaluation pour une paire produit-certification spécifique. Par exemple, un groupe ne peut pas contenir deux évaluations pour Office 365 et NIST CSF. Un groupe ne peut contenir plusieurs évaluations pour le même produit que si la certification ou la réglementation correspondante pour chacune d’elles est différente.
- La suppression d’une évaluation interrompt la relation entre cette évaluation et le groupe.
- Les groupes ne peuvent pas être supprimés.

## <a name="understand-templates-before-creating-assessments"></a>Comprendre les modèles avant de créer des évaluations

Les modèles d’évaluation contiennent les contrôles et les recommandations d’action pour les évaluations, basés sur des certifications pour différentes réglementations et normes de confidentialité. Votre organisation commence par au moins un et peut-être plus **de modèles inclus** disponibles à utiliser, en fonction de votre contrat de licence. Votre organisation peut également acheter des modèles **Premium** supplémentaires.

Chaque modèle existe dans deux versions : une pour une utilisation avec Microsoft 365 (ou d’autres produits Microsoft disponibles), et une version universelle qui peut être adaptée pour évaluer d’autres produits que vous utilisez. Vous pouvez choisir le type de modèle approprié pour le produit que vous souhaitez évaluer.

Pour plus d’informations sur les modèles, consultez [En savoir plus sur les modèles d’évaluation dans le Gestionnaire de conformité](compliance-manager-templates.md).

## <a name="create-assessments"></a>Créer des évaluations

> [!NOTE]
> Seuls les utilisateurs qui détiennent un rôle Administrateur général, Administration du Gestionnaire de conformité ou Évaluateur du Gestionnaire de conformité peuvent créer et modifier des évaluations. En savoir plus sur les [rôles et les autorisations](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

Avant de commencer, assurez-vous de connaître le groupe auquel vous l’affecterez ou d’être prêt à créer un groupe pour cette évaluation. Lisez des détails sur les [groupes et les évaluations](#understand-groups-before-creating-assessments).

Pour créer une évaluation, vous allez utiliser un processus guidé pour sélectionner un modèle et désigner le produit associé. Dans votre page **Évaluations** , nous vous suggérons de commencer par **Ajouter des évaluations recommandées**, qui vous permet d’identifier et de configurer rapidement les évaluations les plus pertinentes pour votre organisation en même temps. Vous pouvez également configurer les évaluations une par une en sélectionnant Ajouter une **évaluation**. Suivez les étapes ci-dessous pour commencer à générer des évaluations.

#### <a name="create-assessments-based-on-recommendations-for-your-org-type"></a>Créer des évaluations basées sur des recommandations pour votre type d’organisation

Le Gestionnaire de conformité peut indiquer quelles évaluations peuvent être les plus pertinentes pour votre organisation. Lorsque vous fournissez des informations de base sur l’industrie et les emplacements de votre organisation, nous vous recommandons les modèles à utiliser à partir de notre bibliothèque de plus de 300 modèles. Choisissez simplement parmi les modèles recommandés pour la configuration rapide de plusieurs évaluations en même temps.

Pour créer une ou plusieurs évaluations basées sur nos recommandations, sélectionnez **Ajouter des évaluations recommandées** dans votre page **Évaluations** et procédez comme suit :

- Sélectionnez un ou plusieurs secteurs d’activité qui identifient votre organisation, puis sélectionnez **Suivant**
- Sélectionnez une ou plusieurs régions pour l’emplacement de votre organisation, puis sélectionnez **Suivant**
- Dans l’écran **Choisir une évaluation, sélectionnez** la flèche **déroulante en regard des modèles recommandés** pour afficher la liste des évaluations que nous pensons appliquer à votre organisation. Cochez les cases en regard des modèles que vous souhaitez utiliser pour créer des évaluations, puis sélectionnez **Suivant**.
- Passez en revue vos sélections finales et **sélectionnez Ajouter des évaluations recommandées** pour créer vos nouvelles évaluations.

#### <a name="create-an-assessment-using-a-guided-process"></a>Créer une évaluation à l’aide d’un processus guidé

1. Dans votre page **Évaluations** , sélectionnez **Ajouter une évaluation**. Cela vous placera dans l’Assistant création d’évaluation.

2. Dans l’écran **Du modèle de base** , **sélectionnez Sélectionner un modèle** pour choisir le modèle de votre évaluation.

3. Dans le volet volant, choisissez le modèle de réglementation ou de certification sur lequel baser l’évaluation. Liste des modèles divisés en catégories incluses et Premium ([obtenir des détails](compliance-manager-templates.md#template-availability-and-licensing)). Le compteur de **modèles activés/sous licence** en haut du volet de menu volant vous montre comment les modèles que vous utilisez sur le nombre total disponible ou votre organisation à utiliser ([en savoir plus](compliance-manager-templates.md#active-and-inactive-templates)).) Sélectionnez la case d’option en regard du modèle que vous avez choisi, puis **sélectionnez Enregistrer**. Vous revenez à l’écran **de votre modèle de base** , où vous pouvez passer en revue les détails du modèle, puis continuer en sélectionnant **Suivant**.

4. **Produit, nom et groupe :** Définissez ces propriétés pour identifier votre évaluation, choisissez le produit qu’elle évaluera et affectez-la à un groupe.

    - **Produit** : sélectionnez le produit auquel votre évaluation doit s’appliquer. Si vous utilisez un modèle Microsoft, tel qu’un modèle conçu pour Microsoft 365, ce champ est rempli pour vous permettre d’indiquer le produit approprié et ne peut pas être modifié. Si vous utilisez un modèle universel, indiquez si vous créez cette évaluation pour un nouveau produit ou un produit personnalisé que vous avez déjà défini dans le Gestionnaire de conformité. Si vous choisissez un nouveau produit, entrez son nom. Notez que vous ne pouvez pas sélectionner un produit Microsoft prédéfini lors de l’utilisation d’un modèle universel.
    - **Nom de l’évaluation** : entrez un nom pour votre évaluation dans le champ **Nom de l’évaluation** . Les noms d’évaluation doivent être uniques au sein des groupes. Si le nom de votre évaluation correspond au nom d’une autre évaluation dans un groupe donné, vous recevez une erreur vous demandant de créer un autre nom.
    - **Groupe** : attribuez votre évaluation à un groupe. Vous pouvez :
        - Sélectionnez **Utiliser le groupe existant** pour l’affecter à un groupe que vous avez déjà créé ; Ou
        - Sélectionnez **Créer un groupe** pour créer un groupe et lui attribuer cette évaluation :
            - Déterminez un nom pour votre groupe et entrez-le dans le champ sous la case d’option.
            - Vous pouvez **copier des données à partir d’un groupe existant**, comme l’implémentation et le test des détails et des documents, en sélectionnant les zones appropriées.

    Quand vous avez terminé, sélectionner **Suivant**.

5. **Passez en revue et terminez :** Passez en revue vos sélections et apportez les modifications nécessaires. Lorsque vous êtes prêt, **sélectionnez Créer une évaluation**.

L’écran suivant confirme que l’évaluation a été créée. Lorsque vous sélectionnez **Terminé**, vous accédez à la page de détails de votre nouvelle évaluation.

Si vous voyez un écran **d’évaluation ayant échoué** après avoir sélectionné **Créer une évaluation**, sélectionnez **Réessayez** pour recréer votre évaluation.

Vous pouvez modifier le nom de votre évaluation après la avoir créée en sélectionnant le bouton **Modifier le nom** dans le coin supérieur droit de la [page de détails de l’évaluation](#monitor-assessment-progress-and-controls).

## <a name="monitor-assessment-progress-and-controls"></a>Surveiller la progression et les contrôles de l’évaluation

Chaque évaluation a une page de détails qui donne une vue d’ensemble de la progression de l’évaluation. La page affiche votre progression dans l’exécution des contrôles et l’état de test des actions d’amélioration clés au sein de ces contrôles.

### <a name="overview-tab"></a>Onglet Overview

L’onglet Vue d’ensemble contient un graphique montrant votre pourcentage vers la fin de l’évaluation. Ce graphique contient une répartition des points des actions que vous possédez et des points des actions détenues par Microsoft. Vous pouvez ainsi voir le nombre de points supplémentaires dont vous avez besoin pour effectuer l’évaluation.

Les principales actions d’amélioration des contrôles dans l’évaluation sont répertoriées dans l’ordre d’impact potentiel le plus élevé pour gagner des points. Le graphique associé détaille l’état de test agrégé de vos actions d’amélioration afin que vous puissiez rapidement évaluer ce qui a été testé et ce qui reste à faire.

Pour accéder aux actions d’amélioration individuelles, visitez l’onglet **Contrôles** ou l’onglet **Vos actions d’amélioration** .

### <a name="controls-tab"></a>Onglet Contrôles

L’onglet Contrôles affiche des informations détaillées pour chaque contrôle mappé à l’évaluation. Un graphique de **répartition de l’état des contrôles** affiche l’état des contrôles par famille. Vous pouvez donc voir en un coup d’œil les regroupements de contrôles qui nécessitent une attention particulière.

Sous le graphique, un tableau répertorie des informations détaillées sur chaque contrôle dans l’évaluation. Les contrôles sont regroupés par famille de contrôles. Développez chaque nom de famille pour révéler les contrôles individuels qu’il contient. Les informations répertoriées pour chaque contrôle incluent :

- **Titre du contrôle**
- **État** : reflète l’état de test des actions d’amélioration dans le contrôle
  - **Passé** : toutes les actions d’amélioration ont l’état de test « passé », ou au moins une est passée et les autres sont « hors de portée »
  - **Échec** : au moins une action d’amélioration a l’état de test « Échec »
  - **Aucun :** toutes les actions d’amélioration n’ont pas été testées
  - **Hors de portée** : toutes les actions d’amélioration sont hors de portée pour cette évaluation
  - **En cours** : les actions d’amélioration ont un état autre que celui indiqué ci-dessus, qui peut inclure « en cours », « crédit partiel » ou « non détecté »
- **ID de contrôle** : numéro d’identification du contrôle, affecté par sa réglementation, sa norme ou sa stratégie correspondantes
- **Points atteints** : nombre de points gagnés en effectuant des actions, sur le nombre total de points réalisables
- **Vos actions** : nombre de vos actions effectuées sur le nombre total d’actions à effectuer
- **Actions Microsoft** : nombre d’actions effectuées par Microsoft

Pour afficher les détails d’un contrôle, sélectionnez-le dans sa ligne dans le tableau. La page détails du contrôle affiche un graphique indiquant l’état de test des actions au sein de ce contrôle. Un tableau sous le graphique montre les actions d’amélioration clés pour ce contrôle.

Sélectionnez une action d’amélioration dans la liste pour explorer la page de détails de l’action d’amélioration. La page d’informations affiche les notes d’état des tests et d’implémentation, puis se lance dans la solution recommandée.

### <a name="your-improvement-actions-tab"></a>Onglet Actions d’amélioration

L’onglet de vos actions d’amélioration répertorie tous les contrôles de l’évaluation gérés par votre organisation. La barre d’état détaille l’état agrégé des tests de vos actions d’amélioration dans l’évaluation afin que vous puissiez rapidement évaluer ce qui a été testé et ce qui doit encore être fait. Sous la barre se trouve la liste complète des actions d’amélioration et des détails clés, notamment : l’état du test, le nombre de points potentiels et gagnés, les réglementations et normes associées, la solution applicable, le type d’action et la famille de contrôles. En savoir plus sur la [façon dont les actions contribuent à votre score de conformité](compliance-score-calculation.md#action-types-and-points).

Sélectionnez une action d’amélioration pour afficher sa page de détails, puis sélectionnez le lien **Lancer maintenant** pour ouvrir la solution pour prendre des mesures.

### <a name="microsoft-actions-tab"></a>Onglet Actions Microsoft

L’onglet Actions Microsoft s’affiche pour les évaluations basées sur des modèles qui prennent en charge les produits Microsoft. Il répertorie toutes les actions de l’évaluation qui sont gérées par Microsoft. La liste présente les détails des actions clés, notamment : l’état du test, les points qui contribuent à votre score de conformité global, les réglementations et normes associées, la solution applicable, le type d’action et la famille de contrôles. Sélectionnez une action d’amélioration pour afficher sa page de détails.

Découvrez [comment les contrôles et les actions d’amélioration sont suivis et notés.](compliance-score-calculation.md)

## <a name="accept-updates-to-assessments"></a>Accepter les mises à jour des évaluations

Lorsqu’une mise à jour est disponible pour une évaluation, une notification s’affiche et vous avez la possibilité d’accepter la mise à jour ou de la différer ultérieurement.

Mises à jour sont disponibles pour les évaluations basées sur des modèles Microsoft, tels que ceux conçus pour une utilisation avec Microsoft 365. Si votre organisation utilise des modèles universels pour évaluer d’autres produits, l’héritage peut ne pas être pris en charge. Pour plus d’informations, consultez [Étendre les modèles d’évaluation](compliance-manager-templates-extend.md).

### <a name="what-causes-an-update"></a>Causes d’une mise à jour

Une mise à jour d’évaluation se produit lorsqu’il existe des modifications de modèle sous-jacentes qui ont un impact sur le scoring. Les modifications peuvent impliquer l’ajustement du mappage des contrôles ou d’autres conseils en fonction des modifications réglementaires ou des modifications apportées aux produits. Les mises à jour d’évaluation peuvent provenir de votre organisation (par exemple, lorsqu’un [modèle personnalisé est modifié](compliance-manager-templates-modify.md)) ainsi que de Microsoft.

Si Microsoft met à jour un modèle de Gestionnaire de conformité que vous avez étendu, votre évaluation héritera de ces mises à jour une fois que vous les aurez acceptées. Votre évaluation conserve les attributs supplémentaires que vous avez appliqués à l’évaluation lorsque vous l’avez étendue.

Les évaluations personnalisées que vous créez ne reçoivent aucune mise à jour de modèle de Microsoft. Les évaluations personnalisées peuvent recevoir des mises à jour des actions d’amélioration, mais toutes les mises à jour Microsoft pour contrôler le mappage entre les évaluations et les actions d’amélioration ne s’appliquent pas aux modèles personnalisés.

> [!NOTE]
> Mises à jour aux évaluations s’appliquent uniquement au niveau du groupe. Si vous avez deux évaluations générées à partir du même modèle qui existent dans deux groupes différents, chaque évaluation aura une notification de mise à jour en attente, et vous devrez accepter la mise à jour de chaque évaluation de son groupe respectif individuellement.

#### <a name="where-youll-see-assessment-update-notifications"></a>Où vous verrez les notifications de mise à jour d’évaluation

La page détails de l’évaluation affiche également une étiquette de **mise à jour en attente** en regard de l’évaluation avec une mise à jour. Sélectionnez cette évaluation pour accéder à sa page de détails.

Un message en haut de la page des détails de l’évaluation indique qu’une mise à jour est disponible pour cette évaluation. Sélectionnez le bouton **Vérifier la mise à jour** dans la bannière pour passer en revue les modifications spécifiques et accepter ou différer la mise à jour.

La page des détails de l’évaluation peut également répertorier les actions d’amélioration qui ont une étiquette de **mise à jour en attente** à côté d’elles. Ces mises à jour concernent des modifications spécifiques des actions d’amélioration elles-mêmes et doivent être acceptées séparément. [Visitez Accepter les mises à jour des actions d’amélioration](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) pour en savoir plus.

#### <a name="review-update-to-accept-or-defer"></a>Passer en revue la mise à jour pour accepter ou différer

Après avoir sélectionné **Vérifier la mise à jour dans** la page détails de l’évaluation, un volet volant s’affiche sur le côté droit de votre écran. Le volet de menu volant fournit les informations clés ci-dessous sur la mise à jour en attente :

- Titre du modèle
- Source de la mise à jour (Microsoft, votre organisation ou un utilisateur spécifique)
- Date de création de la mise à jour
- Vue d’ensemble expliquant la mise à jour
- Détails spécifiques sur les modifications, notamment l’impact sur votre score de conformité, la progression vers l’achèvement de l’évaluation et le nombre spécifique de modifications apportées aux actions d’amélioration et aux contrôles.

La sélection du lien **Modèle mis à jour** télécharge un fichier Excel contenant les données de contrôle pour la version du modèle avec les mises à jour en attente. La sélection du lien Modèle **actuel** télécharge un fichier du modèle existant sans les modifications.

Pour accepter la mise à jour et apporter les modifications à votre évaluation, sélectionnez **Accepter la mise à jour**. Les modifications acceptées sont permanentes.

Si vous sélectionnez **Annuler**, la mise à jour ne sera pas appliquée à l’évaluation. Toutefois, vous continuerez à voir la notification de **mise à jour en attente** jusqu’à ce que vous acceptiez la mise à jour.

**Pourquoi nous vous recommandons d’accepter les mises à jour**

L’acceptation des mises à jour vous permet de disposer des conseils les plus mis à jour sur l’utilisation des solutions et de prendre les mesures d’amélioration appropriées pour vous aider à répondre aux exigences de la certification en cours.

**Pourquoi voulez-vous différer une mise à jour ?**

Si vous êtes en train d’effectuer une évaluation, vous souhaiterez peut-être vous assurer que vous avez terminé de travailler dessus avant d’accepter une mise à jour de l’évaluation susceptible de perturber le mappage des contrôles. Vous pouvez différer la mise à jour pour une date ultérieure en sélectionnant **Annuler** dans le volet de menu volant de la mise à jour de révision.

## <a name="export-an-assessment-report"></a>Exporter un rapport d’évaluation

Vous pouvez exporter une évaluation vers un fichier Excel pour les parties prenantes de conformité de votre organisation ou pour les auditeurs externes et les régulateurs. Dans la page des détails de votre évaluation, sélectionnez le bouton **Générer un rapport** en haut de la page, ce qui crée un fichier Excel que vous pouvez enregistrer et partager.

Le rapport est un instantané de l’évaluation à la date et à l’heure de l’exportation. Il contient les détails des contrôles gérés par vous et Microsoft, y compris l’état de l’implémentation, la date de test et les résultats des tests.

## <a name="delete-an-assessment"></a>Supprimer une évaluation

La suppression d’une évaluation la supprime de la liste de votre page d’évaluations. Notez ces points importants concernant la suppression des évaluations :

- **La suppression d’une évaluation est permanente; vous ne pouvez pas le récupérer.** Si vous souhaitez réutiliser la même évaluation, vous devez la recréer.
- Si les actions d’amélioration de l’évaluation n’apparaissent dans aucune autre évaluation, elles seront supprimées lors de la suppression de l’évaluation.
- Nous vous recommandons [d’exporter un rapport](#export-an-assessment-report) de l’évaluation avant de le supprimer définitivement.

Pour supprimer une évaluation, suivez les étapes ci-dessous :

1. Dans votre page **d’évaluation** , sélectionnez l’évaluation que vous souhaitez supprimer pour ouvrir la page de détails de cette évaluation.

2. Sélectionnez **Supprimer l’évaluation** dans le coin supérieur droit de votre écran.

3. Une fenêtre s’affiche pour vous demander de confirmer que vous souhaitez supprimer définitivement l’évaluation. Sélectionnez **Supprimer l’évaluation** pour fermer la fenêtre. Vous recevrez une fenêtre de confirmation indiquant que votre évaluation a été supprimée du Gestionnaire de conformité.

> [!NOTE]
> Vous ne pouvez pas supprimer toutes vos évaluations. Les organisations ont besoin d’au moins une évaluation pour que le Gestionnaire de conformité fonctionne correctement. Si l’évaluation que vous souhaitez supprimer est la seule, ajoutez une autre évaluation avant de supprimer l’autre évaluation.
