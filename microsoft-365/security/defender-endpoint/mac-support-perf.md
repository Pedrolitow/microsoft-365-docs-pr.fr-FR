---
title: Résoudre les problèmes de performances pour Microsoft Defender pour point de terminaison sur macOS
description: Résoudre les problèmes de performances dans Microsoft Defender pour point de terminaison sur macOS.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, performances
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 7c60a61ca1a0a1179abd27c0f6d59970a0c09866
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2022
ms.locfileid: "66969536"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Résoudre les problèmes de performances pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique fournit des étapes générales qui peuvent être utilisées pour limiter les problèmes de performances liés à Microsoft Defender pour point de terminaison sur macOS.

La protection en temps réel (RTP) est une fonctionnalité de Microsoft Defender pour point de terminaison sur macOS qui surveille et protège en permanence votre appareil contre les menaces. Il se compose de la surveillance des fichiers et des processus et d’autres heuristiques.

Selon les applications que vous exécutez et les caractéristiques de votre appareil, vous pouvez rencontrer des performances non optimales lors de l’exécution de Microsoft Defender pour point de terminaison sur macOS. En particulier, les applications ou les processus système qui accèdent à de nombreuses ressources sur un court intervalle de temps peuvent entraîner des problèmes de performances dans Microsoft Defender pour point de terminaison sur macOS.

Les étapes suivantes peuvent être utilisées pour résoudre et atténuer ces problèmes :

1. Désactivez la protection en temps réel à l’aide de l’une des méthodes suivantes et observez si les performances s’améliorent. Cette approche permet de déterminer si Microsoft Defender pour point de terminaison sur macOS contribue aux problèmes de performances.

      Si votre appareil n’est pas géré par votre organisation, la protection en temps réel peut être désactivée à l’aide de l’une des options suivantes :

    - À partir de l’interface utilisateur. Ouvrez Microsoft Defender pour point de terminaison sur macOS et accédez à **Gérer les paramètres**.

      :::image type="content" source="images/mdatp-36-rtp.png" alt-text=" Page Gérer la protection en temps réel" lightbox="images/mdatp-36-rtp.png":::
      

    - À partir du terminal. Pour des raisons de sécurité, cette opération nécessite une élévation.

      ```bash
      mdatp config real-time-protection --value disabled
      ```

      Si votre appareil est géré par votre organisation, la protection en temps réel peut être désactivée par votre administrateur en suivant les instructions [fournies dans Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md).

      Si le problème de performances persiste pendant que la protection en temps réel est désactivée, l’origine du problème peut être le composant de détection et de réponse du point de terminaison. Dans ce cas, contactez le support technique pour obtenir des instructions supplémentaires et des mesures d’atténuation.

2. Ouvrez Finder et accédez à **Applications** \> **Utilities**. Ouvrez **le Moniteur d’activité** et analysez les applications qui utilisent les ressources de votre système. Les compilateurs et les compilateurs sont des exemples typiques.

3. Pour rechercher les applications qui déclenchent le plus d’analyses, vous pouvez utiliser les statistiques en temps réel collectées par Defender pour point de terminaison sur Mac.

      > [!NOTE]
      > Cette fonctionnalité est disponible dans la version 100.90.70 ou ultérieure.
      Cette fonctionnalité est activée par défaut sur les canaux **Dogfood** et **InsiderFast** . Si vous utilisez un autre canal de mise à jour, cette fonctionnalité peut être activée à partir de la ligne de commande :

      ```bash
      mdatp config real-time-protection-statistics  --value enabled
      ```

      Cette fonctionnalité nécessite une protection en temps réel pour être activée. Pour vérifier l’état de la protection en temps réel, exécutez la commande suivante :

      ```bash
      mdatp health --field real_time_protection_enabled
      ```

    Vérifiez que **l’entrée real_time_protection_enabled** est vraie. Sinon, exécutez la commande suivante pour l’activer :

      ```bash
      mdatp config real-time-protection --value enabled
      ```

      ```output
      Configuration property updated
      ```

      Pour collecter les statistiques actuelles, exécutez :

      ```bash
      mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
      ```

      > [!NOTE]
      > L’utilisation **de --output json** (notez le tiret double) garantit que le format de sortie est prêt pour l’analyse.
      La sortie de cette commande affiche tous les processus et leur activité d’analyse associée.

4. Sur votre système Mac, téléchargez l’exemple d’analyseur Python high_cpu_parser.py à l’aide de la commande :

    ```bash
    curl -O https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    La sortie de cette commande doit être similaire à ce qui suit :

    ```Output
    --2020-11-14 11:27:27-- https://raw.githubusercontent.com/microsoft.
    mdatp-xplat/master/linus/diagnostic/high_cpu_parser.py
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.xxx.xxx
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)| 151.101.xxx.xxx| :443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1020 [text/plain]
    Saving to: 'high_cpu_parser.py'
    100%[===========================================>] 1,020    --.-K/s   in
    0s
    ```

5. Ensuite, tapez les commandes suivantes :

      ```bash
        chmod +x high_cpu_parser.py
      ```

      ```bash
        cat real_time_protection.json | python high_cpu_parser.py  > real_time_protection.log
      ```

      La sortie de ce qui précède est une liste des principaux contributeurs aux problèmes de performances. La première colonne est l’identificateur de processus (PID), la deuxième colonne est le nom du processus te et la dernière colonne est le nombre de fichiers analysés, triés par impact.

      Par exemple, la sortie de la commande ressemble à ce qui suit :

      ```output
        ... > python ~/repo/mdatp-xplat/linux/diagnostic/high_cpu_parser.py <~Downloads/output.json | head -n 10
        27432 None 76703
        73467 actool     1249
        73914 xcodebuild 1081
        73873 bash 1050
        27475 None 836
        1    launchd    407
        73468 ibtool     344
        549  telemetryd_v1   325
        4764 None 228
        125  CrashPlanService 164
      ```

      Pour améliorer les performances de Defender pour point de terminaison sur Mac, recherchez celui avec le nombre le plus élevé sous la ligne Total des fichiers analysés et ajoutez une exclusion pour celui-ci. Pour plus d’informations, consultez [Configurer et valider les exclusions pour Defender pour point de terminaison sur macOS](mac-exclusions.md).

      > [!NOTE]
      > L’application stocke les statistiques en mémoire et effectue uniquement le suivi de l’activité des fichiers depuis son démarrage et l’activation de la protection en temps réel. Les processus qui ont été lancés avant ou pendant les périodes où la protection en temps réel était désactivée ne sont pas comptabilisés. En outre, seuls les événements qui ont déclenché des analyses sont comptabilisés.
      >
6. Configurez Microsoft Defender pour point de terminaison sur macOS avec des exclusions pour les processus ou les emplacements de disque qui contribuent aux problèmes de performances et réactivez la protection en temps réel.

     Pour plus d’informations, consultez [Configurer et valider les exclusions pour Microsoft Defender pour point de terminaison sur macOS](mac-exclusions.md).
