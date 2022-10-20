---
title: Obtenir des informations d’alerte par API d’ID
description: Découvrez comment utiliser l’API Obtenir des informations d’alerte par ID pour récupérer une alerte spécifique par son ID dans Microsoft Defender pour point de terminaison.
keywords: api, api graphe, api prises en charge, get, alert, information, id
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
ms.openlocfilehash: cf46eacec1a8cc3ac30606579dfa285664dec046
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68642610"
---
# <a name="get-alert-information-by-id-api"></a>Obtenir des informations d’alerte par API d’ID

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Récupère une [alerte](alerts.md) spécifique par son ID.

## <a name="limitations"></a>Limites

- Vous pouvez obtenir la dernière mise à jour des alertes en fonction de votre période de rétention configurée.
- Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md).

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Alert.Read.All|« Lire toutes les alertes »
Application|Alert.ReadWrite.All|« Lire et écrire toutes les alertes »
Déléguée (compte professionnel ou scolaire)|Alert.Read|« Lire les alertes »
Déléguée (compte professionnel ou scolaire)|Alert.ReadWrite|« Lire et écrire des alertes »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit disposer au moins de l’autorisation de rôle suivante : « Afficher les données » (voir [Créer et gérer des rôles](user-roles.md) pour plus d’informations)
> - L’utilisateur doit avoir accès à l’appareil associé à l’alerte, en fonction des paramètres du groupe d’appareils (voir [Créer et gérer des groupes d’appareils](machine-groups.md) pour plus d’informations)
>
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.

## <a name="http-request"></a>Requête HTTP

```http
GET /api/alerts/{id}
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

Si elle réussit, cette méthode retourne 200 OK et l’entité [d’alerte](alerts.md) dans le corps de la réponse. Si l’alerte avec l’ID spécifié est introuvable - 404 Introuvable.
