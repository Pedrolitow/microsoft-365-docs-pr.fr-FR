---
title: Configurer et valider des exclusions en fonction de l’extension, du nom ou de l’emplacement
description: Exclure des fichiers Antivirus Microsoft Defender analyses en fonction de leur extension de fichier, de leur nom de fichier ou de leur emplacement.
keywords: exclusions, fichiers, extension, type de fichier, nom de dossier, nom de fichier, analyses
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.date: 08/27/2021
ms.openlocfilehash: 76508ef21b60d4376512f08a07925eca109f68e2
ms.sourcegitcommit: 8ef23d275d7209a705295e2b117d4382b20ad4f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2021
ms.locfileid: "58866654"
---
# <a name="configure-and-validate-exclusions-based-on-file-extension-and-folder-location"></a>Configurer et valider des exclusions en fonction de l’extension de fichier et de l’emplacement du dossier

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)
- Antivirus Microsoft Defender

Vous pouvez définir des exclusions pour les Antivirus Microsoft Defender qui [](run-scan-microsoft-defender-antivirus.md)s’appliquent aux analyses [programmées,](schedule-antivirus-scans.md)aux analyses à la demande et à la protection et à la surveillance en temps réel toujours en temps [réel.](configure-real-time-protection-microsoft-defender-antivirus.md) **En règle générale, il n’est pas nécessaire d’appliquer des exclusions.** Si vous devez appliquer des exclusions, vous pouvez choisir parmi différents types :

- Exclusions basées sur les extensions de fichiers et les emplacements de dossiers (décrits dans cet article)
- [Exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!IMPORTANT]
> Antivirus Microsoft Defender exclusions ne s’appliquent pas aux autres fonctionnalités de Microsoft Defender pour les points de terminaison, notamment [](/microsoft-365/security/defender-endpoint/controlled-folders)les protection évolutive des points de terminaison [(PEPT),](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)les règles de réduction de la surface d’attaque [(ASR)](/microsoft-365/security/defender-endpoint/attack-surface-reduction)et l’accès contrôlé aux dossiers. Les fichiers que vous excluez à l’aide des méthodes décrites dans cet article peuvent toujours déclencher PEPT alertes et autres détections.
> Pour exclure les fichiers à grande étendue, ajoutez-les aux indicateurs [personnalisés](/microsoft-365/security/defender-endpoint/manage-indicators)Microsoft Defender for Endpoint.

## <a name="before-you-begin"></a>Avant de commencer...

Voir [Recommandations pour définir des exclusions](configure-exclusions-microsoft-defender-antivirus.md) avant de définir vos listes d’exclusions.

## <a name="exclusion-lists"></a>Listes d’exclusions

Pour exclure certains fichiers de Antivirus Microsoft Defender analyses, vous modifiez vos listes d’exclusions. Antivirus Microsoft Defender inclut de nombreuses exclusions automatiques basées sur les comportements connus du système d’exploitation et les fichiers de gestion classiques, tels que ceux utilisés dans la gestion d’entreprise, la gestion des bases de données et d’autres scénarios et situations d’entreprise.

> [!NOTE]
> Les exclusions s’appliquent également aux détections d’applications potentiellement indésirables (PUA).
>
> Les exclusions automatiques s’appliquent uniquement Windows Server 2016 et ultérieures. Ces exclusions ne sont pas visibles dans l’application Sécurité Windows et dans PowerShell.

Le tableau suivant répertorie quelques exemples d’exclusions basées sur l’extension de fichier et l’emplacement du dossier.

<br>

****

|Exclusion|Exemples|Liste d’exclusions|
|---|---|---|
|Tout fichier avec une extension spécifique|Tous les fichiers avec l’extension spécifiée, n’importe où sur l’ordinateur. <p> Syntaxe valide : `.test` et `test`|Exclusions d’extensions|
|N’importe quel fichier sous un dossier spécifique|Tous les fichiers sous le `c:\test\sample` dossier|Exclusions de fichiers et de dossiers|
|Un fichier spécifique dans un dossier spécifique|Fichier `c:\sample\sample.test` uniquement|Exclusions de fichiers et de dossiers|
|Un processus spécifique|Fichier exécutable `c:\test\process.exe`|Exclusions de fichiers et de dossiers|

## <a name="characteristics-of-exclusion-lists"></a>Caractéristiques des listes d’exclusions

- Les exclusions de dossiers s’appliquent à tous les fichiers et dossiers de ce dossier, sauf si le sous-dossier est un point d’parage. Les sous-ensembles de points d’parse doivent être exclus séparément.
- Les extensions de fichier s’appliquent à n’importe quel nom de fichier avec l’extension définie si aucun chemin d’accès ou dossier n’est défini.

## <a name="important-notes-about-exclusions-based-on-file-extensions-and-folder-locations"></a>Remarques importantes sur les exclusions basées sur les extensions de fichiers et les emplacements de dossiers

- L’utilisation de caractères génériques tels que l’astérisque ( ) modifie l’interprétation des règles \* d’exclusion. Pour plus d’informations sur le fonctionnement des [caractères génériques,](#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) voir la section Utiliser des caractères génériques dans la section des listes d’exclusions de nom de fichier et de dossier ou d’extension.

- N’excluez pas les lecteurs réseau mappés. Spécifiez le chemin d’accès réseau réel.

- Les dossiers qui sont des points d’parse créés après le démarrage du service Antivirus Microsoft Defender et qui ont été ajoutés à la liste d’exclusions ne seront pas inclus. Redémarrez le service (en redémarré Windows) pour que les nouveaux points d’parparage soient reconnus comme cibles d’exclusion valides.

- Les exclusions s’appliquent [](run-scan-microsoft-defender-antivirus.md)aux analyses [programmées,](scheduled-catch-up-scans-microsoft-defender-antivirus.md)aux analyses à la demande et à la [protection](configure-real-time-protection-microsoft-defender-antivirus.md)en temps réel, mais pas à Travers Defender pour le point de terminaison. Pour définir des exclusions dans Defender pour le point de terminaison, utilisez [des indicateurs personnalisés.](manage-indicators.md)

- Par défaut, les modifications locales apportées aux listes (par les utilisateurs ayant des privilèges d’administrateur, y compris les modifications apportées avec PowerShell et WMI) seront fusionnées avec les listes telles que définies (et déployées) par la stratégie de groupe, Configuration Manager ou Intune. Les listes de stratégie de groupe prévalent en cas de conflit. En outre, les modifications apportées à la liste d’exclusions avec la stratégie de groupe sont visibles dans [l Sécurité Windows app.](microsoft-defender-security-center-antivirus.md)

- Pour permettre aux modifications locales de remplacer les paramètres de déploiement géré, configurez la façon dont les [listes d’exclusions définies](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists)localement et globalement sont fusionnées.

## <a name="configure-the-list-of-exclusions-based-on-folder-name-or-file-extension"></a>Configurer la liste des exclusions en fonction du nom du dossier ou de l’extension de fichier

Vous pouvez choisir parmi plusieurs méthodes pour définir des exclusions pour Antivirus Microsoft Defender.

### <a name="use-intune-to-configure-file-name-folder-or-file-extension-exclusions"></a>Utiliser Intune pour configurer des exclusions de nom de fichier, de dossier ou d’extension de fichier

Consultez les articles suivants :

- [Configurer les paramètres de restriction d’appareil dans Microsoft Intune](/intune/device-restrictions-configure)
- [Antivirus Microsoft Defender de restriction d’appareil pour Windows 10 dans Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

### <a name="use-configuration-manager-to-configure-file-name-folder-or-file-extension-exclusions"></a>Utiliser Configuration Manager pour configurer des exclusions de nom de fichier, de dossier ou d’extension de fichier

Découvrez comment créer et déployer des stratégies de logiciel [anti-programme](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) malveillant : paramètres d’exclusion pour plus d’informations sur la configuration Microsoft Endpoint Manager (branche actuelle).

### <a name="use-group-policy-to-configure-folder-or-file-extension-exclusions"></a>Utiliser une stratégie de groupe pour configurer des exclusions de dossiers ou d’extensions de fichiers

> [!NOTE]
> Si vous spécifiez un chemin d’accès complet à un fichier, seul ce fichier est exclu. Si un dossier est défini dans l’exclusion, tous les fichiers et sous-répertoires de ce dossier sont exclus.

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), faites un clic droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier**.

2. Dans **l’Éditeur de gestion des stratégies de** groupe, sélectionnez **Configuration** ordinateur et **sélectionnez Modèles d’administration.**

3. Développez l’arborescence **Windows composants** \> **Antivirus Microsoft Defender** \> **exclusions.**

4. Ouvrez le **paramètre Exclusions de** chemin d’accès pour modification et ajoutez vos exclusions.
    1. Définissez l’option **sur Activé.**
    2. Sous la section **Options,** sélectionnez **Afficher.**
    3. Spécifiez chaque dossier sur sa propre ligne sous la **colonne Nom de** la valeur.
    4. Si vous spécifiez un fichier, veillez à entrer un chemin d’accès complet au fichier, y compris la lettre de lecteur, le chemin d’accès au dossier, le nom de fichier et l’extension. Entrez **0 dans** la **colonne** Valeur.

5. Sélectionnez **OK**.

6. Ouvrez **le paramètre Exclusions des extensions** pour la modification et ajoutez vos exclusions.
    1. Définissez l’option **sur Activé.**
    2. Sous la section **Options,** sélectionnez **Afficher.**
    3. Entrez chaque extension de fichier sur sa propre ligne sous la **colonne Nom** de la valeurEnter **0** dans la **colonne** Valeur.

7. Sélectionnez **OK**.

<a id="ps"></a>

### <a name="use-powershell-cmdlets-to-configure-file-name-folder-or-file-extension-exclusions"></a>Utiliser les cmdlets PowerShell pour configurer des exclusions de nom de fichier, de dossier ou d’extension de fichier

L’utilisation de PowerShell pour ajouter ou supprimer des exclusions pour des fichiers basés sur l’extension, l’emplacement ou le nom de fichier nécessite l’utilisation d’une combinaison de trois cmdlets et du paramètre de liste d’exclusions approprié. Les cmdlets sont toutes dans le [module Defender.](/powershell/module/defender/)

Le format des cmdlets est le suivant :

```PowerShell
<cmdlet> -<exclusion list> "<item>"
```

Le tableau suivant répertorie les cmdlets que vous pouvez utiliser dans la `<cmdlet>` partie de l’cmdlet PowerShell :

<br>

|Action de configuration|Cmdlet PowerShell|
|:---|:---|
|Créer ou overwrite la liste|`Set-MpPreference`|
|Ajouter à la liste|`Add-MpPreference`|
|Supprimer l’élément de la liste|`Remove-MpPreference`|

Le tableau suivant répertorie les valeurs que vous pouvez utiliser dans la `<exclusion list>` partie de l’cmdlet PowerShell :

<br>

|Type d’exclusion|Paramètre PowerShell|
|---|---|
|Tous les fichiers avec une extension de fichier spécifiée|`-ExclusionExtension`|
|Tous les fichiers sous un dossier (y compris les fichiers dans les sous-répertoires) ou un fichier spécifique|`-ExclusionPath`|

> [!IMPORTANT]
> Si vous avez créé une liste, avec ou , en utilisant à nouveau la `Set-MpPreference` `Add-MpPreference` `Set-MpPreference` cmdlet, la liste existante est réécrite.

Par exemple, l’extrait de code suivant entraîne Antivirus Microsoft Defender analyses pour exclure tout fichier avec `.test` l’extension de fichier :

```PowerShell
Add-MpPreference -ExclusionExtension ".test"
```

> [!TIP]
> Pour plus d’informations, voir [Utiliser les cmdlets PowerShell pour configurer et gérer l'Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et [Cmdlets Defender](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-configure-file-name-folder-or-file-extension-exclusions"></a>Utiliser Windows Management Instruction (WMI) pour configurer les exclusions de nom de fichier, de dossier ou d’extension de fichier

Utilisez les [méthodes Set, Add et Remove](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) de la classe MSFT_MpPreference pour les propriétés suivantes :

```WMI
ExclusionExtension
ExclusionPath
```

**L’utilisation** de Set , **Add** et **Remove** est analogue à leurs équivalents dans PowerShell : , `Set-MpPreference` et `Add-MpPreference` `Remove-MpPreference` .

> [!TIP]
> Pour plus d’informations, [voir Windows Defender API WMIv2.](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

<a id="man-tools"></a>

### <a name="use-the-windows-security-app-to-configure-file-name-folder-or-file-extension-exclusions"></a>Utiliser l’Sécurité Windows pour configurer les exclusions de nom de fichier, de dossier ou d’extension de fichier

Pour [plus d’instructions, voir Ajouter des exclusions Sécurité Windows’application.](microsoft-defender-security-center-antivirus.md)

<a id="wildcards"></a>

## <a name="use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Utiliser des caractères génériques dans les listes d’exclusion de nom de fichier et de dossier ou d’extension

Vous pouvez utiliser l’astérisque, le point d’interrogation ou les variables d’environnement `*` `?` (par exemple) comme caractères génériques lors de la définition d’éléments dans la liste d’exclusion du nom de fichier ou du chemin d’accès du `%ALLUSERSPROFILE%` dossier. La façon dont ces caractères génériques sont interprétés diffère de leur utilisation habituelle dans d’autres applications et langues. Veillez à lire cette section pour comprendre leurs limitations spécifiques.

> [!IMPORTANT]
> Il existe des limitations clés et des scénarios d’utilisation pour ces caractères génériques :
>
> - L’utilisation des variables d’environnement est limitée aux variables de l’ordinateur et à celles applicables aux processus en cours d’exécution en tant que compte NT AUTHORITY\SYSTEM.
> - Vous ne pouvez pas utiliser de caractère générique à la place d’une lettre de lecteur.
> - Un astérisque dans `*` une exclusion de dossier est en place pour un dossier unique. Utilisez plusieurs instances pour `\*\` indiquer plusieurs dossiers imbrifiés avec des noms non spécifiés.
> - Actuellement, Microsoft Endpoint Configuration Manager ne prend pas en charge les caractères génériques (tels que `*` ou `?` ).
    
Le tableau suivant décrit comment les caractères génériques peuvent être utilisés et fournit quelques exemples.

<br>

|Caractère générique|Exemples|
|---|---|
|`*` (astérisque) <p> Dans **les inclusions** de nom de fichier et d’extension de fichier, l’astérisque remplace un nombre quelconque de caractères et s’applique uniquement aux fichiers du dernier dossier défini dans l’argument. <p> Dans **les exclusions de dossiers,** l’astérisque remplace un dossier unique. Utilisez plusieurs `*` dossiers avec barres obliques `\` pour indiquer plusieurs dossiers imbrmbrés. Après la correspondance du nombre de dossiers avec caractères wild carded et nommés, tous les sous-dossiers sont également inclus.|`C:\MyData\*.txt` includes `C:\MyData\notes.txt` <p> `C:\somepath\*\Data` inclut n’importe quel fichier et ses `C:\somepath\Archives\Data` sous-dossiers, `C:\somepath\Authorized\Data` ainsi que ses sous-dossiers <p> `C:\Serv\*\*\Backup` inclut n’importe quel fichier et ses `C:\Serv\Primary\Denied\Backup` sous-dossiers `C:\Serv\Secondary\Allowed\Backup` et ses sous-dossiers|
|`?` (point d’interrogation)  <p> Dans **les inclusions de** nom de fichier et d’extension de fichier, le point d’interrogation remplace un seul caractère et s’applique uniquement aux fichiers du dernier dossier défini dans l’argument. <p> Dans **les exclusions de dossiers,** le point d’interrogation remplace un seul caractère dans un nom de dossier. Après la correspondance du nombre de dossiers avec caractères wild carded et nommés, tous les sous-dossiers sont également inclus.|`C:\MyData\my?.zip` includes `C:\MyData\my1.zip` <p> `C:\somepath\?\Data` inclut `C:\somepath\P\Data` n’importe quel fichier dans et ses sous-dossiers  <p> `C:\somepath\test0?\Data` inclut n’importe `C:\somepath\test01\Data` quel fichier et ses sous-dossiers|
|Variables d’environnement <p> La variable définie est remplie en tant que chemin d’accès lorsque l’exclusion est évaluée.|`%ALLUSERSPROFILE%\CustomLogFiles` inclut `C:\ProgramData\CustomLogFiles\Folder1\file1.txt`|

> [!IMPORTANT]
> Si vous mélangez un argument d’exclusion de fichier avec un argument d’exclusion de dossier, les règles s’arrêteront à la correspondance d’argument de fichier dans le dossier de correspondance et ne rechercheront pas de correspondances de fichiers dans les sous-dossiers.
>
> Par exemple, vous pouvez exclure tous les fichiers qui commencent par « date » dans les dossiers et à l’aide de `c:\data\final\marked` `c:\data\review\marked` l’argument de règle `c:\data\*\marked\date*` .
>
> Toutefois, cet argument ne correspond à aucun fichier des sous-dossiers sous `c:\data\final\marked` ou `c:\data\review\marked` .

<a id="review"></a>

### <a name="system-environment-variables"></a>Variables d’environnement système

Le tableau suivant répertorie et décrit les variables d’environnement de compte système.

    
|Cette variable d’environnement système...|Redirige vers cette|
|---|---|
|`%APPDATA%`|`C:\Users\UserName.DomainName\AppData\Roaming`|
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
|`%USERPROFILE%`|`C:\Windows\System32\config\systemprofile`|
|`%USERPROFILE%\AppData\Local`|`C:\Windows\System32\config\systemprofile\AppData\Local`|
|`%USERPROFILE%\AppData\LocalLow`|`C:\Windows\System32\config\systemprofile\AppData\LocalLow`|
|`%USERPROFILE%\AppData\Roaming`|`C:\Windows\System32\config\systemprofile\AppData\Roaming`|

## <a name="review-the-list-of-exclusions"></a>Passer en revue la liste des exclusions

Vous pouvez récupérer les éléments de la liste d’exclusions à l’aide de l’une des méthodes suivantes :

- [Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
- [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies)
- MpCmdRun
- PowerShell
- [Sécurité Windows application](microsoft-defender-security-center-antivirus.md)

> [!IMPORTANT]
> Les modifications apportées  aux listes d’exclusions avec la stratégie de groupe s’afficheront dans les listes de [l Sécurité Windows app.](microsoft-defender-security-center-antivirus.md)
>
> Les modifications apportées dans l Sécurité Windows’application **ne s’afficheront pas** dans les listes de stratégie de groupe.

Si vous utilisez PowerShell, vous pouvez récupérer la liste de deux manières :

- Récupérez l’état de toutes Antivirus Microsoft Defender préférences. Chaque liste est affichée sur des lignes distinctes, mais les éléments de chaque liste sont combinés dans la même ligne.
- Écrivez l’état de toutes les préférences dans une variable et utilisez cette variable pour appeler uniquement la liste spécifique qui vous intéresse. Chaque utilisation `Add-MpPreference` est écrite sur une nouvelle ligne.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>Valider la liste d’exclusions à l’aide de MpCmdRun

Pour vérifier les exclusions avec l’outil de ligne de commande [dédié mpcmdrun.exe, ](./command-line-arguments-microsoft-defender-antivirus.md?branch=v-anbic-wdav-new-mpcmdrun-options)utilisez la commande suivante :

```DOS
Start, CMD (Run as admin)
cd "%programdata%\microsoft\windows defender\platform"
cd 4.18.1812.3 (Where 4.18.1812.3 is this month's MDAV "Platform Update".)
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> La vérification des exclusions avec MpCmdRun nécessite Antivirus Microsoft Defender CAMP version 4.18.1812.3 (publiée en décembre 2018) ou version ultérieure.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>Passer en revue la liste des exclusions avec toutes les autres préférences Antivirus Microsoft Defender à l’aide de PowerShell

Utilisez la cmdlet suivante :

```PowerShell
Get-MpPreference
```

Dans l’exemple suivant, les éléments contenus dans la `ExclusionExtension` liste sont mis en surbrillant :

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="Sortie PowerShell pour Get-MpPreference.":::

Pour plus d’informations, voir [Utiliser les cmdlets PowerShell pour configurer et gérer l'Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et [Cmdlets Defender](/powershell/module/defender/).

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>Récupérer une liste d’exclusions spécifique à l’aide de PowerShell

Utilisez l’extrait de code suivant (entrez chaque ligne en tant que commande distincte) ; remplacez **WDAVprefs** par l’étiquette que vous souhaitez nommer la variable :

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionExtension
$WDAVprefs.ExclusionPath
```

Dans l’exemple suivant, la liste est divisée en nouvelles lignes pour chaque utilisation de la `Add-MpPreference` cmdlet :

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="Sortie PowerShell affichant uniquement les entrées de la liste d’exclusions.":::

Pour plus d’informations, voir [Utiliser les cmdlets PowerShell pour configurer et gérer l'Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et [Cmdlets Defender](/powershell/module/defender/).

<a id="validate"></a>

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>Valider les listes d’exclusions avec le fichier de test EICAR

Vous pouvez vérifier que vos listes d’exclusions fonctionnent à l’aide de PowerShell avec la cmdlet ou la classe WebClient .NET pour télécharger `Invoke-WebRequest` un fichier de test.

Dans l’extrait de code PowerShell suivant, remplacez-le par un fichier conforme `test.txt` à vos règles d’exclusion. Par exemple, si vous avez exclu `.testing` l’extension, `test.txt` remplacez par `test.testing` . Si vous testez un chemin d’accès, veillez à exécuter la cmdlet dans ce chemin d’accès.

```PowerShell
Invoke-WebRequest "http://www.eicar.org/download/eicar.com.txt" -OutFile "test.txt"
```

Si Antivirus Microsoft Defender signale un programme malveillant, la règle ne fonctionne pas. Si aucun programme malveillant n’est détecté et que le fichier téléchargé existe, l’exclusion fonctionne. Vous pouvez ouvrir le fichier pour confirmer que le contenu est identique à ce qui est décrit sur le site web du fichier [de test EICAR.](http://www.eicar.org/86-0-Intended-use.html)

Vous pouvez également utiliser le code PowerShell suivant, qui appelle la classe WebClient .NET pour télécharger le fichier de test , comme avec l’cmdlet ; remplacer par un fichier conforme à la règle que vous validez `Invoke-WebRequest` `c:\test.txt` :

```PowerShell
$client = new-object System.Net.WebClient
$client.DownloadFile("http://www.eicar.org/download/eicar.com.txt","c:\test.txt")
```

Si vous n’avez pas accès à Internet, vous pouvez créer votre propre fichier de test EICAR en écrivant la chaîne EICAR dans un nouveau fichier texte avec la commande PowerShell suivante :

```PowerShell
[io.file]::WriteAllText("test.txt",'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*')
```

Vous pouvez également copier la chaîne dans un fichier texte vierge et essayer de l’enregistrer avec le nom de fichier ou dans le dossier que vous tentez d’exclure.

## <a name="see-also"></a>Voir aussi

- [Configurer et valider des exclusions dans Antivirus Microsoft Defender analyses](configure-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer des exclusions Antivirus Microsoft Defender sur Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Erreurs courantes à éviter lors de la définition d’exclusions](common-exclusion-mistakes-microsoft-defender-antivirus.md)
