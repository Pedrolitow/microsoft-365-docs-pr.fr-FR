---
title: Configurer des groupes d’appareils dans Jamf Pro
description: Découvrez comment configurer des groupes d’appareils dans Jamf Pro pour Microsoft Defender pour point de terminaison sur macOS
keywords: device, group, microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, deploy, uninstallation, intune, jamfpro, macos, catalina, mojave, high sierra
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 7f3006896ccebdb40f720671427dfe76b3d53025
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67687942"
---
# <a name="set-up-microsoft-defender-for-endpoint-on-macos-device-groups-in-jamf-pro"></a>Configurer Microsoft Defender pour point de terminaison sur des groupes d’appareils macOS dans Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Configurez les groupes d’appareils similaires aux unités d’organisation de stratégie de groupe, à la collection d’appareils de Microsoft Endpoint Configuration Manager et aux groupes d’appareils de Intune.

1. Accédez aux **groupes d’ordinateurs statiques**.

2. Sélectionnez **Nouveau**. 

   :::image type="content" source="images/jamf-pro-static-group.png" alt-text="Page Jamf Pro1" lightbox="images/jamf-pro-static-group.png":::

3. Indiquez un nom d’affichage, puis **sélectionnez Enregistrer**.

   :::image type="content" source="images/jamfpro-machine-group.png" alt-text="Page Jamf Pro2" lightbox="images/jamfpro-machine-group.png":::

4. Vous verrez maintenant le **groupe d’ordinateurs de Contoso** sous **Groupes d’ordinateurs statiques**.

   :::image type="content" source="images/contoso-machine-group.png" alt-text="Page Jamf Pro3" lightbox="images/contoso-machine-group.png":::

## <a name="next-step"></a>Étape suivante
- [Configurer Microsoft Defender pour point de terminaison sur des stratégies macOS dans Jamf Pro](mac-jamfpro-policies.md)
