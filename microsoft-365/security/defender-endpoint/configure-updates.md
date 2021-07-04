---
title: Créer un processus de déploiement progressif personnalisé pour les mises à jour De Microsoft Defender
description: Découvrez comment utiliser les outils pris en charge pour créer un processus de déploiement progressif personnalisé pour les mises à jour
keywords: outils de mise à jour, gpo, intune, gm, gestionnaire de point de terminaison Microsoft, stratégie, powershell
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
ms.openlocfilehash: a7a560cb33190105f8df5922e04aeada4d75f398
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2021
ms.locfileid: "53290038"
---
# <a name="create-a-custom-gradual-rollout-process-for-microsoft-defender-updates"></a>Créer un processus de déploiement progressif personnalisé pour les mises à jour De Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

> [!NOTE]
> Cette fonctionnalité nécessite Antivirus Microsoft Defender version 4.18.2106.X ou plus récente.

Pour créer votre propre processus de déploiement progressif personnalisé pour les mises à jour De Defender, vous pouvez utiliser la stratégie de groupe, Microsoft Endpoint Manager et PowerShell.

Le tableau suivant répertorie les paramètres de stratégie de groupe disponibles pour la configuration des canaux de mise à jour :

| Titre du paramètre  | Description  | Emplacement  |
|:---|:---|:---|
| Sélectionner le canal de déploiement de mise à jour de plateforme mensuelle Microsoft Defender progressif  | Activez cette stratégie pour spécifier quand les appareils reçoivent les mises à jour de la plateforme Microsoft Defender pendant le déploiement progressif mensuel. Canal bêta : les appareils qui sont connectés à ce canal seront les premiers à recevoir de nouvelles mises à jour. Sélectionnez Le canal bêta pour participer à l’identification et au signalement des problèmes à Microsoft. Les appareils du Windows Programme Insider sont abonnés à ce canal par défaut. Pour une utilisation dans des environnements de test (manuels) uniquement et un nombre limité d’appareils.  <br><br>  Canal actuel (prévisualisation) : les appareils qui sont connectés à ce canal se voient proposer des mises à jour au plus tôt au cours du cycle de publication progressive mensuel. Suggéré pour les environnements de pré-production/validation.  <br><br>  Canal actuel (progressive) : des mises à jour seront proposées aux appareils après le cycle de publication progressive mensuel. Il est suggéré de s’appliquer à une petite partie représentative de votre population de production (environ 10 %).  <br><br>  Canal actuel (large) : les mises à jour ne seront proposées aux appareils qu’une fois le cycle de publication progressive terminé. Il est suggéré de s’appliquer à un large éventail d’appareils dans votre population de production (environ 10 à 100 %).  <br><br>   Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste à jour automatiquement pendant le cycle de publication progressive. Convient à la plupart des appareils.  | Windows Components\Antivirus Microsoft Defender  |
| Sélectionner le canal de déploiement de mise à jour mensuelle du moteur Microsoft Defender progressif  | Activez cette stratégie pour spécifier quand les appareils reçoivent les mises à jour du moteur Microsoft Defender pendant le déploiement progressif mensuel.  <br><br>  Canal bêta : les appareils qui sont connectés à ce canal seront les premiers à recevoir de nouvelles mises à jour. Sélectionnez Le canal bêta pour participer à l’identification et au signalement des problèmes à Microsoft. Les appareils du Windows Programme Insider sont abonnés à ce canal par défaut. Pour une utilisation dans des environnements de test (manuels) uniquement et un nombre limité d’appareils.  <br><br>  Canal actuel (prévisualisation) : les appareils qui sont connectés à ce canal se voient proposer des mises à jour au plus tôt au cours du cycle de publication progressive mensuel. Suggéré pour les environnements de pré-production/validation.  <br><br>  Canal actuel (progressive) : des mises à jour seront proposées aux appareils après le cycle de publication progressive mensuel. Il est suggéré de s’appliquer à une petite partie représentative de votre population de production (environ 10 %).  <br><br>  Canal actuel (large) : les mises à jour ne seront proposées aux appareils qu’une fois le cycle de publication progressive terminé. Il est suggéré de s’appliquer à un large éventail d’appareils dans votre population de production (environ 10 à 100 %).  <br><br>  Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste à jour automatiquement pendant le cycle de publication progressive. Convient à la plupart des appareils.  | Windows Components\Antivirus Microsoft Defender  |
| Sélectionner le canal de déploiement des mises à jour quotidiennes des définitions microsoft Defender progressives  | Activez cette stratégie pour spécifier le moment où les appareils reçoivent les mises à jour des définitions De Microsoft Defender pendant le déploiement progressif quotidien. <br><br> Canal actuel (étapes) : les mises à jour seront proposées aux appareils après le cycle de publication. Il est suggéré de s’appliquer à une petite partie représentative de la population de production (environ 10 %). <br><br>   Canal actuel (large) : les mises à jour ne seront proposées aux appareils qu’une fois le cycle de publication progressive terminé. Il est suggéré de s’appliquer à un large éventail d’appareils dans votre population de production (environ 10 à 100 %). <br><br>   Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste automatiquement à jour pendant le cycle de publication quotidien. Convient à la plupart des appareils.  | Windows Components\Antivirus Microsoft Defender  |
| Désactiver le déploiement progressif des mises à jour De Microsoft Defender  | Activez cette stratégie pour désactiver le déploiement progressif des mises à jour De Defender. <br><br> Canal actuel (large) : les mises à jour des appareils qui sont définies sur ce canal seront proposées en dernier au cours du cycle de publication progressive. Il est préférable pour les ordinateurs de centre de données qui ne reçoivent que des mises à jour limitées. <br><br> Remarque : ce paramètre s’applique aux mises à jour mensuelles et quotidiennes de Defender et remplace toutes les sélections de canaux précédemment configurées pour les mises à jour de plateforme et de moteur. <br><br> Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste dans le canal actuel (par défaut), sauf indication contraire dans des canaux spécifiques pour les mises à jour de plateforme et de moteur. Restez à jour automatiquement pendant le cycle de publication progressive. Convient à la plupart des appareils.  | Windows Components\Antivirus Microsoft Defender  |

## <a name="group-policy"></a>Stratégie de groupe

> [!NOTE]
> Un modèle ADMX Defender mis à jour sera publié avec la version 21H2 de Windows 10. Une version non localisée est disponible en téléchargement sur https://github.com/microsoft/defender-updatecontrols .

Vous pouvez utiliser la [stratégie de](/windows/win32/srvnodes/group-policy?redirectedfrom=MSDN)groupe pour configurer et gérer les Antivirus Microsoft Defender sur vos points   de terminaison.

En règle générale, vous pouvez utiliser la procédure suivante pour configurer ou modifier Antivirus Microsoft Defender de stratégie de groupe :

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la  **Console** de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe **à** configurer, puis cliquez sur  **Modifier.**

2. À l’aide de l’Éditeur de gestion des stratégies de groupe, go to **Computer configuration**.

3. Cliquez **sur Modèles d’administration.**

4. Développez l’arborescence **Windows composants > Antivirus Microsoft Defender**.

5. Développez la section (appelée Emplacement dans le tableau de cette rubrique) qui contient le paramètre que vous souhaitez ****   configurer, double-cliquez sur le paramètre pour l’ouvrir et a apporter des modifications de configuration.

6. [Déployez l’GPO mis à jour comme vous le faites normalement.](https://msdn.microsoft.com/library/ee663280(v=vs.85).aspx)

## <a name="intune"></a>Intune

Suivez les instructions du lien ci-dessous pour créer une stratégie personnalisée dans Intune :

[Ajouter des paramètres personnalisés pour Windows 10 appareils dans Microsoft Intune - Documents Microsoft Azure \|](/mem/intune/configuration/custom-settings-windows-10)

Pour plus d’informations sur les CSP Defender utilisés pour le processus de déploiement progressif, voir [CSP Defender](/windows/client-management/mdm/defender-csp).

## <a name="powershell"></a>PowerShell

Utilisez la `Set-MpPreference` cmdlet pour configurer le déploiement des mises à jour progressives.

Utilisez les paramètres suivants :

```powershell
Set-MpPreference
-PlatformUpdatesChannel Beta|Preview|Staged|Broad|NotConfigured
-EngineUpdatesChannel Beta|Preview|Staged|Broad|NotConfigured
-DisableGradualRelease True|False
-SignaturesUpdatesChannel Staged|Broad|NotConfigured
```

Exemple :

Permet `Set-MpPreference -PlatformUpdatesChannel Beta` de configurer les mises à jour de plateforme pour qu’elles arrivent à partir du canal bêta.

Pour plus d’informations sur les paramètres et comment les configurer, voir [Set-MpPreference (Defender) | Microsoft Docs](/powershell/module/defender/set-mppreference).
