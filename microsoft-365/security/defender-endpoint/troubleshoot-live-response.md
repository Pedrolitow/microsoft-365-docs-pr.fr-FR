---
title: Résoudre les problèmes de réponse en direct de Microsoft Defender pour les points de terminaison
description: Résoudre les problèmes qui peuvent survenir lors de l’utilisation d’une réponse en direct dans Microsoft Defender pour le point de terminaison
keywords: résoudre les problèmes de réponse en direct, en direct, réponse, verrouillé, fichier
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.openlocfilehash: 14caf0b2e0467d0f9e844a2dd996c6ccb4cfab30
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60191598"
---
# <a name="troubleshoot-microsoft-defender-for-endpoint-live-response-issues"></a>Résoudre les problèmes de réponse en direct de Microsoft Defender pour les points de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Cette page fournit des étapes détaillées pour résoudre les problèmes de réponse en direct.

## <a name="file-cannot-be-accessed-during-live-response-sessions"></a>Impossible d’accéder au fichier pendant les sessions de réponse en direct

Si, lors d’une tentative d’action au cours d’une session de réponse en direct, vous rencontrez un message d’erreur indiquant que le fichier n’est pas accessible, vous devez suivre les étapes ci-dessous pour résoudre le problème.

1. Copiez l’extrait de code de script suivant et enregistrez-le en tant que fichier PS1 :

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

2. Ajoutez le script à la bibliothèque de réponses en direct.
3. Exécutez le script avec un paramètre : le chemin d’accès au fichier à copier.
4. Accédez à votre dossier TEMP.
5. Exécutez l’action que vous souhaitez exécuter sur le fichier copié.

## <a name="slow-live-response-sessions-or-delays-during-initial-connections"></a>Sessions de réponse en direct lentes ou retards pendant les connexions initiales

Live Response tire parti de Defender pour l’inscription du capteur de point de terminaison auprès du service WNS dans Windows. Si vous avez des problèmes de connectivité avec la réponse en direct, confirmez les détails suivants :

1. `notify.windows.com` n’est pas bloqué dans votre environnement. Pour plus d’informations, voir Configurer [les paramètres de proxy d’appareil et de connectivité Internet.](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)
2. WpnService (Windows Service système de notifications Push) n’est pas désactivé.

Reportez-vous aux articles ci-dessous pour bien comprendre le comportement et les exigences du service WpnService :

- [Windows Vue d’Notification Services (WNS) Push](/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview)
- [Enterprise Configurations de pare-feu et de proxy pour prendre en charge le trafic WNS](/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)
- [Plages IP publiques MPNS (Microsoft Push Notifications Service)](https://www.microsoft.com/download/details.aspx?id=44535)
