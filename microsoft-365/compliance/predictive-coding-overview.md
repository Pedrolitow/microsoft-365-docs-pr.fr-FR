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
description: Le nouveau module de codage prédictif dans Advanced eDiscovery utilise l’apprentissage automatique pour analyser les documents d’un jeu à réviser afin de déterminer quels documents sont pertinents pour votre cas ou votre enquête.
ms.openlocfilehash: 6a3f3b502dfe9efedc785ac3b246f60f13466dcb
ms.sourcegitcommit: ef98b8a18d275e5b5961e63d2b0743d046321737
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2021
ms.locfileid: "51382959"
---
# <a name="predictive-coding-module-for-advanced-ediscovery-preview"></a>Module de codage prédictif pour Advanced eDiscovery (aperçu)

À l’aide du nouveau module de codage prédictif dans Advanced eDiscovery, vous pouvez créer et créer un modèle pour hiérarchiser l’examen des documents en commençant par les documents les plus pertinents. To get started, you can create a model, label as few as 50 documents, and then filter documents by model prediction scores to review relevant non-relevant documents.

Voici une vue d’ensemble rapide du flux de travail :

1. Ouvrez le module de codage prédictif dans un jeu à réviser.

   ![Cliquez sur la liste de listes d’analyse dans une révision pour aller au module de codage prédictif](..\media\PredictiveCoding1.png)

2. Dans la page **Modèles de codage** prédictif, cliquez **sur Nouveau modèle** pour créer un modèle de codage prédictif.

   ![Créer un modèle](..\media\PredictiveCoding2.png)

3. Étiquetez au moins 50 documents comme **pertinents** **ou non pertinents.** Cet étiquetage est utilisé pour former le système.

   ![Étiqueter les documents comme pertinents ou non pertinents pour former le système](..\media\PredictiveCoding3.png)

4. Appliquez **le filtre de score** de prédiction pour votre modèle au jeu à réviser. Pour ce faire :

   1. Dans le jeu à réviser, cliquez sur **Filtres.**
   2. Dans la page de programme volant **Filtres,** développez la section **Analyse/ML,** puis cochez la case de **prédiction** pour le modèle que vous souhaitez appliquer.
   3. Dans le **filtre de score de prédiction,** spécifiez un score de prédiction. Le filtre affiche les documents du jeu à réviser qui correspondent au score de prédiction.

      ![Spécifier un score de prédiction pour filtrer des documents](..\media\PredictiveCoding4.png)

5. Surveillez les performances, l’état et la stabilité de votre modèle.

   ![Surveiller les performances, l’état et la stabilité de votre modèle](..\media\PredictiveCoding5.png)
