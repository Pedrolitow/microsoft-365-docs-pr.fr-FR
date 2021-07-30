---
title: API Importer des indicateurs
description: Découvrez comment utiliser le lot d’importation de l’API d’indicateur dans Microsoft Defender pour le point de terminaison.
keywords: api, api pris en charge, envoyer, ti, indicateur, mettre à jour
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
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 8932b28c2e87431028ae608ea56b95f340485199
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53650546"
---
# <a name="import-indicators-api"></a>API Importer des indicateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Envoie ou met à jour le lot [d’entités](ti-indicator.md) d’indicateur.

La notation CIDR pour les IPs n’est pas prise en charge.

## <a name="limitations"></a>Limites

1. Les limites de taux pour cette API sont de 30 appels par minute.
2. Il existe une limite de 15 000 indicateurs [actifs](ti-indicator.md) par client.
3. La taille de lot maximale pour un appel d’API est de 500.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez La mise [en place](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Ti.ReadWrite|« Lire et écrire des indicateurs »
Application|Ti.ReadWrite.All|« Lire et écrire tous les indicateurs »
Déléguée (compte professionnel ou scolaire)|Ti.ReadWrite|« Lire et écrire des indicateurs »

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.
Content-Type|string|application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissons un objet JSON avec les paramètres suivants :

Parameter|Type|Description
:---|:---|:---
Indicateurs|List<[Indicator](ti-indicator.md)>|Liste des [indicateurs](ti-indicator.md). **Obligatoire**

## <a name="response"></a>Réponse

- Si elle réussit, cette méthode renvoie un code de réponse 200 - OK avec une liste de résultats d’importation par indicateur, voir l’exemple ci-dessous.
- Si elle ne réussit pas : cette méthode retourne 400 - Demande non bonne. Une demande incorrecte indique généralement un corps incorrect.

## <a name="example"></a>Exemple

### <a name="request-example"></a>Exemple de requête

Voici un exemple de demande.

```http
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

```json
{
    "Indicators":
    [
        {
            "indicatorValue": "220e7d15b011d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "title": "demo",
            "application": "demo-test",
            "expirationTime": "2021-12-12T00:00:00Z",
            "action": "Alert",
            "severity": "Informational",
            "description": "demo2",
            "recommendedActions": "nothing",
            "rbacGroupNames": ["group1", "group2"]
        },
        {
            "indicatorValue": "2233223322332233223322332233223322332233223322332233223322332222",
            "indicatorType": "FileSha256",
            "title": "demo2",
            "application": "demo-test2",
            "expirationTime": "2021-12-12T00:00:00Z",
            "action": "Alert",
            "severity": "Medium",
            "description": "demo2",
            "recommendedActions": "nothing",
            "rbacGroupNames": []
        }
    ]
}
```

### <a name="response-example"></a>Exemple de réponse

Voici un exemple de réponse.

```json
{
    "value": [
        {
            "id": "2841",
            "indicator": "220e7d15b011d7fac48f2bd61114db1022197f7f",
            "isFailed": false,
            "failureReason": null
        },
        {
            "id": "2842",
            "indicator": "2233223322332233223322332233223322332233223322332233223322332222",
            "isFailed": false,
            "failureReason": null
        }
    ]
}
```

## <a name="related-topic"></a>Rubrique connexe

- [Gérer des indicateurs](manage-indicators.md)
