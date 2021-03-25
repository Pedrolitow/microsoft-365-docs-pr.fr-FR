---
title: Méthodes et propriétés de score
description: Récupère le score d’exposition de votre organisation, le score de sécurisation de l’appareil et le score d’exposition par groupe d’appareils
keywords: api, api de graphique, api pris en charge, score, score d’exposition, score de sécurité de l’appareil, score d’exposition par groupe d’appareils
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: ellevin
author: levinec
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 72dacca8529b54b082590d911f03aaa86bfe9097
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51200160"
---
# <a name="score-resource-type"></a>Type de ressource Score

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Méthodes

Méthode |Type renvoyé |Description
:---|:---|:---
[Obtenir le score d’exposition](get-exposure-score.md) | [Score](score.md) | Obtenir le score d’exposition de l’organisation.
[Obtenir le score de sécurité de l’appareil](get-device-secure-score.md) | [Score](score.md) | Obtenez le score de sécurité de l’appareil de l’organisation.
[Liste du score d’exposition par groupe d’appareils](get-machine-group-exposure-score.md)| [Score](score.md) | Liste des scores par groupe d’appareils.

## <a name="properties"></a>Propriétés

Propriété |  Type    |   Description
:---|:---|:---
Niveau | Double | Score actuel.
Temps | Date/heure | Date et heure à laquelle l’appel de cette API a été effectué.
RbacGroupName | Chaîne | Nom du groupe d’appareils.
