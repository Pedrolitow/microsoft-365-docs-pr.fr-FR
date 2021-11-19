---
title: Activer l’environnement d’évaluation pour Microsoft Defender pour les applications cloud
description: Découvrez l’architecture de Defender pour les applications cloud dans Microsoft Defender pour Office 365 et comprenez les interactions entre les produits Microsoft 365 Defender cloud.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: e62a87188eb3a092399ef03647a9c70318f37197
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61106538"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-cloud-apps"></a>Activer l’environnement d’évaluation pour Microsoft Defender pour les applications cloud

**S’applique à :**

- Microsoft 365 Defender

Cet article est [l’étape 2 sur 2](eval-defender-mcas-overview.md) dans le processus de configuration de l’environnement d’évaluation de Microsoft Defender pour les applications cloud. Pour plus d’informations sur ce processus, voir [l’article de présentation.](eval-defender-mcas-overview.md)

Cet article vous explique comment accéder au portail Defender pour les applications cloud et configurer l’intégration nécessaire pour collecter les données de trafic des applications cloud.

Pour découvrir les applications cloud utilisées dans votre environnement, vous pouvez :

- Préparez-vous rapidement à la découverte cloud en intégrant Microsoft Defender pour Endpoint. Cette intégration native vous permet de commencer immédiatement à collecter des données sur le trafic cloud sur vos appareils Windows 10 et Windows 11, sur et hors de votre réseau.
- Pour découvrir toutes les applications cloud accessibles par tous les appareils connectés à votre réseau, déployez le collecteur de journaux Defender for Cloud Apps sur vos pare-feu et autres proxies. Cela permet de collecter des données à partir de vos points de terminaison et de les envoyer à Defender pour les applications cloud pour analyse. Defender pour les applications cloud s’intègre en natif à certains proxies tiers pour encore plus de fonctionnalités.

Cet article contient des conseils pour les deux méthodes.

Utilisez les étapes suivantes pour configurer Microsoft Defender pour les applications cloud.

![Étapes permettant d’activer Microsoft Defender pour les applications cloud dans l’environnement d’évaluation de Microsoft Defender.](../../media/defender/m365-defender-mcas-eval-enable-steps.png)

- [Étape 1. Connecter au portail Defender pour les applications cloud](#step-1)
- [Étape 2. Intégration à Microsoft Defender pour point de terminaison](#step-2)
- [Étape 3. Déployer le collecteur de journaux Defender pour les applications cloud sur vos pare-feu et autres proxies](#step-3)
- [Étape 4. Afficher le tableau de bord de découverte cloud pour voir quelles applications sont utilisées dans votre organisation](#step-4)

<a name="step-1"></a>

## <a name="step-1-connect-to-the-defender-for-cloud-apps-portal"></a>Étape 1. Connecter au portail Defender pour les applications cloud

Pour vérifier la gestion des licences et vous connecter au portail Defender pour les applications cloud, voir Démarrage rapide : Mise en place de [Microsoft Defender pour les applications cloud.](/cloud-app-security/getting-started-with-cloud-app-security)

Si vous n’êtes pas immédiatement en mesure de vous connecter au portail, vous devrez peut-être ajouter l’adresse IP à la liste d’adresses IP de votre pare-feu. Voir [configuration de base de Defender pour les applications cloud.](/cloud-app-security/general-setup)

Si vous avez encore des difficultés, examinez la [exigences du réseau.](/cloud-app-security/network-requirements)

<a name="step-2"></a>

## <a name="step-2-integrate-with-microsoft-defender-for-endpoint"></a>Étape 2. Intégration à Microsoft Defender pour point de terminaison

Microsoft Defender pour les applications cloud s’intègre à Microsoft Defender pour Endpoint en natif. L’intégration simplifie le déploiement de la découverte cloud, étend les fonctionnalités de découverte cloud au-delà de votre réseau d’entreprise et permet une investigation basée sur l’appareil. Cette intégration révèle que les applications et services cloud sont accessibles à partir d’appareils gérés Windows 10 et Windows 11 informatiques.

Si vous avez déjà configuré Microsoft Defender pour Endpoint, la configuration de l’intégration avec Defender pour les applications cloud est un basculement Microsoft 365 Defender. Une fois l’intégration désactivée, vous pouvez revenir au portail Defender pour les applications cloud et afficher des données enrichies dans le Tableau de bord de découverte cloud.

Pour effectuer ces tâches, consultez Microsoft Defender pour l’intégration des points de [terminaison avec Microsoft Defender pour les applications cloud.](/cloud-app-security/mde-integration)

<a name="step-3"></a>

## <a name="step-3-deploy-the-defender-for-cloud-apps-log-collector-on-your-firewalls-and-other-proxies"></a>Étape 3. Déployer le collecteur de journaux Defender pour les applications cloud sur vos pare-feu et autres proxies

Pour une couverture sur tous les appareils connectés à votre réseau, déployez le collecteur de journaux Defender for Cloud Apps sur vos pare-feu et autres proxies pour collecter des données à partir de vos points de terminaison et les envoyer à Defender for Cloud Apps pour analyse.

Si vous utilisez l’une des passerelles Web sécurisées (SWG) suivantes, Defender pour les applications cloud offre un déploiement et une intégration transparents :

- Zscaler
- iboss
- Corrata
- Sécurité Menlo

Pour plus d’informations sur l’intégration à ces périphériques réseau, voir [Configurer la découverte cloud.](/cloud-app-security/set-up-cloud-discovery)

<a name="step-4"></a>

## <a name="step-4-view-the-cloud-discovery-dashboard-to-see-what-apps-are-being-used-in-your-organization"></a>Étape 4. Afficher le tableau de bord de découverte cloud pour voir quelles applications sont utilisées dans votre organisation

Le tableau de bord de découverte cloud est conçu pour vous donner plus d’informations sur la façon dont les applications cloud sont utilisées dans votre organisation. Il fournit une vue d’ensemble rapide des types d’applications utilisés, de vos alertes ouvertes et des niveaux de risque des applications dans votre organisation.

Pour commencer à utiliser le tableau de bord de découverte cloud, voir [Utilisation des applications découvertes.](/cloud-app-security/discovered-apps)

## <a name="next-steps"></a>Prochaines étapes

Étape 3 sur 3 : Piloter [Microsoft Defender pour les applications cloud](eval-defender-mcas-pilot.md)

Revenir à la vue d’ensemble [de l’évaluation de Microsoft Defender pour les applications cloud](eval-defender-mcas-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md)
