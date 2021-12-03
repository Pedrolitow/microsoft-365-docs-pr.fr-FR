---
title: Type de ressource utilisateur
description: Récupérer les alertes récentes de Microsoft Defender pour les points de terminaison relatives aux utilisateurs.
keywords: api, api de graphique, api pris en charge, obtenir, alertes, récent
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
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 01b7eb32415e431dce37935abb4a1a69776db0f9
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2021
ms.locfileid: "61301977"
---
# <a name="user-resource-type"></a>Type de ressource utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Méthode|Type renvoyé|Description
---|---|---
[Liste des alertes associées à l’utilisateur](get-user-related-alerts.md)|collection[alert](alerts.md)|Liste de toutes les alertes associées à un [utilisateur.](user.md)
[List User related devices](get-user-related-machines.md)|[collection d’ordinateurs](machine.md)|Liste de tous les appareils qui ont été connectés par un [utilisateur.](user.md)
