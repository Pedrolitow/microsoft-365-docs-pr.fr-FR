---
title: API de recherche avancée de menaces
ms.reviewer: ''
description: Découvrez comment utiliser l’API de recherche avancée pour exécuter des requêtes avancées sur Microsoft Defender for Endpoint. Découvrez les limitations et consultez un exemple.
keywords: api, api pris en charge, recherche avancée, requête
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
ms.openlocfilehash: 54883ab437dcf01b042b5458bdc6312eaf24d179
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59207412"
---
# <a name="advanced-hunting-api"></a>API de recherche avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="limitations"></a>Limites

1. Vous pouvez uniquement exécuter une requête sur les données des 30 derniers jours.

2. Les résultats incluent un maximum de 100 000 lignes.

3. Le nombre d’exécutions est limité par client :
   - Appels d’API : jusqu’à 45 appels par minute, jusqu’à 1 500 appels par heure.
   - Durée d’exécution : 10 minutes d’exécution toutes les heures et 3 heures d’exécution par jour.

4. La durée d’exécution maximale d’une seule demande est de 10 minutes.

5. La réponse 429 représente l’atteinte de la limite de quota soit par nombre de demandes, soit par processeur. Lire le corps de la réponse pour comprendre quelle limite a été atteinte. 

6. La taille maximale des résultats d’une requête ne peut pas dépasser 124 Mo. Si elle est dépassée, http 400 demande non autorisée avec le message « L’exécution de la requête a dépassé la taille de résultat autorisée. Optimisez votre requête en limitant la quantité de résultats et essayez à nouveau ».

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|AdvancedQuery.Read.All|« Exécuter des requêtes avancées »
Déléguée (compte professionnel ou scolaire)|AdvancedQuery.Read|« Exécuter des requêtes avancées »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit avoir le rôle AD « Afficher les données »
> - L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres de groupe d’appareils (voir Créer et gérer des groupes d’appareils [pour](machine-groups.md) plus d’informations)

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

Dans le corps de la demande, fournissons un objet JSON avec les paramètres suivants :

Paramètre|Type|Description
:---|:---|:---
Requête|Texte|Requête à exécuter. **Obligatoire**.

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
> L’objet de réponse illustré ici peut être tronqué pour des raisons de concision. Toutes les propriétés sont renvoyées à partir d’un appel réel.

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

## <a name="related-topics"></a>Rubriques connexes

- [Présentation des API Microsoft Defender pour les points de terminaison](apis-intro.md)
- [Recherche avancée à partir du portail](advanced-hunting-query-language.md)
- [Repérage avancé à l’aide de PowerShell](run-advanced-query-sample-powershell.md)
