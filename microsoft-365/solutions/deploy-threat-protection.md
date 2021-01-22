---
title: Déployer la protection contre les menaces de sécurité réseau dans Microsoft 365
description: Découvrez comment déployer les services de protection contre les menaces et les fonctionnalités de sécurité du réseau informatique dans Microsoft 365 E5.
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.technology: m365d
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-threatprotection
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: 79352aca2012e6615f41b19f4a77fc5cf125f4c4
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49926749"
---
# <a name="deploy-threat-protection-capabilities-across-microsoft-365"></a>Déployer des fonctionnalités de protection contre les menaces dans Microsoft 365

[Les programmes](https://docs.microsoft.com/windows/security/threat-protection/intelligence/understanding-malware)malveillants et les cyberattaques sophistiquées, telles que les menaces sans [fichier,](https://docs.microsoft.com/windows/security/threat-protection/intelligence/fileless-threats)sont une occurrence courante. Les entreprises doivent se protéger elles-mêmes et leurs clients avec des fonctionnalités efficaces de sécurité du réseau informatique. De telles attaques peuvent entraîner des problèmes majeurs pour votre organisation, allant d’une perte de confiance à des difficultés financières, à des temps d’arrêt de l’activité et bien plus encore. La protection contre les menaces est importante, mais il peut être difficile de déterminer où concentrer le temps, les efforts et les ressources de votre organisation. 

Les solutions de sécurité Microsoft sont intégrées à nos produits et services. Les fonctionnalités d’automatisation et d’apprentissage automatique réduisent la charge sur vos équipes de sécurité pour vous assurer que les éléments qui vous sont nécessaires sont traités. Et la force des solutions de sécurité réseau Microsoft repose sur des nombres de signaux que nous traiterons tous les jours dans [notre graphique de sécurité intelligent.](https://cloud-platform-assets.azurewebsites.net/intelligent-security-graph) Microsoft 365 security solutions include [Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection), a solution that brings together signals across your email, data, devices, and identities to paint a picture of advanced threats against your organization.


Regardez cette vidéo de présentation du processus de déploiement.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vsI7]

Utilisez cet article comme guide pour implémenter votre solution de protection contre les menaces.

## <a name="threat-protection-in-microsoft-365-e5"></a>Protection contre les menaces dans Microsoft 365 E5

[Microsoft 365 E5](https://www.microsoft.com/microsoft-365/enterprise-e5-business-software?activetab=pivot%3aoverviewtab) vous permet de protéger votre organisation avec une intelligence intégrée et adaptative. Grâce aux fonctionnalités de protection contre les menaces de Microsoft 365 E5, vous pouvez détecter et examiner les menaces avancées, les identités compromises et les actions malveillantes dans votre environnement local et cloud.

Dans Microsoft 365 E5, les fonctionnalités de protection contre les menaces sont intégrées par défaut. Les signaux de chaque fonctionnalité ajoutent une force à la capacité globale de détecter et de répondre aux menaces. L’ensemble combiné de fonctionnalités offre la meilleure protection pour les organisations, en particulier les organisations multinationales, par rapport à l’exécution de produits autres que Microsoft. L’image suivante illustre les services et fonctionnalités de protection contre les menaces dans Microsoft 365 E5 décrits dans cet article.

![Vue d’ensemble de Microsoft 365 Defender](../media/solutions-architecture-center/deploy-threat-protection-across-m365-overview.png)

Dès que vous déployez l’une des fonctionnalités de Defender pour Office 365, vous pouvez activer Microsoft 365 Defender, qui rassemble les signaux et les données au même endroit. 

![Illustration conceptuelle du tableau de bord Microsoft 365 Defender](../media/solutions-architecture-center/deploy-threat-protection-across-m365-mtp.png)

L’illustration suivante illustre un chemin d’accès recommandé pour le déploiement de ces fonctionnalités individuelles. 

![Signaux de protection contre les menaces M365](../media/solutions-architecture-center/deploy-threat-protection-across-m365.png)

|Solution/fonctionnalités  |Description  |
|---------|---------|
|Authentification multifacteur et accès conditionnel     |Protégez-vous contre les identités et les appareils compromis. Commencez par cette protection, car elle est de base. La configuration recommandée dans ce guide inclut Azure AD Identity Protection comme condition préalable.     |
|Microsoft Defender pour Identity     |  Solution de sécurité basée sur le cloud qui exploite vos signaux Active Directory locaux pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation. Concentrez-vous ensuite sur Microsoft Defender pour l’identité, car il protège votre infrastructure locale et votre infrastructure cloud, n’a pas de dépendances ou de conditions préalables et peut fournir des avantages immédiats.       | 
|Microsoft Defender pour Office 365     | Protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. Protection contre les programmes malveillants, le hameçonnage, l’usurpation et d’autres types d’attaques. La configuration de Microsoft Defender pour Office 365 est recommandée ensuite, car le déploiement du contrôle des changements, de la migration des paramètres à partir d’un système insérez et d’autres considérations peut prendre plus de temps. <br><br>Remarque : veillez à configurer les fonctionnalités de protection contre les menaces incluses dans tous les abonnements Office 365 (Exchange Online Protection).       |
|Microsoft Defender pour point de terminaison    | Plateforme de protection des points de terminaison qui permet de prévenir, de détecter, d’examiner et de répondre aux menaces avancées.  Le déploiement de Defender for Endpoint peut prendre un certain temps, mais la configuration peut être effectuée en parallèle avec d’autres fonctionnalités.   |
|Microsoft Cloud App Security     |   Un courtier de sécurité d’accès au cloud pour la découverte, l’examen et la gouvernance. Vous pouvez activer Microsoft Cloud App Security tôt pour commencer à collecter des données et des informations. L’implémentation d’informations et d’autres protections ciblées au sein de vos applications SaaS implique une planification et peut prendre plus de temps.       | 

> [!TIP]
> Les organisations avec plusieurs équipes de sécurité peuvent implémenter ces fonctionnalités en parallèle.

## <a name="deploy-your-threat-protection-solution"></a>Déployer votre solution de protection contre les menaces

Pour vous assurer que votre organisation dispose de la meilleure protection possible, configurer et déployer votre solution de sécurité pour inclure les étapes suivantes :

1. [Configurer des stratégies d’authentification multifacteur et d’accès conditionnel](deploy-threat-protection-configure.md#step-1-set-up-multi-factor-authentication-and-conditional-access-policies)
2. [Configurer Microsoft Defender pour l’identité](deploy-threat-protection-configure.md#step-2-configure-microsoft-defender-for-identity)
3. [Activer Microsoft 365 Defender](deploy-threat-protection-configure.md#step-3-turn-on-microsoft-365-defender)
4. [Configurer Defender pour Office 365](deploy-threat-protection-configure.md#step-4-configure-microsoft-defender-for-office-365)
5. [Configurer Microsoft Defender pour le point de terminaison](deploy-threat-protection-configure.md#step-5-configure-microsoft-defender-for-endpoint)
6. [Configurer Microsoft Cloud App Security](deploy-threat-protection-configure.md#step-6-configure-microsoft-cloud-app-security)
7. [Surveiller l’état et prendre des mesures](deploy-threat-protection-configure.md#step-7-monitor-status-and-take-actions)
8. [Former les utilisateurs](deploy-threat-protection-configure.md#step-8-train-users)

Vos fonctionnalités de protection contre les menaces peuvent être configurées en parallèle. Ainsi, si plusieurs équipes de sécurité réseau sont responsables de différents services, elles peuvent configurer les fonctionnalités de protection de votre organisation en même temps. Le diagramme suivant illustre le processus de haut niveau de déploiement des fonctionnalités de protection contre les menaces. 

![Processus de déploiement des fonctionnalités de protection contre les menaces](../media/solutions-architecture-center/deploy-threat-protection-across-m365-grid.png) 
