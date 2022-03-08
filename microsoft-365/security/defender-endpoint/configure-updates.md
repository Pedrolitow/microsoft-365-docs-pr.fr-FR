---
title: Créer un processus de déploiement progressif personnalisé pour les mises à jour De Microsoft Defender
description: Découvrez comment utiliser les outils pris en charge pour créer un processus de déploiement progressif personnalisé pour les mises à jour
keywords: outils de mise à jour, gpo, intune, gm, gestionnaire de point de terminaison Microsoft, stratégie, powershell
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
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4261e32721da86233a0a929a435c318904d6ac12
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324142"
---
# <a name="create-a-custom-gradual-rollout-process-for-microsoft-defender-updates"></a>Créer un processus de déploiement progressif personnalisé pour les mises à jour De Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> Cette fonctionnalité nécessite Antivirus Microsoft Defender version 4.18.2106.X ou plus récente.

Pour créer votre propre processus de déploiement progressif personnalisé pour les mises à jour De Defender, vous pouvez utiliser la stratégie de groupe, Microsoft Endpoint Manager et PowerShell.

Le tableau suivant répertorie les paramètres de stratégie de groupe disponibles pour la configuration des canaux de mise à jour :

<br>

****

|Titre du paramètre|Description|Emplacement|
|---|---|---|
|Sélectionner le canal de déploiement de mise à jour de plateforme mensuelle Microsoft Defender progressif|Activez cette stratégie pour spécifier quand les appareils reçoivent les mises à jour de la plateforme Microsoft Defender pendant le déploiement progressif mensuel. <p> Canal bêta : les appareils qui sont connectés à ce canal seront les premiers à recevoir de nouvelles mises à jour. Sélectionnez Le canal bêta pour participer à l’identification et au signalement des problèmes à Microsoft. Les appareils du Windows Programme Insider sont abonnés à ce canal par défaut. Pour une utilisation dans des environnements de test (manuels) uniquement et un nombre limité d’appareils. <p> Canal actuel (prévisualisation) : les appareils qui sont connectés à ce canal se voient proposer des mises à jour au plus tôt au cours du cycle de publication progressive mensuel. Suggéré pour les environnements de pré-production/validation. <p> Canal actuel (progressive) : des mises à jour seront proposées aux appareils après le cycle de publication progressive mensuel. Il est suggéré de s’appliquer à une petite partie représentative de votre population de production (environ 10 %). <p> Canal actuel (large) : les mises à jour ne seront proposées aux appareils qu’une fois le cycle de publication progressive terminé. Il est suggéré de s’appliquer à un large éventail d’appareils dans votre population de production (environ 10 à 100 %). <p> Retard critique : des mises à jour seront proposées aux appareils avec un délai de 48 heures. Suggéré uniquement pour les environnements critiques. <p>Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste à jour automatiquement pendant le cycle de publication progressive. Convient à la plupart des appareils.|Windows Components\Antivirus Microsoft Defender|
|Sélectionner le canal de déploiement de mise à jour mensuelle du moteur Microsoft Defender progressif|Activez cette stratégie pour spécifier quand les appareils reçoivent les mises à jour du moteur Microsoft Defender pendant le déploiement progressif mensuel. <p> Canal bêta : les appareils qui sont connectés à ce canal seront les premiers à recevoir de nouvelles mises à jour. Sélectionnez Le canal bêta pour participer à l’identification et au signalement des problèmes à Microsoft. Les appareils du Windows Programme Insider sont abonnés à ce canal par défaut. Pour une utilisation dans des environnements de test (manuels) uniquement et un nombre limité d’appareils. <p> Canal actuel (prévisualisation) : les appareils qui sont connectés à ce canal se voient proposer des mises à jour au plus tôt au cours du cycle de publication progressive mensuel. Suggéré pour les environnements de pré-production/validation. <p> Canal actuel (progressive) : des mises à jour seront proposées aux appareils après le cycle de publication progressive mensuel. Il est suggéré de s’appliquer à une petite partie représentative de votre population de production (environ 10 %). <p> Canal actuel (large) : les mises à jour ne seront proposées aux appareils qu’une fois le cycle de publication progressive terminé. Il est suggéré de s’appliquer à un large éventail d’appareils dans votre population de production (environ 10 à 100 %). <p> Retard critique : des mises à jour seront proposées aux appareils avec un délai de 48 heures. Suggéré uniquement pour les environnements critiques.<p> Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste à jour automatiquement pendant le cycle de publication progressive. Convient à la plupart des appareils.|Windows Components\Antivirus Microsoft Defender|
|Sélectionner le canal de déploiement progressif des mises à jour de sécurité quotidiennes de Microsoft Defender|Activez cette stratégie pour spécifier quand les appareils reçoivent les mises à jour de l’intelligence de sécurité De Microsoft Defender pendant le déploiement progressif quotidien. <p> Canal actuel (étapes) : des mises à jour seront proposées aux appareils après le cycle de publication. Il est suggéré de s’appliquer à une petite partie représentative de la population de production (environ 10 %). <p> Canal actuel (large) : les mises à jour ne seront proposées aux appareils qu’une fois le cycle de publication progressive terminé. Il est suggéré de s’appliquer à un large éventail d’appareils dans votre population de production (environ 10 à 100 %). <p>  Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste automatiquement à jour pendant le cycle de publication quotidien. Convient à la plupart des appareils.|Windows Components\Antivirus Microsoft Defender|
|Désactiver le déploiement progressif des mises à jour De Microsoft Defender|Activez cette stratégie pour désactiver le déploiement progressif des mises à jour De Defender. <p> Canal actuel (large) : les appareils qui sont connectés à ce canal se voient proposer des mises à jour en dernier au cours du cycle de publication progressive. Il est préférable pour les ordinateurs de centre de données qui ne reçoivent que des mises à jour limitées. <p> Remarque : ce paramètre s’applique aux mises à jour mensuelles et quotidiennes de Defender et remplace toutes les sélections de canaux précédemment configurées pour les mises à jour de plateforme et de moteur. <p> Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste dans le canal actuel (par défaut), sauf indication contraire dans des canaux spécifiques pour les mises à jour de plateforme et de moteur. Restez à jour automatiquement pendant le cycle de publication progressive. Convient à la plupart des appareils.|Windows Components\Antivirus Microsoft Defender|
|

## <a name="group-policy"></a>Stratégie de groupe

> [!NOTE]
> Un modèle ADMX Defender mis à jour sera publié avec la version 21H2 de Windows 10. Une version non localisée est disponible en téléchargement sur https://github.com/microsoft/defender-updatecontrols.

Vous pouvez utiliser la [stratégie de](/windows/win32/srvnodes/group-policy?redirectedfrom=MSDN) groupe pour configurer et gérer les Antivirus Microsoft Defender sur vos points de terminaison.

En règle générale, vous pouvez utiliser la procédure suivante pour configurer ou modifier Antivirus Microsoft Defender de stratégie de groupe :

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la **Console** de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de **groupe à configurer** , puis cliquez sur **Modifier**.

2. À l’aide de l’Éditeur de gestion des stratégies de groupe, allez **à configuration ordinateur**.

3. Cliquez **sur Modèles d’administration**.

4. Développez l’arborescence **Windows composants > Antivirus Microsoft Defender**.

5. Développez la section (appelée Emplacement dans  le tableau de cette rubrique) qui contient le paramètre que vous souhaitez configurer, double-cliquez sur le paramètre pour l’ouvrir et a apporté des modifications de configuration.

6. [Déployez l’GPO mis à jour comme vous le faites normalement](https://msdn.microsoft.com/library/ee663280(v=vs.85).aspx).

## <a name="intune"></a>Intune

Suivez les instructions du lien ci-dessous pour créer une stratégie personnalisée dans Intune :

[Ajouter des paramètres personnalisés pour Windows 10 appareils dans Microsoft Intune - Documents Microsoft Azure \|](/mem/intune/configuration/custom-settings-windows-10)

Pour plus d’informations sur le programme CSP Defender utilisé pour le processus de déploiement progressif, voir [CSP Defender](/windows/client-management/mdm/defender-csp).

## <a name="powershell"></a>PowerShell

Utilisez l’cmdlet `Set-MpPreference` pour configurer le déploiement des mises à jour progressives.

Utilisez les paramètres suivants :

```powershell
Set-MpPreference
-PlatformUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-EngineUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-DisableGradualRelease True|False
-SignaturesUpdatesChannel Staged|Broad|NotConfigured
```

Exemple :

Permet `Set-MpPreference -PlatformUpdatesChannel Beta` de configurer les mises à jour de plateforme pour qu’elles arrivent à partir du canal bêta.

Pour plus d’informations sur les paramètres et leur configuration, voir [Set-MpPreference (Antivirus Microsoft Defender)| Microsoft Docs](/powershell/module/defender/set-mppreference).
