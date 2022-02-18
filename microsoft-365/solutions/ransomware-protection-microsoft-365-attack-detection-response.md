---
title: Étape 2. Déployer la détection et la réponse des attaques
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: rançongiciel, rançongiciel géré par l’homme, rançongiciel géré par l’homme, HumOR, attaque d'extorsion, attaque de rançongiciel, chiffrement, cryptovirologie, confiance zéro
description: Utilisez Microsoft 365 Defender et ses sources de signal de sécurité pour protéger vos ressources Microsoft 365 contre les attaques par rançongiciel.
ms.openlocfilehash: 8459d9ce8a22192d362fd8b3bf95e34c7015f08f
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2022
ms.locfileid: "62886377"
---
# <a name="step-2-deploy-attack-detection-and-response"></a>Étape 2. Déployer la détection et la réponse des attaques

Comme étape initiale fortement recommandée pour la détection et la réponse aux attaques par rançongiciel dans votre client Microsoft 365, [définissez un environnement d’évaluation](/microsoft-365/security/defender/eval-overview) pour évaluer les fonctionnalités et les capacités de Microsoft 365 Defender.

Pour plus d’informations, consultez ces ressources.

| Fonctionnalité | Description | Par où commencer | Comment l’utiliser pour la détection et la réponse |
|:-------|:-----|:-------|:-------|
| [Microsoft 365 Defender](/microsoft-365/security/defender) | Combine les signaux et orchestre les capacités en une seule solution. <br><br> Permet aux professionnels de la sécurité de combiner les signaux des menaces et de déterminer l’étendue et l’impact complets d’une menace. <br><br> Automatise les actions pour empêcher ou arrêter l’attaque et de réparer de manière spontanée les boîtes aux lettres, les points de terminaison et les identités des utilisateurs affectés. | [Prise en main](/microsoft-365/security/defender/get-started) | [Réponse aux incidents](/microsoft-365/security/defender/incidents-overview) |
| [Microsoft Defender pour l’identité](/defender-for-identity/what-is) |  Identifie, détecte et examine les menaces avancées, les identités compromises et les actions malveillantes internes ciblant votre organisation via une interface de sécurité basée sur le cloud qui utilise vos signaux Active Directory Domain Services (AD DS) locaux. | [Vue d’ensemble](/defender-for-identity/what-is) | [Travailler avec le portail Microsoft Defender pour l’identité](/defender-for-identity/workspace-portal) |
| [Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security) | Protège votre organisation contre les menaces malveillantes liées aux courriers électroniques, aux liens (URL) et aux outils de collaboration. <br><br> Protège contre les programmes malveillants, le hameçonnage, l’usurpation et d’autres types d’attaques. | [Vue d’ensemble](/microsoft-365/security/office-365-security/overview) | [Recherche de menaces](/microsoft-365/security/office-365-security/threat-hunting-in-threat-explorer) |
| [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint) | Permet la détection et la réponse aux menaces avancées sur les points de terminaison (appareils). | [Vue d’ensemble](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)  | [Détection et réponse du point de terminaison](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) |
| [Azure Active Directory Identity Protection (Azure AD)](/azure/active-directory/identity-protection/) | Automatise la détection et la correction des risques basés sur l’identité et l’examen de ces risques. | [Vue d’ensemble](/azure/active-directory/identity-protection/overview-identity-protection) | [Examiner le risque](/azure/active-directory/identity-protection/howto-identity-protection-investigate-risk) |
| [Microsoft Defender for Cloud Apps](/cloud-app-security) | Courtier de sécurité d’accès au cloud pour la découverte, l’examen et la gouvernance au sein de tous vos services cloud Microsoft et tiers. | [Vue d’ensemble](/cloud-app-security/what-is-cloud-app-security) | [Examiner](/cloud-app-security/investigate) |

>[!Note]
>Tous ces services nécessitent Microsoft 365 E5 ou Microsoft 365 E3 avec le module complémentaire Microsoft 365 E5 Sécurité.
>

Utilisez ces services pour détecter les menaces courantes suivantes des pirates de rançongiciel et y répondre :

- Vol d’informations d’identification

   - Azure AD Identity Protection
   - Defender pour l’identité
   - Defender pour Office 365

- Compromission de l’appareil

   - Defender pour point de terminaison
   - Defender pour Office 365

- Élévation de privilèges

   - Azure AD Identity Protection
   - Defender for Cloud Apps

- Comportement des applications malveillantes

   - Defender for Cloud Apps

- Exfiltration, suppression ou chargement de données

   - Defender pour Office 365
   - Defender for Cloud Apps avec les [stratégies de détection des anomalies](/cloud-app-security/anomaly-detection-policy#ransomware-activity)

Les services suivants utilisent Microsoft 365 Defender et son portail (https://security.microsoft.com) comme point d’analyse et de collecte des menaces courantes :

- Defender pour l’identité
- Defender pour Office 365
- Defender pour point de terminaison
- Defender for Cloud Apps

Microsoft 365 Defender combine les signaux de menace en alertes et les alertes connectées dans un incident afin que vos analystes de sécurité puissent détecter, examiner et corriger plus rapidement les phases d’une attaque par rançongiciel.

## <a name="resulting-configuration"></a>Configuration résultante

Voici la protection contre les rançongiciels pour votre client pour les étapes 1 et 2.

![Protection contre les rançongiciels pour votre client Microsoft 365 après l’étape 2](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step2.png)

## <a name="next-step"></a>Étape suivante

[![Étape 3 pour la protection contre les rançongiciels avec Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step3.png)](ransomware-protection-microsoft-365-identities.md)

Poursuivez avec [l’Étape 3](ransomware-protection-microsoft-365-identities.md) pour protéger les identités dans votre client Microsoft 365.
