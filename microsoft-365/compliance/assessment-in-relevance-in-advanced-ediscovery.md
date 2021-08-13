---
title: Comprendre l’évaluation en pertinence dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 1d33d4fb-91ed-41c0-b72e-5a26eca3a2a7
description: Obtenez une vue d’ensemble de l’étape d’évaluation et de son rôle dans la détermination de la richesse des problèmes lors de l’entraînement Pertinence Microsoft 365 Advanced eDiscovery.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c3965d15f64559da51b2071679913f02979d89f83db6124703c0d393608effe4
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53808571"
---
# <a name="assessment-in-the-relevance-module-in-advanced-ediscovery"></a>Évaluation dans le module de pertinence dans Advanced eDiscovery
  
Advanced eDiscovery permet une évaluation anticipée, par exemple, pour les problèmes définis et les données importées pour un cas. Advanced eDiscovery permet à l’expert de prendre des décisions sur une approche adoptée et d’appliquer ces décisions au projet de révision de document.
  
## <a name="understanding-assessment"></a>Comprendre l’évaluation

Dans Évaluation, l’expert examine un ensemble aléatoire d’au moins 500 fichiers, qui sont utilisés pour déterminer la richesse des problèmes et pour produire des statistiques qui reflètent les résultats de la formation. L’évaluation réussit lorsque suffisamment de fichiers pertinents sont trouvés pour atteindre un niveau statistique qui vous aidera à Advanced eDiscovery Pertinence afin de fournir des statistiques précises et de déterminer efficacement le point de stabilisation dans le processus de formation. 
  
Plus le nombre de fichiers pertinents dans l’ensemble d’évaluations est élevé, plus les statistiques et l’efficacité de l’algorithme de stabilité sont précises. Le nombre de fichiers pertinents dans les fichiers d’évaluation dépend de la richesse du problème. La richesse est le pourcentage estimé de fichiers pertinents dans l’ensemble pertinent pour un problème. Les problèmes avec une richesse plus élevée atteindront un nombre de fichiers pertinents plus rapidement que les problèmes moins riches. Les problèmes de très faible richesse (par exemple, 2 % ou moins) nécessitent un ensemble d’évaluations très important pour atteindre un nombre significatif de fichiers pertinents.
  
Les statistiques, qui sont présentées dans les onglets Suivi et Décision lors de la formation et après le calcul par lot, incluent des estimations de rappel pour différents ensembles de révision. Dans les statistiques, les estimations basées sur un ensemble d’exemples (dans ce cas, les fichiers d’évaluation) incluent la marge d’erreur et le niveau de confiance de cette marge d’erreur. Par exemple, le rappel estimé de 80 % peut avoir une marge d’erreur de plus ou moins 5 % avec un niveau de confiance de 95 %. Cela signifie que le rappel estimé est en réalité de 75 % à 85 % et que cette estimation a une confiance de 95 %. Plus l’ensemble d’évaluations est important, plus la marge d’erreur est faible et les statistiques sont plus précises. 
  
Une fois que l’expert a passé en revue un ensemble initial de 500 fichiers d’évaluation, Pertinence peut déterminer la marge d’erreur actuelle des valeurs de rappel. La pertinence recommande également une marge d’erreur par défaut à atteindre pour optimiser l’ensemble d’évaluations. Voici quelques exemples :
  
- Si l’ensemble d’évaluations a déjà produit une marge d’erreur de plus ou moins 10 %, Pertinence vous recommande de passer à la formation (aucune révision d’évaluation supplémentaire n’est nécessaire). 

- Si l’ensemble d’évaluations a produit une marge d’erreur de plus ou moins 13 %, Pertinence peut recommander l’examen d’un autre ensemble de fichiers d’évaluation pour atteindre une marge plus petite. 

- Si la richesse est extrêmement faible, la pertinence peut recommander l’arrêt de l’évaluation même si la marge d’erreur est importante (ce qui rend les statistiques peu pratique), car l’ensemble d’évaluations nécessaire pour atteindre une marge d’erreur utile est trop grand.

Chaque problème a sa propre richesse, sa marge d’erreur actuelle et, par conséquent, le nombre estimé de fichiers d’évaluation supplémentaires. Le jeu d’évaluation suivant est créé en fonction du nombre maximal de fichiers (jusqu’à 1 000 dans un même ensemble).
  
Vous pouvez accepter les recommandations de pertinence ou ajuster la marge d’erreur actuelle en fonction de vos besoins. La marge d’erreur actuelle par défaut est déterminée pour le rappel égal ou supérieur à 75 %.
  
> [!NOTE]
> L’étape d’évaluation peut être contourné, dans l’onglet Suivi de  pertinence dans la vue étendue d’un problème, en effanant la case à cocher Évaluation par problème, puis pour « tous les problèmes ». **\>** Par conséquent, il n’y aura pas de statistiques pour ce problème. L’effacement **de la** case à cocher d’évaluation ne peut être effectué qu’avant l’évaluation. Lorsque plusieurs problèmes existent dans un cas, l’évaluation est contourné uniquement si la case à cocher est effacée pour chaque problème.
