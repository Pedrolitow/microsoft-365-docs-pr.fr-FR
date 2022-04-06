---
title: Déployer des services pris en charge par Microsoft 365 Defender
description: Découvrez les services de sécurité Microsoft qui peuvent être intégrés par Microsoft 365 Defender, leurs exigences de licence et leurs procédures de déploiement
keywords: déployer, licences, services pris en charge, provisionnement, Microsoft 365 Defender de configuration, M365, éligibilité aux licences, Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender pour Identity, Microsoft Cloud App Security, MCAS, E5, A5, EMS
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 4ac6186f3ec8ca7d4888a995b2352ec50529e4f1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664895"
---
# <a name="deploy-supported-services"></a>Déployer les services pris en charge

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

[Microsoft 365 Defender](microsoft-365-defender.md) intègre différents services de sécurité Microsoft pour fournir des fonctionnalités centralisées de détection, de prévention et d’investigation contre les attaques sophistiquées. Cet article décrit les services pris en charge, leurs exigences en matière de licences, les avantages et les limitations associés au déploiement d’un ou plusieurs services, ainsi que des liens vers la façon dont vous pouvez les déployer entièrement individuellement.

## <a name="supported-services"></a>Services pris en charge

Une licence Microsoft 365 E5, E5 Security, A5 ou A5 Security ou une combinaison valide de licences permet d’accéder aux services pris en charge suivants et vous permet d’utiliser Microsoft 365 Defender. [Voir les exigences en matière de licences](prerequisites.md#licensing-requirements)

| Service pris en charge | Description |
| ------ | ------ |
| Microsoft Defender pour point de terminaison | Suite endpoint protection basée sur de puissants capteurs comportementaux, l’analytique cloud et l’intelligence des menaces |
|Microsoft Defender pour Office 365 | Protection avancée pour vos applications et données dans Office 365, y compris la messagerie électronique et d’autres outils de collaboration |
| Microsoft Defender pour Identity | Se défendre contre les menaces avancées, les identités compromises et les insiders malveillants à l’aide de signaux Active Directory corrélés |
| Microsoft Defender for Cloud Apps | Identifier et combattre les cybermenaces dans vos services cloud microsoft et tiers |

## <a name="deployed-services-and-functionality"></a>Services et fonctionnalités déployés

Microsoft 365 Defender offre une meilleure visibilité, une meilleure corrélation et une meilleure correction à mesure que vous déployez des services plus pris en charge.

### <a name="benefits-of-full-deployment"></a>Avantages du déploiement complet

Pour bénéficier des avantages complets de Microsoft 365 Defender, nous vous recommandons de déployer tous les services pris en charge. Voici quelques-uns des principaux avantages du déploiement complet :

- Les incidents sont identifiés et corrélés en fonction des alertes et des signaux d’événement de tous les capteurs disponibles et des fonctionnalités d’analyse spécifiques au service
- Les playbooks AIR (Automated Investigation and Remediation) s’appliquent à différents types d’entités, notamment les appareils, les boîtes aux lettres et les comptes d’utilisateur
- Un schéma de repérage avancé plus complet peut être interrogé pour les données d’événements et d’entités provenant d’appareils, de boîtes aux lettres et d’autres entités

### <a name="limited-deployment-scenarios"></a>Scénarios de déploiement limités

Chaque service pris en charge que vous déployez fournit un ensemble extrêmement riche de signaux bruts ainsi que des informations corrélées. Bien que le déploiement limité n’entraîne pas la désactivation de Microsoft 365 Defender fonctionnalité, sa capacité à fournir une visibilité complète sur vos points de terminaison, applications, données et identités est affectée. En même temps, toutes les fonctionnalités de correction s’appliquent uniquement aux entités qui peuvent être gérées par les services que vous avez déployés.

Le tableau ci-dessous répertorie la façon dont chaque service pris en charge fournit des données supplémentaires, des opportunités d’obtenir des insights supplémentaires en mettant en corrélation les données, ainsi que de meilleures fonctionnalités de correction et de réponse.

| Service | Données (signaux & informations corrélées) | Correction & portée de réponse |
| ------ | ------ | ------ |
| Microsoft Defender pour point de terminaison |<ul><li>États de point de terminaison et événements bruts</li><li>Détections et alertes de point de terminaison, notamment antivirus, PEPT, réduction de la surface d’attaque</li><li>Informations sur les fichiers et autres entités observées sur les points de terminaison</li></ul> | Points de terminaison |
|Microsoft Defender pour Office 365 |<ul><li>États de messagerie et de boîte aux lettres et événements bruts</li><li>Détections d’e-mails, de pièces jointes et de liens</li></ul> | <ul><li>Boîtes aux lettres</li><li>comptes Microsoft 365</li></ul> |
| Microsoft Defender pour Identity |<ul><li>Signaux Active Directory, y compris les événements d’authentification</li><li>Détections comportementales liées à l’identité</li></ul> | Identités |
| Microsoft Defender for Cloud Apps |<ul><li>Détection d’applications et de services cloud non approuvés (informatique fantôme)</li><li>Exposition des données aux applications cloud</li><li>Activité de menace associée aux applications cloud</li></ul> | Applications cloud |

## <a name="deploy-the-services"></a>Déployer les services

Le déploiement de chaque service nécessite généralement un approvisionnement pour votre client et une configuration initiale. Consultez le tableau suivant pour comprendre comment chacun de ces services est déployé.

| Service | Instructions de configuration | Configuration initiale |
| ------ | ------ | ------ |
| Microsoft Defender pour point de terminaison | [Guide de déploiement de Microsoft Defender pour point de terminaison](../defender-endpoint/deployment-phases.md) | *Voir les instructions de configuration* |
|Microsoft Defender pour Office 365 | *Aucune, mise en service avec Office 365* | [Configurer les stratégies de Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) |
| Microsoft Defender pour l’identité | [Démarrage rapide : créer votre instance Microsoft Defender pour l’identité](/azure-advanced-threat-protection/install-atp-step1) | *Voir les instructions de configuration* |
| Microsoft Defender for Cloud Apps | *Aucune* | [Démarrage rapide : prise en main de Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security) |

Une fois que vous avez déployé les services pris en charge, [activez Microsoft 365 Defender](m365d-enable.md).

## <a name="related-topics"></a>Voir aussi

- [vue d’ensemble de Microsoft 365 Defender](microsoft-365-defender.md)
- [Activer Microsoft 365 Defender](m365d-enable.md)
- [Microsoft Defender pour point de terminaison vue d’ensemble](../defender-endpoint/microsoft-defender-endpoint.md)
- [Microsoft Defender pour Office 365 vue d’ensemble](../office-365-security/defender-for-office-365.md)
- [Vue d’ensemble de Microsoft Defender pour les applications cloud](/cloud-app-security/what-is-cloud-app-security)
- [Microsoft Defender pour Identity vue d’ensemble](/azure-advanced-threat-protection/what-is-atp)
