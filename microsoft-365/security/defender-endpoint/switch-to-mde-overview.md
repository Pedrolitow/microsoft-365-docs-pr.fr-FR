---
title: Passez de la protection des points de terminaison non-Microsoft à Microsoft Defender pour point de terminaison
description: Passez à Microsoft Defender pour point de terminaison, qui inclut Microsoft Defender Antivirus pour votre solution endpoint protection.
keywords: migration, Windows Defender, protection avancée des points de terminaison, antivirus, logiciel anti-programme malveillant, mode passif, mode actif
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-migratetomdatp
- m365solution-overview
- m365initiative-defender-endpoint
- highpri
- tier1
ms.topic: overview
ms.custom: migrationguides
ms.date: 09/29/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: c81e458d57b4e8ccc67d409a1f11e66b201d8938
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68222933"
---
# <a name="make-the-switch-from-non-microsoft-endpoint-protection-to-microsoft-defender-for-endpoint"></a>Passez de la protection des points de terminaison non-Microsoft à Microsoft Defender pour point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Si vous envisagez de passer d’une solution de protection de point de terminaison non Microsoft à [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md) (Defender pour point de terminaison) ou si vous êtes en phase de planification, utilisez cet article comme guide. Cet article décrit le processus global de déplacement vers Defender pour point de terminaison.

:::image type="content" source="images/nonms-mde-migration.png" alt-text="Processus de migration pour basculer votre solution endpoint protection vers Defender pour point de terminaison" lightbox="images/nonms-mde-migration.png":::

Lorsque vous basculez vers Defender pour point de terminaison, vous commencez par votre protection antivirus/anti-programme malveillant non Microsoft en mode actif. Ensuite, vous allez configurer Microsoft Defender Antivirus en mode passif et intégrer vos appareils à Defender pour point de terminaison. Ensuite, vous configurez vos fonctionnalités endpoint protection, définissez Microsoft Defender Antivirus en mode actif et vérifiez que tout fonctionne correctement. Enfin, vous supprimez la solution non-Microsoft.

## <a name="the-migration-process"></a>Processus de migration

Le processus de migration vers Defender pour point de terminaison peut être divisé en trois phases, comme décrit dans le tableau suivant :

:::image type="content" source="images/phase-diagrams/migration-phases.png" alt-text="Processus de migration MDE" lightbox="images/phase-diagrams/migration-phases.png":::


<br/><br/>

|Phase|Description|
|--|--|
|[Préparer votre migration](switch-to-mde-phase-1.md)|Pendant [la phase **de préparation**](switch-to-mde-phase-1.md) : <br/>1. Mettez à jour les appareils de votre organisation.<br/>2. Obtenir Defender pour point de terminaison.<br/>3. Planifiez les rôles et les autorisations, et accordez l’accès au portail Microsoft 365 Defender.<br/>4. Configurez votre proxy d’appareil et les paramètres Internet pour permettre la communication entre les appareils de votre organisation et Defender pour point de terminaison. |
|[Configurer Defender pour point de terminaison](switch-to-mde-phase-2.md)|Pendant [la phase **d’installation**](switch-to-mde-phase-2.md) : <br/>1. Activez/réinstallez Microsoft Defender Antivirus et définissez-le en mode passif.<br/>2. Configurez Defender pour point de terminaison.<br/>3. Ajoutez Defender pour point de terminaison à la liste d’exclusions de votre solution existante.<br/>4. Ajoutez votre solution existante à la liste d’exclusions pour Microsoft Defender Antivirus.<br/>5. Configurez vos groupes d’appareils, regroupements et unités d’organisation.|
|[Intégrer à Defender pour point de terminaison](switch-to-mde-phase-3.md)|Pendant [la phase **d’intégration**](switch-to-mde-phase-3.md) : <br/>1. Intégrer vos appareils à Defender pour point de terminaison.<br/>2. Exécutez un test de détection.<br/>3. Vérifiez que Microsoft Defender Antivirus s’exécute en mode passif.<br/>4. Obtenir des mises à jour pour Microsoft Defender Antivirus.<br/>5. Désinstallez votre solution de protection de point de terminaison existante.<br/>6. Assurez-vous que Defender pour point de terminaison fonctionne correctement.|

## <a name="whats-included-in-microsoft-defender-for-endpoint"></a>Qu’est-ce qui est inclus dans Microsoft Defender pour point de terminaison ?

Dans ce guide de migration, nous nous concentrons sur les fonctionnalités de protection et de [détection de point de terminaison et de réponse](overview-endpoint-detection-response.md) de [nouvelle génération](microsoft-defender-antivirus-in-windows-10.md) comme point de départ pour passer à Defender pour point de terminaison. Toutefois, Defender pour point de terminaison inclut bien plus que l’antivirus et la protection des points de terminaison. Defender pour point de terminaison est une plateforme unifiée pour la protection préventive, la détection post-violation, l’investigation automatisée et la réponse. Le tableau suivant récapitule les fonctionnalités dans Defender pour point de terminaison.

<br/><br/>

|Fonctionnalité/fonctionnalité|Description|
|---|---|
|[Gestion des vulnérabilités Microsoft Defender](next-gen-threat-and-vuln-mgt.md)|Les fonctionnalités de gestion des vulnérabilités Defender permettent d’identifier, d’évaluer et de corriger les faiblesses de vos points de terminaison (tels que les appareils).|
|[Réduction de la surface d’attaque](overview-attack-surface-reduction.md)|Les règles de réduction de la surface d’attaque aident à protéger les appareils et applications de votre organisation contre les cybermenaces et les attaques.|
|[Protection de nouvelle génération](microsoft-defender-antivirus-in-windows-10.md)|La protection de nouvelle génération inclut Microsoft Defender Antivirus pour aider à bloquer les menaces et les programmes malveillants.|
|[Détection et réponse du point de terminaison](overview-endpoint-detection-response.md)|Les fonctionnalités de détection et de réponse des points de terminaison détectent, examinent et répondent aux tentatives d’intrusion et aux violations actives.|
|[Repérage avancé](advanced-hunting-overview.md)|Les fonctionnalités de repérage avancées permettent à votre équipe chargée des opérations de sécurité de localiser les indicateurs et entités de menaces connues ou potentielles.|
|[Blocage et confinement comportementaux](behavioral-blocking-containment.md)|Les fonctionnalités de blocage et d’endiguement comportementaux permettent d’identifier et d’arrêter les menaces, en fonction de leurs comportements et de leurs arborescences de traitement, même lorsque la menace a démarré l’exécution.|
|[Examen et correction automatisés](automated-investigations.md)|Les fonctionnalités d’investigation et de réponse automatisées examinent les alertes et prennent des mesures de correction immédiates pour résoudre les violations.|
|[Service de chasse aux menaces](microsoft-threat-experts.md) (Spécialistes des menaces Microsoft)|Les services de repérage des menaces fournissent aux équipes chargées des opérations de sécurité une surveillance et une analyse de niveau expert, et permettent de s’assurer que les menaces critiques ne sont pas manquées.|

**Vous voulez en savoir plus ? Consultez [Defender pour point de terminaison](microsoft-defender-endpoint.md).**

## <a name="next-step"></a>Étape suivante

- Procédez à la [préparation de votre migration](switch-to-mde-phase-1.md).
