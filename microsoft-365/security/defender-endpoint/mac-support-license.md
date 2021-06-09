---
title: Résoudre les problèmes de licence pour Microsoft Defender pour endpoint sur Mac
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
ms.openlocfilehash: 1f8428c2995eec2dece290049eda67a3683b4c1e
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52244979"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Résoudre les problèmes de licence pour Microsoft Defender pour le point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Pendant que vous êtes en cours d’utilisation de Microsoft Defender pour point de terminaison sur [macOS](microsoft-defender-endpoint-mac.md) et les tests de déploiement manuel ou d’une preuve de concept, vous pouvez obtenir l’erreur suivante : [](mac-install-manually.md)

![Image de l’erreur de licence](images/no-license-found.png)

**Message:** 

Aucune licence trouvée

Il semble que votre organisation ne soit pas titulaire d’une licence Microsoft 365 Entreprise abonnement.

Contactez votre administrateur pour obtenir de l'aide.

**Cause :** 

Vous avez déployé et/ou installé le package Microsoft Defender for Endpoint pour macOS (« Télécharger le package d’installation ») mais vous avez peut-être exécuté le script de configuration (« Télécharger le package d’intégration ») ou vous n’avez pas attribué de licence à l’utilisateur.

**Solution :**

Suivez les instructions MicrosoftDefenderATPOnboardingMacOs.py documentées ici : [Configuration du client](mac-install-manually.md#client-configuration)
