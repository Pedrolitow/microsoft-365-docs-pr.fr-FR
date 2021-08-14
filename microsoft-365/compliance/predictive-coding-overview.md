---
title: Module de codage prédictif pour Advanced eDiscovery (aperçu)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Le nouveau module de codage prédictif dans Advanced eDiscovery utilise l’apprentissage automatique pour analyser les éléments d’un jeu à réviser afin de prédictive quels éléments sont pertinents pour votre cas ou votre enquête.
ms.openlocfilehash: 5588f65af5d987eb5094a605331d9efd46f8fe999b5983e5a546f19564b09f26
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53891898"
---
# <a name="learn-about-predictive-coding-in-advanced-ediscovery-preview"></a>En savoir plus sur le codage prédictif dans Advanced eDiscovery (aperçu)

Le module de codage prédictif Advanced eDiscovery utilise les fonctionnalités intelligentes d’apprentissage automatique pour vous aider à réduire la quantité de contenu à réviser. Le codage prédictif vous permet de réduire et de réduire les volumes importants de contenu de cas à un ensemble pertinent d’éléments que vous pouvez hiérarchiser pour révision. Pour ce faire, vous devez créer et former vos propres modèles de codage prédictifs qui vous aident à hiérarchiser l’examen des éléments les plus pertinents d’un jeu à réviser.

Le module de codage prédictif est conçu pour simplifier la gestion d’un modèle au sein d’un jeu à réviser et fournir une approche itérative pour former votre modèle afin de pouvoir commencer plus rapidement avec les fonctionnalités d’apprentissage automatique dans Advanced eDiscovery. Pour commencer, vous pouvez créer un modèle, étiqueter aussi peu que 50 éléments comme pertinents ou non pertinents. Le système utilise cette formation pour appliquer des scores de prévision à chaque élément du jeu à réviser. Cela vous permet de filtrer les éléments en fonction du score de prédiction, ce qui vous permet d’examiner d’abord les éléments les plus pertinents (ou non pertinents). Si vous souhaitez entraîner des modèles avec des taux de rappel et des nombres de rappels plus élevés, vous pouvez continuer à étiqueter des éléments dans les séries de formation suivantes jusqu’à ce que le modèle se stabilise.  

## <a name="the-predictive-coding-workflow"></a>Flux de travail de codage prédictif

Voici une vue d’ensemble et une description de chaque flux de travail de codage prédictif d’étape. Pour une description plus détaillée des concepts et de la terminologie du processus de codage prédictif, voir la référence [de codage prédictif.](predictive-coding-reference.md)

![Flux de travail de codage prédictif](..\media\PredictiveCodingWorkflow.png)

1. **Créez un modèle de codage prédictif dans le jeu à réviser.** La première étape consiste à créer un modèle de codage prédictif dans le jeu à réviser. Vous devez avoir au moins 2 000 éléments dans le jeu à réviser pour créer un modèle. Après avoir créé un modèle, le système détermine le nombre d’éléments à utiliser comme jeu *de contrôles.* Le jeu de contrôles est utilisé pendant le processus de formation pour évaluer les scores de prédiction que le modèle affecte aux éléments avec l’étiquetage que vous effectuez pendant les séries de formation. La taille du jeu de contrôles est basée sur le nombre d’éléments du jeu à réviser et sur le niveau de confiance et la marge de valeurs d’erreur qui sont définies lors de la création du modèle. Les éléments du jeu de contrôles ne changent jamais et ne sont pas identifiables aux utilisateurs.

   Pour plus d’informations, voir [Créer un modèle de codage prédictif.](predictive-coding-create-model.md)

2. **Terminez la première série de formation en étiqueter les éléments comme pertinents ou non pertinents.** L’étape suivante consiste à former le modèle en commençant la première série de formations. Lorsque vous démarrez une série d’entraînements, le modèle sélectionne de manière aléatoire des éléments supplémentaires dans le jeu à réviser, appelé ensemble *de formations.* Ces éléments (provenant de l’ensemble de contrôles et du jeu de formation) vous sont présentés afin que vous pouvez étiqueter chacun d’eux comme « pertinent » ou « non pertinent ». La pertinence est basée sur le contenu de l’élément et non sur les métadonnées du document. Une fois que vous avez terminé le processus d’étiquetage dans la série de formations, le modèle « apprend » en fonction de la façon dont vous avez étiqueté les éléments de l’ensemble de formation. En fonction de cette formation, le modèle traitera les éléments du jeu à réviser et appliquera un score de prédiction à chacun d’eux.

   Pour plus d’informations, [voir La formation d’un modèle de codage prédictif.](predictive-coding-train-model.md)

3. **Appliquer le filtre de score de prédiction aux éléments du jeu à réviser.** Une fois l’étape de formation précédente terminée, l’étape suivante consiste à appliquer le filtre de score de prédiction aux éléments de la révision pour afficher les éléments que le modèle a déterminés comme « les plus pertinents » (vous pouvez également utiliser un filtre de prédiction pour afficher les éléments « non pertinents »). Lorsque vous appliquez le filtre de prédiction, vous spécifiez une plage de scores de prédiction à filtrer. La plage des scores de prédiction est entre **0** et **1,** **0** étant « non pertinent » et **1** est pertinent. En règle générale, les éléments avec des scores de prédiction entre **0** et **0,5** sont considérés comme « non pertinents » et les éléments avec des scores de prédiction entre **0,5** et **1** sont considérés comme pertinents.

   Pour plus d’informations, voir [Appliquer un filtre de prédiction à un jeu à réviser.](predictive-coding-apply-prediction-filter.md)

4. **Effectuez d’autres séries de formation jusqu’à ce que le modèle se stabilise.** Vous pouvez effectuer des séries de formation supplémentaires si vous souhaitez créer un modèle avec une plus grande précision de prédiction et des taux de rappel plus élevés. *Le taux de* rappel mesure la proportion d’éléments que le modèle prévoit étaient pertinents parmi les éléments réellement pertinents (ceux que vous avez marqués comme pertinents lors de la formation). Le score de taux de rappel est de **0** à **1**. Un score plus proche de **1** indique que le modèle identifiera les éléments plus pertinents. Dans une nouvelle série de formations, vous étiquetez des éléments supplémentaires dans un nouvel ensemble de formations. Une fois que vous avez terminé cette série d’entraînements, le modèle est mis à jour en fonction des nouveaux apprentissages de votre série la plus récente d’éléments d’étiquetage dans l’ensemble de formation. Le modèle traitera à nouveau les éléments du jeu à réviser et appliquera de nouveaux scores de prédiction. Vous pouvez continuer à effectuer des séries de formation jusqu’à ce que votre modèle se stabilise. Un modèle est considéré comme stable lorsque le taux d’évolution après la dernière série de formation est inférieur à 5 %. *Le taux d’évolution* est défini comme pourcentage d’éléments dans un jeu à réviser où le score de prévision a changé entre les séries d’entraînements. Le tableau de bord de codage prédictif affiche des informations et des statistiques qui vous aident à évaluer la stabilité d’un modèle.

5. Appliquez le filtre de score de prédiction « final » pour passer en revue **les éléments de jeu afin de hiérarchiser la révision.** Une fois que vous avez terminé toutes les séries de formation et stabilisé le modèle, la dernière étape consiste à appliquer le score de prédiction final à l’ensemble de révision afin de hiérarchiser l’examen des éléments pertinents et non pertinents. Il s’agit de la même tâche que celle effectuée à l’étape 3, mais à ce stade, le modèle est stable et vous ne prévoyez pas d’exécuter d’autres séries de formation.
