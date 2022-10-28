---
title: Configurer des groupes d’appareils dans Jamf Pro
description: Découvrez comment configurer des groupes d’appareils dans Jamf Pro pour Microsoft Defender pour point de terminaison sur macOS
keywords: device, group, microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, deploy, uninstallation, intune, jamfpro, macos, catalina, big sur, monterey, ventura, mde for mac
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
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 16247ae629423fd8dd2028455c6d45c894eca77f
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68767835"
---
# <a name="set-up-microsoft-defender-for-endpoint-on-macos-device-groups-in-jamf-pro"></a>Configurer Microsoft Defender pour point de terminaison sur des groupes d’appareils macOS dans Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!NOTE]
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.  

Configurez les groupes d’appareils similaires à la stratégie de groupe, au regroupement d’appareils de Microsoft Endpoint Configuration Manager et aux groupes d’appareils de Intune.

1. Accédez à **Groupes d’ordinateurs statiques**.

2. Sélectionnez **Nouveau**. 

   :::image type="content" source="images/jamf-pro-static-group.png" alt-text="La page Jamf Pro1" lightbox="images/jamf-pro-static-group.png":::

3. Indiquez un nom d’affichage, puis sélectionnez **Enregistrer**.

   :::image type="content" source="images/jamfpro-machine-group.png" alt-text="La page Jamf Pro2" lightbox="images/jamfpro-machine-group.png":::

4. Vous verrez maintenant le **groupe d’ordinateurs de Contoso** sous **Groupes d’ordinateurs statiques**.

   :::image type="content" source="images/contoso-machine-group.png" alt-text="Page Jamf Pro3" lightbox="images/contoso-machine-group.png":::

## <a name="next-step"></a>Étape suivante
- [Configurer Microsoft Defender pour point de terminaison sur les stratégies macOS dans Jamf Pro](mac-jamfpro-policies.md)
