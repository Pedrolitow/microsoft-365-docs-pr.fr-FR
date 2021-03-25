---
title: Collecter les journaux de support dans Microsoft Defender pour les points de terminaison à l’aide d’une réponse en direct
description: Découvrez comment collecter des journaux à l’aide d’une réponse en direct pour résoudre les problèmes de Microsoft Defender pour les points de terminaison
keywords: support, journal, collecter, dépanner, réponse en direct, liveanalyzer, analyseur, en direct, réponse
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
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 50e7bc6d84714411c89f014bb0018a3102617cb7
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51066057"
---
# <a name="collect-support-logs-in-microsoft-defender-for-endpoint-using-live-response"></a>Collecter les journaux de support dans Microsoft Defender pour le point de terminaison à l’aide d’une réponse en direct 


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 


Lorsque vous contactez le support technique, vous pouvez être invité à fournir le package de sortie de l’outil Microsoft Defender for Endpoint Client Analyzer.

Cette rubrique fournit des instructions sur la façon d’exécuter l’outil via Live Response.

1. Télécharger le script approprié
    * Journaux de capteur client Microsoft Defender pour point de terminaison uniquement : [LiveAnalyzer.ps1 script](https://aka.ms/MDELiveAnalyzer).
      - Taille approximative du package de résultats : ~100Kb 
    *  Capteur client microsoft Defender pour point de terminaison et journaux antivirus : [LiveAnalyzer+MDAV.ps1 script](https://aka.ms/MDELiveAnalyzerAV).
       - Taille approximative du package de résultats : ~10 Mo 
 
2.  Lancez [une session Live Response](live-response.md#initiate-a-live-response-session-on-a-device) sur l’ordinateur que vous devez examiner.

3.  Sélectionnez **Télécharger le fichier dans la bibliothèque.**

    ![Image du fichier de téléchargement](images/upload-file.png)

4. Sélectionnez **Choisir un fichier.**

    ![Image du bouton Choisir un fichier1](images/choose-file.png)

5. Sélectionnez le fichier téléchargé nommé MDELiveAnalyzer.ps1 puis cliquez sur **Confirmer**


   ![Image de choisir le bouton2 du fichier](images/analyzer-file.png)


6. Pendant la session LiveResponse, utilisez les commandes ci-dessous pour exécuter l’analyseur et collecter le fichier de résultats :

    ```console
    Run MDELiveAnalyzer.ps1
    GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip" -auto
    ```

    ![Image des commandes](images/analyzer-commands.png)


>[!NOTE]
> - La dernière version d’aperçu de MDEClientAnalyzer peut être téléchargée ici [https://aka.ms/Betamdeanalyzer](https://aka.ms/Betamdeanalyzer) :
> 
> - Le script LiveAnalyzer télécharge le package de dépannage sur l’ordinateur de destination à partir https://mdatpclientanalyzer.blob.core.windows.net de :
> 
>   Si vous ne pouvez pas autoriser l’ordinateur à atteindre l’URL ci-dessus, téléchargez MDEClientAnalyzerPreview.zip fichier dans la bibliothèque avant d’exécutez le script LiveAnalyzer :
>
>   ```console
>   PutFile MDEClientAnalyzerPreview.zip -overwrite
>   Run MDELiveAnalyzer.ps1
>   GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip" -auto
>   ```
> 
> - Pour plus d’informations sur la collecte de données localement sur un ordinateur au cas où l’ordinateur ne communique pas avec Microsoft Defender pour les services cloud de point de terminaison ou n’apparaît pas dans le portail Microsoft Defender pour endpoint comme prévu, voir Vérifier la connectivité client à Microsoft Defender pour les URL de service de point de [terminaison.](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-atp-service-urls)
