---
title: Type de ressource utilisateur
description: Récupérer les alertes récentes de Microsoft Defender pour les points de terminaison relatives aux utilisateurs.
keywords: api, api de graphique, api pris en charge, obtenir, alertes, récent
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: f74e37e502db8a0406a8930dc29d3d35652de7a75d517c332ef219446e129a51
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53817170"
---
# <a name="user-resource-type"></a>Type de ressource utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


Méthode|Type renvoyé |Description
:---|:---|:---
[Liste des alertes associées à l’utilisateur](get-user-related-alerts.md) | collection[alert](alerts.md) |  Liste de toutes les alertes associées à un [utilisateur.](user.md)
[List User related devices](get-user-related-machines.md) | [collection d’ordinateurs](machine.md) | Liste de tous les appareils qui ont été connectés par un [utilisateur.](user.md)
