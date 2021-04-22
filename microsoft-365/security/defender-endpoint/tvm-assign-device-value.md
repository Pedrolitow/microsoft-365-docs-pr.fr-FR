---
title: "Attribuer une valeur d'appareil : gestion des menaces et des vulnérabilités"
description: Découvrez comment affecter une valeur faible, normale ou élevée à un appareil pour vous aider à différencier les priorités des ressources.
keywords: Valeur de l'appareil Microsoft Defender for Endpoint, valeur de l'appareil de gestion des menaces et des vulnérabilités, appareils à valeur élevée, score d'exposition de la valeur de l'appareil
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
ms.openlocfilehash: ca6c88b08b331eb65035387a9c070d0914b1651d
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51935196"
---
# <a name="assign-device-value---threat-and-vulnerability-management"></a>Attribuer une valeur d'appareil : gestion des menaces et des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

La définition de la valeur d'un appareil vous permet de différencier les priorités des ressources. La valeur de l'appareil est utilisée pour incorporer le risque d'exposition d'un bien individuel dans le calcul du score d'exposition de la gestion des menaces et des vulnérabilités. Les appareils affectés en tant que « valeur élevée » recevront plus de poids.

Vous pouvez également utiliser [l'API définir la valeur de l'appareil.](set-device-value.md)

Options de valeur d'appareil :

- Faible
- Normal (valeur par défaut)
- Élevé

Exemples d'appareils à attribuer à une valeur élevée :

- Contrôleurs de domaine, Active Directory
- Appareils connectés à Internet
- Périphériques VIP
- Appareils hébergeant des services de production internes/externes

## <a name="choose-device-value"></a>Choisir la valeur de l'appareil

1. Accédez à n'importe quelle page d'appareil. L'endroit le plus simple est de consulter l'inventaire des appareils.

2. Sélectionnez **la valeur de** l'appareil à trois points près de la barre d'actions en haut de la page.

    ![Exemple de la valeur de l'appareil.](images/tvm-device-value-dropdown.png)

3. Un volant s'affiche avec la valeur actuelle de l'appareil et sa valeur. Examinez la valeur de l'appareil et choisissez celle qui convient le mieux à votre appareil.
![Exemple de volant de valeur d'appareil.](images/tvm-device-value-flyout.png)

## <a name="how-device-value-impacts-your-exposure-score"></a>Impact de la valeur de l'appareil sur votre score d'exposition

Le score d'exposition est une moyenne pondérée sur tous les appareils. Si vous avez des groupes d'appareils, vous pouvez également filtrer le score par groupe d'appareils.

- Les appareils normaux ont un poids de 1
- Les appareils à faible valeur ont un poids de 0,75
- Les appareils à valeur élevée ont un poids de NumberOfAssets / 10.
    - Si vous avez 100 appareils, chaque appareil à valeur élevée aura un poids de 10 (100/10)

## <a name="related-topics"></a>Voir aussi

- [Vue d'ensemble de la gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Score d'exposition](tvm-exposure-score.md)
- [API](next-gen-threat-and-vuln-mgt.md#apis)