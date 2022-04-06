---
title: Microsoft 365 Defender API de recherche avancée
description: Découvrez comment exécuter des requêtes de recherche avancée à l’aide Microsoft 365 Defender’API de recherche avancée de l’utilisateur
keywords: Recherche avancée, API, api, M365 Defender, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 05957fcf7cf2b3b03fbc757fc8b21e67156b285a
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500824"
---
# <a name="microsoft-365-defender-advanced-hunting-api"></a>Microsoft 365 Defender API de recherche avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

[Le recherche avancée](advanced-hunting-overview.md) est un outil de recherche de menaces qui utilise des requêtes spécialement conçues pour examiner les 30 derniers jours de données d’événement dans Microsoft 365 Defender.[](advanced-hunting-query-language.md) Vous pouvez utiliser des requêtes de recherche avancées pour inspecter les activités inhabituelles, détecter les menaces possibles et même répondre aux attaques. L’API de recherche avancée vous permet d’interroger par programmation des données d’événement.

## <a name="quotas-and-resource-allocation"></a>Quotas et allocation de ressources

Les conditions suivantes concernent toutes les requêtes.

1. Les requêtes explorent et retournent des données des 30 derniers jours.
2. Les résultats peuvent renvoyer jusqu’à 100 000 lignes.
3. Vous pouvez effectuer jusqu’à 45 appels par minute et par client.
4. Les requêtes sont bloquées si le client a atteint 100 % jusqu’au terme du cycle de 15 minutes suivant.
5. Si une seule demande s’exécute pendant plus de 10 minutes, elle prend du temps et retourne une erreur.
6. Un `429` code de réponse HTTP indique que vous avez atteint un quota, soit par nombre de demandes envoyées, soit par temps d’exécution alloué. Lisez le corps de la réponse pour comprendre la limite que vous avez atteinte. 

> [!NOTE]
> Tous les quotas répertoriés ci-dessus (par exemple, 15 appels par minute) sont par taille de client. Ces quotas sont au minimum.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler l’API de recherche avancée. Pour en savoir plus, notamment sur la façon de choisir les autorisations, voir [Les API Access Microsoft 365 Defender Protection](api-access.md)

Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation
-|-|-
Application | AdvancedQuery.Read.All| Exécuter des requêtes avancées
Déléguée (compte professionnel ou scolaire) | AdvancedQuery.Read | Exécuter des requêtes avancées

>[!Note]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
>- L’utilisateur doit avoir le rôle AD « Afficher les données »
>- L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres de groupe d’appareils.

## <a name="http-request"></a>Requête HTTP

```HTTP
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a>En-têtes de demande

En-tête | Valeur
-|-
Autorisation | Remarque {token} du porteur **: obligatoire**
Content-Type | application/json

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissons un objet JSON avec les paramètres suivants :

Paramètre | Type | Description
-|-|-
Requête | Texte | Requête à exécuter. **Remarque : obligatoire**

## <a name="response"></a>Réponse

Si elle réussit, cette méthode retourne `200 OK`un objet _QueryResponse_ dans le corps de la réponse.

L’objet de réponse contient trois propriétés de niveau supérieur :

1. Statistiques : dictionnaire des statistiques de performances des requêtes.
2. Schéma : schéma de la réponse, liste des Name-Type pour chaque colonne.
3. Résultats : liste des événements de recherche avancés.

## <a name="example"></a>Exemple

Dans l’exemple suivant, un utilisateur envoie la requête ci-dessous et reçoit un objet de réponse API contenant `Stats`, `Schema`et `Results`.

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

- [Accéder aux API Microsoft 365 Defender de données](api-access.md)
- [En savoir plus sur les limites d’API et les licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
