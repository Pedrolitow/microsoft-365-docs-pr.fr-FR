---
title: 'Microsoft Defender Threat Intelligence (Defender TI) : Chaînage d’infrastructure'
description: Dans cet article de concept, découvrez le chaînage d’infrastructure et comment appliquer ce processus pour effectuer une analyse de l’infrastructure des menaces à l’aide de Microsoft Defender Threat Intelligence (Defender TI).
author: alexroland24
ms.author: aroland
ms.service: threat-intelligence
ms.topic: conceptual
ms.date: 08/02/2022
ms.custom: template-concept
ms.openlocfilehash: 5b094971d4004cb1c58dcf058af68c1182670f92
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2022
ms.locfileid: "67108173"
---
# <a name="infrastructure-chaining"></a>Chaînage d’infrastructure

Le chaînage d’infrastructure tire parti des relations entre les jeux de données hautement connectés pour générer une investigation. Ce processus est au cœur de l’analyse de l’infrastructure des menaces et permet aux organisations d’établir de nouvelles connexions, de regrouper des activités d’attaque similaires et d’étayer les hypothèses lors de la réponse aux incidents.

![Chaînage d’infrastructure](media/infrastructureChaining.png)

## <a name="prerequisites"></a>Configuration requise

1. Consultez [l’article de vue d’ensemble des jeux de données de Microsoft Defender Threat Intelligence (Defender TI)](data-sets.md)
2. Consultez [l’article de procédure de recherche et de pivotage de Microsoft Defender Threat Intelligence (Defender TI)](searching-and-pivoting.md)

## <a name="all-you-need-is-a-starting-point"></a>Il vous suffit d’un point de départ...

Nous voyons que les campagnes d’attaque utilisent un large éventail de techniques d’obfuscation telles que le filtrage géographique simple à des tactiques complexes telles que l’empreinte digitale passive du système d’exploitation. Cela peut potentiellement arrêter un point dans le temps d’investigation dans ses traces. La capture d’écran ci-dessus met en évidence le concept de chaînage d’infrastructure. Avec notre fonctionnalité d’enrichissement des données, nous pourrions commencer par un logiciel malveillant qui tente de se connecter à une adresse IP (éventuellement un C2). Cette adresse IP a peut-être hébergé un certificat SSL qui a un nom commun tel qu’un nom de domaine. Ce domaine peut être connecté à une page qui contient un suivi unique dans le code, tel qu’un NewRelicID ou un autre ID analytique que nous avons peut-être observé ailleurs. Ou, peut-être le domaine a-t-il été historiquement connecté à d’autres infrastructures qui pourraient éclairer notre enquête. Le principal point à retenir est qu’un point de données hors contexte peut ne pas être particulièrement utile, mais quand nous observons la connexion naturelle à toutes ces autres données techniques, nous pouvons commencer à assembler une histoire.

## <a name="an-adversarys-outside-in-perspective"></a>Perspective extérieure d’un adversaire

La perspective extérieure d’un adversaire lui permet de tirer parti de votre présence web et mobile en constante expansion qui fonctionne en dehors de votre pare-feu.

L’approche et l’interaction avec les propriétés web et mobiles en tant qu’utilisateur réel permettent à la technologie d’analyse, d’analyse et d’apprentissage automatique de Microsoft de désarmer les techniques d’évasion des adversaires en collectant des données de session utilisateur, en détectant le hameçonnage, les programmes malveillants, les applications non autorisées, le contenu indésirable et la violation de domaine à grande échelle. Cela permet de fournir des alertes et des flux de travail actionnables et basés sur des événements sous la forme d’informations sur [](reputation-scoring.md) les [menaces](what-is-microsoft-defender-threat-intelligence-defender-tI.md), de [balises système](using-tags.md), [d’insights d’analystes](analyst-insights.md) et de scores de réputation associés à l’infrastructure des adversaires.

À mesure que plus de données sur les menaces sont disponibles, davantage d’outils, d’éducation et d’efforts sont nécessaires pour que les analystes comprennent les jeux de données et leurs menaces correspondantes. Microsoft Defender Threat Intelligence (Defender TI) unifie ces efforts en fournissant une vue unique dans plusieurs sources de données.

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations, consultez [tutoriel : Collecte de renseignements sur les menaces et chaînage d’infrastructure](gathering-threat-intelligence-and-infrastructure-chaining.md).