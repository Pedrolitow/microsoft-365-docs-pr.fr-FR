---
title: Planification d’une analyse antivirus à l’aide d’Anacron dans Microsoft Defender pour point de terminaison sur Linux
description: Découvrez comment planifier une analyse antivirus dans Microsoft Defender pour point de terminaison sur Linux pour une meilleure protection des ressources de votre organisation.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, analyses, antivirus, microsoft defender pour point de terminaison sur linux
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
ms.openlocfilehash: ad13d3e403f3fad81bec275506017f2da4066737
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68223917"
---
# <a name="schedule-an-antivirus-scan-using-anacron-in-microsoft-defender-for-endpoint-on-linux"></a>Planifier une analyse antivirus à l’aide d’Anacron dans Microsoft Defender pour point de terminaison sur Linux

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Pour exécuter une analyse de Microsoft Defender Antivirus pour Linux, consultez [Commandes prises en charge](/microsoft-365/security/defender-endpoint/linux-resources#supported-commands).

> [!NOTE]
> Cet article prend en charge Microsoft Defender pour point de terminaison sur les distributions Linux pour Red Hat Enterprise (RHEL).

## <a name="system-requirements"></a>Configuration requise

Consultez la configuration système requise pour planifier Microsoft Defender’analyse antivirus dans Microsoft Defender point de terminaison sur Linux.

- Distributions et versions de serveur Linux : Red Hat Enterprise Linux 7.2 ou version ultérieure.
- L’option **FANOTIFY** dans le noyau doit être activée.

## <a name="scheduling-microsoft-defender-antivirus-scan-in-red-hat-linux"></a>Planification de l’analyse antivirus Microsoft Defender dans Red Hat Linux

Vous pouvez planifier des travaux cron pour lancer Microsoft Defender analyses antivirus selon une planification. Pour plus d’informations, consultez [Comment planifier des analyses avec Microsoft Defender pour point de terminaison sur Linux](linux-schedule-scan-mde.md). Ce processus fonctionne bien si l’appareil est toujours opérationnel. 

Toutefois, si les appareils Linux sont arrêtés ou hors connexion pendant la planification cron, l’analyse ne s’exécutera pas. Dans ces situations, vous pouvez utiliser **anacron** pour lire l’horodatage et rechercher le dernier travail exécuté. Si l’appareil a été arrêté pendant le travail cron planifié, il doit attendre l’heure planifiée suivante. À **l’aide d’anacron**, le système détecte la dernière fois que l’analyse a été exécutée. Si l’appareil n’a pas exécuté le travail cron, il le démarre automatiquement. 

### <a name="schedule-microsoft-defender-antivirus-scans-in-red-hat-linux"></a>Planifier des analyses antivirus Microsoft Defender dans Red Hat Linux

Utilisez les étapes suivantes pour planifier des analyses :

1. Connectez-vous au serveur RedHat à l’aide de Putty.
1. Modifiez le fichier anacron : 

    ```vi /etc/anacron```

    :::image type="content" source="images/vi_etc_anacron.png" alt-text="fichier anacron":::

    ```
    # /etc/anacrontab: configuration file for anacron
    # See anacron (8) and anacrontab (5) for details.
    SHELL=/bin/sh
    PATH=/sbin:/bin:/usr/sbin:/usr/bin
    RANDOM_DELAY=45
    # Anacron jobs will start between 8pm and 11pm.
    START_HOURS_RANGE=20-23
    # delay will be 5 minutes + RANDOM_DELAY for cron.daily
    ```

1. Notez les éléments suivants dans le fichier.
    1. **Shell:** Shell est appelé ```/bin/sh```, et non comme ```/bin/bash```. N’oubliez pas lors de l’écriture des travaux.
    1. **RANDOM_DELAY :** Décrit la durée maximale en minutes pour le travail. Cette valeur est utilisée pour décaler les travaux afin qu’il n’y ait pas trop de travaux en cours d’exécution en même temps. L’utilisation de ce délai est idéale pour les solutions VDI.
    1. **START_HOURS_RANGE :** Décrit l’intervalle de temps pour exécuter le travail.
    1. **cron.daily :** Décrit 1 comme la période de jours nécessaire pour la fréquence des exécutions de travaux. 5 est le délai en minutes pendant lequel anacron attend après le redémarrage de l’appareil.

1. Examinez les travaux anacron :

    ```ls -lh /etc/cron*```

    :::image type="content" source="images/ls_lh_etc_cron.png" alt-text="travaux anacron":::

    ```
    [root@enaredhat7 /] # 1s -1h /etc/cron*
    - rw - - - - - - -. 1   root    root    0   Nov 30  2021    /etc/cron.deny
    - rw - r - - r - -. 1   root    root    451 Dec 27  2013    /etc/crontab

    /etc/cron.d:
    total 28k
    - rw - r - - r - -. 1   root    root    128 Nov 30  2021    0hourly
    - rw - r - - r - -. 1   root    root    121 Feb 25  18:11   omilogotate
    - rw - r - - r - -. 1   root    root    118 Feb 25  18:14   omsagent
    - rw - r - - r - -. 1   root    root    79  Feb 25  18:15   OMSConsistencyInvoker
    - rw - r - - r - -. 1   root    root    108 Nov 9   2021    raid-check
    - rw - r - - r - -. 1   root    root    135 Jun 1   22:35   scxagent
    - rw - - - - - - -. 1   root    root    235 Jan 20  2020    sysstat

    /etc/cron.daily:
    total 24k
    - rwxr - xr - x.    1   root    root    127 Jun 14  16:49   avscandaily
    - rwx - - - - - -.  1   root    root    219 Aug 7   2019    logrotate
    - rwxr - xr - x.    1   root    root    618 Jul 10  2018    man-db.cron
    - rwx - - - - - -.  1   root    root    208 Nov 9   2017    mlocate
    - rwx - - - - - -.  1   root    root    558 Apr 18  19:03   rhsmd
    - rwxr - xr - x.    1   root    root    114 Apr 8   2021    rhui-update-client

    /etc/cron.hourly:
    total 8.0k
    - rwxr - xr - x.    1   root    root    392 Nov 30  2021    0anacron
    - rwxr - xr - x.    1   root    root    131 Jun 14  17:05   update

    /etc/cron.monthly:
    total 0
    - rwxr - xr - x.    1   root    root    0   Jun 14  17:47   mdatpupdate
    
    /etc/cron.weekly:
    total 0
    ```

1. Ignorez le ```/etc/cron.d``` répertoire, vous verrez ```/etc/corn.daily, hourly, monthly, and weekly```. 

1. Pour planifier une analyse antivirus hebdomadaire, vous pouvez créer un fichier (Travail) sous le ```/etc/cron.weekly``` répertoire.

    ```cd /etc/cron.weekly```

   ``` vi mdavfullscan```

    ```Press Insert```
    
    :::image type="content" source="images/vi_mdavfullscan.png" alt-text="analyses antivirus hebdomadaires":::

   ```
    #!/bin/sh
    set -e
    echo    $(date)     “Time Scan Begins”  >>/logs/mdav_avacron_full_scan.log
    /bin/mdatp scan full >> /logs/mdav_avacron_full_scan.log
    echo    $(date) “Time Scan Finished”        >>/logs/mdav_avacron_full_scan.log
    exit    0
    ~
    ```

    ```Press Esc```

    ```Type: wq!```

1. Modifiez les autorisations de fichier pour permettre l’exécution du fichier.

    ```Chmod 755 mdavfullscan```

    ```ls -la```

    :::image type="content" source="images/chmod-755-mdavfullscan.png" alt-text="7. Modifier les autorisations de fichier":::

    ```
    [root@enaredhat7    cron.weekly]# 1s -1a
    total   16
    drwxr - xr – x. 2   root    root    26  Jun 14  19:19   .
    drwxr - xr – x. 85  root    root    8192    Jun 14  19:01   ..
    - rw - r - - r - -. 1   root    root    128 Jun 14  19:19   mdavfullscan
    [root@enaredhat7 cron.weekly] # chmod 755 mdavfullscan
    [root@enaredhat7 cron.weekly] # 1s  -1h
    total 4. 0k
    - rwxr - xr – x.    1   root    root    128 Jun 14  19:19   mdavfullscan
    [root@enaredhat7 cron.weekly] #
    ```

1. Utilisez la commande pour tester le travail anacron hebdomadaire.
    
    ```./mdavfullscan```

1. Utilisez la commande pour vérifier que le travail s’est correctement exécuté.

    ```cat /logs/mdav_avacron_full_scan.log```

    :::image type="content" source="images/mdav_avacron_full_scan_log.png" alt-text="vérifier que le travail a été exécuté":::

    ```
    [root@enaredhat7    cron.weekly] # cat  / logs / mdav_avacron_full_scan.log
    Tue Jun 14  20:20:44    UTC 2022 Time Scan Begins
    Scan has finished
        66547   file(s) scanned
    0   threat(s) detected
    Tue Jun 14  20:20:50    UTC 2022 Time Scan Finished
    [root@enaredhat7 cron.weekly] #
    ```
