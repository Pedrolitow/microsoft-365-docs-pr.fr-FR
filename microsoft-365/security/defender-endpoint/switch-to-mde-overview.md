---
title: Passer de la protection de point de terminaison non-Microsoft à Microsoft Defender pour le point de terminaison
description: Passez à Microsoft Defender pour le point de terminaison, qui inclut Antivirus Microsoft Defender pour votre solution de protection des points de terminaison.
keywords: migration, windows defender, protection avancée des points de terminaison, antivirus, logiciel anti-programme malveillant, mode passif, mode actif
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-overview
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
- m365initiative-defender-endpoint
ms.topic: overview
ms.custom: migrationguides
ms.date: 11/29/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: eb0971c6f5b8fd8bf37f3d33cb65cff8d331e0d0
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "62245302"
---
# <a name="make-the-switch-from-non-microsoft-endpoint-protection-to-microsoft-defender-for-endpoint"></a>Passer de la protection de point de terminaison non-Microsoft à Microsoft Defender pour le point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804) Si vous envisagez de passer d’une solution de protection de point de terminaison non-Microsoft à [Microsoft Defender pour](microsoft-defender-endpoint.md) point de terminaison (Defender pour point de terminaison) ou si vous êtes en phase de planification, utilisez cet article comme guide. Cet article décrit le processus global de passage à Defender pour Point de terminaison.

:::image type="content" source="images/nonms-mde-migration.png" alt-text="Basculez votre solution de protection de point de terminaison vers Defender pour le point de terminaison.":::

Lorsque vous basculez vers Defender pour le point de terminaison, vous commencez par votre protection antivirus/anti-programme malveillant non-Microsoft en mode actif. Ensuite, vous configurez Antivirus Microsoft Defender en mode passif et intégrer vos appareils à Defender for Endpoint. Ensuite, vous configurez vos fonctionnalités de protection des points de terminaison, définissez Antivirus Microsoft Defender le mode actif et vérifiez que tout fonctionne correctement. Enfin, vous supprimez la solution non-Microsoft.

## <a name="the-migration-process"></a>Processus de migration

Le processus de migration vers Defender pour Point de terminaison peut être divisé en trois phases, comme décrit dans le tableau suivant :

![Processus de migration MDE.](images/phase-diagrams/migration-phases.png)

<br/><br/>

|Phase|Description|
|--|--|
|[Préparer votre migration](switch-to-mde-phase-1.md)|Pendant [la phase **de** préparation](switch-to-mde-phase-1.md): <br/>1. Mettez à jour les appareils de votre organisation.<br/>2. Obtenir Defender pour le point de terminaison.<br/>3. Planifiez les rôles et les autorisations et accordez l’accès Microsoft 365 Defender portail.<br/>4. Configurez les paramètres proxy et Internet de votre appareil pour permettre la communication entre les appareils de votre organisation et Defender pour le point de terminaison. |
|[Configurer Defender pour le point de terminaison](switch-to-mde-phase-2.md)|Pendant [la phase **d’installation**](switch-to-mde-phase-2.md): <br/>1. Activez/réinstallez Antivirus Microsoft Defender et définissez-le en mode passif.<br/>2. Configurez Defender pour endpoint.<br/>3. Ajoutez Defender pour le point de terminaison à la liste d’exclusions de votre solution existante.<br/>4. Ajoutez votre solution existante à la liste d’exclusions pour Antivirus Microsoft Defender.<br/>5. Configurer vos groupes d’appareils, collections et unités d’organisation.<br/>6. Configurez vos stratégies de logiciel anti-programme malveillant et les paramètres de protection en temps réel.|
|[Intégration à Defender pour le point de terminaison](switch-to-mde-phase-3.md)|Pendant [la phase **d’intégration**](switch-to-mde-phase-3.md): <br/>1. Intégrer vos appareils à Defender pour le point de terminaison.<br/>2. Exécutez un test de détection.<br/>3. Confirmez que la Antivirus Microsoft Defender est en cours d’exécution en mode passif.<br/>4. Obtenir les mises à jour de Antivirus Microsoft Defender.<br/>5. Désinstallez votre solution de protection de point de terminaison existante.<br/>6. Assurez-vous que Defender pour le point de terminaison fonctionne correctement.|

## <a name="whats-included-in-microsoft-defender-for-endpoint"></a>Qu’est-ce qui est inclus dans Microsoft Defender pour le point de terminaison ?

Dans ce guide de migration, nous [](overview-endpoint-detection-response.md) nous concentrons sur les fonctionnalités de [protection](microsoft-defender-antivirus-in-windows-10.md) et de protection évolutive des points de terminaison nouvelle génération comme point de départ pour passer à Defender pour Endpoint. Toutefois, Defender pour point de terminaison inclut bien plus que la protection antivirus et de point de terminaison. Defender for Endpoint est une plateforme unifiée pour la protection préventive, la détection post-violation, l’examen automatisé et la réponse. Le tableau suivant récapitule les fonctionnalités de Defender for Endpoint.

<br/><br/>

|Fonctionnalité/fonctionnalité|Description|
|---|---|
|[Gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)|Les fonctionnalités & gestion des vulnérabilités menaces permettent d’identifier, d’évaluer et de corriger les faiblesses sur vos points de terminaison (tels que les appareils).|
|[Réduction de la surface d’attaque](overview-attack-surface-reduction.md)|Les règles de réduction de la surface d’attaque contribuent à protéger les appareils et applications de votre organisation contre les cybermenaces et les attaques.|
|[Protection de nouvelle génération](microsoft-defender-antivirus-in-windows-10.md)|La protection nouvelle génération inclut des Antivirus Microsoft Defender pour bloquer les menaces et les programmes malveillants.|
|[Détection et réponse du point de terminaison](overview-endpoint-detection-response.md)|Les fonctionnalités de détection et de réponse des points de terminaison détectent, examinent et répondent aux tentatives d’intrusion et aux violations actives.|
|[Repérage avancé](advanced-hunting-overview.md)|Les fonctionnalités de recherche avancées permettent à votre équipe des opérations de sécurité de localiser des indicateurs et des entités de menaces connues ou potentielles.|
|[Blocage et confinement comportementaux](behavioral-blocking-containment.md)|Les fonctionnalités de blocage du comportement et de blocage du contenu permettent d’identifier et d’arrêter les menaces, en fonction de leurs comportements et des arbre de traitement, même lorsque la menace a démarré l’exécution.|
|[Examen et correction automatisés](automated-investigations.md)|Les fonctionnalités d’examen et de réponse automatisées examinent les alertes et prennent des mesures correctives immédiates pour résoudre les violations.|
|[Service de recherche de menaces](microsoft-threat-experts.md) (Spécialistes des menaces Microsoft)|Les services de recherche de menace fournissent aux équipes des opérations de sécurité une analyse et une surveillance de niveau expert, et pour vous assurer que les menaces critiques ne sont pas manquées.|

**Vous souhaitez en savoir plus ? Voir [Defender pour le point de terminaison.](microsoft-defender-endpoint.md)**

## <a name="next-step"></a>Étape suivante

- Procédez à [la préparation de votre migration.](switch-to-mde-phase-1.md)
