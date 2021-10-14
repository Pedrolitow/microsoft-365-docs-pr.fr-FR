---
title: Créer et gérer des évaluations dans le Gestionnaire de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
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
description: Créez des évaluations dans le Gestionnaire de conformité Microsoft pour vous aider à répondre aux exigences de réglementations et de certifications importantes pour votre organisation.
ms.openlocfilehash: 536b153a847ef038c4dee25d3dcd23aa638049ee
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2021
ms.locfileid: "60335925"
---
# <a name="build-and-manage-assessments-in-compliance-manager"></a>Créer et gérer des évaluations dans le Gestionnaire de conformité

**Dans cet article :** Découvrez comment personnaliser le Gestionnaire de conformité pour votre organisation en créant et en gérant des **évaluations.** Cet article vous explique comment créer des évaluations, comment les organiser en **groupes,** utiliser des **contrôles,** accepter les mises à jour et exporter des rapports **d’évaluation.**

## <a name="introduction-to-assessments"></a>Présentation des évaluations

Le Gestionnaire de conformité vous aide à créer des évaluations qui évaluent votre conformité avec les réglementations régionales et industrielles qui s’appliquent à votre organisation. Les évaluations reposent sur l’infrastructure des modèles d’évaluation, qui contiennent les contrôles nécessaires, les actions d’amélioration et, le cas échéant, les actions Microsoft pour effectuer l’évaluation. La configuration des évaluations les plus pertinentes pour votre organisation peut vous aider à implémenter des stratégies et des procédures opérationnelles pour limiter vos risques de conformité.

Toutes vos évaluations sont répertoriées sous l’onglet Évaluations du Gestionnaire de conformité. En savoir plus sur [la façon de filtrer votre vue de vos évaluations et d’interpréter les états d’état.](compliance-manager-setup.md#assessments-page)

> [!IMPORTANT]
> Les modèles disponibles pour la création d’évaluations dans votre organisation dépendent de votre contrat de licence. [Passer en revue les détails des licences.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

## <a name="data-protection-baseline-default-assessment"></a>Évaluation par défaut de base de la protection des données

Pour commencer, Microsoft fournit une **évaluation** par défaut dans le Gestionnaire de conformité pour la ligne de base Microsoft 365 protection **des données.** Cette évaluation de référence dispose d’un ensemble de contrôles pour les réglementations et normes clés en matière de protection des données et de gouvernance générale des données. Cette ligne de base dessine principalement des éléments du NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) et de l’ISO (International Organization for Standardization), ainsi que du FedRAMP (Federal Risk and Authorization Management Program) et du R GDPR (Règlement général sur la protection des données de l’Union européenne).

Cette évaluation est utilisée pour calculer votre score de conformité initial la première fois que vous arrivez au Gestionnaire de conformité, avant de configurer d’autres évaluations. Le Gestionnaire de conformité collecte les signaux initiaux de vos solutions Microsoft 365 de conformité. Vous verrez d’un coup d’œil les résultats de votre organisation par rapport aux principales normes et réglementations en matière de protection des données, ainsi que les suggestions d’actions d’amélioration à prendre.

Le Gestionnaire de conformité devient plus utile lorsque vous créez et gérez vos propres évaluations pour répondre aux besoins particuliers de votre organisation.

## <a name="understand-groups-before-creating-assessments"></a>Comprendre les groupes avant de créer des évaluations

Lorsque vous créez une évaluation, vous devez l’affecter à un groupe. Les groupes sont des conteneurs qui vous permettent d’organiser les évaluations d’une manière logique pour vous, par exemple par année ou par réglementation, ou en fonction des divisions ou zones géographiques de votre organisation. C’est pourquoi nous vous recommandons de planifier une stratégie de regroupement avant de créer des évaluations.

Voici des exemples de deux groupes et leurs évaluations sous-jacentes :

- **Évaluation FFIEC IS 2020**
  - FFIEC IS
- **Évaluations de la sécurité et de la confidentialité des données**
  - ISO 27001:2013
  - ISO 27018:2014

Différentes évaluations au sein d’un ou de plusieurs groupes peuvent partager des actions d’amélioration. Les actions d’amélioration peuvent être des modifications apportées dans des solutions techniques mappées à votre client, telles que l’authentification à deux facteurs, ou des actions non techniques que vous effectuez en dehors du système, telles que l’élaboration d’une nouvelle stratégie d’espace de travail. Les mises à jour des détails ou de l’état que vous a faites d’une action d’amélioration technique seront prises en sur mesure par les évaluations de tous les groupes. Les mises à jour des actions d’amélioration non techniques sont reconnues par les évaluations au sein du groupe où vous les appliquez. Cela vous permet d’implémenter une action d’amélioration et de répondre simultanément à plusieurs exigences.

### <a name="create-a-group"></a>Créer un groupe

Vous pouvez créer un groupe lors de la création d’une évaluation. Les groupes ne peuvent pas être créés en tant qu’entités autonomes.

### <a name="what-to-know-when-working-with-groups"></a>Ce qu’il faut savoir lorsque vous travaillez avec des groupes

- Un groupe doit contenir au moins une évaluation.
- Les noms de groupes doivent être uniques au sein de votre organisation.
- Les groupes n’ont pas de propriétés de sécurité. Toutes les autorisations sont associées aux évaluations.
- Une fois que vous avez ajouté une évaluation à un groupe, le regroupement ne peut pas être modifié.
- Si vous ajoutez une nouvelle évaluation à un groupe existant, les informations communes provenant des évaluations de ce groupe sont copiées dans la nouvelle évaluation.
- Les contrôles d’évaluation associés dans différentes évaluations au sein du même groupe sont automatiquement mis à jour lorsqu’ils sont terminés.
- Les groupes peuvent contenir des évaluations pour la même certification ou réglementation, mais chaque groupe ne peut contenir qu’une seule évaluation pour une paire produit-certification spécifique. Par exemple, un groupe ne peut pas contenir deux évaluations pour Office 365 et CSF NIST. Un groupe peut contenir plusieurs évaluations pour le même produit uniquement si la certification ou la réglementation correspondante pour chacune d’elles est différente.
- La suppression d’une évaluation rompt la relation entre cette évaluation et le groupe.
- Les groupes ne peuvent pas être supprimés manuellement.

## <a name="create-assessments"></a>Créer des évaluations

Pour créer une évaluation, vous allez utiliser un Assistant pour sélectionner le modèle qu’il doit utiliser et définir les propriétés de l’évaluation. Les modèles contiennent les contrôles et les recommandations d’action pour l’évaluation, en fonction des certifications pour les différentes réglementations et normes en matière de confidentialité. Les modèles disponibles de votre organisation peuvent inclure un ou plusieurs modèles inclus dans le cadre de votre contrat de licence, ainsi que les modèles premium supplémentaires que vous avez achetés. Chaque modèle, qu’il soit inclus ou premium, existe dans deux versions : une pour une utilisation avec Microsoft 365 et une version universelle qui peut être adaptée à d’autres produits que vous utilisez. Pour en savoir plus sur les modèles, voir [Utiliser des modèles d’évaluation.](compliance-manager-templates.md)

> [!NOTE]
> Seuls les utilisateurs qui détiennent un rôle d’administrateur général, d’administration du Gestionnaire de conformité ou d’évaluateur du Gestionnaire de conformité peuvent créer et modifier des évaluations. En savoir plus sur [les rôles et les autorisations.](compliance-manager-setup.md#set-user-permissions-and-assign-roles)

Pour commencer à créer des évaluations, suivez ces étapes.

1. Connaissez le groupe auquel vous affecterez votre évaluation ou soyez prêt à en créer un nouveau pour cette évaluation.

2. Ouvrez l’Assistant d’évaluation. Vous pouvez accéder à ce volet volant à partir de l’un des deux endroits :
    - Go to your **assessments** page in Compliance Manager and select **Add assessment**; ou
    - Recherchez le modèle que vous souhaitez utiliser sous l’onglet **Modèles** d’évaluation, affichez ses détails et sélectionnez **Créer une évaluation.** Cela remplit le champ de sélection de modèle de l’Assistant pour vous.

3. **Sélectionnez un modèle**: si vous n’avez pas encore choisi de modèle à l’étape 2, choisissez un modèle qui servira de base à votre évaluation. Vous verrez la liste des modèles divisés en catégories incluses et premium (voir [types](compliance-manager-templates.md#template-availability-and-licensing) de modèles pour plus d’informations). Sélectionnez la bouton d’radio en haut de votre modèle, puis sélectionnez **Suivant.**

4. **Produit, nom et groupe :** Définissez ces propriétés pour identifier votre évaluation, choisir le produit qu’elle va évaluer et l’affecter à un groupe.

    - **Produit**: si vous utilisez un modèle universel, sélectionnez si vous créez cette évaluation pour un nouveau produit ou un produit personnalisé existant que vous avez déjà défini dans le Gestionnaire de conformité. Si vous choisissez un nouveau produit, entrez son nom. Notez que vous ne pouvez pas sélectionner Microsoft 365 comme produit lors de l’utilisation d’un modèle universel. Si vous utilisez un modèle Microsoft 365, ce champ est rempli pour vous indiquer Microsoft 365 ne peut pas être modifié.
    - **Nom**: entrez un nom pour votre évaluation dans le champ Nom **de l’évaluation.** Les noms des évaluations doivent être uniques au sein des groupes. Si le nom de votre évaluation correspond au nom d’une autre évaluation dans un groupe donné, vous recevrez une erreur vous demandant de créer un autre nom.
    - **Groupe**: affectez votre évaluation à un groupe. Vous pouvez :
        - Sélectionnez **Utiliser un groupe existant** pour l’affecter à un groupe que vous avez déjà créé ; ou
        - Sélectionnez **Créer un groupe** pour créer un groupe et lui affecter cette évaluation :
            - Déterminez un nom pour votre groupe et entrez-le dans le champ sous la bouton d’radio.
            - Vous pouvez copier des données à partir d’un groupe **existant,** par exemple des détails et des documents d’implémentation et de test, en sélectionnant les zones appropriées.

    Lorsque vous avez terminé, sélectionnez **Suivant**.

5. **Examinez et terminez :** Le dernier écran de l’Assistant affiche le modèle, le nom et le groupe choisis pour l’évaluation. Vous pouvez modifier l’un de ces paramètres à partir des liens à l’écran, ce qui vous permet de revenir aux étapes appropriées de l’Assistant. Lorsque vous êtes prêt, sélectionnez Créer **une évaluation.**

6. L’écran suivant confirme que vous avez bien créé votre nouvelle évaluation. Sélectionnez **Terminé** pour fermer l’Assistant et la page de détails de votre nouvelle évaluation s’affiche à l’écran.

Si vous voyez un **écran** d’échec d’évaluation après avoir sélectionné Créer une **évaluation,** sélectionnez **Réessayer** pour re-créer votre évaluation.

Vous pouvez modifier le nom de votre évaluation  après l’avoir créé en sélectionnant le bouton Modifier le nom dans le coin supérieur droit de la page de détails de [l’évaluation.](#monitor-assessment-progress-and-controls)

## <a name="monitor-assessment-progress-and-controls"></a>Surveiller la progression et les contrôles de l’évaluation

Chaque évaluation possède une page de détails qui donne un aperçu rapide de votre progression dans la réalisation de l’évaluation. La page affiche votre progression dans l’exécution des contrôles, ainsi que l’état de test des actions d’amélioration des clés au sein de ces contrôles.

### <a name="overview-tab"></a>Onglet Overview

L’onglet Vue d’ensemble contient un graphique montrant votre pourcentage vers la fin de l’évaluation. Ce graphique contient une répartition des points des actions que vous possédez et des points d’actions propriété de Microsoft, afin que vous pouvez voir combien de points supplémentaires vous devez effectuer l’évaluation.

Les principales actions d’amélioration des contrôles dans l’évaluation sont répertoriées dans l’ordre de l’impact potentiel le plus important pour gagner des points. Le graphique associé détaille l’état de test agrégé de vos actions d’amélioration afin que vous pouvez évaluer rapidement ce qui a été testé et ce qui reste à faire.

Pour accéder aux actions d’amélioration individuelles, visitez **l’onglet Contrôles** ou **l’onglet Actions d’amélioration.**

### <a name="controls-tab"></a>Onglet Contrôles

L’onglet Contrôles affiche des informations détaillées pour chaque contrôle mappé à l’évaluation. Un **graphique de répartition de** l’état des contrôles affiche l’état des contrôles par famille, de sorte que vous pouvez voir d’un coup d’œil les regroupements de contrôles qui doivent être pris en main.

Sous le graphique, un tableau répertorie des informations détaillées sur chaque contrôle de l’évaluation. Les contrôles sont regroupés par famille de contrôles. Développez chaque nom de famille pour révéler les contrôles qu’elle contient. Les informations répertoriées pour chaque contrôle incluent :

- **Titre du contrôle**
- **État**: reflète l’état de test des actions d’amélioration au sein du contrôle 
    - **Réussi** : toutes les actions d’amélioration ont l’état de test « réussi », ou au moins une est passée et les autres sont « hors de portée »
    -  **Échec :** au moins une action d’amélioration présente l’état de test « Échec »
    - **Aucun** : toutes les actions d’amélioration n’ont pas été testées
    - **Hors de portée :** toutes les actions d’amélioration sont hors de portée de cette évaluation
    - **En cours** : les actions d’amélioration ont un état autre que celui répertorié ci-dessus, qui peut inclure « en cours », « crédit partiel » ou « non détecté »
- **ID de contrôle**: numéro d’identification du contrôle, attribué par sa réglementation, sa norme ou sa stratégie correspondante
- **Points obtenus**: nombre de points gagnés lors de l’exécution d’actions, sur le nombre total de points réalisables 
- **Vos actions**: nombre de vos actions terminées sur le nombre total d’actions à faire
- **Actions Microsoft**: nombre d’actions effectuées par Microsoft

Pour afficher les détails d’un contrôle, sélectionnez-le à partir de sa ligne dans le tableau. La page détails du contrôle affiche un graphique indiquant l’état de test des actions au sein de ce contrôle. Un tableau sous le graphique présente les principales actions d’amélioration de ce contrôle.

Sélectionnez une action d’amélioration dans la liste pour aller dans la page de détails de l’action d’amélioration. La page de détails affiche les notes d’état et d’implémentation des tests, puis se lance dans la solution recommandée.

### <a name="your-improvement-actions-tab"></a>Onglet Actions d’amélioration

L’onglet de vos actions d’amélioration répertorie tous les contrôles de l’évaluation gérés par votre organisation. La barre d’état détaille l’état de test agrégé de vos actions d’amélioration dans l’évaluation afin que vous pouvez évaluer rapidement ce qui a été testé et ce qui reste à faire. Sous la barre se trouve la liste complète des actions d’amélioration et des détails clés, notamment : l’état du test, le nombre de points potentiels et gagnés, les réglementations et normes associées, la solution applicable, le type d’action et la famille de contrôles. En savoir plus sur [la façon dont les actions contribuent à votre score de conformité.](compliance-score-calculation.md#action-types-and-points)

Sélectionnez une action d’amélioration pour afficher  sa page de détails, puis sélectionnez le lien Lancer maintenant pour ouvrir la solution afin d’agir.

### <a name="microsoft-actions-tab"></a>Onglet Actions Microsoft

L’onglet Actions de Microsoft s’affiche pour les évaluations basées sur Microsoft 365 versions des modèles. Il répertorie toutes les actions de l’évaluation qui sont gérées par Microsoft. La liste affiche les détails clés de l’action, notamment : l’état du test, les points qui contribuent à votre score de conformité global, les réglementations et normes associées, la solution applicable, le type d’action et la famille de contrôles. Sélectionnez une action d’amélioration pour afficher sa page de détails.

En savoir plus sur le suivi et les scores des contrôles et [des actions d’amélioration.](compliance-score-calculation.md)

## <a name="accept-updates-to-assessments"></a>Accepter les mises à jour des évaluations

Lorsqu’une mise à jour est disponible pour une évaluation, vous verrez une notification et avez la possibilité d’accepter la mise à jour ou de la différer pour une période ultérieure.

### <a name="what-causes-an-update"></a>Causes d’une mise à jour

Une mise à jour de l’évaluation se produit lorsqu’il existe des modifications de modèle sous-jacentes qui ont une incidence sur le score. Les modifications peuvent impliquer l’ajustement du mappage des contrôles ou d’autres conseils basés sur les modifications réglementaires ou les modifications apportées aux produits. Les mises à jour d’évaluation peuvent provenir de votre organisation (par exemple, lorsqu’un modèle personnalisé est [modifié),](compliance-manager-templates-modify.md)ainsi que de Microsoft.

Si Microsoft met à jour un modèle gestionnaire de conformité que vous avez étendu, votre évaluation héritera de ces mises à jour une fois que vous les aurez acceptées. Votre évaluation conserve les attributs supplémentaires que vous avez appliqués à l’évaluation lorsque vous l’avez étendue.

Les évaluations personnalisées que vous créez ne reçoivent aucune mise à jour de modèle de Microsoft. Les évaluations personnalisées peuvent recevoir des mises à jour des actions d’amélioration, mais les mises à jour Microsoft pour contrôler le mappage entre les évaluations et les actions d’amélioration ne s’appliquent pas aux modèles personnalisés.

> [!NOTE]
> Les mises à jour des évaluations s’appliquent uniquement au niveau du groupe. Si vous avez deux évaluations conçues à partir du même modèle qui existent dans deux groupes différents, chaque évaluation aura une notification de mise à jour en attente et vous devrez accepter la mise à jour de chaque évaluation dans son groupe respectif individuellement.

#### <a name="where-youll-see-assessment-update-notifications"></a>Où vous verrez les notifications de mise à jour de l’évaluation

La page détails de l’évaluation affiche également une **étiquette de** mise à jour en attente en plus de l’évaluation avec une mise à jour. Sélectionnez cette évaluation pour obtenir sa page de détails.

Un message en haut de la page détails de l’évaluation indique qu’une mise à jour est disponible pour cette évaluation. Sélectionnez le **bouton Réviser la** mise à jour dans la bannière pour passer en revue les modifications spécifiques et accepter ou différer la mise à jour.

La page de détails de l’évaluation peut également lister les actions d’amélioration qui ont une **étiquette** de mise à jour en attente à côté d’elles. Ces mises à jour sont pour des modifications spécifiques apportées aux actions d’amélioration elles-mêmes et doivent être acceptées séparément. Pour en [savoir plus, consultez](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) Accepter les mises à jour pour les actions d’amélioration.

#### <a name="review-update-to-accept-or-defer"></a>Passer en revue la mise à jour pour accepter ou différer

Après avoir sélectionné la mise à **jour révision** dans la page détails de l’évaluation, un volet volant s’affiche sur le côté droit de votre écran. Le volet volant fournit les détails clés ci-dessous sur la mise à jour en attente :

- Titre du modèle
- Source de la mise à jour (Microsoft, votre organisation ou un utilisateur spécifique)
- Date de création de la mise à jour
- Présentation de la mise à jour
- Détails spécifiques sur les modifications, y compris l’impact sur votre score de conformité, la progression vers la fin de l’évaluation et le nombre spécifique de modifications apportées aux actions et contrôles d’amélioration.

La sélection du **lien** du modèle mis à jour permet de télécharger un fichier Excel contenant les données de contrôle pour la version du modèle avec les mises à jour en attente. La sélection du **lien Modèle actuel** télécharge un fichier du modèle existant sans les modifications.

Pour accepter la mise à jour et apporter les modifications à votre évaluation, **sélectionnez Accepter la mise à jour.** Les modifications acceptées sont permanentes.

Si vous **sélectionnez Annuler,** la mise à jour ne sera pas appliquée à l’évaluation. Toutefois, vous continuerez à voir la notification de mise à jour **en** attente jusqu’à ce que vous acceptiez la mise à jour.

**Pourquoi nous vous recommandons d’accepter les mises à jour ?**

L’acceptation des mises à jour vous permet de vous assurer que vous avez les conseils les plus mis à jour sur l’utilisation des solutions et la prise d’actions d’amélioration appropriées pour vous aider à répondre aux exigences de la certification.

**Pourquoi différer une mise à jour ?**

Si vous êtes en train d’effectuer une évaluation, vous voudrez peut-être vous assurer que vous avez terminé de travailler dessus avant d’accepter une mise à jour de l’évaluation qui pourrait perturber le mappage des contrôles. Vous pouvez différer la mise à jour ultérieurement en sélectionnant **Annuler** dans le volet volant de révision de la mise à jour.

## <a name="export-an-assessment-report"></a>Exporter un rapport d’évaluation

Vous pouvez exporter une évaluation vers un fichier Excel de conformité pour les parties prenantes de votre organisation ou pour les auditeurs externes et les régulateurs. Dans la page détails  de votre évaluation, sélectionnez le bouton Générer un rapport en haut de la page, ce qui crée un fichier Excel que vous pouvez enregistrer et partager.

Le rapport est un instantané de l’évaluation à la date et à l’heure de l’exportation. Il contient les détails des contrôles gérés par vous et Microsoft, y compris l’état de l’implémentation, la date de test et les résultats des tests.

## <a name="delete-an-assessment"></a>Supprimer une évaluation

La suppression d’une évaluation la supprime de la liste de votre page d’évaluations. Notez ces points importants sur la suppression des évaluations :

- **La suppression d’une évaluation est permanente . vous ne pouvez pas l’obtenir.** Si vous souhaitez utiliser à nouveau la même évaluation, vous devez la créer à nouveau.
- Si les actions d’amélioration de l’évaluation n’apparaissent dans aucune autre évaluation, elles seront supprimées lors de la suppression de l’évaluation.
- Nous vous [recommandons d’exporter un rapport de](#export-an-assessment-report) l’évaluation avant de le supprimer définitivement.

Pour supprimer une évaluation, suivez les étapes ci-dessous :

1. Dans la page **évaluations,** sélectionnez l’évaluation que vous souhaitez supprimer pour ouvrir la page de détails de cette évaluation.

2. Sélectionnez **Supprimer l’évaluation** dans le coin supérieur droit de votre écran.

3. Une fenêtre s’affiche et vous demande de confirmer la suppression définitive de l’évaluation. Sélectionnez **Supprimer l’évaluation** pour fermer la fenêtre. Vous recevrez une fenêtre de confirmation vous confirmant que votre évaluation a été supprimée du Gestionnaire de conformité.

Si vous supprimez la seule évaluation d’un groupe, ce groupe est également supprimé du Gestionnaire de conformité.

> [!NOTE]
> Vous ne pouvez pas supprimer toutes vos évaluations. Les organisations ont besoin d’au moins une évaluation pour que le Gestionnaire de conformité fonctionne correctement. Si l’évaluation que vous souhaitez supprimer est la seule, ajoutez une autre évaluation avant de supprimer l’autre évaluation.
