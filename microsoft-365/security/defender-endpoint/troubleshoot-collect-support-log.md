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
ms.openlocfilehash: ae2a0b538fffc1644d3eb3e26c5b7cd4b512de1c
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61110702"
---
# <a name="collect-support-logs-in-microsoft-defender-for-endpoint-using-live-response"></a>Collecter les journaux de support dans Microsoft Defender pour le point de terminaison à l’aide d’une réponse en direct


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)


Lorsque vous contactez le support technique, vous pouvez être invité à fournir le package de sortie de l’outil Microsoft Defender for Endpoint Client Analyzer.

Cette rubrique fournit des instructions sur la façon d’exécuter l’outil via Live Response.

1. Télécharger le script approprié
   - Journaux de capteur client Microsoft Defender pour point de terminaison uniquement : [LiveAnalyzer.ps1 script](https://aka.ms/MDELiveAnalyzer).
      - Taille approximative du package de résultats : ~100Kb
   - Capteur client microsoft Defender pour point de terminaison et journaux antivirus : [LiveAnalyzer+MDAV.ps1 script](https://aka.ms/MDELiveAnalyzerAV).
       - Taille approximative du package de résultats : ~10 Mo

2. Lancez [une session Live Response](live-response.md#initiate-a-live-response-session-on-a-device) sur l’ordinateur que vous devez examiner.

3. Sélectionnez **Télécharger fichier vers la bibliothèque.**

    ![Image du fichier de téléchargement.](images/upload-file.png)

4. Sélectionnez **Choisir un fichier.**

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
> - La dernière version d’aperçu de MDEClientAnalyzer peut être téléchargée ici [https://aka.ms/Betamdeanalyzer](https://aka.ms/Betamdeanalyzer) :
>
> - Le script LiveAnalyzer télécharge le package de dépannage sur l’ordinateur de destination à partir https://mdatpclientanalyzer.blob.core.windows.net de :
>
>   Si vous ne pouvez pas autoriser l’ordinateur à atteindre l’URL ci-dessus, téléchargez MDEClientAnalyzerPreview.zip fichier dans la bibliothèque avant d’exécutez le script LiveAnalyzer :
>
>   ```console
>   PutFile MDEClientAnalyzerPreview.zip -overwrite
>   Run MDELiveAnalyzer.ps1
>   GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
>   ```
>
> - Pour plus d’informations sur la collecte de données localement sur un ordinateur au cas où l’ordinateur ne communique pas avec Microsoft Defender pour les services cloud de point de terminaison ou n’apparaît pas dans le portail Microsoft Defender pour endpoint comme prévu, voir Vérifier la connectivité client à Microsoft Defender pour les URL de service de point de [terminaison.](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)
> 
> - Comme décrit dans les exemples de commandes de réponse [Live,](live-response-command-examples.md)vous pouvez utiliser le symbole « & » à la fin de la commande pour collecter les journaux en tant qu’action en arrière-plan :
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
