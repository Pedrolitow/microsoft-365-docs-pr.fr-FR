---
title: Passer d’une solution de point de terminaison non-Microsoft à Microsoft Defender pour le point de terminaison
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
ms.topic: conceptual
ms.custom: migrationguides
ms.date: 02/11/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 6e5b79e447579631e4aa2eaf02352dc3fa6a8daa
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51066089"
---
# <a name="make-the-switch-from-a-non-microsoft-endpoint-solution-to-microsoft-defender-for-endpoint"></a>Passer d’une solution de point de terminaison non-Microsoft à Microsoft Defender pour le point de terminaison

Si vous envisagez de passer d’une solution de protection de point de terminaison non-Microsoft à [Microsoft Defender pour point](https://docs.microsoft.com/windows/security/threat-protection) de terminaison (Defender pour point de terminaison), vous êtes au bon endroit. Utilisez cet article comme guide.

:::image type="content" source="images/nonms-mde-migration.png" alt-text="Vue d’ensemble de la migration vers Defender pour le point de terminaison":::

Lorsque vous passez à Defender pour point de terminaison, vous commencez par votre solution non-Microsoft en mode actif, configurez Defender pour Endpoint en mode passif, intégré à Defender pour point de terminaison, puis définissez Defender pour Point de terminaison sur le mode actif et supprimez la solution autre que Microsoft.

> [!TIP]
> - Si vous utilisez actuellement Mc Antivirus Endpoint Security (Mc Antivirus), voir [Migrer de Mc Antivirus vers Microsoft Defender pour Endpoint](mcafee-to-microsoft-defender-migration.md).
> - Si vous utilisez actuellement Symantec Endpoint Protection (Symantec), voir [Migrer de Symantec vers Microsoft Defender pour Endpoint](symantec-to-microsoft-defender-atp-migration.md).

## <a name="the-migration-process"></a>Processus de migration

Lorsque vous basculez vers Microsoft Defender pour le point de terminaison, vous suivez un processus qui peut être divisé en trois phases, comme décrit dans le tableau suivant :

![Phases de migration : préparer, configurer, intégrer](images/phase-diagrams/migration-phases.png)

|Phase |Description |
|--|--|
|[Préparer votre migration](switch-to-microsoft-defender-prepare.md) |Pendant [la phase **de**](switch-to-microsoft-defender-prepare.md)préparation, vous mettez à jour les appareils de votre organisation, obtenez Microsoft Defender pour le point de terminaison, planifiez vos rôles et autorisations et accordez l’accès au Centre de sécurité Microsoft Defender. Vous configurez également les paramètres proxy et Internet de votre appareil pour permettre la communication entre les appareils de votre organisation et Microsoft Defender pour le point de terminaison. |
|[Configurer Microsoft Defender pour le point de terminaison](switch-to-microsoft-defender-setup.md) |Pendant la [phase  ](switch-to-microsoft-defender-setup.md)d’installation, vous activez l’Antivirus Microsoft Defender et assurez-vous qu’il est en mode passif, et vous configurez les paramètres & exclusions pour l’Antivirus Microsoft Defender, Microsoft Defender pour le point de terminaison et votre solution de protection de point de terminaison existante. Vous créez également des groupes d’appareils, des collections et des unités d’organisation. Enfin, vous configurez vos stratégies anti-programme malveillant et vos paramètres de protection en temps réel.|
|[Intégration à Microsoft Defender pour le point de terminaison](switch-to-microsoft-defender-onboard.md) |Pendant [la phase **d’intégration,**](switch-to-microsoft-defender-onboard.md)vous intégrerez vos appareils à Microsoft Defender pour le point de terminaison et vérifiez que ces appareils communiquent avec Microsoft Defender pour endpoint. Enfin, vous désinstallez votre solution de protection de point de terminaison existante et assurez-vous que la protection via l’Antivirus Microsoft Defender & Microsoft Defender pour le point de terminaison est en mode actif. |

## <a name="whats-included-in-microsoft-defender-for-endpoint"></a>Qu’est-ce qui est inclus dans Microsoft Defender pour le point de terminaison ?

Dans ce guide de migration, nous [](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) nous concentrons sur les fonctionnalités de détection et de réponse des points de terminaison et de [protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) nouvelle génération comme point de départ pour passer à Microsoft Defender pour endpoint. Toutefois, Microsoft Defender pour point de terminaison inclut bien plus que la protection antivirus et de point de terminaison. Microsoft Defender pour point de terminaison est une plateforme de sécurité unifiée pour la protection préventive, la détection après effraction, l’examen automatisé et la réponse. Le tableau suivant récapitule les fonctionnalités de Microsoft Defender pour point de terminaison. 

| Fonctionnalité/fonctionnalité | Description |
|---|---|
| [Gestion des & menaces](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) | Les & de gestion des vulnérabilités permettent d’identifier, d’évaluer et de corriger les faiblesses sur vos points de terminaison (tels que les appareils). |
| [Réduction de la surface d’attaque](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-attack-surface-reduction) | Les règles de réduction de la surface d’attaque contribuent à protéger les appareils et applications de votre organisation contre les cybermenaces et les attaques. |
| [Protection nouvelle génération](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) | La nouvelle génération de protection inclut l’Antivirus Microsoft Defender pour bloquer les menaces et les programmes malveillants. |
| [Détection et réponse des points de terminaison](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) | Les fonctionnalités de détection et de réponse des points de terminaison détectent, examinent et répondent aux tentatives d’intrusion et aux violations actives.  |
| [Repérage avancé](advanced-hunting-overview.md) | Les fonctionnalités de recherche avancées permettent à votre équipe des opérations de sécurité de localiser des indicateurs et des entités de menaces connues ou potentielles. |
| [Blocage et contenu comportementaux](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/behavioral-blocking-containment) | Les fonctionnalités de blocage du comportement et de blocage du contenu permettent d’identifier et d’arrêter les menaces, en fonction de leurs comportements et des arbre de traitement, même lorsque la menace a démarré l’exécution. |
| [Examen et correction automatisés](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/automated-investigations) | Les fonctionnalités d’examen et de réponse automatisées examinent les alertes et prennent des mesures correctives immédiates pour résoudre les violations. |
| [Service de recherche de menaces](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/microsoft-threat-experts) (experts microsoft en matière de menaces) | Les services de recherche de menace fournissent aux équipes des opérations de sécurité une analyse et une surveillance de niveau expert, et pour vous assurer que les menaces critiques ne sont pas manquées. |

**Vous souhaitez en savoir plus ? Voir [Microsoft Defender pour le point de terminaison.](https://docs.microsoft.com/windows/security/threat-protection)**

## <a name="next-step"></a>Étape suivante

- Procédez à [la préparation de votre migration.](switch-to-microsoft-defender-prepare.md)
