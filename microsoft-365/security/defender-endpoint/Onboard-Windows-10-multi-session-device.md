---
title: Intégrer des appareils Windows 10 à sessions multiples dans Windows Virtual Desktop
description: En savoir plus dans cet article sur l’intégration d’appareils Windows 10 multisesses dans Windows Virtual Desktop
keywords: Windows Virtual Desktop, WVD, microsoft defender, point de terminaison, intégration
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.openlocfilehash: 3f925fdc514c5e53b50f748d991f54d20fb49bd0
ms.sourcegitcommit: 7ebed5810480d7c49f8ca03207b5ea84993d253f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "51488144"
---
# <a name="onboard-windows-10-multi-session-devices-in-windows-virtual-desktop"></a>Intégrer des appareils Windows 10 à sessions multiples dans Windows Virtual Desktop 
6 minutes de lecture 

S’applique à : 
- Windows 10 multisesse en cours d’exécution sur Windows Virtual Desktop (WVD) 

Microsoft Defender pour point de terminaison prend en charge la surveillance des sessions VDI et Windows Virtual Desktop. Selon les besoins de votre organisation, vous devrez peut-être implémenter des sessions VDI ou Windows Virtual Desktop pour aider vos employés à accéder aux données et applications d’entreprise à partir d’un appareil nonmanaté, d’un emplacement distant ou d’un scénario similaire. Avec Microsoft Defender pour le point de terminaison, vous pouvez surveiller ces machines virtuelles afin de vérifier les activités anormales.

 ## <a name="before-you-begin"></a>Avant de commencer
Familiarisez-vous avec [les considérations pour les VDI non persistants.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1) Bien que [Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/overview) ne propose pas d’options de non-persistance, il offre des moyens d’utiliser une image Windows de premier choix qui peut être utilisée pour mettre en service de nouveaux hôtes et redéployer des ordinateurs. Cela augmente la sécurité dans l’environnement et a un impact sur les entrées créées et conservées dans le portail Microsoft Defender pour points de terminaison, ce qui réduit potentiellement la visibilité de vos analystes de sécurité.

> [!NOTE]
> En fonction de votre choix de méthode d’intégration, les appareils peuvent apparaître dans le portail Microsoft Defender pour Endpoint comme : 
> - Entrée unique pour chaque bureau virtuel 
> - Plusieurs entrées pour chaque bureau virtuel 

Microsoft recommande l’intégration de Windows Virtual Desktop en tant qu’entrée unique par bureau virtuel. Cela garantit que l’expérience d’examen dans le portail Microsoft Defender Endpoint est dans le contexte d’un appareil basé sur le nom de l’ordinateur. Les organisations qui suppriment et redéploient fréquemment des hôtes WVD doivent envisager fortement d’utiliser cette méthode, car elle empêche la création de plusieurs objets pour le même ordinateur dans le portail Microsoft Defender pour Endpoint. Cela peut semer la confusion lors de l’enquête sur les incidents. Pour les environnements de test ou non volatiles, vous pouvez choisir différemment. 

Microsoft recommande d’ajouter le script d’intégration De Microsoft Defender pour point de terminaison à l’image wvd de l’or. De cette façon, vous pouvez vous assurer que ce script d’intégration s’exécute immédiatement au premier démarrage. Il est exécuté en tant que script de démarrage lors du premier démarrage sur tous les ordinateurs WVD qui sont mis en service à partir de l’image de premier niveau WVD. Toutefois, si vous utilisez l’une des images de la galerie sans modification, placez le script dans un emplacement partagé et appelez-le à partir d’une stratégie de groupe locale ou de domaine. 

> [!NOTE]
> Le placement et la configuration du script de démarrage d’intégration VDI sur l’image de base WVD le configurent en tant que script de démarrage qui s’exécute au démarrage du WVD. Il n’est PAS recommandé d’intégrer l’image de qualité WVD réelle. Une autre considération est la méthode utilisée pour exécuter le script. Il doit s’exécuter aussi tôt que possible dans le processus de démarrage/approvisionnement pour réduire le temps entre la mise à disposition de l’ordinateur pour la réception des sessions et l’intégration de l’appareil au service. Les scénarios ci-dessous 1 & 2 prennent cela en compte.

### <a name="scenarios"></a>Scénarios
Il existe plusieurs façons d’intégrer un ordinateur hôte WVD :

- Exécutez le script dans l’image de choix (ou à partir d’un emplacement partagé) au démarrage.
- Utilisez un outil de gestion pour exécuter le script.

#### <a name="scenario-1-using-local-group-policy"></a>*Scénario 1 : utilisation d’une stratégie de groupe locale*
Ce scénario nécessite de placer le script dans une image de base et utilise la stratégie de groupe locale pour s’exécuter au début du processus de démarrage.

Utilisez les instructions des périphériques VDI d’infrastructure de bureau virtuel [non persistants intégrés.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1)

Suivez les instructions pour une entrée unique pour chaque appareil.

#### <a name="scenario-2-using-domain-group-policy"></a>*Scénario 2 : utilisation de la stratégie de groupe de domaine*
Ce scénario utilise un script central et l’exécute à l’aide d’une stratégie de groupe basée sur un domaine. Vous pouvez également placer le script dans l’image d’or et l’exécuter de la même manière.

**Télécharger le fichier WindowsDefenderATPOnboardingPackage.zip à partir du Centre Windows Defender sécurité**
1. Ouvrez le fichier .zip du package de configuration VDI (WindowsDefenderATPOnboardingPackage.zip)  
    - Dans le volet de navigation du Centre de sécurité Microsoft Defender, sélectionnez **Intégration** des  >  **paramètres.** 
    - Sélectionnez Windows 10 comme système d’exploitation. 
    - Dans le **champ Méthode de** déploiement, sélectionnez les scripts d’intégration VDI pour les points de terminaison non persistants. 
    - Cliquez **sur Télécharger le package** et enregistrez le fichier .zip. 
2. Extrayez le contenu du fichier .zip vers un emplacement partagé en lecture seule accessible par l’appareil. Vous devez avoir un dossier appelé **OptionalParamsPolicy** et les fichiers **WindowsDefenderATPOnboardingScript.cmd** **etOnboard-NonPersistentMachine.ps1**.

**Utiliser la console de gestion des stratégies de groupe pour exécuter le script au démarrage de la machine virtuelle**
1. Ouvrez la Console de gestion des stratégies de groupe (GPMC), cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**
1. Dans l’Éditeur de gestion des stratégies de groupe, go to **Computer configuration** \> **Preferences** \> **Control panel settings**. 
1. Cliquez avec le bouton droit **sur Tâches programmées,** cliquez sur **Nouveau,** puis cliquez sur **Tâche immédiate** (Au moins Windows 7). 
1. Dans la fenêtre Tâche qui s’ouvre, allez dans **l’onglet** Général. Sous **Options de sécurité,** cliquez **sur Modifier l’utilisateur ou le** groupe, puis tapez SYSTEM. Cliquez **sur Vérifier les noms,** puis sur OK. NT AUTHORITY\SYSTEM apparaît en tant que compte d’utilisateur que la tâche exécutera. 
1. Sélectionnez **Exécuter, que l’utilisateur soit** connecté ou non, puis cochez la case Exécuter avec les **privilèges les plus élevés.** 
1. Go to the **Actions** tab and click **New**. **Assurez-vous que démarrer un programme** est sélectionné dans le champ Action. Entrez les informations suivantes : 

> Action = « Démarrer un programme » <br>
> Program/Script = C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe <br>
> Ajouter des arguments (facultatif) = -ExecutionPolicy Bypass -command « & \\Path\To\Onboard-NonPersistentMachine.ps1 »

Cliquez **sur OK** et fermez toutes les fenêtres GPMC ouvertes.

#### <a name="scenario-3-onboarding-using-management-tools"></a>*Scénario 3 : intégration à l’aide des outils de gestion*

Si vous envisagez de gérer vos ordinateurs à l’aide d’un outil de gestion, vous pouvez intégrer des appareils avec Microsoft Endpoint Configuration Manager.

Pour plus d’informations, voir : [Intégrer des appareils Windows 10 à l’aide de Configuration Manager](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-sccm) 

> [!WARNING]
> Si vous envisagez d’utiliser les règles de réduction de la [surface](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/attack-surface-reduction)d’attaque, notez que la règle « Bloquer les créations de processus provenant des commandes[PSExec](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/attack-surface-reduction#block-process-creations-originating-from-psexec-and-wmi-commands)et WMI » ne doit pas être utilisée car elle est incompatible avec la gestion via Microsoft Endpoint Configuration Manager, car cette règle bloque les commandes WMI utilisées par le client Configuration Manager pour fonctionner correctement. 

> [!TIP]
> Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier que l’appareil est correctement intégré au service. Pour plus d’informations, voir Exécuter un test de détection sur un appareil [Microsoft Defender pour point de terminaison nouvellement intégré.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/run-detection-test) 

#### <a name="tagging-your-machines-when-building-your-golden-image"></a>Marquage de vos ordinateurs lors de la création de votre image de qualité 

Dans le cadre de votre intégration, vous pouvez envisager de définir une balise d’ordinateur pour différencier plus facilement les ordinateurs WVD dans le Centre de sécurité Microsoft. Pour plus d’informations, voir [Ajouter des balises de périphérique en définition d’une valeur de clé de Registre.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/machine-tags#add-device-tags-by-setting-a-registry-key-value) 

#### <a name="other-recommended-configuration-settings"></a>Autres paramètres de configuration recommandés 

Lorsque vous construisez votre image de premier niveau, vous pouvez également configurer les paramètres de protection initiaux. Pour plus d’informations, [voir autres paramètres de configuration recommandés.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-gp#other-recommended-configuration-settings) 

En outre, si vous utilisez des profils utilisateur FSlogix, nous vous recommandons d’exclure les fichiers suivants de la protection toujours en cours : 

**Exclure des fichiers :** 

> %ProgramFiles%\FSLogix\Apps\frxdrv.sys <br>
> %ProgramFiles%\FSLogix\Apps\frxdrvvt.sys <br>
> %ProgramFiles%\FSLogix\Apps\frxccd.sys <br>
> %TEMP% \* . VHD <br>
> %TEMP% \* . VHDX <br>
> %Windir%\TEMP \* . VHD <br>
> %Windir%\TEMP \* . VHDX <br>
> \\storageaccount.file.core.windows.net\partage \* \* . VHD <br>
> \\storageaccount.file.core.windows.net\partage \* \* . VHDX <br>

**Exclure des processus :**

> %ProgramFiles%\FSLogix\Apps\frxccd.exe <br>
> %ProgramFiles%\FSLogix\Apps\frxccds.exe <br>
> %ProgramFiles%\FSLogix\Apps\frxsvc.exe <br>

#### <a name="licensing-requirements"></a>Critères de licence 

Windows 10 Multi-session est un système d’exploitation client. Les conditions de licence pour Microsoft Defender pour le point de terminaison se trouvent dans : [Conditions de licence.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements)