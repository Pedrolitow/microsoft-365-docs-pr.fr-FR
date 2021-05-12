---
title: Migrer de Symantec vers Microsoft Defender pour le point de terminaison
description: Obtenir une vue d’ensemble de la transition de Symantec vers Microsoft Defender pour endpoint
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
- m365solution-symantecmigrate
- m365solution-overview
ms.topic: article
ms.date: 05/10/2021
ms.custom: migrationguides
ms.reviewer: depicker, yongrhee, chriggs
ms.openlocfilehash: 3e3a30ac4d03a40157fd7ec7f06e6e2a82c685a0
ms.sourcegitcommit: 68383240ef7a673d5f28e2ecfab9f105bf1d8c8f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "52327389"
---
# <a name="migrate-from-symantec-to-microsoft-defender-for-endpoint"></a>Migrer de Symantec vers Microsoft Defender pour le point de terminaison
Si vous envisagez de passer de Symantec Endpoint Protection (Symantec) à [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) (Microsoft Defender for Endpoint), vous êtes au bon endroit. Utilisez cet article comme guide.

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

:::image type="content" source="images/symantec-mde-migration.png" alt-text="Vue d’ensemble de la migration de Symantec vers Defender pour endpoint":::

Lorsque vous passez de Symantec à Defender pour endpoint, vous commencez par votre solution Symantec en mode actif, configurez Defender pour Endpoint en mode passif, intégré à Defender pour Endpoint, puis définissez Defender pour Endpoint en mode actif et supprimez Symantec.

## <a name="the-migration-process"></a>Processus de migration

Lorsque vous passez de Symantec à Microsoft Defender pour le point de terminaison, vous suivez un processus qui peut être divisé en trois phases, comme décrit dans le tableau suivant :

![Phases de migration : préparer, configurer, intégrer](images/phase-diagrams/migration-phases.png)

|Phase |Description |
|--|--|
|[Préparer votre migration](symantec-to-microsoft-defender-atp-prepare.md) |Pendant la phase **de** préparation, vous obtenez Microsoft Defender pour point de terminaison, planifiez vos rôles et autorisations et accordez l’accès au Centre de sécurité Microsoft Defender. Vous configurez également les paramètres proxy et Internet de votre appareil pour permettre la communication entre les appareils de votre organisation et Microsoft Defender pour le point de terminaison. |
|[Configurer Microsoft Defender pour le point de terminaison](symantec-to-microsoft-defender-atp-setup.md) |Pendant la phase **d’installation,** vous configurez les paramètres et les exclusions pour l’Antivirus Microsoft Defender et Symantec Endpoint Protection. Vous créez également des groupes d’appareils, des collections et des unités d’organisation. Enfin, vous configurez vos stratégies de logiciel anti-programme malveillant et vos paramètres de protection en temps réel.|
|[Intégration à Microsoft Defender pour le point de terminaison](symantec-to-microsoft-defender-atp-onboard.md) |Pendant  la phase d’intégration, vous intégrerez vos appareils à Microsoft Defender pour point de terminaison et vérifiez que ces appareils communiquent avec Microsoft Defender pour Endpoint. Enfin, vous désinstallez Symantec et assurez-vous que la protection via Microsoft Defender for Endpoint est en mode actif. |

## <a name="whats-included-in-microsoft-defender-for-endpoint"></a>Qu’est-ce qui est inclus dans Microsoft Defender pour le point de terminaison ?

Dans ce guide de migration, nous [](overview-endpoint-detection-response.md) nous concentrons sur la nouvelle génération de [fonctionnalités](microsoft-defender-antivirus-in-windows-10.md) de protection et de détection de points de terminaison et de réponse comme point de départ pour passer à Microsoft Defender pour endpoint. Toutefois, Microsoft Defender pour point de terminaison inclut bien plus que la protection antivirus et de point de terminaison. Microsoft Defender pour point de terminaison est une plateforme de sécurité unifiée pour la protection préventive, la détection après effraction, l’examen automatisé et la réponse. Le tableau suivant récapitule les fonctionnalités de Microsoft Defender pour Point de terminaison. 

| Fonctionnalité/fonctionnalité | Description |
|---|---|
| [Gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md). | Les & de gestion des vulnérabilités permettent d’identifier, d’évaluer et de corriger les faiblesses sur vos points de terminaison (tels que les appareils). |
| [Réduction de la surface d’attaque](overview-attack-surface-reduction.md) | Les règles de réduction de la surface d’attaque contribuent à protéger les appareils et applications de votre organisation contre les cybermenaces et les attaques. |
| [Protection de nouvelle génération](microsoft-defender-antivirus-in-windows-10.md) | La nouvelle génération de protection inclut l’Antivirus Microsoft Defender pour bloquer les menaces et les programmes malveillants. |
| [Détection et réponse du point de terminaison](overview-endpoint-detection-response.md) | Les fonctionnalités de détection et de réponse des points de terminaison détectent, examinent et répondent aux tentatives d’intrusion et aux violations actives.  |
| [Repérage avancé](advanced-hunting-overview.md) | Les fonctionnalités de recherche avancées permettent à votre équipe des opérations de sécurité de localiser des indicateurs et des entités de menaces connues ou potentielles. |
| [Blocage et confinement comportementaux](behavioral-blocking-containment.md) | Les fonctionnalités de blocage du comportement et de contenu permettent d’identifier et d’arrêter les menaces, en fonction de leurs comportements et des arbre de traitement, même lorsque la menace a démarré l’exécution. |
| [Examen et correction automatisés](automated-investigations.md) | Les fonctionnalités d’examen et de réponse automatisées examinent les alertes et prennent des mesures correctives immédiates pour résoudre les violations. |
| [Service de recherche de menaces](microsoft-threat-experts.md) (experts microsoft en matière de menaces) | Les services de recherche de menace fournissent aux équipes des opérations de sécurité une surveillance et une analyse de niveau expert, et pour vous assurer que les menaces critiques ne sont pas manquées. |

**Vous souhaitez en savoir plus ? Voir [Microsoft Defender pour le point de terminaison.](microsoft-defender-endpoint.md)**

## <a name="next-step"></a>Étape suivante

- Continuez à [préparer votre migration.](symantec-to-microsoft-defender-atp-prepare.md)
