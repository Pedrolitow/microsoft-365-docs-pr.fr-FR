---
title: Informations de référence sur le codage prédictif
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
description: ''
ms.openlocfilehash: 2dd5b5ce984a131031101e6606b8e758864ece30
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64992851"
---
# <a name="predictive-coding-reference-preview"></a>Informations de référence sur le codage prédictif (préversion)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Cet article décrit les concepts clés et les métriques de l’outil de codage prédictif dans Microsoft Purview eDiscovery (Premium). Les sections de l’article sont répertoriées par ordre alphabétique.

## <a name="confidence-level"></a>Niveau de confiance

Le niveau de confiance est un paramètre avancé lorsque vous créez un modèle de codage prédictif. Il définit que les métriques de performances du modèle (par exemple, la richesse, la précision et le rappel) s’inscrivent dans une plage spécifiée (qui détermine la marge d’erreur définie pour le modèle) qui est représentative des valeurs vraies des scores de prédiction que le modèle affecte aux éléments du jeu de révision. Les valeurs du niveau de confiance et de la marge d’erreur permettent également de déterminer le nombre d’éléments inclus dans le jeu de contrôles. La valeur par défaut du niveau de confiance est 0,95 ou 95 %.

## <a name="control-set"></a>Jeu de contrôles

Un jeu de contrôles est utilisé pendant le processus d’entraînement d’un modèle de codage prédictif. Le jeu de contrôles consiste à évaluer les scores de prédiction que le modèle affecte aux éléments avec l’étiquetage que vous effectuez pendant les cycles d’entraînement. La taille du jeu de contrôles est basée sur le nombre d’éléments du jeu de révision et le niveau de confiance et la marge des valeurs d’erreur définies lors de la création du modèle. Les éléments du jeu de contrôles ne changent jamais et ne sont pas identifiables aux utilisateurs. Le nombre total d’éléments dans le jeu de contrôles s’affiche sur la page de menu volant pour un tour d’entraînement.

## <a name="control-set-confusion-matrix"></a>Matrice de confusion du jeu de contrôles

Une fois que vous avez terminé une série d’entraînement, le modèle attribue un score de prédiction aux 10 éléments du jeu de contrôles que vous avez étiquetés pendant la phase d’entraînement. Le modèle compare le score de prédiction de ces 10 éléments avec l’étiquette réelle que vous avez affectée à l’élément pendant la phase d’entraînement. Sur la base de cette comparaison, le modèle identifie les classifications suivantes pour évaluer les performances de prédiction du modèle :

<br>

****

|Étiquette|L’élément de prédiction de modèle est pertinent|L’élément de prédiction de modèle n’est pas pertinent|
|---|---|---|
|**Élément d’étiquettes de réviseur comme pertinent**|Vrai positif|Faux positif|
|**Élément d’étiquettes de réviseur comme non pertinent**|Faux négatif|Vrai négatif|
|

Sur la base de ces comparaisons, le modèle dérive des valeurs pour les métriques de score F, de précision et de rappel, ainsi que la marge d’erreur pour chacune d’elles. Le nombre de chacun des types de confusion de la matrice s’affiche sur la page de menu volant pour un tour d’entraînement.

## <a name="f-score"></a>F-score

Le score F est une moyenne pondérée des scores pour les métriques de précision et de rappel.  La plage de scores pour cette métrique est comprise entre **0** et **1**. Un score plus proche de **1** indique que le modèle détecte plus précisément les éléments pertinents. La métrique de score F s’affiche sur le tableau de bord du modèle et sur la page de menu volant pour chaque cycle d’entraînement.

## <a name="margin-of-error"></a>Marge d’erreur

La marge d’erreur est un paramètre avancé lorsque vous créez un mode de codage prédictif. Il spécifie le degré d’erreur dans les métriques de performances (par exemple, la richesse, la précision et le rappel) qui est dérivé de l’échantillonnage aléatoire d’éléments dans votre jeu de contrôles. Une marge d’erreur inférieure nécessite un ensemble de contrôles plus important pour garantir que les métriques de performances du modèle se situent dans une plage plus petite. Les valeurs de la marge d’erreur et du niveau de confiance permettent également de déterminer le nombre d’éléments inclus dans le jeu de contrôles. La valeur par défaut de la marge d’erreur est 0,05 ou 5 %.

## <a name="model-stability"></a>Stabilité du modèle

La stabilité du modèle indique la capacité du modèle à prédire avec précision si un document d’un ensemble de révisions est pertinent ou non pertinent. Lorsqu’un modèle est instable, d’autres cycles d’entraînement peuvent être nécessaires pour inclure la stabilité du modèle. Lorsque le modèle est stable, il n’est peut-être plus nécessaire d’effectuer des cycles d’entraînement. Le tableau de bord du modèle indique l’état actuel de la stabilité du modèle. Lorsqu’un modèle est stable, les métriques de performances ont atteint un niveau qui correspond aux paramètres du niveau de confiance et de la marge d’erreur.

## <a name="overturn-rate"></a>Taux de retournement

Le taux de basculement est le pourcentage d’éléments de l’ensemble de révision où le score de prédiction a changé entre les cycles d’entraînement. Un modèle est considéré comme stable lorsque le taux de retournement est inférieur à 5 %. La métrique de taux de retournement s’affiche sur le tableau de bord du modèle et sur la page de menu volant pour chaque cycle d’entraînement. Le taux de retournement pour le premier tour d’entraînement est égal à zéro, car il n’y a pas de score de prédiction précédent à inverser.

## <a name="precision"></a>Précision

La métrique de précision mesure la proportion d’éléments qui sont réellement pertinents parmi les éléments que le modèle a prédits étaient pertinents. Cela signifie que les éléments de l’ensemble de contrôles où l’étiquette est pertinente par le réviseur et prédites comme pertinentes par le modèle. La plage de scores pour cette métrique est comprise entre **0** et **1**. Un score plus proche de **1** indique que le modèle identifie moins d’éléments non pertinents. La métrique de précision s’affiche sur le tableau de bord du modèle et sur la page de menu volant pour chaque tour d’entraînement.

## <a name="prediction-score"></a>Score de prédiction

Il s’agit du score qu’un modèle attribue à chaque document d’un ensemble de révisions. Le score est basé sur la pertinence du document par rapport à l’apprentissage du modèle à partir des cycles d’entraînement. En général, les éléments dont les scores de prédiction sont compris entre **0** et **0,5** sont considérés comme non pertinents et les éléments dont les scores de prédiction sont compris entre **0,5** et **1** sont considérés comme pertinents. Le score de prédiction est contenu dans un champ de métadonnées de document. Vous pouvez utiliser un filtre de prédiction pour afficher les éléments d’un ensemble de révisions qui appartiennent à une plage de prédictions spécifiée.

## <a name="recall"></a>Rappeler

La métrique de rappel mesure la proportion d’éléments que le modèle prédit était pertinent parmi les éléments qui sont réellement pertinents. Cela signifie que les éléments du jeu de contrôles que le modèle prédit était pertinent ont également été étiquetés comme pertinents par le réviseur. La plage de scores pour cette métrique est comprise entre **0** et **1**. Un score plus proche de **1** indique que le modèle identifie une plus grande partie des éléments pertinents. La métrique de rappel s’affiche sur le tableau de bord du modèle et sur la page de menu volant pour chaque cycle d’entraînement.

## <a name="review-set"></a>Jeu à réviser

Un jeu de révision fournit l’étendue d’un modèle de codage prédictif. Lorsque vous créez un modèle pour le jeu de révision, les éléments du jeu de contrôles et des jeux d’apprentissage sont sélectionnés dans le jeu de révision. Lorsque le modèle affecte des scores de prédiction, il attribue ces scores aux éléments de la révision. Vous devez ajouter tous les éléments au jeu de révision avant de créer un modèle de codage prédictif. Si vous ajoutez des éléments après avoir créé un modèle, aucun score de prédiction n’est attribué à ces éléments.

## <a name="richness"></a>Richesse

La métrique de richesse mesure le pourcentage d’éléments de jeu de révision que le modèle prédit comme pertinents. La plage de scores pour cette métrique est comprise entre **0** et **1**. La métrique de richesse s’affiche dans le tableau de bord du modèle.

## <a name="sampled-items"></a>Éléments échantillonnées

Le terme *éléments échantillonnés* est une référence à un échantillon aléatoire d’éléments d’un jeu de révision (qui contiennent du texte) qui sont sélectionnés et associés au jeu de contrôles lorsque vous créez un modèle de codage prédictif. Un échantillon aléatoire d’éléments est également sélectionné pour chaque cycle d’entraînement. Les éléments sélectionnés pour le jeu de contrôles d’un modèle ne sont jamais inclus dans un jeu d’entraînement pour ce même modèle. L’inverse est également vrai : les éléments du jeu d’entraînement ne sont jamais inclus dans le jeu de contrôles.

## <a name="training-set"></a>Jeu d’entraînement

Le modèle sélectionne de manière aléatoire les éléments du jeu de révision et les ajoute à un jeu d’apprentissage. Au cours d’une ronde d’entraînement, les éléments du jeu d’entraînement (en plus des éléments du jeu de contrôles) vous sont présentés afin que vous puissiez les étiqueter comme « pertinents » ou « non pertinents ». Ce processus d’étiquetage ou de « formation » permet au modèle d’apprendre à prédire quels éléments de la révision sont pertinents ou non pertinents. Chaque fois que vous effectuez un cycle d’entraînement, le modèle sélectionne d’autres éléments dans la révision et les ajoute au jeu d’entraînement pour cette série d’entraînement. Les éléments du jeu de contrôles ne sont jamais sélectionnés pour un jeu d’entraînement.
