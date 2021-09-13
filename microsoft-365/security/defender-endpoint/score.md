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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 9a8b87a7cee3bb03a0946773012ed6f18bbd75b9
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204654"
---
# <a name="score-resource-type"></a>Type de ressource Score

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
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
