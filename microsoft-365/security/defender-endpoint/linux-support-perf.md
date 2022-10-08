---
title: Résoudre les problèmes de performances pour Microsoft Defender pour point de terminaison sur Linux
description: Résoudre les problèmes de performances dans Microsoft Defender pour point de terminaison sur Linux.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, performances
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
ms.openlocfilehash: 929d1512229afd105dae872c932f4d49c24e3b47
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68225150"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Résoudre les problèmes de performances pour Microsoft Defender pour point de terminaison sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Ce document fournit des instructions sur la façon d’affiner les problèmes de performances liés à Defender pour point de terminaison sur Linux à l’aide des outils de diagnostic disponibles pour être en mesure de comprendre et d’atténuer les pénuries de ressources existantes et les processus qui rendent le système dans de telles situations. Les problèmes de performances sont principalement dus à des goulots d’étranglement dans un ou plusieurs sous-systèmes matériels, selon le profil d’utilisation des ressources sur le système. Parfois, les applications sont sensibles aux ressources d’E/S de disque et peuvent nécessiter plus de capacité d’UC, et parfois certaines configurations ne sont pas durables, et peuvent déclencher un trop grand nombre de nouveaux processus et ouvrir un trop grand nombre de descripteurs de fichiers.

Selon les applications que vous exécutez et les caractéristiques de votre appareil, vous pouvez rencontrer des performances non optimales lors de l’exécution de Defender pour point de terminaison sur Linux. En particulier, les applications ou les processus système qui accèdent à de nombreuses ressources telles que l’UC, le disque et la mémoire sur une courte période peuvent entraîner des problèmes de performances dans Defender pour point de terminaison sur Linux.

> [!WARNING]
> Avant de commencer, **assurez-vous que d’autres produits de sécurité ne sont pas en cours d’exécution sur l’appareil**. Plusieurs produits de sécurité peuvent entrer en conflit et affecter les performances de l’hôte.

## <a name="troubleshoot-performance-issues-using-real-time-protection-statistics"></a>Résoudre les problèmes de performances à l’aide des statistiques de protection en temps réel

**S’applique à :**
- Seuls les problèmes de performances liés à AV

La protection en temps réel (RTP) est une fonctionnalité de Defender pour point de terminaison sur Linux qui surveille et protège en permanence votre appareil contre les menaces. Il se compose de la surveillance des fichiers et des processus et d’autres heuristiques.

Les étapes suivantes peuvent être utilisées pour résoudre et atténuer ces problèmes :

1. Désactivez la protection en temps réel à l’aide de l’une des méthodes suivantes et observez si les performances s’améliorent. Cette approche permet de déterminer si Defender pour point de terminaison sur Linux contribue aux problèmes de performances.

    Si votre appareil n’est pas géré par votre organisation, la protection en temps réel peut être désactivée à partir de la ligne de commande :

    ```bash
    mdatp config real-time-protection --value disabled
    ```

    ```Output
    Configuration property updated
    ```

    Si votre appareil est géré par votre organisation, la protection en temps réel peut être désactivée par votre administrateur à l’aide [des instructions fournies dans Définir les préférences pour Defender pour point de terminaison sur Linux](linux-preferences.md).

    > [!NOTE]
    > Si le problème de performances persiste pendant que la protection en temps réel est désactivée, l’origine du problème peut être le composant de détection et de réponse de point de terminaison (EDR). Dans ce cas, suivez les étapes de la section **Résoudre les problèmes de performances à l’aide de Microsoft Defender pour point de terminaison section Analyseur** client de cet article.

2. Pour rechercher les applications qui déclenchent le plus d’analyses, vous pouvez utiliser les statistiques en temps réel collectées par Defender pour point de terminaison sur Linux.

    > [!NOTE]
    > Cette fonctionnalité est disponible dans la version 100.90.70 ou ultérieure.

    Cette fonctionnalité est activée par défaut sur les canaux et `InsiderFast` les `Dogfood` canaux. Si vous utilisez un autre canal de mise à jour, cette fonctionnalité peut être activée à partir de la ligne de commande :

    ```bash
    mdatp config real-time-protection-statistics --value enabled
    ```

    Cette fonctionnalité nécessite une protection en temps réel pour être activée. Pour vérifier l’état de la protection en temps réel, exécutez la commande suivante :

    ```bash
    mdatp health --field real_time_protection_enabled
    ```

    Vérifiez que l’entrée `real_time_protection_enabled` est `true`. Sinon, exécutez la commande suivante pour l’activer :

    ```bash
    mdatp config real-time-protection --value enabled
    ```

    ```Output
    Configuration property updated
    ```

    Pour collecter les statistiques actuelles, exécutez :

    ```bash
    mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
    ```

    > [!NOTE]
    > L’utilisation ```--output json``` (notez le tiret double) garantit que le format de sortie est prêt pour l’analyse.

    La sortie de cette commande affiche tous les processus et leur activité d’analyse associée.

3. Sur votre système Linux, téléchargez l’exemple d’analyseur Python **high_cpu_parser.py à l’aide de** la commande :

    ```bash
    wget -c https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    La sortie de cette commande doit être similaire à ce qui suit :


    ```Output
    --2020-11-14 11:27:27-- https://raw.githubusercontent.com/microsoft.mdatp-xplat/master/linus/diagnostic/high_cpu_parser.py
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.xxx.xxx
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)| 151.101.xxx.xxx| :443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1020 [text/plain]
    Saving to: 'high_cpu_parser.py'
    100%[===========================================>] 1,020    --.-K/s   in 0s
    ```

4. Ensuite, tapez les commandes suivantes :

    ```bash
    chmod +x high_cpu_parser.py
    ```

    ```bash
    cat real_time_protection.json | python high_cpu_parser.py  > real_time_protection.log
    ```

      La sortie de ce qui précède est une liste des principaux contributeurs aux problèmes de performances. La première colonne est l’identificateur de processus (PID), la deuxième colonne est le nom du processus et la dernière colonne est le nombre de fichiers analysés, triés par impact.
    Par exemple, la sortie de la commande ressemble à ce qui suit : 

    ```Output
    ... > python ~/repo/mdatp-xplat/linux/diagnostic/high_cpu_parser.py <~Downloads/output.json | head -n 10
    27432 None 76703
    73467 actool    1249
    73914 xcodebuild 1081
    73873 bash 1050
    27475 None 836
    1    launchd     407
    73468 ibtool     344
    549  telemetryd_v1   325
    4764 None 228
    125  CrashPlanService 164
    ```

    Pour améliorer les performances de Defender pour point de terminaison sur Linux, recherchez celui avec le nombre le plus élevé sous la `Total files scanned` ligne et ajoutez une exclusion pour celui-ci. Pour plus d’informations, consultez [Configurer et valider les exclusions pour Defender pour point de terminaison sur Linux](linux-exclusions.md).

    > [!NOTE]
    > L’application stocke les statistiques en mémoire et effectue uniquement le suivi de l’activité des fichiers depuis son démarrage et l’activation de la protection en temps réel. Les processus qui ont été lancés avant ou pendant les périodes où la protection en temps réel était désactivée ne sont pas comptabilisés. En outre, seuls les événements qui ont déclenché des analyses sont comptabilisés.

5. Configurez Microsoft Defender pour point de terminaison sur Linux avec des exclusions pour les processus ou les emplacements de disque qui contribuent aux problèmes de performances et réactivez la protection en temps réel.

    Pour plus d’informations, consultez [Configurer et valider les exclusions pour Microsoft Defender pour point de terminaison sur Linux](linux-exclusions.md).

## <a name="troubleshoot-performance-issues-using-microsoft-defender-for-endpoint-client-analyzer"></a>Résoudre les problèmes de performances à l’aide de l’analyseur client Microsoft Defender pour point de terminaison


**S’applique à :**
- Problèmes de performances de tous les composants Defender pour point de terminaison disponibles tels que AV et EDR  

L’analyseur client Microsoft Defender pour point de terminaison (MDECA) peut collecter des traces, des journaux et des informations de diagnostic afin de résoudre les problèmes de performances sur [les appareils intégrés](/microsoft-365/security/defender-endpoint/onboard-configure) sur macOS.

> [!NOTE]
>- L’outil Microsoft Defender pour point de terminaison Client Analyzer est régulièrement utilisé par les services de support technique Microsoft (CSS) pour collecter des informations telles que des adresses IP (mais pas limitées à) des noms de PC qui vous aideront à résoudre les problèmes que vous rencontrez peut-être avec Microsoft Defender pour point de terminaison. Pour plus d’informations sur notre déclaration de confidentialité, consultez [la déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/privacystatement).
>- En règle générale, il est recommandé de mettre à jour [l’agent Microsoft Defender pour point de terminaison vers la  dernière version](mac-whatsnew.md)  disponible et de confirmer que le problème persiste avant d’approfondir l’examen. 

Pour exécuter l’analyseur client pour résoudre les problèmes de performances, consultez [Exécuter l’analyseur client sur macOS et Linux](run-analyzer-macos-linux.md).

>[!NOTE]
>Si, après avoir suivi les étapes ci-dessus, le problème de performances persiste, contactez le support client pour obtenir des instructions supplémentaires et une atténuation. 

## <a name="see-also"></a>Voir aussi

- [Rechercher les problèmes d’état d’intégrité de l’agent](health-status.md)
