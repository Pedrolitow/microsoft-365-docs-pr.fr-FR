---
title: Gérer Windows Defender dans votre entreprise
description: Découvrez comment utiliser la stratégie de groupe, Configuration Manager, PowerShell, WMI, Intune et la ligne de commande pour gérer Microsoft Defender AV
keywords: stratégie de groupe, gpo, gestionnaire de config, sccm, scep, powershell, wmi, intune, defender, antivirus, anti-programme malveillant, sécurité, protection
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 12/16/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: ad3e8d2fb61eb5a2a350d061f926dd7bff8ae109
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690459"
---
# <a name="manage-microsoft-defender-antivirus-in-your-business"></a>Gérer l'Antivirus Microsoft Defender dans votre entreprise

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez gérer et configurer l'Antivirus Microsoft Defender avec les outils suivants :

- [Microsoft Intune](/mem/intune/protect/endpoint-security-antivirus-policy) (désormais partie intégrante de Microsoft Endpoint Manager)
- [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) (qui fait désormais partie de Microsoft Endpoint Manager)
- [Stratégie de groupe](./use-group-policy-microsoft-defender-antivirus.md)
- [Cmdlets PowerShell](./use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [WMI (Windows Management Instrumentation)](./use-wmi-microsoft-defender-antivirus.md)
- Utilitaire de ligne de commande microsoft de protection contre les programmes [malveillants](./command-line-arguments-microsoft-defender-antivirus.md) (appelé *utilitairempcmdrun.exe* logiciel

Les articles suivants fournissent des informations supplémentaires, des liens et des ressources pour l'utilisation de ces outils pour gérer et configurer l'Antivirus Microsoft Defender.

| Article | Description |
|:---|:---|
|[Gérer l'Antivirus Microsoft Defender avec Microsoft Intune et Microsoft Endpoint Configuration Manager](use-intune-config-manager-microsoft-defender-antivirus.md)|Informations sur l'utilisation d'Intune et de Configuration Manager pour déployer, gérer, signaler et configurer l'Antivirus Microsoft Defender |
|[Gérer l'Antivirus Microsoft Defender avec les paramètres de stratégie de groupe](use-group-policy-microsoft-defender-antivirus.md)|Liste de tous les paramètres de stratégie de groupe situés dans les modèles ADMX |
|[Gérer l'Antivirus Microsoft Defender avec les cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md)|Instructions d'utilisation des cmdlets PowerShell pour gérer l'Antivirus Microsoft Defender, ainsi que des liens vers la documentation pour toutes les cmdlets et paramètres autorisés |
|[Gérer l'Antivirus Microsoft Defender avec Windows Management Instrumentation (WMI)](use-wmi-microsoft-defender-antivirus.md)| Instructions sur l'utilisation de WMI pour gérer l'Antivirus Microsoft Defender, ainsi que des liens vers la documentation pour les API WMIv2 (y compris toutes les classes, méthodes et propriétés) |
|[Gérer l'Antivirus Microsoft Defender avec lmpcmdrun.exe de ligne de commande microsoft](command-line-arguments-microsoft-defender-antivirus.md)|Instructions sur l'utilisation de l'outil en ligne de commande dédié pour gérer et utiliser l'Antivirus Microsoft Defender |