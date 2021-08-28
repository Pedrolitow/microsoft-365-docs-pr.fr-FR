---
title: Appliquer le filtre de score de prédiction aux éléments d’un jeu à réviser
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
description: Utilisez un filtre de score de prédiction pour afficher les éléments qu’un modèle de codage prédictif est prévisible comme pertinent ou non pertinent.
ms.openlocfilehash: 34a9b4da55443cae6c2334952f60b94953b0d9d4
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58567699"
---
# <a name="apply-a-prediction-score-filter-to-a-review-set-preview"></a>Appliquer un filtre de score de prédiction à un jeu à réviser (aperçu)

Après avoir créé un modèle de codage prédictif dans Advanced eDiscovery et l’avoir formé au point où il est stable, vous pouvez appliquer le filtre de score de prédiction pour afficher les éléments de jeu à réviser que le modèle a déterminés pertinents (ou non pertinents). Lorsque vous créez un modèle, un filtre de score de prédiction correspondant est également créé. Vous pouvez utiliser ce filtre pour afficher les éléments affectés d’un score de prédiction dans une plage spécifiée. En règle générale, les scores de prédiction entre **0** et **0,5** sont affectés à des éléments que le modèle a prévu ne sont pas pertinents. Les éléments attribués aux scores de prédiction entre **.5** et **1.0** sont des éléments que le modèle a prévu sont pertinents.

Voici deux façons d’utiliser le filtre de score de prédiction :

- Hiérarchiser l’examen des éléments d’un jeu à réviser que le modèle a prévu sont pertinents.

- L’annulation des éléments du jeu à réviser que le modèle a prévu n’est pas pertinente. Vous pouvez également utiliser le filtre de score de prédiction pour dé hiérarchiser l’examen des éléments non pertinents.

## <a name="before-you-apply-a-prediction-score-filter"></a>Avant d’appliquer un filtre de score de prédiction

- Créez un modèle de codage prédictif de sorte qu’un filtre de score de prédiction correspondant soit créé.

- Vous pouvez appliquer un filtre de score de prédiction après l’un des cycles de formation. Toutefois, vous pouvez attendre après avoir effectué plusieurs séries ou jusqu’à ce que le modèle soit stable avant d’utiliser le filtre de score de prédiction.

## <a name="apply-a-prediction-score-filter"></a>Appliquer un filtre de score de prédiction

1. Dans la Centre de conformité Microsoft 365, ouvrez Advanced eDiscovery cas, sélectionnez l’onglet Ensembles de révision, puis ouvrez le jeu à réviser. 

   ![Cliquez sur Filtres pour afficher la page de présentation filtres.](..\media\PredictionScoreFilter0.png)   

   Les filtres par défaut pré-chargés sont affichés en haut de la page de révision. Vous pouvez laisser ces ensembles sur **Any**.

2. Cliquez **sur Filtres** pour afficher la page de présentation **filtres.**

3. Développez la section Analyse & codage **prédictif** pour afficher un ensemble de filtres.

      ![Filtre de score de prédiction dans la section Analyse & codage prédictif.](..\media\PredictionScoreFilter1.png)

   La convention d’attribution de noms pour les filtres de score de prédiction est **le score de prédiction (nom du modèle).** Par exemple, le nom de filtre du score de prédiction pour un modèle nommé **Modèle A** est Le score de **prédiction (modèle A).**

4. Sélectionnez le filtre de score de prédiction à utiliser, puis cliquez sur **Terminé.**

5. Dans la page de jeu à réviser, cliquez sur ladown pour le filtre de score de prédiction et tapez les valeurs minimales et maximales pour la plage de score de prédiction. Par exemple, la capture d’écran suivante montre une plage de scores de prédiction entre **.5** et **1.0**.

   ![Valeurs minimales et maximales pour le filtre de score de prédiction.](..\media\PredictionScoreFilter2.png)

6. Cliquez en dehors du filtre pour appliquer automatiquement le filtre au jeu à réviser.

  Une liste de documents avec un score de prédiction dans la plage que vous avez spécifiée s’affiche sur la page du jeu à réviser. 

  > [!TIP]
  > Pour afficher le score de prédiction réel attribué à un document, vous pouvez cliquer sur l’onglet **Métadonnées** dans le volet de lecture. Les scores de prédiction pour tous les modèles du jeu à réviser sont affichés dans la propriété de métadonnées **RelevanceScores.**

## <a name="more-information"></a>Plus d’informations

- Pour plus d’informations sur l’utilisation des filtres, voir [Requête et filtrage du contenu dans un jeu à réviser.](review-set-search.md)
