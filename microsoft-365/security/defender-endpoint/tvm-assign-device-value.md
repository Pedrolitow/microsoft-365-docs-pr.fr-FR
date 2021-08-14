---
title: Affecter une valeur d’appareil - Gestion des menaces et des vulnérabilités
description: Découvrez comment affecter une valeur faible, normale ou élevée à un appareil pour vous aider à différencier les priorités des ressources.
keywords: Valeur de l’appareil Microsoft Defender pour le point de terminaison, Gestion des menaces et des vulnérabilités valeur de l’appareil, appareils à valeur élevée, score d’exposition de la valeur d’appareil
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 687b125b0b48a6f2adbaaaff9019c7202e1b2228b043160e2d13a6d91a3eeb14
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53894054"
---
# <a name="assign-device-value---threat-and-vulnerability-management"></a>Affecter une valeur d’appareil - Gestion des menaces et des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [La gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

La définition de la valeur d’un appareil vous permet de différencier les priorités des biens. La valeur de l’appareil est utilisée pour incorporer le risque d’exposition d’un bien individuel dans le calcul Gestion des menaces et des vulnérabilités score d’exposition. Les appareils affectés en tant que « valeur élevée » recevront plus de poids.

Vous pouvez également utiliser [l’API définir la valeur de l’appareil.](set-device-value.md)

Options de valeur d’appareil :

- Faible
- Normal (valeur par défaut)
- Élevé

Exemples d’appareils à attribuer à une valeur élevée :

- Contrôleurs de domaine, Active Directory
- Appareils connectés à Internet
- Périphériques VIP
- Appareils hébergeant des services de production internes/externes

## <a name="choose-device-value"></a>Choisir la valeur de l’appareil

1. Accédez à n’importe quelle page d’appareil. L’endroit le plus simple est de consulter l’inventaire des appareils.

2. Sélectionnez **la valeur de** l’appareil à trois points près de la barre d’actions en haut de la page.

    ![Exemple de la valeur de l’appareil.](images/tvm-device-value-dropdown.png)

3. Un volant s’affiche avec la valeur actuelle de l’appareil et sa valeur. Examinez la valeur de l’appareil et choisissez celle qui convient le mieux à votre appareil.
![Exemple de volant de valeur d’appareil.](images/tvm-device-value-flyout.png)

## <a name="how-device-value-impacts-your-exposure-score"></a>Impact de la valeur de l’appareil sur votre score d’exposition

Le score d’exposition est une moyenne pondérée sur tous les appareils. Si vous avez des groupes d’appareils, vous pouvez également filtrer le score par groupe d’appareils.

- Les appareils normaux ont un poids de 1
- Les appareils à faible valeur ont un poids de 0,75
- Les appareils à valeur élevée ont un poids de NumberOfAssets / 10.
    - Si vous avez 100 appareils, chaque appareil à valeur élevée aura un poids de 10 (100/10)

## <a name="related-topics"></a>Sujets connexes

- [Vue d’ensemble gestion des vulnérabilités menaces et gestion des vulnérabilités menaces](next-gen-threat-and-vuln-mgt.md)
- [Score d’exposition](tvm-exposure-score.md)
- [API](next-gen-threat-and-vuln-mgt.md#apis)