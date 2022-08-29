---
title: Mettre à jour les actions d’amélioration et intégrer les données de conformité dans le Gestionnaire de conformité Microsoft Purview
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
description: Migrez vos données de conformité existantes vers le Gestionnaire de conformité Microsoft Purview à l’aide d’un processus de chargement basé sur Excel.
ms.openlocfilehash: 399e361e7da3e658c30e205efdcde627da9ccae6
ms.sourcegitcommit: 0c8934129b5ed147fb873fc3f4d201042c313571
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67333804"
---
# <a name="update-improvement-actions-and-bring-compliance-data-into-compliance-manager"></a>Mettre à jour les actions d’amélioration et intégrer des données de conformité dans le Gestionnaire de conformité

**Dans cet article :** Découvrez comment migrer les activités de conformité existantes de votre organisation vers le Gestionnaire de conformité et mettre à jour plusieurs actions d’amélioration à la fois en chargeant un fichier Excel mis en forme.

## <a name="overview"></a>Vue d’ensemble

Le Gestionnaire de conformité permet aux organisations d’intégrer leurs données et preuves d’activité de conformité existantes dans la solution gestionnaire de conformité. En chargeant un fichier Excel spécialement mis en forme, les organisations qui débutent avec le Gestionnaire de conformité peuvent migrer les activités de conformité effectuées dans d’autres systèmes vers le Gestionnaire de conformité et commencer rapidement à augmenter leur score de conformité global.

Ce processus de chargement offre également aux utilisateurs nouveaux et existants du Gestionnaire de conformité une plus grande flexibilité et une plus grande possibilité de mettre à jour les actions d’amélioration à plus grande échelle. Par exemple, vous pouvez :

- [Ajoutez des résultats de test et des preuves](compliance-manager-improvement-actions.md#perform-work-and-store-documentation) à plusieurs actions d’amélioration qui ont été testées dans un système autre que le Gestionnaire de conformité.
- [Attribuez des actions d’amélioration](compliance-manager-improvement-actions.md#assign-improvement-actions) à différents utilisateurs en fonction du potentiel de score des actions.
- Mettez à jour [l’état d’implémentation](compliance-manager-improvement-actions.md#change-implementation-details) ou l’état de [test](compliance-manager-improvement-actions.md#change-test-status) de plusieurs actions d’amélioration en même temps.
- Modifiez la [source de test](compliance-manager-improvement-actions.md#update-testing-source) des actions d’amélioration de l’implémentation automatique à l’implémentation et au test manuels.
- [Parent la source de test](compliance-manager-improvement-actions.md#parent-testing-source) de plusieurs actions à la fois, afin que ces actions héritent de l’état d’implémentation et de test d’une autre action.

## <a name="getting-started"></a>Prise en main

Pour migrer des données existantes vers le Gestionnaire de conformité ou effectuer une mise à jour en bloc des actions d’amélioration, vous pouvez commencer à partir de l’un des deux emplacements du Gestionnaire de conformité :

- À partir de la page **Évaluations** : vous aide à mettre à jour des évaluations spécifiques avec des informations provenant d’ailleurs, telles que des résultats de test ou des preuves d’actions qui ont été testées par un système distinct. 
- À partir de la page **Actions d’amélioration** : facilite la mise à jour simultanée de plusieurs actions, telles que leur affectation aux utilisateurs, la modification de l’état d’implémentation ou de test, et l’ajout de notes et de preuves.

Pour commencer le processus de migration de données ou de mise à jour des actions, [suivez les étapes décrites ci-dessous](#steps-for-updating-actions).

> [!IMPORTANT]
> - Seules les actions d’amélioration gérées par votre organisation, et non les actions gérées par Microsoft, peuvent être mises à jour par ce processus. (En savoir plus sur les [types d’actions d’amélioration](compliance-score-calculation.md#action-types-and-points).)
> - Les actions d’amélioration doivent déjà être associées à une évaluation avant de pouvoir les mettre à jour via ce processus. (En savoir plus sur [la création et la gestion des évaluations](compliance-manager-assessments.md).)

## <a name="migrating-your-existing-work-into-compliance-manager"></a>Migration de votre travail existant vers le Gestionnaire de conformité

Si vous débutez avec le Gestionnaire de conformité, les étapes ci-dessous illustrent le flux de travail de base pour intégrer vos activités de conformité existantes dans le Gestionnaire de conformité :

1. **Créer une évaluation** : le Gestionnaire de conformité peut recommander des évaluations qui peuvent être les plus pertinentes pour votre organisation, ou vous pouvez en créer une par le biais d’un processus guidé. Pour obtenir des instructions, consultez [Créer des évaluations](compliance-manager-assessments.md#create-assessments) .

2. **Exporter les actions d’amélioration** : vous allez exporter un fichier Excel contenant les données d’action que vous souhaitez mettre à jour. Il peut être plus judicieux de démarrer l’exportation à partir de votre page **Évaluations** , mais vous pouvez également exporter à partir de la page **Actions d’amélioration** . Consultez les [étapes décrites ci-dessous](#steps-for-updating-actions).

3. **Mettre à jour le fichier Excel de l’action d’amélioration** : suivez les instructions de l’onglet **Mettre à jour les actions** du fichier Excel pour ajouter vos informations.

4. **Charger le fichier Excel** : chargez votre fichier Excel modifié en sélectionnant la commande **Charger les actions** dans la page **Évaluations** ou **Actions d’amélioration** .

## <a name="updating-multiple-improvement-actions-at-once"></a>Mise à jour simultanée de plusieurs actions d’amélioration

Pour mettre à jour l’état, les preuves, les notes ou d’autres données dans plusieurs actions d’amélioration simultanées, vous allez suivre le flux de base décrit ci-dessous :

1. **Exporter les actions d’amélioration.** Exportez les actions d’amélioration que vous souhaitez mettre à jour, à partir de votre page **Actions d’amélioration** ou de votre page **Évaluations** . L’exportation est un fichier Excel téléchargé contenant des données d’action d’amélioration. Consultez les [étapes décrites ci-dessous](#steps-for-updating-actions).

2. **Mettez à jour le fichier Excel de l’action d’amélioration.** Suivez les instructions de l’onglet **Mettre à jour les actions** du fichier Excel pour ajouter ou mettre à jour les informations dans le fichier Excel spécialement mis en forme.

3. **Chargez le fichier Excel.** Chargez votre fichier Excel modifié en sélectionnant la commande **Charger les actions** dans la page **Évaluations** ou **Actions d’amélioration** .

> [!NOTE]
> Le processus de mise à jour des actions d’amélioration ne peut pas être utilisé pour ajouter de nouvelles actions d’amélioration au Gestionnaire de conformité. L’ajout d’une nouvelle action nécessite la [création d’un modèle d’évaluation personnalisé](compliance-manager-templates-create.md), qui implique un autre type de fichier Excel avec des données d’action et de mappage de contrôle. Reportez-vous aux [instructions de mise en forme du modèle](compliance-manager-templates-format-excel.md) ; en particulier, les instructions de l’onglet « Actions ».

> [!NOTE]
> Si vous exportez les actions d’amélioration à partir d’une évaluation, le fichier Excel exporté inclut des données de mappage de contrôle pour cette évaluation. Toutefois, vous ne pourrez pas modifier les données de mappage de contrôle lorsque vous modifiez votre fichier Excel.

## <a name="steps-for-updating-actions"></a>Étapes de mise à jour des actions

Les étapes suivantes décrivent le processus d’intégration des données d’activité de conformité dans vos évaluations et la mise à jour des actions d’amélioration.

1. Dans le Gestionnaire de conformité, commencez à partir de la page **Évaluations** ou de la page **Actions d’amélioration** .

2. Exportez les actions d’amélioration que vous souhaitez mettre à jour :

    a. Dans la page **Actions d’amélioration** : recherchez les actions d’amélioration à mettre à jour, puis cochez la case à gauche de leurs noms. Sélectionnez ensuite la commande **Exporter les actions** au-dessus de la liste des actions.
    
    b. Dans la page **Évaluations** : recherchez l’évaluation ou les évaluations que vous souhaitez mettre à jour, puis cochez la case à gauche de leurs noms. Sélectionnez ensuite la commande **Exporter les actions** au-dessus de la liste des évaluations.

4. Un fichier Excel est téléchargé, qui contient toutes les données relatives aux actions. Ouvrez le fichier et reportez-vous aux instructions de mise en forme sous l’onglet Intitulé **Comment mettre à jour les actions.**

5. Modifiez les informations sous l’onglet **Mise à jour** des actions de la feuille de calcul en fonction des instructions de mise en forme. Enregistrez ensuite votre version mise à jour du fichier Excel sur votre ordinateur.

6. Dans votre page **Évaluations** ou page **Actions d’amélioration** , sélectionnez la commande **Mettre à jour les actions** , qui ouvre l’Assistant Mise à jour des actions d’amélioration.

7. La première page de l’Assistant répertorie les principaux prérequis : que toutes les actions d’amélioration doivent être associées à au moins une évaluation et que vos données doivent être mises en forme dans un fichier Excel à charger. Cochez les cases en regard des rappels, puis continuez le processus en sélectionnant **Suivant**.

8. Dans la page **Importer les actions d’amélioration mises à jour** , **sélectionnez Parcourir** pour localiser votre fichier Excel mis à jour à partir de son emplacement enregistré, puis sélectionnez **Suivant**. En cas de problème avec le format de votre fichier, un message d’erreur fournit des instructions pour résoudre le problème. Chargez à nouveau votre fichier corrigé, puis sélectionnez **Suivant**.

9. Dans la page **Révision et fin** , passez en revue le résumé indiquant le nombre d’actions qui seront mises à jour, leurs évaluations associées et la façon dont elles affectent votre score de conformité. À partir de là, vous pouvez charger un autre fichier ou poursuivre le chargement en sélectionnant **Actions de mise à jour**.

10. Une fois votre fichier correctement chargé, un écran de confirmation s’affiche. Sélectionnez **Terminer** pour quitter l’Assistant et revenir à la page où vous avez commencé le processus d’actions de mise à jour.

La plupart des mises à jour prendront effet immédiatement, mais il faudra peut-être jusqu’à une journée pour que toutes les informations mises à jour soient entièrement reflétées dans le Gestionnaire de conformité.

> [!NOTE]
> Le mappage des contrôles n’est pas inclus dans le fichier Excel téléchargé lorsque vous *exportez* des actions. Le mappage des contrôles est géré via le processus de création d’un modèle d’évaluation à l’aide d’un [fichier Excel au format différent pour l’importation de données de modèle](compliance-manager-templates-format-excel.md).
