---
title: Configurer les options d’analyse pour Microsoft Defender Antivirus
description: Vous pouvez configurer Microsoft Defender Antivirus pour analyser les fichiers de stockage de courrier électronique, les points de sauvegarde ou d’analyse, les fichiers réseau et les fichiers archivés (tels que les fichiers .zip).
keywords: analyses avancées, analyse, e-mail, archive, zip, rar, archive, analyse d’analyse
ms.pagetype: security
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.date: 12/03/2021
ms.collection:
- m365-security
- tier2
ms.topic: how-to
search.appverid: met150
ms.openlocfilehash: 9280bb06c6701c05b42be5fa5c5686bfedfaf434
ms.sourcegitcommit: b9282493c371d59c2e583b9803825096499b5e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68151472"
---
# <a name="configure-microsoft-defender-antivirus-scanning-options"></a>Configurer les options d’analyse de l’antivirus Microsoft Defender

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows 

## <a name="use-microsoft-intune-to-configure-scanning-options"></a>Utiliser Microsoft Intune pour configurer les options d’analyse

Pour plus d’informations, consultez [Configurer les paramètres de restriction d’appareil dans Microsoft Intune](/intune/device-restrictions-configure) et [Microsoft Defender paramètres de restriction d’appareil antivirus pour Windows 10 dans Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="use-microsoft-endpoint-manager-to-configure-scanning-options"></a>Utiliser Microsoft Endpoint Manager pour configurer les options d’analyse

Pour plus d’informations sur la configuration de Microsoft Endpoint Manager (current branch), consultez [Comment créer et déployer des stratégies anti-programme malveillant : Paramètres d’analyse](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).

## <a name="use-group-policy-to-configure-scanning-options"></a>Utiliser stratégie de groupe pour configurer les options d’analyse

> [!TIP]
> Téléchargez la feuille de calcul de référence stratégie de groupe, qui répertorie les paramètres de stratégie pour les configurations d’ordinateur et d’utilisateur incluses dans les fichiers de modèle d’administration fournis avec Windows. Vous pouvez configurer la feuille de calcul lorsque vous modifiez stratégie de groupe Objets. <br/><br/> Voici les versions les plus récentes :
> - [Feuille de calcul de référence des paramètres stratégie de groupe pour Windows 10 mise à jour de mai 2020 (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [feuille de calcul de référence des paramètres stratégie de groupe pour Windows 11 mise à jour d’octobre 2021 (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

3. Dans **l’éditeur de gestion stratégie de groupe**, **accédez à Configuration de l’ordinateur**, puis cliquez sur **Modèles d’administration**.

4. Développez l’arborescence sur **les composants** \> Windows **Microsoft Defender Antivirus**, puis sélectionnez un emplacement (reportez-vous aux [paramètres et emplacements](#settings-and-locations) de cet article).

5. Modifiez l’objet de stratégie.

6. Cliquez sur **OK** et répétez l’opération pour tous les autres paramètres.

### <a name="settings-and-locations"></a>Paramètres et emplacements

|Élément de stratégie et emplacement|Paramètre par défaut (s’il n’est pas configuré)|Paramètre PowerShell `Set-MpPreference` ou propriété WMI pour la `MSFT_MpPreference` classe|
|---|---|---|
|analyse Email <p> **Numériser** \> **Activer l’analyse du courrier électronique**<p>Voir [Email limitations de l’analyse](#email-scanning-limitations) (dans cet article)|Désactivé|`-DisableEmailScanning`|
| Analyse des scripts | Activé  | Ce paramètre de stratégie vous permet de configurer l’analyse des scripts. Si vous activez ou ne configurez pas ce paramètre, l’analyse des scripts est activée. <p>Voir [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender)  | 
|Analyser [les points d’analyse](/windows/win32/fileio/reparse-points) <p> **Numériser** \> **Activer l’analyse des points d’analyse**|Désactivé|Non disponible <p>Voir [Points d’analyse](/windows/win32/fileio/reparse-points)|
|Analyser les lecteurs réseau mappés <p> **Numériser** \> **Exécuter une analyse complète sur les lecteurs réseau mappés**|Désactivé|`-DisableScanningMappedNetworkDrivesForFullScan`|
|Analyser les fichiers d’archive (tels que les fichiers .zip ou .rar). <p> **Numériser** \> **Analyser les fichiers d’archive**|Activé|`-DisableArchiveScanning` <p>La [liste d’exclusions d’extensions](configure-extension-file-exclusions-microsoft-defender-antivirus.md) est prioritaire sur ce paramètre.|
|Analyser les fichiers sur le réseau <p> **Numériser** \> **Analyser les fichiers réseau**|Désactivé|`-DisableScanningNetworkFiles`|
|Analyser les exécutables compressés <p> **Numériser** \> **Analyser les exécutables compressés**|Activé|Non disponible|
|Analyser les lecteurs amovibles pendant les analyses complètes uniquement <p> **Numériser** \> **Analyser les lecteurs amovibles**|Désactivé|`-DisableRemovableDriveScanning`|
|Spécifier le niveau des sous-dossiers dans un dossier d’archive à analyser <p>**Numériser** \> **Spécifier la profondeur maximale pour analyser les fichiers d’archive**|0|Non disponible|
|Spécifiez la charge maximale du processeur (en pourcentage) pendant une analyse. <p> **Numériser** \> **Spécifier le pourcentage maximal d’utilisation du processeur pendant une analyse**|50|`-ScanAvgCPULoadFactor` <p>**REMARQUE** : La charge maximale de l’UC n’est pas une limite stricte, mais elle est conseillée pour que le moteur d’analyse ne dépasse pas la valeur maximale en moyenne. Les analyses d’exécution manuelle ignorent ce paramètre et s’exécutent sans limites d’UC.|
|Spécifiez la taille maximale (en kilo-octets) des fichiers d’archive qui doivent être analysés. <p> **Numériser** \> **Spécifier la taille maximale des fichiers d’archive à analyser**|Aucune limite|Non disponible <p>La valeur par défaut 0 n’applique aucune limite|
|Configurer une faible priorité du processeur pour les analyses planifiées <p> **Numériser** \> **Configurer une faible priorité du processeur pour les analyses planifiées**|Désactivé|Non disponible|

> [!NOTE]
> Si la protection en temps réel est activée, les fichiers sont analysés avant d’être consultés et exécutés. L’étendue d’analyse inclut tous les fichiers, y compris les fichiers sur les supports amovibles montés, tels que les lecteurs USB. Si la protection en temps réel ou sur accès est activée sur l’appareil effectuant l’analyse, l’analyse inclut également les partages réseau.

## <a name="use-powershell-to-configure-scanning-options"></a>Utiliser PowerShell pour configurer les options d’analyse

Pour plus d’informations sur l’utilisation de PowerShell avec Microsoft Defender Antivirus, consultez

- [Gérer Microsoft Defender Antivirus avec des applets de commande PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [applets de commande antivirus Microsoft Defender](/powershell/module/defender/)

## <a name="use-wmi-to-configure-scanning-options"></a>Utiliser WMI pour configurer les options d’analyse

Consultez [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="email-scanning-limitations"></a>Email limitations de l’analyse

Email’analyse permet d’analyser les fichiers de courrier utilisés par Outlook et d’autres clients de messagerie pendant les analyses à la demande et planifiées. Les objets incorporés dans l’e-mail (tels que les pièces jointes et les fichiers archivés) sont également analysés. Les types de format de fichier suivants peuvent être analysés et corrigés :

- Dbx
- Mbx
- MIME

Les fichiers PST utilisés par Outlook 2003 ou version antérieure (où le type d’archive est défini sur non unicode) sont également analysés, mais Microsoft Defender Antivirus ne peut pas corriger les menaces détectées dans les fichiers PST.

Si Microsoft Defender Antivirus détecte une menace à l’intérieur d’un e-mail, il affiche les informations suivantes pour vous aider à identifier l’e-mail compromis, afin que vous puissiez corriger la menace manuellement :

- Sujet de l’e-mail
- Nom de la pièce jointe

## <a name="scanning-mapped-network-drives"></a>Analyse des lecteurs réseau mappés

Sur n’importe quel système d’exploitation, seuls les lecteurs réseau mappés au niveau du système sont analysés. Les lecteurs réseau mappés au niveau de l’utilisateur ne sont pas analysés. Les lecteurs réseau mappés au niveau de l’utilisateur sont ceux qu’un utilisateur mappe manuellement dans sa session et à l’aide de ses propres informations d’identification.

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

- [Personnaliser, lancer et examiner les résultats des analyses et des corrections de Microsoft Defender Antivirus](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Configurer et exécuter des analyses à la demande avec l’antivirus Microsoft Defender](run-scan-microsoft-defender-antivirus.md)
- [Configurer des analyses antivirus Microsoft Defender planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
