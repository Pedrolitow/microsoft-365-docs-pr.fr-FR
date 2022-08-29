---
title: Configurer des exclusions pour les fichiers ouverts par des processus spécifiques
description: Vous pouvez exclure des fichiers des analyses s’ils ont été ouverts par un processus spécifique.
keywords: Antivirus Microsoft Defender, processus, exclusion, fichiers, analyses
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 897a443be70afb8248e6a49f24f32b678060b976
ms.sourcegitcommit: d09eb780dc41a01796eb8137fbe9267231af6746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2022
ms.locfileid: "67388746"
---
# <a name="configure-exclusions-for-files-opened-by-processes"></a>Configurer des exclusions pour les fichiers ouverts par des processus


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows 

Vous pouvez exclure des fichiers ouverts par des processus spécifiques des analyses antivirus Microsoft Defender. Consultez [Recommandations pour définir des exclusions](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) avant de définir vos listes d’exclusions.

Cet article explique comment configurer des listes d’exclusions.

## <a name="examples-of-exclusions"></a>Exemples d’exclusions

|Exclusion|Exemple|
|---|---|
|Tout fichier sur l’ordinateur ouvert par n’importe quel processus avec un nom de fichier spécifique|La spécification exclut les `test.exe` fichiers ouverts par : <p>`c:\sample\test.exe` <p> `d:\internal\files\test.exe`|
|Tout fichier sur l’ordinateur ouvert par n’importe quel processus sous un dossier spécifique|La spécification exclut les `c:\test\sample\*` fichiers ouverts par : <p> `c:\test\sample\test.exe` <p> `c:\test\sample\test2.exe` <p> `c:\test\sample\utility.exe`|
|Tout fichier sur l’ordinateur ouvert par un processus spécifique dans un dossier spécifique|Spécifier `c:\test\process.exe` exclurait les fichiers ouverts uniquement par `c:\test\process.exe`|

Lorsque vous ajoutez un processus à la liste d’exclusion de processus, l’Antivirus Microsoft Defender n’analyse pas les fichiers ouverts par ce processus, quel que soit l’emplacement des fichiers. Toutefois, le processus lui-même est analysé, sauf s’il a également été ajouté à la [liste d’exclusions de fichiers](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Les exclusions s’appliquent uniquement à [la protection et à la surveillance en temps réel always-on](configure-real-time-protection-microsoft-defender-antivirus.md). Elles ne s’appliquent pas aux analyses planifiées ou à la demande.

Les modifications apportées avec stratégie de groupe aux listes d’exclusion **s’affichent** dans les listes de [l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md). Toutefois, les modifications apportées à l’application Sécurité Windows **ne s’affichent pas** dans les listes stratégie de groupe.

Vous pouvez ajouter, supprimer et examiner les listes pour les exclusions dans stratégie de groupe, microsoft endpoint Configuration Manager, Microsoft Intune et avec l’application Sécurité Windows, et vous pouvez utiliser des caractères génériques pour personnaliser davantage les listes.

Vous pouvez également utiliser les applets de commande PowerShell et WMI pour configurer les listes d’exclusions, notamment en examinant vos listes.

Par défaut, les modifications locales apportées aux listes (par les utilisateurs disposant de privilèges d’administrateur ; les modifications apportées avec PowerShell et WMI) sont fusionnées avec les listes telles que définies (et déployées) par stratégie de groupe, Configuration Manager ou Intune. Les listes stratégie de groupe sont prioritaires en cas de conflits.

Vous pouvez [configurer la fusion des listes d’exclusions définies localement et globalement](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists) pour permettre aux modifications locales de remplacer les paramètres de déploiement managé.

## <a name="configure-the-list-of-exclusions-for-files-opened-by-specified-processes"></a>Configurer la liste des exclusions pour les fichiers ouverts par les processus spécifiés

### <a name="use-microsoft-intune-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Utilisez Microsoft Intune pour exclure des analyses les fichiers qui ont été ouverts par des processus spécifiés

Consultez [Configurer des paramètres de restriction d’appareils dans Microsoft Intune](/intune/device-restrictions-configure) et [Paramètres de restriction d’appareil de l’Antivirus Microsoft Defender pour Windows 10](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) pour obtenir des détails supplémentaires.

### <a name="use-microsoft-endpoint-manager-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Utiliser Microsoft Endpoint Manager pour exclure des analyses les fichiers qui ont été ouverts par des processus spécifiés

Découvrez [comment créer et déployer des stratégies anti-programme malveillant : Paramètres d’exclusion](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) pour plus d’informations sur la configuration de Microsoft Endpoint Manager (current branch).

### <a name="use-group-policy-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Utiliser stratégie de groupe pour exclure des analyses les fichiers qui ont été ouverts par des processus spécifiés

1. Sur votre ordinateur de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, **accédez à Configuration de l’ordinateur**, puis cliquez sur **Modèles d’administration**.

3. Développez l’arborescence vers **les composants Windows exclusions \> de l’antivirus \> Microsoft Defender**.

4. Double-cliquez sur **Exclusions de processus** et ajoutez les exclusions :
    1. Définissez l’option **sur Activé**.
    2. Dans la section **Options** , cliquez sur **Afficher...**.
    3. Entrez chaque processus sur sa propre ligne sous la colonne **Nom de** la valeur. Consultez l’exemple de tableau pour connaître les différents types d’exclusions de processus. Entrez **0** dans la colonne **Valeur** pour tous les processus.

5. Cliquez sur **OK**.

### <a name="use-powershell-cmdlets-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Utiliser des applets de commande PowerShell pour exclure des analyses les fichiers qui ont été ouverts par des processus spécifiés

L’utilisation de PowerShell pour ajouter ou supprimer des exclusions pour les fichiers qui ont été ouverts par des processus nécessite l’utilisation d’une combinaison de trois applets de commande avec le `-ExclusionProcess` paramètre. Les applets de commande se trouvent toutes dans le [module Defender](/powershell/module/defender/).

Le format des applets de commande est le suivant :

```PowerShell
<cmdlet> -ExclusionProcess "<item>"
```

Les éléments suivants sont autorisés en tant que :\<cmdlet\>

|Action de configuration|Applet de commande PowerShell|
|---|---|
|Créer ou remplacer la liste|`Set-MpPreference`|
|Ajouter à la liste|`Add-MpPreference`|
|Supprimer des éléments de la liste|`Remove-MpPreference`|

> [!IMPORTANT]
> Si vous avez créé une liste, avec `Set-MpPreference` ou `Add-MpPreference`, l’utilisation de l’applet `Set-MpPreference` de commande remplacera à nouveau la liste existante.

Par exemple, l’extrait de code suivant entraîne l’exclusion des analyses antivirus Microsoft Defender de tout fichier ouvert par le processus spécifié :

```PowerShell
Add-MpPreference -ExclusionProcess "c:\internal\test.exe"
```

Pour plus d’informations sur l’utilisation de PowerShell avec l’antivirus Microsoft Defender, consultez Gérer l’antivirus avec les applets de commande PowerShell et [les applets de commande antivirus Microsoft Defender](/powershell/module/defender).

### <a name="use-windows-management-instruction-wmi-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Utiliser l’instruction de gestion Windows (WMI) pour exclure des analyses les fichiers qui ont été ouverts par des processus spécifiés

Utilisez les [méthodes **Set**, **Add** et **Remove** de la classe **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ExclusionProcess
```

L’utilisation de **Set**, **Add** et **Remove** est analogue à leurs équivalents dans PowerShell : `Set-MpPreference`, `Add-MpPreference`et `Remove-MpPreference`.

Pour plus d’informations et les paramètres autorisés, consultez [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

### <a name="use-the-windows-security-app-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Utiliser l’application Sécurité Windows pour exclure des analyses les fichiers qui ont été ouverts par des processus spécifiés

Pour obtenir des instructions, consultez [Ajouter des exclusions dans l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md).

## <a name="use-wildcards-in-the-process-exclusion-list"></a>Utiliser des caractères génériques dans la liste d’exclusion de processus

L’utilisation de caractères génériques dans la liste d’exclusion de processus est différente de leur utilisation dans d’autres listes d’exclusions.

En particulier, vous ne pouvez pas utiliser le caractère générique de point d’interrogation (`?`) et le caractère générique astérisque (`*`) ne peut être utilisé qu’à la fin d’un chemin d’accès complet. Vous pouvez toujours utiliser des variables d’environnement (telles que `%ALLUSERSPROFILE%`) comme caractères génériques lors de la définition d’éléments dans la liste d’exclusion de processus.

Le tableau suivant décrit comment les caractères génériques peuvent être utilisés dans la liste d’exclusion de processus :

|Caractère générique|Exemple d’utilisation|Exemples de correspondances|
|---|---|---|
|`*` (astérisque) <p> Remplace un nombre quelconque de caractères|`C:\MyData\*`|Tout fichier ouvert par `C:\MyData\file.exe`|
|Variables d’environnement <p> La variable définie est remplie en tant que chemin d’accès lorsque l’exclusion est évaluée|`%ALLUSERSPROFILE%\CustomLogFiles\file.exe`|Tout fichier ouvert par `C:\ProgramData\CustomLogFiles\file.exe`|

## <a name="review-the-list-of-exclusions"></a>Examiner la liste des exclusions

Vous pouvez récupérer les éléments de la liste d’exclusion avec MpCmdRun, PowerShell, [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings), [Intune](/intune/device-restrictions-configure) ou [l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md).

Si vous utilisez PowerShell, vous pouvez récupérer la liste de deux manières :

- Récupérez l’état de toutes les préférences de l’Antivirus Microsoft Defender. Chacune des listes s’affiche sur des lignes distinctes, mais les éléments de chaque liste sont combinés dans la même ligne.
- Écrivez l’état de toutes les préférences dans une variable et utilisez cette variable pour appeler uniquement la liste spécifique qui vous intéresse. Chaque utilisation est `Add-MpPreference` écrite dans une nouvelle ligne.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>Valider la liste d’exclusion à l’aide de MpCmdRun

Pour vérifier les exclusions avec [l’outil de ligne de commande dédié mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md?branch=v-anbic-wdav-new-mpcmdrun-options), utilisez la commande suivante :

```DOS
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> La vérification des exclusions avec MpCmdRun nécessite Microsoft Defender Antivirus CAMP version 4.18.1812.3 (publiée en décembre 2018) ou version ultérieure.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>Passez en revue la liste des exclusions avec toutes les autres préférences antivirus Microsoft Defender à l’aide de PowerShell

Utilisez l’applet de commande suivante :

```PowerShell
Get-MpPreference
```

Pour plus d’informations sur l’utilisation de [PowerShell avec l’antivirus Microsoft Defender, consultez Utiliser les applets de commande PowerShell pour configurer et exécuter l’Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et [l’Antivirus Microsoft Defender](/powershell/module/defender) .

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>Récupérer une liste d’exclusions spécifique à l’aide de PowerShell

Utilisez l’extrait de code suivant (entrez chaque ligne comme commande distincte) ; remplacez **WDAVprefs** par l’étiquette que vous souhaitez nommer la variable :

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionProcess
```

Pour plus d’informations sur l’utilisation de [PowerShell avec l’antivirus Microsoft Defender, consultez Utiliser les applets de commande PowerShell pour configurer et exécuter l’Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et [l’Antivirus Microsoft Defender](/powershell/module/defender) .

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-articles"></a>Articles connexes

- [Configurer et valider les exclusions dans les analyses de l’Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions en fonction du nom de fichier, de l’extension et de l’emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer les exclusions de l’Antivirus Microsoft Defender sur Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Erreurs courantes à éviter lors de la définition d’exclusions](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Personnaliser, lancer et passer en revue les résultats des analyses et des corrections de l’Antivirus Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
