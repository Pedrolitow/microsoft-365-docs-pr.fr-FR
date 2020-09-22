---
title: Déployer des services pris en charge par Microsoft Threat Protection
description: Découvrez les services de sécurité Microsoft qui peuvent être intégrés par Microsoft Threat Protection, leurs exigences en matière de licences et les procédures de déploiement
keywords: déploiement, licences, services pris en charge, approvisionnement, configuration de la protection contre les menaces Microsoft, M365, éligibilité de la licence, Microsoft Defender ATP, MDATP, Office 365 ATP, Azure ATP, sécurité des applications Cloud Microsoft, MCAS, protection avancée contre les menaces, E5, a5, EMS
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 73d807a37f1c85e9d79353334cac4208b86bbdc2
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48198884"
---
# <a name="deploy-supported-services"></a>Déployer les services pris en charge

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

[Microsoft Threat Protection](microsoft-threat-protection.md) intègre différents services de sécurité Microsoft pour fournir des fonctionnalités de détection, de prévention et d’enquête centralisées contre les attaques sophistiquées. Cet article décrit les services pris en charge, leurs exigences en matière de licences, les avantages et les limitations associés au déploiement d’un ou de plusieurs services, ainsi que des liens vers la façon de les déployer entièrement individuellement.

## <a name="supported-services"></a>Services pris en charge
Une licence de sécurité Microsoft 365 E5, E5 Security, a5 ou a5 ou une combinaison valide de licences donne accès aux services pris en charge suivants et vous permet d’utiliser Microsoft Threat Protection dans le centre de sécurité Microsoft 365. [Consulter les conditions requises en matière de licences](prerequisites.md#licensing-requirements)

| Service pris en charge | Description |
| ------ | ------ |
| Microsoft Defender ATP | Suite de protection de point de terminaison basée sur des capteurs de comportement puissants, sur l’analyse de Cloud et sur l’intelligence des menaces |
| Office 365 – Protection avancée contre les menaces | Protection avancée de vos applications et données dans Office 365, y compris la messagerie et d’autres outils de collaboration |
| Azure ATP | Défense contre les menaces avancées, les identités compromises et les Insiders malveillants à l’aide de signaux Active Directory corrélés |
| Microsoft Cloud App Security | Identifier et combattre Cyber dans vos services Cloud tiers et Microsoft |

## <a name="deployed-services-and-functionality"></a>Fonctionnalités et services déployés
La protection contre les menaces Microsoft offre une meilleure visibilité, corrélation et correction lorsque vous déployez des services plus pris en charge.

### <a name="benefits-of-full-deployment"></a>Avantages du déploiement complet
Pour bénéficier des avantages complets de la protection contre les menaces Microsoft, nous vous recommandons de déployer tous les services pris en charge. Voici quelques-uns des principaux avantages du déploiement complet :
- Les incidents sont identifiés et corrélés en fonction des alertes et des signaux d’événement de tous les capteurs disponibles et des fonctionnalités d’analyse spécifiques aux services
- Les règles d’enquête et de correction automatisées (AIR) s’appliquent à différents types d’entité, y compris les appareils, les boîtes aux lettres et les comptes d’utilisateur
- Un schéma de chasse avancé plus complet peut être interrogé pour les données d’événement et d’entité à partir des appareils, des boîtes aux lettres et d’autres entités.

### <a name="limited-deployment-scenarios"></a>Scénarios de déploiement limité
Chaque service que vous déployez fournit un ensemble extrêmement riche de signaux bruts ainsi que des informations corrélées. Bien que le déploiement limité ne provoque pas la désactivation de la fonctionnalité protection de Microsoft contre les menaces, sa capacité à fournir une visibilité complète de vos points de terminaison, applications, données et identités est affectée. Dans le même temps, les fonctionnalités de correction ne s’appliquent qu’aux entités qui peuvent être gérées par les services que vous avez déployés.

Le tableau ci-dessous répertorie la façon dont chaque service pris en charge fournit des données supplémentaires, les opportunités d’obtenir des informations supplémentaires en mettant en corrélation les données, ainsi que de meilleures fonctionnalités de correction et de réponse.

| Service | Data (signale & informations corrélées) | Correction de l’étendue de réponse & |
| ------ | ------ | ------ |
| Microsoft Defender ATP | -États de point de terminaison et événements bruts<br />-Détections de point de terminaison et alertes, y compris antivirus, EDR, réduction de surface d’attaque<br />-Infos sur les fichiers et les autres entités observées sur les points de terminaison | Points de terminaison |
| Office 365 – Protection avancée contre les menaces | -États de messagerie et de boîte aux lettres et événements bruts<br />-Détections de messages électroniques, de pièces jointes et de liens | -Boîtes aux lettres<br />-Comptes Microsoft 365 |
| Azure ATP | -Signaux Active Directory, y compris les événements d’authentification<br />-Détections comportementales liées à l’identité | Identités |
| Microsoft Cloud App Security | -Détection d’applications et de services Cloud insanctionnés (cliché instantané)<br />-Exposition des données aux applications Cloud<br />-Activité de menace associée aux applications Cloud | Applications cloud |

## <a name="deploy-the-services"></a>Déployer les services
Le déploiement de chaque service nécessite généralement un approvisionnement de votre client et une configuration initiale. Consultez le tableau suivant pour comprendre la façon dont chacun de ces services est déployé.

| Service | Instructions de mise en service | Configuration initiale |
| ------ | ------ | ------ |
| Microsoft Defender ATP | [Guide de déploiement de Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/deployment-phases) | *Voir les instructions de mise en service* |
| Office 365 – Protection avancée contre les menaces | *Aucun, configuré avec Office 365* | [Configurez des stratégies ATP](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp#configure-atp-policies) |
| Azure ATP | [QuickStart : créer votre instance Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step1) | *Voir les instructions de mise en service* |
| Microsoft Cloud App Security | *Aucune* | [QuickStart : prise en main de la sécurité des applications Cloud Microsoft](https://docs.microsoft.com/cloud-app-security/getting-started-with-cloud-app-security) |

Une fois que vous avez déployé les services pris en charge, [activez Microsoft Threat Protection](mtp-enable.md).

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble de la Protection Microsoft contre les menaces](microsoft-threat-protection.md)
- [Activer la Protection Microsoft contre les menaces](mtp-enable.md)
- [Vue d’ensemble de Microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Vue d’ensemble d’Office 365 – Protection avancée contre les menaces](../office-365-security/office-365-atp.md)
- [Vue d’ensemble de Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)
- [Vue d’ensemble d’Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)
