---
title: Planifier des analyses antivirus à l’aide Windows Management Instrumentation
description: Planifier des analyses antivirus à l’aide de WMI
keywords: analyse rapide, analyse complète, WMI, planification, antivirus
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
ms.openlocfilehash: be22e59f6d2be30ead354099f2cc168868959752
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61160281"
---
# <a name="schedule-antivirus-scans-using-windows-management-instrumentation-wmi"></a>Planifier des analyses antivirus à l’aide de Windows Management Instrumentation (WMI)

**S’applique à :**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Cet article explique comment configurer des analyses programmées à l’aide de WMI. Pour en savoir plus sur la planification des analyses et sur les types d’analyse, voir Configurer des analyses rapides ou [complètes Antivirus Microsoft Defender planification.](schedule-antivirus-scans.md) 

## <a name="use-windows-management-instruction-wmi-to-schedule-scans"></a>Utiliser Windows Management Instruction (WMI) pour planifier des analyses

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

Pour plus d’informations et des paramètres autorisés, [voir Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

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

