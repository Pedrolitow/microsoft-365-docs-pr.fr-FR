---
title: API d’indicateurs de liste
description: Découvrez comment utiliser l’API Indicateurs de liste pour récupérer une collection de tous les indicateurs actifs dans Microsoft Defender pour point de terminaison.
keywords: api, api publique, api pris en charge, collection d’indicateurs
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: a94c9e45fca9e7e5be2dde04d48267fb1c453999
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53624283"
---
# <a name="list-indicators-api"></a>API d’indicateurs de liste

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Extrait une collection de tous les indicateurs [actifs.](ti-indicator.md)

Prend [en charge les requêtes OData V4.](https://www.odata.org/documentation/)

La requête OData est prise en charge sur `$filter` : , , et les `indicatorValue` `indicatorType` `creationTimeDateTimeUtc` `createdBy` `action` `severity` propriétés.

Voir des exemples [dans les requêtes OData avec Microsoft Defender for Endpoint](exposed-apis-odata-samples.md)

## <a name="limitations"></a>Limites

1. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure. 

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez La mise [en place](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Ti.ReadWrite|« Lire et écrire des indicateurs »
Application|Ti.ReadWrite.All|« Lire et écrire tous les indicateurs »
Déléguée (compte professionnel ou scolaire)|Ti.ReadWrite|« Lire et écrire des indicateurs »

## <a name="http-request"></a>Requête HTTP

```http
GET https://api.securitycenter.microsoft.com/api/indicators
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie le code de réponse 200, Ok avec une collection [d’entités Indicator.](ti-indicator.md)

> [!NOTE]
> Si l’application dispose de l’autorisation « Ti.ReadWrite.All » , elle est exposée à tous les indicateurs. Sinon, il sera exposé uniquement aux indicateurs qu’il a créés.

## <a name="example-1"></a>Exemple 1

### <a name="example-1-request"></a>Exemple de requête 1

Voici un exemple de demande qui obtient tous les indicateurs

```http
GET https://api.securitycenter.microsoft.com/api/indicators
```

### <a name="example-1-response"></a>Réponse de l’exemple 1

Voici un exemple de réponse.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Indicators",
    "value": [
        {
            "id": "995",
            "indicatorValue": "12.13.14.15",
            "indicatorType": "IpAddress",
            "action": "Alert",
            "application": "demo-test",
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T11:15:35.3688259Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "test",
            "rbacGroupNames": []
        },
        {
            "id": "996",
            "indicatorValue": "220e7d15b0b3d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "action": "AlertAndBlock",
            "application": null,
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T10:54:23.2009016Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "TEST",
            "rbacGroupNames": [ "Group1", "Group2" ]
        }
        ...
    ]
}
```

## <a name="example-2"></a>Exemple 2

### <a name="example-2-request"></a>Exemple 2 de requête

Voici un exemple de demande qui obtient tous les indicateurs avec l’action « AlertAndBlock » 

```http
GET https://api.securitycenter.microsoft.com/api/indicators?$filter=action+eq+'AlertAndBlock'
```

### <a name="example-2-response"></a>Réponse de l’exemple 2

Voici un exemple de réponse.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Indicators",
    "value": [
        {
            "id": "997",
            "indicatorValue": "111e7d15b0b3d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "action": "AlertAndBlock",
            "application": null,
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T10:54:23.2009016Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "TEST",
            "rbacGroupNames": [ "Group1", "Group2" ]
        }
        ...
    ]
}
```
