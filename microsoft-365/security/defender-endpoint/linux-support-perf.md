---
title: Résoudre les problèmes de performances pour Microsoft Defender pour endpoint sur Linux
description: Résolution des problèmes de performances dans Microsoft Defender pour Point de terminaison sur Linux.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, performances
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
mms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 362e0f20b23068027e65199f3800bd4f315ec2a0
ms.sourcegitcommit: b3c4816b55657b87ed4a5f6a4abe3d505392218e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2021
ms.locfileid: "53726464"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Résoudre les problèmes de performances pour Microsoft Defender pour endpoint sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Cet article fournit quelques étapes générales qui peuvent être utilisées pour affiner les problèmes de performances liés à Defender pour Endpoint sur Linux.

La protection en temps réel (RTP) est une fonctionnalité de Defender for Endpoint sur Linux qui surveille et protège en permanence votre appareil contre les menaces. Il se compose de la surveillance des fichiers et des processus, ainsi que d’autres heuristiques.

Selon les applications que vous exécutez et les caractéristiques de votre appareil, vous pouvez obtenir des performances sous-optimales lors de l’exécution de Defender pour Endpoint sur Linux. En particulier, les applications ou les processus système qui accèdent à de nombreuses ressources sur un court laps de temps peuvent entraîner des problèmes de performances dans Defender pour Endpoint sur Linux.

Avant de commencer, assurez-vous que les autres produits de sécurité ne sont pas en cours **d’exécution sur l’appareil.** Plusieurs produits de sécurité peuvent être en conflit et avoir un impact sur les performances de l’hôte.

Les étapes suivantes peuvent être utilisées pour résoudre et atténuer ces problèmes :

1. Désactivez la protection en temps réel à l’aide de l’une des méthodes suivantes et observez si les performances s’améliorent. Cette approche permet de déterminer si Defender for Endpoint sur Linux contribue aux problèmes de performances.

    Si votre appareil n’est pas géré par votre organisation, la protection en temps réel peut être désactivée à partir de la ligne de commande :

    ```bash
    mdatp config real-time-protection --value disabled
    ```
    ```Output
    Configuration property updated
    ```

    Si votre appareil est géré par votre organisation, la protection en temps réel peut être désactivée par votre administrateur à l’aide des instructions de définir les préférences pour [Defender pour Endpoint sur Linux.](linux-preferences.md)

    Si le problème de performances persiste alors que la protection en temps réel est éteinte, l’origine du problème peut être protection évolutive des points de terminaison composant. Dans ce cas, contactez le support technique pour obtenir des instructions supplémentaires et des mesures de prévention.

2. Pour rechercher les applications qui déclenchent le plus grand nombre d’analyses, vous pouvez utiliser des statistiques en temps réel recueillies par Defender pour Endpoint sur Linux.

    > [!NOTE]
    > Cette fonctionnalité est disponible dans la version 100.90.70 ou une version plus récente.

    Cette fonctionnalité est activée par défaut sur les `Dogfood` canaux et les `InsiderFast` canaux. Si vous utilisez un autre canal de mise à jour, cette fonctionnalité peut être activée à partir de la ligne de commande :
    ```bash
    mdatp config real-time-protection-statistics --value enabled
    ```

    Cette fonctionnalité nécessite une protection en temps réel pour être activée. Pour vérifier l’état de la protection en temps réel, exécutez la commande suivante :

    ```bash
    mdatp health --field real_time_protection_enabled
    ```

    Vérifiez que `real_time_protection_enabled` l’entrée est `true` . Sinon, exécutez la commande suivante pour l’activer :

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
    > L’utilisation (notez le tiret double) permet de s’assurer que le format de sortie ```--output json``` est prêt pour l’utilisation.

    Le résultat de cette commande affiche tous les processus et l’activité d’analyse associée.

3. Sur votre système Linux, téléchargez l’exemple d’analyseur Python **high_cpu_parser.py** à l’aide de la commande :

    ```bash
    wget -c https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```
    La sortie de cette commande doit être similaire à celle-ci :

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

      La sortie de ce qui précède est une liste des principaux contributeurs aux problèmes de performances. La première colonne est l’identificateur de processus (PID), la deuxième colonne est le nom du processus et la dernière colonne le nombre de fichiers analysés, triés par impact.
    Par exemple, la sortie de la commande ressemblera à ce qui suit : 

    ```Output
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

    Pour améliorer les performances de Defender pour Endpoint sur Linux, recherchez celui qui a le plus grand nombre sous la ligne et ajoutez une `Total files scanned` exclusion pour celui-ci. Pour plus d’informations, voir Configurer et valider des [exclusions pour Defender pour Endpoint sur Linux.](linux-exclusions.md)

    >[!NOTE]
    > L’application stocke les statistiques en mémoire et suit uniquement l’activité des fichiers depuis son début et que la protection en temps réel a été activée. Les processus qui ont été lancés avant ou pendant les périodes où la protection en temps réel était hors programme ne sont pas comptabilisés. En outre, seuls les événements qui ont déclenché des analyses sont comptés.

5. Configurez Microsoft Defender pour endpoint sur Linux avec des exclusions pour les processus ou les emplacements de disque qui contribuent aux problèmes de performances et activez à nouveau la protection en temps réel.

    Pour plus d’informations, consultez [Configurer et valider les exclusions pour Microsoft Defender pour point de terminaison sur Linux](linux-exclusions.md).

## <a name="see-also"></a>Voir aussi
- [Rechercher les problèmes d’état d’intégrité de l’agent](health-status.md)
