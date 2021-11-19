---
title: Protection contre les menaces (Windows 10)
description: Microsoft Defender pour point de terminaison est une plateforme de sécurité unifiée pour la protection préventive, la détection après effraction, l’examen automatisé et la réponse.
keywords: protection contre les menaces, Microsoft Defender pour le point de terminaison, réduction de la surface d’attaque, protection nouvelle génération, protection évolutive des points de terminaison, examen et réponse automatisés, experts microsoft en matière de menaces, Score de sécurité Microsoft pour les appareils, recherche avancée, recherche de cybermenace, protection contre les menaces web
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.openlocfilehash: c19189ab33fca3c537347c0d20d14d602fe99da3
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61109034"
---
# <a name="threat-protection"></a>Protection contre les menaces

[Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection) est une plateforme de sécurité unifiée pour la protection préventive, la détection après effraction, l’examen automatisé et la réponse. Defender for Endpoint protège les points de terminaison contre les cybermenaces, détecte les attaques avancées et les violations de données, automatise les incidents de sécurité et améliore la posture de sécurité.

> [!TIP]
> Permet à vos utilisateurs d’accéder facilement aux services cloud et aux applications sur site et d’activer les fonctionnalités de gestion modernes pour tous les appareils. Pour plus d’informations, voir [Sécuriser vos employés distants.](/enterprise-mobility-security/remote-work/) 

<center><h2>Microsoft Defender pour point de terminaison</center></h2>
<table>
<tr>
<td><a href="#tvm"><center><img src="images/TVM_icon.png" alt="threat and vulnerability icon"> <br><b>Menaces & gestion des vulnérabilités</b></center></a></td>
<td><a href="#asr"><center><img src="images/asr-icon.png" alt="attack surface reduction icon"> <br><b>Réduction de la surface d’attaque</b></center></a></td>
<td><center><a href="#ngp"><img src="images/ngp-icon.png" alt="next generation protection icon"><br> <b>Protection de nouvelle génération</b></a></center></td>
<td><center><a href="#edr"><img src="images/edr-icon.png" alt="endpoint detection and response icon"><br> <b>Détection et réponse des points de terminaison</b></a></center></td>
<td><center><a href="#ai"><img src="images/air-icon.png" alt="automated investigation and remediation icon"><br> <b>Examen et correction automatisés</b></a></center></td>
<td><center><a href="#mte"><img src="images/mte-icon.png" alt="microsoft threat experts icon"><br> <b>Spécialistes des menaces Microsoft</b></a></center></td>
</tr>
<tr>
<td colspan="7">
<a href="#apis"><center><b>Configuration et administration centralisées, API</a></b></center></td>
</tr>
<tr>
<td colspan="7"><a href="#mtp"><center><b>Microsoft 365 Defender</a></center></b></td>
</tr>
</table>
<br>

<a name="tvm"></a>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4obJq]

**[Menaces & gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)**<br>
Cette fonctionnalité intégrée utilise une approche basée sur le risque qui change la donne pour découvrir, hiérarchiser et corriger les vulnérabilités et erreurs de configuration des points de terminaison.

- [Vue d’ensemble & gestion des vulnérabilités menaces](next-gen-threat-and-vuln-mgt.md)
- [Prise en main](tvm-prerequisites.md)
- [Accéder à votre posture de sécurité](tvm-dashboard-insights.md)
- [Améliorer votre état de la sécurité et réduire les risques](tvm-security-recommendation.md)
- [Comprendre les vulnérabilités sur vos appareils](tvm-software-inventory.md)

<a name="asr"></a>

**[Réduction de la surface d’attaque](overview-attack-surface-reduction.md)**<br>
L’ensemble de fonctionnalités de réduction de la surface d’attaque fournit la première ligne de défense dans la pile. En veillant à ce que les paramètres de configuration soient correctement définies et que des techniques d’atténuation des attaques soient appliquées, ces fonctionnalités peuvent résister aux attaques et à l’exploitation.

- [Isolation matérielle](overview-hardware-based-isolation.md)
- [Contrôle d’application](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)
- [Contrôle des appareils](/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control)
- [Exploit Protection](exploit-protection.md)
- [Protection du réseau,](network-protection.md) [protection web](web-protection-overview.md)
- [Accès contrôlé aux dossiers](controlled-folders.md)
- [Pare-feu réseau](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)
- [Règles de réduction de la surface d’attaque](attack-surface-reduction.md)

<a name="ngp"></a>

**[Protection de nouvelle génération](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)**<br>
Pour renforcer davantage le périmètre de sécurité de votre réseau, Microsoft Defender pour point de terminaison fait appel à une protection nouvelle génération conçue pour intercepter tous les types de menaces émergentes.

- [Surveillance du comportement](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus)
- [Protection basée sur le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/configure-protection-features-microsoft-defender-antivirus)
- [Apprentissage automatique](/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus)
- [URL Protection](/windows/security/threat-protection/microsoft-defender-antivirus/configure-network-connections-microsoft-defender-antivirus)
- [Service bac à sable automatisé](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus)

<a name="edr"></a>

**[Détection et réponse des points de terminaison](overview-endpoint-detection-response.md)**<br>
Des fonctionnalités de détection et de réponse de point de terminaison sont mises en place pour détecter, examiner et répondre aux tentatives d’intrusion et aux violations actives. Avec le repérage avancé, vous avez un outil de repérage de menaces basé sur une requête qui vous permet de rechercher de manière proactive les violations et de créer des détections personnalisées.

- [Alertes](alerts-queue.md)
- [Données de point de terminaison historiques](investigate-machines.md#timeline)
- [Orchestration de la réponse](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts)
- [Collection d’investigation](respond-machine-alerts.md#collect-investigation-package-from-devices)
- [Veille contre les menaces](threat-indicator-concepts.md)
- [Service d’analyse et de détonation avancée](respond-file-alerts.md#deep-analysis)
- [Repérage avancé](advanced-hunting-overview.md)
    - [Détections personnalisées](overview-custom-detections.md)

<a name="ai"></a>

**[Examen et correction automatisés](automated-investigations.md)**<br>
En plus de répondre rapidement aux attaques avancées, Microsoft Defender pour point de terminaison offre des fonctionnalités d’investigation et de correction automatiques qui permettent de réduire le volume d’alertes en minutes à grande échelle.

- [Examen et correction automatisés](automated-investigations.md)
- [Consulter les détails et les résultats des examens automatisés](auto-investigation-action-center.md)
- [Afficher et approuver des actions de correction](manage-auto-investigation.md)

<a name="mte"></a>

**[Spécialistes des menaces Microsoft](microsoft-threat-experts.md)**<br>
Le nouveau service de recherche contre les menaces gérées de Microsoft Defender pour point de terminaison fournit une recherche proactive, la hiér donc, ainsi que des informations et un contexte supplémentaires. Spécialistes des menaces Microsoft permet aux centres d’opérations de sécurité (SOC) d’identifier les menaces et de répondre rapidement et avec précision aux menaces.

- [Notification d’attaque ciblée](microsoft-threat-experts.md)
- [Experts à la demande](microsoft-threat-experts.md)
- [Configurer votre service de Microsoft 365 Defender de recherche géré](configure-microsoft-threat-experts.md)

<a name="apis"></a>

**[Configuration et administration centralisées, API](management-apis.md)**<br>
Intégrez Microsoft Defender pour point de terminaison à vos flux de travail existants.
- [Intégration](onboard-configure.md)
- [Intégration API et SIEM](configure-siem.md)
- [API exposées](apis-intro.md)
- [Contrôle d’accès basé sur un rôle (RBAC)](rbac.md)
- [Rapports et tendances](threat-protection-reports.md)

<a name="integration"></a>
**[Intégration aux solutions Microsoft](threat-protection-integration.md)** <br>
 Microsoft Defender pour le point de terminaison s’intègre directement à différentes solutions Microsoft, notamment :
- Intune
- Microsoft Defender pour Office 365
- Microsoft Defender pour l’identité
- Microsoft Defender pour le cloud
- Skype Entreprise
- Microsoft Defender for Cloud Apps

<a name="mtp"></a>
**[Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-threat-protection)**<br>
 Avec Microsoft 365 Defender, Microsoft Defender pour point de terminaison et diverses solutions de sécurité Microsoft forment une suite de défense d’entreprise unifiée avant et après la violation qui s’intègre en mode natif à travers le point de terminaison, l’identité, le courrier électronique et les applications pour détecter, empêcher, examiner et répondre automatiquement aux attaques sophistiquées.
