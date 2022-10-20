---
title: Surveiller et signaler la protection antivirus Microsoft Defender
description: Utilisez Configuration Manager ou des outils SIEM (Security Information and Event Management) pour consommer des rapports et surveiller Microsoft Defender Antivirus avec PowerShell et WMI.
keywords: siem, monitor, report, Microsoft Defender AV, Microsoft Defender Antivirus
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.topic: conceptual
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: d05764db303fd06bda8ee178a97009f4875e7b72
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68641290"
---
# <a name="report-on-microsoft-defender-antivirus"></a>Signaler sur l’antivirus Microsoft Defender

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Microsoft Defender Antivirus est intégré à Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 et Windows Server 2016. Microsoft Defender Antivirus est votre protection de nouvelle génération dans Microsoft Defender pour point de terminaison. La protection de nouvelle génération permet de protéger vos appareils contre les menaces logicielles telles que les virus, les programmes malveillants et les logiciels espions dans les e-mails, les applications, le cloud et le web.

Avec Microsoft Defender Antivirus, vous disposez de plusieurs options pour passer en revue l’état de la protection et les alertes. Vous pouvez utiliser Microsoft Endpoint Manager pour [surveiller Microsoft Defender Antivirus](/configmgr/protect/deploy-use/monitor-endpoint-protection) ou [créer des alertes par e-mail](/configmgr/protect/deploy-use/endpoint-configure-alerts). Vous pouvez également surveiller la protection à l’aide [de Microsoft Intune](/intune/introduction-intune).

Si vous disposez d’un serveur SIEM (Security Information and Event Management) tiers, vous pouvez également utiliser [Windows Defender événements clients](/windows/win32/events/windows-events).

Les événements Windows comprennent plusieurs sources d’événements de sécurité, notamment les événements sam (Security Account Manager) ([améliorés pour Windows 10](/windows/whats-new/whats-new-windows-10-version-1507-and-1511), consultez également la rubrique [d’audit de](/windows/security/threat-protection/auditing/security-auditing-overview) sécurité) et [les événements Windows Defender](troubleshoot-microsoft-defender-antivirus.md).

Ces événements peuvent être agrégés de manière centralisée à l’aide du [collecteur d’événements Windows](/windows/win32/wec/windows-event-collector). Souvent, les serveurs SIEM ont des connecteurs pour les événements Windows, ce qui vous permet de mettre en corrélation tous les événements de sécurité dans votre serveur SIEM.

Vous pouvez également [surveiller les événements de programmes malveillants à l’aide de la solution d’évaluation des programmes malveillants dans Log Analytics](/security/benchmark/azure/security-control-logging-monitoring).

Pour la surveillance ou la détermination de l’état avec PowerShell, WMI ou Microsoft Azure, consultez le [(tableau des options de déploiement, de gestion et de création de rapports).](deploy-manage-report-microsoft-defender-antivirus.md#ref2)

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

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Déployer Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
