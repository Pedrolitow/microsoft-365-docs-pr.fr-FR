---
title: Passer en revue les résultats Antivirus Microsoft Defender analyses
description: Passer en revue les résultats des analyses à l’aide Microsoft Endpoint Configuration Manager, Microsoft Intune ou l’application Sécurité Windows de données
keywords: résultats de l’analyse, correction, analyse complète, analyse rapide
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 8727baa9bb1935a1186907ca5f3d9d4f82dad6d4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473648"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>Examiner les Antivirus Microsoft Defender d’analyse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Une fois Antivirus Microsoft Defender analyse terminée, qu’il s’agit d’une analyse à la demande ou d’une analyse [programmée, les](scheduled-catch-up-scans-microsoft-defender-antivirus.md) résultats sont enregistrés et vous pouvez afficher les résultats.[](run-scan-microsoft-defender-antivirus.md) 


## <a name="use-configuration-manager-to-review-scan-results"></a>Utiliser Configuration Manager pour passer en revue les résultats de l’analyse

Découvrez [comment surveiller l’état Endpoint Protection’écran](/configmgr/protect/deploy-use/monitor-endpoint-protection).

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>Utiliser les cmdlets PowerShell pour passer en revue les résultats de l’analyse

L’cmdlet suivante retourne chaque détection sur le point de terminaison. S’il existe plusieurs détections de la même menace, chaque détection est répertoriée séparément, en fonction de l’heure de chaque détection :

```PowerShell
Get-MpThreatDetection
```

:::image type="content" source="../../media/wdav-get-mpthreatdetection.png" alt-text="Cmdlets et sorties PowerShell" lightbox="../../media/wdav-get-mpthreatdetection.png":::

Vous pouvez spécifier `-ThreatID` de limiter la sortie pour afficher uniquement les détections pour une menace spécifique.

Si vous souhaitez lister les détections de menaces, mais combiner les détections de la même menace en un seul élément, vous pouvez utiliser la cmdlet suivante :

```PowerShell
Get-MpThreat
```

:::image type="content" source="../../media/wdav-get-mpthreat.png" alt-text="Le code PowerShell" lightbox="../../media/wdav-get-mpthreat.png":::

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir utiliser les [cmdlets PowerShell pour configurer et exécuter les cmdlets Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et [Antivirus Defender](/powershell/module/defender/).

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>Utiliser Windows Management Instruction (WMI) pour passer en revue les résultats de l’analyse

Utilisez la [**méthode Get** des **classes MSFT_MpThreat** et **MSFT_MpThreatDetection**](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) classes.


## <a name="related-articles"></a>Articles connexes

- [Personnaliser, lancer et examiner les résultats des analyses et Antivirus Microsoft Defender correction](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
