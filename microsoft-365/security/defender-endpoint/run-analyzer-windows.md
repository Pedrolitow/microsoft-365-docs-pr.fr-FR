---
title: Exécuter l’analyse du client sur Windows
description: Découvrez comment exécuter l’analyseur de client Microsoft Defender for Endpoint sur Windows.
keywords: analyseur client, dépannage du capteur, analyseur, mdeanalyzer, windows
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
ms.openlocfilehash: 5fa284f5c57214f356bb6b90e12ca60ae019d277
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467134"
---
# <a name="run-the-client-analyzer-on-windows"></a>Exécuter l’analyse du client sur Windows

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

1. Téléchargez [l’outil MDE Client Analyzer](https://aka.ms/mdatpanalyzer) sur l’ordinateur Windows que vous devez examiner.

2. Extrayez le contenu MDEClientAnalyzer.zip sur l’ordinateur.

3. Ouvrez une invite de commandes avec élévation de privilèges :
    1. Accéder à **Démarrer** et taper **cmd**.
    2. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

4. Entrez la commande suivante et appuyez sur **Entrée** :

   ```dos
   HardDrivePath\MDEClientAnalyzer.cmd
   ```

   **Remplacez HardDrivePath par le chemin d’accès vers lequel l’outil a été extrait, par exemple :**

   ```dos
   C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
   ```

Outre les informations ci-dessus, il existe également une option pour collecter les journaux de prise en charge de l’analyseur [à l’aide de la réponse en direct](troubleshoot-collect-support-log.md).

> [!NOTE]
> Sur Windows 10/11, Windows Server 2019/2022 ou Windows Server 2012R2/2016 avec la [solution](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview) unifiée moderne installée, le script de l’analyseur client appelle un fichier exécutable `MDEClientAnalyzer.exe` appelé pour exécuter les tests de connectivité aux URL de service cloud.
>
> Sur Windows 8.1, Windows Server 2016 ou toute édition précédente du système d’exploitation dans laquelle Microsoft Monitoring Agent (MMA) est utilisé pour l’intégration, le script de l’analyseur client appelle un fichier exécutable `MDEClientAnalyzerPreviousVersion.exe` appelé pour exécuter des tests de connectivité pour les URL de commande et de contrôle (CnC) tout en appelant Microsoft Monitoring Agent’outil de connectivité pour `TestCloudConnection.exe` les URL de canal de données cyber.


Tous les scripts et modules PowerShell inclus dans l’analyseur sont signés par Microsoft.
Si des fichiers ont été modifiés d’une manière ou d’une autre, l’analyseur est censé se quitter avec l’erreur suivante :

:::image type="content" source="images/sigerror.png" alt-text="Erreur de l’analyseur client" lightbox="images/sigerror.png":::


Si cette erreur s’affiche, la sortie issuerInfo.txt contient des informations détaillées sur la raison de cette erreur et sur le fichier concerné :

:::image type="content" source="images/issuerinfo.png" alt-text="Informations sur l’émetteur" lightbox="images/issuerinfo.png":::


Exemple de contenu après MDEClientAnalyzer.ps1 modification :

:::image type="content" source="images/modified-ps1.png" alt-text="Fichier ps1 modifié" lightbox="images/modified-ps1.png":::



## <a name="result-package-contents-on-windows"></a>Contenu du package de résultats sur Windows

> [!NOTE]
> Les fichiers exacts capturés peuvent changer en fonction de facteurs tels que :
>
> - Version des fenêtres sur lesquelles l’analyseur est exécuté.
> - Disponibilité du canal du journal des événements sur l’ordinateur.
> - État de démarrage du capteur PEPT (l’Sense est arrêté si l’ordinateur n’est pas encore intégré).
> - Si un paramètre de dépannage avancé a été utilisé avec la commande de l’analyseur.

Par défaut, le fichier MDEClientAnalyzerResult.zip décompressé contient les éléments suivants.

- MDEClientAnalyzer.htm

  Il s’agit du fichier de sortie HTML principal, qui contient les résultats et les instructions que le script de l’analyseur peut produire sur l’ordinateur.

- Dossier SystemInfoLogs \[\]
  - AddRemovePrograms.csv

    Description : Liste des logiciels x86 installés sur les logiciels de système d’exploitation x64 collectés à partir du Registre.

  - AddRemoveProgramsWOW64.csv

    Description : Liste des logiciels x86 installés sur les logiciels de système d’exploitation x64 collectés à partir du Registre.

    - CertValidate.log

      Description : résultat détaillé de la révocation de certificats exécutée en appelant [CertUtil](/windows-server/administration/windows-commands/certutil).

    - dsregcmd.txt

      Description : sortie de l’exécution [de dsregcmd](/azure/active-directory/devices/troubleshoot-device-dsregcmd). Cela fournit des détails sur l Azure AD de l’ordinateur.

    - IFEO.txt

      Description : sortie des [options d’exécution de fichier image](/previous-versions/windows/desktop/xperf/image-file-execution-options) configurées sur l’ordinateur

    - MDEClientAnalyzer.txt

      Description : ce fichier texte détaillé s’affiche avec des détails sur l’exécution du script de l’analyseur.

    - MDEClientAnalyzer.xml

      Description : format XML contenant les résultats du script de l’analyseur.

    - RegOnboardedInfoCurrent.Json

      Description : informations de l’ordinateur intégré rassemblées au format JSON à partir du Registre.

  - RegOnboardingInfoPolicy.Json

    Description : configuration de la stratégie d’intégration rassemblée au format JSON à partir du Registre.

    - SCHANNEL.txt

      Description : détails sur la [configuration SCHANNEL](/windows-server/security/tls/manage-tls) appliquée à l’ordinateur tels que collectés à partir du Registre.

    - SessionManager.txt

      Description : les paramètres spécifiques du Gestionnaire de session sont collecté à partir du Registre.

    - SSL_00010002.txt

      Description : détails sur la [configuration SSL](/windows-server/security/tls/manage-tls) appliquée à l’ordinateur collecté à partir du Registre.

- EventLogs [Dossier]

  - utc.evtx

    Description : Exportation du journal des événements DiagTrack

  - senseIR.evtx

    Description : exportation du journal des événements d’investigation automatisée

  - sense.evtx

    Description : Exportation du journal des événements principaux du capteur

  - OperationsManager.evtx

    Description : exportation du journal des Microsoft Monitoring Agent’événements




## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’analyseur client](overview-client-analyzer.md)
- [Télécharger et exécuter l’analyseur client](download-client-analyzer.md)
- [Collecte de données pour la résolution avancée des problèmes sur Windows](data-collection-analyzer.md)
- [Comprendre le de rapport HTML de l’analyseur](analyzer-report.md)
