---
title: Module de codage prédictif pour eDiscovery (Premium) (préversion)
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
description: Le nouveau module de codage prédictif dans eDiscovery (Premium) utilise le Machine Learning pour analyser les éléments d’un ensemble de révisions sur prédictifs qui sont pertinents pour votre cas ou votre enquête.
ms.openlocfilehash: 7d45c995fafe5b802713e101ad36a362ab77fa37
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64998989"
---
# <a name="learn-about-predictive-coding-in-ediscovery-premium-preview"></a>En savoir plus sur le codage prédictif dans eDiscovery (Premium) (préversion)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Le module de codage prédictif dans eDiscovery (Premium) utilise les fonctionnalités d’apprentissage automatique intelligentes pour vous aider à réduire la quantité de contenu à examiner. Le codage prédictif vous permet de réduire et d’éliminer de grands volumes de contenu de cas dans un ensemble d’éléments pertinents que vous pouvez classer par ordre de priorité pour révision. Pour ce faire, créez et entraînez vos propres modèles de codage prédictif qui vous aident à hiérarchiser la révision des éléments les plus pertinents d’un ensemble de révisions.

Le module de codage prédictif est conçu pour simplifier la gestion d’un modèle au sein d’un ensemble de révisions et fournir une approche itérative de l’entraînement de votre modèle afin que vous puissiez commencer plus rapidement avec les fonctionnalités de Machine Learning dans eDiscovery (Premium). Pour commencer, vous pouvez créer un modèle, étiqueter jusqu’à 50 éléments comme pertinents ou non pertinents. Le système utilise cette formation pour appliquer des scores de prédiction à chaque élément du jeu de révision. Cela vous permet de filtrer les éléments en fonction du score de prédiction, ce qui vous permet d’examiner d’abord les éléments les plus pertinents (ou non pertinents). Si vous souhaitez entraîner des modèles avec des taux d’accuracies et de rappel plus élevés, vous pouvez continuer à étiqueter les éléments dans les cycles d’entraînement suivants jusqu’à ce que le modèle se stabilise.  

## <a name="the-predictive-coding-workflow"></a>Flux de travail de codage prédictif

Voici une vue d’ensemble et une description de chaque flux de travail de codage prédictif d’étape. Pour obtenir une description plus détaillée des concepts et de la terminologie du processus de codage prédictif, consultez la [référence du codage prédictif](predictive-coding-reference.md).

![Flux de travail de codage prédictif.](..\media\PredictiveCodingWorkflow.png)

1. **Créez un modèle de codage prédictif dans l’ensemble de révisions**. La première étape consiste à créer un modèle de codage prédictif dans l’ensemble de révisions. Vous devez avoir au moins 2 000 éléments dans le jeu de révision pour créer un modèle. Après avoir créé un modèle, le système détermine le nombre d’éléments à utiliser comme *jeu de contrôles*. Le jeu de contrôles est utilisé pendant le processus d’entraînement pour évaluer les scores de prédiction que le modèle affecte aux éléments avec l’étiquetage que vous effectuez pendant les cycles d’entraînement. La taille du jeu de contrôles est basée sur le nombre d’éléments du jeu de révision et le niveau de confiance et la marge des valeurs d’erreur définies lors de la création du modèle. Les éléments du jeu de contrôles ne changent jamais et ne sont pas identifiables aux utilisateurs.

   Pour plus d’informations, consultez [Créer un modèle de codage prédictif](predictive-coding-create-model.md).

2. **Terminez la première série d’entraînement en étiquetant les éléments comme pertinents ou non pertinents**. L’étape suivante consiste à entraîner le modèle en démarrant la première série d’entraînement. Lorsque vous démarrez un cycle d’entraînement, le modèle sélectionne de manière aléatoire des éléments supplémentaires dans le jeu de révision, qui est appelé jeu *d’apprentissage*. Ces éléments (à la fois à partir du jeu de contrôles et du jeu d’apprentissage) vous sont présentés afin que vous puissiez les étiqueter comme « pertinents » ou « non pertinents ». La pertinence est basée sur le contenu de l’élément et non sur les métadonnées du document. Une fois que vous avez terminé le processus d’étiquetage dans la série d’entraînement, le modèle « apprend » en fonction de la façon dont vous avez étiqueté les éléments du jeu d’apprentissage. En fonction de cette formation, le modèle traite les éléments du jeu de révision et applique un score de prédiction à chacun d’eux.

   Pour plus d’informations, consultez [Entraîner un modèle de codage prédictif](predictive-coding-train-model.md).

3. **Appliquez le filtre de score de prédiction aux éléments du jeu de révision**. Une fois l’étape d’entraînement précédente terminée, l’étape suivante consiste à appliquer le filtre de score de prédiction aux éléments de la révision pour afficher les éléments que le modèle a déterminés comme « les plus pertinents » (vous pouvez également utiliser un filtre de prédiction pour afficher les éléments « non pertinents »). Lorsque vous appliquez le filtre de prédiction, vous spécifiez une plage de scores de prédiction à filtrer. La plage de scores de prédiction est comprise entre **0** et **1**, **0** étant « non pertinent » et **1** pertinent. En général, les éléments dont les scores de prédiction sont compris entre **0** et **0,5** sont considérés comme « non pertinents » et les éléments dont les scores de prédiction sont compris entre **0,5** et **1** sont considérés comme pertinents.

   Pour plus d’informations, consultez [Appliquer un filtre de prédiction à un jeu de révision](predictive-coding-apply-prediction-filter.md).

4. **Effectuez d’autres cycles d’entraînement jusqu’à ce que le modèle se stabilise**. Vous pouvez effectuer des séries supplémentaires d’entraînement si vous souhaitez créer un modèle avec une plus grande précision de prédiction et des taux de rappel accrus. *Le taux de rappel* mesure la proportion d’éléments que le modèle prédit était pertinent parmi les éléments qui sont réellement pertinents (celles que vous avez marquées comme pertinentes lors de l’entraînement). Le score du taux de rappel est compris entre **0** et **1**. Un score plus proche de **1** indique que le modèle identifiera des éléments plus pertinents. Dans un nouveau cycle d’entraînement, vous étiquetez des éléments supplémentaires dans un nouveau jeu d’entraînement. Une fois que vous avez terminé cette série d’entraînement, le modèle est mis à jour en fonction des nouveaux apprentissages de votre dernière série d’éléments d’étiquetage dans le jeu d’apprentissage. Le modèle traitera à nouveau les éléments du jeu de révision et appliquera de nouveaux scores de prédiction. Vous pouvez continuer à effectuer des cycles d’entraînement jusqu’à ce que votre modèle se stabilise. Un modèle est considéré comme stabilisé lorsque le taux d’activité après la dernière série d’entraînements est inférieur à 5 %. *Le taux d’attrition* est défini comme pourcentage d’éléments dans un jeu de révision où le score de prédiction a changé entre les cycles d’entraînement. Le tableau de bord de codage prédictif affiche des informations et des statistiques qui vous aident à évaluer la stabilité d’un modèle.

5. **Appliquez le filtre de score de prédiction « final » pour passer en revue les éléments définis afin de hiérarchiser la révision**. Une fois que vous avez terminé toutes les séries d’entraînement et stabilisé le modèle, la dernière étape consiste à appliquer le score de prédiction final à l’ensemble de révision pour hiérarchiser la révision des éléments pertinents et non pertinents. Il s’agit de la même tâche que celle que vous avez effectuée à l’étape 3, mais à ce stade, le modèle est stable et vous n’envisagez pas d’exécuter d’autres cycles d’entraînement.
