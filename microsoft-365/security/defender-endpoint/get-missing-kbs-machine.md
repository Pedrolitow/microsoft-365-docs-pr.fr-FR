---
title: Obtenir les ko manquants par ID d’appareil
description: Récupère les mises à jour de sécurité manquantes par ID d’appareil
keywords: api, api de graphique, api pris en charge, obtenir, liste, fichier, informations, ID d’appareil, api & gestion des vulnérabilités menace, Api tvm microsoft Defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 30428565f082610c64c65da88fad614ef755e557fa56b0fc278cc62bf9d88c26
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53829314"
---
# <a name="get-missing-kbs-by-device-id"></a>Obtenir les ko manquants par ID d’appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Récupère les ko manquants (mises à jour de sécurité) par ID d’appareil

## <a name="http-request"></a>Requête HTTP

```http
GET /api/machines/{machineId}/getmissingkbs
```

## <a name="request-header"></a>En-tête de requête

Nom|Type|Description
:---|:---|:---
Autorisation | Chaîne | Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie 200 OK, avec les données kb du périphérique spécifié manquantes dans le corps.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
GET https://api.securitycenter.microsoft.com/api/machines/2339ad14a01bd0299afb93dfa2550136057bff96/getmissingkbs 
```

### <a name="response"></a>Réponse

Voici un exemple de réponse.


```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicProductFixDto)",
    "value": [
        {
            "id": "4540673",
            "name": "March 2020 Security Updates",
            "productsNames": [
                "windows_10",
                "edge",
                "internet_explorer"
            ],
            "url": "https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB4540673",
            "machineMissedOn": 1,
            "cveAddressed": 97
        },
         ...
        ]
}
```

## <a name="related-topics"></a>Sujets connexes

- [Gestion des menaces & vulnérabilité basée sur les risques](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Inventaire des logiciels de vulnérabilité & menace](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
