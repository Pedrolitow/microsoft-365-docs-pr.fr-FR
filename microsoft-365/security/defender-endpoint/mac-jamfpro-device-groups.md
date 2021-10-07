---
title: Configurer des groupes d’appareils dans Jamf Pro
description: Découvrez comment configurer des groupes d’appareils dans Jamf Pro pour Microsoft Defender pour Endpoint sur macOS
keywords: device, group, microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune, jamfpro, macos,péra, mojave, high sierra
ms.prod: m365-security
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
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 29f67b4bd96775494064789a57ae7e53e6d0d77a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60207798"
---
# <a name="set-up-microsoft-defender-for-endpoint-on-macos-device-groups-in-jamf-pro"></a>Configurer Microsoft Defender pour endpoint sur les groupes d’appareils macOS dans Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Configurer les groupes d’appareils similaires aux groupes d’organisation de stratégie de groupe, à Microsoft Endpoint Configuration Manager collection d’appareils et aux groupes d’appareils d’Intune.

1. Accédez à **Groupes d’ordinateurs statiques.**

2. Sélectionnez **Nouveau**. 

    ![Image de Jamf Pro1.](images/jamf-pro-static-group.png)

3. Fournissez un nom d’affichage et sélectionnez **Enregistrer.**

    ![Image de Jamf Pro2.](images/jamfpro-machine-group.png)

4. Vous verrez maintenant le groupe **d’ordinateurs de Contoso** sous **Groupes d’ordinateurs statiques.**

    ![Image de Jamf Pro3.](images/contoso-machine-group.png)

## <a name="next-step"></a>Étape suivante
- [Configurer Microsoft Defender pour endpoint sur les stratégies macOS dans Jamf Pro](mac-jamfpro-policies.md)
