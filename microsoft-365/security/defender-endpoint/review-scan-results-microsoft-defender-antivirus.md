---
title: Passer en revue les résultats des analyses Antivirus Microsoft Defender
description: Passez en revue les résultats des analyses à l’aide de Microsoft Endpoint Configuration Manager, de Microsoft Intune ou de l’application Sécurité Windows
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
ms.openlocfilehash: 3bbaa19401823eada5b1b9769c259e8296f75924
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417565"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>Examiner Antivirus Microsoft Defender résultats de l’analyse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Une fois l’analyse Antivirus Microsoft Defender terminée, qu’il s’agisse d’une analyse [à la demande](run-scan-microsoft-defender-antivirus.md) ou [planifiée](scheduled-catch-up-scans-microsoft-defender-antivirus.md), les résultats sont enregistrés et vous pouvez afficher les résultats. 


## <a name="use-configuration-manager-to-review-scan-results"></a>Utiliser Configuration Manager pour examiner les résultats de l’analyse

Découvrez [comment surveiller l’état Endpoint Protection](/configmgr/protect/deploy-use/monitor-endpoint-protection).

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>Utiliser des applets de commande PowerShell pour passer en revue les résultats de l’analyse

L’applet de commande suivante retourne chaque détection sur le point de terminaison. S’il existe plusieurs détections de la même menace, chaque détection est répertoriée séparément, en fonction de l’heure de chaque détection :

```PowerShell
Get-MpThreatDetection
```

:::image type="content" source="../../media/wdav-get-mpthreatdetection.png" alt-text="Applets de commande et sorties PowerShell" lightbox="../../media/wdav-get-mpthreatdetection.png":::

Vous pouvez spécifier `-ThreatID` de limiter la sortie pour afficher uniquement les détections d’une menace spécifique.

Si vous souhaitez répertorier les détections de menaces, mais combiner les détections de la même menace en un seul élément, vous pouvez utiliser l’applet de commande suivante :

```PowerShell
Get-MpThreat
```

:::image type="content" source="../../media/wdav-get-mpthreat.png" alt-text="Code PowerShell" lightbox="../../media/wdav-get-mpthreat.png":::

Pour plus d’informations sur l’utilisation de [PowerShell avec Antivirus Microsoft Defender, consultez Utiliser les applets de commande PowerShell pour configurer et exécuter Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et [l’Antivirus Defender](/powershell/module/defender/).

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>Utiliser Windows Management Instruction (WMI) pour passer en revue les résultats de l’analyse

Utilisez la [méthode **Get** des classes **MSFT_MpThreat** et **MSFT_MpThreatDetection**](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)


## <a name="related-articles"></a>Articles connexes

- [Personnaliser, lancer et examiner les résultats des analyses et des corrections Antivirus Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
