---
title: Planifier des analyses avec Microsoft Defender pour Endpoint sur macOS
description: Découvrez comment planifier un temps d’analyse automatique pour Microsoft Defender pour Endpoint dans macOS afin de mieux protéger les ressources de votre organisation.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, analyses, antivirus
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
ms.openlocfilehash: b432f7ba7887176168e482f745be77d431da4f4a7b201025263015c7a6179407
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53811001"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>Planifier des analyses avec Microsoft Defender pour endpoint sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bien que vous pouvez démarrer une analyse des menaces à tout moment avec Microsoft Defender pour le point de terminaison, votre entreprise peut bénéficier d’analyses programmées ou programmées. Par exemple, vous pouvez planifier une analyse à exécuter au début de chaque jour ou semaine de travail. 

## <a name="schedule-a-scan-with-launchd"></a>Planifier une analyse avec *lancement*

Vous pouvez créer une planification d’analyse à l’aide du *daemon* lancé sur un appareil macOS.

Pour plus d’informations sur le format [](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) de fichier *.plist* utilisé ici, voir à propos des fichiers de liste de propriétés d’informations sur le site web officiel du développeur Apple.

### <a name="schedule-a-quick-scan"></a>Planifier une analyse rapide

Le code suivant montre le schéma que vous devez utiliser pour planifier une analyse rapide. 

1. Ouvrez un éditeur de texte et utilisez cet exemple comme guide pour votre propre fichier d’analyse programmé.

    ```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
      "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>Label</key>
        <string>com.microsoft.wdav.schedquickscan</string>
        <key>ProgramArguments</key>
        <array>
            <string>sh</string>
            <string>-c</string>
            <string>/usr/local/bin/mdatp scan quick</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>StartCalendarInterval</key>
        <dict>
            <key>Day</key>
            <integer>3</integer>
            <key>Hour</key>
            <integer>2</integer>
            <key>Minute</key>
            <integer>0</integer>
            <key>Weekday</key>
            <integer>5</integer>
        </dict>
        <key>WorkingDirectory</key>
        <string>/usr/local/bin/</string>
    </dict>
    </plist>
     ```

2. Enregistrez le fichier *sous com.microsoft.wdav.schedquickscan.plist*.

### <a name="schedule-a-full-scan"></a>Planifier une analyse complète

1. Ouvrez un éditeur de texte et utilisez cet exemple pour une analyse complète.

    ```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
      "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>Label</key>
        <string>com.microsoft.wdav.schedfullscan</string>
        <key>ProgramArguments</key>
        <array>
            <string>sh</string>
            <string>-c</string>
            <string>/usr/local/bin/mdatp scan full</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>StartCalendarInterval</key>
        <dict>
            <key>Day</key>
            <integer>3</integer>
            <key>Hour</key>
            <integer>2</integer>
            <key>Minute</key>
            <integer>0</integer>
            <key>Weekday</key>
            <integer>5</integer>
        </dict>
        <key>WorkingDirectory</key>
        <string>/usr/local/bin/</string>
    </dict>
    </plist>
     ```

2. Enregistrez le fichier *sous com.microsoft.wdav.schedfullscan.plist*.
 
### <a name="load-your-file"></a>Charger votre fichier

1. Ouvrez **terminal**.
2. Entrez les commandes suivantes pour charger votre fichier :

    ```bash
    launchctl load /Library/LaunchDaemons/<your file name.plist>
    launchctl start <your file name>
    ```

3. Votre analyse programmée s’exécutera à la date, à l’heure et à la fréquence que vous avez définies dans votre liste p. Dans les exemples ci-dessus, l’analyse s’exécute à 02:00 tous les vendredis. 

    La `Weekday` valeur `StartCalendarInterval` d’utilise un nombre integer pour indiquer le cinquième jour de la semaine ou le vendredi.

 > [!IMPORTANT]
 > Les agents exécutés *avec lancement* ne s’exécutent pas à l’heure prévue pendant que l’appareil est en veille. Ils s’exécutent à la place une fois que l’appareil reprend en mode veille.
 >
 > Si l’appareil est désactivé, l’analyse s’exécutera à la prochaine heure d’analyse programmée.

## <a name="schedule-a-scan-with-intune"></a>Planifier une analyse avec Intune

Vous pouvez également planifier des analyses avec Microsoft Intune. Le [script runMDATPQuickScan.sh](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP#runmdatpquickscansh) shell disponible dans [scripts pour Microsoft Defender pour](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP) le point de terminaison est persistant lorsque l’appareil reprend le mode veille. 

Voir Utiliser des scripts shell sur les appareils macOS dans [Intune](/mem/intune/apps/macos-shell-scripts) pour obtenir des instructions plus détaillées sur l’utilisation de ce script dans votre entreprise.
