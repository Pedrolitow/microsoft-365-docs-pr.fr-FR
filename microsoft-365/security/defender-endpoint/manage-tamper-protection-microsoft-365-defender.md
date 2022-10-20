---
title: Gérer la protection contre les falsifications pour votre organisation à l’aide de Microsoft 365 Defender
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Activez ou désactivez la protection contre les falsifications pour votre locataire à l’aide du portail Microsoft 365 Defender.
keywords: logiciels malveillants, defender, antivirus, protection contre les falsifications, Microsoft 365 Defender
ms.pagetype: security
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
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
ms.openlocfilehash: ce36dacb8b16e068dbe6dec483eacbe82ba30fc2
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68627036"
---
# <a name="manage-tamper-protection-for-your-organization-using-microsoft-365-defender-portal"></a>Gérer la protection contre les falsifications pour votre organisation à l’aide du portail Microsoft 365 Defender

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

La protection contre les falsifications peut être activée ou désactivée pour votre locataire à l’aide du portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Voici quelques points à garder à l’esprit :

- Actuellement, l’option de gestion de la « protection contre les falsifications » dans le portail Microsoft 365 Defender est activée par défaut pour les nouveaux déploiements. Pour les déploiements existants, la « protection contre les falsifications » est disponible sur une base d’adhésion. Pour participer, dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, choisissez **Paramètres points** \> de **terminaison Fonctionnalités avancées** \>  \> **protection contre la falsification**.
- Lorsque vous utilisez le portail Microsoft 365 Defender pour gérer la « protection contre les falsifications », vous n’avez pas besoin d’utiliser Intune ou la méthode d’attachement de locataire.
- Lorsque vous gérez la « protection contre les falsifications » dans le portail Microsoft 365 Defender, le paramètre est appliqué à l’échelle du locataire, ce qui affecte tous vos appareils qui exécutent Windows 10, Windows 10 Entreprise multisession, Windows 11, Windows 11 Entreprise  multisession, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 ou Windows Server 2022. Pour affiner la « protection contre les falsifications » (par exemple, la protection contre les falsifications sur certains appareils, mais désactivée pour d’autres), utilisez la gestion de la protection contre les [falsifications pour votre organisation à l’aide de Microsoft Endpoint Manager](manage-tamper-protection-microsoft-endpoint-manager.md) ou [gérez la protection contre les falsifications à l’aide de l’attachement de locataire avec Configuration Manager, version 2006](manage-tamper-protection-configuration-manager.md).
- Si vous avez un environnement hybride, les paramètres de protection contre les falsifications configurés dans Intune sont prioritaires sur les paramètres configurés dans le portail Microsoft 365 Defender.

## <a name="requirements-for-managing-tamper-protection-in-the-microsoft-365-defender-portal"></a>Configuration requise pour la gestion de la protection contre les falsifications dans le portail Microsoft 365 Defender

- Vous devez disposer [des autorisations](/microsoft-365/security/defender-endpoint/assign-portal-access) appropriées, telles que l’administrateur général, l’administrateur de sécurité ou les opérations de sécurité.

- Vos appareils Windows doivent exécuter l’une des versions suivantes de Windows :
  
  - Windows 11
  - Multisession Windows 11 Entreprise 
  - Windows 10
  - Windows 10 Entreprise à sessions multiples
  - Windows Server 2022
  - Windows Server 2019
  - Windows Server, version 1803 ou ultérieure
  - Windows Server 2016
  - Windows Server 2012 R2

Pour plus d’informations sur les versions, consultez [Windows 10 informations de publication](/windows/release-health/release-information).

- Vos appareils doivent être [intégrés à Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/onboarding).
- Vos appareils doivent utiliser la version `4.18.2010.7` de plateforme anti-programme malveillant (ou ultérieure) et la version `1.1.17600.5` du moteur anti-programme malveillant (ou ultérieure). ([Gérez Microsoft Defender mises à jour antivirus et appliquez des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).)
- [La protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) doit être activée.

> [!NOTE]
> Lorsque la protection contre les falsifications est activée via le portail Microsoft 365 Defender, une protection fournie par le cloud est requise, afin que l’état activé de la protection contre les falsifications puisse être contrôlé.  
> À compter de la mise à jour de novembre 2021 (version `4.18.2111.5`de la plateforme), si la protection fournie par le cloud n’est pas activée pour un appareil et que la protection contre les falsifications est activée dans le portail Microsoft 365 Defender, la protection fournie par le cloud est automatiquement activée pour cet appareil, ainsi que la protection contre les falsifications.   

## <a name="turn-tamper-protection-on-or-off-in-the-microsoft-365-defender-portal"></a>Activer ou désactiver la protection contre les falsifications dans le portail Microsoft 365 Defender

:::image type="content" source="../../media/mde-turn-tamperprotectionon.png" alt-text="Activer la protection contre les falsifications dans le portail Microsoft 365 Defender" lightbox="../../media/mde-turn-tamperprotectionon.png":::

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Choisissez **Les points de terminaison des** \> **paramètres**.

3. Accédez aux **fonctionnalités avancées générales**\>, puis activez la protection contre les falsifications.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)