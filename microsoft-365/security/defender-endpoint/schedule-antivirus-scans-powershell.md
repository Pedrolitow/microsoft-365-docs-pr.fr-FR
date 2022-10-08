---
title: Planifier des analyses antivirus à l’aide de PowerShell
description: Planifier des analyses antivirus à l’aide de PowerShell
keywords: analyse rapide, analyse complète, antivirus, planification, PowerShell
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.subservice: mde
ms.topic: how-to
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 5899b4280a4794799df9acc2d7a3701ff8553cdb
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68233439"
---
# <a name="schedule-antivirus-scans-using-powershell"></a>Planifier des analyses antivirus à l’aide de PowerShell

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Cet article explique comment configurer des analyses planifiées à l’aide d’applets de commande PowerShell. Pour en savoir plus sur la planification des analyses et sur les types d’analyse, consultez [Configurer des analyses antivirus rapides ou complètes planifiées Microsoft Defender](schedule-antivirus-scans.md). 

## <a name="use-powershell-cmdlets-to-schedule-scans"></a>Utiliser des applets de commande PowerShell pour planifier des analyses

Utilisez les applets de commande suivantes :

```PowerShell
Set-MpPreference -ScanParameters
Set-MpPreference -ScanScheduleDay
Set-MpPreference -ScanScheduleTime
Set-MpPreference -RandomizeScheduleTaskTimes

```

Pour plus d’informations, consultez [Utiliser les applets de commande PowerShell pour configurer et exécuter Microsoft Defender applets](use-powershell-cmdlets-microsoft-defender-antivirus.md) de commande [Antivirus et Defender Antivirus](/powershell/module/defender/) pour plus d’informations sur l’utilisation de PowerShell avec Microsoft Defender Antivirus.

## <a name="powershell-cmdlets-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>Applets de commande PowerShell pour la planification des analyses lorsqu’un point de terminaison n’est pas utilisé

Utilisez les applets de commande suivantes :

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled
```

Pour plus d’informations, consultez [Utiliser les applets de commande PowerShell pour configurer et exécuter l’antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et les [Applets de commande de l’antivirus Defender](/powershell/module/defender/).

> [!NOTE]
> Lorsque vous planifiez des analyses pour les moments où les points de terminaison ne sont pas utilisés, les analyses ne respectent pas la configuration de limitation du processeur et tirent pleinement parti des ressources disponibles pour effectuer l’analyse aussi rapidement que possible.

## <a name="powershell-cmdlets-for-scheduling-scans-to-complete-remediation"></a>Applets de commande PowerShell permettant de planifier des analyses pour terminer la correction

Utilisez les applets de commande suivantes :

```PowerShell
Set-MpPreference -RemediationScheduleDay
Set-MpPreference -RemediationScheduleTime
```

Pour plus d’informations sur l’utilisation de PowerShell avec Microsoft Defender Antivirus, consultez Utiliser les applets de commande [PowerShell pour configurer et exécuter Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) antivirus et [Defender Antivirus](/powershell/module/defender/).

## <a name="powershell-cmdlets-for-scheduling-daily-scans"></a>Applets de commande PowerShell pour la planification des analyses quotidiennes

Utilisez les applets de commande suivantes :

```PowerShell
Set-MpPreference -ScanScheduleQuickScanTime
```

Pour plus d’informations sur l’utilisation de PowerShell avec Microsoft Defender Antivirus, consultez [Utiliser les applets de commande PowerShell pour configurer et exécuter Microsoft Defender applets](use-powershell-cmdlets-microsoft-defender-antivirus.md) de commande Antivirus et [Antivirus Defender](/powershell/module/defender/).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)