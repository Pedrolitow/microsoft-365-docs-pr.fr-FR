---
title: Créer un modèle de codage prédictif dans eDiscovery (Premium)
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
description: Découvrez comment créer un modèle de codage prédictif dans eDiscovery (Premium). Il s’agit de la première étape de l’utilisation des fonctionnalités de Machine Learning dans eDiscovery (Premium) pour vous aider à identifier le contenu pertinent et non pertinent dans un ensemble de révisions.
ms.openlocfilehash: 86fc72ae73faf25184c5b137a0e433af8125eb54
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64942268"
---
# <a name="create-a-predictive-coding-model-preview"></a>Créer un modèle de codage prédictif (préversion)

La première étape de l’utilisation des fonctionnalités de Machine Learning du codage prédictif dans eDiscovery (Premium) consiste à créer un modèle de codage prédictif. Après avoir créé un modèle, vous pouvez l’entraîner à identifier le contenu pertinent et non pertinent dans un ensemble de révisions.

Pour passer en revue le flux de travail de codage prédictif, consultez [En savoir plus sur le codage prédictif dans eDiscovery (Premium)](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-create-a-model"></a>Avant de créer un modèle

- Un jeu de révision doit contenir au moins 2 000 éléments pour créer un modèle de codage prédictif.

- Veillez à valider toutes les collections dans le jeu de révision avant de créer un modèle. Les éléments ajoutés à un jeu de révision après la création du modèle ne sont pas traités et un score de prédiction généré par le modèle n’est pas attribué.

- Tout élément de l’ensemble de révision qui ne contient pas de texte ne sera pas traité par le modèle ni affecté de score de prédiction. Les éléments avec du texte seront inclus dans le jeu de contrôles ou un jeu d’apprentissage.

## <a name="create-a-model"></a>Créer un modèle

1. Dans le portail de conformité Microsoft Purview, ouvrez un cas eDiscovery (Premium), puis sélectionnez l’onglet **Révision des ensembles**.

2. Ouvrez un jeu de révision, puis cliquez sur **le codage prédictif AnalyticsManage** >  (préversion).

   ![Cliquez sur le menu déroulant Analyser dans l’ensemble de révision pour accéder à la page de codage prédictif.](..\media\ManagePredictiveCoding.png)

3. Dans la page **Modèles de codage prédictif (préversion),** cliquez sur **Nouveau modèle**.

4. Dans la page de menu volant, tapez un nom pour le modèle et une description facultative.

5. Si vous le souhaitez, vous pouvez configurer des paramètres avancés (en cliquant sur **Options avancées** dans la page de menu volant) liés au niveau de confiance et à la marge d’erreur. Ces paramètres affectent le nombre d’éléments inclus dans le jeu de contrôles. Le *jeu de contrôles* est utilisé pendant le processus d’entraînement pour évaluer les scores de prédiction que le modèle affecte aux éléments avec l’étiquetage que vous effectuez pendant les cycles d’entraînement. Si votre organisation a des instructions sur le niveau de confiance et la marge d’erreur pour l’examen des documents, spécifiez-les dans les zones appropriées. Sinon, utilisez les paramètres par défaut.

6. Cliquez sur **Enregistrer** pour créer le modèle.

   La préparation de votre modèle par le système prendra quelques minutes. Une fois qu’il est prêt, vous pouvez effectuer la première série d’entraînement.

## <a name="what-happens-after-you-create-a-model"></a>Que se passe-t-il après avoir créé un modèle ?

Après avoir créé un modèle, les éléments suivants se produisent en arrière-plan lors de la création et de la préparation du modèle :

- Le système calcule le nombre d’éléments pour le jeu de contrôles. Cette taille est basée sur le nombre d’éléments du jeu de révision et les paramètres du niveau de confiance et de la marge d’erreur. Les éléments du jeu de contrôles sont sélectionnés de manière aléatoire et désignés comme éléments de jeu de contrôles. Le système inclut 10 éléments du jeu de contrôles lors de la première série d’entraînement.

- Le système sélectionne au hasard 40 éléments du jeu de révision à inclure dans le jeu d’entraînement pour la première série d’entraînement. Par conséquent, la première série d’entraînement inclut 50 éléments pour l’étiquetage : 40 éléments du jeu d’apprentissage et 10 éléments du jeu de contrôles.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez créé un modèle pour un ensemble de révisions, l’étape suivante consiste à effectuer des cycles d’entraînement pour « enseigner » le modèle afin d’identifier le contenu pertinent pour votre investigation. Pour plus d’informations, consultez [Entraîner un modèle de codage prédictif](predictive-coding-train-model.md).
