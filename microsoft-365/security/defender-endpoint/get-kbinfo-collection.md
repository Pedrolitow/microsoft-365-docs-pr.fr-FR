---
title: API Obtenir une collection de ko
description: Récupérez une collection de bases de connaissances (Ko) et de détails de la Base de connaissances avec Microsoft Defender pour point de terminaison.
keywords: api, api de graphique, api pris en charge, obtenir, kb
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: leonidzh
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ROBOTS: NOINDEX
ms.technology: mde
ms.openlocfilehash: 22faf080245598957a90122a3ea6b4c5cf3faca4
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53622099"
---
# <a name="get-kb-collection-api"></a>API Obtenir une collection de ko

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Extrait une collection de détails de la Ko et de la Ko.

## <a name="permissions"></a>Autorisations

L’utilisateur a besoin d’autorisations de lecture.

## <a name="http-request"></a>Requête HTTP

```http
GET /testwdatppreview/kbinfo
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

Voici un exemple de demande.

```http
GET https://graph.microsoft.com/testwdatppreview/KbInfo
```

### <a name="response-example"></a>Exemple de réponse

Voici un exemple de réponse.

```json
{
    "@odata.context": "https://graph.microsoft.com/testwdatppreview/$metadata#KbInfo",
    "@odata.count": 271,
    "value":[
        {
            "id": "KB3097617 (10240.16549) Amd64",
            "release": "KB3097617 (10240.16549)",
            "publishingDate": "2015-10-16T21:00:00Z",
            "version": "10.0.10240.16549",
            "architecture": "Amd64"
        },
        ...
}
```
