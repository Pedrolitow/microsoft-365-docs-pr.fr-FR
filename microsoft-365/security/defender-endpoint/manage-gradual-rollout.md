---
title: Gérer le processus de déploiement progressif pour les mises à jour De Microsoft Defender
description: En savoir plus sur le processus de mise à jour progressive et les contrôles
keywords: mise à jour, processus de mise à jour, contrôles, publication
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 0a264f16c35a9fe122c2cb62a56c16334fb162d2
ms.sourcegitcommit: d1eb1c26609146ff5a59b2a1b005dd7ac43ae64e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2021
ms.locfileid: "60099704"
---
# <a name="manage-the-gradual-rollout-process-for-microsoft-defender-updates"></a>Gérer le processus de déploiement progressif pour les mises à jour De Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Il est important de s’assurer que les composants clients sont à jour pour offrir des fonctionnalités de protection critiques et empêcher les attaques.

Les fonctionnalités sont fournies par le biais de plusieurs composants :

- [Endpoint Detection & Response](overview-endpoint-detection-response.md)
- [Protection nouvelle génération avec une](microsoft-defender-antivirus-windows.md) protection [cloud](cloud-protection-microsoft-defender-antivirus.md)
- [Réduction de la surface d’attaque](overview-attack-surface-reduction.md)

Les mises à jour sont publiées tous les mois à l’aide d’un processus de publication progressive. Ce processus permet d’activer la détection des échecs précoces pour détecter l’impact à mesure qu’elle se produit et la traiter rapidement avant un déploiement plus important.

> [!NOTE]
> Pour plus d’informations sur le contrôle des mises à jour quotidiennes de l’intelligence de la sécurité, voir [Planifier Antivirus Microsoft Defender mises à jour de la protection.](manage-protection-update-schedule-microsoft-defender-antivirus.md) Les mises à jour garantissent que la protection nouvelle génération peut se défendre contre les nouvelles menaces, même si la protection assurée par le cloud n’est pas disponible pour le point de terminaison.

## <a name="microsoft-gradual-rollout-model"></a>Modèle de déploiement progressif Microsoft

Le modèle de déploiement progressif suivant est suivi pour les mises à jour mensuelles de Defender :

1. La première version est publiée pour les abonnés au canal bêta.
2. Après la validation, les commentaires et les correctifs, nous commençons le processus de déploiement progressif d’une manière limitée et en premier lieu pour les abonnés au canal d’aperçu.
3. Nous allons ensuite publier la mise à jour pour le reste de la population globale, en la délant de 10 à 100 %.

Nos ingénieurs surveillent en permanence l’impact et réamorcer les problèmes afin de créer un correctif si nécessaire.

## <a name="how-to-customize-your-internal-deployment-process"></a>Comment personnaliser votre processus de déploiement interne

Si vos ordinateurs reçoivent des mises à jour Defender de Windows Update, le processus de déploiement progressif peut entraîner la réception de mises à jour De Defender par certains de vos ordinateurs plus tôt que d’autres. La section suivante explique comment définir une stratégie qui permettra aux mises à jour automatiques de circuler différemment vers des groupes spécifiques d’appareils en tirant parti de la configuration du canal de mise à jour.

> [!NOTE]
> Lors de la planification de votre propre version progressive, assurez-vous de toujours avoir une sélection d’appareils abonnés aux canaux de prévisualisation et de version progressive. Cela permettra à votre organisation ainsi qu’à Microsoft de prévenir ou de rechercher et de résoudre des problèmes spécifiques à votre environnement.

Pour les ordinateurs recevant des mises à jour via, par exemple, Windows Server Update Services (WSUS) ou Microsoft Endpoint Configuration Manager (MECM), d’autres options sont disponibles pour toutes les mises à jour Windows, y compris les options de Microsoft Defender pour endpoint.

- En savoir plus sur l’utilisation d’une solution telle que WSUS, MECM pour gérer la distribution et l’application des mises à jour dans Gérer les mises à jour Antivirus Microsoft Defender et appliquer les lignes de base [- Windows sécurité](manage-updates-baselines-microsoft-defender-antivirus.md#product-updates).

## <a name="update-channels-for-monthly-updates"></a>Mettre à jour les canaux pour les mises à jour mensuelles

Vous pouvez affecter un ordinateur à un canal de mise à jour pour définir la cadence à laquelle un ordinateur reçoit les mises à jour mensuelles du moteur et de la plateforme.

Pour plus d’informations sur la configuration des mises à jour, voir Créer un processus de déploiement progressif personnalisé pour les mises à jour [de Microsoft Defender.](configure-updates.md)

Les canaux de mise à jour suivants sont disponibles :

<br>

****

|Nom du canal|Description|Application|
|---|---|---|
|Canal bêta - Version d’avant-première|Tester les mises à jour avant d’autres|Les appareils qui sont connectés à ce canal seront les premiers à recevoir de nouvelles mises à jour mensuelles. Sélectionnez Le canal bêta pour participer à l’identification et au signalement des problèmes à Microsoft. Les appareils du Windows Programme Insider sont abonnés à ce canal par défaut. À utiliser uniquement dans les environnements de test.|
|Canal actuel (préversion)|Obtenir les mises à jour du canal actuel **plus tôt lors** de la publication progressive|Les appareils qui sont connectés à ce canal se voient proposer des mises à jour au plus tôt au cours du cycle de publication progressive. Suggéré pour les environnements de pré-production/validation.|
|Canal actuel (étapes)|Obtenir les mises à jour du canal actuel ultérieurement lors de la publication progressive|Des mises à jour seront proposées aux appareils plus tard au cours du cycle de publication progressive. Il est suggéré de s’appliquer à une petite partie représentative de la population de votre appareil (environ 10 %).|
|Canal actuel (large)|Obtenir des mises à jour à la fin de la publication progressive|Les mises à jour des appareils ne seront proposées qu’une fois le cycle de publication progressive terminé. Il est suggéré de s’appliquer à un large éventail d’appareils dans votre population de production (environ 10 à 100 %).|
|Critique : délai d’attente|Mises à jour de Delay Defender|Des mises à jour seront proposées aux appareils avec un délai de 48 heures. Il est préférable pour les ordinateurs de centre de données qui ne reçoivent que des mises à jour limitées. Suggéré uniquement pour les environnements critiques.|
|(valeur par défaut)||Si vous désactivez ou ne configurez pas cette stratégie, l’appareil restera dans le canal actuel (par défaut) : restez à jour automatiquement pendant le cycle de publication progressive. Convient à la plupart des appareils.|
|

### <a name="update-channels-for-daily-updates"></a>Mettre à jour les canaux pour les mises à jour quotidiennes

Vous pouvez également affecter un ordinateur à un canal pour définir la cadence à laquelle il reçoit les mises à jour quotidiennes. Notez que contrairement au processus mensuel, il n’existe aucun canal Bêta et ce cycle de publication progressive se produit plusieurs fois par jour.

<br>

****

|Nom du canal|Description|Application|
|---|---|---|
|Canal actuel (étapes)|Obtenir les mises à jour du canal actuel ultérieurement lors de la publication progressive|Des mises à jour seront proposées aux appareils plus tard au cours du cycle de publication progressive. Il est suggéré de s’appliquer à une petite partie représentative de la population de votre appareil (environ 10 %).|
|Canal actuel (large)|Obtenir des mises à jour à la fin de la publication progressive|Des mises à jour seront proposées aux appareils après le cycle de publication progressive. Il est préférable pour les ordinateurs de centre de données qui ne reçoivent que des mises à jour limitées. Remarque : ce paramètre s’applique à toutes les mises à jour de Defender.|
|(valeur par défaut)||Si vous désactivez ou ne configurez pas cette stratégie, l’appareil restera dans le canal actuel (par défaut) : restez à jour automatiquement pendant le cycle de publication progressive. Convient à la plupart des appareils|
|

> [!NOTE]
> Si vous souhaitez forcer une mise à jour de la signature la plus nouvelle au lieu de tirer parti du délai, vous devez d’abord supprimer cette stratégie.

## <a name="update-guidance"></a>Conseils de mise à jour

Dans la plupart des cas, la configuration recommandée lors de l’utilisation de Windows Update consiste à autoriser les points de terminaison à recevoir et à appliquer les mises à jour mensuelles de Defender à mesure qu’elles arrivent. Cela offre le meilleur équilibre entre la protection et l’impact possible associé aux modifications qu’ils peuvent introduire.

Pour les environnements où il est nécessaire d’un déploiement progressif plus contrôlé des mises à jour automatiques de Defender, envisagez une approche avec les groupes de déploiement :

1. Participer au programme Windows Insider ou affecter un groupe d’appareils au canal bêta.
2. Désignez un groupe pilote qui choisit le canal d’aperçu, généralement des environnements de validation, pour recevoir de nouvelles mises à jour en avant-première.
3. Désignez un groupe d’ordinateurs qui reçoivent les mises à jour ultérieurement lors du déploiement progressif à partir du canal de mise en place. En règle générale, il s’agit d’un pourcentage représentatif d’environ 10 % de la population.
4. Désignez un groupe d’ordinateurs qui reçoivent des mises à jour une fois le cycle de publication progressive terminé. Il s’agit généralement de systèmes de production importants.

Pour le reste des appareils, le paramètre par défaut consiste à recevoir de nouvelles mises à jour à mesure qu’elles arrivent pendant le processus de déploiement progressif de Microsoft et aucune configuration supplémentaire n’est requise.

Adoption de ce modèle :

- Vous permet de tester les premières sorties avant qu’elles n’atteignent un environnement de production
- Assurez-vous que l’environnement de production reçoit toujours des mises à jour régulières et assurez-vous de la protection contre les menaces critiques.

## <a name="management-tools"></a>Outils de gestion

Pour créer votre propre processus de déploiement progressif personnalisé pour les mises à jour mensuelles, vous pouvez utiliser les outils suivants :

- Stratégie de groupe
- Gestionnaire de point de terminaison Microsoft
- PowerShell

Pour plus d’informations sur l’utilisation de ces [outils,](configure-updates.md)voir Créer un processus de déploiement progressif personnalisé pour les mises à jour de Microsoft Defender.
