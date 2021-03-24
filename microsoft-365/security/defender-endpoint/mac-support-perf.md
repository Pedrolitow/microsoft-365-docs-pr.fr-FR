---
title: Résoudre les problèmes de performances pour Microsoft Defender ATP pour Mac
description: Résolution des problèmes de performances dans Microsoft Defender ATP pour Mac.
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
ms.openlocfilehash: dbd82bae86ac4181497ecc87bc74181f7a502e15
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51062222"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-for-mac"></a>Résoudre les problèmes de performances pour Microsoft Defender pour Endpoint pour Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison pour Mac](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique fournit quelques étapes générales qui peuvent être utilisées pour affiner les problèmes de performances liés à Microsoft Defender pour Endpoint pour Mac.

La protection en temps réel (RTP) est une fonctionnalité de Microsoft Defender pour Endpoint pour Mac qui surveille et protège en permanence votre appareil contre les menaces. Il se compose de la surveillance des fichiers et des processus et d’autres heuristiques.

Selon les applications que vous exécutez et les caractéristiques de votre appareil, vous pouvez obtenir des performances sous-optimales lors de l’exécution de Microsoft Defender pour Endpoint pour Mac. En particulier, les applications ou les processus système qui accèdent à de nombreuses ressources sur un court laps de temps peuvent entraîner des problèmes de performances dans Microsoft Defender pour Endpoint pour Mac.

Les étapes suivantes peuvent être utilisées pour résoudre et atténuer ces problèmes :

1. Désactivez la protection en temps réel à l’aide de l’une des méthodes suivantes et observez si les performances sont améliorées. Cette approche permet de déterminer si Microsoft Defender pour Endpoint pour Mac contribue aux problèmes de performances.

    Si votre appareil n’est pas géré par votre organisation, la protection en temps réel peut être désactivée à l’aide de l’une des options suivantes :

    - À partir de l’interface utilisateur. Ouvrez Microsoft Defender pour le point de terminaison pour Mac et accédez **à Gérer les paramètres.**

      ![Capture d’écran gérer la protection en temps réel](/windows/security/threat-protection/microsoft-defender-antivirus/images/mdatp-36-rtp)

    - À partir du terminal. Pour des raisons de sécurité, cette opération nécessite une élévation.

      ```bash
      mdatp config real-time-protection --value disabled
      ```

    Si votre appareil est géré par votre organisation, la protection en temps réel peut être désactivée par votre administrateur à l’aide des instructions dans Définir les préférences pour [Microsoft Defender pour Endpoint pour Mac.](mac-preferences.md)

2. Ouvrez Finder et accédez aux  >  **utilitaires d’applications.** Ouvrez **l’Analyseur** d’activité et analysez les applications qui utilisent les ressources de votre système. Les compilateurs et les outils de mise à jour logicielles sont des exemples classiques.

3. Configurez Microsoft Defender pour endpoint pour Mac avec des exclusions pour les processus ou les emplacements de disque qui contribuent aux problèmes de performances et activez à nouveau la protection en temps réel.

    Pour plus d’informations, voir Configurer et valider des [exclusions pour Microsoft Defender pour Endpoint pour Mac.](mac-exclusions.md)
