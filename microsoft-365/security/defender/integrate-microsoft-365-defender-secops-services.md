---
title: Étape 3. Planifier l’intégration Microsoft 365 Defender à votre catalogue de services SOC
description: Principes de base de l’intégration de Microsoft 365 Defender dans votre catalogue de services d’opérations de sécurité.
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
- m365-security
- m365solution-m365dsecops
- tier2
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: f9013f89e38bae603f73039191d256aa19ed47b2
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68051561"
---
# <a name="step-3-plan-for-microsoft-365-defender-integration-with-your-soc-catalog-of-services"></a>Étape 3. Planifier l’intégration Microsoft 365 Defender à votre catalogue de services SOC

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Un centre d’opérations de sécurité (SOC) établi doit avoir un catalogue de services pouvant inclure :

- Analyse des intrusions & des programmes malveillants
- Attribution & ingénierie inverse
- Renseignement sur les menaces
- Analyse
- Enquête sur la chasse
- Investigations
- Réponse aux incidents 
- Équipe de réponse aux incidents de sécurité informatique (CSIRT) (qui peut être séparée de SOC) 
- Test de conformité
- Surveillance des menaces internes & la fraude
- Surveillance des événements d’incident de sécurité & 
- Analyse des vulnérabilités
- Détection et réponse étendues (XDR)/Orchestration de sécurité, Automatisation et réponse (SOAR)
- Hameçonnage
- Protection contre la perte de données
- Surveillance de la marque

Étant donné que Microsoft 365 Defender technologies s’étendent sur différentes fonctions, votre équipe SOC doit déterminer quels rôles et responsabilités sont les mieux adaptés pour gérer chaque composant de Microsoft 365 Defender et s’aligner sur la fonction de service.

Les composants de Microsoft 365 Defender sont les suivants :

- **Microsoft Defender pour Identity** (anciennement Azure Advanced Threat Protection, également appelé Azure ATP) est une solution de sécurité basée sur le cloud qui utilise services de domaine Active Directory  Signaux (AD DS) pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre les organisations.

- **Microsoft Defender pour point de terminaison** est une solution globale de sécurité de point de terminaison fournie par le cloud pour les appareils qui inclut la gestion et l’évaluation des vulnérabilités basées sur les risques, la réduction de la surface d’attaque, la protection de nouvelle génération basée sur le comportement et le cloud, la détection et la réponse des points de terminaison (EDR), l’investigation et la correction automatiques, les services de chasse managés, les API enrichies et une gestion unifiée de la sécurité.

 - **Microsoft Defender pour Office 365** est un service de filtrage de courrier basé sur le cloud qui permet de protéger les organisations contre les programmes malveillants et les virus inconnus en fournissant une protection zero-day robuste et inclut des fonctionnalités pour protéger les organisations contre les liens dangereux en temps réel. Il offre également une gamme complète d’investigation et de chasse, de réponse et de correction, de sensibilisation et de formation, ainsi que des fonctionnalités de posture sécurisée.

- **Microsoft Defender for Cloud Apps** est un répartiteur de sécurité d’accès cloud (CASB) qui prend en charge différents modes de déploiement, notamment la collecte des journaux, les connecteurs d’API et le proxy inverse. Il offre une visibilité riche, un contrôle sur les déplacements de données et des analyses sophistiquées pour identifier et combattre les cybermenaces dans tous les services cloud Microsoft et tiers.

Étant donné que Microsoft 365 Defender composants et technologies couvrent différentes fonctions, votre équipe SOC doit déterminer quels rôles et responsabilités sont les mieux adaptés pour gérer chaque composant de Microsoft 365 Defender et s’aligner sur la fonction de service.

Pour intégrer les fonctionnalités de Microsoft 365 Defender, vous devez affiner les services SOC. Pour plus d’informations sur les fonctionnalités de Microsoft 365 Defender, consultez les articles suivants :

- [Qu’est-ce que Microsoft Defender pour point de terminaison ?](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)
- [Qu’est-ce que Microsoft Defender pour Identity ?](/defender-for-identity/what-is)
- [Qu’est-ce que Defender pour Office 365 ?](/microsoft-365/security/defender/microsoft-365-defender)
- [Qu'est-ce que Microsoft Defender pour les applications cloud ?](/cloud-app-security/what-is-cloud-app-security)

## <a name="next-step"></a>Étape suivante

[Étape 4. Définir Microsoft 365 Defender rôles, responsabilités et supervision](integrate-microsoft-365-defender-secops-roles.md)
