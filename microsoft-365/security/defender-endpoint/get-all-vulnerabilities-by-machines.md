---
title: Obtenir toutes les vulnérabilités par ordinateur et par logiciel
description: Récupère une liste de toutes les vulnérabilités affectant l'organisation par l'ordinateur et les logiciels
keywords: api, api de graphique, api pris en charge, obtenir, informations de vulnérabilité, api tvm Microsoft Defender pour endpoint
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
ms.technology: mde
ms.openlocfilehash: 229c1f9e77a0cb85744155e82934b48dd63052b2
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51933408"
---
# <a name="list-vulnerabilities-by-machine-and-software"></a>Répertorier les vulnérabilités par ordinateur et logiciel

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


Récupère une liste de toutes les vulnérabilités affectant l'organisation par [ordinateur et](machine.md) [par logiciel.](software.md)
- Si la vulnérabilité a une ko de réparation, elle apparaît dans la réponse.
- Prend [en charge les requêtes OData V4.](https://www.odata.org/documentation/)
- OData est ```$filter``` pris en charge sur toutes les propriétés.

>[!Tip]
>Il s'agit d'une EXCELLENTE API pour [l'intégration de Power BI.](api-power-bi.md)

## <a name="permissions"></a>Autorisations
L'une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d'informations, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point](apis-intro.md) de terminaison pour plus d'informations.

Type d’autorisation |   Autorisation  |   Nom d'affichage de l'autorisation
:---|:---|:---
Application |   Vulnerability.Read.All |    « Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire) | Vulnerability.Read |   « Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités »

## <a name="http-request"></a>Requête HTTP
```
GET /api/vulnerabilities/machinesVulnerabilities
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
:---|:---|:---
Autorisation | String | Porteur {token}. **Obligatoire**.


## <a name="request-body"></a>Corps de la demande
Vide

## <a name="response"></a>Réponse
Si elle réussit, cette méthode renvoie 200 OK avec la liste des vulnérabilités dans le corps.


## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```http
GET https://api.securitycenter.microsoft.com/api/vulnerabilities/machinesVulnerabilities
```

**Réponse**

Voici un exemple de la réponse.


```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicAssetVulnerabilityDto)",
    "value": [
        {
            "id": "5afa3afc92a7c63d4b70129e0a6f33f63a427e21-_-CVE-2020-6494-_-microsoft-_-edge_chromium-based-_-81.0.416.77-_-",
            "cveId": "CVE-2020-6494",
            "machineId": "5afa3afc92a7c63d4b70129e0a6f33f63a427e21",
            "fixingKbId": null,
            "productName": "edge_chromium-based",
            "productVendor": "microsoft",
            "productVersion": "81.0.416.77",
            "severity": "Low"
        },
        {
            "id": "7a704e17d1c2977c0e7b665fb18ae6e1fe7f3283-_-CVE-2016-3348-_-microsoft-_-windows_server_2012_r2-_-6.3.9600.19728-_-3185911",
            "cveId": "CVE-2016-3348",
            "machineId": "7a704e17d1c2977c0e7b665fb18ae6e1fe7f3283",
            "fixingKbId": "3185911",
            "productName": "windows_server_2012_r2",
            "productVendor": "microsoft",
            "productVersion": "6.3.9600.19728",
            "severity": "Low"
        },
        ...
    ]

}
```

## <a name="see-also"></a>Voir aussi

- [Gestion des menaces et des vulnérabilités basée sur les risques](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Vulnérabilités dans votre organisation](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/tvm-weaknesses)
