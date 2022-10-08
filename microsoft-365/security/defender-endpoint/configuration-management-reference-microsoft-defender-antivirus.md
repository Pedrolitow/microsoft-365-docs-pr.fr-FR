---
title: Gérer Microsoft Defender Antivirus dans votre entreprise
description: Découvrez comment utiliser stratégie de groupe, Configuration Manager, PowerShell, WMI, Intune et la ligne de commande pour gérer Microsoft Defender Antivirus
keywords: stratégie de groupe, gpo, gestionnaire de configuration, sccm, scep, powershell, wmi, intune, defender, antivirus, logiciel anti-programme malveillant, sécurité, protection
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.topic: article
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: dcf6baf8c2c161d5b8390ef62f08307daa3f7715
ms.sourcegitcommit: b9282493c371d59c2e583b9803825096499b5e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68151560"
---
# <a name="manage-microsoft-defender-antivirus-in-your-business"></a>Gérer Microsoft Defender Antivirus dans votre entreprise

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez gérer et configurer Microsoft Defender Antivirus avec les outils suivants :

- [Microsoft Intune](/mem/intune/protect/endpoint-security-antivirus-policy) (qui fait désormais partie de Microsoft Endpoint Manager)
- [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) (qui fait désormais partie de Microsoft Endpoint Manager)
- [Stratégie de groupe](./use-group-policy-microsoft-defender-antivirus.md)
- [Applets de commande PowerShell](./use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Windows Management Instrumentation (WMI)](./use-wmi-microsoft-defender-antivirus.md)
- [Utilitaire de ligne de commande Microsoft Malware Protection](./command-line-arguments-microsoft-defender-antivirus.md) (appelé utilitaire *mpcmdrun.exe*

Les articles suivants fournissent des informations, des liens et des ressources supplémentaires sur l’utilisation de ces outils pour gérer et configurer Microsoft Defender Antivirus.

|Article|Description|
|:---|:---|
|[Gérer Microsoft Defender Antivirus avec Microsoft Intune et microsoft endpoint Configuration Manager](use-intune-config-manager-microsoft-defender-antivirus.md)|Informations sur l’utilisation de Intune et de Configuration Manager pour déployer, gérer, signaler et configurer Microsoft Defender Antivirus|
|[Gérer Microsoft Defender Antivirus avec des paramètres de stratégie de groupe](use-group-policy-microsoft-defender-antivirus.md)|Liste de tous les paramètres stratégie de groupe situés dans les modèles ADMX|
|[Gérer Microsoft Defender Antivirus avec des applets de commande PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md)|Instructions d’utilisation des applets de commande PowerShell pour gérer Microsoft Defender Antivirus, ainsi que des liens vers la documentation pour toutes les applets de commande et les paramètres autorisés|
|[Gérer Microsoft Defender Antivirus avec Windows Management Instrumentation (WMI)](use-wmi-microsoft-defender-antivirus.md)|Instructions d’utilisation de WMI pour gérer Microsoft Defender Antivirus, ainsi que des liens vers la documentation des API WMIv2 (y compris toutes les classes, méthodes et propriétés)|
|[Gérer Microsoft Defender Antivirus avec l’outil en ligne de commande MpCmdRun.exe](command-line-arguments-microsoft-defender-antivirus.md)|Instructions sur l’utilisation de l’outil en ligne de commande dédié pour gérer et utiliser Microsoft Defender Antivirus|

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)