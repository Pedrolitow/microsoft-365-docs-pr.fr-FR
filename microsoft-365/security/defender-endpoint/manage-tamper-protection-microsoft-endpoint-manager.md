---
title: Gérer la protection contre les falsifications pour votre organisation à l’aide de Microsoft Intune
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Activez ou désactivez la protection contre les falsifications pour votre organisation dans Microsoft Intune.
keywords: logiciels malveillants, defender, antivirus, protection contre les falsifications, Microsoft Intune
ms.pagetype: security
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.date: 10/14/2022
audience: ITPro
ms.topic: conceptual
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
ms.openlocfilehash: c9e1113e20402fce066213861a4e0063f45a5e39
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68623678"
---
# <a name="manage-tamper-protection-for-your-organization-using-microsoft-intune"></a>Gérer la protection contre les falsifications pour votre organisation à l’aide de Microsoft Intune

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Si votre organisation utilise [Microsoft Intune](/mem/intune/fundamentals/what-is-intune), vous pouvez activer ou désactiver la protection contre les falsifications pour votre organisation dans le Centre d’administration [Microsoft Endpoint Manager](https://endpoint.microsoft.com). Utilisez Intune lorsque vous souhaitez affiner les paramètres de protection contre les falsifications. Par exemple, si vous souhaitez activer la protection contre les falsifications sur certains appareils, mais pas tous, utilisez Intune.

## <a name="requirements-for-managing-tamper-protection-in-intune"></a>Configuration requise pour la gestion de la protection contre les falsifications dans Intune

- Vous devez disposer [des autorisations](/microsoft-365/security/defender-endpoint/assign-portal-access) appropriées, telles que l’administrateur général, l’administrateur de sécurité ou les opérations de sécurité.
- Votre organisation utilise [Intune pour gérer les appareils](/mem/endpoint-manager-getting-started). (Intune licences sont requises ; Intune est inclus dans Microsoft 365 E3/E5, Enterprise Mobility + Security E3/E5, Microsoft 365 Business Premium, Microsoft 365 F1/F3, Microsoft 365 Government G3/G5 et licences d’éducation correspondantes.)
- Vos appareils Windows doivent exécuter Windows 10 [version 1709 ou ultérieure](/lifecycle/announcements/revised-end-of-service-windows-10-1709) ou Windows 11. (Pour plus d’informations sur les versions, consultez [Windows 10 informations de publication](/windows/release-health/release-information).)
- Vous devez utiliser la sécurité Windows avec [les informations de sécurité](https://www.microsoft.com/wdsi/definitions) mises à jour vers la version 1.287.60.0 (ou ultérieure).
- Vos appareils doivent utiliser la plateforme anti-programme malveillant version 4.18.1906.3 (ou ultérieure) et la version `1.1.15500.X` du moteur anti-programme malveillant (ou version ultérieure). ([Gérez Microsoft Defender mises à jour antivirus et appliquez des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).)
- Vos locataires Intune et Defender pour point de terminaison doivent partager la même infrastructure Microsoft Entra (Azure Active Directory).
- Vos appareils doivent être intégrés à Defender pour point de terminaison.

> [!NOTE]
> Si vos appareils ne sont pas inscrits dans Microsoft Defender pour point de terminaison, la protection contre les falsifications s’affiche comme **non applicable** tant que le processus d’intégration n’est pas terminé.

## <a name="turn-tamper-protection-on-or-off-in-microsoft-intune"></a>Activer ou désactiver la protection contre les falsifications dans Microsoft Intune

:::image type="content" source="images/turnontamperprotectinmem.png" alt-text="Activer la protection contre les falsifications avec Intune" lightbox="images/turnontamperprotectinmem.png":::

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **l’antivirus** de **sécurité** \> de point de terminaison, puis choisissez **+ Créer une stratégie**.

   - Dans la liste **des plateformes**, sélectionnez **Windows 10, Windows 11 et Windows Server**.
   - Dans la liste **des profils**, sélectionnez **Sécurité Windows expérience**.

2. Créez un profil qui inclut le paramètre suivant :

    - **TamperProtection (appareil) : activer**

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