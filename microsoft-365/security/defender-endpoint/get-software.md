---
title: List software
description: Récupère une liste d’inventaire logiciel
keywords: api, api de graphique, api pris en charge, obtenir, liste, fichier, informations, inventaire logiciel, api de gestion des menaces & vulnérabilité, api tvm mdatp
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
ms.openlocfilehash: 867fb57f61bd98b7c0afabd20b27e68d6bf45ef7
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51198564"
---
# <a name="list-software-inventory-api"></a>API d’inventaire de logiciels de liste

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Récupère l’inventaire logiciel de l’organisation.

## <a name="permissions"></a>Autorisations
L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point](apis-intro.md) de terminaison pour plus d’informations.

Type d’autorisation |   Autorisation  |   Nom d’affichage de l’autorisation
:---|:---|:---
Application |Software.Read.All |    « Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire) | Software.Read |    « Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »

## <a name="http-request"></a>Requête HTTP
```
GET /api/Software
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
:---|:---|:---
Autorisation | Chaîne | Porteur {token}. **Obligatoire**.


## <a name="request-body"></a>Corps de la demande
Vide

## <a name="response"></a>Réponse
Si elle réussit, cette méthode renvoie 200 OK avec l’inventaire logiciel dans le corps.


## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```
GET https://api.securitycenter.microsoft.com/api/Software
```

**Réponse**

Voici un exemple de réponse.


```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Software",
    "value": [
            {
                "id": "microsoft-_-edge",
                "name": "edge",
                "vendor": "microsoft",
                "weaknesses": 467,
                "publicExploit": true,
                "activeAlert": false,
                "exposedMachines": 172,
                "impactScore": 2.39947438
            }
            ...
        ]
}
```

## <a name="related-topics"></a>Voir aussi
- [Gestion des menaces & vulnérabilité basée sur les risques](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Inventaire des logiciels de vulnérabilité & menace](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/tvm-software-inventory)