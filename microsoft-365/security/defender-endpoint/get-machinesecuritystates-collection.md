---
title: API obtenir la collection d’états de sécurité des ordinateurs
description: Récupérez une collection d’états de sécurité d’appareil à l’aide de Microsoft Defender for Endpoint.
keywords: api, api de graphique, api pris en charge, obtenir, appareil, sécurité, état
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: leonidzh
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.custom: api
ms.openlocfilehash: af3881a5215871b0405f2f6b42b73c248af0c00c
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60586872"
---
# <a name="get-machines-security-states-collection-api"></a>API obtenir la collection d’états de sécurité des ordinateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Récupère une collection d’états de sécurité des appareils.

## <a name="permissions"></a>Autorisations

L’utilisateur a besoin d’autorisations de lecture.

## <a name="http-request"></a>Requête HTTP

```http
GET /testwdatppreview/machinesecuritystates
```

## <a name="request-headers"></a>En-têtes de demande

En-tête|Valeur
:---|:---
Autorisation|Porteur {token}. **Obligatoire**.
Type de contenu|application/json

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

En cas de réussite : 200 - OK.

## <a name="example"></a>Exemple

### <a name="request-example"></a>Exemple de requête

Voici un exemple de la demande.

```http
GET https://graph.microsoft.com/testwdatppreview/machinesecuritystates
Content-type: application/json
```

### <a name="response-example"></a>Exemple de réponse

Voici un exemple de réponse.

*L’ID de* champ contient l’ID de l’appareil et est égal à l’ID *de* champ * dans les informations sur les appareils.

```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context":"https://graph.microsoft.com/testwdatppreview/$metadata#MachineSecurityStates",
    "@odata.count":444,
    "@odata.nextLink":"https://graph.microsoft.com/testwdatppreview/machinesecuritystates?$skiptoken=[continuation token]",
    "value":[
        {
            "id":"000050e1b4afeee3742489ede9ad7a3e16bbd9c4",
            "build":14393,
            "revision":2485,
            "architecture":"Amd64",
            "osVersion":"10.0.14393.2485.amd64fre.rs1_release.180827-1809",
            "propertiesRequireAttention":[
                "AntivirusNotReporting",
                "EdrImpairedCommunications"
            ]
        },
        ...
    ]
}
```
