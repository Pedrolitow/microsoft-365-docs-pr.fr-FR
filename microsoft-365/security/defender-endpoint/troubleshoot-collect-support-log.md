---
title: Collecter les journaux de support dans Microsoft Defender pour le point de terminaison à l’aide d’une réponse en direct
description: Découvrez comment collecter des journaux à l’aide d’une réponse en direct pour résoudre les problèmes de Microsoft Defender pour les points de terminaison
keywords: support, journal, collecter, dépanner, réponse en direct, liveanalyzer, analyseur, en direct, réponse
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: a0d0f470a2af18dab298ba3a1af642362590da4c
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63401159"
---
# <a name="collect-support-logs-in-microsoft-defender-for-endpoint-using-live-response"></a>Collecter les journaux de support dans Microsoft Defender pour le point de terminaison à l’aide d’une réponse en direct


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)


Lorsque vous contactez le support technique, vous pouvez être invité à fournir le package de sortie de l’outil Microsoft Defender for Endpoint Client Analyzer.

Cette rubrique fournit des instructions sur la façon d’exécuter l’outil via Live Response.

1. Téléchargez et récupèrez les scripts requis disponibles dans le sous-répertoire « Outils » de l’analyseur de [client Microsoft Defender for Endpoint](https://aka.ms/BetaMDEAnalyzer). <br>
Par exemple, pour obtenir le capteur de base et les journaux d’état de l’appareil, récupérer « . \Tools\MDELiveAnalyzer.ps1 »<br>
Si vous avez également besoin des journaux de prise en charge de l’Antivirus Defender (MpSupportFiles.cab), puis récupérer « . \Tools\MDELiveAnalyzerAV.ps1 » 

2. Lancez [une session Live Response](live-response.md#initiate-a-live-response-session-on-a-device) sur l’ordinateur que vous devez examiner.

3. Sélectionnez **Télécharger fichier vers la bibliothèque**.

    ![Image du fichier de téléchargement.](images/upload-file.png)

4. **Sélectionnez Choisir un fichier**.

    ![Image du bouton de choix du fichier 1.](images/choose-file.png)

5. Sélectionnez le fichier téléchargé nommé MDELiveAnalyzer.ps1 puis cliquez sur **Confirmer**

   ![Image du bouton de choix du fichier 2.](images/analyzer-file.png)

6. Pendant la session LiveResponse, utilisez les commandes ci-dessous pour exécuter l’analyseur et collecter le fichier de résultats :

    ```console
    Run MDELiveAnalyzer.ps1
    GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
    ```

    [![Image des commandes.](images/analyzer-commands.png)](images/analyzer-commands.png#lightbox)

> [!NOTE]
>
> - La dernière version d’aperçu de MDEClientAnalyzer peut être téléchargée ici : [https://aka.ms/Betamdeanalyzer](https://aka.ms/Betamdeanalyzer)
>
> - Le script LiveAnalyzer télécharge le package de dépannage sur l’ordinateur de destination à partir de : https://mdatpclientanalyzer.blob.core.windows.net
>
>   Si vous ne pouvez pas autoriser l’ordinateur à atteindre l’URL ci-dessus, téléchargez MDEClientAnalyzerPreview.zip fichier dans la bibliothèque avant d’exécutez le script LiveAnalyzer :
>
>   ```console
>   PutFile MDEClientAnalyzerPreview.zip -overwrite
>   Run MDELiveAnalyzer.ps1
>   GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
>   ```
>
> - Pour plus d’informations sur la collecte de données localement sur un ordinateur au cas où l’ordinateur ne communique pas avec Microsoft Defender pour les services cloud de point de terminaison ou n’apparaît pas comme prévu dans le portail Microsoft Defender pour points de terminaison, voir Vérifier la connectivité [client à Microsoft Defender](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls) pour les URL de service De point de terminaison.
> 
> - Comme décrit dans les exemples de commandes de réponse [Live](live-response-command-examples.md), vous pouvez utiliser le symbole « & » à la fin de la commande pour collecter les journaux en tant qu’action en arrière-plan :
>   ```console
>   Run MDELiveAnalyzer.ps1&
>   ```


## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble de l’analyseur client](overview-client-analyzer.md)
- [Télécharger et exécuter l’analyseur client](download-client-analyzer.md)
- [Exécuter l’analyseur client sur Windows](run-analyzer-windows.md)
- [Exécuter l’analyseur client sur macOS ou Linux](run-analyzer-macos-linux.md)
- [Collecte de données pour la résolution avancée des problèmes sur Windows](data-collection-analyzer.md)
- [Comprendre le de rapport HTML de l’analyseur](analyzer-report.md)
