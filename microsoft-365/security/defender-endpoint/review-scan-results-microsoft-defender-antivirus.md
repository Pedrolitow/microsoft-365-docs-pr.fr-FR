---
title: Passer en revue les résultats des analyses de l'Antivirus Microsoft Defender
description: Passer en revue les résultats des analyses à l'aide de Microsoft Endpoint Configuration Manager, Microsoft Intune ou l'application sécurité Windows
keywords: résultats de l'analyse, correction, analyse complète, analyse rapide
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/28/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 3b8a299f41541be878a9e9023ab330ea973646fd
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51764144"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>Passer en revue les résultats de l'analyse de l'Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Une fois l'analyse de l'Antivirus [](run-scan-microsoft-defender-antivirus.md) Microsoft Defender terminée, qu'il s'agit d'une analyse à la demande ou d'une analyse [programmée,](scheduled-catch-up-scans-microsoft-defender-antivirus.md)les résultats sont enregistrés et vous pouvez afficher les résultats. 


## <a name="use-configuration-manager-to-review-scan-results"></a>Utiliser Configuration Manager pour passer en revue les résultats de l'analyse

Découvrez [comment surveiller l'état de Endpoint Protection.](/configmgr/protect/deploy-use/monitor-endpoint-protection)

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>Utiliser les cmdlets PowerShell pour passer en revue les résultats de l'analyse

L'cmdlet suivante retourne chaque détection sur le point de terminaison. S'il existe plusieurs détections de la même menace, chaque détection est répertoriée séparément, en fonction de l'heure de chaque détection :

```PowerShell
Get-MpThreatDetection
```

![Capture d'écran des cmdlets et sorties PowerShell](images/defender/wdav-get-mpthreatdetection.png)

Vous pouvez `-ThreatID` spécifier de limiter la sortie pour afficher uniquement les détections d'une menace spécifique.

Si vous souhaitez lister les détections de menaces, mais combiner les détections de la même menace en un seul élément, vous pouvez utiliser la cmdlet suivante :

```PowerShell
Get-MpThreat
```

![Capture d'écran de PowerShell](images/defender/wdav-get-mpthreat.png)

Pour [plus d'informations](use-powershell-cmdlets-microsoft-defender-antivirus.md) sur l'utilisation de PowerShell avec l'Antivirus Microsoft Defender, voir les [cmdlets](/powershell/module/defender/) Utiliser PowerShell pour configurer et exécuter l'Antivirus Microsoft Defender.

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>Utiliser Windows Management Instruction (WMI) pour passer en revue les résultats de l'analyse

Utilisez la [ **méthode Get** des **classes MSFT_MpThreat** et **MSFT_MpThreatDetection**](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) classes.


## <a name="related-articles"></a>Articles connexes

- [Personnaliser, lancer et passer en revue les résultats des analyses et des corrections de l'Antivirus Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)