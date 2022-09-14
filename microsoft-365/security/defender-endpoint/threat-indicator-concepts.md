---
title: Comprendre les concepts de renseignement sur les menaces dans Microsoft Defender pour point de terminaison
description: Créez des alertes de menace personnalisées pour votre organisation et découvrez les concepts liés au renseignement sur les menaces dans Microsoft Defender pour point de terminaison
keywords: renseignement sur les menaces, définitions d’alerte, indicateurs de compromission, ioc
ms.service: microsoft-365-security
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
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: d22f71e732f98bc84816eee4863209905928c7a8
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67689314"
---
# <a name="understand-threat-intelligence-concepts"></a>Comprendre les concepts de veille des menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-threatindicator-abovefoldlink)

Les attaques avancées contre la cybersécurité comprennent plusieurs événements malveillants complexes, des attributs et des informations contextuelles. Il peut être difficile d’identifier et de décider laquelle de ces activités peut être considérée comme suspecte. Votre connaissance des attributs connus et des activités anormales propres à votre secteur d’activité est fondamentale pour savoir quand appeler un comportement observé comme suspect.

Avec Microsoft 365 Defender, vous pouvez créer des alertes de menace personnalisées qui peuvent vous aider à suivre les activités d’attaque possibles dans votre organisation. Vous pouvez signaler les événements suspects pour rassembler des indices et éventuellement arrêter une chaîne d’attaque. Ces alertes de menace personnalisées s’affichent uniquement dans votre organisation et signalent les événements que vous définissez pour le suivi.

Avant de créer des alertes de menace personnalisées, il est important de connaître les concepts qui sous-tendent les définitions d’alerte et les indicateurs de compromission et la relation entre elles.

## <a name="alert-definitions"></a>Définitions d’alerte
Les définitions d’alerte sont des attributs contextuels qui peuvent être utilisés collectivement pour identifier les premiers indices d’une attaque de cybersécurité possible. Ces indicateurs sont généralement une combinaison d’activités, de caractéristiques et d’actions effectuées par un attaquant pour atteindre l’objectif d’une attaque. La surveillance de ces combinaisons d’attributs est essentielle pour obtenir un point de vue sur les attaques et éventuellement interférer avec la chaîne d’événements avant que l’objectif d’un attaquant soit atteint.

## <a name="indicators-of-compromise-ioc"></a>Indicateurs de compromission (IOC)
Les E/S par E/S sont des événements malveillants connus individuellement qui indiquent qu’un réseau ou un appareil a déjà été violé. Contrairement aux définitions d’alerte, ces indicateurs sont considérés comme la preuve d’une violation. Ils sont souvent observés après qu’une attaque a déjà été effectuée et que l’objectif a été atteint, comme l’exfiltration. Il est également important de suivre les IOC pendant les investigations judiciaires. Bien qu’il ne soit peut-être pas en mesure d’intervenir avec une chaîne d’attaque, la collecte de ces indicateurs peut être utile pour créer de meilleures défenses pour d’éventuelles attaques futures.

## <a name="relationship-between-alert-definitions-and-iocs"></a>Relation entre les définitions d’alerte et les E/S par E/S
Dans le contexte de Microsoft 365 Defender et Microsoft Defender pour point de terminaison, les définitions d’alerte sont des conteneurs pour les E/S et définissent l’alerte, y compris les métadonnées déclenchées pour une correspondance IOC spécifique. Différentes métadonnées sont fournies dans le cadre des définitions d’alerte. Des métadonnées telles que le nom de définition d’alerte d’attaque, la gravité et la description sont fournies avec d’autres options.

Chaque IOC définit la logique de détection concrète en fonction de son type, de sa valeur et de son action, qui détermine comment elle est mise en correspondance. Il est lié à une définition d’alerte spécifique qui définit la façon dont une détection est affichée en tant qu’alerte sur la console Microsoft 365 Defender.

Voici un exemple d’ioc :
- Type : Sha1
- Valeur : 92cfceb39d57d914ed8b14d0e37643de0797ae56
- Action : Égal à

Les EIC ont une relation plusieurs-à-un avec les définitions d’alerte, de sorte qu’une définition d’alerte peut avoir de nombreux E/S qui lui correspondent.


## <a name="related-topics"></a>Voir aussi
- [Gérer des indicateurs](manage-indicators.md)
