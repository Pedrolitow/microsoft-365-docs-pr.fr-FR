---
title: API mettre à jour l’entité de l’ordinateur
description: Découvrez comment mettre à jour des balises d’ordinateur à l’aide de cette API. Vous pouvez mettre à jour les balises et les propriétés devicevalue.
keywords: api, api de graphique, api pris en charge, obtenir, alerte, informations, ID
search.product: eADQiWindows 10XVcnh
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 787fcc3851d765a03d452d98106b522f239ea8c6
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61164165"
---
# <a name="update-machine"></a>Mettre à jour l’ordinateur 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Met à jour les propriétés de l’ordinateur [existant.](machine.md)

Les propriétés qui peuvent être mis à jour sont : `machineTags` et `deviceValue` .

## <a name="limitations"></a>Limites

1. Vous pouvez mettre à jour les ordinateurs disponibles dans l’API. 
2. L’ordinateur de mise à jour n’appende que les balises à la collection de balises. S’il existe des balises, elles doivent être incluses dans la collection de balises dans le corps.
3. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Machine.ReadWrite.All|« Lire et écrire des informations sur l’ordinateur pour tous les ordinateurs »
Déléguée (compte professionnel ou scolaire)|Machine.ReadWrite|« Lire et écrire des informations sur l’ordinateur »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
> - L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Investigation des alertes ». Pour plus d’informations, voir [Créer et gérer des rôles.](user-roles.md)
> - L’utilisateur doit avoir accès à l’appareil associé à l’alerte, en fonction des paramètres du groupe d’appareils. Pour plus d’informations, voir [Créer et gérer des groupes d’appareils.](machine-groups.md)

## <a name="http-request"></a>Requête HTTP

```http
PATCH /api/machines/{machineId}
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|String|Porteur {token}. **Obligatoire**.
Content-Type|String|application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissons les valeurs des champs appropriés qui doivent être mis à jour.

Les propriétés existantes qui ne sont pas incluses dans le corps de la demande conserveront leurs valeurs précédentes ou seront recalculées en fonction des modifications apportées à d’autres valeurs des propriétés.

Pour de meilleures performances, vous ne devez pas inclure de valeurs existantes qui n’ont pas changé.

Propriété|Type|Description
:---|:---|:---
machineTags|String collection|Ensemble de [balises d’ordinateur.](machine.md)
deviceValue|Nullable, enum|Valeur [de l’appareil.](tvm-assign-device-value.md) Les valeurs possibles sont : « Normal » (normal), « Low » (faible) et « High » (élevé).

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie 200 OK et l’entité [de l’ordinateur](machine.md) dans le corps de la réponse avec les propriétés mises à jour.

Si la collection de balises d’ordinateur dans le corps ne contient pas de balises d’ordinateur existantes , remplace toutes les balises par les balises fournies dans le corps de la demande.

Si l’ordinateur avec l’ID spécifié est in trouvé - 404 - In trouvé.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de la demande.

```http
PATCH https://api.securitycenter.microsoft.com/api/machines/{machineId}
```

```json
{
    "deviceValue": "Normal",
    "machineTags": [
                     "Demo Device",
                     "Generic User Machine - Attack Source",
                     "Windows 10",
                     "Windows Insider - Fast"
    ]
}
```
