---
title: Passer en revue les résultats des analyses de l’Antivirus Microsoft Defender
description: Passer en revue les résultats des analyses à l’aide Microsoft Endpoint Configuration Manager, Microsoft Intune ou l’Sécurité Windows de données
keywords: résultats de l’analyse, correction, analyse complète, analyse rapide
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/28/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.openlocfilehash: ec3dd2edc09d504af0ed76b17577130b1cdce1b7
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52275371"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>Passer en Antivirus Microsoft Defender résultats d’analyse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Une fois Antivirus Microsoft Defender analyse complète, qu’il s’agit d’une analyse à la demande ou d’une analyse [programmée,](scheduled-catch-up-scans-microsoft-defender-antivirus.md)les résultats sont enregistrés et vous pouvez afficher les résultats. [](run-scan-microsoft-defender-antivirus.md) 


## <a name="use-configuration-manager-to-review-scan-results"></a>Utiliser Configuration Manager pour passer en revue les résultats de l’analyse

Découvrez [comment surveiller l’état Endpoint Protection des ordinateurs.](/configmgr/protect/deploy-use/monitor-endpoint-protection)

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>Utiliser les cmdlets PowerShell pour passer en revue les résultats de l’analyse

L’cmdlet suivante retourne chaque détection sur le point de terminaison. S’il existe plusieurs détections de la même menace, chaque détection est répertoriée séparément, en fonction de l’heure de chaque détection :

```PowerShell
Get-MpThreatDetection
```

![Capture d’écran des cmdlets et sorties PowerShell](images/defender/wdav-get-mpthreatdetection.png)

Vous pouvez `-ThreatID` spécifier de limiter la sortie pour afficher uniquement les détections d’une menace spécifique.

Si vous souhaitez lister les détections de menaces, mais combiner les détections de la même menace en un seul élément, vous pouvez utiliser la cmdlet suivante :

```PowerShell
Get-MpThreat
```

![Capture d’écran de PowerShell](images/defender/wdav-get-mpthreat.png)

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir Utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter des [cmdlets](/powershell/module/defender/) Antivirus Microsoft Defender et Defender.

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>Utiliser Windows Management Instruction (WMI) pour passer en revue les résultats de l’analyse

Utilisez la [ **méthode Get** des **classes MSFT_MpThreat** et **MSFT_MpThreatDetection**](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) classes.


## <a name="related-articles"></a>Articles connexes

- [Personnaliser, lancer et passer en revue les résultats des analyses et Antivirus Microsoft Defender correction](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)