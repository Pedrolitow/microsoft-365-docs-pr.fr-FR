---
title: Entraîner un modèle de codage prédictif dans eDiscovery (Premium)
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
ms.openlocfilehash: 3335e437a659eab984943adda31abdb344908c1c
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997645"
---
# <a name="train-a-predictive-coding-model-preview"></a>Entraîner un modèle de codage prédictif (préversion)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Après avoir créé un modèle de codage prédictif dans Microsoft Purview eDiscovery (Premium), l’étape suivante consiste à effectuer la première série d’entraînement pour entraîner le modèle sur le contenu pertinent et non pertinent dans votre jeu de révision. Une fois la première série d’entraînement terminée, vous pouvez effectuer des cycles d’entraînement ultérieurs pour améliorer la capacité du modèle à prédire le contenu pertinent et non pertinent.

Pour passer en revue le flux de travail de codage prédictif, consultez [En savoir plus sur le codage prédictif dans eDiscovery (Premium)](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-train-a-model"></a>Avant d’entraîner un modèle

- Au cours d’un cycle d’entraînement, étiqueter les éléments comme **pertinents** ou **non pertinents** en fonction de la pertinence du contenu du document. Ne basez pas votre décision sur les valeurs dans les champs de métadonnées. Par exemple, pour les e-mails ou les conversations Teams, ne basez pas votre décision d’étiquetage sur les participants au message.

## <a name="train-a-model-for-the-first-time"></a>Entraîner un modèle pour la première fois

1. Dans le portail de conformité Microsoft Purview, ouvrez un cas eDiscovery (Premium), puis sélectionnez l’onglet **Révision des ensembles**.

2. Ouvrez un jeu de révision, puis cliquez sur **le codage prédictif AnalyticsManage** >  (préversion).

3. Dans la page **Modèles de codage prédictif (préversion),** sélectionnez le modèle que vous souhaitez entraîner.

4. Sous l’onglet **Vue d’ensemble** , sous **Ronde 1**, cliquez sur **Démarrer la prochaine série d’entraînement**.

   L’onglet **Formation** s’affiche et contient 50 éléments à étiqueter.

5. Passez en revue chaque document, puis sélectionnez le bouton **Pertinent** ou **Non pertinent** en bas du volet de lecture pour l’étiqueter.

   ![Étiqueter chaque document comme pertinent ou non pertinent.](..\media\TrainModel1.png)

6. Une fois que vous avez étiqueté les 50 éléments, cliquez sur **Terminer**.

    Il faudra quelques minutes pour que le système « apprenne » à partir de votre étiquetage et met à jour le modèle. Une fois ce processus terminé, l’état **Prêt** s’affiche pour le modèle dans la page **Modèles de codage prédictif (préversion).**

## <a name="perform-additional-training-rounds"></a>Effectuer des rondes d’entraînement supplémentaires

Après avoir effectué la première série d’entraînements, vous pouvez effectuer des cycles d’entraînement suivants en suivant les étapes de la section précédente. La seule différence est que le nombre de la ronde d’entraînement sera mis à jour sous l’onglet **Vue d’ensemble** du modèle. Par exemple, après avoir effectué le premier tour d’entraînement, vous pouvez cliquer sur **Démarrer la prochaine série d’entraînement** pour démarrer la deuxième série d’entraînement. Et ainsi de suite.

Chaque cycle d’entraînement (à la fois ceux en cours et ceux qui sont terminés) s’affiche sous l’onglet **Formation** du modèle. Lorsque vous sélectionnez un tour d’entraînement, une page volante contenant des informations et des métriques pour la ronde s’affiche.

## <a name="what-happens-after-you-perform-a-training-round"></a>Que se passe-t-il après avoir effectué un tour d’entraînement ?

Une fois que vous avez effectué la première série d’entraînement, un travail qui effectue les opérations suivantes est démarré :

- En fonction de la façon dont vous avez étiqueté les 40 éléments du jeu d’apprentissage, le modèle apprend de votre étiquetage et se met à jour pour devenir plus précis.

- Le modèle traite ensuite chaque élément de l’ensemble de révision et attribue un score de prédiction compris entre **0** (non pertinent) et **1** (pertinent).

- Le modèle attribue un score de prédiction aux 10 éléments du jeu de contrôles que vous avez étiquetés pendant la phase d’entraînement. Le modèle compare le score de prédiction de ces 10 éléments avec l’étiquette réelle que vous avez affectée à l’élément pendant la phase d’entraînement. Sur la base de cette comparaison, le modèle identifie la classification suivante (appelée *matrice de confusion du jeu* de contrôles) pour évaluer les performances de prédiction du modèle :

  <br>

  ****

  |Étiquette|L’élément de prédiction de modèle est pertinent|L’élément de prédiction de modèle n’est pas pertinent|
  |---|---|---|
  |**Élément d’étiquettes de réviseur comme pertinent**|Vrai positif|Faux positif|
  |**Élément d’étiquettes de réviseur comme non pertinent**|Faux négatif|Vrai négatif|
  |

  Sur la base de ces comparaisons, le modèle dérive des valeurs pour les métriques de score F, de précision et de rappel, ainsi que la marge d’erreur pour chacune d’elles. Les scores de ces métriques de performances de modèle sont affichés sur une page volante pour la ronde d’entraînement. Pour obtenir une description de ces métriques, consultez la [référence de codage prédictif](predictive-coding-reference.md).

- Enfin, le modèle détermine les 50 éléments suivants qui seront utilisés pour la prochaine série d’entraînement. Cette fois, le modèle peut sélectionner 20 éléments dans le jeu de contrôles et 30 nouveaux éléments dans le jeu de révision et les désigner comme jeu d’entraînement pour la prochaine série. L’échantillonnage de la prochaine série d’entraînements n’est pas échantillonnée uniformément. Le modèle optimise la sélection d’échantillonnage des éléments du jeu de révision pour sélectionner les éléments dont la prédiction est ambiguë, ce qui signifie que le score de prédiction se trouve dans la plage de 0,5. Ce processus est appelé *sélection biaisée*.

### <a name="what-happens-after-you-perform-subsequent-training-rounds"></a>Que se passe-t-il après avoir effectué les cycles d’entraînement suivants ?

Une fois que vous avez effectué les cycles d’entraînement suivants (après la première série d’entraînement), le modèle effectue les opérations suivantes :

- Le modèle est mis à jour en fonction des étiquettes que vous avez appliquées à l’ensemble d’entraînement dans cette série d’entraînement.

- Le système évalue le score de prédiction du modèle sur les éléments du jeu de contrôles et vérifie si le score s’aligne sur la façon dont vous avez étiqueté les éléments dans le jeu de contrôles. L’évaluation est effectuée sur tous les éléments étiquetés du jeu de contrôles pour toutes les séries d’entraînement. Les résultats de cette évaluation sont incorporés dans le tableau de bord sous l’onglet **Vue d’ensemble** du modèle.

- Le modèle mis à jour retraite chaque élément du jeu de révision et attribue à chaque élément un score de prédiction mis à jour.

## <a name="next-steps"></a>Prochaines étapes

Après avoir effectué la première série d’entraînement, vous pouvez effectuer d’autres cycles d’entraînement ou appliquer le filtre de score de prédiction du modèle au jeu de révision pour afficher les éléments que le modèle a prédits comme pertinents ou non pertinents. Pour plus d’informations, consultez [Appliquer un filtre de score de prédiction à un jeu de révision](predictive-coding-apply-prediction-filter.md).
