---
title: API Obtenir les alertes associées à l’ordinateur
description: Découvrez comment utiliser l’API Obtenir les alertes associées à l’ordinateur. Cette API vous permet de récupérer toutes les alertes liées à un appareil spécifique dans Microsoft Defender for Endpoint.
keywords: api, api de graphique, api pris en charge, obtenir, appareils, associés, alertes
search.product: eADQiWindows 10XVcnh
ms.prod: w10
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
ms.openlocfilehash: f9797d80bb0b7b66644b021169abf340c6071698
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60184580"
---
# <a name="get-machine-related-alerts--api"></a>API Obtenir les alertes associées à l’ordinateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Récupère toutes les [alertes associées](alerts.md) à un appareil spécifique.

## <a name="limitations"></a>Limites

1. Vous pouvez interroger sur les appareils la dernière mise à jour en fonction de votre période de rétention configurée.
2. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Alert.Read.All|« Lire toutes les alertes »
Application|Alert.ReadWrite.All|« Lire et écrire toutes les alertes »
Déléguée (compte professionnel ou scolaire) | Alert.Read | « Lire les alertes »
Déléguée (compte professionnel ou scolaire) | Alert.ReadWrite | « Lire et écrire des alertes »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Afficher les données ». Pour plus d’informations sur les autorisations, voir [Créer et gérer des rôles.](user-roles.md)
> - L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres de groupe d’appareils. Pour plus d’informations sur les paramètres de groupe d’appareils, voir [Créer et gérer des groupes d’appareils.](machine-groups.md)

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

En cas de réussite et si l’appareil existe : 200 OK avec la liste [des](alerts.md) entités d’alerte dans le corps. If device was not found: 404 Not Found.
