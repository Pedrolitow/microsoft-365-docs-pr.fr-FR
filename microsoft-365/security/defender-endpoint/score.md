---
title: Méthodes et propriétés du score
description: Récupère le score d’exposition, le score de sécurité de l’appareil et le score d’exposition de votre organisation par groupe d’appareils
keywords: api, API de graphe, api prises en charge, score, score d’exposition, score de sécurisation de l’appareil, score d’exposition par groupe d’appareils
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: d292acd836936d0112d617d4881845b69816858b
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68233813"
---
# <a name="score-resource-type"></a>Noter le type de ressource

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Méthodes

Méthode|Type renvoyé|Description
:---|:---|:---
[Obtenir un score d'exposition](get-exposure-score.md)|[Score](score.md)|Obtenez le score d’exposition de l’organisation.
[Obtenir un score sécurisé d’appareil](get-device-secure-score.md)|[Score](score.md)|Obtenez le score de sécurisation de l’appareil organisationnel.
[Répertorier le score d’exposition par groupe d’appareils](get-machine-group-exposure-score.md)|[Score](score.md)|Répertorie les scores par groupe d’appareils.

> [!NOTE]
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.  

## <a name="properties"></a>Propriétés

Propriété|Type|Description
:---|:---|:---
Niveau|Double|Score actuel.
Temps|Date/heure|Date et heure auxquelles l’appel pour cette API a été effectué.
RbacGroupName|Chaîne|Nom du groupe d’appareils.
RbacGroupId|Chaîne|ID du groupe d’appareils.
