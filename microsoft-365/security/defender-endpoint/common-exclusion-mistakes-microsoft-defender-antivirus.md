---
title: Erreurs courantes à éviter lors de la définition d’exclusions
description: Évitez les erreurs courantes lors de la définition d’exclusions pour les analyses Antivirus Microsoft Defender.
keywords: exclusions, fichiers, extension, type de fichier, nom de dossier, nom de fichier, analyses
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 10/19/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 23c079f8f845e6116bc39b9edb3fb186883ef576
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418223"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>Erreurs courantes à éviter lors de la définition d’exclusions

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender 

**Plateformes**
- Windows
- macOS
- Linux

Vous pouvez définir une liste d’exclusion pour les éléments que vous ne souhaitez pas Antivirus Microsoft Defender analyser. Ces éléments exclus peuvent contenir des menaces qui rendent votre appareil vulnérable. Cet article décrit une erreur courante que vous devez éviter lors de la définition d’exclusions.

Avant de définir vos listes d’exclusions, consultez [Recommandations pour définir des exclusions](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

## <a name="excluding-certain-trusted-items"></a>Exclusion de certains éléments approuvés

Certains fichiers, types de fichiers, dossiers ou processus ne doivent pas être exclus de l’analyse même si vous pensez qu’ils ne sont pas malveillants.

Ne définissez pas d’exclusions pour les emplacements de dossier, les extensions de fichier et les processus répertoriés dans les sections suivantes :
- Emplacements des dossiers
- Extensions de fichier
- Processus

### <a name="folder-locations"></a>Emplacements des dossiers

En général, ne définissez pas d’exclusions pour les emplacements de dossier suivants :

`%systemdrive%`

`C:`

`C:\`

`C:\*`

`%ProgramFiles%\Java`

`C:\Program Files\Java`

`%ProgramFiles%\Contoso\`

`C:\Program Files\Contoso\`

`%ProgramFiles(x86)%\Contoso\`

`C:\Program Files (x86)\Contoso\`

`C:\Temp`

`C:\Temp\`

`C:\Temp\*`

`C:\Users\`

`C:\Users\*`

`C:\Users\<UserProfileName>\AppData\Local\Temp\`**Notez l’exception suivante pour SharePoint** : Excluez `C:\Users\ServiceAccount\AppData\Local\Temp` lorsque vous utilisez la [protection antivirus au niveau des fichiers dans SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

`C:\Users\<UserProfileName>\AppData\LocalLow\Temp\`**Notez l’exception suivante pour SharePoint** : Excluez `C:\Users\Default\AppData\Local\Temp` lorsque vous utilisez la [protection antivirus au niveau des fichiers dans SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

`%Windir%\Prefetch`

`C:\Windows\Prefetch`

`C:\Windows\Prefetch\`

`C:\Windows\Prefetch\*`

`%Windir%\System32\Spool`

`C:\Windows\System32\Spool`

`C:\Windows\System32\CatRoot2`
`%Windir%\Temp`

`C:\Windows\Temp`

`C:\Windows\Temp\`

`C:\Windows\Temp\*`

#### <a name="linux-and-macos-platforms"></a>Plateformes Linux et macOS

`/`

`/bin`

`/sbin`

`/usr/lib`


### <a name="file-extensions"></a>Extensions de fichier

En général, ne définissez pas d’exclusions pour les extensions de fichier suivantes :

`.7z`

`.bat`

`.bin`

`.cab`

`.cmd`

`.com`

`.cpl`

`.dll`

`.exe`

`.fla`

`.gif`

`.gz`

`.hta`

`.inf`

`.java`

`.jar`

`.job`

`.jpeg`

`.jpg`

`.js`

`.ko`

`.ko.gz`

`.msi`

`.ocx`

`.png`

`.ps1`

`.py`

`.rar`

`.reg`

`.scr`

`.sys`

`.tar`

`.tmp`

`.url`

`.vbe`

`.vbs`

`.wsf`

`.zip`

### <a name="processes"></a>Processus

En général, ne définissez pas d’exclusions pour les processus suivants :

`AcroRd32.exe`

`bitsadmin.exe`

`excel.exe`

`iexplore.exe`

`java.exe`

`outlook.exe`

`psexec.exe`

`powerpnt.exe`

`powershell.exe`

`schtasks.exe`

`svchost.exe`

`wmic.exe`

`winword.exe`

`wuauclt.exe`

`addinprocess.exe`

`addinprocess32.exe`

`addinutil.exe`

`bash.exe`

`bginfo.exe`

`cdb.exe`

`csi.exe`

`dbghost.exe`

`dbgsvc.exe`

`dnx.exe`

`dotnet.exe`

`fsi.exe`

`fsiAnyCpu.exe`

`kd.exe`

`ntkd.exe`

`lxssmanager.dll`

`msbuild.exe`

`mshta.exe`

`ntsd.exe`

`rcsi.exe`

`system.management.automation.dll`

`windbg.exe`

#### <a name="linux-and-macos-platforms"></a>Plateformes Linux et macOS

`bash`

`sh`

`python` et `python3`

`java`

`zsh`

> [!NOTE]
> Vous pouvez choisir d’exclure des types de fichiers, tels que `.gif`, `.jpg`, `.jpeg`ou `.png` si votre environnement dispose d’un logiciel moderne et à jour avec une stratégie de mise à jour stricte pour gérer les vulnérabilités.

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>Utilisation uniquement du nom de fichier dans la liste d’exclusions

Les programmes malveillants peuvent avoir le même nom que celui d’un fichier approuvé et que vous souhaitez exclure de l’analyse. Par conséquent, pour éviter d’exclure les programmes malveillants potentiels de l’analyse, utilisez un chemin d’accès complet au fichier que vous souhaitez exclure au lieu d’utiliser uniquement le nom du fichier. Par exemple, si vous souhaitez exclure `Filename.exe` de l’analyse, utilisez le chemin d’accès complet au fichier, par `C:\program files\contoso\Filename.exe`exemple .

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>Utilisation d’une liste d’exclusion unique pour plusieurs charges de travail de serveur

N’utilisez pas une seule liste d’exclusions pour définir des exclusions pour plusieurs charges de travail de serveur. Fractionnez les exclusions pour différentes charges de travail d’application ou de service en plusieurs listes d’exclusions. Par exemple, la liste d’exclusions pour votre charge de travail IIS Server doit être différente de la liste d’exclusions de votre charge de travail SQL Server.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Utilisation de variables d’environnement incorrectes comme caractères génériques dans les listes d’exclusions de nom de fichier et de dossier ou d’extension

Antivirus Microsoft Defender service s’exécute dans le contexte système à l’aide du compte LocalSystem, ce qui signifie qu’il obtient des informations à partir de la variable d’environnement système, et non de la variable d’environnement utilisateur. L’utilisation de variables d’environnement comme caractère générique dans les listes d’exclusion est limitée aux variables système et à celles applicables aux processus s’exécutant en tant que compte NT AUTHORITY\SYSTEM. Par conséquent, n’utilisez pas les variables d’environnement utilisateur comme caractères génériques lors de l’ajout de Antivirus Microsoft Defender dossier et d’exclusions de processus. Consultez le tableau sous [Variables d’environnement système](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) pour obtenir la liste complète des variables d’environnement système.

Pour plus d’informations sur [l’utilisation des caractères génériques dans les listes d’exclusions de nom de fichier et de dossier ou d’extension](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) , voir Utiliser des caractères génériques dans les listes d’exclusions.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
