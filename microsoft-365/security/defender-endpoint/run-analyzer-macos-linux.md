---
title: Exécuter l’analyseur client sur macOS ou Linux
description: Découvrez comment exécuter l’analyseur client Microsoft Defender pour point de terminaison sur macOS ou Linux
keywords: analyseur client, capteur de dépannage, analyseur, mdeanalyzer, macos, linux, mdeanalyzer
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 9880ce99cecf251ced026748474f21abaafbee38
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68632555"
---
# <a name="run-the-client-analyzer-on-macos-and-linux"></a>Exécuter l’analyse du client sur macOS ou Linux


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="running-the-analyzer-through-gui-scenario"></a>Exécution de l’analyseur via un scénario d’interface graphique utilisateur

1. Téléchargez l’outil [Analyseur client XMDE](https://aka.ms/XMDEClientAnalyzer) sur l’ordinateur macOS ou Linux que vous devez examiner.

   > [!NOTE]
   > Le hachage SHA256 actuel de « XMDEClientAnalyzer.zip » téléchargé à partir du lien ci-dessus est : « D54FEAEB444127E486CE2B2646BCD3A076F58C44214490F60E35EDD55F763219 »

2. Extrayez le contenu de XMDEClientAnalyzer.zip sur l’ordinateur.

3. Ouvrez une session de terminal, remplacez le répertoire par l’emplacement extrait et exécutez :

   `./mde_support_tool.sh -d`

   > [!NOTE]
   > Sur Linux, si le script ne dispose pas des autorisations d’exécution, vous devez d’abord exécuter :
   >
   > `chmod a+x mde_support_tool.sh`

## <a name="running-the-analyzer-using-a-terminal-or-ssh-scenario"></a>Exécution de l’analyseur à l’aide d’un terminal ou d’un scénario SSH

Ouvrez un terminal ou un SSH sur l’ordinateur approprié et exécutez les commandes suivantes :

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`

2. `unzip -q XMDEClientAnalyzer.zip`

3. `cd XMDEClientAnalyzer`

4. `chmod +x mde_support_tool.sh`

3. Exécutez l’utilisation non racine pour installer les composants pip et lxml requis : `./mde_support_tool.sh`

4. Pour collecter le package de diagnostic réel et générer le fichier d’archivage des résultats, exécutez à nouveau en tant que racine : `./mde_support_tool.sh -d`

> [!NOTE]
> - Pour Linux, l’analyseur requiert « lxml » pour produire la sortie du résultat. S’il n’est pas installé, l’analyseur tente de l’extraire du référentiel officiel pour les packages Python ci-dessous : <https://pypi.org/search/?q=lxml>
> 
> - En outre, l’outil nécessite actuellement l’installation de Python version 3 ou ultérieure.
>
> - Si vous exécutez sur un ordinateur qui ne peut pas utiliser Python 3 ou extraire le composant lxml, vous pouvez télécharger une version binaire de l’analyseur qui n’a pas les exigences suivantes : [binaire de l’analyseur client XMDE](https://aka.ms/XMDEClientAnalyzerBinary). <br> Notez que le binaire n’est actuellement pas signé. Pour autoriser l’exécution du package sur MacOS, vous devez utiliser la syntaxe « spctl --add /Path/To/Application.app ».
> - Le hachage SHA256 actuel de « XMDEClientAnalyzerBinary.zip » téléchargé à partir du lien ci-dessus est : « 44099C0AA544B6A2E8676D5BB64BA79494E615E17329CE5ACC26C9F48E7F226B »
>
> - Si votre appareil se trouve derrière un proxy, vous pouvez simplement passer le serveur proxy en tant que variable d’environnement au script mde_support_tool.sh. Par exemple : `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

Exemple :

:::image type="content" source="images/4ca188f6c457e335abe3c9ad3eddda26.png" alt-text="Exemple de ligne de commande" lightbox="images/4ca188f6c457e335abe3c9ad3eddda26.png":::

Aide sur la syntaxe supplémentaire :

**-h** \# Aide<br>
\# Afficher le message d’aide

**Performance** \# Performance<br>
\# Collecte un suivi complet pour l’analyse d’un problème de performances qui peut être reproduit à la demande. Permet `--length=<seconds>` de spécifier la durée du benchmark.

**-O** \# Sortie<br>
\# Spécifier le chemin d’accès de destination pour le fichier de résultats

**-Nz** \# No-Zip<br>
\# S’il est défini, un répertoire est créé au lieu d’un fichier d’archive résultant

**-F** \# Force<br>
\# Remplacer si la sortie existe déjà dans le chemin de destination

## <a name="result-package-contents-on-macos-and-linux"></a>Contenu du package de résultats sur macOS et Linux

- report.html

  Description : fichier de sortie HTML principal qui contiendra les résultats et les conseils que le script d’analyseur exécuté sur la machine peut produire.

- mde_diagnostic.zip

  Description : Même sortie de diagnostic générée lors de l’exécution de *la création de diagnostic mdatp* sur [macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-resources#collecting-diagnostic-information)

  or

  [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  Description : sortie XML générée lors de l’exécution et utilisée pour générer le fichier de rapport html.

- Processes_information.txt

  Description : contient les détails des processus Microsoft Defender pour point de terminaison en cours d’exécution sur le système.

- Log.txt

  Description : contient les mêmes messages de journal écrits à l’écran pendant la collecte de données.

- Health.txt

  Description : sortie d’intégrité de base qui s’affiche lors de l’exécution de la commande *d’intégrité mdatp* .

- Events.xml

  Description : Fichier XML supplémentaire utilisé par l’analyseur lors de la génération du rapport HTML.

- Audited_info.txt

  Description : détails sur le service audité et les composants associés pour le système d’exploitation [Linux](/microsoft-365/security/defender-endpoint/linux-resources)

- perf_benchmark.tar.gz

  Description : Rapports de test de performances. Vous ne le verrez que si vous utilisez le paramètre de performances.
