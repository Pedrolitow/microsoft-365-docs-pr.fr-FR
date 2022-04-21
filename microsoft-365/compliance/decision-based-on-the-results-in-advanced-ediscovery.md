---
title: Décision basée sur les résultats dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: aed65bcd-0a4f-43e9-b5e5-b98cc376bdf8
description: Découvrez comment l’onglet Décider dans eDiscovery (Premium) fournit des données qui peuvent vous aider à déterminer la taille correcte de l’ensemble de fichiers de cas de révision.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8acd1cbd6efa821266acc3f5110a83a238841cf8
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000177"
---
# <a name="decisions-based-on-relevance-results-in-ediscovery-premium"></a>Les décisions basées sur la pertinence ont pour résultat eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]
  
Dans le module Pertinence dans eDiscovery (Premium), l’onglet Décider fournit des informations supplémentaires pour afficher et utiliser des statistiques de prise de décision pour déterminer la taille de l’ensemble de fichiers de cas de révision.
  
## <a name="using-the-decide-tab"></a>Utilisation de l’onglet Décider

![Décision de pertinence.](../media/f32fed89-f3b5-404a-90c7-ea25d2eb58a9.png)
  
Cet onglet inclut les composants suivants :
  
- **Problème** : à partir de là, vous pouvez sélectionner le problème d’intérêt dans la liste.

- **Ratio révision-rappel** : comparaisons de la révision eDiscovery (Premium) en fonction des scores de pertinence. Le point de coupure dans le graphique représente le pourcentage de fichiers à examiner, mappé à un score de pertinence. Il est utilisé dans la phase de test de pertinence et comme seuil d’exportation pour l’élimination. Le point d’interruption par défaut, pour le nombre de fichiers à examiner, est au point où l’équilibre entre rappel et précision est optimal. Le point de terminaison réel doit être déterminé par l’utilisateur en fonction des objectifs et du compromis de coût (%review) et du risque (%recall). À l’aide du curseur, vous pouvez ajuster le point de coupure et voir l’effet sur le graphique et les paramètres, lors de l’ajustement du pourcentage de fichiers pertinents à récupérer, et avant de valider une décision.

- **Paramètres : Les paramètres** Review, Recall, Next relevant et Total cost sont des statistiques calculées cumulatives relatives à l’ensemble de révisions par rapport à la collection pour l’ensemble du cas. Les définitions de ces paramètres sont les suivantes :

  - **Révision** : pourcentage de fichiers à examiner en fonction de ce seuil.

  - **Rappel** : Pourcentage de fichiers pertinents dans l’ensemble de révisions.

  - **Suivant pertinent** : Coût de révision et d’identification d’un autre fichier pertinent qui n’est pas actuellement dans l’ensemble de révision.

  - **Coût total** : coût de la révision de ce pourcentage des fichiers de cas. Les paramètres de coût peuvent être définis par le gestionnaire de cas.

  - **Distribution par score de pertinence** : les fichiers dans l’affichage gris foncé à gauche sont inférieurs au score de coupure. Un info-bulle affiche le score de pertinence et le pourcentage associé de fichiers dans le fichier de révision défini par rapport au nombre total de fichiers.

Le volet **Détails** développé affiche plus de détails. Les fichiers des figures de collection n’incluent pas de fichiers vides ou nébuleux. Les figures de fichiers familiaux représentent des fichiers qui ne sont pas chargés dans Relevance, mais qui sont toujours comptabilisés dans la famille.
