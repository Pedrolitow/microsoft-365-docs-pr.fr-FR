---
title: Erreurs courantes à éviter lors de la définition d'exclusions
description: Évitez les erreurs courantes lors de la définition d'exclusions pour les analyses de l'Antivirus Microsoft Defender.
keywords: exclusions, fichiers, extension, type de fichier, nom de dossier, nom de fichier, analyses
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: eb3ac89eb05b39ff3337aa8e9c5ead1c308fbefb
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51764914"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>Erreurs courantes à éviter lors de la définition d'exclusions

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

Vous pouvez définir une liste d'exclusions pour les éléments que vous ne souhaitez pas que l'Antivirus Microsoft Defender analyse. Ces éléments exclus peuvent contenir des menaces qui rendent votre appareil vulnérable. 

Cet article décrit une erreur courante que vous devez éviter lors de la définition d'exclusions. 

Avant de définir vos listes d'exclusions, voir [Recommandations pour définir des exclusions.](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions)

## <a name="excluding-certain-trusted-items"></a>Exclusion de certains éléments fiables

Certains fichiers, types de fichiers, dossiers ou processus ne doivent pas être exclus de l'analyse, même si vous les faites confiance pour ne pas être malveillants. 

Ne définissez pas d'exclusions pour les emplacements de dossiers, les extensions de fichiers et les processus répertoriés dans le tableau suivant :

| Emplacements des dossiers | Extensions de fichier | Processus |
|:--|:--|:--|
| `%systemdrive%` <br/> `C:`<br/> `C:\` <br/> `C:\*` <br/> `%ProgramFiles%\Java` <br/> `C:\Program Files\Java` <br/> `%ProgramFiles%\Contoso\` <br/> `C:\Program Files\Contoso\` <br/> `%ProgramFiles(x86)%\Contoso\` <br/> `C:\Program Files (x86)\Contoso\` <br/> `C:\Temp` <br/> `C:\Temp\` <br/> `C:\Temp\*` <br/> `C:\Users\` <br/> `C:\Users\*` <br/> `C:\Users\<UserProfileName>\AppData\Local\Temp\` <br/> `C:\Users\<UserProfileName>\AppData\LocalLow\Temp\` <br/> `C:\Users\<UserProfileName>\AppData\Roaming\Temp\` <br/> `%Windir%\Prefetch` <br/> `C:\Windows\Prefetch` <br/> `C:\Windows\Prefetch\` <br/> `C:\Windows\Prefetch\*` <br/> `%Windir%\System32\Spool` <br/> `C:\Windows\System32\Spool` <br/> `C:\Windows\System32\CatRoot2` <br/> `%Windir%\Temp` <br/> `C:\Windows\Temp` <br/> `C:\Windows\Temp\` <br/> `C:\Windows\Temp\*` | `.7z` <br/> `.bat` <br/> `.bin` <br/> `.cab` <br/> `.cmd` <br/> `.com` <br/> `.cpl` <br/> `.dll` <br/> `.exe` <br/> `.fla` <br/> `.gif` <br/> `.gz` <br/> `.hta` <br/> `.inf` <br/> `.java` <br/> `.jar` <br/> `.job` <br/> `.jpeg` <br/> `.jpg` <br/> `.js` <br/> `.ko` <br/> `.ko.gz` <br/> `.msi` <br/> `.ocx` <br/> `.png` <br/> `.ps1` <br/> `.py` <br/> `.rar` <br/> `.reg` <br/> `.scr` <br/> `.sys` <br/> `.tar` <br/> `.tmp` <br/> `.url` <br/> `.vbe` <br/> `.vbs` <br/> `.wsf` <br/> `.zip` | `AcroRd32.exe` <br/> `bitsadmin.exe` <br/> `excel.exe` <br/> `iexplore.exe` <br/> `java.exe` <br/> `outlook.exe` <br/> `psexec.exe` <br/> `powerpnt.exe` <br/> `powershell.exe` <br/> `schtasks.exe`  <br/> `svchost.exe` <br/>`wmic.exe` <br/> `winword.exe` <br/> `wuauclt.exe` <br/> `addinprocess.exe` <br/> `addinprocess32.exe` <br/> `addinutil.exe` <br/> `bash.exe` <br/> `bginfo.exe`[1] <br/>`cdb.exe` <br/> `csi.exe` <br/> `dbghost.exe` <br/> `dbgsvc.exe` <br/> `dnx.exe` <br/> `fsi.exe` <br/> `fsiAnyCpu.exe` <br/> `kd.exe` <br/> `ntkd.exe` <br/> `lxssmanager.dll` <br/> `msbuild.exe`[2] <br/> `mshta.exe` <br/> `ntsd.exe` <br/> `rcsi.exe` <br/> `system.management.automation.dll` <br/> `windbg.exe` |

> [!NOTE]
> Vous pouvez choisir d'exclure des types de fichiers, tels que , ou si votre environnement dispose d'un logiciel moderne à jour avec une stratégie de mise à jour stricte pour gérer les `.gif` `.jpg` `.jpeg` `.png` vulnérabilités.

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>Utilisation du nom de fichier dans la liste d'exclusions

Un programme malveillant peut avoir le même nom que celui du fichier que vous faites confiance et que vous souhaitez exclure de l'analyse. Par conséquent, pour éviter d'exclure un programme malveillant potentiel de l'analyse, utilisez un chemin d'accès complet au fichier que vous souhaitez exclure au lieu d'utiliser uniquement le nom du fichier. Par exemple, si vous souhaitez exclure de l'analyse, utilisez le chemin d'accès complet `Filename.exe` au fichier, tel que `C:\program files\contoso\Filename.exe` .

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>Utilisation d'une seule liste d'exclusions pour plusieurs charges de travail serveur

N'utilisez pas une seule liste d'exclusions pour définir des exclusions pour plusieurs charges de travail de serveur. Fractionner les exclusions pour différentes charges de travail d'application ou de service en plusieurs listes d'exclusions. Par exemple, la liste d'exclusions de votre charge de travail de serveur IIS doit être différente de la liste d'exclusions de votre charge SQL Server charge de travail.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Utilisation de variables d'environnement incorrectes comme caractères génériques dans les listes d'exclusions de nom de fichier et de chemin d'accès au dossier ou d'extension

Le service Antivirus Microsoft Defender s'exécute dans le contexte système à l'aide du compte LocalSystem, ce qui signifie qu'il obtient des informations de la variable d'environnement système, et non de la variable d'environnement utilisateur. L'utilisation de variables d'environnement comme caractère générique dans les listes d'exclusions est limitée aux variables système et à celles applicables aux processus en cours d'exécution en tant que compte NT AUTHORITY\SYSTEM. Par conséquent, n'utilisez pas de variables d'environnement utilisateur comme caractères génériques lors de l'ajout d'exclusions de processus et de dossiers de l'Antivirus Microsoft Defender. Consultez le tableau sous [Variables d'environnement système](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) pour obtenir la liste complète des variables d'environnement système.

Pour plus d'informations sur l'utilisation des caractères génériques dans les listes d'exclusions, voir Utiliser des [caractères génériques](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) dans les listes d'exclusions et le chemin d'accès au dossier ou les listes d'exclusions.

## <a name="related-articles"></a>Articles connexes

- [Configurer et valider des exclusions dans les analyses de l'Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions en fonction de l'extension de fichier et de l'emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer les exclusions de l'Antivirus Microsoft Defender sur Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
