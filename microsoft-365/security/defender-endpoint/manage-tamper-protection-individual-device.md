---
title: Gérer la protection contre les falsifications sur un appareil individuel
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Activez ou désactivez la protection contre les falsifications pour un appareil individuel.
keywords: programmes malveillants, defender, antivirus, protection contre les falsifications
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
ms.openlocfilehash: 250d82b4ab61a356c12cb8bee5d03f737c3d0a25
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68221519"
---
# <a name="manage-tamper-protection-on-an-individual-device"></a>Gérer la protection contre les falsifications sur un appareil individuel

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

> [!NOTE]
> Les blocs de protection contre les falsifications tentent de modifier Microsoft Defender paramètres antivirus via le Registre.
> Pour vous assurer que la protection contre les falsifications n’interfère pas avec les produits de sécurité non Microsoft ou les scripts d’installation d’entreprise qui modifient ces paramètres, accédez à **Sécurité Windows** et mettez à jour **security intelligence** vers la version 1.287.60.0 ou ultérieure. (Consultez [les mises à jour du renseignement de sécurité](https://www.microsoft.com/wdsi/definitions).) Une fois cette mise à jour effectuée, la protection contre les falsifications continue de protéger vos paramètres de Registre, et les journaux tentent de les modifier sans retourner d’erreurs.

Si vous êtes un utilisateur domestique ou que vous n’êtes pas soumis à des paramètres gérés par une équipe de sécurité, vous pouvez utiliser l’application Sécurité Windows pour gérer la protection contre les falsifications. Vous devez disposer des autorisations d’administrateur appropriées sur votre appareil pour modifier les paramètres de sécurité, tels que la protection contre les falsifications.

Voici ce que vous voyez dans l’application Sécurité Windows :

:::image type="content" source="images/tamperprotectionturnedon.png" alt-text="Activer la protection contre les falsifications dans Windows 10 Famille" lightbox="images/tamperprotectionturnedon.png":::

1. Sélectionnez **Démarrer**, puis commencez à taper *Sécurité*. Dans les résultats de la recherche, sélectionnez **Sécurité Windows**.

2. Sélectionnez **Virus & protection** \> contre les **menaces Virus & paramètres de protection contre les menaces**.

3. Définissez **la protection contre les falsifications** **sur Activé** ou **Désactivé**.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

