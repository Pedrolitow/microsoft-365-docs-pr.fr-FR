---
title: API obtenir la collection de groupes d’ordinateurs RBAC
description: Découvrez comment utiliser l’API get KB collection pour récupérer une collection de groupes d’appareils RBAC dans Microsoft Defender pour Endpoint.
keywords: api, api de graphique, api pris en charge, obtenir, RBAC, groupe
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
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
ms.date: 10/07/2018
ms.openlocfilehash: 18566025d79f02281c1d2c1509dd98f1e57879c2
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51932774"
---
# <a name="get-kb-collection-api"></a>API Obtenir une collection de ko

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


Récupère une collection de groupes d’appareils RBAC.

## <a name="permissions"></a>Autorisations
L’utilisateur a besoin d’autorisations de lecture.

## <a name="http-request"></a>Requête HTTP
```
GET /testwdatppreview/machinegroups
```

## <a name="request-headers"></a>En-têtes de demande

En-tête | Valeur 
:---|:---
Autorisation | Porteur {token}. **Obligatoire**.
Type de contenu | application/json

## <a name="request-body"></a>Corps de la demande
Vide

## <a name="response"></a>Réponse
En cas de réussite : 200 - OK.

## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```
GET https://graph.microsoft.com/testwdatppreview/machinegroups
Content-type: application/json
```

**Réponse**

Voici un exemple de réponse.
L’ID de champ contient **l’ID** du groupe d’appareils et est égal au champ **rbacGroupId** dans les informations des appareils. Le **champ non regroupé** n’est vrai que pour un seul groupe pour tous les appareils qui n’ont été affectés à aucun groupe. Comme d’habitude, ce groupe a le nom « UnassignedGroup ».

```
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
        …
}
```
