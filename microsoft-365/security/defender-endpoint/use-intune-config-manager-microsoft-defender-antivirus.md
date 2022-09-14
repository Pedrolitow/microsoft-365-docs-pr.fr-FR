---
title: Configurer l’antivirus Microsoft Defender à l’aide de Microsoft Endpoint Manager
description: Utiliser Microsoft Endpoint Manager et Microsoft Intune pour configurer l’antivirus microsoft Defender et Endpoint Protection
keywords: scep, intune, endpoint protection, configuration
ms.service: microsoft-365-security
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
ms.subservice: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
search.appverid: met150
ms.openlocfilehash: ffe94273778a5920d8d4bfcd1dfe7ca310690909
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67687568"
---
# <a name="use-microsoft-endpoint-manager-to-configure-and-manage-microsoft-defender-antivirus"></a>Utiliser Microsoft Endpoint Manager pour configurer et gérer l’antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez utiliser [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) pour configurer les analyses antivirus Microsoft Defender. [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) et [Configuration Manager](/mem/configmgr/core/understand/introduction) font désormais partie de Endpoint Manager.

## <a name="configure-microsoft-defender-antivirus-scans-in-endpoint-manager"></a>Configurer les analyses antivirus Microsoft Defender dans Endpoint Manager

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Accédez à **Endpoint Security**.

3. Sous **Gérer**, choisissez **Antivirus**.

4. Sélectionnez votre stratégie antivirus Microsoft Defender.

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
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-articles"></a>Articles connexes

- [Articles de référence sur les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
