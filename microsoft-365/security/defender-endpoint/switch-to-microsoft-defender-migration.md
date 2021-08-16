---
title: Passer de la protection de point de terminaison non-Microsoft à Microsoft Defender pour le point de terminaison
description: Basculez vers Microsoft Defender pour le point de terminaison. Lisez cet article pour obtenir une vue d’ensemble.
keywords: migration, protection avancée des points de terminaison Windows Defender, pour Endpoint, edr
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
- m365solution-migratetomdatp
- m365solution-overview
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
ms.topic: conceptual
ms.custom: migrationguides
ms.date: 06/14/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: eeb2a64c82d5edec57e7f53a00d8dcedcfadc2900161462b826392a1fea4c2be
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53897742"
---
# <a name="make-the-switch-from-non-microsoft-endpoint-protection-to-microsoft-defender-for-endpoint"></a>Passer de la protection de point de terminaison non-Microsoft à Microsoft Defender pour le point de terminaison

Si vous envisagez de passer d’une solution de protection de point de terminaison non-Microsoft à [Microsoft Defender pour point](microsoft-defender-endpoint.md) de terminaison (Defender pour point de terminaison), vous êtes au bon endroit. Utilisez cet article comme guide.

:::image type="content" source="images/nonms-mde-migration.png" alt-text="Vue d’ensemble de la migration vers Defender pour le point de terminaison":::

Lorsque vous basculez vers Defender pour le point de terminaison, vous commencez par votre solution non-Microsoft fonctionnant en mode actif. Ensuite, vous configurez Defender pour Endpoint en mode passif et vous intégrerez vos appareils à Defender for Endpoint. Ensuite, vous définissez Defender pour le point de terminaison sur le mode actif. Enfin, vous supprimez la solution non-Microsoft.

## <a name="the-migration-process"></a>Processus de migration

Le processus de migration vers Defender pour Endpoint peut être divisé en trois phases, comme décrit dans le tableau suivant :

![Phases de migration : préparer, configurer, intégrer](images/phase-diagrams/migration-phases.png)

|Phase |Description |
|--|--|
|[Préparer votre migration](switch-to-microsoft-defender-prepare.md) |Pendant [la phase **de** préparation](switch-to-microsoft-defender-prepare.md): <p>1. Mettez à jour les appareils de votre organisation. <p>2. Obtenir Defender pour le point de terminaison. <p>3. Planifiez vos rôles et autorisations et accordez l’accès au portail Microsoft 365 Defender. <p>4. Configurez les paramètres proxy et Internet de votre appareil pour permettre la communication entre les appareils de votre organisation et Defender pour le point de terminaison. |
|[Configurer Defender pour le point de terminaison](switch-to-microsoft-defender-setup.md) |Pendant [la phase **d’installation**](switch-to-microsoft-defender-setup.md): <p>1. Activez/réinstallez l’Antivirus Microsoft Defender. <p>2. Configurez Defender pour endpoint. <p>3. Ajoutez Defender pour le point de terminaison à la liste d’exclusions de votre solution existante. <p>4. Ajoutez votre solution existante à la liste d’exclusions de l’Antivirus Microsoft Defender. <p>5. Configurer vos groupes d’appareils, collections et unités d’organisation. <p>6. Configurez vos stratégies de logiciel anti-programme malveillant et les paramètres de protection en temps réel.|
|[Intégration à Defender pour le point de terminaison](switch-to-microsoft-defender-onboard.md) |Pendant [la phase **d’intégration**](switch-to-microsoft-defender-onboard.md): <p>1. Intégrer vos appareils à Defender pour le point de terminaison. <p>2. Exécutez un test de détection. <p>3. Confirmez que l’Antivirus Microsoft Defender s’exécute en mode passif. <p>4. Obtenir les mises à jour de l’Antivirus Microsoft Defender. <p>5. Désinstallez votre solution de protection de point de terminaison existante. <p>6. Assurez-vous que Defender pour le point de terminaison fonctionne correctement. |

## <a name="whats-included-in-microsoft-defender-for-endpoint"></a>Qu’est-ce qui est inclus dans Microsoft Defender pour le point de terminaison ?

Dans ce guide de migration, nous [](overview-endpoint-detection-response.md) nous concentrons sur les fonctionnalités de [protection](microsoft-defender-antivirus-in-windows-10.md) et de détection de point de terminaison et de réponse nouvelle génération comme point de départ pour passer à Defender pour Endpoint. Toutefois, Defender pour point de terminaison inclut bien plus que la protection antivirus et de point de terminaison. Defender pour point de terminaison est une plateforme unifiée pour la protection préventive, la détection post-violation, l’examen automatisé et la réponse. Le tableau suivant récapitule les fonctionnalités de Defender for Endpoint. 

| Fonctionnalité/fonctionnalité | Description |
|---|---|
| [Gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md) | Les & de gestion des vulnérabilités permettent d’identifier, d’évaluer et de corriger les faiblesses sur vos points de terminaison (tels que les appareils). |
| [Réduction de la surface d’attaque](overview-attack-surface-reduction.md) | Les règles de réduction de la surface d’attaque contribuent à protéger les appareils et applications de votre organisation contre les cybermenaces et les attaques. |
| [Protection de nouvelle génération](microsoft-defender-antivirus-in-windows-10.md) | La nouvelle génération de protection inclut l’Antivirus Microsoft Defender pour bloquer les menaces et les programmes malveillants. |
| [Détection et réponse du point de terminaison](overview-endpoint-detection-response.md) | Les fonctionnalités de détection et de réponse des points de terminaison détectent, examinent et répondent aux tentatives d’intrusion et aux violations actives.  |
| [Repérage avancé](advanced-hunting-overview.md) | Les fonctionnalités de recherche avancées permettent à votre équipe des opérations de sécurité de localiser des indicateurs et des entités de menaces connues ou potentielles. |
| [Blocage et confinement comportementaux](behavioral-blocking-containment.md) | Les fonctionnalités de blocage du comportement et de contenu permettent d’identifier et d’arrêter les menaces, en fonction de leurs comportements et des arbre de traitement, même lorsque la menace a démarré l’exécution. |
| [Examen et correction automatisés](automated-investigations.md) | Les fonctionnalités d’examen et de réponse automatisées examinent les alertes et prennent des mesures correctives immédiates pour résoudre les violations. |
| [Service de recherche de menaces](microsoft-threat-experts.md) (experts microsoft en matière de menaces) | Les services de recherche de menace fournissent aux équipes des opérations de sécurité une surveillance et une analyse de niveau expert, et pour vous assurer que les menaces critiques ne sont pas manquées. |

**Vous souhaitez en savoir plus ? Voir [Defender pour le point de terminaison.](microsoft-defender-endpoint.md)**

## <a name="next-step"></a>Étape suivante

- Continuez à [préparer votre migration.](switch-to-microsoft-defender-prepare.md)
