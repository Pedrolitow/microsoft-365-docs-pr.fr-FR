---
title: Liste des appareils par logiciel
description: Récupérez la liste des appareils sur qui ce logiciel est installé.
keywords: api, api de graphique, api pris en charge, obtenir, lister les appareils, liste des appareils, liste des appareils par logiciel, Api tvm microsoft Defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: ff0bb9a6f17b8d4dc6432292ec98743d3eaf952c
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51929096"
---
# <a name="list-devices-by-software"></a>Liste des appareils par logiciel

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S'applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Récupérez la liste des références d'appareils sur les appareils sur qui ce logiciel est installé.

## <a name="permissions"></a>Autorisations
L'une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d'informations, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point](apis-intro.md) de terminaison pour plus d'informations.

Type d’autorisation |   Autorisation  |   Nom d'affichage de l'autorisation
:---|:---|:---
Application | Software.Read.All | « Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire) | Software.Read | « Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »

## <a name="http-request"></a>Requête HTTP
```
GET /api/Software/{Id}/machineReferences 
```

## <a name="request-headers"></a>En-têtes de demande

| Nom        | Type | Description
|:--------------|:-------|:--------------|
| Autorisation | String | Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande
Vide

## <a name="response"></a>Réponse
Si elle réussit, cette méthode renvoie 200 OK et une liste d'appareils avec le logiciel installé dans le corps. 


## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```
GET https://api.securitycenter.microsoft.com/api/Software/microsoft-_-edge/machineReferences
```

**Réponse**

Voici un exemple de réponse.

```json

{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "7c7e1896fa39efb0a32a2cf421d837af1b9bf762",
            "computerDnsName": "dave_desktop",
            "osPlatform": "Windows10",
            "rbacGroupName": "GroupTwo"
        },
        {
            "id": "7d5cc2e7c305e4a0a290392abf6707f9888fda0d",
            "computerDnsName": "jane_PC",
            "osPlatform": "Windows10",
            "rbacGroupName": "GroupTwo"
        }
        ...
    ]
}
```

## <a name="related-topics"></a>Voir aussi
- [Gestion des menaces & vulnérabilité basée sur les risques](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Inventaire des logiciels de vulnérabilité & menace](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/tvm-software-inventory)
