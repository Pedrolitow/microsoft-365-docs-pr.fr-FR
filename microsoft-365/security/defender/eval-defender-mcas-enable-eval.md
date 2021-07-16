---
title: Activer l’environnement d’évaluation pour Microsoft Cloud App Security
description: Découvrez l’architecture de MCAS dans Microsoft Defender pour Office 365 et comprendre les interactions entre les produits Microsoft 365 Defender client.
keywords: Microsoft 365 Defender essai, essayez Microsoft 365 Defender, évaluez Microsoft 365 Defender, laboratoire d’évaluation Microsoft 365 Defender, pilote Microsoft 365 Defender, cybersécurité, menace avancée persistante, sécurité d’entreprise, appareils, appareil, identité, utilisateurs, données, applications, incidents, examen et correction automatisés, recherche avancée
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6ada9613f852e085158b7002cbbb9a9928d36d58
ms.sourcegitcommit: 718759c7146062841f7eb4a0a9a8bdddce0139b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2021
ms.locfileid: "53457763"
---
# <a name="enable-the-evaluation-environment-for-microsoft-cloud-app-security"></a>Activer l’environnement d’évaluation pour Microsoft Cloud App Security


**S’applique à :**

- Microsoft 365 Defender

Cet article est [l’étape 2 sur 2](eval-defender-mcas-overview.md) dans le processus de configuration de l’environnement d’évaluation pour Microsoft Cloud App Security. Pour plus d’informations sur ce processus, voir [l’article de présentation.](eval-defender-mcas-overview.md)

Cet article vous explique comment accéder au portail Sécurité des applications cloud et configurer l’intégration nécessaire pour collecter les données de trafic des applications cloud.

Pour découvrir les applications cloud utilisées dans votre environnement, vous pouvez :

- Préparez-vous rapidement avec la découverte cloud en intégrant Microsoft Defender pour Endpoint. Cette intégration native vous permet de commencer immédiatement à collecter des données sur le trafic cloud sur vos appareils Windows 10, sur et hors de votre réseau.
- Pour découvrir toutes les applications cloud accessibles par tous les appareils connectés à votre réseau, déployez le collecteur de journaux Sécurité des applications cloud sur vos pare-feu et autres proxies. Cela permet de collecter des données à partir de vos points de terminaison et de les envoyer Sécurité des applications cloud pour analyse. Sécurité des applications cloud s’intègre en natif à certains proxies tiers pour encore plus de fonctionnalités.

Cet article contient des conseils pour les deux méthodes.

Utilisez les étapes suivantes pour configurer Microsoft Cloud App Security.

![Étapes pour activer Microsoft Microsoft Cloud App Security dans l’environnement d’évaluation Microsoft Defender](../../media/defender/m365-defender-mcas-eval-enable-steps.png)

- [Étape 1. Connecter sur le portail Sécurité des applications cloud client](#step-1-connect-to-the-cloud-app-security-portal)
- [Étape 2. Intégration à Microsoft Defender pour point de terminaison](#step-2-integrate-with-microsoft-defender-for-endpoint)
- [Étape 3. Déployer le collecteur Sécurité des applications cloud journaux sur vos pare-feu et autres proxies](#step-3-deploy-the-cloud-app-security-log-collector-on-your-firewalls-and-other-proxies)
- [Étape 4. Afficher le tableau de bord de découverte cloud pour voir quelles applications sont utilisées dans votre organisation](#step-4-view-the-cloud-discovery-dashboard-to-see-what-apps-are-being-used-in-your-organization)

## <a name="step-1-connect-to-the-cloud-app-security-portal"></a>Étape 1. Connecter sur le portail Sécurité des applications cloud client

Pour vérifier les licences et vous connecter au portail Sécurité des applications cloud, voir Démarrage rapide : prendre en Microsoft Cloud App Security [.](/cloud-app-security/getting-started-with-cloud-app-security) 

Si vous n’êtes pas immédiatement en mesure de vous connecter au portail, vous devrez peut-être ajouter l’adresse IP à la liste d’adresses IP de votre pare-feu. Voir [Configuration de base pour Sécurité des applications cloud](/cloud-app-security/general-setup).

Si vous avez encore des difficultés, examinez la [exigences du réseau.](/cloud-app-security/network-requirements)

## <a name="step-2-integrate-with-microsoft-defender-for-endpoint"></a>Étape 2. Intégration à Microsoft Defender pour point de terminaison

Microsoft Cloud App Security s’intègre à Microsoft Defender pour Endpoint en natif. L’intégration simplifie le déploiement de la découverte cloud, étend les fonctionnalités de découverte cloud au-delà de votre réseau d’entreprise et permet une enquête basée sur l’appareil. Cette intégration révèle l’accès aux applications et services cloud à partir d’appareils gérés par Windows 10 informatique. 

Si vous avez déjà configuré Microsoft Defender pour Endpoint, la configuration de l’intégration avec Sécurité des applications cloud est un basculement Microsoft 365 Defender. Une fois l’intégration désactivée, vous pouvez revenir au portail Sécurité des applications cloud et afficher des données enrichies dans le Tableau de bord de découverte cloud.

Pour effectuer ces tâches, voir [Microsoft Defender pour l’intégration de point](/cloud-app-security/mde-integration)de terminaison avec Microsoft Cloud App Security . 

## <a name="step-3-deploy-the-cloud-app-security-log-collector-on-your-firewalls-and-other-proxies"></a>Étape 3. Déployer le collecteur Sécurité des applications cloud journaux sur vos pare-feu et autres proxies

Pour une couverture sur tous les appareils connectés à votre réseau, déployez le collecteur de journaux Sécurité des applications cloud sur vos pare-feu et autres proxies pour collecter des données à partir de vos points de terminaison et les envoyer à Sécurité des applications cloud pour analyse. 

Si vous utilisez l’une des passerelles Web sécurisées (SWG) suivantes, Sécurité des applications cloud un déploiement et une intégration transparents :
- Zscaler
- iboss
- Corrata
- Sécurité Menlo

Pour plus d’informations sur l’intégration à ces périphériques réseau, voir [Configurer la découverte cloud.](/cloud-app-security/set-up-cloud-discovery) 
## <a name="step-4-view-the-cloud-discovery-dashboard-to-see-what-apps-are-being-used-in-your-organization"></a>Étape 4. Afficher le tableau de bord de découverte cloud pour voir quelles applications sont utilisées dans votre organisation

Le tableau de bord de découverte cloud est conçu pour vous donner plus d’informations sur la façon dont les applications cloud sont utilisées dans votre organisation. Il fournit une vue d’ensemble rapide des types d’applications utilisés, de vos alertes ouvertes et des niveaux de risque des applications dans votre organisation. 

Pour commencer à utiliser le tableau de bord de découverte cloud, voir [Utilisation des applications découvertes.](/cloud-app-security/discovered-apps)

## <a name="next-steps"></a>Étapes suivantes

Étape 3 sur 3 : [Pilote Microsoft Cloud App Security](eval-defender-mcas-pilot.md)

Revenir à la vue d’ensemble de [l’Microsoft Cloud App Security](eval-defender-mcas-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md)