---
title: API de chasse avancée Microsoft 365 Defender
description: Découvrez comment exécuter des requêtes de chasse avancées à l’aide de l’API de chasse avancée de Microsoft 365 Defender
keywords: Chasse avancée, API, API, MTP, M365 Defender, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
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
ms.openlocfilehash: e7cd9192ec25e01ed06b77cb2b39357cb9df79bd
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719379"
---
# <a name="microsoft-365-defender-advanced-hunting-api"></a>API de chasse avancée Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Protection Microsoft contre les menaces

> [!IMPORTANT]
> Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

La [chasse avancée](advanced-hunting-overview.md) est un outil de recherche de menace qui utilise des [requêtes spécialement construites](advanced-hunting-query-language.md) pour examiner les 30 derniers jours de données d’événement dans Microsoft 365 Defender. Vous pouvez utiliser des requêtes de chasse avancées pour inspecter l’activité inhabituelle, détecter les menaces potentielles et même répondre aux attaques. L’API de chasse avancée vous permet d’interroger des données d’événement par programmation.

## <a name="quotas-and-resource-allocation"></a>Quotas et allocation des ressources

Les conditions suivantes sont liées à toutes les requêtes.

1. Les requêtes explorent et retournent les données des 30 derniers jours.
2. Les résultats peuvent renvoyer jusqu’à 100 000 lignes.
3. Vous pouvez effectuer jusqu’à 10 appels par minute par client.
4. Vous disposez de 10 minutes d’exécution par heure et par client.
5. Vous avez quatre heures au total du temps d’exécution par client.
6. Si une demande unique s’exécute pendant plus de 10 minutes, elle expire et renvoie une erreur.
7. Un `429` Code de réponse http indique que vous avez atteint un quota, soit le nombre de demandes envoyées, soit le temps d’exécution alloué. Le corps de la réponse inclura le temps jusqu’à ce que le quota que vous avez atteint soit réinitialisé.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler l’API de chasse avancée. Pour plus d’informations, notamment sur la façon de choisir des autorisations, consultez [la rubrique Access the Microsoft 365 Defender protection APIs](api-access.md)

Type d’autorisation | Autorisation | Nom d’affichage des autorisations
-|-|-
Application | AdvancedHunting. Read. All | Exécuter des requêtes avancées
Déléguée (compte professionnel ou scolaire) | AdvancedHunting. Read | Exécuter des requêtes avancées

>[!Note]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
>- L’utilisateur doit disposer du rôle « afficher les données » dans Active Directory.
>- L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres du groupe d’appareils.

## <a name="http-request"></a>Requête HTTP

```HTTP
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a>En-têtes de demande

En-tête | Valeur
-|-
Autorisation | Support {Token} **Remarque : obligatoire**
Content-Type | application/json

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissez un objet JSON avec les paramètres suivants :

Paramètre | Type | Description
-|-|-
Requête | Texte | Requête à exécuter. **Remarque : obligatoire**

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie `200 OK` et un objet _QueryResponse_ dans le corps de la réponse.

L’objet Response contient trois propriétés de niveau supérieur :

1. Stats-dictionnaire des statistiques de performances des requêtes.
2. Schema : le schéma de la réponse, une liste de paires Name-Type pour chaque colonne.
3. Results-liste d’événements de chasse avancés.

## <a name="example"></a>Exemple

Dans l’exemple suivant, un utilisateur envoie la requête ci-dessous et reçoit un objet de réponse d’API contenant `Stats` , `Schema` et `Results` .

### <a name="query"></a>Requête

```json
{
    "Query":"DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
}

```

### <a name="response-object"></a>Response, objet

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
- [En savoir plus sur les limites d’API et la gestion des licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
