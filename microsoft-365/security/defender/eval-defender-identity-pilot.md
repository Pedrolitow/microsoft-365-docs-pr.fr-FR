---
title: Microsoft Defender pour Identity pilote
description: Pilotez Microsoft Defender pour Identity, définissez des benchmarks, suivez des didacticiels sur la reconnaissance, les informations d’identification compromises, le mouvement latéral, la domination du domaine et les alertes d’exfiltration, entre autres.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
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
ms.openlocfilehash: b6cf54408fff8139f1cd06a303f91c9785cca98a
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67481281"
---
# <a name="pilot-microsoft-defender-for-identity"></a>Microsoft Defender pour Identity pilote


**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 3 sur 3](eval-defender-identity-overview.md) du processus de configuration de l’environnement d’évaluation pour Microsoft Defender pour Identity. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-identity-overview.md).

Utilisez les étapes suivantes pour configurer le pilote pour Microsoft Defender pour l’identité. Notez que les recommandations n’incluent pas la configuration d’un groupe pilote. La meilleure pratique consiste à installer le capteur sur tous vos serveurs exécutant services de domaine Active Directory (AD DS) et les services fédérés Active Directory (AD FS).

:::image type="content" source="../../media/defender/m365-defender-identity-pilot-steps.png" alt-text="Étapes de pilotage Microsoft Defender pour Identity dans l’environnement d’évaluation Microsoft Defender" lightbox="../../media/defender/m365-defender-identity-pilot-steps.png":::

Le tableau suivant décrit les étapes de l’illustration.

- [Étape 1 : Configurer des recommandations de benchmark pour votre environnement d’identité](#step-1-configure-benchmark-recommendations-for-your-identity-environment)
- [Étape 2 : Tester les fonctionnalités : suivez des didacticiels pour identifier et corriger différents types d’attaques ](#step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types)

## <a name="step-1-configure-benchmark-recommendations-for-your-identity-environment"></a>Étape 1. Configurer des recommandations de benchmark pour votre environnement d’identité

Microsoft fournit des recommandations de benchmark de sécurité pour les clients qui utilisent les services cloud Microsoft. Le [benchmark de sécurité Azure](/security/benchmark/azure/overview) (ASB) fournit des bonnes pratiques et des recommandations prescriptives pour améliorer la sécurité des charges de travail, des données et des services sur Azure.

Ces recommandations de benchmark incluent la [base de référence de sécurité Azure pour Microsoft Defender pour Identity](/security/benchmark/azure/baselines/defender-for-identity-security-baseline). La planification et la mise en œuvre de ces recommandations peuvent prendre un certain temps. Bien qu’elles augmentent considérablement la sécurité de votre environnement d’identité, elles ne doivent pas vous empêcher de continuer à évaluer et à implémenter Microsoft Defender pour Identity. Ceux-ci sont fournis ici pour votre sensibilisation.

## <a name="step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types"></a>Étape 2. Tester les fonctionnalités : suivez des didacticiels pour identifier et corriger différents types d’attaques

La documentation Microsoft Defender pour Identity comprend une série de didacticiels qui vous guident dans le processus d’identification et de correction de différents types d’attaques.

Essayez les didacticiels Defender pour Identity :
- [Alertes de reconnaissance](/defender-for-identity/reconnaissance-alerts)
- [Alertes d’informations d’identification compromises](/defender-for-identity/compromised-credentials-alerts)
- [Alertes de mouvement latéral](/defender-for-identity/lateral-movement-alerts)
- [Alertes de domination de domaine](/defender-for-identity/domain-dominance-alerts)
- [Alertes d’exfiltration](/defender-for-identity/exfiltration-alerts)
- [Examiner un utilisateur](/defender-for-identity/investigate-a-user)
- [Examiner un ordinateur](/defender-for-identity/investigate-a-computer)
- [Enquêter sur les chemins de déplacement latéral](/defender-for-identity/investigate-lateral-movement-path)
- [Examiner des entités](/defender-for-identity/investigate-entity)

## <a name="next-steps"></a>Prochaines étapes

[Évaluer Microsoft Defender pour Office 365](eval-defender-office-365-overview.md)

Revenir à la vue d’ensemble [d’Évaluer Microsoft Defender pour Office 365](eval-defender-office-365-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)