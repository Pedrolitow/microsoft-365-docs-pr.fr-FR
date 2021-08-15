---
title: Score d’exposition en Gestion des menaces et des vulnérabilités
description: Le Gestion des menaces et des vulnérabilités d’exposition reflète la vulnérabilité de votre organisation aux menaces de cybersécurité.
keywords: score d’exposition, score d’exposition de Microsoft Defender pour le point de terminaison, score d’exposition tvm de Microsoft Defender pour les points de terminaison, score d’exposition de l’organisation, score d’exposition de l’organisation tvm, Gestion des menaces et des vulnérabilités, Microsoft Defender pour le point de terminaison
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a0daf8c36a4b216cd79d43e6832816350f554b8d9e7a307649552a6bf9c97e23
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53853574"
---
# <a name="exposure-score---threat-and-vulnerability-management"></a>Score d’exposition : Gestion des menaces et des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [La gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Votre score d’exposition est visible dans le tableau de bord Gestion des vulnérabilités [menaces](tvm-dashboard-insights.md) du portail Microsoft 365 Defender web. Il reflète la vulnérabilité de votre organisation aux menaces de cybersécurité. Un faible score d’exposition signifie que vos appareils sont moins vulnérables à l’exploitation.

- Comprenez et identifiez rapidement les informations de haut niveau concernant l’état de la sécurité dans votre organisation.
- Détecter et répondre aux domaines qui nécessitent une investigation ou une action pour améliorer l’état actuel.
- Communiquer avec les homologues et la direction sur l’impact des efforts de sécurité.

La carte vous donne une vue générale de la tendance de votre score d’exposition au fil du temps. Les pics du graphique vous donnent une indication visuelle d’une exposition à une menace de cybersécurité élevée que vous pouvez examiner plus en détail.

![Carte de score d’exposition](images/tvm_exp_score.png)

## <a name="how-it-works"></a>Mode de fonctionnement

Le score d’exposition est décomposé selon les niveaux suivants :

- 0-29 : score d’exposition faible
- 30-69 : score d’exposition moyen
- 70-100 : score d’exposition élevé

Vous pouvez résoudre les problèmes en vous basant sur des [recommandations](tvm-security-recommendation.md) de sécurité prioritaires pour réduire le score d’exposition. Chaque logiciel présente des faiblesses qui sont transformées en recommandations et hiérarchisées en fonction des risques pour l’organisation.

## <a name="reduce-your-threat-and-vulnerability-exposure"></a>Réduire l’exposition aux menaces et vulnérabilités

Réduire l’exposition aux menaces et vulnérabilités en remédiant aux [recommandations de sécurité.](tvm-security-recommendation.md) Faites le plus d’impact sur votre score d’exposition en remédiant aux recommandations de sécurité les plus importantes, qui peuvent être vues dans [le tableau de bord Gestion des menaces et des vulnérabilités.](tvm-dashboard-insights.md)

## <a name="related-topics"></a>Sujets connexes

- [Vue d’ensemble gestion des vulnérabilités menaces et gestion des vulnérabilités menaces](next-gen-threat-and-vuln-mgt.md)
- [Niveau de sécurité Microsoft pour les appareils](tvm-microsoft-secure-score-devices.md)
- [Recommandations de sécurité](tvm-security-recommendation.md)
- [Chronologie des événements](threat-and-vuln-mgt-event-timeline.md)
