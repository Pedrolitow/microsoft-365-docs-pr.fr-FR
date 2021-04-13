---
title: Résoudre les problèmes sur Microsoft Defender pour le point de terminaison pour Android
description: Résoudre les problèmes de Microsoft Defender pour le point de terminaison pour Android
keywords: microsoft, defender, atp, mde, android, cloud, connectivité, communication
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5fabcb3156a54d4aa8a4671d7561a8deca16fe1f
ms.sourcegitcommit: 987f70e44e406ab6b1dd35f336a9d0c228032794
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2021
ms.locfileid: "51587646"
---
# <a name="troubleshooting-issues-on-microsoft-defender-for-endpoint-for-android"></a>Résolution des problèmes sur Microsoft Defender pour le point de terminaison pour Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

Lors de l’intégration d’un appareil, vous pouvez voir des problèmes de connectez-vous après l’installation de l’application.

Lors de l’intégration, vous pouvez rencontrer des problèmes de connectez-vous après l’installation de l’application sur votre appareil.

Cet article fournit des solutions pour vous aider à résoudre les problèmes d' sign-on.  

## <a name="sign-in-failed---unexpected-error"></a>Échec de la signature : erreur inattendue
**Échec de la signature : erreur** *inattendue, essayez ultérieurement*

![Image de l’erreur d’échec de la signature - Erreur inattendue](images/f9c3bad127d636c1f150d79814f35d4c.png)

**Message:**

Erreur inattendue, essayez ultérieurement

**Cause :**

Une version antérieure de l’application « Microsoft Authenticator » est installée sur votre appareil.

**Solution :**

Installer la dernière version et [Microsoft Authenticator](https://play.google.com/store/apps/details?androidid=com.azure.authenticator) à partir de Google Play Store et essayer à nouveau

## <a name="sign-in-failed---invalid-license"></a>Échec de la signature - Licence non valide

**Échec de la signature : licence** non *valide, contactez l’administrateur*

![Image de l’échec de la signature: contactez l’administrateur](images/920e433f440fa1d3d298e6a2a43d4811.png)

**Message : licence** *non valide, contactez l’administrateur*

**Cause :**

Vous n’avez pas de licence Microsoft 365 attribuée ou votre organisation n’a pas de licence pour l’abonnement Microsoft 365 Entreprise.

**Solution :**

Contactez votre administrateur pour obtenir de l'aide.

## <a name="phishing-pages-arent-blocked-on-some-oem-devices"></a>Les pages de hameçonnage ne sont pas bloquées sur certains appareils OEM

**S’applique à :** OEM spécifiques uniquement

-   **Érmi**

L’hameçonnage et les menaces web dangereuses détectées par Defender pour Endpoint pour Android ne sont pas bloqués sur certains appareils Android. Les fonctionnalités suivantes ne fonctionnent pas sur ces appareils.

![Image du site signalé comme dangereux](images/0c04975c74746a5cdb085e1d9386e713.png)


**Cause :**

Les appareils Demi incluent un nouveau modèle d’autorisation. Cela empêche Defender pour point de terminaison pour Android d’afficher des fenêtres pop-up alors qu’elle s’exécute en arrière-plan.

Autorisation d’appareils : « Afficher les fenêtres pop-up en cours d’exécution en arrière-plan ».

![Image du paramètre de fenêtre pop-up](images/6e48e7b29daf50afddcc6c8c7d59fd64.png)

**Solution :**

Activez l’autorisation requise sur les appareils DeMi.

- Afficher les fenêtres pop-up en cours d’exécution en arrière-plan.