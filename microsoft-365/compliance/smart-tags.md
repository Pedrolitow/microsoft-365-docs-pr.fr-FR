---
title: Configurer des balises actives dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ROBOTS: NOINDEX, NOFOLLOW
description: Les balises intelligentes vous permettent d’appliquer les fonctionnalités de Machine Learning lors de l’examen du contenu dans un cas eDiscovery (Premium). Utilisez des groupes de balises actives pour afficher les résultats des modèles de détection de Machine Learning, tels que le modèle de privilège avocat-client.
ms.openlocfilehash: 9b6cf8fc596a87ccdfd1bcab8f534e3c6923df29
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67822988"
---
# <a name="set-up-smart-tags-in-ediscovery-premium"></a>Configurer des balises actives dans eDiscovery (Premium)

Les fonctionnalités de Machine Learning (ML) dans Microsoft Purview eDiscovery (Premium) peuvent vous aider à rendre le processus de décision plus efficace lors de l’examen des documents de cas dans un ensemble de révisions. Les balises intelligentes sont un moyen d’apporter les fonctionnalités ML à l’endroit où les décisions sont enregistrées : lors de l’étiquetage des documents pendant la révision. Lorsque vous créez un groupe de balises actives, les décisions qui sont le résultat du modèle ML que vous avez associé au groupe de balises actives s’affichent en ligne avec les balises du groupe de balises. Cela permet de voir les informations sur les résultats ml en ligne lorsque vous examinez des documents spécifiques.

## <a name="how-to-set-up-a-smart-tag-group"></a>Comment configurer un groupe de balises actives

1. Dans un ensemble de révisions, cliquez sur **Gérer l’ensemble de révisions** , puis sur **Gérer les balises**.

2. Cliquez sur **Ajouter un groupe de balises** , puis **sélectionnez Ajouter un groupe de balises actives**.

3. Sélectionnez le modèle ML que vous souhaitez associer au groupe de balises.
    
   Cela crée un groupe de balises et des balises *enfants N* , où *N* correspond au nombre de sorties possibles du modèle. Par exemple, le [modèle de détection des privilèges avocat-client](attorney-privilege-detection.md) a deux sorties possibles : 

   - **Positif** : permet d’étiqueter des documents qui contiennent du contenu privilégié avocat-client.
   
   - **Négatif** : permet de baliser des documents qui ne contiennent pas de contenu privilégié avocat-client.
    
    Si vous sélectionnez ce modèle, un groupe de balises avec deux balises enfants est créé (une balise enfant nommée **Positive** et l’autre **négative**) pour le jeu de révision. Dans cet exemple, chaque balise enfant correspond à l’une des sorties possibles du modèle de détection des privilèges avocat-client.

4. Si vous le souhaitez, vous pouvez renommer le groupe de balises et les balises enfants. Par exemple, vous pouvez renommer la balise **Positive** en **Privileged** et la balise **Négative** **en Not privileged**.

## <a name="how-to-use-smart-tags"></a>Comment utiliser des balises actives

Lors de l’examen d’un document, les résultats du modèle s’affichent en regard de la balise enfant appropriée. Par exemple, si vous disposez d’un groupe de balises actives pour la détection des privilèges avocat-client et que vous examinez un document potentiellement privilégié, la raison de cette conclusion s’affiche en regard de la balise appropriée. Il est important de noter que la balise n’est pas appliquée automatiquement au document. Le réviseur prend la décision de baliser le document.
