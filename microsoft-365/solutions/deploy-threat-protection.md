---
title: Déployer la protection contre les menaces de sécurité réseau dans Microsoft 365
description: Découvrez comment déployer les services de protection contre les menaces et les fonctionnalités de sécurité du réseau informatique dans Microsoft 365 E5.
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-threatprotection
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: 1bf06c605290dc94f64da6c2aabca3683c234c9a
ms.sourcegitcommit: 7355cc8871cde5fac6d7d6dcecc3e41e35601623
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2020
ms.locfileid: "48906750"
---
# <a name="deploy-threat-protection-capabilities-across-microsoft-365"></a>Déployer les fonctionnalités de protection contre les menaces sur Microsoft 365

Les [programmes malveillants](https://docs.microsoft.com/windows/security/threat-protection/intelligence/understanding-malware)et les cyberattaques sophistiqués, tels que [les menaces en fichiers](https://docs.microsoft.com/windows/security/threat-protection/intelligence/fileless-threats), sont une occurrence fréquente. Les entreprises doivent se protéger et leurs clients avec des fonctionnalités de sécurité du réseau informatique efficaces. De telles attaques peuvent entraîner des problèmes majeurs pour votre organisation, allant d’une perte de confiance à l’Woes financière, d’un temps d’arrêt menaçant pour les entreprises et bien plus encore. Il est important de se protéger contre les menaces, mais il peut être difficile de déterminer l’importance du temps, des efforts et des ressources de votre organisation. 

Les solutions de sécurité Microsoft sont intégrées à nos produits et services. Les fonctionnalités d’automatisation et d’apprentissage automatique réduisent la charge de vos équipes de sécurité afin de s’assurer que les éléments corrects sont traités. La puissance des solutions de sécurité réseau Microsoft repose sur des milliards de signaux que nous traiterons tous les jours dans notre [graphique de sécurité intelligent](https://cloud-platform-assets.azurewebsites.net/intelligent-security-graph). Les solutions de sécurité Microsoft 365 incluent [microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection), une solution qui rassemble les signaux de vos courriers électroniques, données, périphériques et identités pour peindre une image des menaces avancées contre votre organisation.


Regardez cette vidéo de présentation du processus de déploiement.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vsI7]

Utilisez cet article pour vous aider à implémenter votre solution de protection contre les menaces.

## <a name="threat-protection-in-microsoft-365-e5"></a>Protection contre les menaces dans Microsoft 365 E5

[Microsoft 365 E5](https://www.microsoft.com/microsoft-365/enterprise-e5-business-software?activetab=pivot%3aoverviewtab) vous permet de protéger votre organisation grâce à une intelligence intégrée et intégrée. Les fonctionnalités de protection contre les menaces de Microsoft 365 E5 vous permettent de détecter et d’examiner les menaces avancées, les identités compromises et les actions malveillantes dans votre environnement local et Cloud.

Dans Microsoft 365 E5, les fonctionnalités de protection contre les menaces sont intégrées par défaut. Les signaux de chaque fonctionnalité ajoutent une force à la capacité globale à détecter les menaces et à y répondre. L’ensemble de fonctionnalités combiné offre la meilleure protection pour les organisations, en particulier pour les organisations multinationales, par rapport à l’exécution de produits non-Microsoft. L’image suivante décrit les services et les fonctionnalités de protection contre les menaces dans Microsoft 365 E5 qui sont décrits dans cet article.

![Vue d’ensemble de Microsoft 365 Defender](../media/solutions-architecture-center/deploy-threat-protection-across-m365-overview.png)

Dès que vous déployez l’une des fonctionnalités de Defender pour Office 365, vous pouvez activer Microsoft 365 Defender, qui regroupe les signaux et les données à un seul endroit. 

![Illustration conceptuelle du tableau de bord Microsoft 365 Defender](../media/solutions-architecture-center/deploy-threat-protection-across-m365-mtp.png)

L’illustration suivante représente un chemin d’accès recommandé pour le déploiement de ces fonctionnalités individuelles. 

![Signaux de protection contre les menaces M365](../media/solutions-architecture-center/deploy-threat-protection-across-m365.png)

|Solution/fonctionnalités  |Description  |
|---------|---------|
|Authentification multifacteur et accès conditionnel     |Protégez-vous contre les identités et les appareils compromis. Commencez par cette protection, car elle est fondamentale. La configuration recommandée dans ce guide inclut la protection des identités Azure AD comme condition préalable.     |
|Microsoft Defender pour identité     |  Solution de sécurité basée sur le Cloud qui tire parti de vos signaux Active Directory sur site pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions malveillantes dirigées vers votre organisation. Concentrez-vous sur Microsoft Defender pour Identity Next, car il protège votre infrastructure sur local et votre infrastructure cloud, ne dispose d’aucune dépendance ou prérequis, et peut vous offrir des avantages immédiats.       | 
|Microsoft Defender pour Office 365     | Protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. Protections contre les programmes malveillants, le hameçonnage, l’usurpation d’identité et d’autres types d’attaques. La configuration de Microsoft Defender pour Office 365 est recommandée dans la mesure où le contrôle des modifications, la migration des paramètres du système en place et d’autres considérations peuvent mettre plus de temps à déployer. <br><br>Remarque : Veillez à configurer les fonctionnalités de protection contre les menaces incluses dans tous les abonnements Office 365 (Exchange Online Protection).       |
|Microsoft Defender pour point de terminaison    | Une plateforme de protection des points de terminaison qui permet de prévenir, de détecter, d’examiner et de répondre aux menaces avancées.  Le déploiement de Defender pour le point de terminaison peut prendre un certain temps, mais la configuration peut être réalisée en parallèle avec d’autres fonctionnalités.   |
|Microsoft Cloud App Security     |   Un courtier en matière de sécurité d’accès au Cloud pour la découverte, l’enquête et la gouvernance. Vous pouvez activer Microsoft Cloud App Security dès le début pour commencer à collecter des données et des informations. L’implémentation d’informations et d’autres protections ciblées dans vos applications SaaS implique une planification et peut prendre plus de temps.       | 

> [!TIP]
> Les organisations avec plusieurs équipes de sécurité peuvent implémenter ces fonctionnalités en parallèle.

## <a name="deploy-your-threat-protection-solution"></a>Déployer votre solution de protection contre les menaces

Pour vous assurer que votre organisation dispose de la meilleure protection possible, configurez et déployez votre solution de sécurité pour inclure les étapes suivantes :

1. [Configurer l’authentification multifacteur et les stratégies d’accès conditionnel](deploy-threat-protection-configure.md#step-1-set-up-multi-factor-authentication-and-conditional-access-policies)
2. [Configurer Microsoft Defender pour l’identité](deploy-threat-protection-configure.md#step-2-configure-microsoft-defender-for-identity)
3. [Activer Microsoft 365 Defender](deploy-threat-protection-configure.md#step-3-turn-on-microsoft-365-defender)
4. [Configurer Defender pour Office 365](deploy-threat-protection-configure.md#step-4-configure-microsoft-defender-for-office-365)
5. [Configurer Microsoft Defender pour le point de terminaison](deploy-threat-protection-configure.md#step-5-configure-microsoft-defender-for-endpoint)
6. [Configurer la sécurité des applications Cloud Microsoft](deploy-threat-protection-configure.md#step-6-configure-microsoft-cloud-app-security)
7. [Surveiller l’État et prendre des mesures](deploy-threat-protection-configure.md#step-7-monitor-status-and-take-actions)
8. [Former les utilisateurs](deploy-threat-protection-configure.md#step-8-train-users)

Vos fonctionnalités de protection contre les menaces peuvent être configurées en parallèle, de sorte que si vous avez plusieurs équipes de sécurité réseau responsables de différents services, ils peuvent configurer les fonctionnalités de protection de votre organisation en même temps. Le diagramme suivant illustre le processus de haut niveau pour le déploiement des fonctionnalités de protection contre les menaces. 

![Processus de déploiement des fonctionnalités de protection contre les menaces](../media/solutions-architecture-center/deploy-threat-protection-across-m365-grid.png) 
