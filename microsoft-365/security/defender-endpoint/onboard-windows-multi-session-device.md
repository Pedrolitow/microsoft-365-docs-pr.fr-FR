---
title: Intégrer Windows plusieurs sessions dans Azure Virtual Desktop
description: En savoir plus dans cet article sur l’intégration Windows appareils multisess session dans Azure Virtual Desktop
keywords: Azure Virtual Desktop, WVD, microsoft defender, point de terminaison, intégration
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
ms.openlocfilehash: 709cd408d548e8a7c16973c08b0369616f3b91d1
ms.sourcegitcommit: be095345257225394674698beb3feeb0696ec86d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2021
ms.locfileid: "60240535"
---
# <a name="onboard-windows-multi-session-devices-in-azure-virtual-desktop"></a>Intégrer Windows plusieurs sessions dans Azure Virtual Desktop

6 minutes de lecture

S’applique à :

- Windows sessions multiples s’exécutant sur Azure Virtual Desktop (AVD)

Microsoft Defender pour endpoint prend en charge la surveillance des sessions VDI et Azure Virtual Desktop. En fonction des besoins de votre organisation, vous devrez peut-être implémenter des sessions VDI ou Azure Virtual Desktop pour aider vos employés à accéder aux données et applications d’entreprise à partir d’un appareil nonmanaté, d’un emplacement distant ou d’un scénario similaire. Avec Microsoft Defender pour le point de terminaison, vous pouvez surveiller ces machines virtuelles afin de vérifier les activités anormales.

## <a name="before-you-begin"></a>Avant de commencer

Familiarisez-vous avec les considérations pour [les VDI non persistants.](/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1) Bien [qu’Azure Virtual Desktop](/azure/virtual-desktop/overview) ne propose pas d’options de non-persistance, il offre des moyens d’utiliser une image Windows de premier choix qui peut être utilisée pour mettre en service de nouveaux hôtes et redéployer des ordinateurs. Cela augmente la sécurité dans l’environnement et a un impact sur les entrées créées et conservées dans le portail Microsoft Defender pour points de terminaison, ce qui réduit potentiellement la visibilité de vos analystes de sécurité.

> [!NOTE]
> En fonction de votre choix de méthode d’intégration, les appareils peuvent apparaître dans le portail Microsoft Defender pour Endpoint comme :
>
> - Entrée unique pour chaque bureau virtuel
> - Plusieurs entrées pour chaque bureau virtuel

Microsoft recommande l’intégration d’Azure Virtual Desktop en tant qu’entrée unique par bureau virtuel. Cela garantit que l’expérience d’examen dans le portail Microsoft Defender Endpoint est dans le contexte d’un appareil basé sur le nom de l’ordinateur. Les organisations qui suppriment et redéploient fréquemment des hôtes WVD doivent envisager fortement d’utiliser cette méthode, car elle empêche la création de plusieurs objets pour le même ordinateur dans le portail Microsoft Defender pour Endpoint. Cela peut semer la confusion lors de l’enquête sur les incidents. Pour les environnements de test ou non volatiles, vous pouvez choisir différemment.

Microsoft recommande d’ajouter le script d’intégration Microsoft Defender for Endpoint à l’image de qualité WVD. De cette façon, vous pouvez vous assurer que ce script d’intégration s’exécute immédiatement au premier démarrage. Il est exécuté en tant que script de démarrage lors du premier démarrage sur tous les ordinateurs WVD qui sont mis en service à partir de l’image de premier niveau WVD. Toutefois, si vous utilisez l’une des images de la galerie sans modification, placez le script dans un emplacement partagé et appelez-le à partir d’une stratégie de groupe locale ou de domaine.

> [!NOTE]
> Le placement et la configuration du script de démarrage d’intégration VDI sur l’image de base WVD le configurent en tant que script de démarrage qui s’exécute au démarrage du WVD. Il n’est PAS recommandé d’intégrer l’image de qualité WVD réelle. Une autre considération est la méthode utilisée pour exécuter le script. Il doit s’exécuter aussi tôt que possible dans le processus de démarrage/approvisionnement pour réduire le temps entre la mise à disposition de l’ordinateur pour la réception des sessions et l’intégration de l’appareil au service. Les scénarios ci-dessous 1 & 2 prennent cela en compte.

### <a name="scenarios"></a>Scénarios

Il existe plusieurs façons d’intégrer un ordinateur hôte WVD :

- Exécutez le script dans l’image de choix (ou à partir d’un emplacement partagé) au démarrage.
- Utilisez un outil de gestion pour exécuter le script.
- Par le [biais de l’intégration à Azure Defender](azure-server-integration.md)

#### <a name="scenario-1-using-local-group-policy"></a>*Scénario 1 : utilisation d’une stratégie de groupe locale*

Ce scénario nécessite de placer le script dans une image de base et utilise la stratégie de groupe locale pour s’exécuter au début du processus de démarrage.

Utilisez les instructions de l’outil Intégrer les périphériques [VDI (Virtual Desktop Infrastructure) non persistants.](configure-endpoints-vdi.md)

Suivez les instructions pour une entrée unique pour chaque appareil.

#### <a name="scenario-2-using-domain-group-policy"></a>*Scénario 2 : utilisation de la stratégie de groupe de domaine*

Ce scénario utilise un script central et l’exécute à l’aide d’une stratégie de groupe basée sur un domaine. Vous pouvez également placer le script dans l’image d’or et l’exécuter de la même manière.

##### <a name="download-the-windowsdefenderatponboardingpackagezip-file-from-the-windows-defender-security-center"></a>Télécharger le fichier WindowsDefenderATPOnboardingPackage.zip à partir du Centre de Windows Defender de sécurité

1. Ouvrir le fichier de configuration du package VDI .zip (WindowsDefenderATPOnboardingPackage.zip)

    1. Dans le volet Microsoft 365 Defender navigation du  portail, sélectionnez Paramètres l’intégration des points de terminaison \>  \>  (sous **Gestion des appareils).**
    1. Sélectionnez Windows 10 ou Windows 11 comme système d’exploitation.
    1. Dans le **champ Méthode de** déploiement, sélectionnez les scripts d’intégration VDI pour les points de terminaison non persistants.
    1. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

2. Extrayez le contenu du .zip vers un emplacement partagé en lecture seule accessible par l’appareil. Vous devez avoir un dossier appelé **OptionalParamsPolicy** et les fichiers **WindowsDefenderATPOnboardingScript.cmd** **etOnboard-NonPersistentMachine.ps1**.

##### <a name="use-group-policy-management-console-to-run-the-script-when-the-virtual-machine-starts"></a>Utiliser la console de gestion des stratégies de groupe pour exécuter le script au démarrage de la machine virtuelle

1. Ouvrez la Console de gestion des stratégies de groupe (GPMC), cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans l’Éditeur de gestion des stratégies de groupe, go to **Computer configuration** \> **Preferences** \> **Control panel settings**.

3. Cliquez avec le bouton droit **sur Tâches programmées,** **cliquez** sur Nouveau, puis sur **Tâche** immédiate (au moins Windows 7).

4. Dans la fenêtre Tâche qui s’ouvre, allez dans **l’onglet** Général. Sous **Options de sécurité,** cliquez **sur Modifier l’utilisateur ou le groupe,** puis tapez SYSTEM. Cliquez **sur Vérifier les noms,** puis sur OK. NT AUTHORITY\SYSTEM apparaît en tant que compte d’utilisateur que la tâche exécutera.

5. Sélectionnez **Exécuter, que l’utilisateur soit** connecté ou non, puis cochez la case Exécuter avec les **privilèges les plus élevés.**

6. Go to the **Actions** tab and click **New**. **Assurez-vous que démarrer un programme** est sélectionné dans le champ Action. Entrez les informations suivantes :

   `Action = "Start a program"`

   `Program/Script = C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe`

   `Add Arguments (optional) = -ExecutionPolicy Bypass -command "& \\Path\To\Onboard-NonPersistentMachine.ps1"`

   Ensuite, **sélectionnez OK** et fermez toutes les fenêtres GPMC ouvertes.

#### <a name="scenario-3-onboarding-using-management-tools"></a>*Scénario 3 : intégration à l’aide des outils de gestion*

Si vous envisagez de gérer vos ordinateurs à l’aide d’un outil de gestion, vous pouvez intégrer des appareils Microsoft Endpoint Configuration Manager.

Pour plus d’informations, [voir Onboard Windows à l’aide de Configuration Manager.](configure-endpoints-sccm.md)

> [!WARNING]
> Si vous envisagez d’utiliser les règles de réduction de la [surface](attack-surface-reduction-rules.md)d’attaque, notez que la règle « Bloquer les créations de processus provenant de commandes[PSExec](attack-surface-reduction-rules.md#block-process-creations-originating-from-psexec-and-wmi-commands)et WMI » ne doit pas être utilisée, car cette règle est incompatible avec la gestion via Microsoft Endpoint Configuration Manager. La règle bloque les commandes WMI que le client Configuration Manager utilise pour fonctionner correctement.

> [!TIP]
> Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier que l’appareil est correctement intégré au service. Pour plus d’informations, voir Exécuter un test de détection sur un appareil [Microsoft Defender pour point de terminaison nouvellement intégré.](run-detection-test.md)

#### <a name="tagging-your-machines-when-building-your-golden-image"></a>Marquage de vos ordinateurs lors de la création de votre image de qualité

Dans le cadre de votre intégration, vous pouvez envisager de définir une balise d’ordinateur pour différencier plus facilement les ordinateurs WVD dans le Centre de sécurité Microsoft. Pour plus d’informations, voir [Ajouter des balises de périphérique en définition d’une valeur de clé de Registre.](machine-tags.md#add-device-tags-by-setting-a-registry-key-value)

#### <a name="other-recommended-configuration-settings"></a>Autres paramètres de configuration recommandés

Lorsque vous construisez votre image de premier niveau, vous pouvez également configurer les paramètres de protection initiaux. Pour plus d’informations, [voir autres paramètres de configuration recommandés.](configure-endpoints-gp.md#other-recommended-configuration-settings)

En outre, si vous utilisez des profils utilisateur FSlogix, nous vous recommandons d’exclure les fichiers suivants de la protection toujours en cours :

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

Remarque sur la gestion des licences : lors de l’utilisation de Windows Enterprise multisessexe, en fonction de vos besoins, vous pouvez choisir d’avoir tous les utilisateurs sous licence via Microsoft Defender pour le point de terminaison (par utilisateur), Windows Enterprise E5, Microsoft 365 Security ou Microsoft 365 E5, ou faire en sorte que la VM soit sous licence via Azure Defender.
Les conditions de licence pour Microsoft Defender pour le point de terminaison se trouvent dans : [Exigences de licence.](minimum-requirements.md#licensing-requirements)

#### <a name="related-links"></a>Liens connexes

[Ajouter des exclusions pour Microsoft Defender à l’aide de PowerShell](/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix#add-exclusions-for-windows-defender-by-using-powershell)
