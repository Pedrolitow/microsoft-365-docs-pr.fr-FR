---
title: API de chasse avancée
description: Découvrez comment exécuter des requêtes de chasse avancées à l’aide de l’API Microsoft Threat Protection
keywords: Chasse avancée, API, API, MTP
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
ms.openlocfilehash: 92d5d2840963ae00ae0f03e3359f287371f770ee
ms.sourcegitcommit: 9a275a13af3e063e80ce1bd3cd8142a095db92d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "47650300"
---
# <a name="advanced-hunting-apis"></a>API de chasse avancée

**S’applique à :**
- Protection Microsoft contre les menaces

>[!IMPORTANT] 
>Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

## <a name="limitations"></a>Limites
1. Vous pouvez uniquement exécuter une requête sur les données des 30 derniers jours.
2. Les résultats incluent un maximum de 100 000 lignes.
3. Le nombre d’exécutions est limité par client : jusqu’à 15 appels par minute, 15 minutes d’exécution toutes les heures et 4 heures de temps d’exécution par jour.
4. Le temps d’exécution maximal d’une demande unique est de 10 minutes.

## <a name="permissions"></a>Autorisations
L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur la façon de choisir des autorisations, consultez [la rubrique Access the Microsoft Threat Protection APIs](api-access.md)

Type d’autorisation |   Autorisation  |   Nom d’affichage des autorisations
:---|:---|:---
Application |   AdvancedHunting. Read. All |  « Exécuter des requêtes avancées »
Déléguée (compte professionnel ou scolaire) | AdvancedHunting. Read | « Exécuter des requêtes avancées »

>[!Note]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>- L’utilisateur doit disposer du rôle AD « afficher les données »
>- L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres du groupe d’appareils.

## <a name="http-request"></a>Requête HTTP
```
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a>En-têtes de demande

En-tête | Valeur 
:---|:---
Autorisation | Porteur {token}. **Obligatoire**.
Content-Type    | application/json

## <a name="request-body"></a>Corps de la demande
Dans le corps de la demande, fournissez un objet JSON avec les paramètres suivants :

Paramètre | Type    | Description
:---|:---|:---
Requête | Texte |  Requête à exécuter. **Obligatoire**.

## <a name="response"></a>Réponse
Si elle réussit, cette méthode renvoie 200 OK et l’objet _QueryResponse_ dans le corps de la réponse. <br><br>

L’objet Response est divisé en trois parties (propriétés) :<br>
1) ```Stats``` -Statistiques de performances des requêtes.<br>
2) ```Schema``` -Le schéma de la réponse, une liste de paires nom-type pour chaque colonne. <br>
3) ```Results``` -Une liste d’événements de chasse avancés.

## <a name="example"></a>Exemple

Demande

Voici un exemple de demande.


```json
{
    "Query":"DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
}

```

Réponse

Voici un exemple de réponse.


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

## <a name="related-topic"></a>Voir aussi
- [Accéder aux API de protection contre les menaces Microsoft](api-access.md)
