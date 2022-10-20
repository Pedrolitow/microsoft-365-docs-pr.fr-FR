---
title: Exporter l’évaluation de l’inventaire logiciel du code non produit par appareil
description: Retourne une table avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion pour les logiciels qui n’ont pas d’énumération de plateforme commune (CPE)
keywords: api, api, évaluation d’exportation, évaluation par appareil, rapport d’évaluation des vulnérabilités, évaluation des vulnérabilités des appareils, rapport de vulnérabilité des appareils, évaluation de la configuration sécurisée, rapport de configuration sécurisé, évaluation des vulnérabilités logicielles, rapport de vulnérabilité logicielle, rapport de vulnérabilité par ordinateur,
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 869342240c81c1a337b5241a0b5e2e8308f843b5
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68629718"
---
# <a name="export-non-product-code-software-inventory-assessment-per-device"></a>Exporter l’évaluation de l’inventaire logiciel du code non produit par appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des vulnérabilités de Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette API retourne toutes les données pour les logiciels installés qui n’ont pas [d’énumération de plateforme commune (CPE)](https://nvd.nist.gov/products/cpe) sur une base par appareil. Les informations retournées par cette API, ainsi que les informations retournées par l’API [d’évaluation de l’inventaire logiciel d’exportation](get-assessment-non-cpe-software-inventory.md) , pour les logiciels qui ont un CPE, vous donnent une visibilité complète sur les logiciels installés dans votre organisation et les appareils sur lesquels elle est installée.

> [!NOTE]
> Les logiciels sans CPE ne sont pas pris en charge par la gestion des vulnérabilités. Ils seront affichés dans la page d’inventaire logiciel, mais étant donné que les CPG sont utilisés par la gestion des vulnérabilités pour identifier les logiciels et les vulnérabilités, les informations telles que les exploits, le nombre d’appareils exposés et les faiblesses ne seront pas disponibles pour eux. Pour plus d’informations, consultez [l’inventaire logiciel](../defender-vulnerability-management/tvm-software-inventory.md).

Les différents appels d’API obtiennent différents types de données. Étant donné que la quantité de données peut être importante, il existe deux façons de les récupérer :

- [Exporter une **réponse JSON** d’évaluation de l’inventaire logiciel de code non produit](#1-export-non-product-code-software-inventory-assessment-json-response) L’API extrait toutes les données de votre organisation en tant que réponses Json. Cette méthode est idéale pour _les petites organisations avec moins de 100 K d’appareils_. La réponse étant paginée, vous pouvez utiliser le \@champ odata.nextLink de la réponse pour extraire les résultats suivants.

- [Exporter l’évaluation de l’inventaire logiciel de code non produit **via des fichiers**](#2-export-non-product-code-software-inventory-assessment-via-files)  Cette solution d’API permet d’extraire de plus grandes quantités de données plus rapidement et de manière plus fiable. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 000 appareils. Cette API extrait toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir du stockage Azure. Cette API vous permet de télécharger toutes vos données à partir du Stockage Azure comme suit :
  - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.
  - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traitez les données comme vous le souhaitez.

Les données collectées (à l’aide d’une _réponse Json_ ou _de fichiers_) sont l’instantané actuel de l’état actuel. Il ne contient pas de données historiques. Pour collecter des données historiques, les clients doivent enregistrer les données dans leurs propres stockages de données.

> [!NOTE]
> Sauf indication contraire, toutes les méthodes d’évaluation d’exportation répertoriées sont **_l’exportation complète_** et **_par appareil_** (également appelée **_par appareil_**).

## <a name="1-export-non-product-code-software-inventory-assessment-json-response"></a>1. Exporter l’évaluation de l’inventaire logiciel de code non produit (réponse JSON)

### <a name="11-api-method-description"></a>Description de la méthode d’API 1.1

Cette réponse d’API contient toutes les données des logiciels installés qui n’ont pas [d’énumération de plateforme commune (CPE)](https://nvd.nist.gov/products/cpe) par appareil. Retourne une table avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.

#### <a name="limitations"></a>Limites

- La taille maximale de la page est de 200 000.
- Les limites de débit pour cette API sont de 30 appels par minute et de 1 000 appels par heure.

### <a name="12-permissions"></a>1.2 Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
---|---|---
Application|Software.Read.All|\'Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités\'
Déléguée (compte professionnel ou scolaire)|Software.Read|\'Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités\'

### <a name="13-url"></a>URL 1.3

```http
GET /api/machines/SoftwareInventoryNoProductCodeByMachine
```

### <a name="14-parameters"></a>1.4 Paramètres

- pageSize (valeur par défaut = 50 000) : nombre de résultats en réponse.
- $top : nombre de résultats à retourner (ne retourne pas @odata.nextLink et n’extrait donc pas toutes les données)

### <a name="15-properties"></a>1.5 Propriétés

> [!NOTE]
>
> - Chaque enregistrement est d’environ 0,5 Ko de données. Vous devez en tenir compte lors du choix du paramètre pageSize approprié pour vous.
> - Les propriétés définies dans le tableau suivant sont répertoriées par ordre alphabétique, par ID de propriété. Lors de l’exécution de cette API, la sortie résultante ne sera pas nécessairement retournée dans le même ordre que celui répertorié dans ce tableau.
> - Certaines colonnes supplémentaires peuvent être retournées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.

<br>

Propriété (ID)|Type de données|Description
:---|:---|:---
DeviceId|string|Identificateur unique de l’appareil dans le service.
DeviceName|chaîne|Nom de domaine complet (FQDN) de l’appareil.
OSPlatform|string|Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Il s’agit de systèmes d’exploitation spécifiques avec des variantes au sein de la même famille, telles que Windows 10 et Windows 11. Pour plus [d’informations, consultez systèmes d’exploitation, plateformes et fonctionnalités pris en charge](../defender-vulnerability-management/tvm-supported-os.md) .
RbacGroupName|string|Groupe de contrôle d’accès en fonction du rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur est « Non affecté ». Si l’organisation ne contient aucun groupe RBAC, la valeur est « None ».
RbacGroupId|string|ID de groupe de contrôle d’accès en fonction du rôle (RBAC).
SoftwareLastSeenTimestamp|chaîne|La dernière fois que ce logiciel a été vu sur l’appareil.
SoftwareName|chaîne|Nom du produit logiciel.
SoftwareVendor|string|Nom du fournisseur de logiciels.
SoftwareVersion|chaîne|Numéro de version du produit logiciel.

### <a name="16-examples"></a>1.6 Exemples

#### <a name="161-request-example"></a>Exemple de demande 1.6.1

```http
https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryNoProductCodeByMachine?pageSize=3  &sinceTime=2021-05-19
```

#### <a name="162-response-example"></a>1.6.2 Exemple de réponse

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetNonCpeSoftware)",
    "value": [
        {
           "deviceId": "1234512345123451234512345",
            "rbacGroupId": 11,
            "rbacGroupName": "London",
            "deviceName": "Device1",
            "osPlatform": "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "vs_communitymsi",
            "softwareVersion": "11.11.31111.1",
            "softwareLastSeenTimestamp": "2021-01-30 11:31:12.271"
        },
        {
            "deviceId": "232323232323232322323232323",
            "rbacGroupId": 23,
            "rbacGroupName": "Tokyo",
            "deviceName": "Device23",
            "osPlatform": "Windows10",
            "softwareVendor": "intel",
            "softwareName": "intel®_software_installer",
            "softwareVersion": "22.20.2.2",
            "softwareLastSeenTimestamp": "2022-05-30 15:35:12.271"
        },
        {
            "deviceId": "6565656565",
            "rbacGroupId": 65,
            "rbacGroupName": "Center",
            "deviceName": "Device56",
            "osPlatform": "Windows10",
            "softwareVendor": "Lob Apps",
            "softwareName": "Headtrax",
            "softwareVersion": "60.273.3",
            "softwareLastSeenTimestamp": "2022-05-05 15:35:12.271"
        },
    ],
        "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryNoProductCodeByMachine?pagesize=3%20%20&sincetime=2021-05-19&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMi0wNS0zMC8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}

```

## <a name="2-export-non-product-code-software-inventory-assessment-via-files"></a>2. Exporter l’évaluation de l’inventaire logiciel de code non produit (via des fichiers)

### <a name="21-api-method-description"></a>Description de la méthode API 2.1

Cette réponse d’API contient toutes les données des logiciels installés qui n’ont pas [d’énumération de plateforme commune (CPE)](https://nvd.nist.gov/products/cpe) par appareil. Retourne une table avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.

#### <a name="211-limitations"></a>2.1.1 Limitations

Les limites de débit pour cette API sont de 5 appels par minute et de 20 appels par heure.

### <a name="22-permissions"></a>2.2 Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
---|---|---
Application|Software.Read.All|\'Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités\'
Déléguée (compte professionnel ou scolaire)|Software.Read|\'Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités\'

### <a name="23-url"></a>URL 2.3

```http
GET /api/machines/Api/Machines/SoftwareInventoryNonCpeExport
```

### <a name="parameters"></a>Parameters

- sasValidHours : nombre d’heures pendant lesquelles les URL de téléchargement sont valides (maximum 24 heures)

### <a name="25-properties"></a>2.5 Propriétés

> [!NOTE]
>
> - Les fichiers sont compressés par gzip & au format JSON multiligne.
> - Les URL de téléchargement ne sont valides que pendant 3 heures. Sinon, vous pouvez utiliser le paramètre.
> - Pour une vitesse de téléchargement maximale de vos données, vous pouvez vous assurer que vous téléchargez à partir de la même région Azure que celle où résident vos données.

<br>

****

Propriété (ID)|Type de données|Description|Exemple de valeur retournée
:---|:---|:---|:---
Exporter des fichiers|chaîne de tableau\[\]|Liste des URL de téléchargement pour les fichiers contenant l’instantané actuel de l’organisation|"[Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|string|Heure à laquelle l’exportation a été générée.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Exemples

#### <a name="261-request-example"></a>2.6.1 Exemple de requête

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryNonCpeExport
```

#### <a name="262-response-example"></a>2.6.2 Exemple de réponse

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportexternalprdcanc.blob.core.windows.net/temp-ffd80447-7b3d-4ad2-b366-f0979b129662/2022-05-30/1101/NonCpeSoftwareInventory/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=1/part-00337-5e15412b-5c85-4896-ac60-b7b3ab8da096.c000.json.gz?sv=2020-08-04&st=2022-05-30T13%3A41%3A59Z&se=2022-05-30T16%3A41%3A59Z&sr=b&sp=r&sig=aHnmuOKlIvpR0PsdamYfmCCDZ1nhpuXBzK2%2FkJ9xTpg%3D",
        "https://tvmexportexternalprdcanc.blob.core.windows.net/temp-ffd80447-7b3d-4ad2-b366-f0979b129662/2022-05-30/1101/NonCpeSoftwareInventory/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=1/part-00338-5e15412b-5c85-4896-ac60-b7b3ab8da096.c000.json.gz?sv=2020-08-04&st=2022-05-30T13%3A41%3A59Z&se=2022-05-30T16%3A41%3A59Z&sr=b&sp=r&sig=0fQg%2Ft469x26KvPLmvctLl0g6DC38CNM3lXYi9dnFfo%3D",
        "https://tvmexportexternalprdcanc.blob.core.windows.net/temp-ffd80447-7b3d-4ad2-b366-f0979b129662/2022-05-30/1101/NonCpeSoftwareInventory/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=1/part-00339-5e15412b-5c85-4896-ac60-b7b3ab8da096.c000.json.gz?sv=2020-08-04&st=2022-05-30T13%3A41%3A59Z&se=2022-05-30T16%3A41%3A59Z&sr=b&sp=r&sig=P6HGHoLXXipMauBpLueoQVrwHL7qmvLoCjcij6ERx8o%3D",
        "https://tvmexportexternalprdcanc.blob.core.windows.net/temp-ffd80447-7b3d-4ad2-b366-f0979b129662/2022-05-30/1101/NonCpeSoftwareInventory/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=1/part-00340-5e15412b-5c85-4896-ac60-b7b3ab8da096.c000.json.gz?sv=2020-08-04&st=2022-05-30T13%3A41%3A59Z&se=2022-05-30T16%3A41%3A59Z&sr=b&sp=r&sig=VnpVct%2F8vdiIFTf2xXP9DF7ngWv1Zqew30q2jBPVghg%3D",
        "https://tvmexportexternalprdcanc.blob.core.windows.net/temp-ffd80447-7b3d-4ad2-b366-f0979b129662/2022-05-30/1101/NonCpeSoftwareInventory/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=1/part-00341-5e15412b-5c85-4896-ac60-b7b3ab8da096.c000.json.gz?sv=2020-08-04&st=2022-05-30T13%3A41%3A59Z&se=2022-05-30T16%3A41%3A59Z&sr=b&sp=r&sig=GY0zxMfEmr9v9fZBWYyKEtT2k%2F0ELQIlOP0ct%2B6SdGU%3D",
    ],
    "generatedTime": "2022-05-30T11:01:00Z"
}
```

## <a name="see-also"></a>Voir aussi

- [Exporter l’évaluation logicielle par appareil](get-assessment-software-inventory.md)
- [Exporter des méthodes et des propriétés d’évaluation par appareil](get-assessment-methods-properties.md)
- [Exporter l’évaluation de la configuration sécurisée par appareil](get-assessment-secure-config.md)
- [Exporter l’évaluation des vulnérabilités logicielles par appareil](get-assessment-software-vulnerabilities.md)

Autres éléments connexes
- [Gestion des vulnérabilités Microsoft Defender](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Vulnérabilités dans votre organisation](tvm-weaknesses.md)
