---
title: API De liste des ordinateurs
description: Découvrez comment utiliser l’API Des ordinateurs de liste pour récupérer une collection d’ordinateurs ayant communiqué avec Microsoft Defender pour le cloud endpoint.
keywords: api, api de graphique, api pris en charge, obtenir, appareils
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.topic: article
ms.collection: M365-security-compliance
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 8ffeca3d13b42e39f539e96d563aceabd464aeaf
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59181127"
---
# <a name="list-machines-api"></a>API De liste des ordinateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Récupère une collection [d’ordinateurs](machine.md) qui ont communiqué avec Microsoft Defender pour le cloud endpoint.

Prend [en charge les requêtes OData V4.](https://www.odata.org/documentation/)

La requête OData est prise en charge sur `$filter` : , , , , , , , `computerDnsName` , , `id` et `version` `deviceValue` `aadDeviceId` `machineTags` `lastSeen` `exposureLevel` `lastIpAddress` `healthStatus` `osPlatform` `riskScore` `rbacGroupId` .
<br>```$stop``` avec une valeur maximale de 10 000
<br>```$skip``` Voir des exemples [dans les requêtes OData avec Defender for Endpoint](exposed-apis-odata-samples.md)

## <a name="limitations"></a>Limites

1. Vous pouvez obtenir la dernière vue des appareils en fonction de votre période de rétention configurée.
2. La taille maximale de page est de 10 000.
3. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure. 

## <a name="permissions"></a>Autorisations

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Machine.Read.All|« Lire tous les profils d’ordinateur »
Application|Machine.ReadWrite.All|« Lire et écrire toutes les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire)|Machine.Read|« Lire les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire)|Machine.ReadWrite|« Lire et écrire des informations sur l’ordinateur »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Afficher les données » (voir Créer et gérer des rôles [pour](user-roles.md) plus d’informations)
> - La réponse inclut uniquement les appareils, accessibles par l’utilisateur, en fonction des paramètres de groupe d’appareils (pour plus d’informations, voir Créer et gérer des groupes d’appareils) [](machine-groups.md)

## <a name="http-request"></a>Requête HTTP

```http
GET https://api.securitycenter.microsoft.com/api/machines
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

En cas de réussite et si les ordinateurs existent : 200 - OK avec la liste des entités de [l’ordinateur](machine.md) dans le corps. Si aucun ordinateur récent - 404 - In trouvé.

## <a name="example"></a>Exemple

### <a name="request-example"></a>Exemple de requête

Voici un exemple de demande.

```http
GET https://api.securitycenter.microsoft.com/api/machines
```

### <a name="response-example"></a>Exemple de réponse

Voici un exemple de réponse.

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Machines",
    "value": [
        {
            "id": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07",
            "computerDnsName": "mymachine1.contoso.com",
            "firstSeen": "2018-08-02T14:55:03.7791856Z",
            "lastSeen": "2018-08-02T14:55:03.7791856Z",
            "osPlatform": "Windows10",
            "version": "1709",
            "osProcessor": "x64",
            "lastIpAddress": "172.17.230.209",
            "lastExternalIpAddress": "167.220.196.71",
            "osBuild": 18209,
            "healthStatus": "Active",
            "rbacGroupId": 140,
            "rbacGroupName": "The-A-Team",
            "riskScore": "Low",
            "exposureLevel": "Medium",
            "isAadJoined": true,
            "aadDeviceId": "80fe8ff8-2624-418e-9591-41f0491218f9",
            "machineTags": [ "test tag 1", "test tag 2" ]
        }
        ...
    ]
}
```

## <a name="related-topics"></a>Rubriques connexes

- [Requêtes OData avec Microsoft Defender pour le point de terminaison](exposed-apis-odata-samples.md)
