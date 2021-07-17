---
title: Passer en revue les exigences en matière d’architecture de point de terminaison et les concepts clés de Microsoft Defender
description: Le diagramme technique de Microsoft Defender pour endpoint dans Microsoft 365 Defender vous aidera à comprendre l’identité dans Microsoft 365 avant de créer votre laboratoire d’évaluation ou votre environnement pilote.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: v-jweston
author: jweston-1
ms.date: 07/09/2021
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4df1ac2ca5fdfaa88ec2d08c85112f52da26b873
ms.sourcegitcommit: 718759c7146062841f7eb4a0a9a8bdddce0139b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2021
ms.locfileid: "53458129"
---
# <a name="review-microsoft-defender-for-endpoint-architecture-requirements-and-key-concepts"></a>Passer en revue les exigences en matière d’architecture de point de terminaison et les concepts clés de Microsoft Defender

**S’applique à :** Microsoft 365 Defender

Cet article vous guide dans le processus de configuration de l’évaluation de Microsoft Defender pour l’environnement Endpoint.

Pour plus d’informations sur ce processus, voir [l’article de présentation.](eval-defender-endpoint-overview.md)

Avant d’activer Microsoft Defender pour endpoint, veillez à bien comprendre l’architecture et à répondre aux exigences.

## <a name="understand-the-architecture"></a>Comprendre l’architecture

Le diagramme suivant illustre l’architecture et les intégrations de Microsoft Defender pour les points de terminaison. 

![Étapes de l’ajout de Microsoft Defender pour Office à l’environnement d’évaluation Defender](../../media/defender/m365-defender-endpoint-architecture.png)

Le tableau suivant décrit l’illustration.

Appel | Description
:---|:---|
1 | Les appareils sont pris en charge via l’un des outils de gestion pris en charge. 
2 | Les appareils connectés fournissent des données de signal de point de terminaison à Microsoft Defender et y répondent.
3 | Les appareils gérés sont joints et/ou inscrits Azure Active Directory.
4  | Les appareils joints Windows 10 domaine sont synchronisés avec les Azure Active Directory à l’Azure Active Directory Connecter.
5  | Les alertes, enquêtes et réponses de Microsoft Defender pour les points de terminaison sont gérées Microsoft 365 Defender.

## <a name="understand-key-concepts"></a>Comprendre les concepts clés

Le tableau suivant a identifié les concepts clés à comprendre lors de l’évaluation, de la configuration et du déploiement de Microsoft Defender pour Endpoint : 

Concept | Description | Plus d’informations
:---|:---|:---|
Portail d’administration | Microsoft 365 Defender portail pour surveiller et aider à répondre aux alertes d’activité de menaces persistantes potentielles ou de violations de données. | [Vue d’ensemble du portail Microsoft Defender pour points de terminaison](/defender-endpoint/portal-overview)
Réduction de la surface d’attaque | Réduisez vos surfaces d’attaque en réduisant les endroits où votre organisation est vulnérable aux cybermenaces et aux attaques. | [Vue d’ensemble de la réduction de la surface d'attaque](/defender-endpoint/overview-attack-surface-reduction)
Détection et réponse des points de terminaison | Les fonctionnalités de détection et de réponse des points de terminaison fournissent des détections d’attaques avancées quasiment en temps réel et actionnables. | [Vue d’ensemble protection évolutive des points de terminaison fonctionnalités de gestion](/defender-endpoint/overview-endpoint-detection-response)
Blocage et blocage du comportement | Les fonctionnalités de blocage comportemental et de contenu peuvent aider à identifier et à arrêter les menaces, en fonction de leurs comportements et des arbre de traitement, même lorsque la menace a démarré l’exécution. | [Blocage et confinement comportementaux](/defender-endpoint/behavioral-blocking-containment)
Examen et réponse automatisés | L’examen automatisé utilise différents algorithmes d’inspection basés sur des processus utilisés par les analystes de sécurité et conçus pour examiner les alertes et prendre des mesures immédiates pour résoudre les violations. | [Utiliser des enquêtes automatisées pour examiner et corriger les menaces](/defender-endpoint/automated-investigations)
Repérage avancé | Le recherche avancée est un outil de recherche de menace basé sur une requête qui vous permet d’explorer jusqu’à 30 jours de données brutes afin de pouvoir inspecter de manière proactive les événements de votre réseau afin de localiser les indicateurs et entités de menace. | [Vue d’ensemble du chasse avancée](/defender-endpoint/advanced-hunting-overview)
Analyses de menaces | L’analyse des menaces est un ensemble de rapports d’experts en matière de sécurité Microsoft couvrant les menaces les plus pertinentes. | [Suivre et répondre aux menaces émergentes](/defender-endpoint/threat-analytics)


Pour plus d’informations sur les fonctionnalités incluses avec Microsoft Defender pour le point de terminaison, voir Qu’est-ce [que Microsoft Defender pour point de terminaison](/defender-endpoint/microsoft-defender-endpoint).

## <a name="siem-integration"></a>Intégration SIEM

Vous pouvez intégrer Microsoft Defender pour point de terminaison à Azure Sentinel pour analyser de manière plus complète les événements de sécurité au sein de votre organisation et créer des playbooks pour obtenir une réponse efficace et immédiate. 

Microsoft Defender pour le point de terminaison peut également être intégré à d’autres solutions de gestion des événements et des informations de sécurité (SIEM). Pour plus d’informations, voir [Enable SIEM integration in Microsoft Defender for Endpoint](/defender-endpoint/enable-siem-integration).


## <a name="next-steps"></a>Étapes suivantes
[Activer l’évaluation](eval-defender-endpoint-enable-eval.md)

Revenir à la vue d’ensemble [de l’évaluation de Microsoft Defender pour le point de terminaison](eval-defender-endpoint-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md)