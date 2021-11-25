---
title: Méthodes et propriétés du score
description: Récupère le score d’exposition de votre organisation, le score de sécurisation de l’appareil et le score d’exposition par groupe d’appareils
keywords: api, api de graphique, api pris en charge, score, score d’exposition, score de sécurité de l’appareil, score d’exposition par groupe d’appareils
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 96a565456f0e95ffc33cbff9a36abcf24db94c24
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61160538"
---
# <a name="score-resource-type"></a>Type de ressource Score

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Méthodes

Méthode|Type renvoyé|Description
:---|:---|:---
[Obtenir un score d'exposition](get-exposure-score.md)|[Score](score.md)|Obtenir le score d’exposition de l’organisation.
[Obtenir un score sécurisé d’appareil](get-device-secure-score.md)|[Score](score.md)|Obtenez le score de sécurité de l’appareil de l’organisation.
[Liste du score d’exposition par groupe d’appareils](get-machine-group-exposure-score.md)|[Score](score.md)|Liste des scores par groupe d’appareils.

## <a name="properties"></a>Propriétés

Propriété|Type|Description
:---|:---|:---
Niveau|Double|Score actuel.
Temps|Date/heure|Date et heure à laquelle l’appel de cette API a été effectué.
RbacGroupName|String|Nom du groupe d’appareils.
RbacGroupId|String|ID du groupe d’appareils.
