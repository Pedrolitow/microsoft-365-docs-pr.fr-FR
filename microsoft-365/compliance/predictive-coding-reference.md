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
localization_priority: Normal
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: ''
ms.openlocfilehash: ad9bf2ba40ede2d76246c56bf94b90e0e96aeeff
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59177899"
---
# <a name="predictive-coding-reference-preview"></a>Référence de codage prédictif (aperçu)

Cet article décrit les concepts et mesures clés de l’outil de codage prédictif dans Advanced eDiscovery. Les sections de l’article sont répertoriées par ordre alphabétique.

## <a name="confidence-level"></a>Niveau de confiance

Le niveau de confiance est un paramètre avancé lorsque vous créez un modèle de codage prédictif. Il définit que les mesures de performances du modèle (par exemple, richesse, précision et rappel) sont dans une plage spécifiée (qui détermine la marge d’erreur définie pour le modèle) qui est représentative des valeurs réelles des scores de prédiction que le modèle affecte aux éléments du jeu à réviser. Les valeurs du niveau de confiance et de la marge d’erreur permettent également de déterminer le nombre d’éléments inclus dans le jeu de contrôles. La valeur par défaut du niveau de confiance est 0,95 ou 95 %.

## <a name="control-set"></a>Jeu de contrôles

Un jeu de contrôles est utilisé pendant le processus de formation d’un modèle de codage prédictif. Le jeu de contrôles permet d’évaluer les scores de prédiction que le modèle affecte aux éléments avec l’étiquetage que vous effectuez pendant les séries d’entraînements. La taille du jeu de contrôles est basée sur le nombre d’éléments du jeu à réviser et sur le niveau de confiance et la marge de valeurs d’erreur qui sont définies lors de la création du modèle. Les éléments du jeu de contrôles ne changent jamais et ne sont pas identifiables aux utilisateurs. Le nombre total d’éléments du jeu de contrôles s’affiche sur la page volante d’une série de formations.

## <a name="control-set-confusion-matrix"></a>Matrice de confusion des ensembles de contrôles

Une fois que vous avez terminé une série d’entraînements, le modèle affecte un score de prédiction aux 10 éléments du jeu de contrôles que vous avez étiquetés au cours de la série de formation. Le modèle compare le score de prédiction de ces 10 éléments à l’étiquette réelle que vous avez affectée à l’élément au cours de la série de formation. Sur la base de cette comparaison, le modèle identifie les classifications suivantes pour évaluer les performances de prévision du modèle :

<br>

****

|Étiquette|L’élément de prévision de modèle est pertinent|L’élément de prévision de modèle n’est pas pertinent|
|---|---|---|
|**Élément d’étiquettes de relecteur selon la pertinence**|Vrai positif|Faux positif|
|**Élément d’étiquettes de relecteur non pertinent**|Faux négatif|Vrai négatif|
|

Sur la base de ces comparaisons, le modèle dérive des valeurs pour les mesures F-score, precision et recall et de la marge d’erreur pour chacune d’elles. Le nombre de chacun des types de confusion de la matrice s’affiche sur la page volante d’une série de formations.

## <a name="f-score"></a>Score F

Le score F est une moyenne pondérée des scores pour les mesures de précision et de rappel.  La plage de scores pour cette mesure est de **0** à **1**. Un score plus proche de **1** indique que le modèle détecte plus précisément les éléments pertinents. La mesure score F s’affiche dans le tableau de bord du modèle et dans la page volante de chaque série de formations.

## <a name="margin-of-error"></a>Marge d’erreur

La marge d’erreur est un paramètre avancé lorsque vous créez un mode de codage prédictif. Il spécifie le degré d’erreur dans les mesures de performances (par exemple, richesse, précision et rappel) qui est dérivé de l’échantillonnage aléatoire d’éléments dans votre jeu de contrôles. Une marge d’erreur inférieure nécessite un jeu de contrôles plus important pour s’assurer que les mesures de performances du modèle sont dans une plage plus petite. Les valeurs de la marge d’erreur et du niveau de confiance permettent également de déterminer le nombre d’éléments inclus dans le jeu de contrôles. La valeur par défaut de la marge d’erreur est 0,05 ou 5 %.

## <a name="model-stability"></a>Stabilité du modèle

La stabilité du modèle indique la capacité du modèle à prédire avec précision si un document d’un jeu à réviser est pertinent ou non. Lorsqu’un modèle est instable, d’autres séries de formation devront peut-être être effectuées pour inclure la stabilité du modèle. Lorsque le modèle est stable, il n’est pas nécessaire d’effectuer d’autres séries de formation. Le tableau de bord du modèle indique l’état actuel de la stabilité du modèle. Lorsqu’un modèle est stable, les mesures de performances ont atteint un niveau qui correspond aux paramètres du niveau de confiance et de la marge d’erreur.

## <a name="overturn-rate"></a>Taux d' rate rate

Le taux d’intérêt est le pourcentage d’éléments dans le jeu à réviser où le score de prévision a changé entre les séries d’entraînements. Un modèle est considéré comme stable lorsque le taux d’fréquence est inférieur à 5 %. La mesure de taux d’activité s’affiche sur le tableau de bord du modèle et sur la page de présentation de chaque série de formations. Le taux d’intérêt pour la première série d’entraînement est zéro, car il n’y a pas de score de prévision précédent à prévoir.

## <a name="precision"></a>Précision

La mesure de précision mesure la proportion d’éléments réellement pertinents parmi les éléments que le modèle prévoit était pertinents. Cela signifie que les éléments du jeu de contrôles où l’étiquette est pertinente par le réviseur et prévue comme pertinente par le modèle. La plage de scores pour cette mesure est de **0** à **1**. Un score plus proche de **1** indique que le modèle identifiera moins d’éléments non pertinents. La mesure de précision s’affiche sur le tableau de bord du modèle et sur la page volante de chaque série d’entraînement.

## <a name="prediction-score"></a>Score de prédiction

Il s’agit du score qu’un modèle affecte à chaque document d’un jeu à réviser. Le score est basé sur la pertinence du document par rapport à l’apprentissage du modèle à partir des séries de formation. En règle générale, les éléments avec des scores de prédiction entre **0** et **0,5** sont considérés comme non pertinents et les éléments avec des scores de prédiction entre **0,5** et **1** sont considérés comme pertinents. Le score de prédiction est contenu dans un champ de métadonnées de document. Vous pouvez utiliser un filtre de prédiction pour afficher les éléments d’un jeu à réviser qui se trouve dans une plage de prédictions spécifiée.

## <a name="recall"></a>Recall

La mesure de rappel mesure la proportion d’éléments que le modèle prévoit étaient pertinents parmi les éléments réellement pertinents. Cela signifie que les éléments du jeu de contrôles que le modèle prévu était pertinent ont également été étiquetés comme pertinents par le réviseur. La plage de scores pour cette mesure est de **0** à **1**. Un score plus proche de **1** indique que le modèle identifiera une plus grande partie des éléments pertinents. La mesure de rappel s’affiche dans le tableau de bord du modèle et dans la page volante de chaque série de formations.

## <a name="review-set"></a>Jeu à réviser

Un jeu à réviser fournit l’étendue d’un modèle de codage prédictif. Lorsque vous créez un modèle pour le jeu à réviser, les éléments du jeu de contrôles et des jeux de formation sont sélectionnés dans le jeu à réviser. Lorsque le modèle affecte des scores de prédiction, il affecte ces scores aux éléments de l’avis. Vous devez ajouter tous les éléments au jeu à réviser avant de créer un modèle de codage prédictif. Si vous ajoutez des éléments après avoir créé un modèle, ces éléments ne se voit pas attribuer de score de prédiction.

## <a name="richness"></a>Richesse

La métrique riche mesure le pourcentage d’éléments d’ensemble de révision que le modèle prévoit comme pertinents. La plage de scores pour cette mesure est de **0** à **1**. La métrique riche s’affiche dans le tableau de bord du modèle.

## <a name="sampled-items"></a>Exemples d’éléments

Le  terme éléments échantillonés est une référence à un échantillon aléatoire d’éléments d’un jeu à réviser (qui contiennent du texte) sélectionnés et associés au jeu de contrôles lorsque vous créez un modèle de codage prédictif. Un échantillon aléatoire d’éléments est également sélectionné pour chaque série de formation. Les éléments sélectionnés pour le jeu de contrôles d’un modèle ne sont jamais inclus dans un jeu de formation pour ce même modèle. L’inverse est également vrai : les éléments des ensembles de formations ne sont jamais inclus dans le jeu de contrôles.

## <a name="training-set"></a>Ensemble de formations

Le modèle sélectionne de manière aléatoire les éléments du jeu à réviser et les ajoute à un groupe de formation. Pendant une série d’entraînements, les éléments de l’ensemble de formation (en plus des éléments du jeu de contrôles) vous sont présentés afin que vous pouvez étiqueter chacun d’eux comme « pertinent » ou « non pertinent ». Ce processus d’étiquetage ou de « formation » permet au modèle de savoir comment prévoir les éléments de l’avis qui sont pertinents ou non pertinents. Chaque fois que vous effectuez une série d’entraînements, le modèle sélectionne d’autres éléments dans la révision et les ajoute au groupe de formation pour cette série de formation. Les éléments du jeu de contrôles ne sont jamais sélectionnés pour un groupe de formation.
