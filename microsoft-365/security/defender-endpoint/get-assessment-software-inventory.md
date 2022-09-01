---
title: Exporter l’évaluation de l’inventaire logiciel par appareil
description: Retourne une table avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.
keywords: api, api, évaluation d’exportation, évaluation par appareil, rapport d’évaluation des vulnérabilités, évaluation des vulnérabilités des appareils, rapport de vulnérabilité des appareils, évaluation de la configuration sécurisée, rapport de configuration sécurisé, évaluation des vulnérabilités logicielles, rapport de vulnérabilité logicielle, rapport de vulnérabilité par ordinateur,
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.custom: api
ms.openlocfilehash: 02d14b7aad018d8c4744c5aed012e441f65ac1d0
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67516025"
---
# <a name="export-software-inventory-assessment-per-device"></a>Exporter l’évaluation de l’inventaire logiciel par appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des vulnérabilités de Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette API retourne toutes les données pour les logiciels installés qui disposent d’une [énumération de plateforme commune (CPE),](https://nvd.nist.gov/products/cpe) sur une base par appareil.

Les différents appels d’API obtiennent différents types de données. Étant donné que la quantité de données peut être importante, il existe deux façons de les récupérer :

- [Exporter la **réponse JSON** d’évaluation de l’inventaire logiciel](#1-export-software-inventory-assessment-json-response) L’API extrait toutes les données de votre organisation en tant que réponses Json. Cette méthode est idéale pour _les petites organisations avec moins de 100 K d’appareils_. La réponse étant paginée, vous pouvez utiliser le \@champ odata.nextLink de la réponse pour extraire les résultats suivants.

- [Exporter l’évaluation de l’inventaire logiciel **via des fichiers**](#2-export-software-inventory-assessment-via-files)  Cette solution d’API permet d’extraire de plus grandes quantités de données plus rapidement et de manière plus fiable. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 000 appareils. Cette API extrait toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir du stockage Azure. Cette API vous permet de télécharger toutes vos données à partir du Stockage Azure comme suit :
  - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.
  - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traitez les données comme vous le souhaitez.

Les données collectées (à l’aide d’une _réponse Json_ ou _de fichiers_) sont l’instantané actuel de l’état actuel. Il ne contient pas de données historiques. Pour collecter des données historiques, les clients doivent enregistrer les données dans leurs propres stockages de données.

> [!NOTE]
> Sauf indication contraire, toutes les méthodes d’évaluation d’exportation répertoriées sont **_l’exportation complète_** et **_par appareil_** (également appelée **_par appareil_**).

## <a name="1-export-software-inventory-assessment-json-response"></a>1. Exporter l’évaluation de l’inventaire logiciel (réponse JSON)

### <a name="11-api-method-description"></a>Description de la méthode d’API 1.1

Cette réponse d’API contient toutes les données des logiciels installés qui ont une [énumération de plateforme commune (CPE)](https://nvd.nist.gov/products/cpe) par appareil. Retourne une table avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.

#### <a name="111-limitations"></a>1.1.1 Limitations

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
GET /api/machines/SoftwareInventoryByMachine
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

****

Propriété (ID)|Type de données|Description|Exemple de valeur retournée
:---|:---|:---|:---
DeviceId|string|Identificateur unique de l’appareil dans le service.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|string|Nom de domaine complet (FQDN) de l’appareil.|johnlaptop.europe.contoso.com
DiskPaths|Array[string]|Preuve de disque indiquant que le produit est installé sur l’appareil.|[ « C:\\ Program Files (x86)\\Microsoft\\Silverlight\\Application\\silverlight.exe » ]
EndOfSupportDate|chaîne|Date de fin de la prise en charge de ce logiciel.|2020-12-30
EndOfSupportStatus|chaîne|Fin de l’état du support. Peut contenir ces valeurs possibles : None, EOS Version, Future EOS Version, EOS Software, Future EOS Software.|EOS à venir
ID|string|Identificateur unique de l’enregistrement.|123ABG55_573AG&mnp!
NumberOfWeaknesses|int|Nombre de faiblesses sur ce logiciel sur cet appareil|3
OSPlatform|string|Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Il s’agit de systèmes d’exploitation spécifiques avec des variantes au sein de la même famille, telles que Windows 10 et Windows 11. Pour plus d’informations, consultez Gestion des vulnérabilités Microsoft Defender systèmes d’exploitation et plateformes pris en charge.|Windows 10 et Windows 11
RbacGroupName|chaîne|Groupe de contrôle d’accès en fonction du rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur est « Non affecté ». Si l’organisation ne contient aucun groupe RBAC, la valeur est « None ».|Serveurs
RegistryPaths|Array[string]|Preuve du Registre indiquant que le produit est installé sur l’appareil.|[ « HKEY_LOCAL_MACHINE\\ SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Silverlight » ]
SoftwareFirstSeenTimestamp|string|La première fois que ce logiciel a été vu sur l’appareil.|2019-04-07 02:06:47
SoftwareName|string|Nom du produit logiciel.|Silverlight
SoftwareVendor|chaîne|Nom du fournisseur de logiciels.|microsoft
SoftwareVersion|string|Numéro de version du produit logiciel.|81.0.4044.138
|

### <a name="16-examples"></a>1.6 Exemples

#### <a name="161-request-example"></a>Exemple de demande 1.6.1

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryByMachine?pageSize=5  &sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="162-response-example"></a>1.6.2 Exemple de réponse

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(contoso.windowsDefenderATP.api.AssetSoftware)",
    "value": [
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10" "Windows_11",
            "softwareVersion": "10.0.17763.1637",
            "numberOfWeaknesses": 58,
            "diskPaths": [],
            "registryPaths": [],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "Upcoming EOS Version",
            "endOfSupportDate": "2021-05-11T00:00:00+00:00"
        },
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": ".net_framework",
            "softwareVersion": "4.0.0.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.0\\Client\\Install"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eed80d086e79bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.7.214.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f68765ddaf71234bde6bd733d6a9c59ad4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178aedfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "configuration_manager",
            "softwareVersion": "5.0.8634.1000",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\{B7D3A842-E826-4542-B39B-1D883264B279}"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f38765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2de2f5ea3142726e63f16a.DomainPII_21eeb80d086e79bdfa178eadfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.10.209.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0yNS8wMjAwLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

> [!NOTE]
> Les informations retournées par cette API, ainsi que les informations retournées par l’API [d’évaluation de l’inventaire logiciel non du code produit](get-assessment-non-cpe-software-inventory.md) , pour les logiciels qui n’ont pas de CPE, vous donnent une visibilité complète sur les logiciels installés dans votre organisation et les appareils sur lesquels elle est installée.

## <a name="2-export-software-inventory-assessment-via-files"></a>2. Exporter l’évaluation de l’inventaire logiciel (via des fichiers)

### <a name="21-api-method-description"></a>Description de la méthode API 2.1

Cette réponse d’API contient toutes les données des logiciels installés par appareil. Retourne une table avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.

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
GET /api/machines/SoftwareInventoryExport
```

### <a name="parameters"></a>Paramètres

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
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryExport
```

#### <a name="262-response-example"></a>2.6.2 Exemple de réponse

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>Voir aussi

- [Exporter des méthodes et des propriétés d’évaluation par appareil](get-assessment-methods-properties.md)
- [Exporter l’évaluation de la configuration sécurisée par appareil](get-assessment-secure-config.md)
- [Exporter l’évaluation des vulnérabilités logicielles par appareil](get-assessment-software-vulnerabilities.md)
- [Exporter l’évaluation de l’inventaire logiciel de code non-produit](get-assessment-non-cpe-software-inventory.md)

Autres éléments connexes

- [Gestion des vulnérabilités Microsoft Defender](next-gen-threat-and-vuln-mgt.md)
- [Vulnérabilités dans votre organisation](tvm-weaknesses.md)
