---
title: Comprendre les concepts d’intelligence contre les menaces dans Microsoft Defender pour point de terminaison
description: Créer des alertes contre les menaces personnalisées pour votre organisation et découvrir les concepts liés à l’intelligence des menaces dans Microsoft Defender for Endpoint
keywords: intelligence contre les menaces, définitions d’alertes, indicateurs de compromis, ioc
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 0451d875f149a875872f5d5a32d3580015dbfb0e
ms.sourcegitcommit: e110f00dc6949a7a1345187375547beeb64225b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2021
ms.locfileid: "60804875"
---
# <a name="understand-threat-intelligence-concepts"></a>Comprendre les concepts de veille des menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-threatindicator-abovefoldlink)

Les attaques de cybersécurité avancées comprennent plusieurs événements malveillants complexes, attributs et informations contextuelles. L’identification et le choix des activités éligibles comme suspectes peuvent être une tâche difficile. Votre connaissance des attributs connus et des activités anormales propres à votre secteur d’activité est fondamentale pour savoir quand appeler un comportement observé comme suspect.

Avec Microsoft 365 Defender, vous pouvez créer des alertes contre les menaces personnalisées qui peuvent vous aider à suivre les activités d’attaques possibles dans votre organisation. Vous pouvez indicateurs d’événements suspects pour rassembler des indices et éventuellement arrêter une chaîne d’attaques. Ces alertes de menace personnalisées s’affichent uniquement dans votre organisation et indicateurs les événements que vous lui définissez pour suivre.

Avant de créer des alertes contre les menaces personnalisées, il est important de connaître les concepts sous-tels que les définitions d’alertes et les indicateurs de compromission et la relation entre elles.

## <a name="alert-definitions"></a>Définitions d’alerte
Les définitions d’alerte sont des attributs contextuels qui peuvent être utilisés collectivement pour identifier les indices précoces sur une possible attaque de cybersécurité. Ces indicateurs sont généralement une combinaison d’activités, de caractéristiques et d’actions entreprises par un attaquant pour atteindre l’objectif d’une attaque. La surveillance de ces combinaisons d’attributs est essentielle pour obtenir un point de garde contre les attaques et éventuellement interférer avec la chaîne d’événements avant d’atteindre l’objectif d’un attaquant.

## <a name="indicators-of-compromise-ioc"></a>Indicateurs de compromis (IOC)
Les E/S sont des événements malveillants connus individuellement qui indiquent qu’un réseau ou un appareil a déjà été enfreint. Contrairement aux définitions d’alerte, ces indicateurs sont considérés comme des preuves d’une violation. Elles sont souvent vues après qu’une attaque a déjà été effectuée et que l’objectif a été atteint, par exemple l’exfiltration. Il est également important de suivre les IOCS pendant les enquêtes d’investigation. Bien qu’il ne puisse pas intervenir avec une chaîne d’attaques, la collecte de ces indicateurs peut être utile pour créer de meilleures défenses en cas d’attaques futures.

## <a name="relationship-between-alert-definitions-and-iocs"></a>Relation entre les définitions d’alerte et les IOCs
Dans le contexte de Microsoft 365 Defender et de Microsoft Defender pour le point de terminaison, les définitions d’alerte sont des conteneurs pour les IOC et définissent l’alerte, y compris les métadonnées qui sont élevées pour une correspondance IOC spécifique. Diverses métadonnées sont fournies dans le cadre des définitions d’alerte. Les métadonnées telles que le nom de définition d’alerte de l’attaque, la gravité et la description sont fournies avec d’autres options.

Chaque IOC définit la logique de détection concrète en fonction de son type, de sa valeur et de son action, qui détermine la façon dont elle est mise en correspondance. Il est lié à une définition d’alerte spécifique qui définit la façon dont une détection est affichée en tant qu’alerte sur la console Microsoft 365 Defender.

Voici un exemple d’IOC :
- Type : Sha1
- Valeur : 92cfceb39d57d914ed8b14d0e37643de0797ae56
- Action : est égal à

Les IOC ont une relation plusieurs-à-un avec des définitions d’alertes de telle façon qu’une définition d’alerte peut avoir de nombreux IOC qui lui correspondent.


## <a name="related-topics"></a>Rubriques connexes
- [Gérer des indicateurs](manage-indicators.md)
