---
title: Créer et gérer des évaluations dans le Gestionnaire de conformité Microsoft
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
description: Créez des évaluations dans le Gestionnaire de conformité Microsoft pour vous aider à répondre aux exigences de réglementations et de certifications importantes pour votre organisation.
ms.openlocfilehash: d09103f58be3a5fa39b57ca35da411e8046aace5
ms.sourcegitcommit: 61d7284b412d0f7bbd8bbb2225c2e6324f86b717
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "48262289"
---
# <a name="build-and-manage-assessments-in-compliance-manager"></a>Créer et gérer des évaluations dans le Gestionnaire de conformité

**Dans cet article :** Découvrez comment personnaliser le Gestionnaire de conformité pour votre organisation en créant et en gérant des **évaluations.** Cet article vous explique comment créer des évaluations, comment les organiser en **groupes,** utiliser des **contrôles,** accepter les mises à jour et exporter des rapports **d’évaluation.**

> [!IMPORTANT]
> Les évaluations disponibles pour votre organisation dépendent de votre contrat de licence. [Examinez les détails.](https://go.microsoft.com/fwlink/?linkid=2132371)

## <a name="introduction-to-assessments"></a>Présentation des évaluations

Le Gestionnaire de conformité vous aide à gérer la conformité avec les évaluations des réglementations et certifications qui s’appliquent à votre organisation. Les évaluations sont des regroupements de contrôles d’une réglementation, d’une norme ou d’une stratégie spécifique. Le Gestionnaire de conformité facilite le suivi de votre conformité en fournissant des évaluations pré-conçues qui couvrent diverses réglementations et certifications régionales et industrielles.

Chaque évaluation est créée à partir d’un [modèle d’évaluation.](compliance-manager-templates.md) Les modèles servent d’infrastructure contenant les contrôles nécessaires, les actions d’amélioration et les actions Microsoft pour effectuer l’évaluation. La configuration des évaluations les plus pertinentes pour votre organisation peut vous aider à implémenter des stratégies et des procédures opérationnelles pour limiter vos risques de conformité.

Toutes vos évaluations sont répertoriées sur la page des évaluations. En savoir plus sur [la façon de filtrer votre vue de vos évaluations et d’interpréter les états d’état.](compliance-manager-setup.md#assessments-page)

## <a name="data-protection-baseline-default-assessment"></a>Évaluation par défaut de base de la protection des données

Pour commencer, Microsoft fournit une **évaluation** par défaut dans le Gestionnaire de conformité pour la ligne de base de protection des données **Microsoft 365.** Cette évaluation de référence dispose d’un ensemble de contrôles pour les réglementations et normes clés en matière de protection des données et de gouvernance générale des données. Cette ligne de base tire principalement des éléments du NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) et de l’ISO (International Organization for Standardization), ainsi que du FedRAMP (Federal Risk and Authorization Management Program) et du R GDPR (Règlement général sur la protection des données de l’Union européenne).

Cette évaluation est utilisée pour calculer votre score de conformité initial la première fois que vous arrivez au Gestionnaire de conformité, avant de configurer d’autres évaluations. Le Gestionnaire de conformité collecte les signaux initiaux de vos solutions Microsoft 365. Vous verrez d’un coup d’œil les résultats de votre organisation par rapport aux principales normes et réglementations en matière de protection des données, ainsi que les suggestions d’actions d’amélioration à prendre.

Le Gestionnaire de conformité devient plus utile lorsque vous créez et gérez vos propres évaluations pour répondre aux besoins particuliers de votre organisation.

## <a name="assessment-creation-overview"></a>Vue d’ensemble de la création de l’évaluation

Il existe trois façons de configurer les évaluations :

1. [Utilisez une évaluation pré-conçue.](#use-a-pre-built-assessment)
2. [Étendez une évaluation pré-conçue en fonction de vos propres besoins.](#extend-a-pre-built-assessment)
3. [Créez votre propre évaluation personnalisée.](#create-your-own-custom-assessment)

> [!NOTE]
> Seuls les utilisateurs qui détiennent un rôle d’administrateur général ou d’administration du Gestionnaire de conformité peuvent créer et modifier des évaluations. En savoir plus sur [les rôles et les autorisations.](compliance-manager-setup.md#set-user-permissions-and-assign-roles)

**Utiliser une évaluation pré-conçue**

Lancez votre parcours de conformité en choisissant une évaluation déjà définie par le Gestionnaire de conformité. Nous fournissons un large éventail de modèles pour les [réglementations](compliance-manager-templates.md) et les certifications qui s’alignent sur les secteurs, les régions et les normes de protection des données communes, telles que le R GDPR et la norme ISO 27001. Les modèles contiennent les contrôles et les actions d’amélioration qui vous aident à répondre aux exigences d’une certification particulière. Vous serez invité à choisir un modèle lorsque vous commencerez [à créer une évaluation.](#use-a-pre-built-assessment)

**Étendre une évaluation pré-conçue en fonction de vos besoins**

Vous pouvez modifier une évaluation du Gestionnaire de conformité (processus que nous appelons « extension » ) en ajoutant vos propres contrôles et actions pour mieux répondre aux besoins de votre organisation. Par exemple, si vous devez généralement vous conformer à la loi HIPAA, mais que vous avez besoin de contrôles de sécurité ou de protection des données supplémentaires, vous pouvez étendre notre modèle HIPAA en y ajoutant vos propres contrôles. Consultez les instructions pour [étendre une évaluation pré-conçue.](#extend-a-pre-built-assessment)

**Créer votre propre évaluation personnalisée**

Vous pouvez créer entièrement votre propre évaluation pour suivre précisément ce dont votre organisation a besoin. Pour créer votre propre évaluation, vous devez d’abord créer votre propre modèle pour l’évaluation dans le Gestionnaire de conformité. Consultez les instructions pour [créer votre propre évaluation personnalisée.](#create-your-own-custom-assessment)

## <a name="understand-groups-before-creating-assessments"></a>Comprendre les groupes avant de créer des évaluations

Avant de créer ou de modifier des évaluations, il est important de comprendre le fonctionnement des groupes. Lorsque vous créez une évaluation, vous devez l’affecter à un groupe au cours du processus. C’est pourquoi nous vous recommandons de planifier une stratégie de regroupement pour vos évaluations avant de créer des évaluations.

### <a name="what-are-groups"></a>Qu’est-ce que les groupes ?

Les groupes sont des conteneurs qui vous permettent d’organiser les évaluations. Vous pouvez grouper les évaluations d’une manière logique, par exemple par année ou par réglementation, ou en fonction des divisions ou zones géographiques de votre organisation. Voici des exemples de deux groupes et leurs évaluations sous-jacentes :

- **Évaluation FFIEC IS 2020**
  - FFIEC IS
- **Évaluations de la sécurité et de la confidentialité des données**
  - ISO 27001:2013
  - ISO 27018:2014

Lorsque deux évaluations différentes dans le même groupe partagent des actions d’amélioration qui sont gérées par vous, les mises à jour apportées aux détails ou à l’état d’implémentation d’une action sont automatiquement synchronisées avec la même action dans toute autre évaluation du groupe. Cette synchronisation vous permet d’implémenter une action d’amélioration et de répondre à plusieurs exigences dans plusieurs réglementations.

### <a name="how-to-create-a-group"></a>Comment créer un groupe

Vous créez un groupe au cours du processus de [création d’une nouvelle évaluation.](#to-create-an-assessment)

Les groupes ne peuvent pas être créés en tant qu’entités autonomes. Un groupe doit contenir au moins une évaluation. Pour créer un groupe, vous devez d’abord créer une évaluation à placer dans le groupe.

### <a name="what-to-know-when-working-with-groups"></a>Ce qu’il faut savoir lorsque vous travaillez avec des groupes

- Les noms de groupes doivent être uniques au sein de votre organisation.
- Les groupes n’ont pas de propriétés de sécurité. Toutes les autorisations sont associées aux évaluations.
- Une fois que vous avez ajouté une évaluation à un groupe, le regroupement ne peut pas être modifié.
- Les contrôles d’évaluation associés dans différentes évaluations au sein du même groupe sont automatiquement mis à jour lorsqu’ils sont terminés.
- Si vous ajoutez une nouvelle évaluation à un groupe existant, les informations communes des évaluations de ce groupe sont copiées dans la nouvelle évaluation.
- Les groupes peuvent contenir des évaluations pour la même certification ou réglementation, mais chaque groupe ne peut contenir qu’une seule évaluation pour une paire produit-certification spécifique. Par exemple, un groupe ne peut pas contenir deux évaluations pour Office 365 et CSF NIST. Un groupe peut contenir plusieurs évaluations pour le même produit uniquement si la certification ou la réglementation correspondante pour chacune d’elles est différente.
- La suppression d’une évaluation rompt la relation entre cette évaluation et le groupe.
- Les groupes ne peuvent pas être supprimés.
- Lorsqu’une modification est apportée à une amélioration qui apparaît dans plusieurs groupes, cette modification est reflétée dans toutes les instances de cette action d’amélioration.

## <a name="use-a-pre-built-assessment"></a>Utiliser une évaluation pré-conçue

Il existe deux points de départ pour la création d’une évaluation à partir d’un modèle gestionnaire de conformité.

Vous pouvez commencer le processus à partir  de votre page d’évaluations en sélectionnant le bouton Ajouter une évaluation, puis en passant par l’Assistant création de l’évaluation. Les étapes de ce processus sont les suivantes.

Vous pouvez également commencer à partir de votre page de modèles d’évaluation en trouvant le modèle de votre choix et en le sélectionnant dans la liste pour parvenir à sa page de détails. Dans la page des détails du modèle, **sélectionnez Créer une évaluation.** Vous allez ensuite entrer l’Assistant avec votre modèle déjà sélectionné.

### <a name="to-create-an-assessment"></a>Pour créer une évaluation

1. Connaissez le groupe auquel vous affecterez votre évaluation ou soyez prêt à en créer un nouveau pour cette évaluation. [En savoir plus sur les groupes.](#understand-groups-before-creating-assessments)  

2. Go to your **assessments** page in Compliance Manager and select **Add assessment**. Un Assistant d’évaluation s’affiche dans un grand volet volant.

3. **Sélectionnez un modèle**: choisissez un modèle qui servira de base à votre évaluation. Sélectionnez la bouton d’radio en de côté du modèle choisi, puis sélectionnez **Suivant**.

4. **Nom et groupe :** Entrez un nom pour votre évaluation dans le champ **Nom de l’évaluation.** Les noms des évaluations doivent être uniques au sein des groupes. Si le nom de votre évaluation correspond au nom d’une autre évaluation dans un groupe donné, vous recevrez une erreur vous demandant de créer un autre nom.

5. Affectez votre évaluation à un groupe. Vous pouvez :
    - Sélectionnez **Utiliser un groupe existant** pour l’affecter à un groupe que vous avez déjà créé ; ou
    - Sélectionnez **Créer un groupe** pour créer un groupe et lui affecter cette évaluation :
        - Déterminez un nom pour votre groupe et entrez-le dans le champ sous la bouton d’radio.
        - Vous pouvez copier des données à partir d’un groupe **existant,** comme les détails et les documents d’implémentation et de test, en sélectionnant les zones appropriées.

    Lorsque vous avez terminé, sélectionnez **Suivant**.

6. **Révision et fin :** Le dernier écran de l’Assistant affiche le modèle, le nom et le groupe choisis pour l’évaluation. Vous pouvez modifier l’un de ces paramètres à partir des liens à l’écran, ce qui vous permet de revenir aux étapes appropriées de l’Assistant. Lorsque vous êtes prêt, sélectionnez Créer **une évaluation.**

7. L’écran suivant confirme que vous avez bien créé votre nouvelle évaluation. Sélectionnez **Terminé** pour fermer l’Assistant et la page de détails de votre nouvelle évaluation s’affiche à l’écran.

Si vous voyez un **écran** d’échec d’évaluation après avoir sélectionné Créer une **évaluation,** sélectionnez **Réessayer** pour re-créer votre évaluation.

Vous pouvez modifier le nom de votre évaluation  après l’avoir créé en sélectionnant le bouton Modifier le nom dans le coin supérieur droit de la page de détails de [l’évaluation.](#monitor-assessment-progress-and-controls)

## <a name="extend-a-pre-built-assessment"></a>Étendre une évaluation pré-conçue

Vous pouvez modifier une évaluation pré-conçue en ajoutant vos propres contrôles et actions d’amélioration au modèle de l’évaluation. Ce processus est appelé « extension d’un modèle Microsoft » dans le Gestionnaire de conformité. Lorsque vous étendez le modèle d’une évaluation, il reçoit les mises à jour publiées par Microsoft, ce qui peut se produire lorsque des modifications sont [apportées](#accepting-updates-to-assessments)à la réglementation ou au produit associé (voir Accepter les mises à jour des évaluations).

Vous terminerez ce processus en commençant par votre page de **modèles** d’évaluation plutôt que votre page **d’évaluations.**

**Avant de commencer**

Pour préparer ce processus, vous devez d’abord assembler une feuille de calcul Excel spécialement mise en forme pour importer les données de modèle nécessaires. Il existe des exigences particulières pour les [fichiers Excel formatés utilisés](compliance-manager-templates.md#formatting-your-template-data-with-excel) dans le processus d’extension. Consultez ces points supplémentaires pour éviter les erreurs dans le processus d’importation :

- Votre feuille de calcul doit contenir uniquement les actions et les contrôles que vous souhaitez ajouter à l’évaluation. 
- La feuille de calcul ne peut contenir aucun des contrôles ou actions qui existent déjà dans l’évaluation que vous souhaitez modifier.
- Envisagez d’inclure « extension » dans le titre de votre modèle, par exemple, « R GDPR – extension [nom de votre société] ». Cela facilite l’identification, dans la liste de vos **modèles** d’évaluation, du modèle standard fourni par Microsoft ou d’un modèle personnalisé avec un nom similaire.

Après avoir formaté votre feuille de calcul, suivez les étapes ci-dessous.

**Étapes d’extension d’un modèle de Gestionnaire de conformité**

1. Go to your **Assessment templates** page and select **Create new template**. Un Assistant Création de modèle s’ouvre.

2. Choisissez le type de modèle que vous souhaitez créer. Dans ce cas, **sélectionnez Étendre un modèle Microsoft,** puis **Sélectionnez**.

3. Un volet volant de sélection de modèle s’affiche sur le côté droit de votre écran. Utiliser **la recherche** pour appliquer des filtres pour localiser le modèle de votre recherche

4. Une fois que vous avez localisé votre modèle, sélectionnez la radio à gauche de son nom, puis sélectionnez **Enregistrer**.

5. L’écran suivant montre le modèle que vous avez sélectionné. Si la réponse est correcte, sélectionnez **Suivant.** (Si ce n’est pas le cas, **sélectionnez Sélectionner** un autre modèle à choisir à nouveau.)

6. Dans **l’écran Télécharger un** fichier, sélectionnez **Parcourir** pour rechercher et télécharger votre fichier Excel mis en forme contenant toutes les données de modèle requises.

7. S’il n’y a aucun problème avec votre fichier, l’écran suivant affiche le nom du fichier téléchargé. Sélectionnez Suivant pour continuer (si vous devez modifier le fichier, sélectionnez **Télécharger un autre fichier).** 

    - En cas de problème avec votre fichier, un message d’erreur en haut explique ce qui ne va pas. Vous devrez corriger et charger à l’autre votre fichier. Des erreurs se résultent si votre feuille de calcul n’est pas correctement mise en forme ou s’il existe des informations non valides dans certains champs.
 
8. **L’écran Révision et fin** affiche le nombre d’actions et de contrôles d’amélioration et le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, sélectionnez **Suivant**. (Si vous devez apporter des modifications, **sélectionnez Télécharger un autre fichier.)**

9. Le dernier écran confirme qu’un nouveau modèle a été créé. Sélectionnez **Terminé** pour quitter l’Assistant.

10. Vous arrivez à la page de détails de votre nouveau modèle. À partir de là, vous pouvez créer votre évaluation en sélectionnant **Créer une évaluation.** Pour obtenir des conseils, commencez à l'#4 dans les [instructions de création d’évaluation ci-dessus.](#to-create-an-assessment)

## <a name="create-your-own-custom-assessment"></a>Créer votre propre évaluation personnalisée

Pour créer une évaluation personnalisée dans le Gestionnaire de conformité, vous devez créer votre propre modèle. Pour créer votre propre modèle, vous devez d’abord assembler une feuille de calcul Excel mise en forme pour importer les données de modèle nécessaires. Il vous permet également de déterminer à l’avance le groupe auquel vous affecterez votre évaluation lorsque vous la créerez (en savoir plus sur les [groupes).](#what-are-groups)

**Suivez les étapes ci-dessous pour créer votre évaluation personnalisée :**

1. **Formatez votre fichier Excel.** Commencez par mettre en forme vos données de modèle dans une feuille de calcul Excel à [l’aide de ces instructions.](compliance-manager-templates.md#formatting-your-template-data-with-excel)

2. **Créez votre modèle** en suivant [ces instructions.](compliance-manager-templates.md#create-a-new-template)

3. **Créez votre évaluation** à partir du modèle. Vous pouvez commencer par ouvrir la page de détails du modèle et sélectionner Créer une **évaluation,** ou aller à votre **page** d’évaluations et sélectionner Créer une **évaluation.**

4. Un Assistant Création d’évaluation s’affiche dans un grand volet volant. À partir de là, vous pouvez suivre les instructions en commençant à l’étape #3 [des instructions](#to-create-an-assessment)de création de l’évaluation, en utilisant votre nouveau modèle personnalisé pour votre évaluation.

## <a name="delete-an-assessment"></a>Supprimer une évaluation

La suppression d’une évaluation la supprime de la liste de votre page d’évaluations. Notez ces points importants sur la suppression des évaluations :

- **La suppression d’une évaluation est permanente . vous ne pouvez pas la récupérer.** Si vous souhaitez utiliser à nouveau la même évaluation, vous devez la créer à nouveau.
- Si les actions d’amélioration de l’évaluation n’apparaissent dans aucune autre évaluation, elles seront supprimées lors de la suppression de l’évaluation.
- Nous vous [recommandons d’exporter un rapport de](#export-an-assessment-report) l’évaluation avant de le supprimer définitivement.

Pour supprimer une évaluation, suivez les étapes ci-dessous :

1. Dans la page **évaluations,** sélectionnez l’évaluation que vous souhaitez supprimer pour ouvrir la page de détails de cette évaluation.

2. Sélectionnez **Supprimer l’évaluation** dans le coin supérieur droit de votre écran.

3. Une fenêtre s’affiche vous demandant de confirmer la suppression définitive de l’évaluation. Sélectionnez **Supprimer l’évaluation** pour fermer la fenêtre. Vous recevrez une fenêtre de confirmation vous confirmant que votre évaluation a été supprimée du Gestionnaire de conformité.

Si vous supprimez la seule évaluation d’un groupe, ce groupe est également supprimé du Gestionnaire de conformité.

> [!NOTE]
> Vous ne pouvez pas supprimer toutes vos évaluations. Les organisations ont besoin d’au moins une évaluation pour que le Gestionnaire de conformité fonctionne correctement. Si l’évaluation que vous souhaitez supprimer est la seule, ajoutez une autre évaluation avant de supprimer l’autre évaluation.

## <a name="monitor-assessment-progress-and-controls"></a>Surveiller la progression et les contrôles de l’évaluation

Chaque évaluation possède une page de détails qui donne un aperçu rapide de votre progression dans la réalisation de l’évaluation. La page affiche votre progression dans l’exécution des contrôles, ainsi que l’état de test des actions d’amélioration des clés au sein de ces contrôles.

### <a name="overview-tab"></a>Onglet Vue d’ensemble

L’onglet Vue d’ensemble contient un graphique montrant votre pourcentage vers la fin de l’évaluation. Ce graphique contient une répartition des points des actions que vous possédez et des points d’actions propriété de Microsoft, afin que vous pouvez voir combien de points supplémentaires vous devez effectuer l’évaluation.

Les principales actions d’amélioration des contrôles dans l’évaluation sont répertoriées dans l’ordre de l’impact potentiel le plus important pour gagner des points. Le graphique associé détaille l’état de test agrégé de vos actions d’amélioration afin que vous pouvez évaluer rapidement ce qui a été testé et ce qui reste à faire.

Pour accéder aux actions d’amélioration individuelles, visitez **l’onglet Contrôles** ou **l’onglet Actions d’amélioration.**

### <a name="controls-tab"></a>Onglet Contrôles

L’onglet Contrôles affiche des informations détaillées pour chaque contrôle mappé à l’évaluation. Un **graphique de répartition de** l’état des contrôles affiche l’état des contrôles par famille, afin que vous pouvez voir d’un coup d’œil les regroupements de contrôles qui doivent être pris en main.

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

Sélectionnez une action d’amélioration dans la liste pour aller dans la page de détails de l’action d’amélioration. Les pages de détails indiquent l’état du test, les notes d’implémentation et le lancement dans la solution recommandée.

### <a name="your-improvement-actions-tab"></a>Onglet Actions d’amélioration

L’onglet de vos actions d’amélioration répertorie tous les contrôles de l’évaluation gérés par votre organisation. La barre d’état détaille l’état de test agrégé de vos actions d’amélioration dans l’évaluation afin que vous pouvez évaluer rapidement ce qui a été testé et ce qui reste à faire. Sous la barre se trouve la liste complète des actions d’amélioration et des détails clés, notamment : l’état du test, le nombre de points potentiels et gagnés, les réglementations et normes associées, la solution applicable, le type d’action et la famille de contrôles. En savoir plus sur [la façon dont les actions contribuent à votre score de conformité.](compliance-score-calculation.md#action-types-and-points)

Sélectionnez une action d’amélioration pour afficher  sa page de détails, puis sélectionnez le lien Lancer maintenant pour ouvrir la solution afin d’agir.

### <a name="microsoft-actions-tab"></a>Onglet Actions Microsoft

L’onglet Actions de Microsoft répertorie toutes les actions de l’évaluation qui sont gérées par Microsoft. La liste affiche les détails clés de l’action, notamment : l’état du test, les points qui contribuent à votre score de conformité global, les réglementations et normes associées, la solution applicable, le type d’action et la famille de contrôles. Sélectionnez une action d’amélioration pour afficher sa page de détails.

En savoir plus sur le suivi et le score des contrôles et [des actions d’amélioration.](compliance-score-calculation.md)

## <a name="accepting-updates-to-assessments"></a>Acceptation des mises à jour des évaluations

Lorsqu’une mise à jour est disponible pour une évaluation, vous verrez une notification et avez la possibilité d’accepter la mise à jour ou de la différer pour une période ultérieure.

### <a name="what-causes-an-update"></a>Causes d’une mise à jour

Une mise à jour de l’évaluation se produit lorsqu’il existe des modifications de modèle sous-jacentes qui ont une incidence sur le score. Les modifications peuvent impliquer l’ajustement du mappage des contrôles ou d’autres instructions basées sur les modifications réglementaires ou les modifications apportées aux produits. Les mises à jour d’évaluation peuvent provenir de votre organisation (par exemple, lorsqu’un modèle personnalisé est [modifié),](compliance-manager-templates.md#modify-a-template)ainsi que de Microsoft.

Si Microsoft met à jour un modèle gestionnaire de conformité que vous avez étendu, votre évaluation héritera de ces mises à jour une fois que vous les aurez acceptées. Votre évaluation conserve les attributs supplémentaires que vous avez appliqués à l’évaluation lorsque vous l’avez étendue.

Les évaluations personnalisées que vous créez ne reçoivent aucune mise à jour de modèle de Microsoft. Les évaluations personnalisées peuvent recevoir des mises à jour des actions d’amélioration, mais les mises à jour Microsoft pour contrôler le mappage entre les évaluations et les actions d’amélioration ne s’appliquent pas aux modèles personnalisés.

> [!NOTE]
> Les mises à jour des évaluations s’appliquent uniquement au niveau du groupe. Si vous avez deux évaluations conçues à partir du même modèle qui existent dans deux groupes différents, chaque évaluation aura une notification de mise à jour en attente et vous devrez accepter la mise à jour de chaque évaluation dans son groupe respectif individuellement.

#### <a name="where-youll-see-assessment-update-notifications"></a>Où vous verrez les notifications de mise à jour de l’évaluation

La page détails de l’évaluation affiche également une **étiquette de** mise à jour en attente en plus de l’évaluation avec une mise à jour. Sélectionnez cette évaluation pour obtenir sa page de détails.

Un message en haut de la page détails de l’évaluation indique qu’une mise à jour est disponible pour cette évaluation. Sélectionnez le **bouton Réviser la** mise à jour dans la bannière pour passer en revue les modifications spécifiques et accepter ou différer la mise à jour.

La page de détails de l’évaluation peut également lister les actions d’amélioration qui ont une **étiquette** de mise à jour en attente à côté d’elles. Ces mises à jour sont pour des modifications spécifiques apportées aux actions d’amélioration elles-mêmes et doivent être acceptées séparément. Pour en savoir [plus, consultez](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) Accepter les mises à jour pour les actions d’amélioration.

#### <a name="review-update-to-accept-or-defer"></a>Passer en revue la mise à jour pour accepter ou différer

Après avoir sélectionné la mise à **jour révision** dans la page détails de l’évaluation, un volet volant s’affiche sur le côté droit de votre écran. Le volet volant fournit les détails clés ci-dessous sur la mise à jour en attente :

- Titre du modèle
- Source de la mise à jour (Microsoft, votre organisation ou un utilisateur spécifique)
- Date de création de la mise à jour
- Présentation de la mise à jour
- Détails spécifiques sur les modifications, y compris l’impact sur votre score de conformité, la progression vers la fin de l’évaluation et le nombre spécifique de modifications apportées aux actions et contrôles d’amélioration.

La sélection du **lien du modèle** Mis à jour téléchargera un fichier Excel contenant des données de contrôle pour la version du modèle avec les mises à jour en attente. La sélection du **lien Modèle actuel** télécharge un fichier du modèle existant sans les modifications.

Pour accepter la mise à jour et apporter les modifications à votre évaluation, **sélectionnez Accepter la mise à jour.** Les modifications acceptées sont permanentes.

Si vous **sélectionnez Annuler,** la mise à jour ne sera pas appliquée à l’évaluation. Toutefois, vous continuerez à voir la notification de mise à jour **en** attente jusqu’à ce que vous acceptiez la mise à jour.

**Pourquoi nous vous recommandons d’accepter les mises à jour ?**

L’acceptation des mises à jour vous permet de vous assurer que vous avez les conseils les plus mis à jour sur l’utilisation des solutions et la prise d’actions d’amélioration appropriées pour vous aider à répondre aux exigences de la certification.

**Pourquoi différer une mise à jour ?**

Si vous êtes en train d’effectuer une évaluation, vous voudrez peut-être vous assurer que vous avez terminé de travailler dessus avant d’accepter une mise à jour de l’évaluation qui pourrait perturber le mappage des contrôles. Vous pouvez différer la mise à jour ultérieurement en sélectionnant **Annuler** dans le volet volant de révision de la mise à jour.

## <a name="export-an-assessment-report"></a>Exporter un rapport d’évaluation

Vous pouvez exporter une évaluation dans un fichier Excel pour les parties prenantes de conformité de votre organisation ou pour les auditeurs externes et les régulateurs. Dans la page détails  de votre évaluation, sélectionnez le bouton Générer un rapport en haut de la page, ce qui crée un fichier Excel que vous pouvez enregistrer et partager.

Le rapport est un instantané de l’évaluation à la date et à l’heure de l’exportation. Il contient les détails des contrôles gérés par vous et Microsoft, y compris l’état de l’implémentation, la date de test et les résultats des tests.