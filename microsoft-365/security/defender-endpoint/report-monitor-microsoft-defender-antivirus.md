---
title: Surveiller et signaler la protection Antivirus Microsoft Defender données
description: Utilisez Configuration Manager ou les outils de gestion des informations et des événements de sécurité (SIEM) pour utiliser des rapports et surveiller Microsoft Defender AV avec PowerShell et WMI.
keywords: siem, monitor, report, Microsoft Defender AV
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/23/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 1e754f43cc1963ae7991a72a65fef2aefa833305
ms.sourcegitcommit: 584445b62cb82218597b62495fb76fcb5b12af9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2021
ms.locfileid: "59498063"
---
# <a name="report-on-microsoft-defender-antivirus"></a>Signaler sur l’antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Antivirus Microsoft Defender est intégré à Windows 10, Windows Server 2019 et Windows Server 2016. Antivirus Microsoft Defender est de votre nouvelle génération de protection dans Microsoft Defender for Endpoint. La protection nouvelle génération permet de protéger vos appareils contre les menaces logicielles telles que les virus, les programmes malveillants et les logiciels espions dans le courrier électronique, les applications, le cloud et le web.

Avec Antivirus Microsoft Defender, vous avez plusieurs options pour passer en revue l’état et les alertes de la protection. Vous pouvez utiliser Microsoft Endpoint Manager pour [surveiller Antivirus Microsoft Defender](/configmgr/protect/deploy-use/monitor-endpoint-protection) ou créer [des alertes par courrier électronique.](/configmgr/protect/deploy-use/endpoint-configure-alerts) Vous pouvez également surveiller la protection à [l’aide Microsoft Intune](/intune/introduction-intune).

Microsoft Operations Management [](/windows/deployment/update/update-compliance-get-started) Suite dispose d’un module de conformité des mises à jour qui signale les Antivirus Microsoft Defender problèmes clés, notamment les mises à jour de la protection et les paramètres de protection en temps réel.

Si vous avez un serveur tiers d’informations sur la sécurité et de gestion des événements (SIEM), vous pouvez également utiliser Windows Defender [événements clients.](/windows/win32/events/windows-events)

Windows événements comprennent plusieurs sources d’événements de sécurité, notamment les événements [](/windows/device-security/auditing/security-auditing-overview) sam (Security Account Manager) (améliorés pour[Windows 10](/windows/whats-new/whats-new-windows-10-version-1507-and-1511), voir également la rubrique Audit de sécurité) et les [événements Windows Defender.](troubleshoot-microsoft-defender-antivirus.md)

Ces événements peuvent être regroupés de manière centralisée à [l’aide du Windows d’événements.](/windows/win32/wec/windows-event-collector) Souvent, les serveurs SIEM ont des connecteurs pour Windows événements, ce qui vous permet de corréler tous les événements de sécurité dans votre serveur SIEM.

Vous pouvez également surveiller les événements de programmes malveillants à [l’aide de la solution d’évaluation des programmes malveillants dans Log Analytics.](/azure/log-analytics/log-analytics-malware)

Pour surveiller ou déterminer l’état avec PowerShell, WMI ou Microsoft Azure, consultez [le tableau (Options](deploy-manage-report-microsoft-defender-antivirus.md#ref2)de déploiement, de gestion et de rapport).

## <a name="related-articles"></a>Articles connexes

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Antivirus Microsoft Defender sur Windows Server 2016 et 2019](microsoft-defender-antivirus-on-windows-server.md)
- [Déployer Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)