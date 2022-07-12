---
title: Guide de déploiement de l’infrastructure de bureau virtuel antivirus Microsoft Defender
description: Découvrez comment déployer l’antivirus Microsoft Defender dans un environnement de bureau virtuel pour un meilleur équilibre entre la protection et les performances.
keywords: vdi, hyper-v, machine virtuelle, machine virtuelle, windows defender, antivirus, av, bureau virtuel, bureau à distance
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: jesquive
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 61f0e265e0a375aaff4d1ad445ac6e1bbeb05b1d
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717511"
---
# <a name="deployment-guide-for-microsoft-defender-antivirus-in-a-virtual-desktop-infrastructure-vdi-environment"></a>Guide de déploiement de l’antivirus Microsoft Defender dans un environnement VDI (Virtual Desktop Infrastructure)

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

En plus des configurations locales ou matérielles standard, vous pouvez utiliser l’antivirus Microsoft Defender dans un environnement de bureau à distance (RDS) ou d’infrastructure de bureau virtuel (VDI) non persistant. Avec la possibilité de déployer facilement des mises à jour sur des machines virtuelles s’exécutant dans des VM, vous pouvez obtenir des mises à jour sur vos machines rapidement et facilement. Vous n’avez plus besoin de créer et de sceller régulièrement des images d’or, car les mises à jour sont développées dans leurs bits de composant sur le serveur hôte, puis téléchargées directement sur la machine virtuelle lorsqu’elle est activée.

Ce guide explique comment configurer vos machines virtuelles pour une protection et des performances optimales, notamment comment :

- [Configurer un partage de fichiers VDI dédié pour les mises à jour du renseignement de sécurité](#set-up-a-dedicated-vdi-file-share)
- [Analyses aléatoires planifiées](#randomize-scheduled-scans)
- [Utiliser des analyses rapides](#use-quick-scans)
- [Empêcher les notifications](#prevent-notifications)
- [Désactiver l’occurrence d’analyses après chaque mise à jour](#disable-scans-after-an-update)
- [Analyser les machines obsolètes ou les machines qui sont hors connexion depuis un certain temps](#scan-vms-that-have-been-offline)
- [Appliquer des exclusions](#exclusions)

Pour plus d’informations sur Bureau à distance Microsoft services et la prise en charge de VDI, consultez [la documentation Azure Virtual Desktop](/azure/virtual-desktop).

Pour les machines virtuelles basées sur Azure, consultez [Installer Endpoint Protection dans Microsoft Defender pour cloud](/azure/defender-for-cloud/endpoint-protection-recommendations-technical).

> [!IMPORTANT]
> Bien que l’infrastructure VDI puisse être hébergée sur Windows Server 2012 ou Windows Server 2016, les machines virtuelles doivent être en cours d’exécution Windows 10, 1607 au minimum, en raison de l’augmentation des technologies de protection et des fonctionnalités qui ne sont pas disponibles dans les versions antérieures de Windows.
> Il existe des améliorations des performances et des fonctionnalités dans la façon dont Microsoft Defender AV fonctionne sur les machines virtuelles dans Windows 10 Insider Preview, build 18323 (et versions ultérieures). Nous allons identifier dans ce guide si vous devez utiliser une build Insider Preview ; si elle n’est pas spécifiée, la version minimale requise pour une protection et des performances optimales est Windows 10 1607.

## <a name="set-up-a-dedicated-vdi-file-share"></a>Configurer un partage de fichiers VDI dédié

Dans Windows 10, version 1903, nous avons introduit la fonctionnalité d’intelligence de sécurité partagée, qui décharge le déballage des mises à jour de renseignement de sécurité téléchargées sur un ordinateur hôte, ce qui permet d’enregistrer les ressources précédentes de processeur, de disque et de mémoire sur des ordinateurs individuels. Cette fonctionnalité a été rétroportée et fonctionne désormais dans Windows 10 version 1703 et ultérieure. Vous pouvez définir cette fonctionnalité avec un stratégie de groupe ou PowerShell.

### <a name="use-group-policy-to-enable-the-shared-security-intelligence-feature"></a>Utilisez stratégie de groupe pour activer la fonctionnalité d’intelligence de sécurité partagée :

1. Sur votre ordinateur de gestion stratégie de groupe, ouvrez la console de gestion stratégie de groupe, cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Cliquez sur **Modèles d’administration**.

4. Développez l’arborescence sur **les composants Windows de** \> **l’antivirus** \> Microsoft Defender **Mises à jour**.

5. Double-cliquez sur **Définir l’emplacement du renseignement de sécurité pour les clients VDI**, puis définissez l’option **sur Activé**. Un champ s’affiche automatiquement.

6. Entrez `\\<sharedlocation\>\wdav-update` (pour obtenir de l’aide sur cette valeur, consultez [Télécharger et décompresser](#download-and-unpackage-the-latest-updates)).

7. Cliquez sur **OK**.

8. Déployez l’objet de stratégie de groupe sur les machines virtuelles que vous souhaitez tester.

### <a name="use-powershell-to-enable-the-shared-security-intelligence-feature"></a>Utiliser PowerShell pour activer la fonctionnalité d’intelligence de sécurité partagée

Utilisez l’applet de commande suivante pour activer la fonctionnalité. Vous devez ensuite envoyer (push) cette stratégie, car vous envoyez normalement des stratégies de configuration basées sur PowerShell sur les machines virtuelles :

```PowerShell
Set-MpPreference -SharedSignaturesPath \\<shared location>\wdav-update
```

Consultez la section [Télécharger et décompresser](#download-and-unpackage-the-latest-updates) pour savoir ce qu’il \<shared location\> sera.

## <a name="download-and-unpackage-the-latest-updates"></a>Télécharger et décompresser les dernières mises à jour

Vous pouvez maintenant commencer à télécharger et installer de nouvelles mises à jour. Nous avons créé un exemple de script PowerShell pour vous ci-dessous. Ce script est le moyen le plus simple de télécharger de nouvelles mises à jour et de les préparer pour vos machines virtuelles. Vous devez ensuite définir le script à exécuter à un moment donné sur l’ordinateur de gestion à l’aide d’une tâche planifiée (ou, si vous êtes familiarisé avec l’utilisation de scripts PowerShell dans Azure, Intune ou SCCM, vous pouvez également utiliser ces scripts).

```PowerShell
$vdmpathbase = "$env:systemdrive\wdav-update\{00000000-0000-0000-0000-"
$vdmpathtime = Get-Date -format "yMMddHHmmss"
$vdmpath = $vdmpathbase + $vdmpathtime + '}'
$vdmpackage = $vdmpath + '\mpam-fe.exe'

New-Item -ItemType Directory -Force -Path $vdmpath | Out-Null

Invoke-WebRequest -Uri 'https://go.microsoft.com/fwlink/?LinkID=121721&arch=x64' -OutFile $vdmpackage

cmd /c "cd /d $vdmpath & mpam-fe.exe /x"
```

Vous pouvez définir une tâche planifiée à exécuter une fois par jour afin que chaque fois que le package est téléchargé et décompressé, les machines virtuelles reçoivent la nouvelle mise à jour.
Nous vous suggérons de commencer par une fois par jour, mais vous devez essayer d’augmenter ou de diminuer la fréquence pour comprendre l’impact.

Les packages de renseignement de sécurité sont généralement publiés toutes les trois à quatre heures. La définition d’une fréquence inférieure à quatre heures n’est pas recommandée, car elle augmente la surcharge réseau sur votre ordinateur de gestion sans aucun avantage.

Vous pouvez également configurer votre serveur ou ordinateur unique pour récupérer les mises à jour pour le compte des machines virtuelles à un intervalle et les placer dans le partage de fichiers à des fins de consommation.
Cela est possible lorsque les appareils disposent des autorisations de partage et NTFS pour l’accès en lecture au partage afin qu’ils puissent récupérer les mises à jour. Pour cela :

 1. Créez un partage de fichiers SMB/CIFS. 
 
 2. Utilisez l’exemple suivant pour créer un partage de fichiers avec les autorisations de partage suivantes.

    ```PowerShell
    PS c:\> Get-SmbShareAccess -Name mdatp$

    Name   ScopeName AccountName AccessControlType AccessRight
    ----   --------- ----------- ----------------- -----------
    mdatp$ *         Everyone    Allow             Read
    ```
   
    > [!NOTE]
    > Une autorisation NTFS est ajoutée pour **les utilisateurs authentifiés :Read:**. 

    Pour cet exemple, le partage de fichiers est le suivant :

    `\\fileserver.fqdn\mdatp$\wdav-update`

### <a name="set-a-scheduled-task-to-run-the-powershell-script"></a>Définir une tâche planifiée pour exécuter le script PowerShell

1. Sur l’ordinateur de gestion, ouvrez le menu Démarrer et tapez **Planificateur de tâches**. Ouvrez-la et **sélectionnez Créer une tâche...** dans le panneau latéral.

2. Entrez le nom de **décompresseur Security Intelligence**. Accédez à l’onglet **Déclencheur** . Sélectionnez **Nouveau...** \> **Tous les jours**, puis sélectionnez **OK**.

3. Accédez à l’onglet **Actions** . Sélectionnez **Nouveau...** Entrez **PowerShell** dans le champ **Programme/Script** . Entrez `-ExecutionPolicy Bypass c:\wdav-update\vdmdlunpack.ps1` le champ **Ajouter des arguments** . Sélectionnez **OK**.

4. Vous pouvez choisir de configurer des paramètres supplémentaires si vous le souhaitez.

5. Sélectionnez **OK** pour enregistrer la tâche planifiée.

Vous pouvez lancer la mise à jour manuellement en cliquant avec le bouton droit sur la tâche et en cliquant sur **Exécuter**.

### <a name="download-and-unpackage-manually"></a>Télécharger et décompresser manuellement

Si vous préférez tout faire manuellement, voici ce qu’il faut faire pour répliquer le comportement du script :

1. Créez un dossier à la racine du système appelé `wdav_update` pour stocker les mises à jour d’intelligence, par exemple, créez le dossier `c:\wdav_update`.

2. Créer un sous-dossier sous *wdav_update* avec un nom GUID, tel que `{00000000-0000-0000-0000-000000000000}`

   Voici un exemple : `c:\wdav_update\{00000000-0000-0000-0000-000000000000}`

   > [!NOTE]
   > Dans le script, nous le définissons de sorte que les 12 derniers chiffres du GUID correspondent à l’année, au mois, au jour et à l’heure de téléchargement du fichier afin qu’un nouveau dossier soit créé à chaque fois. Vous pouvez modifier ce paramètre afin que le fichier soit téléchargé dans le même dossier à chaque fois.

3. Téléchargez un package security intelligence à partir du [https://www.microsoft.com/wdsi/definitions](https://www.microsoft.com/wdsi/definitions)  dossier GUID. Le fichier doit être nommé `mpam-fe.exe`.

4. Ouvrez une fenêtre d’invite de commandes et accédez au dossier GUID que vous avez créé. Utilisez la commande d’extraction **/X** pour extraire les fichiers, par exemple `mpam-fe.exe /X`.

   > [!NOTE]
   > Les machines virtuelles récupèrent le package mis à jour chaque fois qu’un nouveau dossier GUID est créé avec un package de mise à jour extrait ou chaque fois qu’un dossier existant est mis à jour avec un nouveau package extrait.

## <a name="randomize-scheduled-scans"></a>Analyses aléatoires planifiées

Les analyses planifiées s’exécutent en plus de la [protection et de l’analyse en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md).

L’heure de début de l’analyse elle-même est toujours basée sur la stratégie d’analyse planifiée (**ScheduleDay**, **ScheduleTime** et **ScheduleQuickScanTime**). La randomisation entraîne le démarrage d’une analyse par l’Antivirus Microsoft Defender sur chaque ordinateur dans une fenêtre de quatre heures à partir de l’heure définie pour l’analyse planifiée.

Consultez [Les analyses de planification](scheduled-catch-up-scans-microsoft-defender-antivirus.md) pour obtenir d’autres options de configuration disponibles pour les analyses planifiées.

## <a name="use-quick-scans"></a>Utiliser des analyses rapides

Vous pouvez spécifier le type d’analyse qui doit être effectué lors d’une analyse planifiée. Les analyses rapides sont l’approche par défaut, car elles sont conçues pour être actives dans tous les endroits où les programmes malveillants doivent résider. La procédure suivante décrit comment configurer des analyses rapides à l’aide de stratégie de groupe.

1. Dans votre éditeur stratégie de groupe, accédez aux **modèles d’administration composants** \> \> **Windows** Analyse **antivirus** \> Microsoft Defender.

2. Sélectionnez **Spécifier le type d’analyse à utiliser pour une analyse planifiée** , puis modifiez le paramètre de stratégie.

3. Définissez la stratégie **sur Activé**, puis sous **Options**, sélectionnez  **Analyse rapide**.

4. Sélectionnez **OK**.

5. Déployez votre objet de stratégie de groupe comme vous le faites habituellement.

## <a name="prevent-notifications"></a>Empêcher les notifications

Parfois, les notifications de l’Antivirus Microsoft Defender peuvent être envoyées ou conservées sur plusieurs sessions. Pour réduire ce problème, vous pouvez verrouiller l’interface utilisateur de l’Antivirus Microsoft Defender. La procédure suivante décrit comment supprimer des notifications avec stratégie de groupe.

1. Dans votre éditeur stratégie de groupe, accédez à **l’interface cliente** de l’antivirus \> **Microsoft Defender** des **composants** \> Windows.

2. Sélectionnez **Supprimer toutes les notifications** , puis modifiez les paramètres de stratégie.

3. Définissez la stratégie **sur Activé**, puis sélectionnez **OK**.

4. Déployez votre objet de stratégie de groupe comme vous le faites habituellement.

La suppression des notifications empêche l’affichage des notifications de l’Antivirus Microsoft Defender dans le Centre d’actions sur Windows 10 lorsque des analyses sont effectuées ou que des actions de correction sont effectuées. Toutefois, votre équipe chargée des opérations de sécurité verra les résultats de l’analyse pendant que l’attaque a été détectée et arrêtée ; Les alertes, telles qu’une « alerte d’accès initial », sont déclenchées et apparaissent dans le [portail Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Pour ouvrir le Centre d’actions sur Windows 10 ou Windows 11, effectuez l’une des étapes suivantes :
> - À l’extrémité droite de la barre des tâches, sélectionnez l’icône Centre d’actions.
> - Appuyez sur le bouton touche de logo Windows + A.
> - Sur un appareil à écran tactile, balayez à partir du bord droit de l’écran.

## <a name="disable-scans-after-an-update"></a>Désactiver les analyses après une mise à jour

La désactivation d’une analyse après une mise à jour empêche l’analyse de se produire après la réception d’une mise à jour. Vous pouvez appliquer ce paramètre lors de la création de l’image de base si vous avez également exécuté une analyse rapide. De cette façon, vous pouvez empêcher la machine virtuelle nouvellement mise à jour d’effectuer une nouvelle analyse (comme vous l’avez déjà analysée lors de la création de l’image de base).

> [!IMPORTANT]
> L’exécution d’analyses après une mise à jour permet de s’assurer que vos machines virtuelles sont protégées par les dernières mises à jour du renseignement de sécurité. La désactivation de cette option réduit le niveau de protection de vos machines virtuelles et ne doit être utilisée que lors de la création ou du déploiement de l’image de base.

1. Dans votre éditeur stratégie de groupe, accédez aux **composants** \> Windows microsoft **Defender Antivirus** \> **Security Intelligence Mises à jour**.

2. Sélectionnez **Activer l’analyse après la mise à jour du renseignement de sécurité** , puis modifiez le paramètre de stratégie.

3. Définissez la stratégie sur **Désactivé**.

4. Sélectionnez **OK**.

5. Déployez votre objet de stratégie de groupe comme vous le faites habituellement.

Cette stratégie empêche l’exécution d’une analyse immédiatement après une mise à jour.

## <a name="disable-the-scanonlyifidle-option"></a>Désactiver l’option `ScanOnlyIfIdle`

Utilisez l’applet de commande suivante pour arrêter une analyse rapide ou planifiée chaque fois que l’appareil est inactif s’il est en mode passif.

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled $false
```

Vous pouvez également désactiver l’option dans l’Antivirus `ScanOnlyIfIdle` Microsoft Defender par configuration via une stratégie de groupe de domaine ou locale. Cela empêche la contention importante de l’UC dans les environnements à haute densité.

Pour plus d’informations, consultez [Démarrer l’analyse planifiée uniquement lorsque l’ordinateur est activé, mais qu’il n’est pas utilisé](https://admx.help/?Category=SystemCenterEndpointProtection&Policy=Microsoft.Policies.Antimalware::scan_scanonlyifidle).

## <a name="scan-vms-that-have-been-offline"></a>Analyser les machines virtuelles qui ont été hors connexion

1. Dans votre éditeur stratégie de groupe, accédez à **l’analyse** antivirus \> **Microsoft Defender** **des composants** \> Windows.

2. Sélectionnez **Activer l’analyse rapide de rattrapage** , puis modifiez le paramètre de stratégie.

3. Définissez la stratégie **sur Activé**.

4. Sélectionnez **OK**.

5. Déployez votre objet stratégie de groupe comme d’habitude.

Cette stratégie force une analyse si la machine virtuelle a manqué au moins deux analyses planifiées consécutives.

## <a name="enable-headless-ui-mode"></a>Activer le mode d’interface utilisateur sans tête

1. Dans votre éditeur stratégie de groupe, accédez à **l’interface cliente** de l’antivirus \> **Microsoft Defender** des **composants** \> Windows.

2. Sélectionnez **Activer le mode d’interface utilisateur sans tête** et modifiez la stratégie.

3. Définissez la stratégie **sur Activé**.

4. Cliquez sur **OK**.

5. Déployez votre objet stratégie de groupe comme d’habitude.

Cette stratégie masque l’intégralité de l’interface utilisateur de l’Antivirus Microsoft Defender aux utilisateurs finaux de votre organisation.

## <a name="exclusions"></a>Exclusions

Les exclusions peuvent être ajoutées, supprimées ou personnalisées en fonction de vos besoins.

Pour plus d’informations, consultez [Configurer les exclusions de l’antivirus Microsoft Defender sur Windows Server](configure-exclusions-microsoft-defender-antivirus.md).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="additional-resources"></a>Ressources supplémentaires

- [Blog de la communauté technique : Configuration de l’antivirus Microsoft Defender pour les machines VDI non persistantes](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/configuring-microsoft-defender-antivirus-for-non-persistent-vdi/ba-p/1489633)
- [Forums TechNet sur les services Bureau à distance et VDI](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)
- [Script PowerShell SignatureDownloadCustomTask](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4)
