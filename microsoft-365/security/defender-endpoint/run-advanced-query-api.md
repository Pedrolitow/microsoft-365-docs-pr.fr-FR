---
title: API de recherche avancée de menaces
ms.reviewer: ''
description: Apprenez à utiliser l’API de chasse avancée pour exécuter des requêtes avancées sur Microsoft Defender pour point de terminaison. Découvrez les limitations et consultez un exemple.
keywords: api, api prises en charge, repérage avancé, requête
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
ms.openlocfilehash: c813127a138b4050252d47cceedfc0131e3af9a3
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68636385"
---
# <a name="advanced-hunting-api"></a>API de chasse avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

> [!NOTE]
> Cette API peut uniquement interroger des tables appartenant à Microsoft Defender pour point de terminaison. Les tables appartenant à d’autres services Microsoft 365 Defender nécessitent l’utilisation de [l’API de chasse avancée Microsoft 365 Defender](/microsoft-365/security/defender/api-advanced-hunting).

## <a name="limitations"></a>Limites

1. Vous ne pouvez exécuter une requête que sur les données des 30 derniers jours.

2. Les résultats incluent un maximum de 10 000 lignes.

3. Le nombre d’exécutions est limité par locataire :
   - Appels d’API : jusqu’à 45 appels par minute, jusqu’à 1 500 appels par heure.
   - Durée d’exécution : 10 minutes de temps d’exécution toutes les heures et 3 heures d’exécution par jour.

4. Le temps d’exécution maximal d’une requête unique est de 200 secondes.

5. La réponse 429 représente l’atteinte de la limite de quota par nombre de demandes ou par processeur. Lisez le corps de la réponse pour comprendre quelle limite a été atteinte.

6. La taille maximale du résultat d’une requête ne peut pas dépasser 124 Mo. Si la valeur est dépassée, http 400 Demande incorrecte avec le message « L’exécution de la requête a dépassé la taille de résultat autorisée. Optimiser votre requête en limitant le nombre de résultats et réessayer » s’affiche.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|AdvancedQuery.Read.All|'Exécuter des requêtes avancées'
Déléguée (compte professionnel ou scolaire)|AdvancedQuery.Read|'Exécuter des requêtes avancées'

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit avoir le rôle AD « Afficher les données »
> - L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres du groupe d’appareils (voir [Créer et gérer des groupes d’appareils](machine-groups.md) pour plus d’informations)
>
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.  

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/advancedqueries/run
```

## <a name="request-headers"></a>En-têtes de demande

En-tête|Valeur
:---|:---
Autorisation|Porteur {token}. **Obligatoire**.
Content-Type|application/json

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissez un objet JSON avec les paramètres suivants :

Paramètre|Type|Description
:---|:---|:---
Requête|Text|Requête à exécuter. **Obligatoire**.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie 200 OK et l’objet _QueryResponse_ dans le corps de la réponse.

## <a name="example"></a>Exemple

### <a name="request-example"></a>Exemple de requête

Voici un exemple de demande.

```http
POST https://api.securitycenter.microsoft.com/api/advancedqueries/run
```

```json
{
    "Query":"DeviceProcessEvents
|where InitiatingProcessFileName =~ 'powershell.exe'
|where ProcessCommandLine contains 'appdata'
|project Timestamp, FileName, InitiatingProcessFileName, DeviceId
|limit 2"
}
```

### <a name="response-example"></a>Exemple de réponse

Voici un exemple de réponse.

> [!NOTE]
> L’objet de réponse présenté ici peut être tronqué par souci de concision. Toutes les propriétés sont renvoyées à partir d’un appel réel.

```json
{
    "Schema": [
        {
            "Name": "Timestamp",
            "Type": "DateTime"
        },
        {
            "Name": "FileName",
            "Type": "String"
        },
        {
            "Name": "InitiatingProcessFileName",
            "Type": "String"
        },
        {
            "Name": "DeviceId",
            "Type": "String"
        }
    ],
    "Results": [
        {
            "Timestamp": "2020-02-05T01:10:26.2648757Z",
            "FileName": "csc.exe",
            "InitiatingProcessFileName": "powershell.exe",
            "DeviceId": "10cbf9182d4e95660362f65cfa67c7731f62fdb3"
        },
        {
            "Timestamp": "2020-02-05T01:10:26.5614772Z",
            "FileName": "csc.exe",
            "InitiatingProcessFileName": "powershell.exe",
            "DeviceId": "10cbf9182d4e95660362f65cfa67c7731f62fdb3"
        }
    ]
}
```

## <a name="related-topics"></a>Voir aussi

- [présentation des API Microsoft Defender pour point de terminaison](apis-intro.md)
- [Repérage avancé à partir du portail](advanced-hunting-query-language.md)
- [Repérage avancé à l’aide de PowerShell](run-advanced-query-sample-powershell.md)
