---
title: Mettre à jour l’API d’entité de machine
description: Découvrez comment mettre à jour les balises de machine à l’aide de cette API. Vous pouvez mettre à jour les balises et les propriétés devicevalue.
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
ms.openlocfilehash: 640a5ec91fbfefe674f692e29ef9544dc54f14e1
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68644218"
---
# <a name="update-machine"></a>Mettre à jour l’ordinateur 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Mises à jour propriétés de [l’ordinateur](machine.md) existant.

Les propriétés pouvant être mises à jour sont : `machineTags` et `deviceValue`.

## <a name="limitations"></a>Limites

1. Vous pouvez mettre à jour les machines disponibles dans l’API. 
2. La machine de mise à jour ajoute uniquement des balises à la collection de balises. S’il existe des balises, elles doivent être incluses dans la collection de balises dans le corps.
3. Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Machine.ReadWrite.All|« Lire et écrire des informations sur l’ordinateur pour toutes les machines »
Déléguée (compte professionnel ou scolaire)|Machine.ReadWrite|« Lire et écrire des informations sur la machine »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
> - L’utilisateur doit disposer au moins de l’autorisation de rôle suivante : « Investigation des alertes ». Pour plus d’informations, consultez [Créer et gérer des rôles](user-roles.md).
> - L’utilisateur doit avoir accès à l’appareil associé à l’alerte, en fonction des paramètres du groupe d’appareils. Pour plus d’informations, consultez [Créer et gérer des groupes d’appareils](machine-groups.md).
>
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.

## <a name="http-request"></a>Requête HTTP

```http
PATCH /api/machines/{machineId}
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.
Content-Type|String|application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissez les valeurs des champs pertinents qui doivent être mis à jour.

Les propriétés existantes qui ne sont pas incluses dans le corps de la demande conserveront leurs valeurs précédentes ou seront recalculées en fonction des modifications apportées à d’autres valeurs des propriétés.

Pour de meilleures performances, vous ne devez pas inclure les valeurs existantes qui n’ont pas changé.

Propriété|Type|Description
:---|:---|:---
machineTags|Collection de chaînes|Ensemble de balises [d’ordinateur](machine.md) .
deviceValue|Énumération nullable|[Valeur de l’appareil](tvm-assign-device-value.md). Les valeurs possibles sont : ' Normal', 'Low' et 'High'.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode retourne 200 OK et l’entité [de machine](machine.md) dans le corps de la réponse avec les propriétés mises à jour.

Si la collection d’étiquettes de machine dans le corps ne contient pas de balises de machine existantes , remplace toutes les balises par les balises fournies dans le corps de la demande.

Si l’ordinateur avec l’ID spécifié est introuvable - 404 Introuvable.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de la requête.

```http
PATCH https://api.securitycenter.microsoft.com/api/machines/{machineId}
```

```json
{
    "deviceValue": "Normal",
    "machineTags": [
                     "Demo Device",
                     "Generic User Machine - Attack Source",
                     "Windows 10" "Windows11",
                     "Windows Insider - Fast"
    ]
}
```
