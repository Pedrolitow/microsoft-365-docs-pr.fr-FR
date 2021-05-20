---
title: Migrer de Mc Antivirus vers Microsoft Defender pour le point de terminaison
description: Passez de Mc Antivirus à Microsoft Defender pour le point de terminaison. Lisez cet article pour obtenir une vue d’ensemble.
keywords: migration, Microsoft Defender pour point de terminaison, edr
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-mcafeemigrate
- m365solution-overview
ms.topic: article
ms.custom: migrationguides
ms.date: 05/14/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 5bbcf885ec160204916507aee60398aee35e470b
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52538050"
---
# <a name="migrate-from-mcafee-to-microsoft-defender-for-endpoint"></a>Migrer de Mc Antivirus vers Microsoft Defender pour le point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Si vous envisagez de passer de Mc Antivirus Endpoint Security (Mc Antivirus) à [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) (Microsoft Defender for Endpoint), vous êtes au bon endroit. Utilisez cet article comme guide.


:::image type="content" source="images/mcafee-mde-migration.png" alt-text="Vue d’ensemble de la migration de Mc Antivirus vers Defender pour endpoint":::

Lorsque vous passez de Mc Antivirus à Defender pour point de terminaison, vous commencez par votre solution Mc Antivirus en mode actif, configurez Defender pour Endpoint en mode passif, intégrer Defender pour Point de terminaison, puis définissez Defender pour Point de terminaison sur le mode actif et supprimez Mc Antivirus.

## <a name="the-migration-process"></a>Processus de migration

Lorsque vous passez de Mc Antivirus à Microsoft Defender pour le point de terminaison, vous suivez un processus qui peut être divisé en trois phases : Préparer, Installer et Intégrer. 

![Phases de migration : préparer l’intégration de l’installation](images/phase-diagrams/migration-phases.png)

|Phase |Description |
|--|--|
|[Préparer votre migration](mcafee-to-microsoft-defender-prepare.md) |Pendant la phase [**de**](mcafee-to-microsoft-defender-prepare.md) préparation, vous mettez à jour les appareils de votre organisation, obtenez Microsoft Defender pour le point de terminaison, planifiez vos rôles et autorisations et accordez l’accès au Centre de sécurité Microsoft Defender. Vous configurez également les paramètres proxy et Internet de votre appareil pour permettre la communication entre les appareils de votre organisation et Microsoft Defender pour le point de terminaison. |
|[Configurer Microsoft Defender pour le point de terminaison](mcafee-to-microsoft-defender-setup.md) |Pendant la phase [**d’installation,**](mcafee-to-microsoft-defender-setup.md) vous activez Antivirus Microsoft Defender et définissez-le en mode passif. Vous configurez également les paramètres & exclusions pour Antivirus Microsoft Defender et votre solution de protection de point de terminaison existante. Ensuite, vous créez vos groupes d’appareils, collections et unités d’organisation. Enfin, vous configurez vos stratégies de logiciel anti-programme malveillant et vos paramètres de protection en temps réel.|
|[Intégration à Microsoft Defender pour le point de terminaison](mcafee-to-microsoft-defender-onboard.md) |Pendant la [**phase**](mcafee-to-microsoft-defender-onboard.md) d’intégration, vous intégrerez vos appareils à Microsoft Defender pour point de terminaison, vérifiez que Antivirus Microsoft Defender est en cours d’exécution en mode passif et vérifiez que vos points de terminaison communiquent avec Defender pour Endpoint. Ensuite, vous désinstallez Mc Antivirus et assurez-vous que Defender pour le point de terminaison fonctionne correctement. |

## <a name="whats-included-in-microsoft-defender-for-endpoint"></a>Qu’est-ce qui est inclus dans Microsoft Defender pour le point de terminaison ?

Dans ce guide de migration, nous [](overview-endpoint-detection-response.md) nous concentrons sur les fonctionnalités de [protection](microsoft-defender-antivirus-in-windows-10.md) et de protection évolutive des points de terminaison nouvelle génération comme point de départ pour passer à Microsoft Defender pour endpoint. Toutefois, Microsoft Defender pour point de terminaison inclut bien plus que la protection antivirus et de point de terminaison. Microsoft Defender pour point de terminaison est une plateforme de sécurité unifiée pour la protection préventive, la détection après effraction, l’examen automatisé et la réponse. Le tableau suivant récapitule les fonctionnalités de Microsoft Defender pour Point de terminaison. 

| Fonctionnalité/fonctionnalité | Description |
|---|---|
| [Gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md). | Les fonctionnalités & gestion des vulnérabilités menace permettent d’identifier, d’évaluer et de corriger les faiblesses sur vos points de terminaison (tels que les appareils). |
| [Réduction de la surface d’attaque](overview-attack-surface-reduction.md) | Les règles de réduction de la surface d’attaque contribuent à protéger les appareils et applications de votre organisation contre les cybermenaces et les attaques. |
| [Protection de nouvelle génération](microsoft-defender-antivirus-in-windows-10.md) | La protection nouvelle génération inclut des Antivirus Microsoft Defender pour bloquer les menaces et les programmes malveillants. |
| [Détection et réponse du point de terminaison](overview-endpoint-detection-response.md) | Les fonctionnalités de détection et de réponse des points de terminaison détectent, examinent et répondent aux tentatives d’intrusion et aux violations actives.  |
| [Repérage avancé](advanced-hunting-overview.md) | Les fonctionnalités de recherche avancées permettent à votre équipe des opérations de sécurité de localiser des indicateurs et des entités de menaces connues ou potentielles. |
| [Blocage et confinement comportementaux](behavioral-blocking-containment.md) | Les fonctionnalités de blocage du comportement et de contenu permettent d’identifier et d’arrêter les menaces, en fonction de leurs comportements et des arbre de traitement, même lorsque la menace a démarré l’exécution. |
| [Examen et correction automatisés](automated-investigations.md) | Les fonctionnalités d’examen et de réponse automatisées examinent les alertes et prennent des mesures correctives immédiates pour résoudre les violations. |
| [Service de recherche de menaces](microsoft-threat-experts.md) (Spécialistes des menaces Microsoft) | Les services de recherche de menace fournissent aux équipes des opérations de sécurité une surveillance et une analyse de niveau expert, et pour vous assurer que les menaces critiques ne sont pas manquées. |

**Vous souhaitez en savoir plus ? Voir [Microsoft Defender pour le point de terminaison.](microsoft-defender-endpoint.md)**

## <a name="next-step"></a>Étape suivante

- Continuez à [préparer votre migration.](mcafee-to-microsoft-defender-prepare.md)
