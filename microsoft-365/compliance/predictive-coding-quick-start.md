---
title: Codage prédictif dans eDiscovery (Premium) - Démarrage rapide
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Découvrez comment commencer à utiliser le module de codage prédictif dans eDiscovery (Premium). Cet article vous guide tout au long du processus de bout en bout d’utilisation du codage prédictif pour identifier le contenu d’un ensemble de révisions le plus pertinent pour votre investigation.
ms.openlocfilehash: dc4edcb6affa7ccfd6a915839ef84b0d453fcfca
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996149"
---
# <a name="quick-start-predictive-coding-in-ediscovery-premium-preview"></a>Démarrage rapide : Codage prédictif dans eDiscovery (Premium) (préversion)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Cet article présente un guide de démarrage rapide pour l’utilisation du codage prédictif dans Microsoft Purview eDiscovery (Premium). Le module de codage prédictif utilise des fonctionnalités de Machine Learning intelligentes pour vous aider à éliminer de grands volumes de contenu de cas qui ne sont pas pertinents pour votre investigation. Pour ce faire, créez et entraînez vos propres modèles de codage prédictif qui vous aident à hiérarchiser les éléments les plus pertinents à examiner.

Voici une vue d’ensemble rapide du processus de codage prédictif :

![Processus de démarrage rapide pour le codage de prédiction.](..\media\PredictiveCodingQuickStartProcess.png)

Pour commencer, vous créez un modèle, étiqueter jusqu’à 50 éléments comme pertinents ou non pertinents. Le système utilise ensuite cette formation pour appliquer des scores de prédiction à chaque élément du jeu de révision. Cela vous permet de filtrer les éléments en fonction du score de prédiction, ce qui vous permet d’examiner d’abord les éléments les plus pertinents (ou non pertinents). Si vous souhaitez entraîner des modèles avec des taux d’accuracies et de rappel plus élevés, vous pouvez continuer à étiqueter les éléments dans les cycles d’entraînement suivants jusqu’à ce que le modèle se stabilise. Une fois le modèle stabilisé, vous pouvez appliquer le filtre de prédiction final pour hiérarchiser les éléments à examiner.

Pour obtenir une vue d’ensemble détaillée du codage prédictif, consultez [En savoir plus sur le codage prédictif dans eDiscovery (Premium).](predictive-coding-overview.md)

## <a name="step-1-create-a-new-predictive-coding-model"></a>Étape 1 : Créer un modèle de codage prédictif

La première étape consiste à créer un modèle de codage prédictif dans l’ensemble de révisions

1. Dans le portail de conformité Microsoft Purview, ouvrez un cas eDiscovery (Premium), puis sélectionnez l’onglet **Révision des ensembles**.

2. Ouvrez un jeu de révision, puis cliquez sur **le codage prédictif AnalyticsManage** >  (préversion).

   ![Cliquez sur le menu déroulant Analyser dans l’ensemble de révision pour accéder à la page de codage prédictif.](..\media\ManagePredictiveCoding.png)

3. Dans la page **Modèles de codage prédictif (préversion),** cliquez sur **Nouveau modèle**.

4. Dans la page de menu volant, tapez un nom pour le modèle et une description facultative.

5. Cliquez sur **Enregistrer** pour créer le modèle.

   La préparation de votre modèle par le système prendra quelques minutes. Une fois qu’il est prêt, vous pouvez effectuer la première série d’entraînement.

Pour obtenir des instructions plus détaillées, consultez [Créer un modèle de codage prédictif](predictive-coding-create-model.md).

## <a name="step-2-perform-the-first-training-round"></a>Étape 2 : Effectuer le premier tour d’entraînement

Après avoir créé le modèle, l’étape suivante consiste à terminer la première série d’entraînement en étiquetant les éléments comme pertinents ou non pertinents.

1. Ouvrez le jeu de révisions, puis cliquez sur **le codage prédictif AnalyticsManage** >  (préversion).

2. Dans la page **Modèles de codage prédictif (préversion),** sélectionnez le modèle que vous souhaitez entraîner.

3. Sous l’onglet **Vue d’ensemble** , sous **Ronde 1**, cliquez sur **Démarrer la prochaine série d’entraînement**.

   L’onglet **Formation** s’affiche et contient 50 éléments à étiqueter.

4. Passez en revue chaque document, puis sélectionnez le bouton **Pertinent** ou **Non pertinent** en bas du volet de lecture pour l’étiqueter.

   ![Étiqueter chaque document comme pertinent ou non pertinent.](..\media\TrainModel1.png)

5. Une fois que vous avez étiqueté les 50 éléments, cliquez sur **Terminer**.

    Il faudra quelques minutes pour que le système « apprenne » à partir de votre étiquetage et met à jour le modèle. Une fois ce processus terminé, l’état **Prêt** s’affiche pour le modèle dans la page **Modèles de codage prédictif (préversion).**

Pour obtenir des instructions plus détaillées, consultez [Entraîner un modèle de codage prédictif](predictive-coding-train-model.md).

## <a name="step-3-apply-the-prediction-score-filter-to-items-in-review-set"></a>Étape 3 : Appliquer le filtre de score de prédiction aux éléments du jeu de révision

Une fois que vous avez effectué au bail une série d’entraînement, vous pouvez appliquer le filtre de score de prédiction aux éléments du jeu de révision. Cela vous permet de passer en revue les éléments que le modèle a prédits comme pertinents ou non pertinents.   

1. Ouvrez le jeu de révisions.

   ![Cliquez sur Filtres pour afficher la page de menu volant Filtres.](..\media\PredictionScoreFilter0.png)

   Les filtres par défaut pré-chargés s’affichent en haut de la page de l’ensemble de révisions. Vous pouvez laisser ces paramètres définis sur **Any**.

2. Cliquez sur **Filtres** pour afficher la page de menu volant **Filtres** .

3. Développez la section **Analyse & codage prédictif** pour afficher un ensemble de filtres.

      ![Filtre de score de prédiction dans la section Analyse & codage prédictif.](..\media\PredictionScoreFilter1.png)

   La convention d’affectation de noms pour les filtres de score de prédiction est **le score de prédiction (nom du modèle).** Par exemple, le nom du filtre de score de prédiction pour un modèle nommé **Modèle A** est Score de **prédiction (modèle A).**

4. Sélectionnez le filtre de score de prédiction que vous souhaitez utiliser, puis cliquez sur **Terminé**.

5. Dans la page du jeu de révision, cliquez sur la liste déroulante pour le filtre de score de prédiction et tapez les valeurs minimales et maximales pour la plage de score de prédiction. Par exemple, la capture d’écran suivante montre une plage de score de prédiction comprise entre **.5** et **1.0**.

   ![Valeurs minimales et maximales pour le filtre de score de prédiction.](..\media\PredictionScoreFilter2.png)

6. Cliquez en dehors du filtre pour appliquer automatiquement le filtre au jeu de révision.

  Une liste de documents avec un score de prédiction dans la plage que vous avez spécifiée s’affiche sur la page du jeu de révision.

Pour obtenir des instructions plus détaillées, consultez [Appliquer un filtre de prédiction à un ensemble de révisions](predictive-coding-apply-prediction-filter.md).

## <a name="step-4-perform-more-training-rounds"></a>Étape 4 : Effectuer d’autres cycles d’entraînement

Plus que probablement, vous devrez effectuer plus de cycles d’entraînement pour entraîner le module afin de mieux prédire les éléments pertinents et non pertinents dans l’ensemble de révision. En général, vous allez entraîner le modèle suffisamment de temps jusqu’à ce qu’il se stabilise suffisamment pour répondre à vos besoins.

Pour plus d’informations, consultez [Effectuer des rondes d’entraînement supplémentaires](predictive-coding-train-model.md#perform-additional-training-rounds)

## <a name="step-5-apply-the-final-prediction-score-filter-to-prioritize-review"></a>Étape 5 : Appliquer le filtre de score de prédiction final pour hiérarchiser la révision

Répétez les instructions de l’étape 3 pour appliquer le score de prédiction final à l’ensemble de révision afin de hiérarchiser la révision des éléments pertinents et non pertinents une fois que vous avez terminé tous les cycles d’entraînement et stabilisé le modèle.
