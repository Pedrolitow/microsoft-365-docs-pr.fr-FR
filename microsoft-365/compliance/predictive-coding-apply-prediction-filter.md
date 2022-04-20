---
title: Appliquer le filtre de score de prédiction à un ensemble de révisions
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
description: Utilisez un filtre de score de prédiction pour afficher les éléments qu’un modèle de codage prédictif prédit comme pertinents ou non pertinents.
ms.openlocfilehash: ab97c91196456b69f7f420ccd317747f638b4ee5
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993071"
---
# <a name="apply-a-prediction-score-filter-to-a-review-set-preview"></a>Appliquer un filtre de score de prédiction à un jeu de révision (préversion)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Après avoir créé un modèle de codage prédictif dans Microsoft Purview eDiscovery (Premium) et l’avoir entraîné jusqu’au point où il est stable, vous pouvez appliquer le filtre de score de prédiction pour afficher les éléments d’ensemble de révision que le modèle a déterminés sont pertinents (ou non pertinents). Lorsque vous créez un modèle, un filtre de score de prédiction correspondant est également créé. Vous pouvez utiliser ce filtre pour afficher les éléments auxquels un score de prédiction a été attribué dans une plage spécifiée. En général, les scores de prédiction compris entre **0** et **0,5** sont affectés à des éléments que le modèle a prédits ne sont pas pertinents. Les éléments affectés aux scores de prédiction entre **.5** et **1.0** sont des éléments que le modèle a prédits sont pertinents.

Voici deux façons d’utiliser le filtre de score de prédiction :

- Hiérarchiser la révision des éléments d’un ensemble de révisions prédit par le modèle sont pertinents.

- Les éléments d’élimination de l’ensemble d’examens que le modèle a prédit ne sont pas pertinents. Vous pouvez également utiliser le filtre de score de prédiction pour supprimer la hiérarchisation de la révision des éléments non pertinents.

## <a name="before-you-apply-a-prediction-score-filter"></a>Avant d’appliquer un filtre de score de prédiction

- Créez un modèle de codage prédictif afin qu’un filtre de score de prédiction correspondant soit créé.

- Vous pouvez appliquer un filtre de score de prédiction après l’une des séries d’entraînement. Toutefois, vous souhaiterez peut-être attendre plusieurs tours ou jusqu’à ce que le modèle soit stable avant d’utiliser le filtre de score de prédiction.

## <a name="apply-a-prediction-score-filter"></a>Appliquer un filtre de score de prédiction

1. Dans le portail de conformité Microsoft Purview, ouvrez le cas eDiscovery (Premium), sélectionnez l’onglet **Ensembles** de révision, puis ouvrez l’ensemble de révisions.

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

  > [!TIP]
  > Pour afficher le score de prédiction réel attribué à un document, vous pouvez cliquer sur l’onglet **Métadonnées** dans le volet de lecture. Les scores de prédiction pour tous les modèles du jeu de révision sont affichés dans la propriété **de métadonnées RelevanceScores** .

## <a name="more-information"></a>Plus d’informations

- Pour plus d’informations sur l’utilisation de filtres, consultez [Interroger et filtrer du contenu dans un ensemble de révisions](review-set-search.md).
