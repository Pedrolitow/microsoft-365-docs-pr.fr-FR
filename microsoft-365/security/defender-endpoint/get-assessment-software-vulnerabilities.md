---
title: Exporter l’évaluation des vulnérabilités logicielles par appareil
description: La réponse api est par appareil et contient les logiciels vulnérables installés sur vos appareils exposés, ainsi que les vulnérabilités connues dans ces produits logiciels. Cette table inclut également des informations sur le système d’exploitation, les ID CVE et sur la gravité des vulnérabilités.
keywords: api, api, évaluation d’exportation, évaluation par appareil, rapport d’évaluation des vulnérabilités, évaluation des vulnérabilités d’appareils, rapport de vulnérabilité d’appareil, évaluation de la configuration sécurisée, rapport de configuration sécurisé, évaluation des vulnérabilités logicielles, rapport de vulnérabilité logicielle, rapport de vulnérabilité par ordinateur,
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: c9964ce7abdae004b33fb7317740b30b46b72d95
ms.sourcegitcommit: 132b8dc316bcd4b456de33d6a30e90ca69b0f956
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58603290"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>Exporter l’évaluation des vulnérabilités logicielles par appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Renvoie toutes les vulnérabilités logicielles connues et leurs détails pour tous les appareils, par appareil.

Il existe différents appels d’API pour obtenir différents types de données. Étant donné que la quantité de données peut être très importante, il existe deux façons de les récupérer :

1. [Exporter la réponse JSON de l’évaluation **des vulnérabilités logicielles**](#1-export-software-vulnerabilities-assessment-json-response)  L’API tire toutes les données de votre organisation en tant que réponses Json. Cette méthode est la meilleure pour _les petites organisations avec moins de 100 K appareils._ La réponse est paginée, afin que vous pouvez utiliser le champ odata.nextLink de la réponse \@ pour récupérer les résultats suivants.

2. [Exporter l’évaluation des vulnérabilités **logicielles via des fichiers**](#2-export-software-vulnerabilities-assessment-via-files) Cette solution d’API permet d’tirer plus rapidement et de manière plus fiable des données plus volumineuses. Les fichiers via les fichiers sont recommandés pour les grandes organisations, avec plus de 100 Périphériques K. Cette API tire toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir de stockage Azure. Cette API vous permet de télécharger toutes vos données à partir stockage Azure comme suit :
   - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.
   - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traiter les données comme vous le souhaitez.

3. [Réponse JSON de l’évaluation des vulnérabilités **logicielles d’exportation delta**](#3-delta-export-software-vulnerabilities-assessment-json-response)  Renvoie un tableau avec une entrée pour chaque combinaison unique de : DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId et EventTimestamp.
L’API tire les données de votre organisation en tant que réponses Json. La réponse est paginée, afin que vous pouvez utiliser le champ @odata.nextLink de la réponse pour récupérer les résultats suivants.

   Contrairement à l’évaluation complète des vulnérabilités logicielles (réponse JSON), qui permet d’obtenir un instantané complet de l’évaluation des vulnérabilités logicielles de votre organisation par appareil, l’appel de l’API d’exportation delta est utilisé pour récupérer uniquement les modifications qui se sont produites entre une date sélectionnée et la date actuelle (l’appel d’API « delta »). Au lieu d’obtenir une exportation complète avec une grande quantité de données à chaque fois, vous obtenez uniquement des informations spécifiques sur les vulnérabilités nouvelles, fixes et mises à jour. L’appel de l’API de réponse JSON d’exportation delta peut également être utilisé pour calculer différents KPI, tels que « combien de vulnérabilités ont été corrigées ? » ou « combien de nouvelles vulnérabilités ont été ajoutées à mon organisation ? »

   Étant donné que l’appel de l’API de réponse JSON d’exportation delta pour les vulnérabilités logicielles renvoie des données uniquement pour une plage de dates ciblée, il n’est pas considéré comme _une exportation complète._

Les données collectées (à l’aide d’une réponse _Json_ ou _de_ fichiers) sont l’instantané actuel de l’état actuel et ne contiennent pas de données historiques. Pour collecter des données historiques, les clients doivent les enregistrer dans leurs propres stockages de données.

> [!NOTE]
> Sauf indication contraire, toutes les méthodes **** d’évaluation d’exportation répertoriées sont l’exportation complète et par appareil **_(également_** appelé **_par appareil)._**

## <a name="1-export-software-vulnerabilities-assessment-json-response"></a>1. Exporter l’évaluation des vulnérabilités logicielles (réponse JSON)

### <a name="11-api-method-description"></a>1.1 Description de la méthode API

Cette réponse API contient toutes les données des logiciels installés par appareil. Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="111-limitations"></a>1.1.1 Limitations

- La taille maximale de page est de 200 000.
- Les limites de taux pour cette API sont de 30 appels par minute et de 1 000 appels par heure.

### <a name="12-permissions"></a>1.2 Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir Utiliser Microsoft Defender pour les API de point de [terminaison pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
---|---|---
Application|Vulnerability.Read.All|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'
Déléguée (compte professionnel ou scolaire)|Vulnerability.Read|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>1.4 Paramètres

- pageSize (valeur par défaut = 50 000) : nombre de résultats en réponse.
- $top : nombre de résultats à renvoyer (ne retourne pas @odata.nextLink et, par conséquent, ne tire pas toutes les données).

### <a name="15-properties"></a>1.5 Propriétés

> [!NOTE]
>
> - Chaque enregistrement représente environ 1 Ko de données. Vous devez en tenir compte lors du choix du paramètre pageSize approprié pour vous.
> - Certaines colonnes supplémentaires peuvent être renvoyées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.
> - Les propriétés définies dans le tableau suivant sont répertoriées par ordre alphabétique, par ID de propriété. Lors de l’exécution de cette API, la sortie résultante ne sera pas nécessairement renvoyée dans le même ordre que celui répertorié dans ce tableau.

<br>

****

Propriété (ID)|Type de données|Description|Exemple de valeur renvoyée
:---|:---|:---|:---
CveId|string|Identificateur unique affecté à la vulnérabilité de sécurité sous le système CVE (Common Vulnerabilities and Exposures).|CVE-2020-15992
CvssScore|string|Score CVSS de la CVE.|6.2
DeviceId|chaîne|Identificateur unique de l’appareil dans le service.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|chaîne|Nom de domaine complet (FQDN) de l’appareil.|johnlaptop.europe.contoso.com
DiskPaths|Chaîne de \[ tableau\]|Preuve disque que le produit est installé sur l’appareil.|[ « C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe » ]
ExploitabilityLevel|string|Le niveau d’exploitabilité de cette vulnérabilité (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit
FirstSeenTimestamp|string|Première fois que la CVE de ce produit a été vue sur l’appareil.|2020-11-03 10:13:34.8476880
ID|string|Identificateur unique de l’enregistrement.|123ABG55_573AG&mnp!
LastSeenTimestamp|string|Dernière fois que la CVE a été vue sur l’appareil.|2020-11-03 10:13:34.8476880
OSPlatform|string|Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cette propriété indique des systèmes d’exploitation spécifiques, y compris des variantes au sein de la même famille, telles que Windows 10 et Windows 7. Pour plus d’informations, voir les systèmes d’exploitation et les plateformes pris en charge par tvm.|Windows 10
RbacGroupName|string|Groupe de contrôle d’accès basé sur un rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur sera « Unassigned ». Si l’organisation ne contient aucun groupe RBAC, la valeur sera « None ».|Serveurs
RecommendationReference|string|Référence à l’ID de recommandation associé à ce logiciel.|va-_-microsoft-_-silverlight
RecommendedSecurityUpdate (facultatif)|chaîne|Nom ou description de la mise à jour de sécurité fournie par le fournisseur de logiciels pour résoudre la vulnérabilité.|Mises à jour de sécurité d’avril 2020
RecommendedSecurityUpdateId (facultatif)|string|Identificateur des mises à jour de sécurité applicables ou identificateur pour les articles de base de connaissances ou de conseils correspondants|4550961
RegistryPaths|Chaîne de \[ tableau\]|Preuve dans le Registre que le produit est installé sur l’appareil.|[ « HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight » ]
SoftwareName|chaîne|Nom du produit logiciel.|chrome
SoftwareVendor|chaîne|Nom du fournisseur de logiciels.|google
SoftwareVersion|string|Numéro de version du produit logiciel.|81.0.4044.138
VulnerabilitySeverityLevel|string|Niveau de gravité affecté à la vulnérabilité de sécurité en fonction du score CVSS et des facteurs dynamiques influencés par le paysage des menaces.|Moyen
|

### <a name="16-examples"></a>1.6 Exemples

#### <a name="161-request-example"></a>1.6.1 Exemple de requête

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pageSize=5
```

#### <a name="162-response-example"></a>1.6.2 Exemple de réponse

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetVulnerability)",
    "value": [
        {
            "id": "00044f612345baf759462dbe6db733b6a9c59ab4_edge_10.0.17763.1637__",
            "deviceId": "00044f612345daf756462bde6bd733b9a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2de2f5ea3142726e63f16a.DomainPII_21eeb80d089e79bdfa178eabfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "edge",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-edge"
        },
        {
            "id": "00044f912345baf756462bde6db733b9a9c56ad4_.net_framework_4.0.0.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ad4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e79bdfa178eabfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": ".net_framework",
            "softwareVersion": "4.0.0.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.0\\Client\\Install"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-.net_framework"
        },
        {
            "id": "00044f912345baf756462dbe6db733d6a9c59ab4_system_center_2012_endpoint_protection_4.10.209.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eed80b089e79bdfa178eadfa25e8be6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.10.209.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-system_center_2012_endpoint_protection"
        },
        {
            "id": "00044f612345bdaf759462dbe6bd733b6a9c59ab4_onedrive_20.245.1206.2__",
            "deviceId": "00044f91234daf759492dbe6bd733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_189663d45612eed224b2be2f5ea3142729e63f16a.DomainPII_21eed80b086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "onedrive",
            "softwareVersion": "20.245.1206.2",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_USERS\\S-1-5-21-2944539346-1310925172-2349113062-1001\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\OneDriveSetup.exe"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-onedrive"
        },
        {
            "id": "00044f912345daf759462bde6db733b6a9c56ab4_windows_10_10.0.17763.1637__",
            "deviceId": "00044f912345daf756462dbe6db733d6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eeb224d2be2f5ea3142729e63f16a.DomainPII_21eeb80d086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-windows_10"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-vulnerabilities-assessment-via-files"></a>2. Exporter l’évaluation des vulnérabilités logicielles (via des fichiers)

### <a name="21-api-method-description"></a>2.1 Description de la méthode API

Cette réponse API contient toutes les données des logiciels installés par appareil. Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="212-limitations"></a>2.1.2 Limitations

Les limites de taux pour cette API sont de 5 appels par minute et de 20 appels par heure.

### <a name="22-permissions"></a>2.2 Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir Utiliser Microsoft Defender pour les API de point de [terminaison pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
---|---|---
Application|Vulnerability.Read.All|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'
Déléguée (compte professionnel ou scolaire)|Vulnerability.Read|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>2.4 Paramètres

- sasValidHours : nombre d’heures de validité des URL de téléchargement (maximum 24 heures).

### <a name="25-properties"></a>2.5 Propriétés

> [!NOTE]
>
> - Les fichiers sont compressés gzip & au format Json multiligne.
> - Les URL de téléchargement ne sont valides que pendant 3 heures . Sinon, vous pouvez utiliser le paramètre.
> - Pour une vitesse de téléchargement maximale de vos données, vous pouvez vous assurer que vous téléchargez à partir de la même région Azure que vos données résident.
>
> - Chaque enregistrement représente environ 1 To de données. Vous devez prendre cela en compte lors du choix du paramètre pageSize approprié pour vous.
> - Certaines colonnes supplémentaires peuvent être renvoyées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.

<br>

****

Propriété (ID)|Type de données|Description|Exemple de valeur renvoyée
:---|:---|:---|:---
Exporter des fichiers|chaîne de \[ tableau\]|Liste des URL de téléchargement pour les fichiers qui contiennent la capture instantanée actuelle de l’organisation.|["https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|string|Heure de la générer.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Exemples

#### <a name="261-request-example"></a>2.6.1 Exemple de requête

```http
GET https://api-us.securitycenter.contoso.com/api/machines/SoftwareVulnerabilitiesExport
```

#### <a name="262-response-example"></a>2.6.2 Exemple de réponse

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c002.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="3-delta-export-software-vulnerabilities-assessment-json-response"></a>3. Évaluation des vulnérabilités logicielles d’exportation delta (réponse JSON)

### <a name="31-api-method-description"></a>3.1 Description de la méthode d’API

Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. L’API tire les données de votre organisation en tant que réponses Json. La réponse est paginée, afin que vous pouvez utiliser le champ @odata.nextLink de la réponse pour récupérer les résultats suivants. Contrairement à l’évaluation complète des vulnérabilités logicielles (réponse JSON) (qui permet d’obtenir un instantané complet de l’évaluation des vulnérabilités logicielles de votre organisation par périphérique), l’appel de l’API de réponse JSON d’exportation delta est utilisé pour récupérer uniquement les modifications qui se sont produites entre une date sélectionnée et la date actuelle (l’appel d’API « delta »). Au lieu d’obtenir une exportation complète avec une grande quantité de données à chaque fois, vous obtenez uniquement des informations spécifiques sur les vulnérabilités nouvelles, fixes et mises à jour. L’appel de l’API de réponse JSON d’exportation delta peut également être utilisé pour calculer différents KPI, tels que « combien de vulnérabilités ont été corrigées ? » ou « combien de nouvelles vulnérabilités ont été ajoutées à mon organisation ? »

> [!NOTE]
> Il est vivement recommandé d’utiliser l’évaluation complète des vulnérabilités logicielles d’exportation par appel d’API d’appareil au moins une fois par semaine, et cette exportation supplémentaire de vulnérabilités logicielles change par api d’appareil (delta) tous les autres jours de la semaine. Contrairement aux autres API de réponse JSON d’évaluations, l'« exportation delta » n’est pas une exportation complète. L’exportation delta inclut uniquement les modifications qui se sont produites entre une date sélectionnée et la date actuelle (l’appel d’API « delta »).

#### <a name="311-limitations"></a>3.1.1 Limitations

- La taille maximale de page est de 200 000.
- Le paramètre sinceTime a un maximum de 14 jours.
- Les limites de taux pour cette API sont de 30 appels par minute et de 1 000 appels par heure.

### <a name="32-permissions"></a>3.2 Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir Utiliser Microsoft Defender pour les API de point de [terminaison pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
---|---|---
Application|Vulnerability.Read.All|« Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire)|Vulnerability.Read|« Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités »

### <a name="33-url"></a>3.3 URL

```http
GET /api/machines/SoftwareVulnerabilityChangesByMachine
```

### <a name="34-parameters"></a>3.4 Paramètres

- sinceTime (obligatoire) : données entre une heure sélectionnée et aujourd’hui.
- pageSize (valeur par défaut = 50 000) : nombre de résultats en réponse.
- $top : nombre de résultats à renvoyer (ne retourne pas @odata.nextLink et, par conséquent, ne tire pas toutes les données).

### <a name="35-properties"></a>3.5 Propriétés

Chaque enregistrement renvoyé contient toutes les données de l’évaluation complète des vulnérabilités logicielles d’exportation par API d’appareil, ainsi que deux champs supplémentaires :  _**EventTimestamp**_ et _**Status**_.

> [!NOTE]
>
> - Certaines colonnes supplémentaires peuvent être renvoyées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez donc uniquement les colonnes documentées.
> - Les propriétés définies dans le tableau suivant sont répertoriées par ordre alphabétique, par ID de propriété. Lors de l’exécution de cette API, la sortie résultante ne sera pas nécessairement renvoyée dans le même ordre que celui répertorié dans ce tableau.

<br>

****

Propriété (ID)|Type de données|Description|Exemple de valeur renvoyée
:---|:---|:---|:---
CveId |chaîne|Identificateur unique affecté à la vulnérabilité de sécurité sous le système CVE (Common Vulnerabilities and Exposures).|CVE-2020-15992  
CvssScore|string|Score CVSS de la CVE.|6.2  
DeviceId|string|Identificateur unique de l’appareil dans le service.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1  
DeviceName|string|Nom de domaine complet (FQDN) de l’appareil.|johnlaptop.europe.contoso.com  
DiskPaths|Array[string]|Preuve disque que le produit est installé sur l’appareil.|["C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe"]  
EventTimestamp|Chaîne|Heure de la découverte de cet événement delta.|2021-01-11T11:06:08.291Z
ExploitabilityLevel|string|Le niveau d’exploitabilité de cette vulnérabilité (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit  
FirstSeenTimestamp|chaîne|Première fois que la CVE de ce produit a été vue sur l’appareil.|2020-11-03 10:13:34.8476880  
ID|string|Identificateur unique de l’enregistrement.|123ABG55_573AG&mnp!  
LastSeenTimestamp|chaîne|Dernière fois que la CVE a été vue sur l’appareil.|2020-11-03 10:13:34.8476880  
OSPlatform|string|Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. Pour plus d’informations, voir les systèmes d’exploitation et les plateformes pris en charge par tvm.|Windows 10  
RbacGroupName|chaîne|Groupe de contrôle d’accès basé sur un rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur sera « Unassigned ». Si l’organisation ne contient aucun groupe RBAC, la valeur sera « None ».|Serveurs  
RecommendationReference|string|Référence à l’ID de recommandation associé à ce logiciel.|va--microsoft--silverlight  
RecommendedSecurityUpdate |chaîne|Nom ou description de la mise à jour de sécurité fournie par le fournisseur de logiciels pour résoudre la vulnérabilité.|Mises à jour de sécurité d’avril 2020  
RecommendedSecurityUpdateId |string|Identificateur des mises à jour de sécurité applicables ou identificateur pour les articles de base de connaissances ou d’aide correspondants|4550961  
RegistryPaths |Array[string]|Preuve dans le Registre que le produit est installé sur l’appareil.|[ « HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\Google Chrome » ]  
SoftwareName|string|Nom du produit logiciel.|chrome  
SoftwareVendor|string|Nom du fournisseur de logiciels.|google  
SoftwareVersion|string|Numéro de version du produit logiciel.|81.0.4044.138  
Statut|Chaîne|**Nouveau**   (pour une nouvelle vulnérabilité introduite sur un appareil)  (1) **Corrigé**(si cette vulnérabilité n’existe plus sur l’appareil, ce qui signifie   qu’elle a été corrigée). (2)  **Mise à jour**   (si une vulnérabilité sur un appareil a changé. Les modifications possibles sont les suivants : score CVSS, niveau d’exploitabilité, niveau de gravité, DiskPaths, RegistryPaths, RecommendedSecurityUpdate). |Fixed
VulnerabilitySeverityLevel|string|Niveau de gravité affecté à la vulnérabilité de sécurité en fonction du score CVSS et des facteurs dynamiques influencés par le paysage des menaces.|Moyen
|

#### <a name="clarifications"></a>Clarifications

- Si le logiciel a été mis à jour de la version 1.0 à la version 2.0 et que les deux versions sont exposées à CVE-A, vous recevrez 2 événements distincts :
   1. Fixed: CVE-A on version 1.0 was fixed.
   1. Nouveauté : CVE-A sur la version 2.0 a été ajouté.

- Si une vulnérabilité spécifique (par exemple, CVE-A) a été vue pour la première fois à un moment spécifique (par exemple, le 10 janvier) sur un logiciel avec la version 1.0, et quelques jours plus tard, ce logiciel a été mis à jour vers la version 2.0 qui a également été exposée au même CVE-A, vous recevrez ces deux événements séparés :
   1. Fixe : CVE-X, FirstSeenTimestamp 10 janvier, version 1,0.
   1. Nouveauté : CVE-X, FirstSeenTimestamp 10 janvier, version 2.0.

### <a name="36-examples"></a>3.6 Exemples

#### <a name="361-request-example"></a>3.6.1 Exemple de requête

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilityChangesByMachine?pageSize=5&sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="362-response-example"></a>3.6.2 Exemple de réponse

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.DeltaAssetVulnerability)",
    "value": [
        {
            "id": "008198251234544f7dfa715e278d4cec0c16c171_chrome_87.0.4280.88__",
            "deviceId": "008198251234544f7dfa715e278b4cec0c19c171",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_1c8fee370690ca24b6a0d3f34d193b0424943a8b8.DomainPII_0dc1aee0fa366d175e514bd91a9e7a5b2b07ee8e.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "google",
            "softwareName": "chrome",
            "softwareVersion": "87.0.4280.88",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Google Chrome"
            ],
            "lastSeenTimestamp": "2021-01-04 00:29:42",
            "firstSeenTimestamp": "2020-11-06 03:12:44",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-google-_-chrome",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "00e59c61234533860738ecf488eec8abf296e41e_onedrive_20.64.329.3__",
            "deviceId": "00e56c91234533860738ecf488eec8abf296e41e",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_82c13a8ad8cf3dbaf7bf34fada9fa3aebc124116.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.18363.1256",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "onedrive",
            "softwareVersion": "20.64.329.3",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_USERS\\S-1-5-21-2127521184-1604012920-1887927527-24918864\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\OneDriveSetup.exe"
            ],
            "lastSeenTimestamp": "2020-12-11 19:49:48",
            "firstSeenTimestamp": "2020-12-07 18:25:47",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-onedrive",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "01aa8c73095bb12345918663f3f94ce322107d24_firefox_83.0.0.0_CVE-2020-26971_",
            "deviceId": "01aa8c73065bb12345918693f3f94ce322107d24",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_42684eb981bea2d670027e7ad2caafd3f2b381a3.DomainPII_21eed80b086e76dbfa178eabfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "mozilla",
            "softwareName": "firefox",
            "softwareVersion": "83.0.0.0",
            "cveId": "CVE-2020-26971",
            "vulnerabilitySeverityLevel": "High",
            "recommendedSecurityUpdate": "193220",
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Mozilla Firefox\\firefox.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Mozilla Firefox 83.0 (x86 en-US)"
            ],
            "lastSeenTimestamp": "2021-01-05 17:04:30",
            "firstSeenTimestamp": "2020-05-06 12:42:19",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-mozilla-_-firefox",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "026f0fcb12345fbd2decd1a339702131422d362e_project_16.0.13701.20000__",
            "deviceId": "029f0fcb13245fbd2decd1a336702131422d392e",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_a5706750acba75f15d69cd17f4a7fcd268d6422c.DomainPII_f290e982685f7e8eee168b4332e0ae5d2a069cd6.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "project",
            "softwareVersion": "16.0.13701.20000",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\ProjectProRetail - en-us"
            ],
            "lastSeenTimestamp": "2021-01-03 23:38:03",
            "firstSeenTimestamp": "2019-08-01 22:56:12",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-project",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "038df381234510b357ac19d0113ef622e4e212b3_chrome_81.0.4044.138_CVE-2020-16011_",
            "deviceId": "038df381234510d357ac19b0113ef922e4e212b3",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_365f5c0bb7202c163937dad3d017969b2d760eb4.DomainPII_29596a43a2ef2bbfa00f6a16c0cb1d108bc63e32.DomainPII_3c5fefd2e6fda2f36257359404f6c1092aa6d4b8.net",
            "osPlatform": "Windows10",
            "osVersion": "10.0.18363.1256",
            "osArchitecture": "x64",
            "softwareVendor": "google",
            "softwareName": "chrome",
            "softwareVersion": "81.0.4044.138",
            "cveId": "CVE-2020-16011",
            "vulnerabilitySeverityLevel": "High",
            "recommendedSecurityUpdate": "ADV 200002",
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\{C4EBFDFD-0C55-3E5F-A919-E3C54949024A}"
            ],
            "lastSeenTimestamp": "2020-12-10 22:45:41",
            "firstSeenTimestamp": "2020-07-26 02:13:43",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-google-_-chrome",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        }
    ],
    "@odata.nextLink": "https://wpatdadi-eus-stg.cloudapp.net/api/machines/SoftwareVulnerabilitiesTimeline?sincetime=2021-01-11&pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="see-also"></a>Voir aussi

- [Exporter les méthodes et propriétés d’évaluation par appareil](get-assessment-methods-properties.md)
- [Exporter l’évaluation de la configuration sécurisée par appareil](get-assessment-secure-config.md)
- [Exporter l’évaluation de l’inventaire logiciel par appareil](get-assessment-software-inventory.md)

Autres associés

- [Menaces basées sur les risques & gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Vulnérabilités de votre organisation](tvm-weaknesses.md)
