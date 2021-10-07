---
title: Codage prédictif dans Advanced eDiscovery - Démarrage rapide
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
description: Découvrez comment commencer à utiliser le module de codage prédictif dans Advanced eDiscovery. Cet article vous explique le processus de bout en bout d’utilisation du codage prédictif pour identifier le contenu d’un jeu à réviser le plus pertinent pour votre enquête.
ms.openlocfilehash: 38607459057ff06a2ce74364b752130467deaddd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60197592"
---
# <a name="quick-start-predictive-coding-in-advanced-ediscovery-preview"></a>Démarrage rapide : codage prédictif dans Advanced eDiscovery (aperçu)

Cet article présente un démarrage rapide pour l’utilisation du codage prédictif dans Advanced eDiscovery. Le module de codage prédictif dans Advanced eDiscovery utilise les fonctionnalités intelligentes d’apprentissage automatique dans Advanced eDiscovery pour vous aider à réduire la quantité de contenu à réviser. Le codage prédictif vous permet de réduire et de réduire les volumes importants de contenu de cas à un ensemble pertinent d’éléments que vous pouvez hiérarchiser pour révision. Pour ce faire, vous devez créer et former vos propres modèles de codage prédictifs qui vous aident à hiérarchiser l’examen des éléments les plus pertinents d’un jeu à réviser.

Voici un aperçu rapide du processus de codage prédictif :

![Processus de démarrage rapide pour le codage de prédiction.](..\media\PredictiveCodingQuickStartProcess.png)

Pour commencer, vous créez un modèle, en étiqueter aussi peu que 50 éléments comme pertinents ou non pertinents. Le système utilise ensuite cette formation pour appliquer des scores de prévision à chaque élément du jeu à réviser. Cela vous permet de filtrer les éléments en fonction du score de prédiction, ce qui vous permet d’examiner d’abord les éléments les plus pertinents (ou non pertinents). Si vous souhaitez entraîner des modèles avec des taux de rappel et des nombres de rappels plus élevés, vous pouvez continuer à étiqueter des éléments dans les séries de formation suivantes jusqu’à ce que le modèle se stabilise. Une fois le modèle stabilisé, vous pouvez appliquer le filtre de prédiction final pour hiérarchiser les éléments à réviser.

Pour une vue d’ensemble détaillée du codage prédictif, voir En savoir plus sur le codage prédictif [dans Advanced eDiscovery](predictive-coding-overview.md).

## <a name="step-1-create-a-new-predictive-coding-model"></a>Étape 1 : Créer un modèle de codage prédictif

La première étape consiste à créer un modèle de codage prédictif dans le jeu à réviser

1. Dans la Centre de conformité Microsoft 365, ouvrez un Advanced eDiscovery, puis sélectionnez l’onglet Ensembles **de révision.**

2. Ouvrez un jeu à réviser, puis cliquez sur **Analyse** Gérer le  >  **codage prédictif (prévisualisation).**

   ![Cliquez sur le menu déroulant Analyser dans le jeu à réviser pour aller à la page Codage prédictif.](..\media\ManagePredictiveCoding.png)

3. Dans la page **Modèles de codage prédictif (prévisualisation),** cliquez **sur Nouveau modèle.**

4. Dans la page volante, tapez un nom pour le modèle et une description facultative.

5. Cliquez **sur Enregistrer** pour créer le modèle.

   La préparation de votre modèle prendra quelques minutes. Une fois prêt, vous pouvez effectuer la première série de formations.

Pour obtenir des instructions plus détaillées, voir [Créer un modèle de codage prédictif.](predictive-coding-create-model.md)

## <a name="step-2-perform-the-first-training-round"></a>Étape 2 : Effectuer la première série de formations

Après avoir créé le modèle, l’étape suivante consiste à effectuer la première série de formations en étiqueter les éléments comme pertinents ou non pertinents.

1. Ouvrez le jeu à réviser, puis cliquez sur **Analyse** Gérer le  >  **codage prédictif (prévisualisation).**

2. Dans la page **Modèles de codage prédictif (prévisualisation),** sélectionnez le modèle que vous souhaitez entraîner.

3. Sous **l’onglet** Vue d’ensemble, sous **La première** série, cliquez **sur Démarrer la série de formation suivante.**

   **L’onglet** Formation s’affiche et contient 50 éléments à étiqueter.

4. Examinez chaque document, puis  **sélectionnez** le bouton Pertinent ou Non pertinent en bas du volet de lecture pour l’étiqueter.

   ![Étiqueter chaque document comme pertinent ou non pertinent.](..\media\TrainModel1.png)

5. Une fois que vous avez étiqueté les 50 éléments, cliquez sur **Terminer.**

    Il faudra quelques minutes au système pour « apprendre » de votre étiquetage et mettre à jour le modèle. Une fois ce processus terminé, l’état **Prêt** s’affiche pour le modèle sur la page Modèles de codage prédictif **(prévisualisation).**

Pour obtenir des instructions plus détaillées, voir [La formation d’un modèle de codage prédictif.](predictive-coding-train-model.md)

## <a name="step-3-apply-the-prediction-score-filter-to-items-in-review-set"></a>Étape 3 : Appliquer le filtre de score de prédiction aux éléments du jeu à réviser

Après avoir effectué une série de formation en bail, vous pouvez appliquer le filtre de score de prédiction aux éléments du jeu à réviser. Cela vous permet de passer en revue les éléments que le modèle a prévu comme pertinents ou non pertinents.   

1. Ouvrez le jeu à réviser.

   ![Cliquez sur Filtres pour afficher la page de présentation filtres.](..\media\PredictionScoreFilter0.png)

   Les filtres par défaut pré-chargés sont affichés en haut de la page de révision. Vous pouvez laisser ces ensembles sur **Any**.

2. Cliquez **sur Filtres** pour afficher la page de présentation **filtres.**

3. Développez la section Analyse & codage **prédictif** pour afficher un ensemble de filtres.

      ![Filtre de score de prédiction dans la section Analyse & codage prédictif.](..\media\PredictionScoreFilter1.png)

   La convention d’attribution de noms pour les filtres de score de prédiction est **le score de prédiction (nom du modèle).** Par exemple, le nom du filtre de score de prédiction pour un modèle nommé **Modèle A** est Le score de **prédiction (modèle A).**

4. Sélectionnez le filtre de score de prédiction à utiliser, puis cliquez sur **Terminé.**

5. Dans la page de jeu à réviser, cliquez sur ladown pour le filtre de score de prédiction et tapez les valeurs minimales et maximales pour la plage de score de prédiction. Par exemple, la capture d’écran suivante montre une plage de scores de prédiction entre **.5** et **1.0**.

   ![Valeurs minimales et maximales pour le filtre de score de prédiction.](..\media\PredictionScoreFilter2.png)

6. Cliquez en dehors du filtre pour appliquer automatiquement le filtre au jeu à réviser.

  Une liste de documents avec un score de prédiction dans la plage que vous avez spécifiée s’affiche sur la page du jeu à réviser.

Pour obtenir des instructions plus détaillées, voir Appliquer un filtre de prédiction [à un jeu à réviser.](predictive-coding-apply-prediction-filter.md)

## <a name="step-4-perform-more-training-rounds"></a>Étape 4 : Effectuer d’autres séries de formations

Il est plus probable que vous de dû effectuer davantage de séries de formation pour former le module afin de mieux prévoir les éléments pertinents et non pertinents dans l’ensemble de révision. En règle générale, vous allez entraîner le modèle suffisamment de fois jusqu’à ce qu’il soit suffisamment stabilisé pour répondre à vos besoins.

Pour plus d’informations, voir [Effectuer des séries de formation supplémentaires](predictive-coding-train-model.md#perform-additional-training-rounds)

## <a name="step-5-apply-the-final-prediction-score-filter-to-prioritize-review"></a>Étape 5 : Appliquer le filtre de score de prédiction final pour hiérarchiser la révision

Répétez les instructions de l’étape 3 pour appliquer le score de prédiction final au jeu à réviser afin de hiérarchiser la révision des éléments pertinents et non pertinents une fois que vous avez terminé toutes les séries de formation et stabilisé le modèle.
