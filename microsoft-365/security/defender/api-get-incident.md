---
title: Obtenir l’API d’incident
description: Découvrez comment utiliser l’API Obtenir les incidents pour obtenir un seul incident dans Microsoft 365 Defender.
keywords: api, api graphe, api prises en charge, get, file, hash
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.topic: article
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 17eb5fbb7249ba3ff38c30267632447d0c594f17
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68078060"
---
# <a name="get-incident-information-api"></a>Obtenir l’API d’informations sur les incidents

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Récupère un incident spécifique par son ID

## <a name="limitations"></a>Limites

1. Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API.

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
---|---|---
Application|Incident.Read.All|« Lire tous les incidents »
Application|Incident.ReadWrite.All|« Lire et écrire tous les incidents »
Déléguée (compte professionnel ou scolaire)|Incident.Read|« Lire les incidents »
Déléguée (compte professionnel ou scolaire)|Incident.ReadWrite|« Lire et écrire des incidents »

> [!NOTE]
>
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit disposer au moins de l’autorisation de rôle suivante : « Afficher les données »
> - La réponse inclut uniquement les incidents auxquels l’utilisateur est exposé

## <a name="http-request"></a>Requête HTTP

```console
GET .../api/incidents/{id}
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
---|---|---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

Si elle réussit, cette méthode retourne 200 OK et l’entité d’incident dans le corps de la réponse.
Si l’incident avec l’ID spécifié est introuvable - 404 Introuvable.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de la requête.

```http
GET https://api.security.microsoft.com/api/incidents/{id}
```
