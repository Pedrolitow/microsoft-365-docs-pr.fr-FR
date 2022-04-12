---
title: Configurer Antivirus Microsoft Defender à l’aide de Microsoft Endpoint Manager
description: Utilisez Microsoft Endpoint Manager et Microsoft Intune pour configurer Antivirus Microsoft Defender et Endpoint Protection
keywords: scep, intune, endpoint protection, configuration
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 12/16/2021
ms.reviewer: phuijbr, oogunrinde
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: b25e57ee28ae0ef3f219a9adda1ff3f860d063db
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789291"
---
# <a name="use-microsoft-endpoint-manager-to-configure-and-manage-microsoft-defender-antivirus"></a>Utiliser Microsoft Endpoint Manager pour configurer et gérer Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez utiliser [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) pour configurer Antivirus Microsoft Defender analyses. [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) et [Configuration Manager](/mem/configmgr/core/understand/introduction) font désormais partie de Endpoint Manager.

## <a name="configure-microsoft-defender-antivirus-scans-in-endpoint-manager"></a>Configurer des analyses Antivirus Microsoft Defender dans Endpoint Manager

1. Accédez au centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Accédez à **Endpoint Security**.

3. Sous **Gérer**, choisissez **Antivirus**.

4. Sélectionnez votre stratégie de Antivirus Microsoft Defender.

5. Sous **Gérer**, choisissez **Propriétés**.

6. Près de **Paramètres de configuration**, choisissez **Modifier**.

   > [!IMPORTANT]
   > Les paramètres antivirus AllowOnAccessProtection et AllowIntrusionPreventionSystem sont officiellement déconseillés et ne peuvent donc pas être configurés. 

7. Développez la section **Analyse** et examinez ou modifiez vos paramètres d’analyse.

8. Choisissez **Vérifier + enregistrer**.

> [!TIP]
> Besoin d’aide ? Consultez [Gérer la sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison sur les fonctionnalités Android](android-configure.md)
> - [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-articles"></a>Articles connexes

- [Articles de référence sur les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
