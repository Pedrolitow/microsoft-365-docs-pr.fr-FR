---
title: Planifier des analyses antivirus à l’aide de Windows Management Instrumentation
description: Planifier des analyses antivirus à l’aide de WMI
keywords: analyse rapide, analyse complète, WMI, planification, antivirus
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
ms.collection: M365-security-compliance
search.appverid: met150
ms.openlocfilehash: 19612e81aad9b7437b677e6d48a0a2a05d48f83e
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67686612"
---
# <a name="schedule-antivirus-scans-using-windows-management-instrumentation-wmi"></a>Planifier des analyses antivirus à l’aide de Windows Management Instrumentation (WMI)

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Cet article explique comment configurer des analyses planifiées à l’aide de WMI. Pour en savoir plus sur la planification des analyses et sur les types d’analyse, consultez [Configurer les analyses antivirus Microsoft Defender rapides ou complètes planifiées](schedule-antivirus-scans.md). 

## <a name="use-windows-management-instruction-wmi-to-schedule-scans"></a>Utiliser Windows Management Instruction (WMI) pour planifier des analyses

Utilisez la [méthode **Set** de la classe **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

Pour plus d’informations et les paramètres autorisés, consultez [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="wmi-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>WMI pour la planification des analyses lorsqu’un point de terminaison n’est pas utilisé

Utilisez la [méthode Set de la classe MSFT_MpPreference](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ScanOnlyIfIdleEnabled
```

Pour plus d’informations sur les API et les paramètres autorisés, consultez [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!NOTE]
> Lorsque vous planifiez des analyses pour les moments où les points de terminaison ne sont pas utilisés, les analyses ne respectent pas la configuration de limitation du processeur et tirent pleinement parti des ressources disponibles pour effectuer l’analyse aussi rapidement que possible.


## <a name="wmi-for-scheduling-scans-to-complete-remediation"></a>WMI pour la planification des analyses pour terminer la correction

Utilisez la [méthode **Set** de la classe **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
RemediationScheduleDay
RemediationScheduleTime
```

Pour plus d’informations et les paramètres autorisés, consultez [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="wmi-for-scheduling-daily-scans"></a>WMI pour la planification des analyses quotidiennes

Utilisez la [méthode **Set** de la classe **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ScanScheduleQuickScanTime
```

Pour plus d’informations et les paramètres autorisés, consultez [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)