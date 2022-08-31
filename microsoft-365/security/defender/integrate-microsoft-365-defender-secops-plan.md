---
title: Étape 1. Planifier la préparation des opérations Microsoft 365 Defender
description: Principes de base de la planification de la préparation des opérations Microsoft 365 Defender lors de l’intégration de Microsoft 365 Defender dans vos opérations de sécurité.
keywords: incidents, alertes, examiner, corrélation, attaque, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyberattaque, étendues, opérations de sécurité, soc
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: e4cae3512e9f4d856dd97f04f3678ac113d0ecb6
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67483143"
---
# <a name="step-1-plan-for-microsoft-365-defender-operations-readiness"></a>Étape 1. Planifier la préparation des opérations Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Quelle que soit la maturité actuelle de vos opérations de sécurité, il est important que vous vous aligniez sur votre Centre des opérations de sécurité (SOC). Bien qu’il n’existe aucun modèle unique adapté à chaque organisation, certains aspects sont plus courants que d’autres.

Les sections suivantes décrivent les fonctions principales du SOC.

## <a name="provide-situational-awareness-of-modern-threats"></a>Sensibiliser la situation aux menaces modernes

Une équipe SOC prépare et chasse les menaces nouvelles et entrantes afin qu’elle puisse collaborer avec l’organisation pour établir des contre-mesures et des réponses. Votre équipe SOC doit disposer d’un personnel hautement formé aux méthodes et techniques d’attaque modernes et à la compréhension des acteurs des menaces. Des infrastructures et des informations sur les menaces partagées telles que [cyber-chaîne de destruction](https://www.microsoft.com/security/blog/2016/11/28/disrupting-the-kill-chain/) ou [MITRE ATT&framework CK](https://attack.mitre.org/) peuvent permettre à votre personnel d’analystes des menaces et de chasseurs de menaces.

## <a name="provide-first-second-and-potentially-third-level-responses-to-cyber-incidents-and-events"></a>Fournir des réponses de premier, de deuxième et potentiellement de troisième niveau aux cyber incidents et aux événements

Le SOC est la première ligne de défense contre les événements et incidents de sécurité. Lorsqu’un événement, une menace, une attaque, une violation de stratégie ou une recherche d’audit déclenche une alerte ou un appel à l’action, l’équipe SOC effectue une évaluation pour le trier et la contenir ou l’élever pour investigation. Par conséquent, les répondeurs de première ligne SOC doivent avoir une connaissance technique étendue des événements et des indicateurs de sécurité.

## <a name="centralize-monitoring-and-logging-of-your-organizations-security-sources"></a>Centraliser la surveillance et la journalisation des sources de sécurité de votre organisation

En règle générale, la fonction principale de l’équipe SOC est de s’assurer que tous les appareils de sécurité tels que les pare-feu, les systèmes de prévention des intrusions, les systèmes de protection contre la perte de données, les systèmes de gestion des vulnérabilités et les systèmes d’identité fonctionnent correctement et sont surveillés. Les équipes SOC travailleront avec les opérations réseau plus larges telles que l’identité, DevOps, le cloud, les applications, la science des données et d’autres équipes commerciales pour s’assurer que l’analyse des informations de sécurité est centralisée et sécurisée. En outre, l’équipe SOC est responsable de la gestion des journaux des données dans des formats utilisables et lisibles, ce qui peut inclure l’analyse et la normalisation de formats disparates.

## <a name="establish-red-blue-and-purple-team-operational-readiness"></a>Établir la préparation opérationnelle de l’équipe Rouge, Bleu et Violet

Chaque équipe soc doit tester sa préparation en réponse à un cyber incident. Les tests peuvent être effectués par le biais d’exercices de formation, tels que des tables et des exécutions de pratiques avec différentes personnes dans le domaine informatique, la sécurité et au niveau de l’entreprise. Les équipes d’exercices d’entraînement individuels sont créées en fonction de rôles représentatifs et jouent le rôle d’un défenseur (équipe bleue), d’un attaquant (Équipe Rouge) ou en tant qu’observateurs qui cherchent à améliorer les méthodes et les techniques des équipes Bleu et Rouge par le biais de forces et de faiblesses découvertes pendant l’exercice (Purple Team).

## <a name="next-step"></a>Étape suivante

[Étape 2. Effectuer une évaluation de la préparation de l’intégration SOC à l’aide de Confiance nulle Framework](integrate-microsoft-365-defender-secops-readiness.md)
