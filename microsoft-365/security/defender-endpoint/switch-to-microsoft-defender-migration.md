---
title: Passer de la protection de point de terminaison non-Microsoft à Microsoft Defender pour le point de terminaison
description: Passez à Microsoft Defender pour le point de terminaison, qui inclut Antivirus Microsoft Defender pour votre solution de protection des points de terminaison.
keywords: migration, windows defender, protection avancée des points de terminaison, antivirus, logiciel anti-programme malveillant, mode passif, mode actif
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
ms.date: 08/16/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 267787b2cacc00a1d402c2f4dd2e57f42bd3dda3
ms.sourcegitcommit: 4740e69326eb7f8302eec7bab5bd516d498e4492
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2021
ms.locfileid: "59402165"
---
# <a name="make-the-switch-from-non-microsoft-endpoint-protection-to-microsoft-defender-for-endpoint"></a>Passer de la protection de point de terminaison non-Microsoft à Microsoft Defender pour le point de terminaison

Si vous envisagez de passer d’une solution de protection de point de terminaison non-Microsoft à [Microsoft Defender pour point](microsoft-defender-endpoint.md) de terminaison (Defender pour point de terminaison), vous êtes au bon endroit. Utilisez cet article comme guide.

:::image type="content" source="images/nonms-mde-migration.png" alt-text="Basculez votre solution de protection de point de terminaison vers Defender pour le point de terminaison.":::

Lorsque vous basculez vers Defender pour le point de terminaison, vous commencez par votre protection antivirus/anti-programme malveillant non Microsoft en mode actif. Ensuite, vous configurez Antivirus Microsoft Defender en mode passif et intégrer vos appareils à Defender for Endpoint. Ensuite, vous configurez vos fonctionnalités de protection des points de terminaison, définissez Antivirus Microsoft Defender en mode actif et vérifiez que tout fonctionne correctement. Enfin, vous supprimez la solution non-Microsoft.

## <a name="the-migration-process"></a>Processus de migration

Le processus de migration vers Defender pour Endpoint peut être divisé en trois phases, comme décrit dans le tableau suivant :

![Processus de migration MDE.](images/phase-diagrams/migration-phases.png)

|Phase|Description|
|--|--|
|[Préparer votre migration](switch-to-microsoft-defender-prepare.md)|Pendant [la phase **de** préparation](switch-to-microsoft-defender-prepare.md): <ol><li>Mettez à jour les appareils de votre organisation.</li><li>Obtenir Defender pour le point de terminaison.</li><li>Planifiez les rôles et les autorisations, et accordez l’accès Microsoft 365 Defender portail.</li><li>Configurez les paramètres proxy et Internet de votre appareil pour activer la communication entre les appareils de votre organisation et Defender pour le point de terminaison.</li></ol>|
|[Configurer Defender pour le point de terminaison](switch-to-microsoft-defender-setup.md)|Pendant [la phase **d’installation**](switch-to-microsoft-defender-setup.md): <ol><li>Activez/réinstallez Antivirus Microsoft Defender et définissez-le en mode passif.</li><li> Configurez Defender pour endpoint.</li><li>Ajoutez Defender pour le point de terminaison à la liste d’exclusions de votre solution existante.</li><li>Ajoutez votre solution existante à la liste d’exclusions Antivirus Microsoft Defender.</li><li>Configurer vos groupes d’appareils, collections et unités d’organisation.</li><li>Configurez vos stratégies de logiciel anti-programme malveillant et vos paramètres de protection en temps réel.</li></ol>|
|[Intégration à Defender pour le point de terminaison](switch-to-microsoft-defender-onboard.md)|Pendant [la phase **d’intégration**](switch-to-microsoft-defender-onboard.md): <ol><li>Intégrer vos appareils à Defender for Endpoint.</li><li>Exécutez un test de détection.</li><li>Confirmez que Antivirus Microsoft Defender est en cours d’exécution en mode passif.</li><li>Obtenir les mises à jour de Antivirus Microsoft Defender.</li><li>Désinstallez votre solution de protection de point de terminaison existante.</li><li>Assurez-vous que Defender pour le point de terminaison fonctionne correctement.</li></ol>|

## <a name="whats-included-in-microsoft-defender-for-endpoint"></a>Qu’est-ce qui est inclus dans Microsoft Defender pour le point de terminaison ?

Dans ce guide de migration, nous [](overview-endpoint-detection-response.md) nous concentrons sur les fonctionnalités de [protection](microsoft-defender-antivirus-in-windows-10.md) et de protection évolutive des points de terminaison nouvelle génération comme point de départ pour passer à Defender pour endpoint. Toutefois, Defender pour point de terminaison inclut bien plus que la protection antivirus et de point de terminaison. Defender pour point de terminaison est une plateforme unifiée pour la protection préventive, la détection post-violation, l’examen automatisé et la réponse. Le tableau suivant récapitule les fonctionnalités de Defender for Endpoint.

<br/><br/>

|Fonctionnalité/fonctionnalité|Description|
|---|---|
|[Gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)|Les fonctionnalités & gestion des vulnérabilités menace permettent d’identifier, d’évaluer et de corriger les faiblesses sur vos points de terminaison (tels que les appareils).|
|[Réduction de la surface d’attaque](overview-attack-surface-reduction.md)|Les règles de réduction de la surface d’attaque contribuent à protéger les appareils et applications de votre organisation contre les cybermenaces et les attaques.|
|[Protection de nouvelle génération](microsoft-defender-antivirus-in-windows-10.md)|La protection nouvelle génération inclut des Antivirus Microsoft Defender pour bloquer les menaces et les programmes malveillants.|
|[Détection et réponse du point de terminaison](overview-endpoint-detection-response.md)|Les fonctionnalités de détection et de réponse des points de terminaison détectent, examinent et répondent aux tentatives d’intrusion et aux violations actives.|
|[Repérage avancé](advanced-hunting-overview.md)|Les fonctionnalités de recherche avancées permettent à votre équipe des opérations de sécurité de localiser des indicateurs et des entités de menaces connues ou potentielles.|
|[Blocage et confinement comportementaux](behavioral-blocking-containment.md)|Les fonctionnalités de blocage du comportement et de contenu permettent d’identifier et d’arrêter les menaces, en fonction de leurs comportements et des arbre de traitement, même lorsque la menace a démarré l’exécution.|
|[Examen et correction automatisés](automated-investigations.md)|Les fonctionnalités d’examen et de réponse automatisées examinent les alertes et prennent des mesures correctives immédiates pour résoudre les violations.|
|[Service de recherche de menaces](microsoft-threat-experts.md) (Spécialistes des menaces Microsoft)|Les services de recherche de menace fournissent aux équipes des opérations de sécurité une surveillance et une analyse de niveau expert, et pour vous assurer que les menaces critiques ne sont pas manquées.|

**Vous souhaitez en savoir plus ? Voir [Defender pour le point de terminaison.](microsoft-defender-endpoint.md)**

## <a name="next-step"></a>Étape suivante

- Continuez à [préparer votre migration.](switch-to-microsoft-defender-prepare.md)
