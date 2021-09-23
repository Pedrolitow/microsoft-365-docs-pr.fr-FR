---
title: Erreurs courantes à éviter lors de la définition d’exclusions
description: Évitez les erreurs courantes lors de la définition d’exclusions Antivirus Microsoft Defender analyses.
keywords: exclusions, fichiers, extension, type de fichier, nom de dossier, nom de fichier, analyses
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 09/22/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 85c3aee098786d75a7a2f17d1c9c4d11c0c87aeb
ms.sourcegitcommit: 6968594dc8cf8b30a4c958df6d65dfd0cd2cfae1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2021
ms.locfileid: "59490906"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>Erreurs courantes à éviter lors de la définition d’exclusions

Vous pouvez définir une liste d’exclusions pour les éléments que vous ne souhaitez Antivirus Microsoft Defender analyser. Ces éléments exclus peuvent contenir des menaces qui rendent votre appareil vulnérable. Cet article décrit une erreur courante que vous devez éviter lors de la définition d’exclusions.

Avant de définir vos listes d’exclusions, [voir Recommandations pour définir des exclusions.](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions)

## <a name="excluding-certain-trusted-items"></a>Exclusion de certains éléments fiables

Certains fichiers, types de fichiers, dossiers ou processus ne doivent pas être exclus de l’analyse, même si vous les faites confiance pour ne pas être malveillants.

Ne définissez pas d’exclusions pour les emplacements de dossiers, les extensions de fichiers et les processus répertoriés dans les sections suivantes :
- Emplacements des dossiers
- Extensions de fichier
- Processus

### <a name="folder-locations"></a>Emplacements des dossiers

En règle générale, ne définissez pas d’exclusions pour les emplacements de dossiers suivants :

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

`C:\Users\<UserProfileName>\AppData\Local\Temp\`**Notez l’exception suivante SharePoint**: exclure lorsque vous utilisez la protection antivirus au niveau du `C:\Users\ServiceAccount\AppData\Local\Temp` fichier dans [SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

`C:\Users\<UserProfileName>\AppData\LocalLow\Temp\`**Notez l’exception suivante SharePoint**: exclure lorsque vous utilisez la protection antivirus au niveau du `C:\Users\Default\AppData\Local\Temp` fichier dans [SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

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

En règle générale, ne définissez pas d’exclusions pour les extensions de fichier suivantes :

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

En règle générale, ne définissez pas d’exclusions pour les processus suivants :

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
> Vous pouvez choisir d’exclure des types de fichiers, tels que , ou si votre environnement dispose d’un logiciel moderne à jour avec une stratégie de mise à jour stricte pour gérer les `.gif` `.jpg` `.jpeg` `.png` vulnérabilités.

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>Utilisation du nom de fichier dans la liste d’exclusions

Les programmes malveillants peuvent porter le même nom que celui d’un fichier que vous faites confiance et que vous souhaitez exclure de l’analyse. Par conséquent, pour éviter d’exclure les programmes malveillants potentiels de l’analyse, utilisez un chemin d’accès complet au fichier que vous souhaitez exclure au lieu d’utiliser uniquement le nom du fichier. Par exemple, si vous souhaitez exclure de l’analyse, utilisez le chemin d’accès complet `Filename.exe` au fichier, tel que `C:\program files\contoso\Filename.exe` .

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>Utilisation d’une seule liste d’exclusions pour plusieurs charges de travail de serveur

N’utilisez pas une seule liste d’exclusions pour définir des exclusions pour plusieurs charges de travail de serveur. Fractionner les exclusions pour différentes charges de travail d’application ou de service en plusieurs listes d’exclusions. Par exemple, la liste d’exclusions de votre charge de travail de serveur IIS doit être différente de la liste d’exclusions pour SQL Server charge de travail.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Utilisation de variables d’environnement incorrectes comme caractères génériques dans les listes d’exclusions de nom de fichier et de chemin d’accès au dossier ou d’extension

Antivirus Microsoft Defender Le service s’exécute dans le contexte système à l’aide du compte LocalSystem, ce qui signifie qu’il obtient des informations à partir de la variable d’environnement système, et non de la variable d’environnement utilisateur. L’utilisation de variables d’environnement comme caractère générique dans les listes d’exclusions est limitée aux variables système et à celles applicables aux processus en cours d’exécution en tant que compte NT AUTHORITY\SYSTEM. Par conséquent, n’utilisez pas de variables d’environnement utilisateur comme caractères génériques lors de l Antivirus Microsoft Defender exclusions de dossiers et de processus. Consultez le tableau sous [Variables d’environnement système](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) pour obtenir la liste complète des variables d’environnement système.

Pour plus d’informations sur l’utilisation des caractères génériques dans les listes d’exclusion, voir Utiliser des [caractères génériques](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) dans les listes d’exclusions et le chemin d’accès au dossier ou les listes d’exclusions.
