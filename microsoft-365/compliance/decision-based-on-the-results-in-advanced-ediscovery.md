---
title: Décision basée sur les résultats dans Advanced eDiscovery
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
description: Découvrez comment l’onglet décider dans Advanced eDiscovery fournit des données qui peuvent vous aider à déterminer la taille correcte de l’ensemble de révision des fichiers de cas.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7a4c2fe891a48451d9b8d852f603b225ab7b080d
ms.sourcegitcommit: 5ba0015c1554048f817fdfdc85359eee1368da64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "49769149"
---
# <a name="decisions-based-on-relevance-results-in-advanced-ediscovery"></a>Décisions basées sur les résultats de pertinence dans Advanced eDiscovery
  
Dans le module de pertinence de Advanced eDiscovery, l’onglet décider fournit des informations supplémentaires sur l’affichage et l’utilisation des statistiques d’aide à la décision pour déterminer la taille de l’ensemble de révision des fichiers de cas.
  
## <a name="using-the-decide-tab"></a>Utilisation de l’onglet décider

![Décision de pertinence](../media/f32fed89-f3b5-404a-90c7-ea25d2eb58a9.png)
  
Cet onglet comprend les composants suivants :
  
- **Problème**: à partir de là, vous pouvez sélectionner le problème d’intérêt dans la liste.

- **Review-ratio de rappel**: comparaisons de la révision eDiscovery avancée en fonction des scores de pertinence. Le point de coupure dans le graphique représente le pourcentage de fichiers à examiner, mappé à un score de pertinence. Il est utilisé dans la phase test de pertinence et en tant que seuil d’exportation pour l’élimination. Le point de démarcation par défaut, pour le nombre de fichiers à réviser, se trouve à l’endroit où l’équilibre entre rappel et précision est optimal. Le point de démarcation réel doit être déterminé par l’utilisateur en fonction des objectifs et du coût compromis (pourcentage de révision) et du risque (pourcentage de rappel). À l’aide du curseur, vous pouvez ajuster le point de coupure et observer l’effet sur le graphique et les paramètres, lors de l’ajustement du pourcentage de fichiers pertinents à extraire, et avant la validation d’une décision.

- **Paramètres**: Review, Recall, les paramètres de coût total et pertinents suivants sont des statistiques calculées cumulatives relatives au jeu de révision en relation avec la collection pour l’ensemble du cas. Les définitions de ces paramètres sont les suivantes :

  - **Révision**: pourcentage de fichiers à vérifier en fonction de ce seuil de troncature.

  - **Rappel**: pourcentage de fichiers pertinents dans l’ensemble de révision.

  - **Suivant**: coût de révision et d’identification d’un autre fichier pertinent qui n’est pas actuellement dans l’ensemble de révision.

  - **Coût total**: coût de révision de ce pourcentage des fichiers de cas. Les paramètres de coût des paramètres peuvent être définis par le gestionnaire de cas.

  - **Répartition par score de pertinence**: les fichiers dans l’affichage gris foncé vers la gauche sont en dessous du score de coupure. Une info-bulle affiche le score de pertinence et le pourcentage de fichiers correspondant dans le jeu de fichiers de révision en relation avec le nombre total de fichiers.

Le volet de **Détails** étendu affiche plus de détails. Les fichiers dans les figures de collection n’incluent pas les fichiers vides ou nebulous. Les figures des fichiers de famille représentent des fichiers qui ne sont pas chargés en pertinence, mais qui sont toujours comptés dans le cadre de la famille.
