---
title: Obtenir l’API d’alertes liées à la machine
description: Découvrez comment utiliser l’API d’alertes liées à l’ordinateur. Cette API vous permet de récupérer toutes les alertes liées à un appareil spécifique dans Microsoft Defender pour point de terminaison.
keywords: api, api graphe, api prises en charge, get, appareils, connexes, alertes
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
- tier3
ms.topic: conceptual
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 565ea2f2cf2902251771c7d3a04dd39c772521be
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68628705"
---
# <a name="get-machine-related-alerts--api"></a>Obtenir l’API d’alertes liées à la machine

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Récupère toutes les [alertes](alerts.md) liées à un appareil spécifique.

## <a name="limitations"></a>Limites

1. Vous pouvez interroger sur les appareils mis à jour pour la dernière fois en fonction de votre période de rétention configurée.
2. Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Alert.Read.All|« Lire toutes les alertes »
Application|Alert.ReadWrite.All|« Lire et écrire toutes les alertes »
Déléguée (compte professionnel ou scolaire) | Alert.Read | « Lire les alertes »
Déléguée (compte professionnel ou scolaire) | Alert.ReadWrite | « Lire et écrire des alertes »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit disposer au moins de l’autorisation de rôle suivante : « Afficher les données ». Pour plus d’informations sur les autorisations, consultez [Créer et gérer des rôles](user-roles.md).
> - L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres du groupe d’appareils. Pour plus d’informations sur les paramètres de groupe d’appareils, consultez [Créer et gérer des groupes d’appareils](machine-groups.md).
>
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.
## <a name="http-request"></a>Requête HTTP

```http
GET /api/machines/{id}/alerts
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation | Chaîne | Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

En cas de réussite et d’appareil : 200 OK avec la liste des entités [d’alerte](alerts.md) dans le corps. Si l’appareil est introuvable : 404 Introuvable.
