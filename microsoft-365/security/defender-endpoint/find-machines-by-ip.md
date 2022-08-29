---
title: Rechercher des appareils par API IP interne
description: Rechercher les appareils affichés avec l’adresse IP interne demandée dans l’intervalle de temps de 15 minutes avant et après un horodatage donné
keywords: api, api graphe, api prises en charge, get, device, IP, find, find device, by ip, ip
ms.prod: m365-security
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
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 84db0ee6740e6b6a47090a94ebc032d0176071f9
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67323336"
---
# <a name="find-devices-by-internal-ip-api"></a>Rechercher des appareils par API IP interne

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Recherchez [les ordinateurs](machine.md) affichés avec l’adresse IP interne demandée dans l’intervalle de temps de 15 minutes avant et après un horodatage donné.

## <a name="limitations"></a>Limites

1. L’horodatage donné doit se trouver au cours des 30 derniers jours.
2. Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Machine.Read.All|'Lire tous les profils d’ordinateur'
Application|Machine.ReadWrite.All|« Lire et écrire toutes les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire)|Machine.Read|« Lire les informations de l’ordinateur »
Déléguée (compte professionnel ou scolaire)|Machine.ReadWrite|« Lire et écrire des informations sur la machine »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - La réponse inclut uniquement les appareils auxquels l’utilisateur a accès en fonction des paramètres de groupe d’appareils (voir [Créer et gérer des groupes d’appareils](machine-groups.md) pour plus d’informations)
> - L’utilisateur doit disposer au moins de l’autorisation de rôle suivante : « Afficher les données » (voir [Créer et gérer des rôles](user-roles.md) pour plus d’informations)
> - La réponse inclut uniquement les appareils auxquels l’utilisateur a accès en fonction des paramètres de groupe d’appareils (voir [Créer et gérer des groupes d’appareils](machine-groups.md) pour plus d’informations)

## <a name="http-request"></a>Requête HTTP

```http
GET /api/machines/findbyip(ip='{IP}',timestamp={TimeStamp})
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

En cas de réussite - 200 OK avec la liste des machines dans le corps de la réponse.
Si l’horodatage n’est pas dans les 30 derniers jours - 400 Demande incorrecte.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de la requête.

```http
GET https://api.securitycenter.microsoft.com/api/machines/findbyip(ip='10.248.240.38',timestamp=2019-09-22T08:44:05Z)
```
