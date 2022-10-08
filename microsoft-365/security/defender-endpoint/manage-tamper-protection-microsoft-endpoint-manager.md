---
title: Gérer la protection contre les falsifications pour votre organisation à l’aide de Microsoft Endpoint Manager
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Activez ou désactivez la protection contre les falsifications pour votre organisation dans Microsoft Endpoint Manager.
keywords: programmes malveillants, defender, antivirus, protection contre les falsifications, Microsoft Endpoint Manager
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
ms.openlocfilehash: d939c942d77a1fd2b160aff91f4583f703ca6815
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68223939"
---
# <a name="manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager"></a>Gérer la protection contre les falsifications pour votre organisation à l’aide de Microsoft Endpoint Manager

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows


Si votre organisation utilise Microsoft Endpoint Manager (MEM), vous pouvez activer ou désactiver la protection contre les falsifications pour votre organisation dans le Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Utilisez Intune lorsque vous souhaitez affiner les paramètres de protection contre les falsifications. Par exemple, si vous souhaitez activer la protection contre les falsifications sur certains appareils, mais pas tous, utilisez Intune.

## <a name="requirements-for-managing-tamper-protection-in-endpoint-manager"></a>Configuration requise pour la gestion de la protection contre les falsifications dans Endpoint Manager

- Vous devez disposer [des autorisations](/microsoft-365/security/defender-endpoint/assign-portal-access) appropriées, telles que l’administrateur général, l’administrateur de sécurité ou les opérations de sécurité.
- Votre organisation utilise [Microsoft Endpoint Manager pour gérer les appareils](/mem/endpoint-manager-getting-started). Des licences (Microsoft Endpoint Manager (MEM) sont requises ; MEM est inclus dans Microsoft 365 E3/E5, Enterprise Mobility + Security E3/E5, Microsoft 365 Business Premium, Microsoft 365 F1/F3, Microsoft 365 Government G3/G5 et les licences éducation correspondantes.)
- Vos appareils Windows doivent exécuter Windows 11 ou Windows 10 [1709](/lifecycle/announcements/revised-end-of-service-windows-10-1709), [1803](/lifecycle/announcements/windows-server-1803-end-of-servicing), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) ou version ultérieure. (Pour plus d’informations sur les versions, consultez [Windows 10 informations de publication](/windows/release-health/release-information).)
- Vous devez utiliser la sécurité Windows avec [les informations de sécurité](https://www.microsoft.com/wdsi/definitions) mises à jour vers la version 1.287.60.0 (ou ultérieure).
- Vos appareils doivent utiliser la plateforme anti-programme malveillant version 4.18.1906.3 (ou ultérieure) et la version `1.1.15500.X` du moteur anti-programme malveillant (ou version ultérieure). ([Gérez Microsoft Defender mises à jour antivirus et appliquez des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).)

## <a name="turn-tamper-protection-on-or-off-in-microsoft-endpoint-manager"></a>Activer ou désactiver la protection contre les falsifications dans Microsoft Endpoint Manager

:::image type="content" source="images/turnontamperprotectinmem.png" alt-text="Activer la protection contre les falsifications avec Intune" lightbox="images/turnontamperprotectinmem.png":::

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **l’antivirus** de **sécurité** \> de point de terminaison, puis choisissez **+ Créer une stratégie**.

   - Dans la liste **des plateformes**, sélectionnez **Windows 10 et versions ultérieures**.
   - Dans la liste **des profils**, sélectionnez **Sécurité Windows expérience**.

2. Créez un profil qui inclut le paramètre suivant :

    - **Activer la protection contre les falsifications pour empêcher la désactivation de Microsoft Defender : Activer**

3. Affectez le profil à un ou plusieurs groupes.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)