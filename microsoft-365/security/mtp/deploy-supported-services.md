---
title: Déployer les services pris en charge par Microsoft 365 Defender
description: Découvrez les services de sécurité Microsoft qui peuvent être intégrés par Microsoft 365 Defender, leurs exigences en matière de licences et les procédures de déploiement
keywords: déployer, licences, services pris en charge, approvisionnement, configuration Microsoft Threat Protection, M365, éligibilité aux licences, Microsoft Defender ATP, MDATP, Office 365 ATP, Azure ATP, Microsoft Cloud App Security, MCAS, protection avancée contre les menaces, E5, A5, EMS
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 5af58a1c6850619ca08960997a30fe4a81158446
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49928961"
---
# <a name="deploy-supported-services"></a>Déployer les services pris en charge

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

[Microsoft 365 Defender](microsoft-threat-protection.md) intègre différents services de sécurité Microsoft pour fournir des fonctionnalités centralisées de détection, de prévention et d’examen contre les attaques sophistiquées. Cet article décrit les services pris en charge, leurs exigences en matière de licences, les avantages et les limitations associés au déploiement d’un ou plusieurs services, ainsi que des liens vers la façon dont vous pouvez les déployer entièrement individuellement.

## <a name="supported-services"></a>Services pris en charge
Une licence Microsoft 365 E5, E5 Security, A5 ou A5 Security ou une combinaison valide de licences permet d’accéder aux services pris en charge suivants et vous permet d’utiliser Microsoft 365 Defender dans le Centre de sécurité Microsoft 365. [Voir les exigences en matière de licences](prerequisites.md#licensing-requirements)

| Service pris en charge | Description |
| ------ | ------ |
| Microsoft Defender pour point de terminaison | Suite de protection des points de terminaison conçue autour de puissants capteurs comportementaux, d’analyses cloud et d’intelligence des menaces |
|Microsoft Defender pour Office 365 | Protection avancée de vos applications et données dans Office 365, y compris la messagerie électronique et d’autres outils de collaboration |
| Microsoft Defender pour Identity | Se défendre contre les menaces avancées, les identités compromises et les insiders malveillants à l’aide de signaux Active Directory corrélés |
| Microsoft Cloud App Security | Identifier et lutter contre les cybermenaces au sein de vos services cloud Microsoft et tiers |

## <a name="deployed-services-and-functionality"></a>Services et fonctionnalités déployés
Microsoft 365 Defender offre une meilleure visibilité, une corrélation et une correction à mesure que vous déployez des services pris en charge.

### <a name="benefits-of-full-deployment"></a>Avantages d’un déploiement complet
Pour bénéficier des avantages complets de Microsoft 365 Defender, nous vous recommandons de déployer tous les services pris en charge. Voici quelques-uns des principaux avantages du déploiement complet :
- Les incidents sont identifiés et corrélés en fonction des alertes et des signaux d’événement de tous les capteurs disponibles et des fonctionnalités d’analyse propres au service
- Les manuels d’examen et de correction automatisés (AIR) s’appliquent à différents types d’entités, notamment les appareils, les boîtes aux lettres et les comptes d’utilisateurs.
- Un schéma de recherche avancée plus complet peut être interrogé pour les données d’événements et d’entités provenant d’appareils, de boîtes aux lettres et d’autres entités

### <a name="limited-deployment-scenarios"></a>Scénarios de déploiement limités
Chaque service pris en charge que vous déployez fournit un ensemble extrêmement riche de signaux bruts, ainsi que des informations corrélées. Bien que le déploiement limité n’entraîne pas la fonctionnalité de Microsoft 365 Defender à désactiver, sa capacité à fournir une visibilité complète sur vos points de terminaison, applications, données et identités est affectée. En même temps, toutes les fonctionnalités de correction s’appliquent uniquement aux entités qui peuvent être gérées par les services que vous avez déployés.

Le tableau ci-dessous répertorie la façon dont chaque service pris en charge fournit des données supplémentaires, des opportunités d’obtenir des informations supplémentaires en les corrélant, ainsi que de meilleures fonctionnalités de correction et de réponse.

| Service | Données (signaux & des informations corrélées) | Correction et & de réponse |
| ------ | ------ | ------ |
| Microsoft Defender pour point de terminaison | - États de point de terminaison et événements bruts<br />- Détections et alertes de point de terminaison, y compris antivirus, EDR, réduction de la surface d’attaque<br />- Informations sur les fichiers et autres entités observées sur les points de terminaison | Points de terminaison |
|Microsoft Defender pour Office 365 | - États de messagerie et de boîte aux lettres et événements bruts<br />- Détections de messages électroniques, de pièces jointes et de liens | - Boîtes aux lettres<br />- Comptes Microsoft 365 |
| Microsoft Defender pour Identity | - Signaux Active Directory, y compris les événements d’authentification<br />- Détections comportementales liées à l’identité | Identités |
| Microsoft Cloud App Security | - Détection d’applications et de services cloud non locaux (shadow IT)<br />- Exposition des données aux applications cloud<br />- Activité contre les menaces associée aux applications cloud | Applications cloud |

## <a name="deploy-the-services"></a>Déployer les services
Le déploiement de chaque service nécessite généralement l’approvisionnement de votre client et une configuration initiale. Consultez le tableau suivant pour comprendre comment chacun de ces services est déployé.

| Service | Instructions d’approvisionnement | Configuration initiale |
| ------ | ------ | ------ |
| Microsoft Defender pour point de terminaison | [Guide de déploiement de Microsoft Defender for Endpoint](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/deployment-phases) | *Voir les instructions d’approvisionnement* |
|Microsoft Defender pour Office 365 | *Aucun, mise en service avec Office 365* | [Configurer les stratégies de Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp#configure-atp-policies) |
| Microsoft Defender pour Identity | [Démarrage rapide : créer votre instance De Microsoft Defender pour l’identité](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step1) | *Voir les instructions d’approvisionnement* |
| Microsoft Cloud App Security | *Aucune* | [Démarrage rapide : mise en place de Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/getting-started-with-cloud-app-security) |

Une fois que vous avez déployé les services pris en charge, [allumez Microsoft 365 Defender.](mtp-enable.md)

## <a name="related-topics"></a>Rubriques associées

- [Vue d’ensemble de Microsoft 365 Defender](microsoft-threat-protection.md)
- [Activer Microsoft 365 Defender](mtp-enable.md)
- [Vue d’ensemble de Microsoft Defender for Endpoint](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Présentation de Microsoft Defender pour Office 365](../office-365-security/office-365-atp.md)
- [Vue d’ensemble de Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)
- [Vue d’ensemble de Microsoft Defender for Identity](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)
