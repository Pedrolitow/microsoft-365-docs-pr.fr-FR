---
title: Obtenir les bases de connaissances manquantes par ID d’appareil
description: Récupère les mises à jour de sécurité manquantes par ID d’appareil
keywords: api, api graphe, api prises en charge, get, list, file, information, device id, threat & vulnerability management api, Microsoft Defender pour point de terminaison tvm api
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 2d8200d93b3cab7acff237113a2c98d8571be1a7
ms.sourcegitcommit: 6e570b79944862c86735db455349b685d5b903b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2022
ms.locfileid: "67020118"
---
# <a name="get-missing-kbs-by-device-id"></a>Obtenir les bases de connaissances manquantes par ID d’appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des vulnérabilités Microsoft Defender](../defender-vulnerability-management/index.yml)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> Vous voulez découvrir Gestion des vulnérabilités Microsoft Defender ? En savoir plus sur la façon dont vous pouvez vous inscrire à la [Gestion des vulnérabilités Microsoft Defender préversion publique](../defender-vulnerability-management/get-defender-vulnerability-management.md).

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Récupère les bases de connaissances manquantes (mises à jour de sécurité) par ID d’appareil

## <a name="http-request"></a>Requête HTTP

```http
GET /api/machines/{machineId}/getmissingkbs
```
## <a name="permissions"></a>Autorisations

L’autorisation suivante est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md).

Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation
:---|:---|:---
Application | Software.Read.All | « Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »

## <a name="request-header"></a>En-tête de requête

Nom|Type|Description
:---|:---|:---
Autorisation | Chaîne | Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

Si elle réussit, cette méthode retourne 200 OK, avec les données kb de l’appareil spécifiées dans le corps.

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
        }
        ]
}
```

## <a name="related-topics"></a>Voir aussi

- [Gestion des vulnérabilités & des menaces basée sur les risques](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Inventaire logiciel threat & Vulnerability](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
