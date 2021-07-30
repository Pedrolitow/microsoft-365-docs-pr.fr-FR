---
title: API Obtenir un incident
description: Découvrez comment utiliser l’API Obtenir des incidents pour obtenir un seul incident dans Microsoft 365 Defender.
keywords: api, api de graphique, api pris en charge, obtenir, fichier, hachage
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
ms.openlocfilehash: 6f1e59dd653ef0718797a4b71e67c3607b39824c
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53652586"
---
# <a name="get-incident-information-api"></a>API Obtenir des informations sur l’incident

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Récupère un incident spécifique par son ID

## <a name="limitations"></a>Limites

1. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API.

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
---|---|---
Application|Incident.Read.All|« Lire tous les incidents »
Application|Incident.ReadWrite.All|« Lire et écrire tous les incidents »
Déléguée (compte professionnel ou scolaire)|Incident.Read|' Read Incidents'
Déléguée (compte professionnel ou scolaire)|Incident.ReadWrite|« Lire et écrire des incidents »

> [!NOTE]
>
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Afficher les données »
> - La réponse inclut uniquement les incidents que l’utilisateur est exposé à

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

Si elle réussit, cette méthode renvoie 200 OK et l’entité d’incident dans le corps de la réponse.
Si l’incident avec l’ID spécifié n’a pas été trouvé - 404 - In trouvé.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
GET https://api.security.microsoft.com/api/incidents/{id}
```
