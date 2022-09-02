---
title: Résoudre Microsoft Defender pour point de terminaison problèmes de réponse en direct
description: Résoudre les problèmes qui peuvent survenir lors de l’utilisation d’une réponse active dans Microsoft Defender pour point de terminaison
keywords: résoudre les problèmes de réponse en direct, en direct, réponse, verrouillé, fichier
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
ms.openlocfilehash: 3e9111edf7400ff09b366783a45ee40397bec81a
ms.sourcegitcommit: 62368e5a48e569c8e475b07d194d7d8ff7d167ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67560238"
---
# <a name="troubleshoot-microsoft-defender-for-endpoint-live-response-issues"></a>Résoudre Microsoft Defender pour point de terminaison problèmes de réponse en direct

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Cette page fournit des étapes détaillées pour résoudre les problèmes de réponse en direct.

## <a name="file-cannot-be-accessed-during-live-response-sessions"></a>Impossible d’accéder au fichier pendant les sessions de réponse en direct

Si, lors de la tentative d’action pendant une session de réponse en direct, vous rencontrez un message d’erreur indiquant que le fichier n’est pas accessible, vous devez suivre les étapes ci-dessous pour résoudre le problème.

1. Copiez l’extrait de code de script suivant et enregistrez-le sous la forme d’un fichier PS1 :

    ```powershell
    $copied_file_path=$args[0]
    $action=Copy-Item $copied_file_path -Destination $env:TEMP -PassThru -ErrorAction silentlyContinue

    if ($action){
         Write-Host "You copied the file specified in $copied_file_path to $env:TEMP Succesfully"
    }

    else{
        Write-Output "Error occoured while trying to copy a file, details:"
        Write-Output  $error[0].exception.message

    }
    ```

2. Ajoutez le script à la bibliothèque de réponses actives.
3. Exécutez le script avec un paramètre : le chemin d’accès du fichier à copier.
4. Accédez à votre dossier TEMP.
5. Exécutez l’action que vous souhaitez effectuer sur le fichier copié.

## <a name="slow-live-response-sessions-or-delays-during-initial-connections"></a>Sessions ou retards de réponse en direct lents pendant les connexions initiales

La réponse dynamique tire parti de l’inscription du capteur Defender pour point de terminaison avec le service WNS dans Windows. Si vous rencontrez des problèmes de connectivité avec la réponse en direct, confirmez les détails suivants :

1. WpnService (service système de notifications Push Windows) n’est pas désactivé.
2. La connectivité WpnService avec le cloud WNS n’est pas désactivée via la stratégie de groupe ou le paramètre GPM. [L’option « Désactiver l’utilisation du réseau de notifications »](/windows/client-management/mdm/policy-csp-notifications) ne doit pas être définie sur « 1 ».

Reportez-vous aux articles ci-dessous pour bien comprendre le comportement et les exigences du service WpnService :

- [Vue d’ensemble de Windows Push Notification Services (WNS)](/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview)
- [Configurations de pare-feu d’entreprise et de proxy pour prendre en charge le trafic WNS](/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)
- [Plages d’adresses IP publiques de Microsoft Push Notifications Service (MPNS)](https://www.microsoft.com/download/details.aspx?id=44535)
