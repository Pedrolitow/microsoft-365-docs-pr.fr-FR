---
title: Exécutez un test de détection sur un appareil pour vérifier qu’il a été correctement intégré à Microsoft Defender pour point de terminaison
description: Exécutez le script de test de détection sur un appareil récemment intégré au service Microsoft Defender pour point de terminaison pour vérifier qu’il est correctement ajouté.
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 49be12c14f04cc441165aff500479760cdc24c02
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67586399"
---
# <a name="run-a-detection-test-on-a-newly-onboarded-microsoft-defender-for-endpoint-device"></a>Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- Windows 11
- Versions Windows 10 prises en charge
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server, version 1803
- Windows Server 2019
- Windows Server 2022
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Lorsque vous ajoutez un appareil au service Microsoft Defender pour point de terminaison pour la gestion, il s’agit également d’appareils d’intégration. L’intégration permet aux appareils de signaler au service des signaux sur leur état d’intégrité.

La vérification ou la vérification de l’ajout d’un appareil au service est une étape critique dans l’ensemble du processus de déploiement. Il garantit que tous les appareils attendus sont gérés. 

## <a name="verify-microsoft-defender-for-endpoint-onboarding-of-a-device-using-a-powershell-detection-test"></a>Vérifier Microsoft Defender pour point de terminaison l’intégration d’un appareil à l’aide d’un test de détection PowerShell

Exécutez le script PowerShell suivant sur un appareil nouvellement intégré pour vérifier qu’il signale correctement au service Defender pour point de terminaison.

1. Créez un dossier : « C:\test-MDATP-test ».
2. Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil et exécutez le script :

   1. Accéder à **Démarrer** et taper **cmd**.

   1. Cliquez avec le bouton droit sur **l’invite de commandes** , puis **sélectionnez Exécuter en tant qu’administrateur**.

      :::image type="content" source="images/run-as-admin.png" alt-text="Menu Démarrer pointant vers Exécuter en tant qu’administrateur" lightbox="images/run-as-admin.png":::
    
3. À l’invite, copiez et exécutez la commande suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

La fenêtre d’invite de commandes se ferme automatiquement. Si elle réussit, une nouvelle alerte s’affiche dans le portail pour l’appareil intégré dans environ dix minutes.

## <a name="related-topics"></a>Voir aussi

- [Intégrer des appareils Windows 10](configure-endpoints.md)
- [Intégrer des serveurs](configure-server-endpoints.md)
- [Résoudre les problèmes d’intégration Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)
