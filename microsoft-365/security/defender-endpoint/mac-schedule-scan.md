---
title: Comment planifier des analyses avec Microsoft Defender pour point de terminaison sur macOS
description: Découvrez comment planifier une heure d’analyse automatique pour Microsoft Defender pour point de terminaison dans macOS afin de mieux protéger les ressources de votre organisation.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, scans, antivirus, catalina, big sur, monterey, ventura, mde pour mac
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
ms.openlocfilehash: 791288321d6968d63ba551e0872491a773ce53d4
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68769378"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>Planifier des analyses avec Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bien que vous puissiez démarrer une analyse des menaces à tout moment avec Microsoft Defender pour point de terminaison, votre entreprise peut tirer parti des analyses planifiées ou chronomodées. Par exemple, vous pouvez planifier l’exécution d’une analyse au début de chaque jour ou semaine. 

## <a name="schedule-a-scan-with-launchd"></a>Planifier une analyse avec *lancement*

Vous pouvez créer une planification d’analyse à l’aide du démon *lancé* sur un appareil macOS.

Pour plus d’informations sur le format de fichier *.plist* utilisé ici, voir [About Information Property List Files](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) sur le site web officiel des développeurs Apple.

### <a name="schedule-a-quick-scan"></a>Planifier une analyse rapide

Le code suivant montre le schéma que vous devez utiliser pour planifier une analyse rapide. 

1. Ouvrez un éditeur de texte et utilisez cet exemple comme guide pour votre propre fichier d’analyse planifiée.

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

2. Enregistrez le fichier sous *com.microsoft.wdav.schedquickscan.plist*.

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
            <integer>50</integer>
            <key>Weekday</key>
            <integer>5</integer>
        </dict>
        <key>WorkingDirectory</key>
        <string>/usr/local/bin/</string>
    </dict>
    </plist>
     ```

2. Enregistrez le fichier sous *com.microsoft.wdav.schedfullscan.plist*.
 
### <a name="load-your-file"></a>Charger votre fichier

1. Ouvrez **Terminal**.
2. Entrez les commandes suivantes pour charger votre fichier :

    ```bash
    launchctl load /Library/LaunchDaemons/<your file name.plist>
    launchctl start <your file name>
    ```

3. Votre analyse planifiée s’exécutera à la date, à l’heure et à la fréquence que vous avez définies dans votre liste p. Dans les exemples précédents, l’analyse s’exécute à 2 h 50 tous les vendredis. 

    - La `Weekday` valeur de `StartCalendarInterval` utilise un entier pour indiquer le cinquième jour de la semaine ou le vendredi. La plage est comprise entre 0 et 7, 7 représentant le dimanche.
    - La `Day` valeur de `StartCalendarInterval` utilise un entier pour indiquer le troisième jour du mois. La plage est comprise entre 1 et 31.
    - La `Hour` valeur de `StartCalendarInterval` utilise un entier pour indiquer la deuxième heure de la journée. La plage est comprise entre 0 et 24.
    La `Minute` valeur de `StartCalendarInterval` utilise un entier pour indiquer cinquante minutes de l’heure. La plage est comprise entre 0 et 59.
    
    
 > [!IMPORTANT]
 > Les agents exécutés avec *launchd* ne s’exécutent pas à l’heure planifiée pendant que l’appareil est en veille. Ils s’exécutent à la place une fois que l’appareil reprend le mode veille.
 >
 > Si l’appareil est éteint, l’analyse s’exécutera à l’heure d’analyse planifiée suivante.

## <a name="schedule-a-scan-with-intune"></a>Planifier une analyse avec Intune

Vous pouvez également planifier des analyses avec Microsoft Intune. Le script [d’interpréteur de commandes runMDATPQuickScan.sh](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP#runmdatpquickscansh) disponible dans [Scripts pour Microsoft Defender pour point de terminaison](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP) est conservé lorsque l’appareil passe du mode veille. 

Consultez [Utiliser des scripts shell sur des appareils macOS dans Intune](/mem/intune/apps/macos-shell-scripts) pour obtenir des instructions plus détaillées sur l’utilisation de ce script dans votre entreprise.
