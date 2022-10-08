---
title: Collecter les journaux de support dans Microsoft Defender pour point de terminaison à l’aide d’une réponse dynamique
description: Découvrez comment collecter des journaux à l’aide de la réponse en direct pour résoudre les problèmes de Microsoft Defender pour point de terminaison
keywords: support, journaliser, collecter, résoudre les problèmes, réponse en direct, liveanalyzer, analyseur, live, réponse
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
- m365-security
- tier3
ms.topic: troubleshooting
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: b5cb21c7f3fa75e49d696d6a3b3323ed287e41c3
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68224093"
---
# <a name="collect-support-logs-in-microsoft-defender-for-endpoint-using-live-response"></a>Collecter les journaux de support dans Microsoft Defender pour point de terminaison à l’aide d’une réponse dynamique


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)


Lorsque vous contactez le support technique, vous pouvez être invité à fournir le package de sortie de l’outil Microsoft Defender pour point de terminaison Analyseur client.

Cette rubrique fournit des instructions sur l’exécution de l’outil via Live Response.

1. Téléchargez et récupérez les scripts requis disponibles dans le sous-répertoire « Outils » de [l’analyseur client Microsoft Defender pour point de terminaison](https://aka.ms/BetaMDEAnalyzer). <br>
Par exemple, pour obtenir les journaux d’intégrité du capteur et de l’appareil de base, récupérez « .. \Tools\MDELiveAnalyzer.ps1 ».<br>
Si vous avez également besoin des journaux de support antivirus Defender (MpSupportFiles.cab), récupérez « .. \Tools\MDELiveAnalyzerAV.ps1 » 

2. Lancez une [session de réponse en direct](live-response.md#initiate-a-live-response-session-on-a-device) sur l’ordinateur que vous devez examiner.

3. Sélectionnez **Charger le fichier dans la bibliothèque**.

   :::image type="content" source="images/upload-file.png" alt-text="Fichier de chargement" lightbox="images/upload-file.png":::

4. **Sélectionnez Choisir un fichier**.

   :::image type="content" source="images/choose-file.png" alt-text="Bouton Choisir un fichier-1" lightbox="images/choose-file.png":::

5. Sélectionnez le fichier téléchargé nommé MDELiveAnalyzer.ps1, puis cliquez sur **Confirmer**

   :::image type="content" source="images/analyzer-file.png" alt-text="Bouton Choisir un fichier-2" lightbox="images/analyzer-file.png":::

6. Toujours dans la session LiveResponse, utilisez les commandes ci-dessous pour exécuter l’analyseur et collecter le fichier de résultats :

    ```console
    Run MDELiveAnalyzer.ps1
    GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
    ```

    [![Image des commandes.](images/analyzer-commands.png)](images/analyzer-commands.png#lightbox)

> [!NOTE]
>
> - La dernière préversion de MDEClientAnalyzer peut être téléchargée ici : [https://aka.ms/Betamdeanalyzer](https://aka.ms/Betamdeanalyzer).
>
> - Le script LiveAnalyzer télécharge le package de dépannage sur l’ordinateur de destination à partir de : https://mdatpclientanalyzer.blob.core.windows.net.
>
>   Si vous ne pouvez pas autoriser l’ordinateur à atteindre l’URL ci-dessus, chargez MDEClientAnalyzerPreview.zip fichier dans la bibliothèque avant d’exécuter le script LiveAnalyzer :
>
>   ```console
>   PutFile MDEClientAnalyzerPreview.zip -overwrite
>   Run MDELiveAnalyzer.ps1
>   GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
>   ```
>
> - Pour plus d’informations sur la collecte de données localement sur un ordinateur si l’ordinateur ne communique pas avec Microsoft Defender pour point de terminaison services cloud ou s’il n’apparaît pas dans Microsoft Defender pour point de terminaison portail comme prévu, consultez [Vérifier la connectivité du client à MICROSOFT DEFENDER POUR POINT DE TERMINAISON URL de service](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls).
> 
> - Comme décrit dans [les exemples de commandes de réponse en direct](live-response-command-examples.md), vous pouvez utiliser le symbole « & » à la fin de la commande pour collecter les journaux en tant qu’action en arrière-plan :
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
