---
title: Intégrer des appareils Windows dans Azure Virtual Desktop
description: Découvrir l’intégration d’appareils Windows à Defender pour point de terminaison dans Azure Virtual Desktop
keywords: Azure Virtual Desktop, AVD, microsoft defender, point de terminaison, intégration
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 63966b84fc2d5a57f9c8b405a97d61ba17450dfb
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66822132"
---
# <a name="onboard-windows-devices-in-azure-virtual-desktop"></a>Intégrer des appareils Windows dans Azure Virtual Desktop

6 minutes pour lire

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Windows multisession s’exécutant sur Azure Virtual Desktop (AVD)
- [Windows 10 Entreprise multisession](/microsoft-365/security/defender-endpoint/azure-server-integration)

Microsoft Defender pour point de terminaison prend en charge la surveillance des sessions VDI et Azure Virtual Desktop. En fonction des besoins de votre organisation, vous devrez peut-être implémenter des sessions VDI ou Azure Virtual Desktop pour aider vos employés à accéder aux données et applications d’entreprise à partir d’un appareil non managé, d’un emplacement distant ou d’un scénario similaire. Avec Microsoft Defender pour point de terminaison, vous pouvez surveiller ces machines virtuelles pour détecter une activité anormale.

## <a name="before-you-begin"></a>Avant de commencer

Familiarisez-vous avec [les considérations relatives à l’IDV non persistant](/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1). Bien [qu’Azure Virtual Desktop](/azure/virtual-desktop/overview) ne fournisse pas d’options de non-persistance, il fournit des moyens d’utiliser une image Windows dorée qui peut être utilisée pour approvisionner de nouveaux hôtes et redéployer des machines. Cela augmente la volatilité dans l’environnement et a donc un impact sur les entrées créées et conservées dans le portail Microsoft Defender pour point de terminaison, ce qui peut réduire la visibilité pour vos analystes de sécurité.

> [!NOTE]
> Selon votre choix de méthode d’intégration, les appareils peuvent apparaître dans Microsoft Defender pour point de terminaison portail comme suit :
>
> - Entrée unique pour chaque bureau virtuel
> - Plusieurs entrées pour chaque bureau virtuel

Microsoft recommande l’intégration d’Azure Virtual Desktop en tant qu’entrée unique par bureau virtuel. Cela garantit que l’expérience d’investigation dans le portail Microsoft Defender pour point de terminaison se trouve dans le contexte d’un appareil en fonction du nom de l’ordinateur. Les organisations qui suppriment et redéployent fréquemment des hôtes AVD doivent fortement envisager d’utiliser cette méthode, car elle empêche la création de plusieurs objets pour la même machine dans le portail Microsoft Defender pour point de terminaison. Cela peut entraîner une confusion lors de l’enquête sur les incidents. Pour les environnements de test ou non volatiles, vous pouvez choisir différemment.

Microsoft recommande d’ajouter le script d’intégration Microsoft Defender pour point de terminaison à l’image d’or AVD. De cette façon, vous pouvez être sûr que ce script d’intégration s’exécute immédiatement au premier démarrage. Il est exécuté en tant que script de démarrage au premier démarrage sur toutes les machines AVD approvisionnées à partir de l’image d’or AVD. Toutefois, si vous utilisez l’une des images de la galerie sans modification, placez le script dans un emplacement partagé et appelez-le à partir d’une stratégie de groupe de domaine ou locale.

> [!NOTE]
> Le positionnement et la configuration du script de démarrage d’intégration VDI sur l’image d’or AVD le configurent en tant que script de démarrage qui s’exécute au démarrage de l’AVD. Il n’est **pas** recommandé d’intégrer l’image d’or AVD réelle. Une autre considération est la méthode utilisée pour exécuter le script. Il doit s’exécuter aussi tôt que possible dans le processus de démarrage/approvisionnement pour réduire le temps entre l’ordinateur disponible pour recevoir des sessions et l’intégration de l’appareil au service. Les scénarios 1 et 2 ci-dessous en tiennent compte.

### <a name="scenarios"></a>Scénarios

Il existe plusieurs façons d’intégrer un ordinateur hôte AVD :

- Exécutez le script dans l’image d’or (ou à partir d’un emplacement partagé) au démarrage.
- Utilisez un outil de gestion pour exécuter le script.
- Par [le biais de l’intégration à Microsoft Defender pour le cloud](azure-server-integration.md)

#### <a name="scenario-1-using-local-group-policy"></a>*Scénario 1 : Utilisation d’une stratégie de groupe locale*

Ce scénario nécessite de placer le script dans une image d’or et utilise une stratégie de groupe locale pour s’exécuter au début du processus de démarrage.

Suivez les instructions fournies dans [Intégrer les appareils VDI (Virtual Desktop Infrastructure) non persistants](configure-endpoints-vdi.md).

Suivez les instructions d’une entrée unique pour chaque appareil.

#### <a name="scenario-2-using-domain-group-policy"></a>*Scénario 2 : Utilisation de la stratégie de groupe de domaines*

Ce scénario utilise un script centralisé et l’exécute à l’aide d’une stratégie de groupe basée sur un domaine. Vous pouvez également placer le script dans l’image d’or et l’exécuter de la même façon.

##### <a name="download-the-windowsdefenderatponboardingpackagezip-file-from-the-microsoft-365-defender-portal"></a>Télécharger le fichier WindowsDefenderATPOnboardingPackage.zip à partir du portail Microsoft 365 Defender

1. Ouvrir le fichier .zip du package de configuration VDI (WindowsDefenderATPOnboardingPackage.zip)

    1. Dans le volet de navigation du portail Microsoft 365 Defender, sélectionnez **Paramètres** \> **Endpoints** \> **Onboarding** (sous **Gestion des appareils**).
    1. Sélectionnez Windows 10 ou Windows 11 comme système d’exploitation.
    1. Dans le champ **Méthode de déploiement** , sélectionnez les scripts d’intégration VDI pour les points de terminaison non persistants.
    1. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.

2. Extrayez le contenu du fichier .zip à un emplacement partagé en lecture seule accessible par l’appareil. Vous devez disposer d’un dossier appelé **OptionalParamsPolicy** et des fichiers **WindowsDefenderATPOnboardingScript.cmd** et **Onboard-NonPersistentMachine.ps1**.

##### <a name="use-group-policy-management-console-to-run-the-script-when-the-virtual-machine-starts"></a>Utiliser stratégie de groupe console de gestion pour exécuter le script au démarrage de la machine virtuelle

1. Ouvrez la console de gestion stratégie de groupe (GPMC), cliquez avec le bouton droit sur l’objet stratégie de groupe (GPO) que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. Dans l’éditeur de gestion stratégie de groupe, accédez aux **paramètres du panneau de configuration** **des préférences** \> de **l’ordinateur**\>.

3. Cliquez avec le bouton droit sur **Tâches planifiées**, cliquez sur **Nouveau**, puis sur **Tâche immédiate** (Au moins Windows 7).

4. Dans la fenêtre Tâche qui s’ouvre, accédez à l’onglet **Général** . Sous **Options de sécurité,** cliquez sur **Modifier l’utilisateur ou le groupe** et tapez SYSTEM. Cliquez sur **Vérifier les noms** , puis sur OK. NT AUTHORITY\SYSTEM apparaît sous la forme du compte d’utilisateur sous lequel la tâche s’exécutera.

5. Sélectionnez **Exécuter si l’utilisateur est connecté ou non** et cochez la case **Exécuter avec les privilèges les plus élevés** .

6. Accédez à l’onglet **Actions** , puis cliquez sur **Nouveau**. Vérifiez que **démarrer un programme** est sélectionné dans le champ Action. Entrez les informations suivantes :

   `Action = "Start a program"`

   `Program/Script = C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe`

   `Add Arguments (optional) = -ExecutionPolicy Bypass -command "& \\Path\To\Onboard-NonPersistentMachine.ps1"`

   Ensuite, sélectionnez **OK** et fermez toutes les fenêtres GPMC ouvertes.

#### <a name="scenario-3-onboarding-using-management-tools"></a>*Scénario 3 : Intégration à l’aide d’outils de gestion*

Si vous envisagez de gérer vos machines à l’aide d’un outil de gestion, vous pouvez intégrer des appareils à Microsoft Endpoint Configuration Manager.

Pour plus d’informations, consultez [Intégrer des appareils Windows à l’aide de Configuration Manager](configure-endpoints-sccm.md).

> [!WARNING]
> Si vous envisagez d’utiliser la [référence des règles de réduction de la surface](attack-surface-reduction-rules-reference.md) d’attaque, notez que la règle « [Bloquer les créations de processus provenant de commandes PSExec et WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands) » ne doit pas être utilisée, car cette règle est incompatible avec la gestion par le biais de Microsoft Endpoint Configuration Manager. La règle bloque les commandes WMI que le client Configuration Manager utilise pour fonctionner correctement.

> [!TIP]
> Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier que l’appareil est correctement intégré au service. Pour plus d’informations, consultez [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md).

#### <a name="tagging-your-machines-when-building-your-golden-image"></a>Marquage de vos machines lors de la création de votre image d’or

Dans le cadre de votre intégration, vous pouvez envisager de définir une balise d’ordinateur pour différencier plus facilement les machines AVD dans le Centre de sécurité Microsoft. Pour plus d’informations, consultez [Ajouter des balises d’appareil en définissant une valeur de clé de Registre](machine-tags.md#add-device-tags-by-setting-a-registry-key-value).

#### <a name="other-recommended-configuration-settings"></a>Autres paramètres de configuration recommandés

Lors de la génération de votre image d’or, vous souhaiterez peut-être également configurer les paramètres de protection initiaux. Pour plus d’informations, consultez [Autres paramètres de configuration recommandés](configure-endpoints-gp.md#other-recommended-configuration-settings).

En outre, si vous utilisez des profils utilisateur FSlogix, nous vous recommandons d’exclure les fichiers suivants de la protection always-on :

**Exclure des fichiers :**

`%ProgramFiles%\FSLogix\Apps\frxdrv.sys`

`%ProgramFiles%\FSLogix\Apps\frxdrvvt.sys`

`%ProgramFiles%\FSLogix\Apps\frxccd.sys`

`%TEMP%\*.VHD`

`%TEMP%\*.VHDX`

`%Windir%\TEMP\*.VHD`

`%Windir%\TEMP\*.VHDX`

`\\storageaccount.file.core.windows.net\share\*\*.VHD`

`\\storageaccount.file.core.windows.net\share\*\*.VHDX`

**Exclure les processus :**

`%ProgramFiles%\FSLogix\Apps\frxccd.exe`

`%ProgramFiles%\FSLogix\Apps\frxccds.exe`

`%ProgramFiles%\FSLogix\Apps\frxsvc.exe`

#### <a name="licensing-requirements"></a>Conditions d'octroi de licence

Remarque sur les licences : lorsque vous utilisez Windows Enterprise multisession, en fonction de vos besoins, vous pouvez choisir d’avoir tous les utilisateurs sous licence par le biais de Microsoft Defender pour point de terminaison (par utilisateur), Windows Enterprise E5, Microsoft 365 Security ou Microsoft 365 E5, ou de disposer d’une licence de machine virtuelle par le biais de Microsoft Defender pour le cloud.
Les exigences de licence pour Microsoft Defender pour point de terminaison sont disponibles à l’adresse suivante : [Conditions de licence](minimum-requirements.md#licensing-requirements).

### <a name="known-issues-and-limitations"></a>Problèmes connus et conseils

Seul Microsoft Edge est pris en charge pour le filtrage web dans Windows 10 multisession.

#### <a name="related-links"></a>Liens connexes

[Ajouter des exclusions pour Defender pour point de terminaison via PowerShell](/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix#add-exclusions-for-microsoft-defender-by-using-powershell)
