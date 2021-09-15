---
title: Déployer des fonctionnalités de protection contre les menaces dans Microsoft 365
description: Obtenez une vue d’ensemble des services de protection contre les menaces et des fonctionnalités de sécurité dans Microsoft 365 E5. Protégez vos comptes d’utilisateurs, appareils, contenu de messagerie, etc. avec Microsoft 365 E5.
keywords: protection microsoft contre les menaces, defender, configuration, protection avancée contre les menaces, sécurité, microsoft 365 E5, protéger les appareils
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.technology: m365d
audience: ITPro
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-threatprotection
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: 1aed90c47ca72cb514d8d3df1fa22e5dff4feb44
ms.sourcegitcommit: f88a0ec621e7d9bc5f376eeaf70c8a9800711f88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59357288"
---
# <a name="deploy-threat-protection-capabilities-across-microsoft-365-e5"></a>Déployer des fonctionnalités de protection contre les menaces dans Microsoft 365 E5

Cette solution décrit les fonctionnalités puissantes de protection contre les menaces Microsoft 365 E5 et pourquoi la protection contre les menaces est importante. Obtenez une vue d’ensemble de la protection contre Microsoft 365 E5 et découvrez comment aborder la configuration et la configuration pour votre organisation.

## <a name="why-threat-protection-is-important"></a>Pourquoi la protection contre les menaces est-elle importante ? 

[Les programmes](/windows/security/threat-protection/intelligence/understanding-malware)malveillants et les cyberattaques sophistiquées, telles que les menaces sans [fichier,](/windows/security/threat-protection/intelligence/fileless-threats)sont une occurrence courante. Les entreprises doivent se protéger elles-mêmes et leurs clients avec des fonctionnalités de sécurité informatique efficaces. Les cyberattaques peuvent entraîner des problèmes majeurs pour votre organisation, allant d’une perte de confiance à des difficultés financières, à des temps d’arrêt de l’activité et bien plus encore. La protection contre les menaces est importante, mais il peut être difficile de déterminer où concentrer le temps, les efforts et les ressources de votre organisation. Microsoft 365 E5 peut vous aider. 

## <a name="threat-protection-in-microsoft-365-e5"></a>Protection contre les menaces dans Microsoft 365 E5

Les solutions de sécurité Microsoft sont intégrées à nos produits et services. Les fonctionnalités d’automatisation et d’apprentissage automatique réduisent la charge sur vos équipes de sécurité pour vous assurer que les éléments qui vous sont nécessaires sont traités. La force des solutions de sécurité Microsoft repose sur des nombres de signaux que nous traiterons tous les jours dans notre système de sécurité [intelligente Graph](/graph/security-concept-overview). Microsoft 365 solutions de sécurité incluent [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md), une solution qui regroupe les signaux de votre messagerie électronique, données, appareils et identités pour peindre une image des menaces avancées contre votre organisation.

[Microsoft 365 E5](https://www.microsoft.com/microsoft-365/enterprise-e5-business-software?activetab=pivot%3aoverviewtab) vous permet de protéger votre organisation avec une intelligence intégrée adaptative. Grâce aux fonctionnalités de sécurité de Microsoft 365 E5, vous pouvez détecter et examiner les menaces avancées, les identités compromises et les actions malveillantes dans votre environnement (en local et dans le cloud).

## <a name="better-protection-with-integration"></a>Meilleure protection avec intégration

Dans Microsoft 365 E5, les fonctionnalités de protection contre les menaces sont intégrées par défaut. Les signaux de chaque fonctionnalité ajoutent une force à la capacité globale de détecter et de répondre aux menaces. L’ensemble combiné de fonctionnalités offre la meilleure protection pour les organisations, en particulier les organisations multinationales, par rapport à l’exécution de produits autres que Microsoft. L’image suivante illustre les services et fonctionnalités de protection contre les menaces décrits dans cet article.

![Vue d’ensemble Microsoft 365 Defender.](../media/deploy-threat-protection/deploy-threat-protection-across-m365-overview.png)

Microsoft 365 Defender rassemble les signaux et les données dans un centre de [sécurité Microsoft 365 unifié.](/microsoft-365/security/defender/overview-security-center) 

> [!div class="mx-imgBorder"]
> ![Illustration conceptuelle de Microsoft 365 Defender tableau de bord.](../media/deploy-threat-protection/deploy-threat-protection-across-m365-mtp.png)

## <a name="deployment-overview"></a>Vue d’ensemble du déploiement

L’illustration suivante illustre un chemin d’accès recommandé pour le déploiement de ces fonctionnalités individuelles. 

> [!div class="mx-imgBorder"]
> ![Signaux de protection contre les menaces M365.](../media/deploy-threat-protection/deploy-threat-protection-across-m365.png)

Regardez cette vidéo de présentation du processus de déploiement.
<br><br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vsI7]

Le tableau suivant décrit les différentes solutions/fonctionnalités à configurer et ce qu’elles font.<br/><br/>

|Étape |Solution/fonctionnalités  |Description  |
|--|---------|---------|
| 1 |[Authentification multifacteur et accès conditionnel](deploy-threat-protection-configure.md#step-1-set-up-multi-factor-authentication-and-conditional-access-policies)     |Protégez-vous contre les identités et les appareils compromis. Commencez par cette protection, car elle est de base. La configuration recommandée dans ce guide inclut Azure AD Identity Protection comme condition préalable. Pour plus d’informations, [voir Azure AD Identity Protection.](/azure/security/fundamentals/threat-detection#azure-active-directory-identity-protection)     |
| 2 |[Microsoft Defender pour l’identité](deploy-threat-protection-configure.md#step-2-configure-microsoft-defender-for-identity)     |  Solution de sécurité basée sur le cloud qui utilise vos services de domaine Active Directory (AD DS) locaux pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation. Concentrez-vous ensuite sur Microsoft Defender pour l’identité, car il protège votre infrastructure locale et cloud, n’a pas de dépendances ni de conditions préalables et peut offrir des avantages immédiats en matière de sécurité. Pour plus d’informations, [voir Qu’est-ce que la protection des identités ?](/azure/active-directory/identity-protection/overview-identity-protection) | 
| 3 |[Microsoft 365 Defender](deploy-threat-protection-configure.md#step-3-turn-on-microsoft-365-defender) |Combine les signaux et orchestre les fonctionnalités dans une solution unique. Permet aux professionnels de la sécurité de assembler les signaux des menaces et de déterminer l’étendue et l’impact complets d’une menace. Microsoft 365 Defender des actions automatiques pour empêcher ou arrêter l’attaque et auto-panser les boîtes aux lettres, les points de terminaison et les identités des utilisateurs affectés. Pour plus d’informations, [voir Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). |
| 4  |[Microsoft Defender pour Office 365](deploy-threat-protection-configure.md#step-4-configure-microsoft-defender-for-office-365)     | Protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. Protège contre les programmes malveillants, le hameçonnage, l’usurpation et d’autres types d’attaques. La configuration de Microsoft Defender pour Office 365 est recommandée, car le déploiement du contrôle des changements, de la migration des paramètres à partir d’un système insérez et d’autres considérations peut prendre plus de temps. Pour plus d’informations, [voir Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365).       |
| 5  |[Microsoft Defender pour point de terminaison](deploy-threat-protection-configure.md#step-5-configure-microsoft-defender-for-endpoint)    | Permet d’éviter, de détecter, d’examiner et de répondre aux menaces avancées sur les appareils (également appelés points de terminaison). Defender for Endpoint est une offre de protection contre les menaces robuste. Pour plus d’informations, [voir Microsoft Defender pour le point de terminaison.](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)  |
| 6  |[Microsoft Cloud App Security](deploy-threat-protection-configure.md#step-6-configure-microsoft-cloud-app-security)     | Un courtier de sécurité d’accès au cloud pour la découverte, l’examen et la gouvernance. Vous pouvez activer Microsoft Cloud App Security données pour commencer à collecter des données et des informations. L’implémentation d’informations et d’autres protections ciblées au sein de vos applications SaaS implique une planification et peut prendre plus de temps. Pour plus d’informations, [voir Qu’est-ce Sécurité des applications cloud ?](/cloud-app-security/what-is-cloud-app-security)      | 

> [!TIP]
> Les organisations qui ont plusieurs équipes de sécurité peuvent implémenter des fonctionnalités en parallèle. Par exemple, une équipe peut configurer Defender pour Office 365 tandis qu’une autre équipe configure Defender pour Endpoint. La configuration n’a pas besoin de suivre exactement l’ordre suggéré. 

## <a name="plan-to-deploy-your-threat-protection-solution"></a>Planifier le déploiement de votre solution de protection contre les menaces

Le diagramme suivant illustre le processus de haut niveau pour le déploiement des fonctionnalités de protection contre les menaces. 

![Processus de déploiement des fonctionnalités de protection contre les menaces.](../media/deploy-threat-protection/deploy-threat-protection-across-m365-grid.png)

Pour vous assurer que votre organisation dispose de la meilleure protection possible, définissez et déployez votre [solution](deploy-threat-protection-configure.md) de sécurité avec un processus qui comprend les étapes suivantes :

1. [Configurer l’authentification multifacteur et les stratégies d’accès conditionnel.](deploy-threat-protection-configure.md#step-1-set-up-multi-factor-authentication-and-conditional-access-policies)
2. [Configurez Microsoft Defender pour l’identité.](deploy-threat-protection-configure.md#step-2-configure-microsoft-defender-for-identity)
3. [Activer Microsoft 365 Defender](deploy-threat-protection-configure.md#step-3-turn-on-microsoft-365-defender).
4. [Configurez Defender pour Office 365](deploy-threat-protection-configure.md#step-4-configure-microsoft-defender-for-office-365).
5. [Configurez Microsoft Defender pour le point de terminaison.](deploy-threat-protection-configure.md#step-5-configure-microsoft-defender-for-endpoint)
6. [Configurez Microsoft Cloud App Security](deploy-threat-protection-configure.md#step-6-configure-microsoft-cloud-app-security).
7. [Surveillez l’état et prenez des mesures.](deploy-threat-protection-configure.md#step-7-monitor-status-and-take-actions)
8. [Former les utilisateurs.](deploy-threat-protection-configure.md#step-8-train-users)

Vos fonctionnalités de protection contre les menaces peuvent être configurées en parallèle. Ainsi, si plusieurs équipes de sécurité réseau sont responsables de différents services, elles peuvent configurer les fonctionnalités de protection de votre organisation en même temps.

## <a name="next-step"></a>Étape suivante

Continuez à [configurer les fonctionnalités de protection contre](deploy-threat-protection-configure.md)les menaces dans Microsoft 365 .


