---
title: Obtenir l’API de collecte des groupes d’ordinateurs RBAC
description: Découvrez comment utiliser l’API de collecte Get KB pour récupérer une collection de groupes d’appareils RBAC dans Microsoft Defender pour point de terminaison.
keywords: api, api graphe, api prises en charge, get, RBAC, groupe
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
ms.date: 10/07/2018
ms.custom: api
ms.openlocfilehash: 528b80b3c40fd7df853190788abb347ed90a82e4
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825165"
---
# <a name="get-kb-collection-api"></a>Obtenir l’API de collection de bases de connaissances

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Récupère une collection de groupes d’appareils RBAC.

## <a name="permissions"></a>Autorisations

L’utilisateur a besoin d’autorisations de lecture.

## <a name="http-request"></a>Requête HTTP

```http
GET https://graph.microsoft.com/testwdatppreview/machinegroups
```

## <a name="request-headers"></a>En-têtes de demande

En-tête|Valeur
:---|:---
Autorisation | Porteur {token}. **Obligatoire**.
Type de contenu | application/json

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

En cas de réussite - 200 OK.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
GET https://graph.microsoft.com/testwdatppreview/machinegroups
Content-type: application/json
```

### <a name="response-example"></a>Exemple de réponse

Voici un exemple de réponse.
L’ID de champ contient **l’ID** de groupe d’appareils et est égal au **champ rbacGroupId** dans les informations sur les appareils.
Le champ **non groupé** n’est vrai que pour un seul groupe pour tous les appareils qui n’ont pas été affectés à un groupe. Comme d’habitude, ce groupe porte le nom « UnassignedGroup ».

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context":"https://graph.microsoft.com/testwdatppreview/$metadata#MachineGroups",
    "@odata.count":7,
    "value":[
        {
            "id":86,
            "name":"UnassignedGroup",
            "description":"",
            "ungrouped":true},
        ...
}
```
