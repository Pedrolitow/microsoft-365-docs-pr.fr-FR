---
title: Exporter l’évaluation des vulnérabilités logicielles par appareil
description: La réponse API est par appareil et contient les logiciels vulnérables installés sur vos appareils exposés, ainsi que les vulnérabilités connues dans ces produits logiciels. Cette table inclut également des informations sur le système d’exploitation, les ID CVE et sur la gravité des vulnérabilités.
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
ms.openlocfilehash: 951f78ba361a12e404a5cce2071f931eab30c43f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2021
ms.locfileid: "52778325"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>Exporter l’évaluation des vulnérabilités logicielles par appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]
>
>
Renvoie toutes les vulnérabilités logicielles connues et leurs détails pour tous les appareils, par appareil.

Il existe différents appels d’API pour obtenir différents types de données. Étant donné que la quantité de données peut être très importante, il existe deux façons de les récupérer :

- [Exporter l’évaluation des vulnérabilités logicielles OData](#1-export-software-vulnerabilities-assessment-odata)  L’API pulls all data in your organization as Json responses, following the OData protocol. Cette méthode est la meilleure pour _les petites organisations avec moins de 100 K appareils._ La réponse est paginée, afin que vous pouvez utiliser le champ odata.nextLink de la réponse \@ pour récupérer les résultats suivants.

- [Exporter l’évaluation des vulnérabilités logicielles via des fichiers](#2-export-software-vulnerabilities-assessment-via-files) Cette solution d’API permet d’tirer plus rapidement et de manière plus fiable des données plus volumineuses. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 K appareils. Cette API tire toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir de stockage Azure. Cette API vous permet de télécharger toutes vos données à partir stockage Azure comme suit :

  - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.

  - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traiter les données comme vous le souhaitez.

Les données collectées (à l’aide _d’OData_ ou _via_ des fichiers) sont l’instantané actuel de l’état actuel et ne contiennent pas de données historiques. Pour collecter des données historiques, les clients doivent les enregistrer dans leurs propres stockages de données.

> [!Note]
>
> Sauf indication contraire, toutes les méthodes **** d’évaluation d’exportation répertoriées sont l’exportation complète et par appareil **_(également_** appelé **_par appareil)._**

## <a name="1-export-software-vulnerabilities-assessment-odata"></a>1. Exporter l’évaluation des vulnérabilités logicielles (OData)

### <a name="11-api-method-description"></a>1.1 Description de la méthode API

Cette réponse API contient toutes les données des logiciels installés par appareil. Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="limitations"></a>Limitations

>- La taille maximale de page est de 200 000.
>
>- Les limites de taux pour cette API sont de 30 appels par minute et de 1 000 appels par heure.

### <a name="12-permissions"></a>1.2 Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir Utiliser Microsoft Defender pour les API de point de [terminaison pour plus d’informations.](apis-intro.md)

Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation
---|---|---
Application | Vulnerability.Read.All | \'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'
Déléguée (compte professionnel ou scolaire) | Vulnerability.Read | \'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>1.4 Paramètres

- pageSize (valeur par défaut = 50 000) : nombre de résultats en réponse
- $top : nombre de résultats à renvoyer (ne retourne pas @odata.nextLink et, par conséquent, ne tire pas toutes les données)

### <a name="15-properties"></a>1.5 Propriétés
>
>[!Note]
>
>- Chaque enregistrement représente environ 1 To de données. Vous devez prendre cela en compte lors du choix du paramètre pageSize approprié pour vous.
>
>- Certaines colonnes supplémentaires peuvent être renvoyées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.
>
>- Les propriétés définies dans le tableau suivant sont répertoriées par ordre alphabétique, par ID de propriété.  Lors de l’exécution de cette API, la sortie résultante ne sera pas nécessairement renvoyée dans le même ordre que celui répertorié dans ce tableau.
>

Propriété (ID) | Type de données | Description | Exemple de valeur renvoyée
:---|:---|:---|:---
CveId | string | Identificateur unique affecté à la vulnérabilité de sécurité sous le système CVE (Common Vulnerabilities and Exposures). | CVE-2020-15992
CvssScore | string | Score CVSS de la CVE. | 6.2
DeviceId | string | Identificateur unique de l’appareil dans le service. | 9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName | string | Nom de domaine complet (FQDN) de l’appareil. | johnlaptop.europe.contoso.com
DiskPaths  | Chaîne de \[ tableau\] | Preuve disque que le produit est installé sur l’appareil. | [ « C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe » ]
ExploitabilityLevel | string | Le niveau d’exploitabilité de cette vulnérabilité (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit) | ExploitIsInKit
FirstSeenTimestamp | string | Première fois que la CVE de ce produit a été vue sur l’appareil. | 2020-11-03 10:13:34.8476880
ID | string | Identificateur unique de l’enregistrement. | 123ABG55_573AG&mnp !
LastSeenTimestamp | string | Dernière fois que la CVE a été vue sur l’appareil. | 2020-11-03 10:13:34.8476880
OSPlatform | string | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. Pour plus d’informations, voir les systèmes d’exploitation et les plateformes pris en charge par tvm. | Windows 10
RbacGroupName  | string | Groupe de contrôle d’accès basé sur un rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur sera « Unassigned ». Si l’organisation ne contient aucun groupe RBAC, la valeur sera « None ». | Serveurs
RecommendationReference | string | Référence à l’ID de recommandation associé à ce logiciel. | va-_-microsoft-_-silverlight
RecommendedSecurityUpdate (facultatif) | string | Nom ou description de la mise à jour de sécurité fournie par le fournisseur de logiciels pour résoudre la vulnérabilité. | Mises à jour de sécurité d’avril 2020
RecommendedSecurityUpdateId (facultatif) | string | Identificateur des mises à jour de sécurité applicables ou identificateur pour les articles de base de connaissances ou d’aide correspondants | 4550961
RegistryPaths  | Chaîne de \[ tableau\] | Preuve dans le Registre que le produit est installé sur l’appareil. | [ « HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight » ]
SoftwareName | string | Nom du produit logiciel. | chrome
SoftwareVendor | string | Nom du fournisseur de logiciels. | google
SoftwareVersion | string | Numéro de version du produit logiciel. | 81.0.4044.138
VulnerabilitySeverityLevel  | string | Niveau de gravité affecté à la vulnérabilité de sécurité en fonction du score CVSS et des facteurs dynamiques influencés par le paysage des menaces. | Moyenne

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

### <a name="21-api-method-description"></a>Description de la méthode api 2.1

Cette réponse API contient toutes les données des logiciels installés par appareil. Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="212-limitations"></a>2.1.2 Limitations

Les limites de taux pour cette API sont de 5 appels par minute et de 20 appels par heure.

### <a name="22-permissions"></a>2.2 Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir Utiliser Microsoft Defender pour les API de point de [terminaison pour plus d’informations.](apis-intro.md)

Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation
---|---|---
Application | Vulnerability.Read.All | \'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'
Déléguée (compte professionnel ou scolaire) | Vulnerability.Read | \'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>2.4 Paramètres

- sasValidHours : nombre d’heures de validité des URL de téléchargement (maximum 24 heures)

### <a name="25-properties"></a>2.5 Propriétés

>[!Note]
>
>- Les fichiers sont compressés gzip & au format Json multiligne.
>
>- Les URL de téléchargement ne sont valides que pendant 3 heures . Sinon, vous pouvez utiliser le paramètre.
>
>- Pour une vitesse de téléchargement maximale de vos données, vous pouvez vous assurer que vous téléchargez à partir de la même région Azure que vos données résident.
>

>[!Note]
>
>- Chaque enregistrement représente environ 1 To de données. Vous devez prendre cela en compte lors du choix du paramètre pageSize approprié pour vous.
>
>- Certaines colonnes supplémentaires peuvent être renvoyées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.
>

Propriété (ID) | Type de données | Description | Exemple de valeur renvoyée
:---|:---|:---|:---
Exporter des fichiers | chaîne de \[ tableau\]  | Liste des URL de téléchargement pour les fichiers qui contiennent la capture instantanée actuelle de l’organisation. | [  “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2”  ]
GeneratedTime | string | Heure de la générer. | 2021-05-20T08:00:00Z

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

## <a name="see-also"></a>Voir aussi

- [Exporter les méthodes et propriétés d’évaluation par appareil](get-assessmnt-1methods-properties.md)

- [Exporter l’évaluation de la configuration sécurisée par appareil](get-assessmnt-secure-cfg.md)

- [Exporter l’évaluation de l’inventaire logiciel par appareil](get-assessmnt-software-inventory.md)

Autres associés

- [Menaces basées sur les risques & gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)

- [Vulnérabilités dans votre organisation](tvm-weaknesses.md)
