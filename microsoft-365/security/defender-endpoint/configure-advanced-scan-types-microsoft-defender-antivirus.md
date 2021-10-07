---
title: Configurer les options d’analyse pour Antivirus Microsoft Defender
description: Vous pouvez configurer Microsoft Defender AV pour analyser les fichiers de stockage de messagerie, les points de stockage ou d’analyse, les fichiers réseau et les fichiers archivés (tels que les fichiers .zip).
keywords: analyses avancées, analyse, e-mail, archive, zip, rar, archive, analyse de l’analyse
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
ms.date: 09/14/2021
ms.collection: M365-security-compliance
ms.topic: how-to
ms.openlocfilehash: 3ce0945fc687623c5f5fd7ba26e57ad191ec3ecb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60207964"
---
# <a name="configure-microsoft-defender-antivirus-scanning-options"></a>Configurer les options d’analyse de l’antivirus Microsoft Defender

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

## <a name="use-microsoft-intune-to-configure-scanning-options"></a>Utiliser Microsoft Intune pour configurer les options d’analyse

Pour plus d’informations, voir Configurer les [paramètres](/intune/device-restrictions-configure) de restriction d’appareil Microsoft Intune et Antivirus Microsoft Defender paramètres de restriction d’appareil pour Windows 10 [dans Intune.](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

## <a name="use-microsoft-endpoint-manager-to-configure-scanning-options"></a>Utiliser Microsoft Endpoint Manager pour configurer les options d’analyse

Pour plus d’informations sur la configuration Microsoft Endpoint Manager (branche actuelle), voir Comment créer et déployer des stratégies de logiciel [anti-programme](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings)malveillant : Analyser les paramètres .

## <a name="use-group-policy-to-configure-scanning-options"></a>Utiliser la stratégie de groupe pour configurer les options d’analyse

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier.**

3. Dans **l’Éditeur de gestion des stratégies de** groupe, cliquez sur **Configuration** ordinateur et cliquez **sur Modèles d’administration.**

4. Développez **l’arborescence Windows composants** Antivirus Microsoft Defender, puis sélectionnez un emplacement (voir Paramètres et emplacements \> dans cet [](#settings-and-locations) article).

5. Modifiez l’objet de stratégie.

6. Cliquez **sur OK,** puis répétez l’une des autres configurations.

### <a name="settings-and-locations"></a>Paramètres et emplacements

|Élément de stratégie et emplacement|Paramètre par défaut (s’il n’est pas configuré)|Paramètre PowerShell `Set-MpPreference` ou propriété WMI pour la `MSFT_MpPreference` classe|
|---|---|---|
|Analyse du courrier électronique <p> **Analyse** \> **Activer l’analyse du courrier électronique**<p>Voir [limitations de l’analyse du](#email-scanning-limitations) courrier électronique (dans cet article)|Désactivé|`-DisableEmailScanning`|
|Analyser [les points d’analyse](/windows/win32/fileio/reparse-points) <p> **Analyse** \> **Activer l’analyse des points d’analyse**|Désactivé|Non disponible <p>Voir [Points d’parse](/windows/win32/fileio/reparse-points)|
|Analyser les lecteurs réseau mappés <p> **Analyse** \> **Exécuter une analyse complète sur des lecteurs réseau mappés**|Désactivé|`-DisableScanningMappedNetworkDrivesForFullScan`|
|Analyser les fichiers d’archive (tels .zip ou .rar fichiers). <p> **Analyse** \> **Analyser les fichiers d’archive**|Activé|`-DisableArchiveScanning` <p>La [liste d’exclusions des extensions](configure-extension-file-exclusions-microsoft-defender-antivirus.md) est prioritaire sur ce paramètre.|
|Analyser les fichiers sur le réseau <p> **Analyse** \> **Analyser les fichiers réseau**|Désactivé|`-DisableScanningNetworkFiles`|
|Analyser les exécutables packés <p> **Analyse** \> **Analyser les exécutables packés**|Activé|Non disponible|
|Analyser les lecteurs amovibles uniquement pendant les analyses complètes <p> **Analyse** \> **Analyser les lecteurs amovibles**|Désactivé|`-DisableRemovableDriveScanning`|
|Spécifier le niveau de sous-dossiers dans un dossier d’archivage à analyser <p>**Analyse** \> **Spécifier la profondeur maximale pour analyser les fichiers d’archivage**|0|Non disponible|
|Spécifiez la charge processeur maximale (en pourcentage) au cours d’une analyse. <p> **Analyse** \> **Spécifier le pourcentage maximal d’utilisation du processeur pendant une analyse**|50|`-ScanAvgCPULoadFactor` <p>**REMARQUE**: la charge processeur maximale n’est pas une limite difficile, mais est une recommandation pour que le moteur d’analyse ne dépasse pas le maximum en moyenne. L’exécuter manuellement ignore ce paramètre et s’exécute sans limites de processeur.|
|Spécifiez la taille maximale (en kilo-octets) des fichiers d’archivage qui doivent être analysés. <p> **Analyse** \> **Spécifier la taille maximale des fichiers d’archivage à scanner**|Aucune limite|Non disponible <p>La valeur par défaut 0 ne s’applique pas à la limite|
|Configurer une faible priorité du processeur pour les analyses programmées <p> **Analyse** \> **Configurer une faible priorité du processeur pour les analyses programmées**|Désactivé|Non disponible|

> [!NOTE]
> Si la protection en temps réel est désactivée, les fichiers sont analysés avant d’être accessibles et exécutés. L’étendue d’analyse inclut tous les fichiers, y compris les fichiers sur les supports amovibles montés, tels que les lecteurs USB. Si l’appareil qui effectue l’analyse dispose d’une protection en temps réel ou d’une protection à l’accès, l’analyse inclut également les partages réseau.

## <a name="use-powershell-to-configure-scanning-options"></a>Utiliser PowerShell pour configurer les options d’analyse

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir

- [Gérer Antivirus Microsoft Defender avec les cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Cmdlets Defender](/powershell/module/defender/)

## <a name="use-wmi-to-configure-scanning-options"></a>Utiliser WMI pour configurer les options d’analyse

Voir [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="email-scanning-limitations"></a>Limitations de l’analyse du courrier électronique

L’analyse du courrier électronique permet d’analyser les fichiers de messagerie utilisés par Outlook clients de messagerie et d’autres clients de messagerie lors d’analyses à la demande et programmées. Les objets incorporés dans le courrier électronique (tels que les pièces jointes et les fichiers archivés) sont également analysés. Les types de format de fichier suivants peuvent être analysés et corrigés :

- DBX
- MBX
- MIME

Les fichiers PST utilisés par Outlook 2003 ou une ancienne génération (où le type d’archive est non unicode) sont également analysés, mais Antivirus Microsoft Defender ne peut pas corriger les menaces détectées dans les fichiers PST.

Si Antivirus Microsoft Defender une menace à l’intérieur d’un message électronique, elle affiche les informations suivantes pour vous aider à identifier le courrier électronique compromis, afin que vous pouvez corriger la menace manuellement :

- Sujet de l’e-mail
- Nom de la pièce jointe

## <a name="scanning-mapped-network-drives"></a>Analyse des lecteurs réseau mappés

Sur n’importe quel système d’exploitation, seuls les lecteurs réseau qui sont mappés au niveau du système sont analysés. Les lecteurs réseau mappés au niveau de l’utilisateur ne sont pas analysés. Les lecteurs réseau mappés au niveau de l’utilisateur sont ceux qu’un utilisateur mase dans sa session manuellement et à l’aide de ses propres informations d’identification.

## <a name="see-also"></a>Voir aussi

- [Personnaliser, lancer et passer en revue les résultats des analyses et Antivirus Microsoft Defender correction](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Configurer et exécuter des analyses à la demande avec l’antivirus Microsoft Defender](run-scan-microsoft-defender-antivirus.md)
- [Configurer des analyses de Antivirus Microsoft Defender programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
