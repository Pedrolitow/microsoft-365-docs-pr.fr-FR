---
title: Exécuter l’analyseur client sur macOS ou Linux
description: Découvrez comment exécuter l’analyseur de client Microsoft Defender pour Endpoint sur macOS ou Linux
keywords: analyseur client, dépannage du capteur, analyseur, mdeanalyzer, macos, linux, mdeanalyzer
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 813dff46f3ba26c32f3b704645a9ca35ca740001
ms.sourcegitcommit: f88a0ec621e7d9bc5f376eeaf70c8a9800711f88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59353597"
---
# <a name="run-the-client-analyzer-on-macos-and-linux"></a>Exécuter l’analyse du client sur macOS ou Linux

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)

## <a name="running-the-analyzer-through-gui-scenario"></a>Exécution de l’analyseur via le scénario d’interface graphique graphique

1. Téléchargez [l’outil Analyseur de client XMDE](https://aka.ms/XMDEClientAnalyzer) sur l’ordinateur macOS ou Linux que vous devez examiner.

   > [!NOTE]
   > Le hachage SHA256 actuel de « XMDEClientAnalyzer.zip » téléchargé à partir du lien ci-dessus est : '973725417D136B7B17AF4B301F1E99BA21D7F4A7DF88036DC5A731A4B768A8B2'.

2. Extrayez le contenu des XMDEClientAnalyzer.zip sur l’ordinateur.

3. Ouvrez une session terminal, modifiez le répertoire vers l’emplacement extrait et exécutez :

   `./mde_support_tool.sh -d`

   > [!NOTE]
   > Sur Linux, si le script ne peut pas s’exécuter, vous devez d’abord exécuter :
   >
   > `chmod a+x mde_support_tool.sh`

## <a name="running-the-analyzer-using-a-terminal-or-ssh-scenario"></a>Exécution de l’analyseur à l’aide d’un scénario terminal ou SSH

1. Ouvrez un terminal ou un SSH sur l’ordinateur approprié.

2. Exécuter `wget --quiet -O XMDEClientAnalyzer.zip* <https://aka.ms/XMDEClientAnalyzer> *&& unzip -q XMDEClientAnalyzer.zip && cd XMDEClientAnalyzer && chmod +x mde_support_tool.sh"`

3. Exécutez `./mde_support_tool.sh -d` cette ligne pour générer le fichier d’archivage des résultats.

> [!NOTE]
> Pour Linux, l’analyseur requiert « lxml » pour produire la sortie des résultats. S’il n’est pas installé, l’analyseur essaiera de l’extraire du référentiel officiel pour les packages Python ci-dessous : <https://files.pythonhosted.org/packages/\*/lxml\*.whl>
>
> En outre, l’outil nécessite actuellement l’installation de Python version 3 ou ultérieure.

Exemple :

![Image de l’exemple de ligne de commande.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

Aide supplémentaire sur la syntaxe :

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

## <a name="result-package-contents-on-macos-and-linux"></a>Contenu du package de résultats sur macOS et Linux

- report.html

  Description : fichier de sortie HTML principal qui contiendra les résultats et les instructions que le script de l’analyseur peut exécuter sur l’ordinateur.

- mde_diagnostic.zip

  Description : même sortie de diagnostic qui est générée lors de l’exécution du *diagnostic mdatp créer* sur [macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-resources#collecting-diagnostic-information)

  ou

  [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

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
