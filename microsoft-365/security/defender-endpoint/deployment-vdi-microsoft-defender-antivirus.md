---
title: Antivirus Microsoft Defender Guide de déploiement de l’infrastructure de bureau virtuel
description: Découvrez comment déployer des Antivirus Microsoft Defender dans un environnement de bureau virtuel pour un meilleur équilibre entre la protection et les performances.
keywords: vdi, hyper-v, vm, machine virtuelle, windows defender, antivirus, av, bureau virtuel, rds, bureau à distance
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: normal
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 06/11/2021
ms.reviewer: jesquive
manager: dansimp
ms.technology: mde
ms.openlocfilehash: cbf1cae088af2606e8fea1e40e0cfe34c7a74832
ms.sourcegitcommit: 6c342a956b2dbc32be33bac1a23a5038490f1b40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58533518"
---
# <a name="deployment-guide-for-microsoft-defender-antivirus-in-a-virtual-desktop-infrastructure-vdi-environment"></a>Guide de déploiement de l’antivirus Microsoft Defender dans un environnement VDI (Virtual Desktop Infrastructure)

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Outre les configurations matérielles ou locales standard, vous pouvez également utiliser Antivirus Microsoft Defender dans un environnement bureau à distance (RDS) ou vDI (Virtual Desktop Infrastructure).

Voir [Windows virtual desktop documentation](/azure/virtual-desktop) for more details on Bureau à distance Microsoft Services and VDI support.

Pour les machines virtuelles basées sur Azure, voir [Installer Endpoint Protection dans Azure Defender.](/azure/security-center/security-center-install-endpoint-protection)

Avec la possibilité de déployer facilement des mises à jour sur des ordinateurs VM en cours d’exécution dans des VDIs, nous avons raccourci ce guide pour vous concentrer sur la façon dont vous pouvez obtenir des mises à jour sur vos ordinateurs rapidement et facilement. Vous n’avez plus besoin de créer et de sceller régulièrement des images d’or, car les mises à jour sont étendues dans leurs bits de composant sur le serveur hôte, puis téléchargées directement sur la VM lorsqu’elle est allumée.

Ce guide décrit comment configurer vos VM pour une protection et des performances optimales, notamment comment :

- [Configurer un partage de fichiers VDI dédié pour les mises à jour de l’intelligence de la sécurité](#set-up-a-dedicated-vdi-file-share)
- [Randomiser les analyses programmées](#randomize-scheduled-scans)
- [Utiliser des analyses rapides](#use-quick-scans)
- [Empêcher les notifications](#prevent-notifications)
- [Désactiver l’analyse après chaque mise à jour](#disable-scans-after-an-update)
- [Analyser les ordinateurs ou ordinateurs hors connexion depuis un certain temps](#scan-vms-that-have-been-offline)
- [Appliquer des exclusions](#exclusions)

Vous pouvez également télécharger le Antivirus Microsoft Defender de livre blanc sur [l’infrastructure](https://demo.wd.microsoft.com/Content/wdav-testing-vdi-ssu.pdf)de bureau virtuel, qui examine la nouvelle fonctionnalité de mise à jour de l’intelligence de sécurité partagée, ainsi que des tests de performances et des conseils sur la façon de tester les performances de l’antivirus sur votre propre environnement VDI.

> [!IMPORTANT]
> Bien que l’environnement VDI puisse être hébergé sur Windows Server 2012 ou Windows Server 2016, les machines virtuelles doivent au minimum être en Windows 10, 1607, en raison de l’augmentation des technologies et des fonctionnalités de protection qui ne sont pas disponibles dans les versions antérieures de Windows.
>
> Il existe des améliorations en matière de performances et de fonctionnalités dans le fonctionnement de Microsoft Defender AV sur des machines virtuelles dans Windows 10 Insider Preview, build 18323 (et version ultérieure). Nous identifierons dans ce guide si vous devez utiliser une build Insider Preview ; Si elle n’est pas spécifiée, la version minimale requise pour une protection et des performances Windows 10 1607.

## <a name="set-up-a-dedicated-vdi-file-share"></a>Configurer un partage de fichiers VDI dédié

Dans Windows 10, version 1903, nous avons introduit la fonctionnalité d’intelligence de sécurité partagée, qui décharge le déballage des mises à jour d’informations de sécurité téléchargées sur un ordinateur hôte, ce qui permet d’enregistrer les ressources précédentes de l’UC, du disque et de la mémoire sur des ordinateurs individuels. Cette fonctionnalité a été backportée et fonctionne désormais dans Windows 10 version 1703 et versions supérieures. Vous pouvez définir cette fonctionnalité avec une stratégie de groupe ou PowerShell.

### <a name="use-group-policy-to-enable-the-shared-security-intelligence-feature"></a>Utilisez la stratégie de groupe pour activer la fonctionnalité d’intelligence de sécurité partagée :

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la Console de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

3. Cliquez **sur Modèles d’administration.**

4. Développez l’arborescence **Windows composants Antivirus Microsoft Defender** \>  \> **security intelligence updates**.

5. Double-cliquez sur **Définir l’emplacement d’intelligence** de sécurité pour les clients VDI, puis définissez l’option **sur Activé.** Un champ s’affiche automatiquement.

6. Entrez `\\<sharedlocation\>\wdav-update` (pour obtenir de l’aide sur cette valeur, voir [Télécharger et décompresser).](#download-and-unpackage-the-latest-updates)

7. Cliquez sur **OK**.

8. Déployez l’GPO sur les VM que vous souhaitez tester.

### <a name="use-powershell-to-enable-the-shared-security-intelligence-feature"></a>Utiliser PowerShell pour activer la fonctionnalité d’intelligence de sécurité partagée

Utilisez l’cmdlet suivante pour activer la fonctionnalité. Vous devez ensuite la pousser comme vous le feriez normalement pour les stratégies de configuration basées sur PowerShell sur les ordinateurs VM :

```PowerShell
Set-MpPreference -SharedSignaturesPath \\<shared location>\wdav-update
```

Consultez la section [Télécharger et décompresser](#download-and-unpackage-the-latest-updates) pour savoir ce \<shared location\> qui sera.

## <a name="download-and-unpackage-the-latest-updates"></a>Télécharger et décompresser les dernières mises à jour

Vous pouvez maintenant commencer à télécharger et installer de nouvelles mises à jour. Nous avons créé un exemple de script PowerShell ci-dessous. Ce script est le moyen le plus simple de télécharger de nouvelles mises à jour et de les préparer pour vos VM. Vous devez ensuite définir le script pour qu’il s’exécute à un moment donné sur l’ordinateur de gestion à l’aide d’une tâche programmée (ou, si vous êtes familiarisé avec l’utilisation de scripts PowerShell dans Azure, Intune ou SCCM, vous pouvez également utiliser ces scripts).

```PowerShell
$vdmpathbase = "$env:systemdrive\wdav-update\{00000000-0000-0000-0000-"
$vdmpathtime = Get-Date -format "yMMddHHmmss"
$vdmpath = $vdmpathbase + $vdmpathtime + '}'
$vdmpackage = $vdmpath + '\mpam-fe.exe'

New-Item -ItemType Directory -Force -Path $vdmpath | Out-Null

Invoke-WebRequest -Uri 'https://go.microsoft.com/fwlink/?LinkID=121721&arch=x64' -OutFile $vdmpackage

cmd /c "cd $vdmpath & c: & mpam-fe.exe /x"
```

Vous pouvez définir une tâche programmée de sorte qu’elle s’exécute une fois par jour de sorte que chaque fois que le package est téléchargé et décompressé, les VM reçoivent la nouvelle mise à jour.
Nous vous suggérons de commencer une fois par jour, mais vous devez essayer d’augmenter ou de réduire la fréquence pour en comprendre l’impact.

Les packages d’informations de sécurité sont généralement publiés toutes les trois à quatre heures. Il n’est pas conseillé de définir une fréquence de moins de quatre heures, car cela augmente la surcharge réseau sur votre ordinateur de gestion sans aucun avantage.

### <a name="set-a-scheduled-task-to-run-the-powershell-script"></a>Définir une tâche programmée pour exécuter le script PowerShell

1. Sur l’ordinateur de gestion, ouvrez le menu Démarrer et tapez **Le Programmeur de tâches.** Ouvrez-le et **sélectionnez Créer une tâche...** sur le panneau latéral.

2. Entrez le nom en **tant que décompresseur security intelligence**. Go to the **Trigger** tab. Select **New...** \> **Tous les** jours, puis sélectionnez **OK.**

3. Go to the **Actions** tab. Select **New...** Entrez **PowerShell dans** le **champ Programme/Script.** Entrez `-ExecutionPolicy Bypass c:\wdav-update\vdmdlunpack.ps1` le champ Ajouter des **arguments.** Sélectionnez **OK**.

4. Vous pouvez choisir de configurer des paramètres supplémentaires si vous le souhaitez.

5. Sélectionnez **OK** pour enregistrer la tâche programmée.

Vous pouvez lancer la mise à jour manuellement en cliquant avec le bouton droit sur la tâche et en cliquant sur **Exécuter.**

### <a name="download-and-unpackage-manually"></a>Télécharger et décompresser manuellement

Si vous préférez tout faire manuellement, voici comment répliquer le comportement du script :

1. Créez un dossier à la racine du système appelé pour stocker les mises à jour d’intelligence, par `wdav_update` exemple, créez le `c:\wdav_update` dossier.

2. Créez un *sous-wdav_update* sous un nom GUID, par exemple `{00000000-0000-0000-0000-000000000000}`

   Voici un exemple : `c:\wdav_update\{00000000-0000-0000-0000-000000000000}`

   > [!NOTE]
   > Dans le script, nous l’avons définie de sorte que les 12 derniers chiffres du GUID soient l’année, le mois, le jour et l’heure de téléchargement du fichier afin qu’un nouveau dossier soit créé à chaque fois. Vous pouvez modifier cela afin que le fichier soit téléchargé dans le même dossier à chaque fois.

3. Téléchargez un package d’informations de sécurité [https://www.microsoft.com/wdsi/definitions](https://www.microsoft.com/wdsi/definitions)  à partir du dossier GUID. Le fichier doit être nommé `mpam-fe.exe` .

4. Ouvrez une fenêtre d’invite de cmd et accédez au dossier GUID que vous avez créé. Utilisez la **commande d’extraction /X** pour extraire les fichiers, par `mpam-fe.exe /X` exemple.

   > [!NOTE]
   > Les VMs sélectionnent le package mis à jour chaque fois qu’un nouveau dossier GUID est créé avec un package de mise à jour extrait ou chaque fois qu’un dossier existant est mis à jour avec un nouveau package extrait.

## <a name="randomize-scheduled-scans"></a>Randomiser les analyses programmées

Les analyses programmées s’exécutent en plus de la protection et de [l’analyse en temps réel.](configure-real-time-protection-microsoft-defender-antivirus.md)

L’heure de début de l’analyse elle-même est toujours basée sur la stratégie d’analyse programmée (**ScheduleDay**, **ScheduleTime** et **ScheduleQuickScanTime**). La randomisation entraîne Antivirus Microsoft Defender démarrer une analyse sur chaque ordinateur dans une fenêtre de 4 heures à partir de l’heure définie pour l’analyse programmée.

Voir [Analyses de planification pour](scheduled-catch-up-scans-microsoft-defender-antivirus.md) les autres options de configuration disponibles pour les analyses programmées.

## <a name="use-quick-scans"></a>Utiliser des analyses rapides

Vous pouvez spécifier le type d’analyse à effectuer lors d’une analyse programmée. Les analyses rapides sont l’approche préférée, car elles sont conçues pour rechercher tous les endroits où les programmes malveillants doivent résider pour être actifs. La procédure suivante décrit comment configurer des analyses rapides à l’aide de la stratégie de groupe.

1. Dans votre Éditeur de stratégie de groupe, allez aux **modèles** \> **d’administration Windows composants** \> **Antivirus Microsoft Defender** \> **Scan**.

2. Sélectionnez **Spécifier le type d’analyse à utiliser pour une analyse** programmée, puis modifiez le paramètre de stratégie.

3. Définissez la stratégie **sur Activé,** puis sous **Options,** sélectionnez **Analyse rapide.**

4. Sélectionnez **OK**.

5. Déployez votre objet de stratégie de groupe comme vous le faites habituellement.

## <a name="prevent-notifications"></a>Empêcher les notifications

Parfois, Antivirus Microsoft Defender notifications peuvent être envoyées à plusieurs sessions ou être persistantes. Pour minimiser ce problème, vous pouvez verrouiller l’interface Antivirus Microsoft Defender’utilisateur. La procédure suivante décrit comment supprimer les notifications avec la stratégie de groupe.

1. Dans votre Éditeur de stratégie de groupe, Windows **composants** \> **Antivirus Microsoft Defender** \> **interface client.**

2. Sélectionnez **Supprimer toutes les notifications,** puis modifiez les paramètres de stratégie.

3. Définissez la stratégie **sur Activé,** puis sélectionnez **OK.**

4. Déployez votre objet de stratégie de groupe comme vous le faites habituellement.

La suppression des notifications empêche les notifications d’Antivirus Microsoft Defender de s’afficher dans le centre de notifications sur Windows 10 lorsque des analyses sont réalisées ou que des actions de correction sont prises. Toutefois, votre équipe des opérations de sécurité verra les résultats de l’analyse dans [le portail Microsoft 365 Defender.](microsoft-defender-security-center.md)

> [!TIP]
> Pour ouvrir le Centre de Windows 10, prenez l’une des étapes suivantes :
>
> - À l’extrémité droite de la barre des tâches, sélectionnez l’icône centre de travail.
> - Appuyez sur Windows touche de logo + A.
> - Sur un appareil tactile, effectuez un balayage à partir du bord droit de l’écran.

## <a name="disable-scans-after-an-update"></a>Désactiver les analyses après une mise à jour

La désactivation d’une analyse après une mise à jour empêche l’analyse de se produire après la réception d’une mise à jour. Vous pouvez appliquer ce paramètre lors de la création de l’image de base si vous avez également exécuté une analyse rapide. De cette façon, vous pouvez empêcher la nouvelle mise à jour de la VM d’effectuer à nouveau une analyse (comme vous l’avez déjà analysé lors de la création de l’image de base).

> [!IMPORTANT]
> L’exécution d’analyses après une mise à jour permet de s’assurer que vos VM sont protégées avec les dernières mises à jour d’intelligence de sécurité. La désactivation de cette option réduit le niveau de protection de vos VM et ne doit être utilisée que lors de la création ou du déploiement de l’image de base.

1. Dans votre Éditeur de stratégie de groupe, Windows **composants** Antivirus Microsoft Defender mises à jour \>  \> **security intelligence**.

2. Sélectionnez **Activer l’analyse après la mise** à jour des informations de sécurité, puis modifiez le paramètre de stratégie.

3. Définissez la stratégie sur **Désactivé.**

4. Sélectionnez **OK**.

5. Déployez votre objet de stratégie de groupe comme vous le faites habituellement.

Cette stratégie empêche l’exécution d’une analyse immédiatement après une mise à jour.

## <a name="scan-vms-that-have-been-offline"></a>Analyser les ordinateurs VM qui ont été hors connexion

1. Dans votre Éditeur de stratégie de groupe, Windows **composants** \> **Antivirus Microsoft Defender** \> **Scan**.

2. Sélectionnez **Activer l’analyse rapide de rattrapage,** puis modifiez le paramètre de stratégie.

3. Définissez la stratégie **sur Activé.**

4. Sélectionnez **OK**.

5. Déployez votre objet de stratégie de groupe comme vous le faites généralement.

Cette stratégie force une analyse si la VM a manqué au moins deux analyses programmées consécutives.

## <a name="enable-headless-ui-mode"></a>Activer le mode d’interface utilisateur sans en-tête

1. Dans votre Éditeur de stratégie de groupe, Windows **composants** \> **Antivirus Microsoft Defender** \> **interface client.**

2. Sélectionnez **Activer le mode d’interface utilisateur sans tête** et modifiez la stratégie.

3. Définissez la stratégie **sur Activé.**

4. Cliquez sur **OK**.

5. Déployez votre objet de stratégie de groupe comme vous le faites généralement.

Cette stratégie masque l’intégralité Antivirus Microsoft Defender’interface utilisateur des utilisateurs finaux de votre organisation.

## <a name="exclusions"></a>Exclusions

Les exclusions peuvent être ajoutées, supprimées ou personnalisées en fonction de vos besoins.

Pour plus d’informations, [voir Configurer Antivirus Microsoft Defender exclusions sur Windows Server.](configure-exclusions-microsoft-defender-antivirus.md)

## <a name="additional-resources"></a>Ressources supplémentaires

- [Blog tech Community : Configuration de Antivirus Microsoft Defender pour les ordinateurs VDI non persistants](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/configuring-microsoft-defender-antivirus-for-non-persistent-vdi/ba-p/1489633)
- [Forums TechNet sur les services Bureau à distance et VDI](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)
- [Script PowerShell SignatureDownloadCustomTask](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4)
