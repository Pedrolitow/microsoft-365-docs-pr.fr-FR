---
title: Activer l’environnement d’évaluation pour Microsoft Defender for Cloud Apps
description: Découvrez l’architecture de Defender pour Cloud Apps dans Microsoft Defender pour Office 365 et comprenez les interactions entre les produits Microsoft 365 Defender.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
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
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
- highpri
ms.topic: conceptual
ms.openlocfilehash: 11a86a99da5709c76fd40263745589e71a8ed54d
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67481765"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-cloud-apps"></a>Activer l’environnement d’évaluation pour Microsoft Defender for Cloud Apps

**S’applique à :**

- Microsoft 365 Defender

Cet article est [l’étape 2 sur 2](eval-defender-mcas-overview.md) du processus de configuration de l’environnement d’évaluation pour Microsoft Defender for Cloud Apps. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-mcas-overview.md).

Cet article vous guide tout au long du processus d’accès au portail Defender pour Cloud Apps et de configuration de l’intégration nécessaire pour collecter les données de trafic des applications cloud.

Pour découvrir les applications cloud utilisées dans votre environnement, vous pouvez implémenter une ou les deux méthodes suivantes :

- Démarrez rapidement avec Cloud Discovery en vous intégrant à Microsoft Defender pour point de terminaison. Cette intégration native vous permet de commencer immédiatement à collecter des données sur le trafic cloud sur vos appareils Windows 10 et Windows 11, sur et hors de votre réseau.
- Pour découvrir toutes les applications cloud accessibles par tous les appareils connectés à votre réseau, déployez le collecteur de journaux Defender pour Cloud Apps sur vos pare-feu et autres proxys. Ce déploiement permet de collecter des données à partir de vos points de terminaison et de les envoyer à Defender pour Cloud Apps à des fins d’analyse. Defender pour Cloud Apps s’intègre en mode natif à certains proxys tiers pour encore plus de fonctionnalités.

Cet article contient des conseils pour les deux méthodes.

Procédez comme suit pour configurer Microsoft Defender for Cloud Apps.

:::image type="content" source="../../media/defender/m365-defender-mcas-eval-enable-steps.png" alt-text="Étapes permettant d’activer Microsoft Microsoft Defender for Cloud Apps dans l’environnement d’évaluation Microsoft Defender" lightbox="../../media/defender/m365-defender-mcas-eval-enable-steps.png":::

- [Étape 1. Se connecter au portail Defender pour Cloud Apps](#step-1)
- [Étape 2. Intégrer à Microsoft Defender pour point de terminaison](#step-2)
- [Étape 3. Déployer le collecteur de journaux Defender pour Cloud Apps sur vos pare-feu et autres proxys](#step-3)
- [Étape 4. Afficher le tableau de bord Cloud Discovery pour voir quelles applications sont utilisées dans votre organisation](#step-4)

<a name="step-1"></a>

## <a name="step-1-connect-to-the-defender-for-cloud-apps-portal"></a>Étape 1. Se connecter au portail Defender pour Cloud Apps

Pour vérifier les licences et se connecter au portail Defender pour Cloud Apps, consultez [Démarrage rapide : Bien démarrer avec Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security).

Si vous n’êtes pas immédiatement en mesure de vous connecter au portail, vous devrez peut-être ajouter l’adresse IP à la liste verte de votre pare-feu. Consultez [la configuration de base pour Defender pour Cloud Apps](/cloud-app-security/general-setup).

Si vous rencontrez toujours des problèmes, passez en revue les [exigences du réseau](/cloud-app-security/network-requirements).

<a name="step-2"></a>

## <a name="step-2-integrate-with-microsoft-defender-for-endpoint"></a>Étape 2. Intégrer à Microsoft Defender pour point de terminaison

Microsoft Defender for Cloud Apps s’intègre à Microsoft Defender pour point de terminaison en mode natif. L’intégration simplifie le déploiement de Cloud Discovery, étend les fonctionnalités cloud discovery au-delà de votre réseau d’entreprise et permet l’investigation basée sur les appareils. Cette intégration révèle que les applications et services cloud sont accessibles à partir d’appareils Windows 10 et Windows 11 gérés par l’informatique.

Si vous avez déjà configuré Microsoft Defender pour point de terminaison, la configuration de l’intégration à Defender pour Cloud Apps est un basculement dans Microsoft 365 Defender. Une fois l’intégration activée, vous pouvez revenir au portail Defender pour Cloud Apps et afficher des données enrichies dans le tableau de bord Cloud Discovery.

Pour effectuer ces tâches, consultez [Microsoft Defender pour point de terminaison intégration à Microsoft Defender for Cloud Apps](/cloud-app-security/mde-integration).

<a name="step-3"></a>

## <a name="step-3-deploy-the-defender-for-cloud-apps-log-collector-on-your-firewalls-and-other-proxies"></a>Étape 3. Déployer le collecteur de journaux Defender pour Cloud Apps sur vos pare-feu et autres proxys

Pour une couverture sur tous les appareils connectés à votre réseau, déployez le collecteur de journaux Defender pour Cloud Apps sur vos pare-feu et autres proxys pour collecter des données à partir de vos points de terminaison et les envoyer à Defender pour Cloud Apps à des fins d’analyse.

Si vous utilisez l’une des passerelles web sécurisées (SWG) suivantes, Defender pour Cloud Apps offre un déploiement et une intégration transparents :

- Zscaler
- iboss
- Corrata
- Menlo Security

Pour plus d’informations sur l’intégration à ces appareils réseau, consultez [Configurer Cloud Discovery](/cloud-app-security/set-up-cloud-discovery).

<a name="step-4"></a>

## <a name="step-4-view-the-cloud-discovery-dashboard-to-see-what-apps-are-being-used-in-your-organization"></a>Étape 4. Afficher le tableau de bord Cloud Discovery pour voir quelles applications sont utilisées dans votre organisation

Le tableau de bord Cloud Discovery est conçu pour vous donner plus d’informations sur la façon dont les applications cloud sont utilisées dans votre organisation. Il fournit une vue d’ensemble des types d’applications utilisés, de vos alertes ouvertes et des niveaux de risque des applications de votre organisation.

Pour commencer à utiliser le tableau de bord Cloud Discovery, consultez [Utilisation des applications découvertes](/cloud-app-security/discovered-apps).

## <a name="next-steps"></a>Prochaines étapes

Étape 3 sur 3 : [Pilote Microsoft Defender for Cloud Apps](eval-defender-mcas-pilot.md)

Revenir à la vue d’ensemble de [Evaluate Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)
