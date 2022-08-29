---
title: Gérer l’antivirus Microsoft Defender dans votre entreprise
description: Découvrez comment utiliser stratégie de groupe, Configuration Manager, PowerShell, WMI, Intune et la ligne de commande pour gérer l’antivirus Microsoft Defender
keywords: stratégie de groupe, gpo, gestionnaire de configuration, sccm, scep, powershell, wmi, intune, defender, antivirus, logiciel anti-programme malveillant, sécurité, protection
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
ms.openlocfilehash: c26f3e045efa5ea1c538796b9165bef5fa763c98
ms.sourcegitcommit: d09eb780dc41a01796eb8137fbe9267231af6746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2022
ms.locfileid: "67388812"
---
# <a name="manage-microsoft-defender-antivirus-in-your-business"></a>Gérer l’antivirus Microsoft Defender dans votre entreprise

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez gérer et configurer l’antivirus Microsoft Defender avec les outils suivants :

- [Microsoft Intune](/mem/intune/protect/endpoint-security-antivirus-policy) (qui fait désormais partie de Microsoft Endpoint Manager)
- [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) (qui fait désormais partie de Microsoft Endpoint Manager)
- [Stratégie de groupe](./use-group-policy-microsoft-defender-antivirus.md)
- [Applets de commande PowerShell](./use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Windows Management Instrumentation (WMI)](./use-wmi-microsoft-defender-antivirus.md)
- [Utilitaire de ligne de commande Microsoft Malware Protection](./command-line-arguments-microsoft-defender-antivirus.md) (appelé utilitaire *mpcmdrun.exe*

Les articles suivants fournissent des informations, des liens et des ressources supplémentaires sur l’utilisation de ces outils pour gérer et configurer l’antivirus Microsoft Defender.

|Article|Description|
|:---|:---|
|[Gérer l’antivirus Microsoft Defender avec Microsoft Intune et microsoft endpoint Configuration Manager](use-intune-config-manager-microsoft-defender-antivirus.md)|Informations sur l’utilisation de Intune et de Configuration Manager pour déployer, gérer, signaler et configurer l’antivirus Microsoft Defender|
|[Gérer l’antivirus Microsoft Defender avec des paramètres de stratégie de groupe](use-group-policy-microsoft-defender-antivirus.md)|Liste de tous les paramètres stratégie de groupe situés dans les modèles ADMX|
|[Gérer l’antivirus Microsoft Defender avec des applets de commande PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md)|Instructions d’utilisation des applets de commande PowerShell pour gérer l’antivirus Microsoft Defender, ainsi que des liens vers la documentation pour toutes les applets de commande et les paramètres autorisés|
|[Gérer l’antivirus Microsoft Defender avec Windows Management Instrumentation (WMI)](use-wmi-microsoft-defender-antivirus.md)|Instructions d’utilisation de WMI pour gérer l’Antivirus Microsoft Defender, ainsi que des liens vers la documentation pour les API WMIv2 (y compris toutes les classes, méthodes et propriétés)|
|[Gérer l’antivirus Microsoft Defender avec l’outil en ligne de commande MpCmdRun.exe](command-line-arguments-microsoft-defender-antivirus.md)|Instructions sur l’utilisation de l’outil en ligne de commande dédié pour gérer et utiliser l’antivirus Microsoft Defender|

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)