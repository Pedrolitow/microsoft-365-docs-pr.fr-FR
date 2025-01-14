---
title: Résoudre les problèmes de performances pour Microsoft Defender pour point de terminaison sur macOS
description: Résolvez les problèmes de performances dans Microsoft Defender pour point de terminaison sur macOS.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, performance, catalina, big sur, monterey, ventura, mde pour mac
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
ms.openlocfilehash: 738c21b637e0708c86937044cd4c026ba99e162e
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68768630"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Résoudre les problèmes de performances pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique fournit quelques étapes générales qui peuvent être utilisées pour limiter les problèmes de performances liés à Microsoft Defender pour point de terminaison sur macOS.


Selon les applications que vous exécutez et les caractéristiques de votre appareil, vous pouvez rencontrer des performances non optimales lors de l’exécution de Microsoft Defender pour point de terminaison sur macOS. En particulier, les applications ou les processus système qui accèdent à de nombreuses ressources sur une courte période peuvent entraîner des problèmes de performances dans Microsoft Defender pour point de terminaison sur macOS.

>[!WARNING]
>Avant de commencer, vérifiez que les autres produits de sécurité ne sont pas en cours d’exécution sur l’appareil. Plusieurs produits de sécurité peuvent entrer en conflit et avoir un impact sur les performances de l’hôte.

## <a name="troubleshoot-performance-issues-using-real-time-protection-statistics"></a>Résoudre les problèmes de performances à l’aide des statistiques de protection en temps réel

**S’applique à :**
- Seuls les problèmes de performances liés à l’antivirus

La protection en temps réel (RTP) est une fonctionnalité de Defender pour point de terminaison sur macOS qui surveille et protège en permanence votre appareil contre les menaces. Il se compose de la surveillance des fichiers et des processus et d’autres heuristiques.

Les étapes suivantes peuvent être utilisées pour résoudre et atténuer ces problèmes :

1. Désactivez la protection en temps réel à l’aide de l’une des méthodes suivantes et observez si les performances s’améliorent. Cette approche permet de déterminer si Microsoft Defender pour point de terminaison sur macOS contribue aux problèmes de performances.

      Si votre appareil n’est pas géré par votre organisation, la protection en temps réel peut être désactivée à l’aide de l’une des options suivantes :

    - À partir de l’interface utilisateur. Ouvrez Microsoft Defender pour point de terminaison sur macOS et accédez à **Gérer les paramètres**.

      :::image type="content" source="images/mdatp-36-rtp.png" alt-text=" Page Gérer la protection en temps réel" lightbox="images/mdatp-36-rtp.png":::

    - À partir du terminal. Pour des raisons de sécurité, cette opération nécessite une élévation.

      ```bash
      mdatp config real-time-protection --value disabled
      ```

      Si votre appareil est géré par votre organisation, la protection en temps réel peut être désactivée par votre administrateur à l’aide des instructions fournies dans [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md).

      Si le problème de performances persiste alors que la protection en temps réel est désactivée, l’origine du problème peut être le composant de détection et de réponse de point de terminaison. Dans ce cas, contactez le support client pour obtenir des instructions supplémentaires et des mesures d’atténuation.

2. Ouvrez Finder et accédez à **Utilitaires d’applications**\>. Ouvrez **le Moniteur d’activité** et analysez les applications qui utilisent les ressources de votre système. Les exemples classiques incluent les compilateurs et les éditeurs de mises à jour logicielles.

3. Pour trouver les applications qui déclenchent le plus d’analyses, vous pouvez utiliser les statistiques en temps réel collectées par Defender pour point de terminaison sur Mac.

      > [!NOTE]
      > Cette fonctionnalité est disponible dans la version 100.90.70 ou ultérieure.
      Cette fonctionnalité est activée par défaut sur les canaux **Dogfood** et **InsiderFast** . Si vous utilisez un autre canal de mise à jour, cette fonctionnalité peut être activée à partir de la ligne de commande :

      ```bash
      mdatp config real-time-protection-statistics  --value enabled
      ```

      Cette fonctionnalité nécessite l’activation de la protection en temps réel. Pour vérifier l’état de la protection en temps réel, exécutez la commande suivante :

      ```bash
      mdatp health --field real_time_protection_enabled
      ```

    Vérifiez que l’entrée **real_time_protection_enabled** est true. Sinon, exécutez la commande suivante pour l’activer :

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
      La sortie de cette commande affiche tous les processus et l’activité d’analyse associée.

4. Sur votre système Mac, téléchargez l’exemple d’analyseur Python high_cpu_parser.py à l’aide de la commande :

    ```bash
    curl -O https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    La sortie de cette commande doit ressembler à ce qui suit :

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

      La sortie de ce qui précède est une liste des principaux contributeurs aux problèmes de performances. La première colonne est l’identificateur de processus (PID), la deuxième colonne est le nom du processus et la dernière colonne correspond au nombre de fichiers analysés, triés par impact.

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

      Pour améliorer les performances de Defender pour point de terminaison sur Mac, recherchez celui dont le nombre est le plus élevé sous la ligne Nombre total de fichiers analysés et ajoutez une exclusion pour celui-ci. Pour plus d’informations, consultez [Configurer et valider des exclusions pour Defender pour point de terminaison sur macOS](mac-exclusions.md).

      > [!NOTE]
      > L’application stocke les statistiques en mémoire et effectue uniquement le suivi de l’activité des fichiers depuis son démarrage et l’activation de la protection en temps réel. Les processus lancés avant ou pendant les périodes où la protection en temps réel était désactivée ne sont pas pris en compte. En outre, seuls les événements qui ont déclenché des analyses sont comptabilisés.
      >
6. Configurez Microsoft Defender pour point de terminaison sur macOS avec des exclusions pour les processus ou les emplacements de disque qui contribuent aux problèmes de performances et réactivent la protection en temps réel.

     Pour plus d’informations[, consultez Configurer et valider des exclusions pour Microsoft Defender pour point de terminaison sur macOS](mac-exclusions.md).

## <a name="troubleshoot-performance-issues-using-microsoft-defender-for-endpoint-client-analyzer"></a>Résoudre les problèmes de performances à l’aide de Microsoft Defender pour point de terminaison Client Analyzer

**S’applique à :**
- Problèmes de performances de tous les composants Defender pour point de terminaison disponibles tels que AV et EDR

L’analyseur client Microsoft Defender pour point de terminaison (MDECA) peut collecter des traces, des journaux et des informations de diagnostic afin de résoudre les problèmes de performances sur [les appareils intégrés](/microsoft-365/security/defender-endpoint/onboard-configure) sur macOS.

> [!NOTE]
>
> - L’outil Analyseur client Microsoft Defender pour point de terminaison est régulièrement utilisé par les services de support technique Microsoft (CSS) pour collecter des informations telles que (mais sans s’y limiter) des adresses IP et des noms de PC qui vous aideront à résoudre les problèmes que vous pouvez rencontrer avec Microsoft Defender pour point de terminaison. Pour plus d’informations sur notre déclaration de confidentialité, consultez [Déclaration de confidentialité Microsoft](https://privacy.microsoft.com/privacystatement).
> - En règle générale, il est recommandé de mettre à jour [l’agent Microsoft Defender pour point de terminaison vers la dernière version disponible](linux-whatsnew.md) et de confirmer que le problème persiste avant de poursuivre l’examen.

Pour exécuter l’analyseur client afin de résoudre les problèmes de performances, consultez [Exécuter l’analyseur client sur macOS et Linux](run-analyzer-macos-linux.md).

> [!NOTE]
> Si, après avoir suivi les étapes ci-dessus, le problème de performances persiste, contactez le support client pour obtenir des instructions supplémentaires et des mesures d’atténuation.

## <a name="see-also"></a>Voir aussi

- [Rechercher les problèmes d’état d’intégrité de l’agent](health-status.md)
