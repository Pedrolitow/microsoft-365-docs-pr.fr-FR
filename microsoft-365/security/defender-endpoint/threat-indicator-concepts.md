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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ccb61bb84581ce98f0cd095b39bf53426997d4308efee4666011e9c85b9100d0
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53799705"
---
# <a name="understand-threat-intelligence-concepts"></a>Comprendre les concepts de veille des menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-threatindicator-abovefoldlink)

Les attaques de cybersécurité avancées comprennent plusieurs événements malveillants, attributs et informations contextuelles complexes. L’identification et le choix des activités éligibles comme suspectes peuvent être une tâche difficile. Votre connaissance des attributs connus et des activités anormales propres à votre secteur d’activité est fondamentale pour savoir quand appeler un comportement observé comme suspect.

Avec Microsoft Defender pour point de terminaison, vous pouvez créer des alertes contre les menaces personnalisées qui peuvent vous aider à suivre les activités d’attaques possibles dans votre organisation. Vous pouvez indicateurs d’événements suspects pour rassembler des indices et éventuellement arrêter une chaîne d’attaques. Ces alertes de menace personnalisées apparaissent uniquement dans votre organisation et indicateurs des événements que vous lui avez fixés pour suivre.

Avant de créer des alertes contre les menaces personnalisées, il est important de connaître les concepts sous-tels que les définitions d’alertes et les indicateurs de compromission et la relation entre elles.

## <a name="alert-definitions"></a>Définitions d’alerte
Les définitions d’alerte sont des attributs contextuels qui peuvent être utilisés collectivement pour identifier les indices précoces sur une possible attaque de cybersécurité. Ces indicateurs sont généralement une combinaison d’activités, de caractéristiques et d’actions entreprises par un attaquant pour atteindre l’objectif d’une attaque. La surveillance de ces combinaisons d’attributs est essentielle pour obtenir un point de garde contre les attaques et éventuellement interférer avec la chaîne d’événements avant d’atteindre l’objectif d’un attaquant.

## <a name="indicators-of-compromise-ioc"></a>Indicateurs de compromis (IOC)
Les IOC sont des événements malveillants connus individuellement qui indiquent qu’un réseau ou un appareil a déjà été enfreint. Contrairement aux définitions d’alerte, ces indicateurs sont considérés comme des preuves d’une violation. Elles sont souvent vues après qu’une attaque a déjà été effectuée et que l’objectif a été atteint, par exemple l’exfiltration. Il est également important de suivre les IOCS pendant les enquêtes d’investigation. Bien qu’il ne fournisse pas la possibilité d’intervenir avec une chaîne d’attaques, la collecte de ces indicateurs peut être utile pour créer de meilleures défenses en cas d’attaques futures possibles.

## <a name="relationship-between-alert-definitions-and-iocs"></a>Relation entre les définitions d’alerte et les IOCs
Dans le contexte de Microsoft Defender pour le point de terminaison, les définitions d’alerte sont des conteneurs pour les IOC et définissent l’alerte, y compris les métadonnées qui sont élevées en cas de correspondance d’IOC spécifique. Diverses métadonnées sont fournies dans le cadre des définitions d’alerte. Les métadonnées telles que le nom de définition d’alerte de l’attaque, la gravité et la description sont fournies avec d’autres options.

Chaque IOC définit la logique de détection concrète en fonction de son type et de sa valeur, ainsi que de son action, qui détermine la façon dont elle est mise en correspondance. Il est lié à une définition d’alerte spécifique qui définit la façon dont une détection est affichée en tant qu’alerte sur la console Microsoft Defender for Endpoint.

Voici un exemple d’IOC :
- Type : Sha1
- Valeur : 92cfceb39d57d914ed8b14d0e37643de0797ae56
- Action : est égal à

Les IOC ont une relation plusieurs-à-un avec des définitions d’alertes de telle façon qu’une définition d’alerte peut avoir de nombreux IOC qui lui correspondent.

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
:---|:---
[Tirer les détections vers vos outils SIEM](configure-siem.md)| Découvrez les différentes façons d’en tirer les détections.
[Activer l’intégration SIEM dans Microsoft Defender pour le point de terminaison](enable-siem-integration.md)| Découvrez comment activer la fonctionnalité d’intégration SIEM dans la page **Paramètres** du portail afin de pouvoir utiliser et générer les informations requises pour configurer les outils SIEM pris en charge.
[Configurer Splunk pour tirer Microsoft Defender pour les détections de points de terminaison](configure-siem.md)| Découvrez comment installer l’application REST API Modular Input et d’autres paramètres de configuration pour permettre à Splunk d’obtenir Microsoft Defender pour les détections de points de terminaison.
[Configurer HP ArcSight pour tirer microsoft Defender pour les détections de points de terminaison](configure-arcsight.md)| Découvrez comment installer le package HP ArcSight REST FlexConnector et les fichiers dont vous avez besoin pour configurer ArcSight afin d’obtenir Microsoft Defender pour les détections de points de terminaison.
[Champs Microsoft Defender pour la détection des points de terminaison](api-portal-mapping.md) | Comprendre les champs de données qui sont exposés dans le cadre de l’API d’alertes et comment ils sont map Centre de sécurité Microsoft Defender.
[Détecter Microsoft Defender pour les points de terminaison à l’aide de l’API REST](pull-alerts-using-rest-api.md) | Utilisez le flux OAuth 2.0 d’informations d’identification client pour tirer les détections de Microsoft Defender pour point de terminaison à l’aide de l’API REST.
[Résoudre des problèmes d’intégration de l’outil SIEM](troubleshoot-siem.md) | Résoudre les problèmes que vous pouvez rencontrer lors de l’utilisation de la fonctionnalité d’intégration SIEM.



## <a name="related-topics"></a>Sujets connexes
- [Gérer des indicateurs](manage-indicators.md)
