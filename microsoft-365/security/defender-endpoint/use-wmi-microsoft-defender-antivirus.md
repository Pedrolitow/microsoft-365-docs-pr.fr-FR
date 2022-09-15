---
title: Configurer l’antivirus Microsoft Defender avec WMI
description: Découvrez comment configurer et gérer l’Antivirus Microsoft Defender à l’aide de scripts WMI pour récupérer, modifier et mettre à jour les paramètres dans Microsoft Defender pour point de terminaison.
keywords: wmi, scripts, instrumentation de gestion windows, configuration
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
search.appverid: met150
ms.openlocfilehash: 9930e9bce4c5b5de3a4508ace82dd04562026d2c
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67699771"
---
# <a name="use-windows-management-instrumentation-wmi-to-configure-and-manage-microsoft-defender-antivirus"></a>Utiliser Windows Management Instrumentation (WMI) pour configurer et gérer l’antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Windows Management Instrumentation (WMI) est une interface de script qui vous permet de récupérer, modifier et mettre à jour les paramètres.

Pour en savoir plus sur WMI, consultez la [bibliothèque Microsoft Developer Network System Administration](/windows/win32/wmisdk/wmi-start-page).

L’Antivirus Microsoft Defender dispose d’un certain nombre de classes WMI spécifiques qui peuvent être utilisées pour effectuer la plupart des mêmes fonctions que stratégie de groupe et d’autres outils de gestion. La plupart des classes sont analogues aux [applets de commande Defender pour Cloud PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md).

La [bibliothèque de référence du fournisseur MSDN Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) répertorie les classes WMI disponibles pour l’antivirus Microsoft Defender et inclut des exemples de scripts.

Les modifications apportées à WMI affectent les paramètres locaux sur le point de terminaison où les modifications sont déployées ou effectuées. Cela signifie que les déploiements de stratégie avec stratégie de groupe, Microsoft Endpoint Configuration Manager ou Microsoft Intune peuvent remplacer les modifications apportées avec WMI. 

Vous pouvez [configurer les paramètres qui peuvent être remplacés localement avec des remplacements de stratégie locale](configure-local-policy-overrides-microsoft-defender-antivirus.md).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-topics"></a>Voir aussi

- [Rubriques de référence sur les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
