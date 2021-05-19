---
title: Configurer les options d’analyse pour Antivirus Microsoft Defender
description: Vous pouvez configurer Microsoft Defender AV pour analyser les fichiers de stockage de messagerie, les points de stockage ou d’analyse, les fichiers réseau et les fichiers archivés (tels que les fichiers .zip).
keywords: analyses avancées, analyse, e-mail, archive, zip, rar, archive, analyse de l’analyse
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.date: 05/06/2021
ms.topic: how-to
ms.openlocfilehash: 1942531b77df1c2bd9408815d3ad54b4b7211e8b
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52538398"
---
# <a name="configure-microsoft-defender-antivirus-scanning-options"></a>Configurer les options d’analyse de l’antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

## <a name="use-microsoft-intune-to-configure-scanning-options"></a>Utiliser Microsoft Intune pour configurer les options d’analyse

Consultez [Configurer des paramètres de restriction d’appareils dans Microsoft Intune](/intune/device-restrictions-configure) et [Paramètres de restriction d’appareil de l’Antivirus Microsoft Defender pour Windows 10](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) pour obtenir des détails supplémentaires.

## <a name="use-microsoft-endpoint-manager-to-configure-scanning-options"></a>Utiliser Microsoft Endpoint Manager pour configurer les options d’analyse

Découvrez comment créer et déployer des stratégies [de logiciel anti-programme](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) malveillant : analyser les paramètres pour plus d’informations sur la configuration Microsoft Endpoint Manager (branche actuelle).

## <a name="use-group-policy-to-configure-scanning-options"></a>Utiliser la stratégie de groupe pour configurer les options d’analyse

Pour configurer les paramètres de stratégie de groupe décrits dans le tableau suivant :

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, cliquez sur **Configuration** ordinateur et cliquez **sur Modèles d’administration.**

3. Développez  **l’arborescence Windows composants > Antivirus Microsoft Defender** puis l’emplacement spécifié dans le tableau ci-dessous.

4. Double-cliquez sur le paramètre **de** stratégie comme indiqué dans le tableau ci-dessous et définissez l’option sur la configuration souhaitée. Cliquez **sur OK,** puis répétez l’une des autres configurations.

| Description | Emplacement et paramètre | Paramètre par défaut (s’il n’est pas configuré) | Paramètre PowerShell `Set-MpPreference` ou propriété WMI pour la `MSFT_MpPreference` classe |
|---|---|---|---|
| Analyse du courrier électronique : [consultez les limitations de l’analyse du courrier électronique](#ref1)| Analyser > activer l’analyse du courrier électronique | Désactivé | `-DisableEmailScanning` |
|Analyser [les points d’analyse](/windows/win32/fileio/reparse-points) | Analyser > activer l’analyse des points d’analyse | Désactivé | Non disponible |
| Analyser les lecteurs réseau mappés | Analyser > exécuter une analyse complète sur des lecteurs réseau mappés | Désactivé | `-DisableScanningMappedNetworkDrivesForFullScan`|
 Analyser les fichiers d’archive (tels .zip ou .rar fichiers). La [liste d’exclusions des extensions](configure-extension-file-exclusions-microsoft-defender-antivirus.md) est prioritaire sur ce paramètre. | Analyser > fichiers archivés | Activé | `-DisableArchiveScanning` |
| Analyser les fichiers sur le réseau | Analyser les > fichiers réseau | Désactivé | `-DisableScanningNetworkFiles` |
| Analyser les exécutables packés | Analyser > les exécutables packés d’analyse | Activé | Non disponible |
| Analyser les lecteurs amovibles uniquement pendant les analyses complètes | Analyser > analyser les lecteurs amovibles | Désactivé | `-DisableRemovableDriveScanning` |
| Spécifier le niveau de sous-dossiers dans un dossier d’archivage à analyser | Analyser > spécifier la profondeur maximale pour analyser les fichiers archivés | 0 | Non disponible |
| Spécifiez la charge processeur maximale (en pourcentage) pendant une analyse. Remarque : il ne s’agit pas d’une limite difficile, mais plutôt d’une recommandation pour que le moteur d’analyse ne dépasse pas ce maximum en moyenne. L’exécuter manuellement ignore ce paramètre et s’exécute sans limites de processeur. | Analyser > spécifier le pourcentage maximal d’utilisation du processeur au cours d’une analyse | 50 |  `-ScanAvgCPULoadFactor` |
| Spécifiez la taille maximale (en kilo-octets) des fichiers d’archivage qui doivent être analysés. La valeur par défaut, **0**, ne s’applique pas à la limite | Analyser > spécifier la taille maximale des fichiers d’archivage à analyser | Sans limite | Non disponible |
| Configurer une faible priorité du processeur pour les analyses programmées | Analyser > configurer une faible priorité du processeur pour les analyses programmées | Désactivé | Non disponible |
 
> [!NOTE]
> Si la protection en temps réel est désactivée, les fichiers sont analysés avant d’être accessibles et exécutés. L’étendue d’analyse inclut tous les fichiers, y compris les fichiers sur les supports amovibles montés, tels que les lecteurs USB. Si l’appareil qui effectue l’analyse dispose d’une protection en temps réel ou d’une protection à l’accès, l’analyse inclut également les partages réseau.

## <a name="use-powershell-to-configure-scanning-options"></a>Utiliser PowerShell pour configurer les options d’analyse

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir Gérer les Antivirus Microsoft Defender avec les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) et les [cmdlets](/powershell/module/defender/) Defender.

## <a name="use-wmi-to-configure-scanning-options"></a>Utiliser WMI pour configurer les options d’analyse

Pour utiliser des classes WMI, [voir Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="ref1"></a>

## <a name="email-scanning-limitations"></a>Limitations de l’analyse du courrier électronique

L’analyse du courrier électronique permet d’analyser les fichiers de messagerie utilisés par Outlook clients de messagerie et d’autres clients de messagerie lors d’analyses à la demande et programmées. Les objets incorporés dans un fichier de courrier électronique (tels que les pièces jointes et les fichiers archivés) sont également analysés. Les types de format de fichier suivants peuvent être analysés et corrigés :

- DBX
- MBX
- MIME

Les fichiers PST utilisés par Outlook 2003 ou une ancienne génération (lorsque le type d’archive est non unicode) seront également analysés, mais Windows Defender ne peut pas corriger les menaces détectées dans les fichiers PST.

Si Antivirus Microsoft Defender une menace à l’intérieur d’un e-mail, elle affiche les informations suivantes pour vous aider à identifier le courrier électronique compromis, afin que vous pouvez corriger la menace manuellement :

- Sujet de l’e-mail
- Nom de la pièce jointe

## <a name="related-topics"></a>Voir aussi

- [Personnaliser, lancer et passer en revue les résultats des analyses et Antivirus Microsoft Defender correction](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Configurer et exécuter des analyses à la demande avec l’antivirus Microsoft Defender](run-scan-microsoft-defender-antivirus.md).
- [Configurer des analyses de Antivirus Microsoft Defender programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
