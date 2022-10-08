---
title: Répertorier les fichiers d’une bibliothèque
description: Découvrez comment répertorier les fichiers de la bibliothèque de réponses en direct.
keywords: api, api graphe, api prises en charge, get, appareils
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
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
ms.collection:
- m365-security
- tier3
ms.topic: reference
ms.subservice: mde
ms.custom: api
ms.openlocfilehash: 5699f13fba91d02a8a5e00656487b12d882d07d8
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68226864"
---
#  <a name="list-library-files"></a>Répertorier les fichiers d’une bibliothèque 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Répertorier les fichiers de la bibliothèque de réponses actives.

## <a name="limitations"></a>Limites

1.  Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Prise en main](apis-intro.md).

|Type d’autorisation                       |      Autorisation          |  Nom d’affichage de l’autorisation | 
|-----------------|--------|---------------------------|  
| Application                        | Library.Manage | Gérer la bibliothèque de réponses en direct |
| Déléguée (compte professionnel ou scolaire) | Library.Manage | Gérer la bibliothèque de réponses en direct |

## <a name="http-request"></a>Requête HTTP

```HTTP
GET https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="request-headers"></a>En-têtes de demande

| Nom         |      Type                     | Description
|-----------------|--------|---------------------------|
| Autorisation   | Chaîne | Bearer {token}. Required. |

## <a name="request-body"></a>Corps de la demande
Vide

## <a name="response"></a>Réponse 
Si elle réussit, cette méthode renvoie le code de réponse 200 - OK avec une collection d’entités de fichier de bibliothèque de réponses actives.

## <a name="example"></a>Exemple

**Demande**

Voici un exemple de requête qui obtient tous les fichiers de bibliothèque de réponses en direct

```HTTP
GET https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="response-example"></a>Exemple de réponse

Voici un exemple de réponse.

```JSON
HTTP/1.1 200 Ok
Content-type: application/json
{
"\@odata.context": "https://api.securitycenter.microsoft.com
/api/\$metadata\#LibraryFiles",
"value": [
    {
    "fileName": "script1.ps1",
    "sha256": "6e212a0db618507c44e4ec8ee7499dfef7e5767e5f8d31144df3b96fd1145caf",
    "description": null,
    "creationTime": "2019-10-24T10:54:23.2009016Z",
    "lastUpdatedTime": "2019-10-24T10:54:23.2009016Z",
    "createdBy": "admin",
    "hasParameters": true,
    "parametersDescription": "test"
    },
    {
    "fileName": "script.sh",
    "sha256": "d0f3e3b0641dbf88ee39c822516e81a909d1d06d22341dd9b1f12aa5e5c027a2",
    "description": null,
    "creationTime": "2018-10-24T11:15:35.3688259Z",
    "lastUpdatedTime": "2018-10-24T11:15:35.3688259Z",
    "createdBy": "username",
    "hasParameters": false
    },
    {
    "fileName": "memdump.exe",
    "sha256": "fa70b87730290c0d30fe255d1dfb65de82f96286ebfeeb1d88ed3cc831329825",
    "description": "Process memory dump",
    "creationTime": "2018-10-24T10:54:23.2009016Z",
    "lastUpdatedTime": "2018-10-24T10:54:23.2009016Z",
    "createdBy": "admin",
    "hasParameters": false
    }
]
}
```


## <a name="related-topic"></a>Rubrique connexe
- [Exécuter la réponse en direct](run-live-response.md) 