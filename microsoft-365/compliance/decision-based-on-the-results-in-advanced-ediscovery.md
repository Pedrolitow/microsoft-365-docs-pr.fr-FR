---
title: Décision basée sur les résultats de la Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: aed65bcd-0a4f-43e9-b5e5-b98cc376bdf8
description: Découvrez comment l’onglet Décider dans Advanced eDiscovery fournit des données qui peuvent vous aider à déterminer la taille correcte du jeu de révision des fichiers de cas.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b1bab0cc7460e9260dd8f7bc6b5adb90d5a06a9b0e7832b28f7d3a2cb4e35f85
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53842342"
---
# <a name="decisions-based-on-relevance-results-in-advanced-ediscovery"></a>Les décisions basées sur la pertinence entraînent Advanced eDiscovery
  
Dans le module Pertinence de Advanced eDiscovery, l’onglet Décider fournit des informations supplémentaires pour l’affichage et l’utilisation des statistiques de prise de décision pour déterminer la taille du jeu de fichiers de cas à réviser.
  
## <a name="using-the-decide-tab"></a>Utilisation de l’onglet Décider

![Décision de pertinence](../media/f32fed89-f3b5-404a-90c7-ea25d2eb58a9.png)
  
Cet onglet comprend les composants suivants :
  
- **Problème**: à partir de là, vous pouvez sélectionner le problème d’intérêt dans la liste.

- **Taux de révision/rappel :** comparaisons des Advanced eDiscovery en fonction des scores de pertinence. Le point de coupure dans le graphique représente le pourcentage de fichiers à réviser, mappé à un score de pertinence. Il est utilisé dans la phase test de pertinence et comme seuil d’exportation pour l’élimination. Le point de coupure par défaut, pour le nombre de fichiers à réviser, est au point où l’équilibre entre Rappel et Précision est optimal. Le point de coupure réel doit être déterminé par l’utilisateur en fonction des objectifs et du compromis de coût (%review) et du risque (%recall). À l’aide du curseur, vous pouvez ajuster le point de coupure et voir l’effet sur le graphique et les paramètres, lors de l’ajustement du pourcentage de fichiers pertinents à récupérer et avant de valider une décision.

- **Parameters**: Review, Recall, Next relevant and Total cost parameters are cumulative calculated statistics pertaining to the review set in relation to the collection for the entire case. Les définitions de ces paramètres sont les suivantes :

  - **Révision**: Pourcentage de fichiers à réviser en fonction de ce cutoff.

  - **Rappel**: pourcentage de fichiers pertinents dans le jeu à réviser.

  - **Pertinence suivante**: coût de révision et d’identification d’un autre fichier pertinent qui n’est pas actuellement dans l’ensemble de révision.

  - **Coût total**: coût pour la révision de ce pourcentage des fichiers de cas. Les paramètres de coût peuvent être définies par le gestionnaire de cas.

  - **Répartition par score de pertinence**: les fichiers dans l’affichage gris foncé à gauche sont inférieurs au score de seuil. Une info-conseil affiche le score de pertinence et le pourcentage connexe de fichiers dans le jeu de fichiers de révision par rapport au nombre total de fichiers.

Le volet **Détails développé** affiche plus de détails. Les fichiers dans les figures de collection n’incluent pas de fichiers vides ou nebules. Les figures de fichiers de famille représentent des fichiers qui ne sont pas chargés en Pertinence, mais qui sont toujours comptés dans le cadre de la famille.
