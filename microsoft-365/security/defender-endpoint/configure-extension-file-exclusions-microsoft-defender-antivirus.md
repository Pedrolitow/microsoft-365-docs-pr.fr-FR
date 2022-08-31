---
title: Configurer et valider des exclusions en fonction de l’extension, du nom ou de l’emplacement
description: Excluez les fichiers des analyses de l’Antivirus Microsoft Defender en fonction de leur extension de fichier, nom de fichier ou emplacement.
keywords: exclusions, fichiers, extension, type de fichier, nom de dossier, nom de fichier, analyses
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.date: 07/25/2022
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: thdoucet
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 49e6a54928c4459f7b19a1eb766c63cd6a182f5f
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67481919"
---
# <a name="configure-and-validate-exclusions-based-on-file-extension-and-folder-location"></a>Configurer et valider des exclusions en fonction de l’extension de fichier et de l’emplacement du dossier

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**

- Windows

Vous pouvez définir des exclusions pour l’antivirus Microsoft Defender qui s’appliquent aux [analyses planifiées](schedule-antivirus-scans.md), aux [analyses à la demande](run-scan-microsoft-defender-antivirus.md) et à la [protection et à la surveillance en temps réel en permanence](configure-real-time-protection-microsoft-defender-antivirus.md). **En règle générale, vous n’avez pas besoin d’appliquer des exclusions**. Si vous devez appliquer des exclusions, vous pouvez choisir parmi les éléments suivants :

- Exclusions basées sur les extensions de fichier et les emplacements des dossiers (décrits dans cet article)
- [Exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!IMPORTANT]
> Les exclusions de l’Antivirus Microsoft Defender ne s’appliquent pas à d’autres fonctionnalités Microsoft Defender pour point de terminaison, telles que les [règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction.md) et l’accès [contrôlé aux dossiers](controlled-folders.md). Les fichiers que vous excluez à l’aide des méthodes décrites dans cet article peuvent toujours déclencher des alertes de détection de point de terminaison et de réponse (EDR) et d’autres détections.
> Pour exclure les fichiers de manière générale, ajoutez-les aux [indicateurs personnalisés](manage-indicators.md) Microsoft Defender pour point de terminaison.

## <a name="before-you-begin"></a>Avant de commencer

Consultez [Recommandations pour définir des exclusions](configure-exclusions-microsoft-defender-antivirus.md) avant de définir vos listes d’exclusions.

## <a name="exclusion-lists"></a>Listes d’exclusions

Pour exclure certains fichiers des analyses de l’Antivirus Microsoft Defender, modifiez vos listes d’exclusion. L’Antivirus Microsoft Defender inclut de nombreuses exclusions automatiques basées sur les comportements connus du système d’exploitation et les fichiers de gestion classiques, tels que ceux utilisés dans la gestion d’entreprise, la gestion des bases de données et d’autres scénarios et situations d’entreprise.

> [!NOTE]
> Les exclusions s’appliquent également aux [détections d’applications potentiellement indésirables (PUA](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) ).
> Les exclusions automatiques s’appliquent uniquement aux Windows Server 2016 et versions ultérieures. Ces exclusions ne sont pas visibles dans l’application Sécurité Windows et dans PowerShell.

Le tableau suivant répertorie quelques exemples d’exclusions basées sur l’extension de fichier et l’emplacement du dossier.

|Exclusion|Exemples|Liste d’exclusions|
|---|---|---|
|Tout fichier avec une extension spécifique|Tous les fichiers avec l’extension spécifiée, n’importe où sur l’ordinateur. <p> Syntaxe valide : `.test` et `test`|Exclusions d’extension|
|Tout fichier sous un dossier spécifique|Tous les fichiers sous le `c:\test\sample` dossier|Exclusions de fichiers et de dossiers|
|Un fichier spécifique dans un dossier spécifique|`c:\sample\sample.test` Fichier uniquement|Exclusions de fichiers et de dossiers|
|Un processus spécifique|Fichier exécutable `c:\test\process.exe`|Exclusions de fichiers et de dossiers|

## <a name="characteristics-of-exclusion-lists"></a>Caractéristiques des listes d’exclusion

- Les exclusions de dossier s’appliquent à tous les fichiers et dossiers sous ce dossier, sauf si le sous-dossier est un point d’analyse. Les sous-dossiers de point d’analyse doivent être exclus séparément.
- Les extensions de fichier s’appliquent à n’importe quel nom de fichier avec l’extension définie si un chemin d’accès ou un dossier n’est pas défini.

## <a name="important-notes-about-exclusions-based-on-file-extensions-and-folder-locations"></a>Remarques importantes sur les exclusions basées sur les extensions de fichier et les emplacements des dossiers

- L’utilisation de caractères génériques tels que l’astérisque (\*) modifie la façon dont les règles d’exclusion sont interprétées. Pour plus d’informations importantes sur [le fonctionnement des caractères génériques, consultez la section Utiliser des caractères génériques dans la section nom de fichier et chemin d’accès au dossier ou listes d’exclusion d’extension](#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) .

- N’excluez pas les lecteurs réseau mappés. Spécifiez le chemin d’accès réseau réel.

- Les dossiers qui sont des points d’analyse sont créés après le démarrage du service Antivirus Microsoft Defender, et ceux qui ont été ajoutés à la liste d’exclusion ne seront pas inclus. Redémarrez le service en redémarrant Windows pour les nouveaux points d’analyse à reconnaître comme cible d’exclusion valide.

- Les exclusions s’appliquent aux [analyses planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md), aux [analyses à la demande](run-scan-microsoft-defender-antivirus.md) et à la [protection en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md), mais pas à toutes les fonctionnalités de Defender pour point de terminaison. Pour définir des exclusions entre Defender pour point de terminaison, utilisez [des indicateurs personnalisés](manage-indicators.md).

- Par défaut, les modifications locales apportées aux listes (par les utilisateurs disposant de privilèges d’administrateur, y compris les modifications apportées avec PowerShell et WMI) sont fusionnées avec les listes telles que définies (et déployées) par stratégie de groupe, Configuration Manager ou Intune. Les listes stratégie de groupe sont prioritaires en cas de conflits. En outre, les modifications apportées à la liste d’exclusion avec stratégie de groupe sont visibles dans [l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md).

- Pour autoriser les modifications locales à remplacer les paramètres de déploiement managé, [configurez la façon dont les listes d’exclusions définies localement et globalement sont fusionnées](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists).

## <a name="configure-the-list-of-exclusions-based-on-folder-name-or-file-extension"></a>Configurer la liste des exclusions en fonction du nom du dossier ou de l’extension de fichier

Vous pouvez choisir parmi plusieurs méthodes pour définir des exclusions pour l’antivirus Microsoft Defender.

### <a name="use-intune-to-configure-file-name-folder-or-file-extension-exclusions"></a>Utiliser Intune pour configurer les exclusions de nom de fichier, de dossier ou d’extension de fichier

Consultez les articles suivants :

- [Configurer des paramètres de restriction d’appareils dans Microsoft Intune](/intune/device-restrictions-configure)
- [Paramètres de restriction d’appareil antivirus Microsoft Defender pour les Windows 10 dans Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

### <a name="use-configuration-manager-to-configure-file-name-folder-or-file-extension-exclusions"></a>Utiliser Configuration Manager pour configurer les exclusions de nom de fichier, de dossier ou d’extension de fichier

Découvrez [comment créer et déployer des stratégies anti-programme malveillant : Paramètres d’exclusion](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) pour plus d’informations sur la configuration de Microsoft Endpoint Manager (current branch).

### <a name="use-group-policy-to-configure-folder-or-file-extension-exclusions"></a>Utiliser stratégie de groupe pour configurer des exclusions d’extension de dossier ou de fichier

> [!NOTE]
> Si vous spécifiez un chemin d’accès complet à un fichier, seul ce fichier est exclu. Si un dossier est défini dans l’exclusion, tous les fichiers et sous-répertoires sous ce dossier sont exclus.

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), faites un clic droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**, puis sélectionnez **Modèles d’administration**.

3. Développez l’arborescence vers **les composants Windows exclusions** \> **de l’antivirus** \> Microsoft Defender.

4. Ouvrez le paramètre **Exclusions de chemin** d’accès à modifier et ajoutez vos exclusions.

    1. Définissez l’option **sur Activé**.
    2. Dans la section **Options** , sélectionnez **Afficher**.
    3. Spécifiez chaque dossier sur sa propre ligne sous la colonne **Nom de** la valeur.
    4. Si vous spécifiez un fichier, veillez à entrer un chemin d’accès complet au fichier, y compris la lettre de lecteur, le chemin d’accès au dossier, le nom de fichier et l’extension.
    5. Entrez **0** dans la colonne **Valeur** .

5. Sélectionnez **OK**.

6. Ouvrez le paramètre **Exclusions d’extension** pour modifier et ajoutez vos exclusions.

    1. Définissez l’option **sur Activé**.
    2. Dans la section **Options** , sélectionnez **Afficher**.
    3. Entrez chaque extension de fichier sur sa propre ligne sous la colonne **Nom de** la valeur.
    4. Entrez **0** dans la colonne **Valeur** .

7. Sélectionnez **OK**.

<a id="ps"></a>

### <a name="use-powershell-cmdlets-to-configure-file-name-folder-or-file-extension-exclusions"></a>Utiliser les applets de commande PowerShell pour configurer les exclusions de nom de fichier, de dossier ou d’extension de fichier

L’utilisation de PowerShell pour ajouter ou supprimer des exclusions pour les fichiers en fonction de l’extension, de l’emplacement ou du nom de fichier nécessite l’utilisation d’une combinaison de trois applets de commande et du paramètre de liste d’exclusions approprié. Les applets de commande se trouvent toutes dans le [module Defender](/powershell/module/defender/).

Le format des applets de commande est le suivant :

```PowerShell
<cmdlet> -<exclusion list> "<item>"
```

Le tableau suivant répertorie les applets de commande que vous pouvez utiliser dans la `<cmdlet>` partie de l’applet de commande PowerShell :

|Action de configuration|Applet de commande PowerShell|
|:---|:---|
|Créer ou remplacer la liste|`Set-MpPreference`|
|Ajouter à la liste|`Add-MpPreference`|
|Supprimer un élément de la liste|`Remove-MpPreference`|

Le tableau suivant répertorie les valeurs que vous pouvez utiliser dans la `<exclusion list>` partie de l’applet de commande PowerShell :

|Type d’exclusion|Paramètre PowerShell|
|---|---|
|Tous les fichiers avec une extension de fichier spécifiée|`-ExclusionExtension`|
|Tous les fichiers sous un dossier (y compris les fichiers dans les sous-répertoires) ou un fichier spécifique|`-ExclusionPath`|

> [!IMPORTANT]
> Si vous avez créé une liste, avec `Set-MpPreference` ou `Add-MpPreference`, l’utilisation de l’applet `Set-MpPreference` de commande remplacera à nouveau la liste existante.

Par exemple, l’extrait de code suivant entraîne l’exclusion des analyses antivirus Microsoft Defender de tout fichier avec l’extension de `.test` fichier :

```PowerShell
Add-MpPreference -ExclusionExtension ".test"
```

> [!TIP]
> Pour plus d’informations, consultez [Utiliser les applets de commande PowerShell pour configurer et exécuter l’antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et les [Applets de commande de l’antivirus Defender](/powershell/module/defender/).

### <a name="use-windows-management-instrumentation-wmi-to-configure-file-name-folder-or-file-extension-exclusions"></a>Utiliser Windows Management Instrumentation (WMI) pour configurer les exclusions de nom de fichier, de dossier ou d’extension de fichier

Utilisez les [méthodes Set, Add et Remove de la classe MSFT_MpPreference](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ExclusionExtension
ExclusionPath
```

L’utilisation de **Set**, **Add** et **Remove** est analogue à leurs équivalents dans PowerShell : `Set-MpPreference`, `Add-MpPreference`et `Remove-MpPreference`.

> [!TIP]
> Pour plus d’informations, consultez [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="man-tools"></a>

### <a name="use-the-windows-security-app-to-configure-file-name-folder-or-file-extension-exclusions"></a>Utiliser l’application Sécurité Windows pour configurer les exclusions de nom de fichier, de dossier ou d’extension de fichier

Pour obtenir des instructions, consultez [Ajouter des exclusions dans l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md).

<a id="wildcards"></a>

## <a name="use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Utiliser des caractères génériques dans les listes d’exclusions de nom de fichier et de dossier ou d’extension

Vous pouvez utiliser l’astérisque `*`, le point `?`d’interrogation ou les variables d’environnement (par `%ALLUSERSPROFILE%`exemple) comme caractères génériques lors de la définition d’éléments dans le nom de fichier ou la liste d’exclusion du chemin d’accès au dossier. La façon dont ces caractères génériques sont interprétés diffère de leur utilisation habituelle dans d’autres applications et langages. Veillez à lire cette section pour comprendre leurs limitations spécifiques.

> [!IMPORTANT]
> Il existe des limitations clés et des scénarios d’utilisation pour ces caractères génériques :
> - L’utilisation des variables d’environnement est limitée aux variables de machine et à celles applicables aux processus s’exécutant en tant que compte NT AUTHORITY\SYSTEM.
> - Vous ne pouvez utiliser qu’un maximum de six caractères génériques par entrée.
> - Vous ne pouvez pas utiliser un caractère générique à la place d’une lettre de lecteur.
> - Un astérisque `*` dans une exclusion de dossier est en place pour un dossier unique. Utilisez plusieurs instances pour `\*\` indiquer plusieurs dossiers imbriqués avec des noms non spécifiés.
    
Le tableau suivant décrit comment utiliser les caractères génériques et fournit quelques exemples.

|Caractère générique|Exemples|
|---|---|
|`*` (astérisque) <p> Dans **les inclusions de nom de fichier et d’extension de fichier**, l’astérisque remplace n’importe quel nombre de caractères et s’applique uniquement aux fichiers du dernier dossier défini dans l’argument. <p> Dans **les exclusions de dossier,** l’astérisque remplace un seul dossier. Utilisez plusieurs `*` barres obliques avec des dossiers `\` pour indiquer plusieurs dossiers imbriqués. Après avoir mis en correspondance le nombre de dossiers génériques et nommés, tous les sous-dossiers sont également inclus.|`C:\MyData\*.txt` Comprend `C:\MyData\notes.txt` <p> `C:\somepath\*\Data` inclut n’importe quel fichier dans `C:\somepath\Archives\Data` et ses sous-dossiers, ainsi que `C:\somepath\Authorized\Data` ses sous-dossiers <p> `C:\Serv\*\*\Backup` inclut n’importe quel fichier dans `C:\Serv\Primary\Denied\Backup` et ses sous-dossiers, ainsi que `C:\Serv\Secondary\Allowed\Backup` ses sous-dossiers|
|`?` (Point d’interrogation)  <p> Dans **les inclusions de nom de fichier et d’extension de fichier**, le point d’interrogation remplace un caractère unique et s’applique uniquement aux fichiers du dernier dossier défini dans l’argument. <p> Dans **les exclusions de dossier**, le point d’interrogation remplace un caractère unique dans un nom de dossier. Après avoir mis en correspondance le nombre de dossiers génériques et nommés, tous les sous-dossiers sont également inclus.|`C:\MyData\my?.zip` Comprend `C:\MyData\my1.zip` <p> `C:\somepath\?\Data` inclut n’importe quel fichier dans `C:\somepath\P\Data` et ses sous-dossiers  <p> `C:\somepath\test0?\Data` inclurait n’importe quel fichier dans `C:\somepath\test01\Data` et ses sous-dossiers|
|Variables d’environnement <p> La variable définie est remplie en tant que chemin d’accès lorsque l’exclusion est évaluée.|`%ALLUSERSPROFILE%\CustomLogFiles` inclurait `C:\ProgramData\CustomLogFiles\Folder1\file1.txt`|

> [!IMPORTANT]
> Si vous mélangez un argument d’exclusion de fichier à un argument d’exclusion de dossier, les règles s’arrêtent à la correspondance de l’argument de fichier dans le dossier correspondant et ne recherchent pas les correspondances de fichiers dans les sous-dossiers.
> Par exemple, vous pouvez exclure tous les fichiers qui commencent par « date » dans les dossiers `c:\data\final\marked` et `c:\data\review\marked` à l’aide de l’argument `c:\data\*\marked\date*`de règle.
> Toutefois, cet argument ne correspond à aucun fichier dans les sous-dossiers sous `c:\data\final\marked` ou `c:\data\review\marked`.

<a id="review"></a>

### <a name="system-environment-variables"></a>Variables d’environnement système

Le tableau suivant répertorie et décrit les variables d’environnement de compte système.

|Cette variable d’environnement système...|Redirige vers ce|
|---|---|
|`%APPDATA%`|`C:\Windows\system32\config\systemprofile\Appdata\Roaming`|
|`%APPDATA%\Microsoft\Internet Explorer\Quick Launch`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch`|
|`%APPDATA%\Microsoft\Windows\Start Menu`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Windows\Start Menu`|
|`%APPDATA%\Microsoft\Windows\Start Menu\Programs`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Windows\Start Menu\Programs`|
|`%LOCALAPPDATA%`|`C:\Windows\System32\config\systemprofile\AppData\Local`|
|`%ProgramData%`|`C:\ProgramData`|
|`%ProgramFiles%`|`C:\Program Files`|
|`%ProgramFiles%\Common Files`|`C:\Program Files\Common Files`|
|`%ProgramFiles%\Windows Sidebar\Gadgets`|`C:\Program Files\Windows Sidebar\Gadgets`|
|`%ProgramFiles%\Common Files`|`C:\Program Files\Common Files`|
|`%ProgramFiles(x86)%`|`C:\Program Files (x86)`|
|`%ProgramFiles(x86)%\Common Files`|`C:\Program Files (x86)\Common Files`|
|`%SystemDrive%`|`C:`|
|`%SystemDrive%\Program Files`|`C:\Program Files`|
|`%SystemDrive%\Program Files (x86)`|`C:\Program Files (x86)`|
|`%SystemDrive%\Users`|`C:\Users`|
|`%SystemDrive%\Users\Public`|`C:\Users\Public`|
|`%SystemRoot%`|`C:\Windows`|
|`%windir%`|`C:\Windows`|
|`%windir%\Fonts`|`C:\Windows\Fonts`|
|`%windir%\Resources`|`C:\Windows\Resources`|
|`%windir%\resources\0409`|`C:\Windows\resources\0409`|
|`%windir%\system32`|`C:\Windows\System32`|
|`%ALLUSERSPROFILE%`|`C:\ProgramData`|
|`%ALLUSERSPROFILE%\Application Data`|`C:\ProgramData\Application Data`|
|`%ALLUSERSPROFILE%\Documents`|`C:\ProgramData\Documents`|
|`%ALLUSERSPROFILE%\Documents\My Music\Sample Music`|`C:\ProgramData\Documents\My Music\Sample Music`|
|`%ALLUSERSPROFILE%\Documents\My Music`|`C:\ProgramData\Documents\My Music`|
|`%ALLUSERSPROFILE%\Documents\My Pictures`|`C:\ProgramData\Documents\My Pictures`|
|`%ALLUSERSPROFILE%\Documents\My Pictures\Sample Pictures`|`C:\ProgramData\Documents\My Pictures\Sample Pictures`|
|`%ALLUSERSPROFILE%\Documents\My Videos`|`C:\ProgramData\Documents\My Videos`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\DeviceMetadataStore`|`C:\ProgramData\Microsoft\Windows\DeviceMetadataStore`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\GameExplorer`|`C:\ProgramData\Microsoft\Windows\GameExplorer`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Ringtones`|`C:\ProgramData\Microsoft\Windows\Ringtones`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu`|`C:\ProgramData\Microsoft\Windows\Start Menu`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Administrative Tools`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Administrative Tools`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\StartUp`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Templates`|`C:\ProgramData\Microsoft\Windows\Templates`|
|`%ALLUSERSPROFILE%\Start Menu`|`C:\ProgramData\Start Menu`|
|`%ALLUSERSPROFILE%\Start Menu\Programs`| `C:\ProgramData\Start Menu\Programs`|
|`%ALLUSERSPROFILE%\Start Menu\Programs\Administrative Tools`|`C:\ProgramData\Start Menu\Programs\Administrative Tools`|
|`%ALLUSERSPROFILE%\Templates`|`C:\ProgramData\Templates`|
|`%LOCALAPPDATA%\Microsoft\Windows\ConnectedSearch\Templates`|`C:\Windows\System32\config\systemprofile\AppData\Local\Microsoft\Windows\ConnectedSearch\Templates`|
|`%LOCALAPPDATA%\Microsoft\Windows\History`|`C:\Windows\System32\config\systemprofile\AppData\Local\Microsoft\Windows\History`|
|`%PUBLIC%`|`C:\Users\Public`|
|`%PUBLIC%\AccountPictures`|`C:\Users\Public\AccountPictures`|
|`%PUBLIC%\Desktop`|`C:\Users\Public\Desktop`|
|`%PUBLIC%\Documents`|`C:\Users\Public\Documents`|
|`%PUBLIC%\Downloads`|`C:\Users\Public\Downloads`|
|`%PUBLIC%\Music\Sample Music`|`C:\Users\Public\Music\Sample Music`|
|`%PUBLIC%\Music\Sample Playlists`|`C:\Users\Public\Music\Sample Playlists`|
|`%PUBLIC%\Pictures\Sample Pictures`|`C:\Users\Public\Pictures\Sample Pictures`|
|`%PUBLIC%\RecordedTV.library-ms`|`C:\Users\Public\RecordedTV.library-ms`|
|`%PUBLIC%\Videos`|`C:\Users\Public\Videos`|
|`%PUBLIC%\Videos\Sample Videos`|`C:\Users\Public\Videos\Sample Videos`|
|`%USERPROFILE%`|`C:\Windows\system32\config\systemprofile`|
|`%USERPROFILE%\AppData\Local`|`C:\Windows\system32\config\systemprofile\AppData\Local`|
|`%USERPROFILE%\AppData\LocalLow`|`C:\Windows\system32\config\systemprofile\AppData\LocalLow`|
|`%USERPROFILE%\AppData\Roaming`|`C:\Windows\system32\config\systemprofile\AppData\Roaming`|

## <a name="review-the-list-of-exclusions"></a>Examiner la liste des exclusions

Vous pouvez récupérer les éléments de la liste d’exclusion à l’aide de l’une des méthodes suivantes :

- [Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)
- [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies)
- [MpCmdRun](command-line-arguments-microsoft-defender-antivirus.md)
- [PowerShell](/powershell/module/defender)
- [Application Sécurité Windows](microsoft-defender-security-center-antivirus.md)

> [!IMPORTANT]
> Les modifications apportées à la liste d’exclusion avec stratégie de groupe **s’affichent** dans les listes de [Sécurité Windows’application](microsoft-defender-security-center-antivirus.md).
> Les modifications apportées à l’application Sécurité Windows **ne s’affichent pas** dans les listes stratégie de groupe.

Si vous utilisez PowerShell, vous pouvez récupérer la liste de deux manières :

- Récupérez l’état de toutes les préférences de l’Antivirus Microsoft Defender. Chaque liste s’affiche sur des lignes distinctes, mais les éléments de chaque liste sont combinés dans la même ligne.
- Écrivez l’état de toutes les préférences dans une variable et utilisez cette variable pour appeler uniquement la liste spécifique qui vous intéresse. Chaque utilisation est `Add-MpPreference` écrite dans une nouvelle ligne.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>Valider la liste d’exclusion à l’aide de MpCmdRun

Pour vérifier les exclusions avec [l’outil de ligne de commande dédié mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md), utilisez la commande suivante :

```console
Start, CMD (Run as admin)
cd "%programdata%\microsoft\windows defender\platform"
cd 4.18.2111-5.0 (Where 4.18.2111-5.0 is this month's Microsoft Defender Antivirus "Platform Update".)
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> La vérification des exclusions avec MpCmdRun nécessite microsoft Defender Antivirus CAMP version 4.18.2111-5.0 (publiée en décembre 2021) ou version ultérieure.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>Passez en revue la liste des exclusions avec toutes les autres préférences antivirus Microsoft Defender à l’aide de PowerShell

Utilisez l’applet de commande suivante :

```PowerShell
Get-MpPreference
```

Dans l’exemple suivant, les éléments contenus dans la `ExclusionExtension` liste sont mis en surbrillance :

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="Sortie PowerShell pour Get-MpPreference" lightbox="../../media/wdav-powershell-get-exclusions-variable.png":::

Pour plus d’informations, consultez [Utiliser les applets de commande PowerShell pour configurer et exécuter l’antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et les [Applets de commande de l’antivirus Defender](/powershell/module/defender/).

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>Récupérer une liste d’exclusions spécifique à l’aide de PowerShell

Utilisez l’extrait de code suivant (entrez chaque ligne comme commande distincte) ; remplacez **WDAVprefs** par l’étiquette que vous souhaitez nommer la variable :

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionExtension
$WDAVprefs.ExclusionPath
```

Dans l’exemple suivant, la liste est divisée en nouvelles lignes pour chaque utilisation de l’applet `Add-MpPreference` de commande :

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="Sortie PowerShell affichant uniquement les entrées dans la liste d’exclusions" lightbox="../../media/wdav-powershell-get-exclusions-variable.png":::

Pour plus d’informations, consultez [Utiliser les applets de commande PowerShell pour configurer et exécuter l’antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et les [Applets de commande de l’antivirus Defender](/powershell/module/defender/).

<a id="validate"></a>

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>Valider les listes d’exclusions avec le fichier de test EICAR

Vous pouvez vérifier que vos listes d’exclusion fonctionnent à l’aide de PowerShell avec l’applet `Invoke-WebRequest` de commande ou la classe WebClient .NET pour télécharger un fichier de test.

Dans l’extrait de code PowerShell suivant, remplacez-le par `test.txt` un fichier conforme à vos règles d’exclusion. Par exemple, si vous avez exclu l’extension`.testing`, remplacez `test.testing``test.txt` par . Si vous testez un chemin d’accès, veillez à exécuter l’applet de commande dans ce chemin.

```PowerShell
Invoke-WebRequest "http://www.eicar.org/download/eicar.com.txt" -OutFile "test.txt"
```

Si l’Antivirus Microsoft Defender signale un programme malveillant, la règle ne fonctionne pas. S’il n’existe aucun rapport de programmes malveillants et que le fichier téléchargé existe, l’exclusion fonctionne. Vous pouvez ouvrir le fichier pour confirmer que le contenu est le même que celui décrit sur le [site web du fichier de test EICAR](http://www.eicar.org/86-0-Intended-use.html).

Vous pouvez également utiliser le code PowerShell suivant, qui appelle la classe WebClient .NET pour télécharger le fichier de test , comme avec l’applet de commande ; remplacez-le `Invoke-WebRequest` `c:\test.txt` par un fichier conforme à la règle que vous validez :

```PowerShell
$client = new-object System.Net.WebClient
$client.DownloadFile("http://www.eicar.org/download/eicar.com.txt","c:\test.txt")
```

Si vous n’avez pas accès à Internet, vous pouvez créer votre propre fichier de test EICAR en écrivant la chaîne EICAR dans un nouveau fichier texte à l’aide de la commande PowerShell suivante :

```PowerShell
[io.file]::WriteAllText("test.txt",'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*')
```

Vous pouvez également copier la chaîne dans un fichier texte vide et tenter de l’enregistrer avec le nom du fichier ou dans le dossier que vous tentez d’exclure.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="see-also"></a>Voir aussi

- [Configurer et valider les exclusions dans les analyses de l’Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider les exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer les exclusions de l’Antivirus Microsoft Defender sur Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Erreurs courantes à éviter lors de la définition d’exclusions](common-exclusion-mistakes-microsoft-defender-antivirus.md)
