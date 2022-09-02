---
title: Gérer le processus de déploiement progressif pour les mises à jour de Microsoft Defender
description: En savoir plus sur le processus de mise à jour progressive et les contrôles
keywords: mise à jour, processus de mise à jour, contrôles, mise en production
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.subservice: m365d
ms.openlocfilehash: f1be806e9a1a7c300f6a33244a69aae1dea77959
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67521540"
---
# <a name="manage-the-gradual-rollout-process-for-microsoft-defender-updates"></a>Gérer le processus de déploiement progressif pour les mises à jour de Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Il est important de s’assurer que les composants clients sont à jour pour fournir des fonctionnalités de protection critiques et empêcher les attaques.

Les fonctionnalités sont fournies par le biais de plusieurs composants :

- [Endpoint Detection & Response](overview-endpoint-detection-response.md)
- [Protection de nouvelle génération](microsoft-defender-antivirus-windows.md) avec [protection fournie par le cloud](cloud-protection-microsoft-defender-antivirus.md)
- [Réduction de la surface d’attaque](overview-attack-surface-reduction.md)

Mises à jour sont publiées mensuellement à l’aide d’un processus de mise en production progressive. Ce processus permet d’activer la détection précoce des défaillances pour intercepter l’impact au fur et à mesure qu’il se produit et y remédier rapidement avant un déploiement plus important.

> [!NOTE]
> Pour plus d’informations sur la façon de contrôler les mises à jour quotidiennes du renseignement de sécurité, consultez [Planifier les mises à jour de protection antivirus Microsoft Defender](manage-protection-update-schedule-microsoft-defender-antivirus.md). Mises à jour veiller à ce que la protection de nouvelle génération puisse se défendre contre les nouvelles menaces, même si la protection fournie par le cloud n’est pas disponible pour le point de terminaison.

## <a name="microsoft-gradual-rollout-model"></a>Modèle de déploiement progressif Microsoft

Le modèle de déploiement progressif suivant est suivi pour les mises à jour defender mensuelles :

1. La première version est disponible pour les abonnés au canal bêta.
2. Après la validation, les commentaires et les correctifs, nous commençons le processus de déploiement progressif de manière limitée et vers les abonnés de canal en préversion en premier.
3. Nous allons ensuite publier la mise à jour pour le reste de la population mondiale, en passant de 10 à 100 %.

Nos ingénieurs surveillent en permanence l’impact et réaffectent tous les problèmes pour créer un correctif en fonction des besoins.

## <a name="how-to-customize-your-internal-deployment-process"></a>Comment personnaliser votre processus de déploiement interne

Si vos machines reçoivent des mises à jour Defender de Windows Update, le processus de déploiement progressif peut entraîner la réception de mises à jour Defender par certaines de vos machines plus tôt que d’autres. La section suivante explique comment définir une stratégie qui permettra aux mises à jour automatiques de circuler différemment vers des groupes d’appareils spécifiques en tirant parti de la configuration du canal de mise à jour.

> [!NOTE]
> Lors de la planification de votre propre version progressive, veillez à toujours avoir une sélection d’appareils abonnés à la préversion et aux canaux intermédiaires. Cela permet à votre organisation ainsi qu’à Microsoft d’empêcher ou de rechercher et de résoudre des problèmes spécifiques à votre environnement.

Pour les machines recevant des mises à jour via, par exemple, Windows Server Update Services (WSUS) ou Microsoft Endpoint Configuration Manager (MECM), d’autres options sont disponibles pour toutes les mises à jour Windows, y compris les options pour Microsoft Defender pour point de terminaison.

- En savoir plus sur l’utilisation d’une solution comme WSUS, MECM pour gérer la distribution et l’application des mises à jour dans [Gérer les mises à jour de l’Antivirus Microsoft Defender et appliquer des bases de référence - Sécurité Windows](manage-updates-baselines-microsoft-defender-antivirus.md#product-updates).

## <a name="update-channels-for-monthly-updates"></a>Mettre à jour les canaux pour les mises à jour mensuelles

Vous pouvez affecter un ordinateur à un canal de mise à jour pour définir la cadence dans laquelle un ordinateur reçoit les mises à jour mensuelles du moteur et de la plateforme.

Pour plus d’informations sur la configuration des mises à jour, consultez [Créer un processus de déploiement progressif personnalisé pour les mises à jour de Microsoft Defender](configure-updates.md).

Les canaux de mise à jour suivants sont disponibles :

<br>

****

|Nom du canal|Description|Application|
|---|---|---|
|Canal bêta - Préversion|Tester les mises à jour avant d’autres|Les appareils définis sur ce canal seront les premiers à recevoir de nouvelles mises à jour mensuelles. Sélectionnez Canal bêta pour participer à l’identification et à la création de rapports sur les problèmes à Microsoft. Les appareils du programme Windows Insider sont abonnés à ce canal par défaut. À utiliser uniquement dans les environnements de test.|
|Canal actuel (préversion)|Obtenir les mises à jour du canal actuel **plus tôt** lors de la mise en production progressive|Les appareils définis sur ce canal recevront les mises à jour les plus tôt pendant le cycle de mise en production progressive. Suggéré pour les environnements de préproduction/validation.|
|Canal actuel (intermédiaire)|Obtenir les mises à jour du canal actuel ultérieurement lors de la mise en production progressive|Des mises à jour seront proposées aux appareils ultérieurement au cours du cycle de mise en production progressive. Suggéré de s’appliquer à une petite partie représentative de la population de votre appareil (environ 10 %).|
|Canal actuel (large)|Obtenir les mises à jour à la fin de la mise en production progressive|Les mises à jour ne seront proposées aux appareils qu’une fois le cycle de mise en production progressif terminé. Suggéré de s’appliquer à un large éventail d’appareils dans votre population de production (~10-100%).|
|Critique : Délai d’attente|Retarder les mises à jour de Defender|Les mises à jour des appareils seront proposées avec un délai de 48 heures. Idéal pour les machines de centre de données qui reçoivent uniquement des mises à jour limitées. Suggéré pour les environnements critiques uniquement.|
|(par défaut)||Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste dans le canal actuel (par défaut) : restez à jour automatiquement pendant le cycle de mise en production progressive. Convient à la plupart des appareils.|
|

### <a name="update-channels-for-daily-updates"></a>Mettre à jour les canaux pour les mises à jour quotidiennes

Vous pouvez également affecter un ordinateur à un canal pour définir la cadence dans laquelle il reçoit les mises à jour quotidiennes. Notez que contrairement au processus mensuel, il n’existe aucun canal bêta et que ce cycle de mise en production progressive se produit plusieurs fois par jour.

<br>

****

|Nom du canal|Description|Application|
|---|---|---|
|Canal actuel (intermédiaire)|Obtenir les mises à jour du canal actuel ultérieurement lors de la mise en production progressive|Des mises à jour seront proposées aux appareils ultérieurement au cours du cycle de mise en production progressive. Suggéré de s’appliquer à une petite partie représentative de la population de votre appareil (environ 10 %).|
|Canal actuel (large)|Obtenir les mises à jour à la fin de la mise en production progressive|Des mises à jour seront proposées aux appareils après le cycle de mise en production progressive. Idéal pour les machines de centre de données qui reçoivent uniquement des mises à jour limitées. Remarque : ce paramètre s’applique à toutes les mises à jour Defender.|
|(par défaut)||Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste dans le canal actuel (par défaut) : restez à jour automatiquement pendant le cycle de mise en production progressive. Convient à la plupart des appareils|
|

> [!NOTE]
> Si vous souhaitez forcer une mise à jour vers la signature la plus récente au lieu de tirer parti du délai, vous devez d’abord supprimer cette stratégie.

## <a name="update-guidance"></a>Guide de mise à jour

Dans la plupart des cas, la configuration recommandée lors de l’utilisation de Windows Update consiste à autoriser les points de terminaison à recevoir et à appliquer des mises à jour Defender mensuelles à leur arrivée. Cela offre le meilleur équilibre entre la protection et l’impact possible associé aux modifications qu’ils peuvent introduire.

Pour les environnements où un déploiement progressif plus contrôlé des mises à jour defender automatiques est nécessaire, envisagez une approche avec les groupes de déploiement :

1. Participez au programme Windows Insider ou attribuez un groupe d’appareils au canal bêta.
2. Désignez un groupe pilote qui choisit le canal en préversion, généralement les environnements de validation, pour recevoir de nouvelles mises à jour plus tôt.
3. Désignez un groupe de machines qui recevront des mises à jour ultérieurement pendant le déploiement progressif à partir du canal intermédiaire. En règle générale, il s’agit d’un représentant d’environ 10 % de la population.
4. Désignez un groupe de machines qui reçoivent des mises à jour une fois le cycle de mise en production progressif terminé. Il s’agit généralement de systèmes de production importants.

Pour le reste des appareils, le paramètre par défaut est de recevoir de nouvelles mises à jour à mesure qu’elles arrivent pendant le processus de déploiement progressif de Microsoft et aucune autre configuration n’est requise.

Adoption de ce modèle :

- Vous permet de tester les versions anticipées avant qu’elles n’atteignent un environnement de production
- Assurez-vous que l’environnement de production reçoit toujours des mises à jour régulières et assurez-vous de la protection contre les menaces critiques.

## <a name="management-tools"></a>Outils de gestion

Pour créer votre propre processus de déploiement progressif personnalisé pour les mises à jour mensuelles, vous pouvez utiliser les outils suivants :

- Stratégie de groupe
- Microsoft Endpoint Manager
- PowerShell

Pour plus d’informations sur l’utilisation de ces outils, consultez [Créer un processus de déploiement progressif personnalisé pour les mises à jour de Microsoft Defender](configure-updates.md).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)