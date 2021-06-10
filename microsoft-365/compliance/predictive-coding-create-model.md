---
title: Créer un modèle de codage prédictif dans Advanced eDiscovery
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
description: Découvrez comment créer un modèle de codage prédictif dans Advanced eDiscovery. Il s’agit de la première étape de l’utilisation des fonctionnalités d’apprentissage automatique dans Advanced eDiscovery pour vous aider à identifier le contenu pertinent et non pertinent dans un jeu à réviser.
ms.openlocfilehash: 7724062848d8d757fbfd3a7870853d6f2c409d84
ms.sourcegitcommit: 50908a93554290ff1157b58d0a868a33e012513c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52822571"
---
# <a name="create-a-predictive-coding-model-preview"></a>Créer un modèle de codage prédictif (prévisualisation)

La première étape de l’utilisation des fonctionnalités d’apprentissage automatique du codage prédictif dans Advanced eDiscovery consiste à créer un modèle de codage prédictif. Après avoir créé un modèle, vous pouvez l’entraîner à identifier le contenu pertinent et non pertinent dans un jeu à réviser.

Pour passer en revue le flux de travail de codage prédictif, voir [En savoir plus sur le codage prédictif dans Advanced eDiscovery](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-create-a-model"></a>Avant de créer un modèle

- Un ensemble de révision doit comprendre au moins 2 000 éléments pour créer un modèle de codage prédictif.

- Veillez à valider toutes les collections dans le jeu à réviser avant de créer un modèle. Les éléments ajoutés à un jeu à réviser après la création du modèle ne seront pas traitées et un score de prédiction généré par le modèle ne sera pas attribué.

- Tout élément du jeu à réviser qui ne contient pas de texte ne sera pas traitée par le modèle ou n’aura pas de score de prédiction. Les éléments avec du texte seront inclus dans le jeu de contrôles ou dans un groupe de formation.

## <a name="create-a-model"></a>Créer un modèle

1. Dans le centre Microsoft 365 conformité, ouvrez un Advanced eDiscovery, puis sélectionnez l’onglet Ensembles **de révision.**

2. Ouvrez un jeu à réviser, puis cliquez sur **Analyse** Gérer le  >  **codage prédictif (prévisualisation).**

   ![Cliquez sur le menu déroulant Analyser dans le jeu à réviser pour aller à la page Codage prédictif](..\media\ManagePredictiveCoding.png)

3. Dans la page **Modèles de codage prédictif (prévisualisation),** cliquez **sur Nouveau modèle.**

4. Dans la page volante, tapez un nom pour le modèle et une description facultative.

5. Si vous le souhaitez, vous pouvez configurer des paramètres avancés (en cliquant sur **Options** avancées sur la page volante) liés au niveau de confiance et à la marge d’erreur. Ces paramètres affectent le nombre d’éléments inclus dans le jeu de contrôles. Le *jeu de contrôles* est utilisé pendant le processus de formation pour évaluer les scores de prédiction que le modèle affecte aux éléments avec l’étiquetage que vous effectuez pendant les séries de formation. Si votre organisation a des recommandations sur le niveau de confiance et la marge d’erreur pour la révision des documents, spécifiez-les dans les zones appropriées. Dans le cas contraire, utilisez les paramètres par défaut.

6. Cliquez **sur Enregistrer** pour créer le modèle.

   La préparation de votre modèle prendra quelques minutes. Une fois prêt, vous pouvez effectuer la première série de formations.

## <a name="what-happens-after-you-create-a-model"></a>Que se passe-t-il après la création d’un modèle ?

Après avoir créé un modèle, les éléments suivants se produisent en arrière-plan lors de la création et de la préparation du modèle :

- Le système calcule le nombre d’éléments du jeu de contrôles. Cette taille est basée sur le nombre d’éléments du jeu à réviser et sur les paramètres du niveau de confiance et de la marge d’erreur. Les éléments du jeu de contrôles sont sélectionnés de manière aléatoire et désignés en tant qu’éléments de jeu de contrôles. Le système inclut 10 éléments du jeu de contrôles de la première série de formation.

- Le système sélectionne de manière aléatoire 40 éléments dans le jeu à réviser à inclure dans l’ensemble de formation pour la première série de formations. Par conséquent, la première série de formations inclut 50 éléments pour l’étiquetage : 40 éléments de l’ensemble de formations et 10 éléments de l’ensemble de contrôles.

## <a name="next-steps"></a>Prochaines étapes

Après avoir créé un modèle pour un groupe de révision, l’étape suivante consiste à effectuer des séries de formation pour « enseigner » le modèle afin d’identifier le contenu pertinent pour votre examen. Pour plus d’informations, [voir Formation d’un modèle de codage prédictif.](predictive-coding-train-model.md)
