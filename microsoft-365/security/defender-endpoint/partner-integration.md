---
title: Scénarios et opportunités de partenaires Microsoft Defender ATP
ms.reviewer: ''
description: Découvrez comment étendre les offres de sécurité existantes en plus de l’infrastructure ouverte et d’un ensemble riche d’API pour créer des extensions et des intégrations avec Microsoft Defender ATP
keywords: API, partenaire, étendre, ouvrir une infrastructure, api, extensions, intégrations, détection, gestion, réponse, vulnérabilités, intelligence
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
ms.openlocfilehash: 7907f66bb633f22e83e165d3e3f20369f4c0f07f
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51063913"
---
# <a name="microsoft-defender-for-endpoint-partner-opportunities-and-scenarios"></a>Scénarios et opportunités de partenaires Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 


Les partenaires peuvent facilement étendre leurs offres de sécurité existantes en plus de l’infrastructure ouverte et d’un ensemble complet et complet d’API pour créer des extensions et des intégrations avec Defender for Endpoint. 

Les API couvrent des domaines fonctionnels, notamment la détection, la gestion, la réponse, les vulnérabilités et la gamme de cas d’utilisation à l’échelle de l’intelligence. En fonction du cas d’utilisation et des besoins, les partenaires peuvent soit diffuser des données, soit interroger des données à partir de Defender for Endpoint. 


## <a name="scenario-1-external-alert-correlation-and-automated-investigation-and-remediation"></a>Scénario 1 : corrélation d’alertes externes et examen et correction automatisés
Defender pour le point de terminaison offre des fonctionnalités d’investigation et de correction automatisées uniques pour stimuler la réponse aux incidents à grande échelle. 

L’intégration de la fonctionnalité d’examen et de réponse automatisée à d’autres solutions telles que des produits de sécurité réseau ou d’autres produits de sécurité de point de terminaison permettra de résoudre les alertes. L’intégration réduit également les complexités qui entourent la corrélation de signal réseau et de périphérique, rationalisant efficacement les actions d’examen et de correction des menaces sur les appareils.

Defender pour le point de terminaison ajoute la prise en charge de ce scénario sous les formes suivantes :

- Les alertes externes peuvent être poussées dans Defender pour point de terminaison et présentées côte à côte avec des alertes supplémentaires basées sur l’appareil de Defender pour le point de terminaison. Cette vue fournit le contexte complet de l’alerte, avec le processus réel et l’article complet de l’attaque.

- Une fois qu’une alerte est générée, le signal est partagé entre tous les points de terminaison protégés par Defender for Endpoint dans l’entreprise. Defender pour le point de terminaison prend immédiatement une réponse automatisée ou assistée par l’opérateur pour résoudre l’alerte.

## <a name="scenario-2-security-orchestration-and-automation-response-soar-integration"></a>Scénario 2 : intégration de l’orchestration de la sécurité et de la réponse automation (CASER)
Les solutions d’orchestration peuvent aider à créer des playbooks et à intégrer le modèle de données enrichi et les actions que les API Defender for Endpoint exposent pour orchestrer des réponses, telles que la requête de données de périphérique, déclencher l’isolation de l’appareil, bloquer/autoriser, résoudre une alerte, etc.

## <a name="scenario-3-indicators-matching"></a>Scénario 3 : correspondance des indicateurs 
L’indicateur de compromission (IoCs) est une fonctionnalité essentielle dans chaque solution de protection des points de terminaison. Cette fonctionnalité est disponible dans Defender pour point de terminaison et permet de définir une liste d’indicateurs pour la prévention, la détection et l’exclusion d’entités. Vous pouvez définir l’action à prendre ainsi que la durée de l’application de l’action.

Les scénarios ci-dessus servent d’exemples d’extensibilité de la plateforme. Vous n’êtes pas limité aux exemples et nous vous encourageons certainement à tirer parti de l’infrastructure ouverte pour découvrir et explorer d’autres scénarios.

Suivez les étapes [de l’étape](get-started-partner-integration.md) Devenir un partenaire Microsoft Defender pour Point de terminaison pour intégrer votre solution dans Defender for Endpoint.

## <a name="related-topic"></a>Rubrique connexe
- [Vue d’ensemble de la gestion et des API](management-apis.md)
