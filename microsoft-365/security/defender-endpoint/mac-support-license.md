---
title: Résoudre les problèmes de licence pour Microsoft Defender pour Endpoint pour Mac
description: Résolution des problèmes de licence dans Microsoft Defender pour Point de terminaison pour Mac.
keywords: microsoft, defender, atp, mac, performances
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
ms.openlocfilehash: 3fb351d9ce8e9beef812e6aaa7d463161a6af8df
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "51862186"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Résoudre les problèmes de licence pour Microsoft Defender pour le point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Pendant que vous êtes en cours d'utilisation de Microsoft Defender pour point de terminaison sur [macOS](microsoft-defender-endpoint-mac.md) et les tests de déploiement manuel ou d'une preuve de concept, vous pouvez obtenir l'erreur suivante : [](mac-install-manually.md)

![Image de l'erreur de licence](images/no-license-found.png)

**Message:** 

Aucune licence trouvée

Il semble que votre organisation n'a pas de licence pour l'abonnement Microsoft 365 Entreprise.

Contactez votre administrateur pour obtenir de l'aide.

**Cause :** 

Vous avez déployé et/ou installé microsoft Defender pour le point de terminaison sur le package macOS (« Télécharger le package d'installation ») mais vous avez peut-être exécuté le script de configuration (« Télécharger le package d'intégration »).

**Solution :**

Suivez les instructions MicrosoftDefenderATPOnboardingMacOs.py documentées ici : [Configuration du client](mac-install-manually.md#client-configuration)

