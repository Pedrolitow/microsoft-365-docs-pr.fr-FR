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
ms.date: 06/16/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 99d59c2027d3b34ad5c9c19444a51dd08cc22276
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128655"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>Erreurs courantes à éviter lors de la définition d’exclusions

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender pour point de terminaison Plan 1
- Antivirus Microsoft Defender 

**Plateformes**

- Windows
- macOS
- Linux

> [!IMPORTANT]
> **Ajoutez des exclusions avec précaution**. Les exclusions pour les analyses Antivirus Microsoft Defender réduisent le niveau de protection des appareils.

Vous pouvez définir une liste d’exclusion pour les éléments que vous ne souhaitez pas Antivirus Microsoft Defender analyser. Toutefois, les éléments exclus peuvent contenir des menaces qui rendent votre appareil vulnérable. Cet article décrit certaines erreurs courantes que vous devez éviter lors de la définition d’exclusions.

Avant de définir vos listes d’exclusions, consultez [Recommandations pour définir des exclusions](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

## <a name="excluding-certain-trusted-items"></a>Exclusion de certains éléments approuvés

Certains fichiers, types de fichiers, dossiers ou processus ne doivent pas être exclus de l’analyse même si vous pensez qu’ils ne sont pas malveillants.

Ne définissez pas d’exclusions pour les emplacements de dossier, les extensions de fichier et les processus répertoriés dans les sections suivantes :

- [Emplacements des dossiers](#folder-locations)
- [Extensions de fichier](#file-extensions)
- [Processus](#processes)

### <a name="folder-locations"></a>Emplacements des dossiers

> [!IMPORTANT]
> Certains dossiers ne doivent pas être exclus des analyses, car ils finissent par être des dossiers où des fichiers malveillants peuvent être supprimés.

En général, ne définissez pas d’exclusions pour les emplacements de dossier suivants :

- `%systemdrive%`
- `C:`, `C:\`ou `C:\*`
- `%ProgramFiles%\Java` ou `C:\Program Files\Java`
- `%ProgramFiles%\Contoso\`, `C:\Program Files\Contoso\`, `%ProgramFiles(x86)%\Contoso\`ou `C:\Program Files (x86)\Contoso\`
- `C:\Temp`, `C:\Temp\`ou `C:\Temp\*`
- `C:\Users\` ou `C:\Users\*`
- `C:\Users\<UserProfileName>\AppData\Local\Temp\` ou `C:\Users\<UserProfileName>\AppData\LocalLow\Temp\`. **Notez les exceptions importantes suivantes pour SharePoint** : **excluez** `C:\Users\ServiceAccount\AppData\Local\Temp` ou `C:\Users\Default\AppData\Local\Temp` utilisez la [protection antivirus au niveau des fichiers dans SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).
- `%Windir%\Prefetch`, `C:\Windows\Prefetch`, `C:\Windows\Prefetch\`ou `C:\Windows\Prefetch\*`
- `%Windir%\System32\Spool` ou `C:\Windows\System32\Spool`
- `C:\Windows\System32\CatRoot2`
- `%Windir%\Temp`, `C:\Windows\Temp`, `C:\Windows\Temp\`ou `C:\Windows\Temp\*`

#### <a name="linux-and-macos-platforms"></a>Plateformes Linux et macOS

En général, ne définissez pas d’exclusions pour les emplacements de dossier suivants :

- `/`
- `/bin` ou `/sbin`
- `/usr/lib`

### <a name="file-extensions"></a>Extensions de fichier

> [!IMPORTANT]
> Certaines extensions de fichier ne doivent pas être exclues, car elles peuvent être des types de fichiers utilisés dans une attaque.

En général, ne définissez pas d’exclusions pour les extensions de fichier suivantes :

- `.7z`
- `.bat`
- `.bin`
- `.cab`
- `.cmd`
- `.com`
- `.cpl`
- `.dll`
- `.exe`
- `.fla`
- `.gif`
- `.gz`
- `.hta`
- `.inf`
- `.java`
- `.jar`
- `.job`
- `.jpeg`
- `.jpg`
- `.js`
- `.ko` ou `.ko.gz`
- `.msi`
- `.ocx`
- `.png`
- `.ps1`
- `.py`
- `.rar`
- `.reg`
- `.scr`
- `.sys`
- `.tar`
- `.tmp`
- `.url`
- `.vbe`
- `.vbs`
- `.wsf`
- `.zip`

### <a name="processes"></a>Processus

> [!IMPORTANT]
> Certains processus ne doivent pas être exclus, car ils sont utilisés pendant les attaques.

En général, ne définissez pas d’exclusions pour les processus suivants :

- `AcroRd32.exe`
- `addinprocess.exe`
- `addinprocess32.exe`
- `addinutil.exe`
- `bash.exe`
- `bginfo.exe`
- `bitsadmin.exe`
- `cdb.exe`
- `csi.exe`
- `dbghost.exe`
- `dbgsvc.exe`
- `dnx.exe`
- `dotnet.exe`
- `excel.exe`
- `fsi.exe`
- `fsiAnyCpu.exe`
- `iexplore.exe`
- `java.exe`
- `kd.exe`
- `lxssmanager.dll`
- `msbuild.exe`
- `mshta.exe`
- `ntkd.exe`
- `ntsd.exe`
- `outlook.exe`
- `psexec.exe`
- `powerpnt.exe`
- `powershell.exe`
- `rcsi.exe`
- `svchost.exe`
- `schtasks.exe`
- `system.management.automation.dll`
- `windbg.exe`
- `winword.exe`
- `wmic.exe`
- `wuauclt.exe`

> [!NOTE]
> Vous pouvez choisir d’exclure des types de fichiers, tels que `.gif`, `.jpg`, `.jpeg`ou `.png` si votre environnement dispose d’un logiciel moderne et à jour avec une stratégie de mise à jour stricte pour gérer les vulnérabilités.

#### <a name="linux-and-macos-platforms"></a>Plateformes Linux et macOS

En général, ne définissez pas d’exclusions pour les processus suivants :

- `bash`
- `java`
- `python` et `python3`
- `sh`
- `zsh`

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>Utilisation uniquement du nom de fichier dans la liste d’exclusions

Les programmes malveillants peuvent avoir le même nom que celui d’un fichier approuvé et que vous souhaitez exclure de l’analyse. Par conséquent, pour éviter d’exclure les programmes malveillants potentiels de l’analyse, utilisez un chemin d’accès complet au fichier que vous souhaitez exclure au lieu d’utiliser uniquement le nom du fichier. Par exemple, si vous souhaitez exclure `Filename.exe` de l’analyse, utilisez le chemin d’accès complet au fichier, par `C:\program files\contoso\Filename.exe`exemple .

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>Utilisation d’une liste d’exclusion unique pour plusieurs charges de travail de serveur

N’utilisez pas une seule liste d’exclusions pour définir des exclusions pour plusieurs charges de travail de serveur. Fractionnez les exclusions pour différentes charges de travail d’application ou de service en plusieurs listes d’exclusions. Par exemple, la liste d’exclusions pour votre charge de travail IIS Server doit être différente de la liste d’exclusions de votre charge de travail SQL Server.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Utilisation de variables d’environnement incorrectes comme caractères génériques dans les listes d’exclusions de nom de fichier et de dossier ou d’extension

Antivirus Microsoft Defender service s’exécute dans le contexte système à l’aide du compte LocalSystem, ce qui signifie qu’il obtient des informations à partir de la variable d’environnement système, et non de la variable d’environnement utilisateur. L’utilisation de variables d’environnement comme caractère générique dans les listes d’exclusion est limitée aux variables système et à celles applicables aux processus s’exécutant en tant que compte NT AUTHORITY\SYSTEM. Par conséquent, n’utilisez pas les variables d’environnement utilisateur comme caractères génériques lors de l’ajout d’exclusions de dossiers et de processus Antivirus Microsoft Defender. Consultez le tableau sous [Variables d’environnement système](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) pour obtenir la liste complète des variables d’environnement système.

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
