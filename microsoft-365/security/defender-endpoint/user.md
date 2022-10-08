---
title: Type de ressource utilisateur
description: Récupérez les alertes de Microsoft Defender pour point de terminaison récentes liées aux utilisateurs.
keywords: api, api graphe, api prises en charge, get, alertes, recent
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: af00cc62ae86b31c440353a8885941856b94d6d7
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68225545"
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
[Répertorier les alertes liées à l’utilisateur](get-user-related-alerts.md)|collection[alert](alerts.md)|Répertorie toutes les alertes associées à un [utilisateur](user.md).
[Répertorier les appareils associés à l’utilisateur](get-user-related-machines.md)|[collection d’ordinateurs](machine.md)|Répertoriez tous les appareils qui ont été connectés par un [utilisateur](user.md).
