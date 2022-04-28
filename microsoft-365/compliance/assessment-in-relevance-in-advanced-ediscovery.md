---
title: Comprendre l’évaluation dans la pertinence dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 1d33d4fb-91ed-41c0-b72e-5a26eca3a2a7
description: Obtenez une vue d’ensemble de l’étape d’évaluation et de son rôle dans la détermination de la richesse des problèmes lors de la formation pertinence dans Microsoft Purview eDiscovery (Premium).
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3bfd6087bbcade2c7e4d9afdcda0f47bbea6f53d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096113"
---
# <a name="assessment-in-the-relevance-module-in-ediscovery-premium"></a>Évaluation dans le module Pertinence dans eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]
  
Microsoft Purview eDiscovery (Premium) permet une évaluation précoce, par exemple, pour les problèmes définis et les données importées pour un cas. eDiscovery (Premium) permet à l’expert de prendre des décisions sur une approche adoptée et d’appliquer ces décisions au projet d’examen des documents.
  
## <a name="understanding-assessment"></a>Présentation de l’évaluation

Dans l’évaluation, l’expert examine un ensemble aléatoire d’au moins 500 fichiers, qui sont utilisés pour déterminer la richesse des problèmes et produire des statistiques qui reflètent les résultats de la formation. L’évaluation réussit lorsque suffisamment de fichiers pertinents sont trouvés pour atteindre un niveau statistique qui aidera eDiscovery (Premium) Pertinence à fournir des statistiques précises et à déterminer efficacement le point de stabilisation dans le processus de formation. 
  
Plus le nombre de fichiers pertinents dans le jeu d’évaluations est élevé, plus les statistiques et l’efficacité de l’algorithme de stabilité sont précises. Le nombre de fichiers pertinents dans les fichiers d’évaluation dépend de la richesse du problème. La richesse est le pourcentage estimé de fichiers pertinents dans l’ensemble pertinents pour un problème. Les problèmes avec une richesse plus élevée atteignent un plus grand nombre de fichiers pertinents plus rapidement que les problèmes avec une richesse inférieure. Les problèmes avec une richesse extrêmement faible (par exemple, 2 % ou moins) nécessitent un ensemble d’évaluations très volumineux pour atteindre un nombre significatif de fichiers pertinents.
  
Les statistiques, qui sont présentées dans les onglets Suivi et Décision pendant l’entraînement et après le calcul Batch, incluent des estimations de rappel pour différents jeux d’examen. Dans les statistiques, les estimations basées sur un échantillon d’ensemble (dans ce cas, les fichiers d’évaluation) incluent la marge d’erreur et le niveau de confiance de cette marge d’erreur. Par exemple, le rappel estimé de 80 % peut avoir une marge d’erreur de plus ou moins 5 % avec un niveau de confiance de 95 %. Cela signifie que le rappel estimé est en fait de 75 %-85 % et que cette estimation a une confiance de 95 %. Plus l’ensemble d’évaluations est volumineux, plus la marge d’erreur est faible et les statistiques sont plus précises. 
  
Une fois que l’expert a examiné un ensemble d’évaluations initial de 500 fichiers, la pertinence peut déterminer la marge d’erreur actuelle des valeurs de rappel. La pertinence recommandera également une marge d’erreur par défaut à atteindre pour optimiser le jeu d’évaluations. Voici quelques exemples :
  
- Si l’ensemble d’évaluations a déjà généré une marge d’erreur de plus ou moins 10 %, la pertinence recommande de passer à la formation (aucun examen d’évaluation supplémentaire n’est nécessaire). 

- Si l’ensemble d’évaluations a généré une marge d’erreur de plus ou moins 13 %, la pertinence peut recommander l’examen d’un autre ensemble de fichiers d’évaluation pour atteindre une marge inférieure. 

- Si la richesse est extrêmement faible, la pertinence peut recommander l’arrêt de l’évaluation même si la marge d’erreur est importante (ce qui rend les statistiques peu pratiques), car l’ensemble d’évaluations nécessaire pour atteindre une marge d’erreur utile est trop grand.

Chaque problème a sa propre richesse, la marge d’erreur actuelle et, par conséquent, le nombre estimé de fichiers d’évaluation supplémentaires. Le jeu d’évaluation suivant est créé en fonction du nombre maximal de fichiers (jusqu’à 1 000 dans un seul ensemble).
  
Vous pouvez accepter les recommandations de pertinence ou ajuster la marge d’erreur actuelle en fonction de vos besoins. La marge d’erreur actuelle par défaut est déterminée pour le rappel à un niveau égal ou supérieur à 75 %.
  
> [!NOTE]
> L’étape d’évaluation peut être contournée, sous l’onglet **Suivi de la pertinence \>** dans la vue développée pour un problème, en désactivant la case à cocher **Évaluation** par problème, puis pour « tous les problèmes ». Par conséquent, il n’y aura aucune statistique pour ce problème. L’effacement de la case à cocher **Évaluation** ne peut être effectué qu’avant l’évaluation. Lorsque plusieurs problèmes existent dans un cas, l’évaluation n’est contournée que si la case à cocher est désactivée pour chaque problème.
