---
title: API de détails sur l’intégrité des appareils antivirus Microsoft Defender
description: Récupère une liste des détails d’intégrité des appareils antivirus Microsoft Defender.
keywords: api, api graphe, api prises en charge, get, api d’intégrité de l’appareil, Microsoft Defender pour point de terminaison api de rapport api rapports microsoft defender, api de création de rapports microsoft defender pour point de terminaison, api de création de rapports Windows Defender, api de création de rapports Defender pour point de terminaison, API de rapport Windows Defender
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
ms.date: 08/08/2022
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.custom: api
ms.openlocfilehash: 6907852501ac78784a3a642851c62cfeb2a065ac
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67520360"
---
# <a name="microsoft-defender-antivirus-device-health-details-api"></a>API de détails sur l’intégrité des appareils antivirus Microsoft Defender

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="api-description"></a>Description de l’API

Récupère une liste des détails d’intégrité des appareils antivirus Microsoft Defender.
URL : GET : /api/public/avdeviceshealth
<br>Prend [en charge les requêtes OData V4](https://www.odata.org/documentation/).
<br>Opérateurs OData pris en charge :
<br>```$filter```on: ```machineId```, ```computerDnsName```, ```osKind```, ```osPlatform```, ```osVersion```a```vMode```, ```avSignatureVersion```, ```avEngineVersion```, ```avPlatformVersion```, ```quickScanResult```, , ```quickScanError``````fullScanResult```, , ```fullScanError```, ```avIsSignatureUpToDate```, ```avIsEngineUpToDate``````vIsPlatformUpToDate``````rbacGroupId```
<br>```$top``` avec une valeur maximale de 10 000.
<br>```$skip```.
<br>Consultez des exemples dans [Requêtes OData avec Microsoft Defender pour point de terminaison.] (exposed-apis-odata-samples.md]

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md) pour plus d’informations.

| Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation |
|:----|:----|:----|
| Application | Machine.Read.All | 'Lire tous les profils d’ordinateur' |
| Application | Machine.ReadWrite.All | « Lire et écrire toutes les informations sur l’ordinateur » |
| Déléguée (compte professionnel ou scolaire) | Machine.Read | « Lire les informations de l’ordinateur » |
| Déléguée (compte professionnel ou scolaire) | Macine.ReadWrite | « Lire et écrire des informations sur la machine » |

## <a name="http-request"></a>Requête HTTP

```http
GET /api/public/avdeviceshealth
```

## <a name="request-headers"></a>En-têtes de demande

| Nom | Type | Description |
|:----|:----|:----|
| Autorisation | Chaîne | Porteur {token}. **Obligatoire** |

## <a name="request-body"></a>Corps de la demande

_Empty_

## <a name="response"></a>Réponse

Si elle réussit, cette méthode retourne 200 OK avec une liste des détails d’intégrité de l’appareil.

## <a name="example"></a>Exemple

### <a name="example-request"></a>Exemple de requête

Voici un exemple de la requête :

```http
GET https://api.securitycenter.microsoft.com/api/public/avdeviceshealth 
```

### <a name="example-response"></a>Exemple de réponse

Voici un exemple de réponse :

```json
{ 

    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#avdeviceshealth", 

    "value": [ 

        { 

           "id": "sampleId", 

           "machineId": "sampleMachineId", 

           "computerDnsName": "sampleDnsName", 

           "osKind": "mac", 

           "osPlatform": "macOS", 

           "osVersion": "11.6.5.0", 

           "avMode": "0", 

           "avSignatureVersion": "87523", 

           "avEngineVersion": "3.0", 

           "avPlatformVersion": "101.61.69", 

           "lastSeenTime": "2022-04-02T06:12:07+00:00", 

           "quickScanResult": "-", 

           "quickScanError": "-", 

           "fullScanResult": "-", 

           "fullScanError": "-", 

           "dataRefreshTimestamp": "2022-04-06T21:50:48+00:00", 

           "avSignatureUpdateTime": "2022-04-01T01:31:58+00:00", 

           "avIsSignatureUpToDate": "Unknown", 

           "avIsEngineUpToDate": "Unknown", 

           "avIsPlatformUpToDate": "Unknown", 

           "rbacGroupId": 86 

        }, 

        ... 

     ] 

}  
```

## <a name="see-also"></a>Voir aussi

[Rapport d’intégrité et de conformité des appareils dans Microsoft Defender pour point de terminaison](machine-reports.md)
