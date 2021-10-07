---
title: Étape 3. Planifier l’intégration Microsoft 365 Defender avec votre catalogue de services SOC
description: Les principes de base de l’intégration Microsoft 365 Defender dans votre catalogue de services d’opérations de sécurité.
keywords: incidents, alertes, examiner, corrélation, attaque, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyber-attaque, secops, opérations de sécurité, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: e9a915cfb698e80756e0810963e112889bd67a66
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60157685"
---
# <a name="step-3-plan-for-microsoft-365-defender-integration-with-your-soc-catalog-of-services"></a>Étape 3. Planifier l’intégration Microsoft 365 Defender avec votre catalogue de services SOC

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Un centre d’opérations de sécurité (SOC) établi doit avoir un catalogue de services qui peuvent inclure :

- Analyse des intrusions & programmes malveillants
- Attribution et &'ingénierie inverse
- Veille contre les menaces
- Analyse
- Recherche de recherche
- Investigations
- Réponse aux incidents 
- Équipe de réponse aux incidents de sécurité de l’ordinateur (CSIRT) (qui peut être séparée de SOC) 
- Tests de conformité
- Surveillance des menaces internes & fraude
- Surveillance des incidents de sécurité & événements 
- Analyse des vulnérabilités
- Détection et réponse étendues (XDR)/Orchestration de sécurité, automation et réponse (CASER)
- Hameçonnage
- Protection contre la perte de données
- Surveillance de la marque

Étant donné Microsoft 365 Defender technologies s’étendent sur différentes fonctions, votre équipe SOC devra déterminer les rôles et responsabilités les mieux adaptés pour gérer chaque composant de Defender et s’aligner sur la fonction de service.

Les composants de Microsoft 365 Defender sont les Microsoft 365 Defender :

- **Microsoft Defender pour** l’identité (anciennement Azure Advanced Threat Protection, également appelé Azure ATP) est une solution de sécurité basée sur le cloud qui utilise les signaux des services de domaine Active Directory (AD DS) pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre les organisations.

- **Microsoft Defender pour** point de terminaison est une solution globale de sécurité de point de terminaison dans le cloud pour les appareils qui inclut des gestion des vulnérabilités et une évaluation basées sur les risques, la réduction de la surface d’attaque, une protection de nouvelle génération basée sur le comportement et basée sur le cloud, protection évolutive des points de terminaison ( PEPT), l’examen et la correction automatiques, les services de recherche gérés, les API enrichies et la gestion unifiée de la sécurité.

 - **Microsoft Defender pour Office 365** est un service de filtrage de courrier électronique basé sur le cloud qui permet de protéger les organisations contre les programmes malveillants et les virus inconnus en offrant une protection zero-day robuste et inclut des fonctionnalités permettant de protéger les organisations contre les liens dangereux en temps réel. Il offre également une gamme complète d’investigation et de recherche, de réponse et de correction, de sensibilisation et de formation, ainsi que de fonctionnalités de posture sécurisée.

- **Microsoft Cloud App Security** est un courtier de sécurité d’accès cloud (CASB) qui prend en charge différents modes de déploiement, notamment la collecte de journaux, les connecteurs d’API et le proxy inverse. Il offre une visibilité enrichie, un contrôle sur les déplacements de données et des analyses sophistiquées pour identifier et lutter contre les cybermenaces dans tous les services cloud microsoft et tiers.

Étant donné que Microsoft 365 Defender composants et technologies couvrent différentes fonctions, votre équipe SOC devra déterminer les rôles et responsabilités les plus adaptés pour gérer chaque composant de Microsoft 365 Defender et s’aligner sur la fonction de service.

Pour intégrer les fonctionnalités de Microsoft 365 Defender, vous devez affiner les services SOC. Pour plus d’informations sur les fonctionnalités de Microsoft 365 Defender, consultez les articles suivants :

- [Qu’est-ce que Microsoft Defender pour point de terminaison ?](/defender-endpoint/microsoft-defender-endpoint)
- [Qu’est-ce que Microsoft Defender pour Identity ?](/defender-for-identity/what-is)
- [Qu’est-ce que Defender pour Office 365 ?](/office-365-security/defender-for-office-365)
- [Qu’est-ce que Microsoft Cloud App Security ?](/cloud-app-security/what-is-cloud-app-security)

## <a name="next-step"></a>Étape suivante

[Étape 4. Définir Microsoft 365 Defender rôles, responsabilités et supervision](integrate-microsoft-365-defender-secops-roles.md)

