---
title: Exporter l’évaluation de la configuration sécurisée par appareil
description: Retourne une entrée pour chaque combinaison unique de DeviceId, ConfigurationId.
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
ms.collection:
- m365-security
- tier3
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 64f9db688a9d32d3704a64d199be7074ae860398
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68209951"
---
# <a name="export-secure-configuration-assessment-per-device"></a>Exporter l’évaluation de la configuration sécurisée par appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des vulnérabilités de Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Retourne toutes les configurations et leur état, par appareil.

Il existe différents appels d’API pour obtenir différents types de données. Étant donné que la quantité de données peut être importante, il existe deux façons de les récupérer :

- [Exporter la **réponse JSON** d’évaluation de la configuration sécurisée](#1-export-secure-configuration-assessment-json-response) : l’API extrait toutes les données de votre organisation en tant que réponses Json. Cette méthode est idéale pour _les petites organisations avec moins de 100 K d’appareils_. La réponse étant paginée, vous pouvez utiliser le \@champ odata.nextLink de la réponse pour extraire les résultats suivants.

- [Exporter l’évaluation de la configuration sécurisée **via des fichiers**](#2-export-secure-configuration-assessment-via-files) : cette solution API permet d’extraire de plus grandes quantités de données plus rapidement et de manière plus fiable. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 K appareils. Cette API extrait toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir du stockage Azure. Cette API vous permet de télécharger toutes vos données à partir du Stockage Azure comme suit :

  - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.

  - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traitez les données comme vous le souhaitez.

Les données collectées (à l’aide d’une _réponse JSON_ ou _par le biais de fichiers_) sont l’instantané actuel de l’état actuel et ne contiennent pas de données historiques. Pour collecter des données historiques, les clients doivent enregistrer les données dans leurs propres stockages de données.

> [!NOTE]
> Sauf indication contraire, toutes les méthodes d’évaluation d’exportation répertoriées sont **_l’exportation complète_** et **_par appareil_** (également appelée **_par appareil_**).

## <a name="1-export-secure-configuration-assessment-json-response"></a>1. Exporter l’évaluation de la configuration sécurisée (réponse JSON)

### <a name="11-api-method-description"></a>Description de la méthode d’API 1.1

Cette réponse d’API contient l’évaluation de la configuration sécurisée sur vos appareils exposés et retourne une entrée pour chaque combinaison unique de DeviceId, ConfigurationId.

#### <a name="111-limitations"></a>1.1.1 Limitations

- La taille maximale de la page est de 200 000.

- Les limites de débit pour cette API sont de 30 appels par minute et de 1 000 appels par heure.

### <a name="12-permissions"></a>1.2 Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md) pour plus d’informations.

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
---|---|---
Application|Vulnerability.Read.All|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'
Déléguée (compte professionnel ou scolaire)|Vulnerability.Read|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'

### <a name="13-url"></a>URL 1.3

```http
GET /api/machines/SecureConfigurationsAssessmentByMachine
```

### <a name="14-parameters"></a>1.4 Paramètres

- pageSize \(default = 50 000\) : nombre de résultats en réponse.
- \$top : le nombre de résultats à retourner \(ne retourne \@pas odata.nextLink et n’extrait donc pas toutes les données\).

### <a name="15-properties"></a>1.5 Propriétés

> [!NOTE]
>
> - Les propriétés définies dans le tableau suivant sont répertoriées par ordre alphabétique, par ID de propriété. Lors de l’exécution de cette API, la sortie résultante ne sera pas nécessairement retournée dans le même ordre que celui répertorié dans ce tableau.
> - Certaines colonnes supplémentaires peuvent être retournées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.

<br>

****

Propriété (ID)|Type de données|Description|Exemple de valeur retournée
---|---|---|---
ConfigurationCategory|string|Catégorie ou regroupement auquel appartient la configuration : application, système d’exploitation, réseau, comptes, contrôles de sécurité|Contrôles de sécurité
ConfigurationId|string|Identificateur unique pour une configuration spécifique|scid-10000
ConfigurationImpact|string|Impact nominal de la configuration sur la note de configuration globale (1-10)|9 
ConfigurationName|string|Nom d’affichage de la configuration|Intégrer des appareils à Microsoft Defender pour point de terminaison
ConfigurationSubcategory|string|Sous-catégorie ou sous-groupement auquel appartient la configuration. Dans de nombreux cas, cela décrit des capacités ou des fonctionnalités spécifiques.|Intégrer des appareils
DeviceId|string|Identificateur unique de l’appareil dans le service.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|chaîne|Nom de domaine complet (FQDN) de l’appareil.|johnlaptop.europe.contoso.com
IsApplicable|bool|Indique si la configuration ou la stratégie est applicable|true
IsCompliant|bool|Indique si la configuration ou la stratégie est correctement configurée.|false
IsExpectedUserImpact|bool|Indique s’il y aura un impact sur l’utilisateur si la configuration sera appliquée|true
OSPlatform|string|Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cela indique des systèmes d’exploitation spécifiques, y compris des variations au sein de la même famille, telles que Windows 10 et Windows 11. Pour plus d’informations, consultez Gestion des vulnérabilités Microsoft Defender (MDVM) pris en charge par les systèmes d’exploitation et les plateformes.|Windows 10 et Windows 11
RbacGroupName|string|Groupe de contrôle d’accès en fonction du rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur est « Non affecté ». Si l’organisation ne contient aucun groupe RBAC, la valeur est « None ».|Serveurs
RecommandationReference|string|Référence à l’ID de recommandation associé à ce logiciel.|sca-_-scid-20000
Timestamp|string|Dernière fois que la configuration a été vue sur l’appareil|2020-11-03 10:13:34.8476880
|

### <a name="16-examples"></a>1.6 Exemples

#### <a name="161-request-example"></a>Exemple de demande 1.6.1

```http
GET https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentByMachine?pageSize=5
```

#### <a name="162-response-example"></a>1.6.2 Exemple de réponse

```json
{
    "@odata.context": "api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetConfiguration)",
    "value": [
        {
            "deviceId": "00013ee62c6b12345b10214e1801b217b50ab455c293d",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_5d96860d69c73fdd06fc8d1679e1eb73eceb8330",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "NT kernel 6.x",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol - Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "0002a1be533813b9a8c6de739785365bce7910",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-20000",
            "configurationCategory": "Security controls",
            "configurationSubcategory": "Onboard Devices",
            "configurationImpact": 9,
            "isCompliant": false,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Onboard devices to Microsoft Defender for Endpoint",
            "recommendationReference": "sca-_-scid-20000"
        },
        {
            "deviceId": "0002a1de123456a8c06de736785395d4ce7610",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol - Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "00044f912345bdaf756492dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663d45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-39",
            "configurationCategory": "OS",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Enable 'Domain member: Digitally sign secure channel data (when possible)'",
            "recommendationReference": "sca-_-scid-39"
        },
        {
            "deviceId": "00044f912345daf759462bde6bd733d6a9c56ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45612eeb224d2de2f5ea3142726e63f16a.DomainPII_21eed80d086e76dbfa178eadfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-6093",
            "configurationCategory": "Security controls",
            "configurationSubcategory": "Antivirus",
            "configurationImpact": 5,
            "isCompliant": false,
            "isApplicable": false,
            "isExpectedUserImpact": false,
            "configurationName": "Enable Microsoft Defender Antivirus real-time behavior monitoring for Linux",
            "recommendationReference": "sca-_-scid-6093"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-secure-configuration-assessment-via-files"></a>2. Exporter l’évaluation de la configuration sécurisée (via des fichiers)

### <a name="21-api-method-description"></a>Description de la méthode API 2.1

Cette réponse d’API contient l’évaluation de la configuration sécurisée sur vos appareils exposés et retourne une entrée pour chaque combinaison unique de DeviceId, ConfigurationId.

#### <a name="211-limitations"></a>2.1.1 Limitations

Les limites de débit pour cette API sont de 5 appels par minute et de 20 appels par heure.

### <a name="22-permissions"></a>2.2 Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
---|---|---
Application|Vulnerability.Read.All|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'
Déléguée (compte professionnel ou scolaire)|Vulnerability.Read|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'

### <a name="23-url"></a>URL 2.3

```http
GET /api/machines/SecureConfigurationsAssessmentExport
```

### <a name="parameters"></a>Parameters

- sasValidHours : nombre d’heures pendant lesquelles les URL de téléchargement sont valides (maximum 24 heures).

### <a name="25-properties"></a>2.5 Propriétés

> [!NOTE]
>
> - Les fichiers sont compressés par gzip & au format Json multiligne.
> - Les URL de téléchargement ne sont valides que pendant 3 heures ; sinon, vous pouvez utiliser le paramètre.
> - Pour une vitesse de téléchargement maximale de vos données, vous pouvez vous assurer que vous téléchargez à partir de la même région Azure dans laquelle se trouvent vos données.

<br>

****

Propriété (ID)|Type de données|Description|Exemple de valeur retournée
---|---|---|---
Exporter des fichiers|chaîne de tableau\[\]|Liste des URL de téléchargement pour les fichiers contenant l’instantané actuel de l’organisation|["Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|string|Heure à laquelle l’exportation a été générée.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Exemples

#### <a name="261-request-example"></a>2.6.1 Exemple de requête

```http
GET https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentExport
```

#### <a name="262-response-example"></a>2.6.2 Exemple de réponse

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#contoso.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>Voir aussi

- [Exporter des méthodes et des propriétés d’évaluation par appareil](get-assessment-methods-properties.md)
- [Exporter l’évaluation de l’inventaire logiciel par appareil](get-assessment-software-inventory.md)
- [Exporter l’évaluation des vulnérabilités logicielles par appareil](get-assessment-software-vulnerabilities.md)

Autres éléments connexes

- [Gestion des vulnérabilités Microsoft Defender](next-gen-threat-and-vuln-mgt.md)
- [Vulnérabilités dans votre organisation](tvm-weaknesses.md)
