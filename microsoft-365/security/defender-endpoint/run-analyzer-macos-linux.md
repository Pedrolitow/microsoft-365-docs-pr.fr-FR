---
title: Exécuter l’analyseur client sur macOS ou Linux
description: Découvrez comment exécuter l’analyseur de client Microsoft Defender pour Endpoint sur macOS ou Linux
keywords: analyseur client, dépannage du capteur, analyseur, mdeanalyzer, macos, linux, mdeanalyzer
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
ms.openlocfilehash: 087e7ff666ddcad02b5ead5ab62b483e60541a90
ms.sourcegitcommit: 6e43aeff217afe97876137b1ead8df26db6e9937
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/16/2022
ms.locfileid: "62859276"
---
# <a name="run-the-client-analyzer-on-macos-and-linux"></a>Exécuter l’analyse du client sur macOS ou Linux


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="running-the-analyzer-through-gui-scenario"></a>Exécution de l’analyseur via un scénario d’interface graphique graphique

1. Téléchargez [l’outil Analyseur client XMDE](https://aka.ms/XMDEClientAnalyzer) sur l’ordinateur macOS ou Linux que vous devez examiner.

   > [!NOTE]
   > Le hachage SHA256 actuel de « XMDEClientAnalyzer.zip » qui est téléchargé à partir du lien ci-dessus est : 'AA6E73A5F451C3B78B066C9D55EE6499CE3C2F1A6E05CCE691A6055F36F93A3B'.

2. Extrayez le contenu du XMDEClientAnalyzer.zip sur l’ordinateur.

3. Ouvrez une session terminal, modifiez le répertoire vers l’emplacement extrait et exécutez :

   `./mde_support_tool.sh -d`

   > [!NOTE]
   > Sur Linux, si le script n’est pas autorisé à s’exécuter, vous devez d’abord exécuter :
   >
   > `chmod a+x mde_support_tool.sh`

## <a name="running-the-analyzer-using-a-terminal-or-ssh-scenario"></a>Exécution de l’analyseur à l’aide d’un scénario terminal ou SSH

Ouvrez un terminal ou un SSH sur l’ordinateur approprié et exécutez les commandes suivantes :

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`

2. `unzip -q XMDEClientAnalyzer.zip`

3. `cd XMDEClientAnalyzer`

4. `chmod +x mde_support_tool.sh`

3. Exécutez en tant qu’utilisation non racine pour installer les composants pip et lxml requis : `./mde_support_tool.sh`

4. Pour collecter le package de diagnostic réel et générer le fichier d’archivage des résultats, exécutez à nouveau en tant que racine : `./mde_support_tool.sh -d`

> [!NOTE]
> - Pour Linux, l’analyseur requiert « lxml » pour produire la sortie des résultats. S’il n’est pas installé, l’analyseur essaie de l’extraire du référentiel officiel pour les packages Python ci-dessous : <https://files.pythonhosted.org/packages/\*/lxml\*.whl>
> 
> - En outre, l’outil nécessite actuellement l’installation de Python version 3 ou ultérieure.
>
> - Si vous exécutez sur un ordinateur qui ne peut pas utiliser Python 3 ou extraire le composant lxml, vous pouvez télécharger une version binaire de l’analyseur qui n’a aucune des conditions requises : [XMDE Client Analyzer Binary](https://aka.ms/XMDEClientAnalyzerBinary)
>
> - Si votre appareil se trouve derrière un proxy, vous pouvez simplement transmettre le serveur proxy en tant que variable d’environnement au script mde_support_tool.sh. Par exemple : `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

Exemple :

![Image de l’exemple de ligne de commande.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

Aide supplémentaire sur la syntaxe :

**-h** \# Aide<br>
\# Afficher le message d’aide

**performance** \# Performances<br>
\# Collecte un suivi complet pour l’analyse d’un problème de performances qui peut être reproduit à la demande. Utilisation pour `--length=<seconds>` spécifier la durée du critère.

**-o** \# Sortie<br>
\# Spécifier le chemin d’accès de destination pour le fichier de résultats

**-nz** \# No-Zip<br>
\# S’il est définie, un répertoire est créé au lieu d’un fichier d’archivage résultant

**-f** \# Force<br>
\# Overwrite si la sortie existe déjà dans le chemin de destination

## <a name="result-package-contents-on-macos-and-linux"></a>Contenu du package de résultats sur macOS et Linux

- report.html

  Description : fichier de sortie HTML principal qui contiendra les résultats et les instructions que le script de l’analyseur peut produire sur l’ordinateur.

- mde_diagnostic.zip

  Description : même sortie de diagnostic qui est générée lors de l’exécution de *diagnostic mdatp créer* sur [macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-resources#collecting-diagnostic-information)

  ou

  [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  Description : sortie XML générée lors de l’exécution et utilisée pour générer le fichier de rapport html.

- Processes_information.txt

  Description : contient les détails des processus microsoft Defender pour point de terminaison en cours d’exécution sur le système.

- Log.txt

  Description : contient les mêmes messages de journal écrits à l’écran pendant la collecte de données.

- Health.txt

  Description : sortie d’état d’état de base affichée lors de l’exécution de la *commande d’état d’état mdatp* .

- Events.xml

  Description : fichier XML supplémentaire utilisé par l’analyseur lors de la génération du rapport HTML.

- Auditd_info.txt

  Description : détails sur le service audité et les composants associés pour le système [d’exploitation Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-support-events)

- perf_benchmark.tar.gz

  Description : rapports de test de performances. Vous ne le verrez que si vous utilisez le paramètre performance.
