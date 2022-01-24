---
title: Résoudre les problèmes de performances pour Microsoft Defender pour point de terminaison sur Linux
description: Résolution des problèmes de performances dans Microsoft Defender pour point de terminaison sur Linux.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, performances
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
ms.openlocfilehash: 6f7a3404ec0ae64e3dcdc4d6a3072e7fc2936646
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2022
ms.locfileid: "62172450"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Résoudre les problèmes de performances pour Microsoft Defender pour point de terminaison sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Ce document fournit des instructions sur la façon de limiter les problèmes de performances liés à Defender for Endpoint sur Linux à l’aide des outils de diagnostic disponibles pour comprendre et atténuer la ressource existante et les processus qui placent le système dans de telles situations. Les problèmes de performances sont principalement causés par des goulots d’étranglement dans un ou plusieurs sous-systèmes matériels, selon le profil de l’utilisation des ressources sur le système. Parfois, les applications sont sensibles aux ressources d’I/S disque et peuvent avoir besoin d’une plus grande capacité de processeur, et parfois certaines configurations ne sont pas durables, et peuvent déclencher trop de nouveaux processus et ouvrir trop de descripteurs de fichiers.

Selon les applications que vous exécutez et les caractéristiques de votre appareil, vous pouvez obtenir des performances sous-optimales lors de l’exécution de Defender pour Endpoint sur Linux. En particulier, les applications ou les processus système qui accèdent à de nombreuses ressources telles que le processeur, le disque et la mémoire sur un court laps de temps peuvent entraîner des problèmes de performances dans Defender pour Endpoint sur Linux.

> [!WARNING]
> Avant de commencer, assurez-vous que les autres produits de sécurité ne sont pas en cours **d’exécution sur l’appareil.** Plusieurs produits de sécurité peuvent être en conflit et avoir un impact sur les performances de l’hôte.

## <a name="troubleshoot-performance-issues-using-real-time-protection-statistics"></a>Résoudre les problèmes de performances à l’aide des statistiques de protection en temps réel

**S’applique à :**
- Uniquement les problèmes de performances liés à l’antivirus

La protection en temps réel (RTP) est une fonctionnalité de Defender for Endpoint sur Linux qui surveille et protège en permanence votre appareil contre les menaces. Il se compose de la surveillance des fichiers et des processus et d’autres heuristiques.

Les étapes suivantes peuvent être utilisées pour résoudre et atténuer ces problèmes :

1. Désactivez la protection en temps réel à l’aide de l’une des méthodes suivantes et observez si les performances sont améliorées. Cette approche permet de déterminer si Defender for Endpoint sur Linux contribue aux problèmes de performances.

    Si votre appareil n’est pas géré par votre organisation, la protection en temps réel peut être désactivée à partir de la ligne de commande :

    ```bash
    mdatp config real-time-protection --value disabled
    ```

    ```Output
    Configuration property updated
    ```

    Si votre appareil est géré par votre organisation, la protection en temps réel peut être désactivée par votre administrateur à l’aide des instructions dans Définir les préférences pour [Defender pour Endpoint sur Linux.](linux-preferences.md)

    > [!NOTE]
    > Si le problème de performances persiste alors que la protection en temps réel est éteinte, l’origine du problème peut être le composant protection évolutive des points de terminaison (PEPT). Dans ce cas, suivez les étapes de la section Résolution des problèmes de performances à l’aide de **Microsoft Defender pour Endpoint Client Analyzer** de cet article.

2. Pour rechercher les applications qui déclenchent le plus d’analyses, vous pouvez utiliser des statistiques en temps réel recueillies par Defender pour Endpoint sur Linux.

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

    > [!NOTE]
    > L’application stocke les statistiques en mémoire et suit uniquement l’activité des fichiers depuis son début et que la protection en temps réel a été activée. Les processus qui ont été lancés avant ou pendant les périodes où la protection en temps réel était hors programme ne sont pas comptabilisés. En outre, seuls les événements qui ont déclenché des analyses sont comptés.

5. Configurez Microsoft Defender pour endpoint sur Linux avec des exclusions pour les processus ou les emplacements de disque qui contribuent aux problèmes de performances et activez à nouveau la protection en temps réel.

    Pour plus d’informations, consultez [Configurer et valider les exclusions pour Microsoft Defender pour point de terminaison sur Linux](linux-exclusions.md).

## <a name="troubleshoot-performance-issues-using-microsoft-defender-for-endpoint-client-analyzer"></a>Résoudre les problèmes de performances à l’aide de Microsoft Defender pour Endpoint Client Analyzer

**S’applique à :**
- Problèmes de performances de tous les composants Defender pour point de terminaison disponibles, tels que av et PEPT  

Microsoft Defender for Endpoint Client Analyzer (MDECA) peut collecter des suivis, des journaux [](/microsoft-365/security/defender-endpoint/onboard-configure) et des informations de diagnostic afin de résoudre les problèmes de performances sur les appareils intégrés sur Linux.

> [!NOTE]
> L’outil Microsoft Defender for Endpoint Client Analyzer est régulièrement utilisé par les services de support technique Microsoft (CSS) pour collecter des informations telles que (mais sans s’y limiter) des adresses IP, des noms de PC qui vous aideront à résoudre les problèmes que vous rencontrez peut-être avec Microsoft Defender pour le point de terminaison. Pour plus d’informations sur notre déclaration de confidentialité, voir [déclaration de confidentialité Microsoft.](https://privacy.microsoft.com/privacystatement)

### <a name="requirements"></a>Conditions requises

- L’analyseur client peut s’exécuter sur des présentations de [Linux](microsoft-defender-endpoint-linux.md#system-requirements) prise en charge avant ou après l’intégration à Microsoft Defender pour Endpoint.
- Téléchargez l’analyseur client pour Linux à partir de la dernière version d’aperçu disponible en téléchargement ici : <https://aka.ms/XMDEClientAnalyzer>
- Si votre appareil se trouve derrière un proxy, vous pouvez simplement transmettre le serveur proxy en tant que variable d’environnement au script mde_support_tool.sh. Par exemple : `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

### <a name="run-the-client-analyzer-on-linux"></a>Exécuter l’analyseur client sur Linux

Ouvrez un terminal ou un SSH sur l’ordinateur approprié et exécutez les commandes suivantes :

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`
2. `unzip -q XMDEClientAnalyzer.zip`
3. `cd XMDEClientAnalyzer`
4. `chmod +x mde_support_tool.sh`
5. Exécutez en tant qu’utilisation non racine pour installer les composants pip et lxml requis : `./mde_support_tool.sh`
6. Pour collecter le package de diagnostic réel et générer le fichier d’archivage des résultats, exécutez à nouveau en tant que racine `./mde_support_tool.sh -d` : Exemple :

   ![Image de l’exemple de ligne de commande.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

> [!NOTE]
> - L’analyseur requiert « lxml » pour produire la sortie des résultats. S’il n’est pas installé, l’analyseur essaie de l’extraire du référentiel officiel pour les packages Python ci-dessous : <https://files.pythonhosted.org/packages/\*/lxml\*.whl>
> 
> - En outre, l’outil nécessite actuellement l’installation de Python version 3 ou ultérieure.
>
> - Si vous exécutez sur un ordinateur qui ne peut pas utiliser Python 3 ou extraire le composant lxml, vous pouvez télécharger une version binaire de l’analyseur qui n’a aucune des conditions requises : [XMDE Client Analyzer Binary](https://aka.ms/XMDEClientAnalyzerBinary)

### <a name="additional-syntax-help"></a>Aide supplémentaire sur la syntaxe :

**-h** \# Aide<br>
\# Afficher le message d’aide

**performance** \# Performances<br>
\# Collecte un suivi complet pour l’analyse d’un problème de performances qui peut être reproduit à la demande. Utilisation `--length=<seconds>` pour spécifier la durée du critère.

**-o** \# Sortie<br>
\# Spécifier le chemin d’accès de destination pour le fichier de résultats

**-nz** \# No-Zip<br>
\# S’il est définie, un répertoire est créé au lieu d’un fichier d’archivage résultant

**-f** \# Force<br>
\# Overwrite si la sortie existe déjà dans le chemin de destination

### <a name="result-package-contents"></a>Contenu du package de résultats

- report.html

  Description : fichier de sortie HTML principal qui contiendra les résultats et les instructions que le script de l’analyseur peut produire sur l’ordinateur.

- mde_diagnostic.zip

  Description : sortie de diagnostic identique générée lors de l’exécution de la création de *diagnostic mdatp* sur [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  Description : sortie XML générée lors de l’exécution et utilisée pour générer le fichier de rapport html.

- Processes_information.txt

  Description : contient les détails des processus microsoft Defender pour point de terminaison en cours d’exécution sur le système.

- Log.txt

  Description : contient les mêmes messages de journal écrits à l’écran pendant la collecte de données.

- Health.txt

  Description : sortie d’état d’état de base affichée lors de l’exécution de la *commande d’état d’état mdatp.*

- Events.xml

  Description : fichier XML supplémentaire utilisé par l’analyseur lors de la génération du rapport HTML.

- Auditd_info.txt

  Description : détails sur le service audité et les composants associés pour le système [d’exploitation Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-support-events)

- perf_benchmark.tar.gz

  Description : rapports de test de performances. Vous ne le verrez que si vous utilisez le paramètre performance.

> [!NOTE]
> Dans le cas où, après avoir suivi les étapes ci-dessus, le problème de performances persiste, contactez le support technique pour obtenir des instructions supplémentaires et une atténuation.



## <a name="see-also"></a>Voir aussi

- [Rechercher les problèmes d’état d’intégrité de l’agent](health-status.md)
