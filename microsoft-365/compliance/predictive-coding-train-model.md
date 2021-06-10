---
title: Former un modèle de codage prédictif dans Advanced eDiscovery
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
ms.openlocfilehash: ef6d1cf23d6cca58f4226696bc63c1dea5816cc1
ms.sourcegitcommit: 50908a93554290ff1157b58d0a868a33e012513c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52822554"
---
# <a name="train-a-predictive-coding-model-preview"></a>Former un modèle de codage prédictif (prévisualisation)

Après avoir créé un modèle de codage prédictif dans Advanced eDiscovery, l’étape suivante consiste à effectuer la première série de formations pour former le modèle à ce qui est pertinent et non pertinent dans votre jeu à réviser. Une fois que vous avez terminé la première série de formations, vous pouvez effectuer des séries de formation suivantes pour améliorer la capacité du modèle à prévoir du contenu pertinent et non pertinent.

Pour passer en revue le flux de travail de codage prédictif, voir [En savoir plus sur le codage prédictif dans Advanced eDiscovery](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-train-a-model"></a>Avant d’entraîner un modèle

- Au cours d’une série de formations, étiquettez les éléments comme **pertinents** ou **non** pertinents en fonction de la pertinence du contenu dans le document. Ne basez pas votre décision sur les valeurs des champs de métadonnées. Par exemple, pour les messages électroniques ou Teams conversations, ne basez pas votre décision d’étiquetage sur les participants au message. 

## <a name="train-a-model-for-the-first-time"></a>Former un modèle pour la première fois

1. Dans le centre Microsoft 365 conformité, ouvrez un Advanced eDiscovery, puis sélectionnez l’onglet Ensembles **de révision.**

2. Ouvrez un jeu à réviser, puis cliquez sur **Analyse** Gérer le  >  **codage prédictif (prévisualisation).**

3. Dans la page **Modèles de codage prédictif (prévisualisation),** sélectionnez le modèle que vous souhaitez entraîner.

4. Sous **l’onglet** Vue d’ensemble, sous **La première** série, cliquez **sur Démarrer la série de formation suivante.**

   **L’onglet** Formation s’affiche et contient 50 éléments à étiqueter.

5. Examinez chaque document, puis  **sélectionnez** le bouton Pertinent ou Non pertinent en bas du volet de lecture pour l’étiqueter.

   ![Étiqueter chaque document comme pertinent ou non pertinent](..\media\TrainModel1.png)

6. Une fois que vous avez étiqueté les 50 éléments, cliquez sur **Terminer.**

    Il faudra quelques minutes au système pour « apprendre » de votre étiquetage et mettre à jour le modèle. Une fois ce processus terminé, l’état **Prêt** s’affiche pour le modèle sur la page Modèles de codage prédictif **(prévisualisation).**

## <a name="perform-additional-training-rounds"></a>Effectuer des séries de formation supplémentaires

Après avoir effectué la première série de formations, vous pouvez effectuer des séries de formation suivantes en suivant les étapes de la section précédente. La seule différence est que le nombre de la série de formations sera mis à jour sous l’onglet **Vue d’ensemble du** modèle. Par exemple, après avoir effectué la première  série de formations, vous pouvez cliquer sur Démarrer la série de formation suivante pour démarrer la deuxième série d’entraînements. Et ainsi de suite.

Chaque série de formations (celles en cours et celles qui  sont terminées) s’affiche sous l’onglet Formation du modèle. Lorsque vous sélectionnez une série d’entraînements, une page volante avec des informations et des mesures pour la série s’affiche.

## <a name="what-happens-after-you-perform-a-training-round"></a>Que se passe-t-il après avoir effectué une série de formations ?

Une fois que vous avez effectué la première série de formations, un travail est démarré et effectue les étapes suivantes :

- En fonction de la façon dont vous avez étiqueté les 40 éléments de l’ensemble de formation, le modèle apprend de votre étiquetage et se met à jour pour devenir plus précis.

- Le modèle traite ensuite chaque élément de l’ensemble de révision et affecte un score de prédiction entre **0** (non pertinent) et **1** (pertinent).  

- Le modèle affecte un score de prédiction aux 10 éléments du jeu de contrôles que vous avez étiquetés pendant la série d’entraînement. Le modèle compare le score de prédiction de ces 10 éléments à l’étiquette réelle que vous avez affectée à l’élément pendant la série de formation. Sur la base de cette comparaison, le modèle identifie la classification suivante (appelée matrice de *confusion* du jeu de contrôles) pour évaluer les performances de prévision du modèle :
  
  |          |L’élément de prévision de modèle est pertinent |L’élément de prévision de modèle n’est pas pertinent |
  |:---------|:---------|:---------|
  |**Élément d’étiquettes de relecteur pertinent**| Vrai positif| Faux positif |
  |**Élément d’étiquettes de relecteur non pertinent**| Faux négatif |Vrai négatif |
  ||||

  Sur la base de ces comparaisons, le modèle dérive des valeurs pour les mesures F-score, precision et recall et de la marge d’erreur pour chacune d’elles. Les scores pour ces mesures de performances de modèle sont affichés sur une page volante pour la série de formation. Pour obtenir une description de ces mesures, voir la référence [de codage prédictif.](predictive-coding-reference.md)

- Enfin, le modèle détermine les 50 éléments suivants qui seront utilisés pour la série de formation suivante. Cette fois, le modèle peut sélectionner 20 éléments du jeu de contrôles et 30 nouveaux éléments du jeu à réviser et les désigner en tant que groupe de formation pour la série suivante. L’échantillonnage de la série de formation suivante n’est pas uniformément échantilloné. Le modèle optimise la sélection d’échantillonnage des éléments du jeu à réviser pour sélectionner les éléments pour lesquels la prédiction est ambiguë, ce qui signifie que le score de prédiction se trouve dans la plage 0,5. Ce processus est appelé sélection *biaisée.*

### <a name="what-happens-after-you-perform-subsequent-training-rounds"></a>Que se passe-t-il après avoir effectué les séries de formation suivantes ?

Après avoir effectué les séries de formation suivantes (après la première série de formations), le modèle effectue les étapes suivantes :

- Le modèle est mis à jour en fonction des étiquettes que vous avez appliquées à l’ensemble de formation de cette série de formations.

- Le système évalue le score de prédiction du modèle sur les éléments du jeu de contrôles et vérifie si le score s’aligne sur la façon dont vous avez étiqueté les éléments dans le jeu de contrôles. L’évaluation est effectuée sur tous les éléments étiquetés à partir du jeu de contrôles pour toutes les séries de formation. Les résultats de cette évaluation sont incorporés dans le tableau de bord sous l’onglet **Vue d’ensemble** du modèle.

- Le modèle mis à jour retrait chaque élément du jeu à réviser et affectait à chaque élément un score de prédiction mis à jour.

## <a name="next-steps"></a>Prochaines étapes

Après avoir effectué la première série de formations, vous pouvez effectuer d’autres séries de formations ou appliquer le filtre de score de prédiction du modèle au jeu à réviser pour afficher les éléments que le modèle a prévu comme pertinents ou non pertinents. Pour plus d’informations, voir [Appliquer un filtre de score de prédiction à un jeu à réviser.](predictive-coding-apply-prediction-filter.md)
