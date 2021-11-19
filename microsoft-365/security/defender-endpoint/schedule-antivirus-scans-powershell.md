---
title: Planifier des analyses antivirus à l’aide de PowerShell
description: Planifier des analyses antivirus à l’aide de PowerShell
keywords: analyse rapide, analyse complète, antivirus, planification, PowerShell
ms.prod: m365-security
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
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 03978feb5a9d0ca98d432fbec91e0fd5ce83724e
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61111254"
---
# <a name="schedule-antivirus-scans-using-powershell"></a>Planifier des analyses antivirus à l’aide de PowerShell

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Cet article explique comment configurer des analyses programmées à l’aide d’cmdlets PowerShell. Pour en savoir plus sur la planification des analyses et sur les types d’analyse, voir Configurer des analyses rapides ou [complètes Antivirus Microsoft Defender planification.](schedule-antivirus-scans.md) 

## <a name="use-powershell-cmdlets-to-schedule-scans"></a>Utiliser les cmdlets PowerShell pour planifier des analyses

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -ScanParameters
Set-MpPreference -ScanScheduleDay
Set-MpPreference -ScanScheduleTime
Set-MpPreference -RandomizeScheduleTaskTimes

```

Pour plus d’informations, voir Utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter les [cmdlets](/powershell/module/defender/) Antivirus Microsoft Defender et Defender for Cloud pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender.

## <a name="powershell-cmdlets-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>Cmdlets PowerShell pour la planification des analyses lorsqu’un point de terminaison n’est pas utilisé

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled
```

Pour plus d’informations, voir Utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter Antivirus Microsoft Defender et [Defender pour les cmdlets cloud.](/powershell/module/defender/)

> [!NOTE]
> Lorsque vous programmez des analyses à des moments où les points de terminaison ne sont pas utilisés, les analyses ne respectent pas la configuration de limitation du processeur et tirez pleinement parti des ressources disponibles pour effectuer l’analyse aussi rapidement que possible.

## <a name="powershell-cmdlets-for-scheduling-scans-to-complete-remediation"></a>Cmdlets PowerShell pour la planification des analyses afin de terminer la correction

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -RemediationScheduleDay
Set-MpPreference -RemediationScheduleTime
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, consultez les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter les [cmdlets](/powershell/module/defender/) Antivirus Microsoft Defender et Defender for Cloud.

## <a name="powershell-cmdlets-for-scheduling-daily-scans"></a>Cmdlets PowerShell pour la planification des analyses quotidiennes

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -ScanScheduleQuickScanTime
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir Utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter les [cmdlets](/powershell/module/defender/)Antivirus Microsoft Defender et Defender pour le cloud.
