---
title: Exécutez l’analyseur client sur Windows
description: Découvrez comment exécuter Microsoft Defender for Endpoint Client Analyzer sur Windows.
keywords: analyseur client, capteur de dépannage, analyseur, mdeanalyzer, windows
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
ms.openlocfilehash: 754ec7b6cdd6e6c5e3c9f5765d839bd94a1d720b
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58254899"
---
#  <a name="run-the-client-analyzer-on-windows"></a>Exécutez l’analyseur client sur Windows

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)


1.  Téléchargez [l’outil MDE Client Analyzer](https://aka.ms/mdatpanalyzer) sur l Windows que vous devez examiner.

2.  Extrayez le contenu du MDEClientAnalyzer.zip sur l’ordinateur.

3.  Ouvrez une invite de commandes avec élévation de privilèges :
    1. Accéder à **Démarrer** et taper **cmd**.
    2. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

4.  Entrez la commande suivante et appuyez sur **Entrée** :

```
HardDrivePath\MDEClientAnalyzer.cmd
```

**Remplacez HardDrivePath par le chemin d’accès vers lequel l’outil a été extrait, par exemple :**

`C:\Work\tools\MDATPClientAnalyzer\MDEClientAnalyzer.cmd`

En plus des informations ci-dessus, il existe également une option pour collecter les journaux de prise en charge de l’analyseur [à l’aide de la réponse en direct.](troubleshoot-collect-support-log.md)

> [!NOTE]  
> Sur windows 10, Windows Server 2019 ou les éditions ultérieures du système d’exploitation, le script de l’analyseur client appelle un fichier exécutable appelé pour exécuter les tests de connectivité vers les URL de `MDEClientAnalyzer.exe` service cloud. <br> <br> Sur Windows 8.1, Windows Server 2016 ou des éditions antérieures du système d’exploitation, le script de l’analyseur client appelle un fichier exécutable appelé pour exécuter des tests de connectivité pour les URL de commande et de contrôle (CnC) tout en appelant l’outil de connectivité Microsoft Monitoring Agent pour les URL de canal de `MDEClientAnalyzerPreviousVersion.exe` `TestCloudConnection.exe` cyber-données.

## <a name="result-package-contents-on-windows"></a>Contenu du package de résultats sur Windows

> [!NOTE]    
> Les fichiers exacts capturés peuvent changer en fonction de facteurs tels que :
> -   Version des fenêtres sur lesquelles l’analyseur est exécuté.
> -   Disponibilité du canal du journal des événements sur l’ordinateur.
> -   État de démarrage du capteur PEPT (l’Sense est arrêté si l’ordinateur n’est pas encore intégré).
>-   Si un paramètre de dépannage avancé a été utilisé avec la commande de l’analyseur.

Par défaut, le fichier MDEClientAnalyzerResult.zip décompressé contient les éléments suivants.

-   MDEClientAnalyzer.htm il s’agit du fichier de sortie HTML principal, qui contient les résultats et les instructions que le script d’analyseur peut produire sur \| l’ordinateur.

-   SystemInfoLogs [Dossier]

    -   AddRemovePrograms.csv <br> Description : Liste des logiciels installés collectés à partir du Registre.

-   AddRemoveProgramsWOW64.csv <br> Description : Liste des logiciels x86 installés sur les logiciels de système d’exploitation x64 collectés à partir du Registre.

    -   CertValidate.log <br> Description : résultat détaillé de la révocation de certificats exécutée en appelant [CertUtil](/windows-server/administration/windows-commands/certutil).

    -   dsregcmd.txt <br> Description : Sortie de l’exécution [dsregcmd](/azure/active-directory/devices/troubleshoot-device-dsregcmd).
        Cela fournit des détails sur l’état Azure AD de l’ordinateur.

    -   IFEO.txt <br> Description : sortie des [options d’exécution de fichier image](/previous-versions/windows/desktop/xperf/image-file-execution-options) configurées sur l’ordinateur

    -   MDEClientAnalyzer.txt <br> Description : il s’agit d’un fichier texte détaillé avec des détails sur l’exécution du script de l’analyseur.

    -   MDEClientAnalyzer.xml <br> Description : format XML contenant les résultats du script de l’analyseur.

    -   RegOnboardedInfoCurrent.Jssur <br> Description : informations de l’ordinateur intégré rassemblées au format JSON à partir du Registre.

    -   RegOnboardingInfoPolicy.Jssur <br> Description : configuration de la stratégie d’intégration rassemblée au format JSON à partir du Registre.

    -   SCHANNEL.txt <br> Description : détails sur la [configuration SCHANNEL](/windows-server/security/tls/manage-tls) appliquée à l’ordinateur tels que collectés à partir du Registre.

    -   SessionManager.txt <br> Description : les paramètres spécifiques du Gestionnaire de session sont collecté à partir du Registre.

    -   SSL_00010002.txt <br> Description : détails sur la [configuration SSL](/windows-server/security/tls/manage-tls) appliquée à l’ordinateur collecté à partir du Registre.

-   EventLogs [Dossier]

    -   utc.evtx <br> Description : Exportation du journal des événements DiagTrack

    -   senseIR.evtx <br> Description : exportation du journal des événements d’investigation automatisée

    -   sense.evtx <br> Description : Exportation du journal des événements principaux du capteur

    -   OperationsManager.evtx <br> Description : Exportation du journal des événements Microsoft Monitoring Agent’événements


## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble de l’analyseur client](overview-client-analyzer.md)
- [Télécharger et exécuter l’analyseur client](download-client-analyzer.md)
- [Collecte de données pour la résolution avancée des problèmes sur Windows](data-collection-analyzer.md)
- [Comprendre le rapport HTML de l’analyseur](analyzer-report.md)
