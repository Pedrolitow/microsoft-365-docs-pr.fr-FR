---
title: Configurer des balises intelligentes dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ROBOTS: NOINDEX, NOFOLLOW
description: Les balises intelligentes vous permet d’appliquer les fonctionnalités d’apprentissage automatique lors de l’examen du contenu dans Advanced eDiscovery cas. Utilisez des groupes de balises intelligentes pour afficher les résultats des modèles de détection d’apprentissage automatique, tels que le modèle de privilège client-avocat.
ms.openlocfilehash: 4b793b53001a9d03e53d9aadac1bd39d2d6c98d8ab498d91be12d9a6886e185b
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53859778"
---
# <a name="set-up-smart-tags-in-advanced-ediscovery"></a>Configurer des balises intelligentes dans Advanced eDiscovery

Les fonctionnalités d’apprentissage automatique (ML) dans Advanced eDiscovery peuvent vous aider à améliorer l’efficacité du processus de décision lors de l’examen des documents de cas dans un groupe de révision. Les balises intelligentes sont un moyen d’ML les fonctionnalités à l’endroit où les décisions sont enregistrées : lors du marquage des documents pendant la révision. Lorsque vous créez un groupe de balises intelligentes, les décisions qui résultent du modèle ML que vous avez associé au groupe de balises intelligentes sont affichées en ligne avec les balises du groupe de balises. Cela permet de voir les ML résultats en ligne lorsque vous examinez des documents spécifiques.

## <a name="how-to-set-up-a-smart-tag-group"></a>Comment configurer un groupe de balises intelligentes

1. Dans un jeu à réviser, cliquez sur **Gérer le jeu à réviser,** puis sur Gérer les **balises.**

2. Cliquez **sur Ajouter un groupe de balises,** puis **sélectionnez Ajouter un groupe de balises intelligentes.**

3. Sélectionnez ML modèle à associer au groupe de balises.
    
   Cela crée un groupe de balises et des balises *enfants N,* où *N* est le nombre de sorties possibles du modèle. Par exemple, le modèle [de détection des privilèges client-avocat](attorney-privilege-detection.md) a deux sorties possibles : 

   - **Positif** : utilisez cette balise pour baliser les documents qui contiennent du contenu privilégié client-avocat.
   
   - **Négatif** : utilisez cette balise pour baliser les documents qui ne contiennent pas de contenu privilégié client-avocat.
    
    Si vous sélectionnez ce modèle, un groupe de balises avec deux balises enfants est créé (une balise enfant nommée **Positive** et l’autre nommée **Negative**) pour le jeu à réviser. Dans cet exemple, chaque balise enfant correspond à l’une des sorties possibles du modèle de détection des privilèges client-avocat.

4. Si vous le souhaitez, vous pouvez renommer le groupe de balises et les balises enfants. Par exemple, vous pouvez renommer la balise **Positive** en **Privileged** et la balise **Negative** sur **Not privileged**.

## <a name="how-to-use-smart-tags"></a>Comment utiliser des balises intelligentes

Lors de la révision d’un document, les résultats du modèle s’affichent à côté de la balise enfant appropriée. Par exemple, si vous avez un groupe de balises intelligentes pour la détection des privilèges client-avocat et que vous examinez un document potentiellement privilégié, la raison de cette conclusion s’affiche à côté de la balise appropriée. Il est important de noter que la balise n’est pas appliquée automatiquement au document. Le réviseur décide de la façon de baliser le document.
