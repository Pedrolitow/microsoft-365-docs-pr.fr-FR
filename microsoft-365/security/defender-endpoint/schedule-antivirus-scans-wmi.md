---
title: Planifier des analyses antivirus à l’aide Windows Management Instrumentation
description: Planifier des analyses antivirus à l’aide de WMI
keywords: analyse rapide, analyse complète, WMI, planification, antivirus
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 06/09/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.openlocfilehash: 1aa174f4601fb57eebbc4fb7c78e1809b9f072c8
ms.sourcegitcommit: 337e8d8a2fee112d799edd8a0e04b3a2f124f900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2021
ms.locfileid: "52879674"
---
# <a name="schedule-antivirus-scans-using-windows-management-instrumentation-wmi"></a>Planifier des analyses antivirus à l’aide Windows Management Instrumentation (WMI)

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Cet article explique comment configurer des analyses programmées à l’aide de WMI. Pour en savoir plus sur la planification des analyses et sur les types d’analyse, voir Configurer des analyses rapides ou [complètes Antivirus Microsoft Defender planification.](schedule-antivirus-scans.md) 

## <a name="use-windows-management-instruction-wmi-to-schedule-scans"></a>Utiliser Windows Management Instruction (WMI) pour planifier des analyses

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

Pour plus d’informations et les paramètres autorisés, [voir Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="wmi-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>WMI pour la planification des analyses lorsqu’un point de terminaison n’est pas utilisé

Utilisez la [méthode Set de la classe MSFT_MpPreference pour](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) les propriétés suivantes :

```WMI
ScanOnlyIfIdleEnabled
```

Pour plus d’informations sur les API et les paramètres autorisés, [voir Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!NOTE]
> Lorsque vous programmez des analyses à des moments où les points de terminaison ne sont pas utilisés, les analyses ne respectent pas la configuration de limitation du processeur et tirez pleinement parti des ressources disponibles pour effectuer l’analyse aussi rapidement que possible.


## <a name="wmi-for-scheduling-scans-to-complete-remediation"></a>WMI pour la planification des analyses afin de terminer la correction

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
RemediationScheduleDay
RemediationScheduleTime
```

Pour plus d’informations et les paramètres autorisés, [voir Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="wmi-for-scheduling-daily-scans"></a>WMI pour la planification des analyses quotidiennes

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ScanScheduleQuickScanTime
```

Pour plus d’informations et les paramètres autorisés, [voir Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

