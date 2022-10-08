---
title: Gérer la protection contre les falsifications à l’aide de l’attachement de locataire avec Configuration Manager, version 2006
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Activez ou désactivez la protection contre les falsifications à l’aide de l’attachement de locataire avec Configuration Manager.
keywords: programmes malveillants, defender, antivirus, protection contre les falsifications, Configuration Manager
ms.pagetype: security
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom:
- nextgen
- admindeeplinkDEFENDER
ms.subservice: mde
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 1c928c6f7a7ccc3c9d4b22d9f69f75051bd17c5c
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68222025"
---
# <a name="manage-tamper-protection-using-tenant-attach-with-configuration-manager-version-2006"></a>Gérer la protection contre les falsifications à l’aide de l’attachement de locataire avec Configuration Manager, version 2006

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Si vous utilisez la [version 2006 de Configuration Manager](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006), vous pouvez gérer les paramètres de protection contre les falsifications sur Windows 10, Windows 10 Entreprise multisession, Windows 11 Windows 11 Entreprise multisession, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 et Windows Server 2022 à l’aide d’une méthode appelée *attachement de locataire*. L’attachement de locataire vous permet de synchroniser vos appareils Configuration Manager locaux uniquement dans le Centre d’administration Microsoft Endpoint Manager, puis de fournir des stratégies de configuration de sécurité de point de terminaison aux regroupements locaux & appareils.

> [!NOTE]
> La procédure peut être utilisée pour étendre la protection contre les falsifications aux appareils exécutant Windows 10, Windows 10 Entreprise multisession, Windows 11, Windows 11 Entreprise multisession, Windows Server 2019 et Windows Server 2022. Veillez à examiner les prérequis et d’autres informations dans les ressources mentionnées dans cette procédure. Pour Windows Server 2012 R2 exécutant la solution unifiée moderne [version 2203 de Configuration Manager](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2203) est requise.

1. Configurez l’attachement de locataire. Pour plus d’informations, consultez [Prise en main : Créer et déployer des stratégies de sécurité de point de terminaison à partir du centre d’administration](/mem/configmgr/tenant-attach/endpoint-security-get-started).

2. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **l’antivirus** de **sécurité** \> de point de terminaison, puis choisissez **+ Créer une stratégie**.

   - Dans la liste **des plateformes**, sélectionnez **Windows 10, Windows 11 et Windows Server (ConfigMgr).**
   - Dans la liste **des profils**, sélectionnez **Sécurité Windows expérience (préversion).**

3. Déployez la stratégie sur votre collection d’appareils.

## <a name="need-help-with-this-method"></a>Vous avez besoin d’aide avec cette méthode ?

Consultez les ressources suivantes :

- [Paramètres du profil d’expérience Sécurité Windows dans Microsoft Intune](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [Blog tech community : Annonce de la protection contre les falsifications pour Configuration Manager clients d’attachement de locataire](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)