---
title: Déployer les services pris en charge par Microsoft 365 Defender
description: En savoir plus sur les services de sécurité Microsoft qui peuvent être intégrés par Microsoft 365 Defender, leurs exigences en matière de licences et les procédures de déploiement
keywords: déployer, licences, services pris en charge, approvisionnement, Microsoft 365 Defender de configuration, M365, éligibilité aux licences, Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender pour l’identité, Microsoft Cloud App Security, MCAS, E5, A5, EMS
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
localization_priority: Normal
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
ms.openlocfilehash: 4a3aac06f19c7ed86af67f3b72bac8bf367628a8
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204516"
---
# <a name="deploy-supported-services"></a>Déployer les services pris en charge

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

[Microsoft 365 Defender](microsoft-365-defender.md) intègre différents services de sécurité Microsoft pour fournir des fonctionnalités centralisées de détection, de prévention et d’enquête contre les attaques sophistiquées. Cet article décrit les services pris en charge, leurs exigences en matière de licences, les avantages et les limitations associés au déploiement d’un ou plusieurs services, ainsi que des liens vers la façon dont vous pouvez les déployer entièrement individuellement.

## <a name="supported-services"></a>Services pris en charge
Une licence Microsoft 365 E5, sécurité E5, A5 ou A5 ou une combinaison valide de licences permet d’accéder aux services pris en charge suivants et vous donne la possibilité d’utiliser Microsoft 365 Defender. [Voir les exigences en matière de licences](prerequisites.md#licensing-requirements)

| Service pris en charge | Description |
| ------ | ------ |
| Microsoft Defender pour point de terminaison | Suite de protection des points de terminaison conçue autour de puissants capteurs comportementaux, d’analyse cloud et d’intelligence des menaces |
|Microsoft Defender pour Office 365 | Protection avancée de vos applications et données dans Office 365, y compris la messagerie électronique et d’autres outils de collaboration |
| Microsoft Defender pour Identity | Se défendre contre les menaces avancées, les identités compromises et les insiders malveillants à l’aide de signaux Active Directory corrélés |
| Microsoft Cloud App Security | Identifier et lutter contre les cybermenaces au sein de vos services cloud Microsoft et tiers |

## <a name="deployed-services-and-functionality"></a>Services et fonctionnalités déployés
Microsoft 365 Defender offre une meilleure visibilité, une corrélation et une correction à mesure que vous déployez des services pris en charge.

### <a name="benefits-of-full-deployment"></a>Avantages d’un déploiement complet
Pour bénéficier des avantages complets de Microsoft 365 Defender, nous vous recommandons de déployer tous les services pris en charge. Voici quelques-uns des principaux avantages du déploiement complet :
- Les incidents sont identifiés et corrélés en fonction des alertes et des signaux d’événement de tous les capteurs disponibles et des fonctionnalités d’analyse propres au service
- Les manuels d’examen et de correction automatisés (AIR) s’appliquent à différents types d’entités, notamment les appareils, les boîtes aux lettres et les comptes d’utilisateurs.
- Un schéma de recherche avancé plus complet peut être interrogé pour les données d’événements et d’entités provenant d’appareils, de boîtes aux lettres et d’autres entités

### <a name="limited-deployment-scenarios"></a>Scénarios de déploiement limités
Chaque service pris en charge que vous déployez fournit un ensemble extrêmement riche de signaux bruts, ainsi que des informations corrélées. Bien que le déploiement limité ne soit pas à l’origine de la Microsoft 365 Defender à désactiver, sa capacité à fournir une visibilité complète sur vos points de terminaison, applications, données et identités est affectée. En même temps, toutes les fonctionnalités de correction s’appliquent uniquement aux entités qui peuvent être gérées par les services que vous avez déployés.

Le tableau ci-dessous répertorie la façon dont chaque service pris en charge fournit des données supplémentaires, des opportunités d’obtenir des informations supplémentaires en les corrélant, ainsi que de meilleures fonctionnalités de correction et de réponse.

| Service | Données (signaux & des informations corrélées) | Correction et & de réponse |
| ------ | ------ | ------ |
| Microsoft Defender pour point de terminaison | - États de point de terminaison et événements bruts<br />- Détections et alertes de point de terminaison, notamment antivirus, PEPT, réduction de la surface d’attaque<br />- Informations sur les fichiers et autres entités observées sur les points de terminaison | Points de terminaison |
|Microsoft Defender pour Office 365 | - États de messagerie et de boîte aux lettres et événements bruts<br />- Détections de messages électroniques, de pièces jointes et de liens | - Boîtes aux lettres<br />- Microsoft 365 comptes |
| Microsoft Defender pour Identity | - Signaux Active Directory, y compris les événements d’authentification<br />- Détections comportementales liées à l’identité | Identités |
| Microsoft Cloud App Security | - Détection d’applications et de services cloud non locaux (shadow IT)<br />- Exposition des données aux applications cloud<br />- Activité contre les menaces associée aux applications cloud | Applications cloud |

## <a name="deploy-the-services"></a>Déployer les services
Le déploiement de chaque service nécessite généralement un approvisionnement pour votre client et une configuration initiale. Consultez le tableau suivant pour comprendre comment chacun de ces services est déployé.

| Service | Instructions de configuration | Configuration initiale |
| ------ | ------ | ------ |
| Microsoft Defender pour point de terminaison | [Guide de déploiement de Microsoft Defender pour point de terminaison](../defender-endpoint/deployment-phases.md) | *Voir les instructions de configuration* |
|Microsoft Defender pour Office 365 | *Aucune, mise en service avec Office 365* | [Configurer les stratégies de Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) |
| Microsoft Defender pour l’identité | [Démarrage rapide : créer votre instance Microsoft Defender pour l’identité](/azure-advanced-threat-protection/install-atp-step1) | *Voir les instructions de configuration* |
| Microsoft Cloud App Security | *Aucune* | [Démarrage rapide : prise en main de Microsoft Cloud App Security](/cloud-app-security/getting-started-with-cloud-app-security) |

Une fois que vous avez déployé les services pris en charge, [Microsoft 365 Defender](m365d-enable.md).

## <a name="related-topics"></a>Rubriques connexes

- [Microsoft 365 Defender vue d’ensemble](microsoft-365-defender.md)
- [Activer Microsoft 365 Defender](m365d-enable.md)
- [Vue d’ensemble de Microsoft Defender for Endpoint](../defender-endpoint/microsoft-defender-endpoint.md)
- [Vue d’ensemble Office 365 Microsoft Defender for Office 365](../office-365-security/defender-for-office-365.md)
- [Aperçu de Microsoft Cloud App Security ](/cloud-app-security/what-is-cloud-app-security)
- [Vue d’ensemble de Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)
