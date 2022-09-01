---
title: Résoudre les problèmes d’extension de noyau dans Microsoft Defender pour point de terminaison sur macOS
description: Résoudre les problèmes liés aux extensions de noyau dans Microsoft Defender pour point de terminaison sur macOS.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, noyau, extension
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
ms.openlocfilehash: 333fa4bce74aec78f18872751f153191ac163142
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67521968"
---
# <a name="troubleshoot-kernel-extension-issues-in-microsoft-defender-for-endpoint-on-macos"></a>Résoudre les problèmes d’extension de noyau dans Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cet article fournit des informations sur la résolution des problèmes liés à l’extension de noyau installée dans le cadre de Microsoft Defender pour point de terminaison sur macOS.

À compter de macOS High Sierra (10.13), macOS exige que toutes les extensions du noyau soient explicitement approuvées avant d’être autorisées à s’exécuter sur l’appareil.

Si vous n’avez pas approuvé l’extension de noyau pendant le déploiement/l’installation de Microsoft Defender pour point de terminaison sur macOS, l’application affiche une bannière vous invitant à l’activer :

:::image type="content" source="images/mdatp-32-main-app-fix.png" alt-text="RTP désactivé" lightbox="images/mdatp-32-main-app-fix.png":::

Vous pouvez également exécuter ```mdatp health```. Il indique si la protection en temps réel est activée, mais pas disponible. Cela indique que l’extension de noyau n’est pas approuvée pour s’exécuter sur votre appareil.

```bash
mdatp health
```
```Output
...
real_time_protection_enabled                : false
real_time_protection_available              : true
...
```

Les sections suivantes fournissent des conseils sur la façon de résoudre ce problème, en fonction de la méthode que vous avez utilisée pour déployer Microsoft Defender pour point de terminaison sur macOS.

## <a name="managed-deployment"></a>Déploiement managé

Consultez les instructions correspondant à l’outil de gestion que vous avez utilisé pour déployer le produit :

- [Déploiement basé sur JAMF](mac-install-with-jamf.md)
- [Déploiement basé sur Microsoft Intune](mac-install-with-intune.md#create-system-configuration-profiles)

## <a name="manual-deployment"></a>Déploiement manuel

Si moins de 30 minutes se sont écoulées depuis l’installation du produit, accédez à **System Preferences** \> **Security & Privacy**, où vous devez **autoriser** les logiciels système des développeurs « Microsoft Corporation ».

Si vous ne voyez pas cette invite, cela signifie que 30 minutes ou plus sont passées et que l’extension du noyau n’a toujours pas été approuvée pour s’exécuter sur votre appareil :

:::image type="content" source="images/mdatp-33-securityprivacysettings-noprompt.png" alt-text="Fenêtre de sécurité et de confidentialité après l’expiration de l’invite" lightbox="images/mdatp-33-securityprivacysettings-noprompt.png":::

Dans ce cas, vous devez effectuer les étapes suivantes pour déclencher à nouveau le flux d’approbation.

1. Dans Terminal, essayez d’installer le pilote. L’opération suivante échoue, car l’extension du noyau n’a pas été approuvée pour s’exécuter sur l’appareil. Toutefois, il déclenchera à nouveau le flux d’approbation.

    ```bash
    sudo kextutil /Library/Extensions/wdavkext.kext
    ```

    ```Output
    Kext rejected due to system policy: <OSKext 0x7fc34d528390 [0x7fffa74aa8e0]> { URL = "file:///Library/StagedExtensions/Library/Extensions/wdavkext.kext/", ID = "com.microsoft.wdavkext" }
    Kext rejected due to system policy: <OSKext 0x7fc34d528390 [0x7fffa74aa8e0]> { URL = "file:///Library/StagedExtensions/Library/Extensions/wdavkext.kext/", ID = "com.microsoft.wdavkext" }
    Diagnostics for /Library/Extensions/wdavkext.kext:
    ```

2. Ouvrez **La sécurité des préférences** \> système **& confidentialité** dans le menu. (Fermez-le en premier, s’il est ouvert.)

3. **Autoriser** les logiciels système des développeurs « Microsoft Corporation »

4. Dans Terminal, réinstallez le pilote. Cette fois, l’opération aboutit :

    ```bash
    sudo kextutil /Library/Extensions/wdavkext.kext
    ```

    La bannière doit disparaître de l’application Defender et ```mdatp health``` doit maintenant signaler que la protection en temps réel est à la fois activée et disponible :

    ```bash
    mdatp health
    ```

    ```Output
    ...
    real_time_protection_enabled                : true
    real_time_protection_available              : true
    ...
    ```
