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
ms.openlocfilehash: 6008e59abadc179f8e6580d56007ea88b9415ab5
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58254849"
---
#  <a name="run-the-client-analyzer-on-macos-and-linux"></a>Exécuter l’analyseur client sur macOS et Linux

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)


## <a name="running-the-analyzer-through-gui-scenario"></a>Exécution de l’analyseur via le scénario d’interface graphique graphique

1.  Téléchargez [l’outil Analyseur de client XMDE](https://aka.ms/XMDEClientAnalyzer) sur l’ordinateur macOS ou Linux que vous devez examiner.
> [!NOTE]  
> Le hachage SHA256 actuel de « XMDEClientAnalyzer.zip » téléchargé à partir du lien ci-dessus est : '029296D437BA97B5563D0C75DD874F8F51C563B2B5AC16745619F4DB2E064C85'.

2.  Extrayez le contenu du XMDEClientAnalyzer.zip sur l’ordinateur.

3.  Ouvrez une session terminal, modifiez le répertoire vers l’emplacement extrait et exécutez :

`./mde_support_tool.sh -d`

! Remarque  
Sur Linux, si le script ne peut pas s’exécuter, vous devez d’abord exécuter :  
*chmod a+x mde_support_tool.sh*

## <a name="running-the-analyzer-using-a-terminal-or-ssh-scenario"></a>Exécution de l’analyseur à l’aide d’un scénario terminal ou SSH

1.  Ouvrez un terminal ou un SSH sur l’ordinateur approprié.

2.  Exécuter `wget --quiet -O XMDEClientAnalyzer.zip*
    <http://aka.ms/XMDEClientAnalyzer> *&& unzip -q XMDEClientAnalyzer.zip && cd
    XMDEClientAnalyzer && chmod +x mde_support_tool.sh"`

3.  Exécutez ` ./mde_support_tool.sh -d ` cette ligne pour générer le fichier d’archivage des résultats.

> [!NOTE]  
> Pour Linux, l’analyseur requiert « lxml » pour produire la sortie des résultats. S’il n’est pas installé, l’analyseur essaiera de l’extraire du référentiel officiel pour les packages Python ci-dessous :  
https://files.pythonhosted.org/packages/\*/lxml \* .whl

Exemple :  


![Image de l’exemple de ligne de commande](images/4ca188f6c457e335abe3c9ad3eddda26.png)

  
  
Aide supplémentaire sur la syntaxe :

**-h** \# Aide  
\# Afficher le message d’aide

**-p** \# Performances  
\# Paramètre planifié qui n’est pas encore implémenté.  
\# Collecte un suivi complet pour l’analyse d’un problème de performances qui peut être reproduit à la demande.

**-o** \# Sortie  
\# Spécifier le chemin d’accès de destination pour le fichier de résultats

**-nz** \# No-Zip  
\# S’il est définie, un répertoire est créé au lieu d’un fichier d’archivage résultant

**-f** \# Force  
\# Overwrite si la sortie existe déjà dans le chemin de destination

## <a name="result-package-contents-on-macos-and-linux"></a>Contenu du package de résultats sur macOS et Linux

-   report.html <br> Description : fichier de sortie HTML principal qui contiendra les résultats et les instructions que le script de l’analyseur peut exécuter sur l’ordinateur.

-   mde_diagnostic.zip <br> Description : même sortie de diagnostic générée lors de l’exécution du *diagnostic mdatp créer* sur [macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-resources#collecting-diagnostic-information) ou [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

-   mde.xml <br> Description : sortie XML générée lors de l’exécution et utilisée pour générer le fichier de rapport html.

-   Processes_information.txt <br> Description : contient les détails des processus microsoft Defender pour point de terminaison en cours d’exécution sur le système.

-   Log.txt <br> Description : contient les mêmes messages de journal écrits à l’écran pendant la collecte de données.

-   Health.txt <br> Description : sortie d’état d’état de base affichée lors de l’exécution de la *commande d’état d’état mdatp.*

-   Events.xml <br> Description : fichier XML supplémentaire utilisé par l’analyseur lors de la génération du rapport HTML.

-   Auditd_info.txt <br> Description : détails sur le service audité et les composants associés pour le système [d’exploitation Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-support-events)
