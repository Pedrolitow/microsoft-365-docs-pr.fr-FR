---
title: Résoudre les problèmes de licence pour Microsoft Defender ATP pour Mac
description: Résoudre les problèmes de licence dans Microsoft Defender ATP pour Mac.
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
ms.openlocfilehash: 44105ae8d1872c3ecefcf84a5e2efef122849b8c
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51066430"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-for-mac"></a>Résoudre les problèmes de licence pour Microsoft Defender pour Endpoint pour Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison pour Mac](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Pendant que vous êtes en cours d’utilisation de [Microsoft Defender pour Endpoint pour Mac](microsoft-defender-endpoint-mac.md) et de tests de déploiement manuel ou d’une preuve de concept, vous pouvez obtenir l’erreur suivante : [](mac-install-manually.md)

![Image de l’erreur de licence](images/no-license-found.png)

**Message:** 

Aucune licence trouvée

Il semble que votre organisation n’a pas de licence pour l’abonnement Microsoft 365 Entreprise.

Contactez votre administrateur pour obtenir de l'aide.

**Cause :** 

Vous avez déployé et/ou installé le package Microsoft Defender for Endpoint pour macOS (« Télécharger le package d’installation ») mais vous avez peut-être exécuté le script de configuration (« Télécharger le package d’intégration »).

**Solution :**

Suivez les instructions MicrosoftDefenderATPOnboardingMacOs.py documentées ici : [Configuration du client](mac-install-manually.md#client-configuration)

