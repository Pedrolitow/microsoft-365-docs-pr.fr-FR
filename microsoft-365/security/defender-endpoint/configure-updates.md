---
title: Créer un processus de déploiement progressif personnalisé pour les mises à jour Microsoft Defender
description: Découvrez comment utiliser les outils pris en charge pour créer un processus de déploiement progressif personnalisé pour les mises à jour
keywords: update tools, gpo, intune, mdm, microsoft endpoint manager, policy, powershell
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
ms.openlocfilehash: 4a963172e69b61a7cb33486132630e0d56d0420b
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788543"
---
# <a name="create-a-custom-gradual-rollout-process-for-microsoft-defender-updates"></a>Créer un processus de déploiement progressif personnalisé pour les mises à jour Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

> [!NOTE]
> Cette fonctionnalité nécessite Antivirus Microsoft Defender version 4.18.2106.X ou ultérieure.

Pour créer votre propre processus de déploiement progressif personnalisé pour les mises à jour Defender, vous pouvez utiliser stratégie de groupe, Microsoft Endpoint Manager et PowerShell.

Le tableau suivant répertorie les paramètres de stratégie de groupe disponibles pour la configuration des canaux de mise à jour :

<br>

****

|Définition du titre|Description|Emplacement|
|---|---|---|
|Sélectionner le canal de lancement de mise à jour mensuelle de la plateforme Microsoft Defender progressif|Activez cette stratégie pour spécifier quand les appareils reçoivent les mises à jour de la plateforme Microsoft Defender pendant le déploiement progressif mensuel. <p> Canal bêta : les appareils définis sur ce canal seront les premiers à recevoir de nouvelles mises à jour. Sélectionnez Canal bêta pour participer à l’identification et à la création de rapports sur les problèmes à Microsoft. Les appareils du programme Windows Insider sont abonnés par défaut à ce canal. Pour une utilisation dans des environnements de test (manuels) uniquement et un nombre limité d’appareils. <p> Canal actuel (préversion) : les appareils définis sur ce canal recevront les mises à jour les plus tôt pendant le cycle de publication progressif mensuel. Suggéré pour les environnements de préproduction/validation. <p> Canal actuel (intermédiaire) : les appareils recevront des mises à jour après le cycle de mise en production progressif mensuel. Nous vous suggérons de vous appliquer à une petite partie représentative de votre population de production (environ 10 %). <p> Canal actuel (large) : les appareils ne seront mis à jour qu’une fois le cycle de mise en production progressif terminé. Suggéré de s’appliquer à un large éventail d’appareils dans votre population de production (~10-100%). <p> Délai critique : les appareils se verront proposer des mises à jour avec un délai de 48 heures. Suggéré pour les environnements critiques uniquement. <p>Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste à jour automatiquement pendant le cycle de mise en production progressive. Convient à la plupart des appareils.|composants Windows\Antivirus Microsoft Defender|
|Sélectionner le canal de lancement de mise à jour mensuelle du moteur Microsoft Defender progressif|Activez cette stratégie pour spécifier quand les appareils reçoivent les mises à jour du moteur Microsoft Defender pendant le déploiement progressif mensuel. <p> Canal bêta : les appareils définis sur ce canal seront les premiers à recevoir de nouvelles mises à jour. Sélectionnez Canal bêta pour participer à l’identification et à la création de rapports sur les problèmes à Microsoft. Les appareils du programme Windows Insider sont abonnés par défaut à ce canal. Pour une utilisation dans des environnements de test (manuels) uniquement et un nombre limité d’appareils. <p> Canal actuel (préversion) : les appareils définis sur ce canal recevront les mises à jour les plus tôt pendant le cycle de publication progressif mensuel. Suggéré pour les environnements de préproduction/validation. <p> Canal actuel (intermédiaire) : les appareils recevront des mises à jour après le cycle de mise en production progressif mensuel. Nous vous suggérons de vous appliquer à une petite partie représentative de votre population de production (environ 10 %). <p> Canal actuel (large) : les appareils ne seront mis à jour qu’une fois le cycle de mise en production progressif terminé. Suggéré de s’appliquer à un large éventail d’appareils dans votre population de production (~10-100%). <p> Délai critique : les appareils se verront proposer des mises à jour avec un délai de 48 heures. Suggéré pour les environnements critiques uniquement.<p> Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste à jour automatiquement pendant le cycle de mise en production progressive. Convient à la plupart des appareils.|composants Windows\Antivirus Microsoft Defender|
|Sélectionner le canal de déploiement progressif des mises à jour quotidiennes du renseignement de sécurité Microsoft Defender|Activez cette stratégie pour spécifier quand les appareils reçoivent les mises à jour du renseignement de sécurité Microsoft Defender pendant le déploiement progressif quotidien. <p> Canal actuel (intermédiaire) : les appareils recevront des mises à jour après le cycle de mise en production. Suggéré de s’appliquer à une petite partie représentative de la population de production (environ 10 %). <p> Canal actuel (large) : les appareils ne seront mis à jour qu’une fois le cycle de mise en production progressif terminé. Suggéré de s’appliquer à un large éventail d’appareils dans votre population de production (~10-100%). <p>  Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste à jour automatiquement pendant le cycle de publication quotidien. Convient à la plupart des appareils.|composants Windows\Antivirus Microsoft Defender|
|Désactiver le déploiement progressif des mises à jour de Microsoft Defender|Activez cette stratégie pour désactiver le déploiement progressif des mises à jour Defender. <p> Canal actuel (large) : les appareils définis sur ce canal seront mis à jour en dernier pendant le cycle de mise en production progressive. Idéal pour les machines de centre de données qui reçoivent uniquement des mises à jour limitées. <p> Remarque : ce paramètre s’applique à la fois aux mises à jour mensuelles et quotidiennes de Defender et remplace toutes les sélections de canaux précédemment configurées pour les mises à jour de plateforme et de moteur. <p> Si vous désactivez ou ne configurez pas cette stratégie, l’appareil reste dans le canal actuel (par défaut), sauf indication contraire dans des canaux spécifiques pour les mises à jour de plateforme et de moteur. Restez à jour automatiquement pendant le cycle de mise en production progressive. Convient à la plupart des appareils.|composants Windows\Antivirus Microsoft Defender|
|

## <a name="group-policy"></a>Stratégie de groupe

> [!NOTE]
> Un modèle Defender ADMX mis à jour sera publié avec la version 21H2 de Windows 10. Une version non localisée est disponible en téléchargement à l’adresse https://github.com/microsoft/defender-updatecontrols.

Vous pouvez utiliser [stratégie de groupe](/windows/win32/srvnodes/group-policy?redirectedfrom=MSDN) pour configurer et gérer Antivirus Microsoft Defender sur vos points de terminaison.

En général, vous pouvez utiliser la procédure suivante pour configurer ou modifier Antivirus Microsoft Defender paramètres de stratégie de groupe :

1. Sur votre machine de gestion stratégie de groupe, ouvrez la **console de gestion stratégie de groupe**, cliquez avec le bouton droit sur **l’objet stratégie de groupe** (GPO) que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. À l’aide de l’éditeur de gestion stratégie de groupe, accédez à **la configuration de l’ordinateur**.

3. Cliquez sur **Modèles d’administration**.

4. Développez l’arborescence pour **Windows composants > Antivirus Microsoft Defender**.

5. Développez la section (appelée **Emplacement** dans le tableau de cette rubrique) qui contient le paramètre que vous souhaitez configurer, double-cliquez sur le paramètre pour l’ouvrir et apportez des modifications à la configuration.

6. [Déployez l’objet de stratégie de groupe mis à jour comme vous le faites normalement](https://msdn.microsoft.com/library/ee663280(v=vs.85).aspx).

## <a name="intune"></a>Intune

Suivez les instructions du lien ci-dessous pour créer une stratégie personnalisée dans Intune :

[Ajouter des paramètres personnalisés pour les appareils Windows 10 dans Microsoft Intune - Azure \|Microsoft Docs](/mem/intune/configuration/custom-settings-windows-10)

Pour plus d’informations sur le fournisseur de solutions CSP Defender utilisé pour le processus de déploiement progressif, consultez [Le fournisseur de solutions Cloud Defender](/windows/client-management/mdm/defender-csp).

## <a name="powershell"></a>PowerShell

Utilisez l’applet `Set-MpPreference` de commande pour configurer le déploiement des mises à jour progressives.

Utilisez les paramètres suivants :

```powershell
Set-MpPreference
-PlatformUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-EngineUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-DisableGradualRelease True|False
-SignaturesUpdatesChannel Staged|Broad|NotConfigured
```

Exemple :

Permet `Set-MpPreference -PlatformUpdatesChannel Beta` de configurer les mises à jour de plateforme pour qu’ils arrivent à partir du canal bêta.

Pour plus d’informations sur les paramètres et sur la façon de les configurer, consultez [Set-MpPreference (Antivirus Microsoft Defender)|Microsoft Docs](/powershell/module/defender/set-mppreference).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison sur les fonctionnalités Android](android-configure.md)
> - [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)