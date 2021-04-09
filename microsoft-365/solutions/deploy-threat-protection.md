---
title: Déployer les fonctionnalités de protection contre les menaces dans Microsoft 365
description: Obtenez une vue d’ensemble des services de protection contre les menaces et des fonctionnalités de sécurité dans Microsoft 365 E5. Protégez vos comptes d’utilisateurs, appareils, contenu de messagerie, etc. avec Microsoft 365 E5.
keywords: protection avancée contre les menaces, sécurité, microsoft 365 E5, solution, protéger les appareils, defender
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.technology: m365d
audience: Admin
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-threatprotection
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: ea28e9c244b6b8faaeb9b1f3685d57169605cbb9
ms.sourcegitcommit: a46532bb422ee51331f478ff50cc5444586bf6a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2021
ms.locfileid: "51650313"
---
# <a name="deploy-threat-protection-capabilities-across-microsoft-365-e5"></a>Déployer des fonctionnalités de protection contre les menaces dans Microsoft 365 E5

Cette solution décrit les puissantes fonctionnalités de protection contre les menaces dans Microsoft 365 E5. Lisez cette solution pour obtenir une vue d’ensemble des fonctionnalités incluses, de son fonctionnement et de la façon de commencer à déployer ces fonctionnalités dans votre organisation.

## <a name="why-protecting-against-threats-is-important"></a>Pourquoi la protection contre les menaces est-elle importante ? 

[Les programmes](/windows/security/threat-protection/intelligence/understanding-malware)malveillants et les cyberattaques sophistiquées, telles que les menaces sans [fichier,](/windows/security/threat-protection/intelligence/fileless-threats)sont une occurrence courante. Les entreprises doivent se protéger elles-mêmes et leurs clients avec des fonctionnalités de sécurité informatique efficaces. Les cyberattaques peuvent entraîner des problèmes majeurs pour votre organisation, allant d’une perte de confiance à des difficultés financières, à des temps d’arrêt de l’activité et bien plus encore. La protection contre les menaces est importante, mais il peut être difficile de déterminer où concentrer le temps, les efforts et les ressources de votre organisation. Microsoft 365 E5 peut vous aider. 

Les solutions de sécurité Microsoft sont intégrées à nos produits et services. Les fonctionnalités d’automatisation et d’apprentissage automatique réduisent la charge sur vos équipes de sécurité pour vous assurer que les éléments qui vous sont nécessaires sont traités. Et la force des solutions de sécurité Microsoft repose sur des nombres de signaux que nous traiterons tous les jours dans notre Graphique de [sécurité intelligent.](/graph/security-concept-overview) Microsoft 365 security solutions include [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md), a solution that brings together signals across your email, data, devices, and identities to paint a picture of advanced threats against your organization.

Regardez cette vidéo de présentation du processus de déploiement.
<br><br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vsI7]


## <a name="threat-protection-in-microsoft-365-e5"></a>Protection contre les menaces dans Microsoft 365 E5

[Microsoft 365 E5](https://www.microsoft.com/microsoft-365/enterprise-e5-business-software?activetab=pivot%3aoverviewtab) vous permet de protéger votre organisation avec une intelligence intégrée adaptative. Grâce aux fonctionnalités de protection contre les menaces de Microsoft 365 E5, vous pouvez détecter et examiner les menaces avancées, les identités compromises et les actions malveillantes dans votre environnement local et cloud.

Dans Microsoft 365 E5, les fonctionnalités de protection contre les menaces sont intégrées par défaut. Les signaux de chaque fonctionnalité ajoutent une force à la capacité globale de détecter et de répondre aux menaces. L’ensemble combiné de fonctionnalités offre la meilleure protection pour les organisations, en particulier les organisations multinationales, par rapport à l’exécution de produits autres que Microsoft. L’image suivante illustre les services et fonctionnalités de protection contre les menaces dans Microsoft 365 E5 décrits dans cet article.

![Vue d’ensemble de Microsoft 365 Defender](../media/deploy-threat-protection/deploy-threat-protection-across-m365-overview.png)

Microsoft 365 Defender rassemble les signaux et les données dans un centre de sécurité [Microsoft 365 unifié.](/microsoft-365/security/defender/overview-security-center) 

> [!div class="mx-imgBorder"]
> ![Illustration conceptuelle du tableau de bord Microsoft 365 Defender](../media/deploy-threat-protection/deploy-threat-protection-across-m365-mtp.png)

L’illustration suivante illustre un chemin d’accès recommandé pour le déploiement de ces fonctionnalités individuelles. 

> [!div class="mx-imgBorder"]
> ![Signaux de protection contre les menaces M365](../media/deploy-threat-protection/deploy-threat-protection-across-m365.png)

|Solution/fonctionnalités  |Description  |
|---------|---------|
|Authentification multifacteur et accès conditionnel     |Protégez-vous contre les identités et les appareils compromis. Commencez par cette protection, car elle est de base. La configuration recommandée dans ce guide inclut Azure AD Identity Protection comme condition préalable.     |
|Microsoft Defender pour Identity     |  Solution de sécurité basée sur le cloud qui exploite vos signaux AD DS (Active Directory Domain Services) locaux pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions malveillantes internes dirigées contre votre organisation. Concentrez-vous ensuite sur Microsoft Defender pour l’identité, car il protège votre infrastructure locale et cloud, n’a pas de dépendances ni de conditions préalables et peut offrir des avantages immédiats en matière de sécurité. | 
|Microsoft Defender pour Office 365     | Protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. Protection contre les programmes malveillants, le hameçonnage, l’usurpation et d’autres types d’attaques. La configuration de Microsoft Defender pour Office 365 est recommandée ensuite, car le déploiement du contrôle des changements, de la migration des paramètres à partir d’un système insérez et d’autres considérations peut prendre plus de temps. <p>**REMARQUE**: veillez à configurer les fonctionnalités de protection contre les menaces incluses dans tous les abonnements Office 365 (Exchange Online Protection).       |
|Microsoft Defender pour point de terminaison    | Plateforme de protection des points de terminaison qui permet d’éviter, de détecter, d’examiner et de répondre aux menaces avancées.  Le déploiement de Defender for Endpoint peut prendre un certain temps, mais la configuration peut être effectuée en parallèle avec d’autres fonctionnalités.   |
|Microsoft Cloud App Security     |   Un courtier de sécurité d’accès au cloud pour la découverte, l’examen et la gouvernance. Vous pouvez activer Microsoft Cloud App Security tôt pour commencer à collecter des données et des informations. L’implémentation d’informations et d’autres protections ciblées au sein de vos applications SaaS implique une planification et peut prendre plus de temps.       | 

> [!TIP]
> Les organisations qui ont plusieurs équipes de sécurité peuvent implémenter ces fonctionnalités en parallèle. 

## <a name="plan-to-deploy-your-threat-protection-solution"></a>Planifier le déploiement de votre solution de protection contre les menaces

Le diagramme suivant illustre le processus de haut niveau pour le déploiement des fonctionnalités de protection contre les menaces. 

![Processus de déploiement des fonctionnalités de protection contre les menaces](../media/deploy-threat-protection/deploy-threat-protection-across-m365-grid.png)

Pour vous assurer que votre organisation dispose de la meilleure protection possible, définissez et déployez votre solution de sécurité à l’aide d’un processus qui comprend les étapes suivantes :

1. [Configurer l’authentification multifacteur et les stratégies d’accès conditionnel.](deploy-threat-protection-configure.md#step-1-set-up-multi-factor-authentication-and-conditional-access-policies)
2. [Configurez Microsoft Defender pour l’identité.](deploy-threat-protection-configure.md#step-2-configure-microsoft-defender-for-identity)
3. [Activer Microsoft 365 Defender.](deploy-threat-protection-configure.md#step-3-turn-on-microsoft-365-defender)
4. [Configurez Defender pour Office 365.](deploy-threat-protection-configure.md#step-4-configure-microsoft-defender-for-office-365)
5. [Configurez Microsoft Defender pour le point de terminaison.](deploy-threat-protection-configure.md#step-5-configure-microsoft-defender-for-endpoint)
6. [Configurer Microsoft Cloud App Security](deploy-threat-protection-configure.md#step-6-configure-microsoft-cloud-app-security).
7. [Surveillez l’état et prenez des mesures.](deploy-threat-protection-configure.md#step-7-monitor-status-and-take-actions)
8. [Former les utilisateurs.](deploy-threat-protection-configure.md#step-8-train-users)

Vos fonctionnalités de protection contre les menaces peuvent être configurées en parallèle. Ainsi, si plusieurs équipes de sécurité réseau sont responsables de différents services, elles peuvent configurer les fonctionnalités de protection de votre organisation en même temps.

## <a name="next-step"></a>Étape suivante

Procédez à [la configuration des fonctionnalités de protection contre les menaces dans Microsoft 365.](deploy-threat-protection-configure.md)


