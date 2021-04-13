---
title: Configurer les options d'analyse pour Microsoft Defender AV
description: Vous pouvez configurer Microsoft Defender AV pour analyser les fichiers de stockage de messagerie, les points de stockage ou d'analyse, les fichiers réseau et les fichiers archivés (tels que les fichiers .zip).
keywords: analyses avancées, analyse, e-mail, archive, zip, rar, archive, analyse de l'analyse
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 625c84e79efe53cae2bc8f511726ad3f384ea505
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690458"
---
# <a name="configure-microsoft-defender-antivirus-scanning-options"></a>Configurer les options d'analyse de l'Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

## <a name="use-microsoft-intune-to-configure-scanning-options"></a>Utiliser Microsoft Intune pour configurer les options d'analyse

Pour plus d'informations, voir Configurer les paramètres de restriction d'appareil dans [Microsoft Intune](/intune/device-restrictions-configure) et l'Antivirus Microsoft Defender pour [Windows 10 dans Intune.](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

## <a name="use-microsoft-endpoint-manager-to-configure-scanning-options"></a>Utiliser Microsoft Endpoint Manager pour configurer les options d'analyse

Découvrez comment créer et déployer des stratégies [anti-programme](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) malveillant : analyser les paramètres pour plus d'informations sur la configuration de Microsoft Endpoint Manager (branche actuelle).

## <a name="use-group-policy-to-configure-scanning-options"></a>Utiliser la stratégie de groupe pour configurer les options d'analyse

Pour configurer les paramètres de stratégie de groupe décrits dans le tableau suivant :

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l'Éditeur de gestion des stratégies de** groupe, cliquez sur **Configuration** ordinateur et cliquez **sur Modèles d'administration.**

3. Développez l'arborescence **des composants Windows > Antivirus Microsoft Defender,** puis l'emplacement spécifié dans le tableau ci-dessous. 

4. Double-cliquez sur le paramètre **de** stratégie comme indiqué dans le tableau ci-dessous et définissez l'option sur la configuration souhaitée. Cliquez **sur OK,** puis répétez l'une des autres configurations.

Description | Emplacement et paramètre | Paramètre par défaut (s'il n'est pas configuré) | Paramètre PowerShell `Set-MpPreference` ou propriété WMI pour la `MSFT_MpPreference` classe
---|---|---|---
Analyse du courrier électronique : [consultez les limitations de l'analyse du courrier électronique](#ref1)| Analyser > activer l'analyse du courrier électronique | Désactivé | `-DisableEmailScanning`
Analyser [les points d'analyse](/windows/win32/fileio/reparse-points) | Analyser > activer l'analyse des points d'analyse | Désactivé | Non disponible
Analyser les lecteurs réseau mappés | Analyser > exécuter une analyse complète sur des lecteurs réseau mappés | Désactivé | `-DisableScanningMappedNetworkDrivesForFullScan`
 Analyser les fichiers d'archive (tels que les fichiers .zip ou .rar). La [liste d'exclusions des extensions](configure-extension-file-exclusions-microsoft-defender-antivirus.md) est prioritaire sur ce paramètre. | Analyser > fichiers archivés | Activé | `-DisableArchiveScanning`
Analyser les fichiers sur le réseau | Analyser les > fichiers réseau | Désactivé | `-DisableScanningNetworkFiles`
Analyser les exécutables packés | Analyser > les exécutables packés d'analyse | Activé | Non disponible
Analyser les lecteurs amovibles uniquement pendant les analyses complètes | Analyser > analyser les lecteurs amovibles | Désactivé | `-DisableRemovableDriveScanning`
Spécifier le niveau de sous-dossiers dans un dossier d'archivage à analyser | Analyser > spécifier la profondeur maximale pour analyser les fichiers archivés | 0 | Non disponible
 Spécifiez la charge processeur maximale (en pourcentage) au cours d'une analyse. Remarque : il ne s'agit pas d'une limite difficile, mais plutôt d'une recommandation pour que le moteur d'analyse ne dépasse pas ce maximum en moyenne. | Analyser > spécifier le pourcentage maximal d'utilisation du processeur au cours d'une analyse | 50 |  `-ScanAvgCPULoadFactor`
 Spécifiez la taille maximale (en kilo-octets) des fichiers d'archivage qui doivent être analysés. La valeur par défaut, **0**, ne s'applique pas à la limite | Analyser > spécifier la taille maximale des fichiers d'archivage à analyser | Sans limite | Non disponible
 Configurer une faible priorité du processeur pour les analyses programmées | Analyser > configurer une faible priorité du processeur pour les analyses programmées | Désactivé | Non disponible
 
> [!NOTE]
> Si la protection en temps réel est désactivée, les fichiers sont analysés avant d'être accessibles et exécutés. L'étendue d'analyse inclut tous les fichiers, y compris les fichiers sur les supports amovibles montés, tels que les lecteurs USB. Si l'appareil qui effectue l'analyse dispose d'une protection en temps réel ou d'une protection à l'accès, l'analyse inclut également les partages réseau.

## <a name="use-powershell-to-configure-scanning-options"></a>Utiliser PowerShell pour configurer les options d'analyse

Pour plus d'informations sur l'utilisation de PowerShell avec l'Antivirus Microsoft Defender, voir Gérer l'antivirus Microsoft Defender avec les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) et les [cmdlets](/powershell/module/defender/) Defender.

## <a name="use-wmi-to-configure-scanning-options"></a>Utiliser WMI pour configurer les options d'analyse

Pour utiliser des classes WMI, voir [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="ref1"></a>

## <a name="email-scanning-limitations"></a>Limitations de l'analyse du courrier électronique

L'analyse du courrier électronique permet d'analyser les fichiers de messagerie utilisés par Outlook et d'autres clients de messagerie lors d'analyses à la demande et programmées. Les objets incorporés dans un fichier de courrier électronique (tels que les pièces jointes et les fichiers archivés) sont également analysés. Les types de format de fichier suivants peuvent être analysés et corrigés :

- DBX
- MBX
- MIME

Les fichiers PST utilisés par Outlook 2003 ou une ancienne édition (où le type d'archive est non unicode) seront également analysés, mais Windows Defender ne peut pas corriger les menaces détectées dans les fichiers PST.

Si l'Antivirus Microsoft Defender détecte une menace à l'intérieur d'un e-mail, il affiche les informations suivantes pour vous aider à identifier le courrier électronique compromis, afin que vous pouvez corriger la menace manuellement :

- Sujet de l’e-mail
- Nom de la pièce jointe

## <a name="related-topics"></a>Voir aussi

- [Personnaliser, lancer et passer en revue les résultats des analyses et des corrections de l'Antivirus Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Configurer et exécuter des analyses de l'Antivirus Microsoft Defender à la demande](run-scan-microsoft-defender-antivirus.md)
- [Configurer des analyses de l'Antivirus Microsoft Defender programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)