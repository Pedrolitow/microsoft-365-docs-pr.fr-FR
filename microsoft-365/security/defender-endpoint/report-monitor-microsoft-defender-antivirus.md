---
title: Surveiller et signaler la protection Antivirus Microsoft Defender
description: Utilisez Configuration Manager ou des outils SIEM (Security Information and Event Management) pour consommer des rapports et surveiller Microsoft Defender AV avec PowerShell et WMI.
keywords: siem, monitor, report, Microsoft Defender AV
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
ms.openlocfilehash: c36902d6c636c726a42292d7a6e4f0cdec60edb7
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415104"
---
# <a name="report-on-microsoft-defender-antivirus"></a>Signaler sur l’antivirus Microsoft Defender

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Antivirus Microsoft Defender est intégré à Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 et Windows Server 2016. Antivirus Microsoft Defender est votre protection de nouvelle génération dans Microsoft Defender pour point de terminaison. La protection de nouvelle génération permet de protéger vos appareils contre les menaces logicielles telles que les virus, les programmes malveillants et les logiciels espions dans les e-mails, les applications, le cloud et le web.

Avec Antivirus Microsoft Defender, vous disposez de plusieurs options pour passer en revue l’état de la protection et les alertes. Vous pouvez utiliser Microsoft Endpoint Manager pour [surveiller Antivirus Microsoft Defender](/configmgr/protect/deploy-use/monitor-endpoint-protection) ou [créer des alertes par e-mail](/configmgr/protect/deploy-use/endpoint-configure-alerts). Vous pouvez également surveiller la protection à l’aide [de Microsoft Intune](/intune/introduction-intune).

Si vous disposez d’un serveur SIEM (Security Information and Event Management) tiers, vous pouvez également utiliser [Windows Defender événements clients](/windows/win32/events/windows-events).

Windows événements comprennent plusieurs sources d’événements de sécurité, notamment les événements sam (Security Account Manager) ([améliorés pour Windows 10](/windows/whats-new/whats-new-windows-10-version-1507-and-1511), consultez également la rubrique [d’audit de sécurité](/windows/device-security/auditing/security-auditing-overview)) et [les événements Windows Defender](troubleshoot-microsoft-defender-antivirus.md).

Ces événements peuvent être agrégés de manière centralisée à l’aide du [collecteur d’événements Windows](/windows/win32/wec/windows-event-collector). Souvent, les serveurs SIEM ont des connecteurs pour Windows événements, ce qui vous permet de mettre en corrélation tous les événements de sécurité dans votre serveur SIEM.

Vous pouvez également [surveiller les événements de programmes malveillants à l’aide de la solution d’évaluation des programmes malveillants dans Log Analytics](/azure/log-analytics/log-analytics-malware).

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
- [Déployer Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
