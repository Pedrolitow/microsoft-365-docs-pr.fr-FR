---
title: Microsoft Defender Antivirus Device Health exporter les rapports d’intégrité de l’antivirus de l’appareil
description: Présente les méthodes permettant de récupérer Microsoft Defender détails de l’intégrité de l’appareil antivirus.
keywords: api, api graph, api prises en charge, get, api d’intégrité de l’appareil, api de rapport Microsoft Defender pour point de terminaison api de rapports microsoft defender, api de rapports microsoft defender pour point de terminaison, api de création de rapports windows defender, api defender pour rapports de point de terminaison, API de rapport Windows Defender
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
ms.date: 09/01/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 76e200022f01836195d82d46f159d35701f77a29
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68770324"
---
<!-- v-jweston/jweston-1 is scheduled to resume authorship Apr/May 2023.-->

# <a name="export-device-antivirus-health-report"></a>Exportation du rapport de santé antivirus de l'appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Cette API dispose de deux méthodes pour récupérer Microsoft Defender détails de l’intégrité de l’antivirus des appareils antivirus :

- **Méthode 1 :** [1 Exporter la **réponse**\) JSON des rapports \( d’intégrité](#1-export-health-reporting-json-response) La méthode extrait toutes les données de votre organisation sous forme de réponses JSON. Cette méthode est idéale pour _les petites organisations avec moins de 100 000 appareils_. La réponse étant paginée, vous pouvez utiliser le \@champ odata.nextLink de la réponse pour extraire les résultats suivants.

- **Méthode 2 :** [2 Exporter les rapports \( d’intégrité **via des fichiers**\)](#2-export-health-reporting-via-files) Cette méthode permet d’extraire de plus grandes quantités de données plus rapidement et de manière plus fiable. Il est donc recommandé pour les grandes organisations, avec plus de 100 000 appareils. Cette API extrait toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir du stockage Azure. Cette API vous permet de télécharger toutes vos données à partir du Stockage Azure comme suit :
  - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.
  - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traitez les données comme vous le souhaitez.

Les données collectées à l’aide de « _réponse JSON_ ou _via des fichiers_ » sont l’instantané actuel de l’état actuel. Il ne contient pas de données historiques. Pour collecter des données historiques, les clients doivent enregistrer les données dans leurs propres stockages de données. Consultez [Exporter les méthodes et propriétés de l’API détails de l’intégrité de l’appareil](device-health-api-methods-properties.md).

> [!IMPORTANT]
>
> Actuellement, seule la **réponse JSON d’intégrité de l’antivirus** est en disponibilité générale. **L’API d’intégrité antivirus via des fichiers** n’est actuellement disponible qu’en préversion publique.
>
> **La requête personnalisée de chasse avancée** n’est actuellement disponible qu’en préversion publique, même si les requêtes sont toujours visibles.

> [!IMPORTANT]
>
> Pour que Windows&nbsp;Server&nbsp;2012&nbsp;R2 et Windows&nbsp;Server&nbsp;2016 apparaissent dans les rapports d’intégrité des appareils, ces appareils doivent être intégrés à l’aide du package de solution unifiée moderne. Pour plus d’informations, consultez [Nouvelles fonctionnalités de la solution unifiée moderne pour Windows Server 2012 R2 et 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution).

> [!NOTE]
>
> Pour plus d’informations sur l’utilisation de l’outil de création de rapports sur **l’intégrité de l’appareil et la conformité antivirus** dans le tableau de bord sécurité Microsoft 365, consultez : Rapport sur l’intégrité [de l’appareil et la conformité antivirus dans Microsoft Defender pour point de terminaison](machine-reports.md).
>

## <a name="1-export-health-reporting-json-response"></a>1 Exporter les rapports d’intégrité (réponse JSON)

### <a name="11-api-method-description"></a>1.1 Description de la méthode d’API

Cette API récupère une liste des détails d’intégrité de l’antivirus des appareils antivirus Microsoft Defender. Retourne une table avec une entrée pour chaque combinaison unique de :

- DeviceId
- Nom du périphérique
- Mode AV
- État à jour
- Résultats de l’analyse

#### <a name="111-limitations"></a>1.1.1 Limitations

- la taille maximale de la page est de 200 000
- Les limitations de débit pour cette API sont (**_par exemple_** , 30 appels par minute et 1 000 appels par hour._)

#### <a name="odata-supported-operators"></a>Opérateurs pris en charge par OData

- `$filter`on : `machineId`, `computerDnsName`, `osKind`, `osPlatform`, `osVersion`, `avMode`, , `avEngineVersion``avSignatureVersion``avPlatformVersion``quickScanResult``quickScanError``fullScanResult``fullScanError``avIsSignatureUpToDate``avIsEngineUpToDate``avIsPlatformUpToDate``rbacGroupId`
- `$top` avec la valeur maximale de 10 000.
- `$skip`

### <a name="12-permissions"></a>1.2 Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez Utiliser les API Microsoft Defender pour point de terminaison pour plus d’informations.

| Type d’autorisation | Autorisation | Nom complet de l’autorisation |
|:---|:---|:---|
| Application | Machine.Read.All | « Lire tous les profils de machine » |
|Déléguée (compte professionnel ou scolaire) | Machine.Read | « Lire les informations de l’ordinateur » |

### <a name="13-url-http-request"></a>1.3 URL (requête HTTP)

```http
URL: GET: /api/deviceavinfo
```

#### <a name="131-request-headers"></a>1.3.1 En-têtes de requête

| Nom | Type | Description |
|:---|:---|:---|
| Autorisation | Chaîne | Porteur {token}. Obligatoire. |

#### <a name="132-request-body"></a>1.3.2 Corps de la demande

Vide

#### <a name="133-response"></a>1.3.3 Réponse

Si elle réussit, cette méthode retourne 200 OK avec une liste de détails d’intégrité de l’appareil.

### <a name="14-parameters"></a>1.4 Paramètres

- La taille de page par défaut est 20
- Consultez des exemples dans [requêtes OData avec Microsoft Defender pour point de terminaison](exposed-apis-odata-samples.md).

### <a name="15-properties"></a>1.5 Propriétés

Consultez : [1.2 Exporter les détails de l’intégrité de l’antivirus des appareils propriétés de l’API (réponse JSON)](device-health-api-methods-properties.md#12-export-device-antivirus-health-details-api-properties-json-response)

Prend en charge [les requêtes OData V4](https://www.odata.org/documentation/).

### <a name="16-example"></a>1.6 Exemple

#### <a name="request-example"></a>Exemple de requête

Voici un exemple de demande :

```http
GET https://api.securitycenter.microsoft.com/api/deviceavinfo
```

#### <a name="response-example"></a>Exemple de réponse

Voici un exemple de réponse :

```json
{

    @odata.context: "https://api.securitycenter.microsoft.com/api/$metadata#DeviceAvInfo",

"value": [{

            "id": "Sample Guid",

            "machineId": "Sample Machine Guid",

            "computerDnsName": "appblockstg1",

            "osKind": "windows",

            "osPlatform": "Windows10",

            "osVersion": "10.0.19044.1865",

            "avMode": "0",

            "avSignatureVersion": "1.371.1279.0",

            "avEngineVersion": "1.1.19428.0",

            "avPlatformVersion": "4.18.2206.108",

            "lastSeenTime": "2022-08-02T19:40:45Z",

            "quickScanResult": "Completed",

            "quickScanError": "",

            "quickScanTime": "2022-08-02T18:40:15.882Z",

            "fullScanResult": "",

            "fullScanError": "",

            "fullScanTime": null,

            "dataRefreshTimestamp": "2022-08-02T21:16:23Z",

            "avEngineUpdateTime": "2022-08-02T00:03:39Z",

            "avSignatureUpdateTime": "2022-08-02T00:03:39Z",

            "avPlatformUpdateTime": "2022-06-20T16:59:35Z",

            "avIsSignatureUpToDate": "True",

            "avIsEngineUpToDate": "True",

            "avIsPlatformUpToDate": "True",

            "avSignaturePublishTime": "2022-08-02T00:03:39Z",

            "rbacGroupName": "TVM1",

            "rbacGroupId": 4415

        },

        ...

     ]

}
```

## <a name="2-export-health-reporting-via-files"></a>2 Exporter les rapports d’intégrité (via des fichiers)

> [!IMPORTANT]
> Les informations contenues dans cette section concernent les produits pré-publiés qui peuvent être modifiés de manière substantielle avant sa commercialisation. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

### <a name="21-api-method-description"></a>2.1 Description de la méthode d’API

Cette réponse d’API contient toutes les données d’intégrité et d’état de l’antivirus par appareil. Retourne une table avec une entrée pour chaque combinaison unique de :

- DeviceId
- nom du périphérique
- Mode AV
- État à jour
- Résultats de l’analyse

#### <a name="212-limitations"></a>2.1.2 Limitations

- La taille maximale de la page est de 200 000.
- Les limitations de débit pour cette API sont de 30 appels par minute et de 1 000 appels par heure.

### <a name="22-permissions"></a>2.2 Autorisations

L’une des autorisations suivantes est requise pour appeler cette API.

| Type d’autorisation | Autorisation | Nom complet de l’autorisation |
|:---|:---|:---|
| Application | Vulnerability.Read.All | « Lire les informations de vulnérabilité « Gestion des menaces et des vulnérabilités » |
| Déléguée (compte professionnel ou scolaire) | Vulnerability.Read | « Lire les informations de vulnérabilité « Gestion des menaces et des vulnérabilités » |

Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser les API Microsoft Defender pour point de terminaison pour plus d’informations](apis-intro.md).

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/InfoGatheringExport
```

### <a name="24-parameters"></a>2.4 Paramètres

- `sasValidHours`: nombre d’heures pendant lesquelles les URL de téléchargement seront valides (maximum 24 heures).

### <a name="25-properties"></a>2.5 Propriétés

Consultez : [1.3 Exporter les propriétés \(de l’API détails de l’intégrité de l’antivirus de l’appareil via des fichiers\)](device-health-api-methods-properties.md#13-export-device-antivirus-health-details-api-properties-via-files).

### <a name="26-examples"></a>2.6 Exemples

#### <a name="261-request-example"></a>2.6.1 Exemple de demande

Voici un exemple de demande :

```HTTP
GET https://api-us.securitycenter.contoso.com/api/machines/InfoGatheringExport
```

#### <a name="262-response-example"></a>2.6.2 Exemple de réponse

Voici un exemple de réponse :

```json
{

   "@odata.context": "https://api-us.securitycenter.windows.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",

   "exportFiles": [

       "https://tvmexportexternalprdeus.blob.core.windows.net/temp-../2022-08-02/2201/InfoGatheringExport/json/OrgId=../_RbacGroupId=../part-00055-12fc2fcd-8f56-4e09-934f-e8efe7ce74a0.c000.json.gz?sv=2020-08-04&st=2022-08-02T22%3A47%3A11Z&se=2022-08-03T01%3A47%3A11Z&sr=b&sp=r&sig=..",

       "https://tvmexportexternalprdeus.blob.core.windows.net/temp-../2022-08-02/2201/InfoGatheringExport/json/OrgId=../_RbacGroupId=../part-00055-12fc2fcd-8f56-4e09-934f-e8efe7ce74a0.c000.json.gz?sv=2020-08-04&st=2022-08-02T22%3A47%3A11Z&se=2022-08-03T01%3A47%3A11Z&sr=b&sp=r&sig=.."

   ],


   "generatedTime": "2022-08-02T22:01:00Z"


}
```

## <a name="see-also"></a>Voir aussi

[Méthodes et propriétés de l'état de santé de l'appareil d'exportation](device-health-api-methods-properties.md)

[Rapports sur l’intégrité et la conformité des appareils](device-health-reports.md)
