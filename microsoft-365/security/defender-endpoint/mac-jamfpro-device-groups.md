---
title: Configurer des groupes d’appareils dans Jamf Pro
description: Découvrez comment configurer des groupes d’appareils dans Jamf Pro pour Microsoft Defender pour Endpoint sur macOS
keywords: device, group, microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune, jamfpro, macos,péra, mojave, high sierra
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8d7994ac207f6f066b5cfe69de75ddfb608ddd40fa53105492a5076aced01de5
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53833702"
---
# <a name="set-up-microsoft-defender-for-endpoint-on-macos-device-groups-in-jamf-pro"></a>Configurer Microsoft Defender pour endpoint sur les groupes d’appareils macOS dans Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Configurer les groupes d’appareils de la même façon que les groupes d’organisation de stratégie de groupe Microsoft Endpoint Configuration Manager la collection d’appareils de Microsoft Endpoint Configuration Manager et les groupes d’appareils d’Intune.

1. Accédez à **Groupes d’ordinateurs statiques.**

2. Sélectionnez **Nouveau**. 

    ![Image de Jamf Pro1](images/jamf-pro-static-group.png)

3. Fournissez un nom d’affichage et sélectionnez **Enregistrer.**

    ![Image de Jamf Pro2](images/jamfpro-machine-group.png)

4. Vous verrez maintenant le groupe **d’ordinateurs de Contoso** sous **Groupes d’ordinateurs statiques.**

    ![Image de Jamf Pro3](images/contoso-machine-group.png)

## <a name="next-step"></a>Étape suivante
- [Configurer Microsoft Defender pour endpoint sur les stratégies macOS dans Jamf Pro](mac-jamfpro-policies.md)
