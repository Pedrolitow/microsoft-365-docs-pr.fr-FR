---
title: Résoudre les problèmes sur Microsoft Defender pour le point de terminaison sur Android
description: Résoudre les problèmes de Microsoft Defender pour point de terminaison sur Android
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, mde, android, cloud, connectivité, communication
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
ms.openlocfilehash: d46a2ff2b1faa7360c27ca8c4571bd55e72ede1e93a8bf62dbc24d9f0ea08050
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53834432"
---
# <a name="troubleshooting-issues-on-microsoft-defender-for-endpoint-on-android"></a>Résolution des problèmes sur Microsoft Defender pour point de terminaison sur Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

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

Installer la dernière version et [les](https://play.google.com/store/apps/details?androidid=com.azure.authenticator) Microsoft Authenticator à partir de Google Play Store et essayer à nouveau

## <a name="sign-in-failed---invalid-license"></a>Échec de la signature - Licence non valide

**Échec de la signature : licence** non *valide, contactez l’administrateur*

![Image de l’échec de la connectez-vous. Contactez l’administrateur](images/920e433f440fa1d3d298e6a2a43d4811.png)

**Message : licence** *non valide, contactez l’administrateur*

**Cause :**

Vous n’avez pas Microsoft 365 licence attribuée ou votre organisation n’en a pas pour Microsoft 365 Entreprise abonnement.

**Solution :**

Contactez votre administrateur pour obtenir de l'aide.

## <a name="report-unsafe-site"></a>Signaler un site non sécurisé

Les sites web de hameçonnage usurpent l’identité de sites web dignes de confiance dans le but d’obtenir vos informations personnelles ou financières. Consultez la page [Fournir des commentaires sur la protection](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) du réseau si vous souhaitez signaler un site web qui pourrait être un site de hameçonnage.

## <a name="phishing-pages-arent-blocked-on-some-oem-devices"></a>Les pages de hameçonnage ne sont pas bloquées sur certains appareils OEM

**S’applique à :** OEM spécifiques uniquement

-   **Érmi**

L’hameçonnage et les menaces web dangereuses détectées par Defender pour Endpoint pour Android ne sont pas bloqués sur certains appareils. Les fonctionnalités suivantes ne fonctionnent pas sur ces appareils.

![Image du site signalé comme dangereux](images/0c04975c74746a5cdb085e1d9386e713.png)


**Cause :**

Les appareils Demi incluent un nouveau modèle d’autorisation. Cela empêche Defender pour point de terminaison pour Android d’afficher des fenêtres pop-up alors qu’elle s’exécute en arrière-plan.

Autorisation d’appareils : « Afficher les fenêtres pop-up en cours d’exécution en arrière-plan ».

![Image du paramètre de fenêtre pop-up](images/6e48e7b29daf50afddcc6c8c7d59fd64.png)

**Solution :**

Activez l’autorisation requise sur les appareils DeMi.

- Afficher les fenêtres pop-up en cours d’exécution en arrière-plan.
