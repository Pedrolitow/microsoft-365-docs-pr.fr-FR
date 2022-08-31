---
title: Passer en revue les exigences en matière d’architecture Microsoft Defender pour point de terminaison et les concepts clés
description: Le diagramme technique de Microsoft Defender pour point de terminaison dans Microsoft 365 Defender vous aidera à comprendre l’identité dans Microsoft 365 avant de créer votre laboratoire d’essai ou votre environnement pilote.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: v-jweston
author: jweston-1
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
- highpri
ms.topic: conceptual
ms.openlocfilehash: 5a446047168394fd8506f2aaed911ce3af284f10
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67467962"
---
# <a name="review-microsoft-defender-for-endpoint-architecture-requirements-and-key-concepts"></a>Passer en revue les exigences en matière d’architecture Microsoft Defender pour point de terminaison et les concepts clés

**S’applique à :** Microsoft 365 Defender

Cet article vous guidera dans le processus de configuration de l’évaluation pour Microsoft Defender pour point de terminaison environnement.

Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-endpoint-overview.md).

Avant d’activer Microsoft Defender pour point de terminaison, veillez à bien comprendre l’architecture et à répondre aux exigences.

## <a name="understand-the-architecture"></a>Comprendre l’architecture

Le diagramme suivant illustre Microsoft Defender pour point de terminaison architecture et intégrations. 

:::image type="content" source="../../media/defender/m365-defender-endpoint-architecture.png" alt-text="Étapes d’ajout de Microsoft Defender pour Office à l’environnement d’évaluation Defender" lightbox="../../media/defender/m365-defender-endpoint-architecture.png":::

Le tableau suivant décrit l’illustration.

Appel sortant | Description
:---|:---|
1 | Les appareils sont embarqués via l’un des outils de gestion pris en charge. 
2 | Les appareils embarqués fournissent et répondent aux données de signal Microsoft Defender pour point de terminaison.
3 | Les appareils gérés sont joints et/ou inscrits dans Azure Active Directory.
4 | Les appareils Windows joints à un domaine sont synchronisés avec Azure Active Directory à l’aide d’Azure Active Directory Connect.
5 | Microsoft Defender pour point de terminaison alertes, investigations et réponses sont gérées dans Microsoft 365 Defender.

## <a name="understand-key-concepts"></a>Comprendre les concepts clés

Le tableau suivant a identifié des concepts clés importants à comprendre lors de l’évaluation, de la configuration et du déploiement de Microsoft Defender pour point de terminaison : 

Concept | Description | Plus d’informations
:---|:---|:---|
Portail d’administration | Microsoft 365 Defender portail pour surveiller et aider à répondre aux alertes de menaces persistantes avancées potentielles ou de violations de données. | [Vue d’ensemble du portail Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/portal-overview)
Réduction de la surface d’attaque | Contribuez à réduire vos surfaces d’attaque en réduisant les endroits où votre organisation est vulnérable aux cybermenaces et aux attaques. | [Vue d’ensemble de la réduction de la surface d'attaque](/microsoft-365/security/defender-endpoint/overview-attack-surface-reduction)
Détection et réponse du point de terminaison | Les fonctionnalités de détection et de réponse des points de terminaison fournissent des détections d’attaque avancées qui sont quasiment en temps réel et exploitables. | [Vue d’ensemble des fonctionnalités de détection et de réponse des points de terminaison](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
Blocage comportemental et confinement | Les fonctionnalités de blocage comportemental et d’endiguement peuvent aider à identifier et à arrêter les menaces, en fonction de leurs comportements et de leurs arborescences de traitement, même lorsque la menace a démarré l’exécution. | [Blocage et confinement comportementaux](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment)
Investigation et réponse automatisées | L’investigation automatisée utilise différents algorithmes d’inspection basés sur des processus utilisés par les analystes de sécurité et conçus pour examiner les alertes et prendre des mesures immédiates pour résoudre les violations. | [Utiliser des investigations automatisées pour examiner et corriger les menaces](/microsoft-365/security/defender-endpoint/automated-investigations)
Repérage avancé | La chasse avancée est un outil de chasse aux menaces basé sur une requête qui vous permet d’explorer jusqu’à 30 jours de données brutes afin de pouvoir inspecter de manière proactive les événements de votre réseau pour localiser les indicateurs et entités de menace. | [Vue d’ensemble de la chasse avancée](/microsoft-365/security/defender-endpoint/advanced-hunting-overview)
Analyses de menaces | L’analyse des menaces est un ensemble de rapports d’experts en sécurité Microsoft qui couvrent les menaces les plus pertinentes. | [Suivre et répondre aux menaces émergentes](/microsoft-365/security/defender-endpoint/threat-analytics)


Pour plus d’informations sur les fonctionnalités incluses dans Microsoft Defender pour point de terminaison, consultez [Ce qui est Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="siem-integration"></a>Intégration SIEM

Vous pouvez intégrer Microsoft Defender pour point de terminaison à Microsoft Sentinel pour analyser de manière plus complète les événements de sécurité au sein de votre organisation et créer des playbooks pour une réponse efficace et immédiate. 

Microsoft Defender pour point de terminaison peuvent également être intégrées à d’autres solutions SIEM (Security Information and Event Management). Pour plus d’informations, consultez [Activer l’intégration SIEM dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/enable-siem-integration).


## <a name="next-steps"></a>Prochaines étapes
[Activer l’évaluation](eval-defender-endpoint-enable-eval.md)

Revenir à la vue d’ensemble [d’Évaluer Microsoft Defender pour point de terminaison](eval-defender-endpoint-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)
