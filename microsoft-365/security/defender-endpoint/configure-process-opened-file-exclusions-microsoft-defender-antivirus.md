---
title: Configurer des exclusions pour les fichiers ouverts par des processus spécifiques
description: Vous pouvez exclure des fichiers des analyses si elles ont été ouvertes par un processus spécifique.
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
ms.openlocfilehash: 44107228cf0e05f43484bfb88a757335fe6c2b86
ms.sourcegitcommit: e09ced3e3628bf2ccb84d205d9699483cbb4b3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2021
ms.locfileid: "60882728"
---
# <a name="configure-exclusions-for-files-opened-by-processes"></a>Configurer des exclusions pour les fichiers ouverts par des processus


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez exclure des analyses des fichiers qui ont été ouverts par des processus spécifiques Antivirus Microsoft Defender analyses. Voir [Recommandations pour définir des exclusions](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) avant de définir vos listes d’exclusions.

Cet article explique comment configurer des listes d’exclusions.

## <a name="examples-of-exclusions"></a>Exemples d’exclusions

<br/><br/>

|Exclusion|Exemple|
|---|---|
|Tout fichier sur l’ordinateur ouvert par n’importe quel processus avec un nom de fichier spécifique|La spécification `test.exe` exclurait les fichiers ouverts par : <p>`c:\sample\test.exe` <p> `d:\internal\files\test.exe`|
|Tout fichier sur l’ordinateur ouvert par un processus sous un dossier spécifique|La spécification `c:\test\sample\*` exclurait les fichiers ouverts par : <p> `c:\test\sample\test.exe` <p> `c:\test\sample\test2.exe` <p> `c:\test\sample\utility.exe`|
|Tout fichier sur l’ordinateur ouvert par un processus spécifique dans un dossier spécifique|La spécification `c:\test\process.exe` exclurait les fichiers ouverts uniquement par `c:\test\process.exe`|

Lorsque vous ajoutez un processus à la liste d’exclusions de processus, Antivirus Microsoft Defender pas analyser les fichiers ouverts par ce processus, quel que soit l’emplacement des fichiers. Toutefois, le processus proprement dit sera analysé, sauf s’il a également été ajouté à la liste [d’exclusions de fichiers.](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

Les exclusions s’appliquent uniquement à la protection et à la surveillance en temps [réel toujours en temps réel.](configure-real-time-protection-microsoft-defender-antivirus.md) Elles ne s’appliquent pas aux analyses programmées ou à la demande.

Les modifications apportées avec  la stratégie de groupe aux listes d’exclusions s’afficheront dans les listes de [l Sécurité Windows app.](microsoft-defender-security-center-antivirus.md) Toutefois, les modifications apportées dans l Sécurité Windows appapplment de groupe **ne s’afficheront** pas dans les listes de stratégie de groupe.

Vous pouvez ajouter, supprimer et examiner les listes pour les exclusions dans la stratégie de groupe, Microsoft Endpoint Configuration Manager, Microsoft Intune et avec l’application Sécurité Windows, et vous pouvez utiliser des caractères génériques pour personnaliser davantage les listes.

Vous pouvez également utiliser les cmdlets PowerShell et WMI pour configurer les listes d’exclusions, y compris la révision de vos listes.

Par défaut, les modifications locales apportées aux listes (par les utilisateurs ayant des privilèges d’administrateur, les modifications apportées avec PowerShell et WMI) sont fusionnées avec les listes telles que définies (et déployées) par la stratégie de groupe, Configuration Manager ou Intune. Les listes de stratégies de groupe sont prioritaire en cas de conflit.

Vous pouvez [configurer la façon dont les listes d’exclusions définies](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists) localement et globalement sont fusionnées pour permettre aux modifications locales de remplacer les paramètres de déploiement géré.

## <a name="configure-the-list-of-exclusions-for-files-opened-by-specified-processes"></a>Configurer la liste des exclusions pour les fichiers ouverts par des processus spécifiés

### <a name="use-microsoft-intune-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Utiliser Microsoft Intune pour exclure des analyses les fichiers qui ont été ouverts par des processus spécifiés

Consultez [Configurer des paramètres de restriction d’appareils dans Microsoft Intune](/intune/device-restrictions-configure) et [Paramètres de restriction d’appareil de l’Antivirus Microsoft Defender pour Windows 10](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) pour obtenir des détails supplémentaires.

### <a name="use-microsoft-endpoint-manager-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Utiliser Microsoft Endpoint Manager pour exclure des analyses les fichiers qui ont été ouverts par des processus spécifiés

Découvrez comment créer et déployer des stratégies de logiciel [anti-programme](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) malveillant : paramètres d’exclusion pour plus d’informations sur la configuration Microsoft Endpoint Manager (branche actuelle).

### <a name="use-group-policy-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Utiliser la stratégie de groupe pour exclure des analyses les fichiers qui ont été ouverts par des processus spécifiés

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, cliquez sur **Configuration** ordinateur et cliquez **sur Modèles d’administration.**

3. Développez l’arborescence **Windows composants \> Antivirus Microsoft Defender \> exclusions.**

4. Double-cliquez sur **Exclusions de processus** et ajoutez les exclusions :
    1. Définissez l’option **sur Activé.**
    2. Sous la section **Options,** cliquez sur **Afficher...**.
    3. Entrez chaque processus sur sa propre ligne sous la **colonne Nom de** la valeur. Consultez l’exemple de tableau pour les différents types d’exclusions de processus. Entrez **0 dans** la colonne **Valeur** pour tous les processus.

5. Cliquez sur **OK**.

### <a name="use-powershell-cmdlets-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Utiliser les cmdlets PowerShell pour exclure des analyses les fichiers qui ont été ouverts par des processus spécifiés

L’utilisation de PowerShell pour ajouter ou supprimer des exclusions pour les fichiers qui ont été ouverts par des processus nécessite l’utilisation d’une combinaison de trois cmdlets avec le `-ExclusionProcess` paramètre. Les cmdlets sont toutes dans le [module Defender.](/powershell/module/defender/)

Le format des cmdlets est :

```PowerShell
<cmdlet> -ExclusionProcess "<item>"
```

Les listes suivantes sont autorisées en tant que \<cmdlet\> :

<br/><br/>

|Action de configuration|Cmdlet PowerShell|
|---|---|
|Créer ou overwrite la liste|`Set-MpPreference`|
|Ajouter à la liste|`Add-MpPreference`|
|Supprimer des éléments de la liste|`Remove-MpPreference`|

> [!IMPORTANT]
> Si vous avez créé une liste, avec ou , en utilisant à nouveau la `Set-MpPreference` `Add-MpPreference` `Set-MpPreference` cmdlet, la liste existante est réécrite.

Par exemple, l’extrait de code suivant entraîne l’exclusion par les analyses de l’Antivirus Microsoft Defender de tout fichier ouvert par le processus spécifié :

```PowerShell
Add-MpPreference -ExclusionProcess "c:\internal\test.exe"
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir Gérer l’antivirus avec les cmdlets PowerShell et [Antivirus Microsoft Defender cmdlets.](/powershell/module/defender)

### <a name="use-windows-management-instruction-wmi-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Utiliser Windows Management Instruction (WMI) pour exclure des analyses les fichiers qui ont été ouverts par des processus spécifiés

Utilisez les [ **méthodes Set,** **Add** et **Remove** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ExclusionProcess
```

L’utilisation **de Set**, **Add** et **Remove** est analogue à leurs équivalents dans PowerShell : , `Set-MpPreference` et `Add-MpPreference` `Remove-MpPreference` .

Pour plus d’informations et les paramètres autorisés, [voir Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

### <a name="use-the-windows-security-app-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Utiliser l’Sécurité Windows pour exclure des analyses les fichiers qui ont été ouverts par des processus spécifiés

Pour [plus d’instructions, voir Ajouter des exclusions Sécurité Windows’application.](microsoft-defender-security-center-antivirus.md)

## <a name="use-wildcards-in-the-process-exclusion-list"></a>Utiliser des caractères génériques dans la liste d’exclusions de processus

L’utilisation de caractères génériques dans la liste d’exclusions de processus est différente de leur utilisation dans d’autres listes d’exclusions.

En particulier, vous ne pouvez pas utiliser le caractère générique de point d’interrogation ( ) et le caractère générique astérisque ( ) ne peut être utilisé qu’à la fin d’un `?` `*` chemin d’accès complet. Vous pouvez toujours utiliser des variables d’environnement (par exemple) comme caractères génériques lors de la définition d’éléments dans la liste `%ALLUSERSPROFILE%` d’exclusions de processus.

Le tableau suivant décrit comment les caractères génériques peuvent être utilisés dans la liste d’exclusions de processus :

<br/><br/>

|Caractère générique|Exemple d’utilisation|Exemples de correspondances|
|---|---|---|
|`*` (astérisque) <p> Remplace un nombre quelconque de caractères|`C:\MyData\*`|Tout fichier ouvert par `C:\MyData\file.exe`|
|Variables d’environnement <p> La variable définie est remplie en tant que chemin d’accès lorsque l’exclusion est évaluée|`%ALLUSERSPROFILE%\CustomLogFiles\file.exe`|Tout fichier ouvert par `C:\ProgramData\CustomLogFiles\file.exe`|

## <a name="review-the-list-of-exclusions"></a>Passer en revue la liste des exclusions

Vous pouvez récupérer les éléments de la liste d’exclusions avec MpCmdRun, PowerShell, [Microsoft Endpoint Configuration Manager,](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) [Intune](/intune/device-restrictions-configure)ou [l’application Sécurité Windows.](microsoft-defender-security-center-antivirus.md)

Si vous utilisez PowerShell, vous pouvez récupérer la liste de deux manières :

- Récupérez l’état de toutes Antivirus Microsoft Defender préférences. Chacune des listes s’affichera sur des lignes distinctes, mais les éléments de chaque liste seront combinés dans la même ligne.
- Écrivez l’état de toutes les préférences dans une variable et utilisez cette variable pour appeler uniquement la liste spécifique qui vous intéresse. Chaque utilisation `Add-MpPreference` est écrite sur une nouvelle ligne.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>Valider la liste d’exclusions à l’aide de MpCmdRun

Pour vérifier les exclusions avec l’outil en ligne de commande [mpcmdrun.exe, ](./command-line-arguments-microsoft-defender-antivirus.md?branch=v-anbic-wdav-new-mpcmdrun-options)utilisez la commande suivante :

```DOS
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> La vérification des exclusions avec MpCmdRun nécessite Antivirus Microsoft Defender CAMP version 4.18.1812.3 (publiée en décembre 2018) ou ultérieure.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>Passer en revue la liste des exclusions avec toutes les autres préférences Antivirus Microsoft Defender à l’aide de PowerShell

Utilisez l’cmdlet suivante :

```PowerShell
Get-MpPreference
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter des [cmdlets](/powershell/module/defender) Antivirus Microsoft Defender et Defender.

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>Récupérer une liste d’exclusions spécifique à l’aide de PowerShell

Utilisez l’extrait de code suivant (entrez chaque ligne en tant que commande distincte) ; remplacez **WDAVprefs** par l’étiquette que vous souhaitez nommer la variable :

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionProcess
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter des [cmdlets](/powershell/module/defender) Antivirus Microsoft Defender et Defender.

## <a name="related-articles"></a>Articles connexes

- [Configurer et valider des exclusions dans Antivirus Microsoft Defender analyses](configure-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions en fonction du nom de fichier, de l’extension et de l’emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer des exclusions Antivirus Microsoft Defender sur Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Erreurs courantes à éviter lors de la définition d’exclusions](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Personnaliser, lancer et passer en revue les résultats des analyses et Antivirus Microsoft Defender correction](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
