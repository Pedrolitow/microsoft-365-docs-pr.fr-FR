---
title: Exécuter l’analyse du client sur Windows
description: Découvrez comment exécuter l’analyseur client Pertahanan Microsoft untuk Titik Akhir sur Windows.
keywords: analyseur client, capteur de dépannage, analyseur, mdeanalyzer, fenêtres
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
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: d348a1c48ac44a0e05768eea684efd3ad27dcb4f
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67741629"
---
# <a name="run-the-client-analyzer-on-windows"></a>Exécuter l’analyse du client sur Windows

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

1. Téléchargez [l’outil MDE Client Analyzer](https://aka.ms/mdatpanalyzer) sur l’ordinateur Windows que vous devez examiner.

2. Extrayez le contenu de MDEClientAnalyzer.zip sur l’ordinateur.

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

En plus de ce qui précède, il existe également une option permettant de [collecter les journaux de prise en charge de l’analyseur à l’aide de la réponse dynamique.](troubleshoot-collect-support-log.md)

> [!NOTE]
> Le Windows 10/11, Windows Server 2019/2022 ou Windows Server 2012R2/2016 avec la [solution unifiée moderne](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) installée, le script de l’analyseur client appelle un fichier exécutable appelé `MDEClientAnalyzer.exe` pour exécuter les tests de connectivité aux URL de service cloud.
>
> Sur Windows 8.1, Windows Server 2016 ou n’importe quelle édition précédente du système d’exploitation où Microsoft Monitoring Agent (MMA) est utilisé pour l’intégration, le script de l’analyseur client appelle un fichier exécutable appelé `MDEClientAnalyzerPreviousVersion.exe` pour exécuter des tests de connectivité pour les URL de commande et de contrôle (CnC) tout en appelant l’outil `TestCloudConnection.exe` de connectivité de Microsoft Monitoring Agent pour les URL de canal de cyberdondation.


Tous les scripts et modules PowerShell inclus dans l’analyseur sont signés par Microsoft.
Si des fichiers ont été modifiés d’une quelconque manière, l’analyseur est censé se fermer avec l’erreur suivante :

:::image type="content" source="images/sigerror.png" alt-text="Erreur de l’analyseur client" lightbox="images/sigerror.png":::


Si cette erreur s’affiche, la sortie issuerInfo.txt contient des informations détaillées sur la raison de cette erreur et sur le fichier affecté :

:::image type="content" source="images/issuerinfo.png" alt-text="Informations sur l’émetteur" lightbox="images/issuerinfo.png":::


Exemples de contenu après la modification de MDEClientAnalyzer.ps1 :

:::image type="content" source="images/modified-ps1.png" alt-text="Fichier ps1 modifié" lightbox="images/modified-ps1.png":::



## <a name="result-package-contents-on-windows"></a>Contenu du package de résultats sur Windows

> [!NOTE]
> Les fichiers exacts capturés peuvent changer en fonction de facteurs tels que :
>
> - Version des fenêtres sur lesquelles l’analyseur est exécuté.
> - Disponibilité du canal du journal des événements sur l’ordinateur.
> - État de démarrage du capteur EDR (Sense est arrêté si l’ordinateur n’est pas encore intégré).
> - Si un paramètre de dépannage avancé a été utilisé avec la commande de l’analyseur.

Par défaut, le fichier MDEClientAnalyzerResult.zip décompressé contient les éléments suivants.

- MDEClientAnalyzer.htm

  Il s’agit du fichier de sortie HTML principal, qui contiendra les résultats et les conseils que le script d’analyseur exécuté sur l’ordinateur peut produire.

- Dossier SystemInfoLogs \[\]
  - AddRemovePrograms.csv

    Description : Liste des logiciels x64 installés sur le système d’exploitation x64 collectés à partir du Registre.

  - AddRemoveProgramsWOW64.csv

    Description : Liste des logiciels x86 installés sur le système d’exploitation x64 collectés à partir du Registre.

    - CertValidate.log

      Description : Résultat détaillé de la révocation de certificat exécutée en appelant [CertUtil](/windows-server/administration/windows-commands/certutil).

    - dsregcmd.txt

      Description : Sortie de [l’exécution de dsregcmd](/azure/active-directory/devices/troubleshoot-device-dsregcmd). Cela fournit des détails sur l’état Azure AD de l’ordinateur.

    - IFEO.txt

      Description : Sortie des [options d’exécution de fichier image](/previous-versions/windows/desktop/xperf/image-file-execution-options) configurées sur l’ordinateur

    - MDEClientAnalyzer.txt

      Description : Il s’agit d’un fichier texte détaillé montrant les détails de l’exécution du script de l’analyseur.

    - MDEClientAnalyzer.xml

      Description : format XML contenant les résultats du script de l’analyseur.

    - RegOnboardedInfoCurrent.Json

      Description : Informations sur la machine intégrée collectées au format JSON à partir du Registre.

  - RegOnboardingInfoPolicy.Json

    Description : Configuration de la stratégie d’intégration collectée au format JSON à partir du Registre.

    - SCHANNEL.txt

      Description : Détails sur la [configuration SCHANNEL](/windows-server/security/tls/manage-tls) appliquée à l’ordinateur tel qu’il a été collecté à partir du Registre.

    - SessionManager.txt

      Description : Les paramètres spécifiques du Gestionnaire de session sont collectés à partir du Registre.

    - SSL_00010002.txt

      Description : Détails sur la [configuration SSL](/windows-server/security/tls/manage-tls) appliquée à l’ordinateur collecté à partir du Registre.

- EventLogs [Dossier]

  - utc.evtx

    Description : Exportation du journal des événements DiagTrack

  - senseIR.evtx

    Description : Exportation du journal des événements d’investigation automatisée

  - sense.evtx

    Description : Exportation du journal des événements principaux du capteur

  - OperationsManager.evtx

    Description : Exportation du journal des événements de Microsoft Monitoring Agent




## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’analyseur client](overview-client-analyzer.md)
- [Télécharger et exécuter l’analyseur client](download-client-analyzer.md)
- [Collecte de données pour la résolution avancée des problèmes sur Windows](data-collection-analyzer.md)
- [Comprendre le de rapport HTML de l’analyseur](analyzer-report.md)
