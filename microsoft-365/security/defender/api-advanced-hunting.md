---
title: MICROSOFT 365 DEFENDER’API de chasse avancée
description: Découvrez comment exécuter des requêtes de chasse avancées à l’aide de l’API de chasse avancée de Microsoft 365 Defender
keywords: Repérage avancé, API, API, M365 Defender, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.custom: api
ms.openlocfilehash: 4e0114e2a53a9fd532f49ef5c928e15751a9aa2e
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67482007"
---
# <a name="microsoft-365-defender-advanced-hunting-api"></a>MICROSOFT 365 DEFENDER API de chasse avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

[La chasse avancée](advanced-hunting-overview.md) est un outil de chasse aux menaces qui utilise des [requêtes spécialement construites](advanced-hunting-query-language.md) pour examiner les 30 derniers jours de données d’événements dans Microsoft 365 Defender. Vous pouvez utiliser des requêtes de chasse avancées pour inspecter les activités inhabituelles, détecter les menaces possibles et même répondre aux attaques. L’API de chasse avancée vous permet d’interroger par programmation des données d’événement.

## <a name="quotas-and-resource-allocation"></a>Quotas et allocation de ressources

Les conditions suivantes concernent toutes les requêtes.

1. Les requêtes explorent et retournent des données des 30 derniers jours.
2. Les résultats peuvent retourner jusqu’à 100 000 lignes.
3. Vous pouvez effectuer jusqu’à 45 appels par minute par locataire.
4. Les requêtes sont bloquées si le client a atteint 100 % jusqu’au terme du cycle de 15 minutes suivant.
5. Si une seule requête s’exécute pendant plus de 10 minutes, elle expire et retourne une erreur.
6. Un `429` code de réponse HTTP indique que vous avez atteint un quota, soit par nombre de demandes envoyées, soit par temps d’exécution alloué. Lisez le corps de la réponse pour comprendre la limite que vous avez atteinte. 

> [!NOTE]
> Tous les quotas répertoriés ci-dessus (par exemple, 15 appels par minute) sont au niveau du locataire. Ces quotas sont le minimum.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler l’API de chasse avancée. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Access the Microsoft 365 Defender Protection API](api-access.md).

Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation
-|-|-
Application | AdvancedHunting.Read.All| Exécuter des requêtes avancées
Déléguée (compte professionnel ou scolaire) | AdvancedHunting.Read | Exécuter des requêtes avancées

>[!Note]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
>- L’utilisateur doit avoir le rôle « Afficher les données ».
>- L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres du groupe d’appareils.

## <a name="http-request"></a>Requête HTTP

```HTTP
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a>En-têtes de demande

En-tête | Valeur
-|-
Autorisation | Note du porteur {token} **: obligatoire**
Content-Type | application/json

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissez un objet JSON avec les paramètres suivants :

Paramètre | Type | Description
-|-|-
Requête | Text | Requête à exécuter. **(obligatoire)**

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie `200 OK`et un objet _QueryResponse_ dans le corps de la réponse.

L’objet de réponse contient trois propriétés de niveau supérieur :

1. Statistiques : dictionnaire des statistiques de performances des requêtes.
2. Schéma : schéma de la réponse, liste de paires Name-Type pour chaque colonne.
3. Résultats : liste des événements de chasse avancés.

## <a name="example"></a>Exemple

Dans l’exemple suivant, un utilisateur envoie la requête ci-dessous et reçoit un objet de réponse d’API contenant `Stats`, `Schema`et `Results`.

### <a name="query"></a>Requête

```json
{
    "Query":"DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
}

```

### <a name="response-object"></a>Objet Response

```json
{
    "Stats": {
        "ExecutionTime": 4.621215,
        "resource_usage": {
            "cache": {
                "memory": {
                    "hits": 773461,
                    "misses": 4481,
                    "total": 777942
                },
                "disk": {
                    "hits": 994,
                    "misses": 197,
                    "total": 1191
                }
            },
            "cpu": {
                "user": "00:00:19.0468750",
                "kernel": "00:00:00.0156250",
                "total cpu": "00:00:19.0625000"
            },
            "memory": {
                "peak_per_node": 236822432
            }
        },
        "dataset_statistics": [
            {
                "table_row_count": 2,
                "table_size": 102
            }
        ]
    },
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
        }
    ],
    "Results": [
        {
            "Timestamp": "2020-08-30T06:38:35.7664356Z",
            "FileName": "conhost.exe",
            "InitiatingProcessFileName": "powershell.exe"
        },
        {
            "Timestamp": "2020-08-30T06:38:30.5163363Z",
            "FileName": "conhost.exe",
            "InitiatingProcessFileName": "powershell.exe"
        }
    ]
}
```

## <a name="related-articles"></a>Articles connexes

- [Accéder aux API Microsoft 365 Defender](api-access.md)
- [En savoir plus sur les limites d’API et les licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
