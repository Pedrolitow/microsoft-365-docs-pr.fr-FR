---
title: Résoudre les problèmes de licence pour Microsoft Defender pour point de terminaison sur Mac
description: Résolution des problèmes de licence dans Microsoft Defender pour point de terminaison sur Mac.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, performances
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5b1cee16f4eccaa8f6fd36d8764b1305cba3131f
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204768"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Résoudre les problèmes de licence pour Microsoft Defender pour le point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Pendant que vous êtes en cours d’utilisation de Microsoft Defender pour point de terminaison sur [macOS](microsoft-defender-endpoint-mac.md) et les tests de déploiement manuel ou d’une preuve de concept, vous pouvez obtenir l’erreur suivante : [](mac-install-manually.md)

![Image de l’erreur de licence.](images/no-license-found.png)

**Message:** 

Aucune licence trouvée

Il semble que votre organisation ne soit pas titulaire d’une licence Microsoft 365 Entreprise abonnement.

Contactez votre administrateur pour obtenir de l'aide.

**Cause :** 

Vous avez déployé et/ou installé le package Microsoft Defender for Endpoint pour macOS (« Télécharger le package d’installation ») mais vous n’avez peut-être pas exécuté le script de configuration (« Télécharger le package d’intégration ») ou vous n’avez pas attribué de licence à l’utilisateur.

**Solution :**

Suivez les instructions MicrosoftDefenderATPOnboardingMacOs.py documentées ici : [Configuration du client](mac-install-manually.md#client-configuration)
