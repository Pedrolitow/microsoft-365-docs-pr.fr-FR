---
title: Exporter l’évaluation de la configuration sécurisée par appareil
description: Renvoie une entrée pour chaque combinaison unique de DeviceId, ConfigurationId.
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
ms.openlocfilehash: ad8b2030da4fb4815eb71ca53fb2dbac67a05d79
ms.sourcegitcommit: bc64d9f619259bd0a94e43a9010aae5cffb4d6c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "53022389"
---
# <a name="export-secure-configuration-assessment-per-device"></a>Exporter l’évaluation de la configuration sécurisée par appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

>
Renvoie toutes les configurations et leur état, par appareil.

Il existe différents appels d’API pour obtenir différents types de données. Étant donné que la quantité de données peut être importante, il existe deux façons de les récupérer :

- [Exporter la réponse **JSON**](#1-export-secure-configuration-assessment-json-response)d’évaluation de la configuration sécurisée : l’API tire toutes les données de votre organisation en tant que réponses Json. Cette méthode est la meilleure pour _les petites organisations avec moins de 100 Ko d’appareils._ La réponse est paginée, afin que vous pouvez utiliser le champ odata.nextLink de la réponse \@ pour récupérer les résultats suivants.

- [Exporter l’évaluation de la configuration **sécurisée via des fichiers**](#2-export-secure-configuration-assessment-via-files): cette solution API permet d’obtenir plus de données plus rapidement et de manière plus fiable. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 K appareils. Cette API tire toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir de Azure Storage. Cette API vous permet de télécharger toutes vos données à partir Azure Storage comme suit :

  - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.

  - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traiter les données comme vous le souhaitez.

Les données collectées (à l’aide _d’OData_ ou _via_ des fichiers) sont l’instantané actuel de l’état actuel et ne contiennent pas de données historiques. Pour collecter des données historiques, les clients doivent les enregistrer dans leurs propres stockages de données.

> [!Note]
>
> Sauf indication contraire, toutes les méthodes **** d’évaluation d’exportation répertoriées sont l’exportation complète et par appareil **_(également_** appelé **_par appareil)._**

## <a name="1-export-secure-configuration-assessment-json-response"></a>1. Exporter l’évaluation de la configuration sécurisée (réponse JSON)

### <a name="11-api-method-description"></a>1.1 Description de la méthode API

Cette réponse API contient l’évaluation de la configuration sécurisée sur vos appareils exposés et renvoie une entrée pour chaque combinaison unique de DeviceId, ConfigurationId.

#### <a name="111-limitations"></a>1.1.1 Limitations

- La taille maximale de page est de 200 000.

- Les limites de taux pour cette API sont de 30 appels par minute et de 1 000 appels par heure.

### <a name="12-permissions"></a>1.2 Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point](apis-intro.md) de terminaison pour plus d’informations.

Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation
---|---|---
Application | Vulnerability.Read.All | \'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'
Déléguée (compte professionnel ou scolaire) | Vulnerability.Read | \'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SecureConfigurationsAssessmentByMachine
```

### <a name="14-parameters"></a>1.4 Paramètres

- pageSize \( par défaut = 50 000 : nombre de résultats en \) réponse

- \$top : le nombre de résultats à renvoyer ne \( retourne pas odata.nextLink et par conséquent ne tire pas \@ toutes les données\)

### <a name="15-properties"></a>1.5 Propriétés

>[!Note]
>
>- Les propriétés définies dans le tableau suivant sont répertoriées par ordre alphabétique, par ID de propriété.  Lors de l’exécution de cette API, la sortie résultante ne sera pas nécessairement renvoyée dans le même ordre que celui répertorié dans ce tableau.
>
>- Certaines colonnes supplémentaires peuvent être renvoyées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.
>

Propriété (ID) | Type de données | Description | Exemple de valeur renvoyée
:---|:---|:---|:---
ConfigurationCategory | string | Catégorie ou regroupement auquel appartient la configuration : application, système d’exploitation, réseau, comptes, contrôles de sécurité | Contrôles de sécurité
ConfigurationId | string | Identificateur unique pour une configuration spécifique | scid-10000
ConfigurationImpact | string | Impact nominal de la configuration sur la note de configuration globale (1-10) | 9 
ConfigurationName | string | Nom d’affichage de la configuration | Intégrer des appareils à Microsoft Defender pour point de terminaison
ConfigurationSubcategory | string | Sous-catégorie ou sous-groupement auquel appartient la configuration. Dans de nombreux cas, cela décrit des capacités ou des fonctionnalités spécifiques. | Appareils intégrés
DeviceId | string | Identificateur unique de l’appareil dans le service. | 9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName | string | Nom de domaine complet (FQDN) de l’appareil. | johnlaptop.europe.contoso.com
IsApplicable | bool | Indique si la configuration ou la stratégie est applicable | true
IsCompliant | bool | Indique si la configuration ou la stratégie est correctement configurée. | false
IsExpectedUserImpact | bool | Indique s’il y aura un impact sur l’utilisateur si la configuration est appliquée | true
OSPlatform | string | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. Pour plus d’informations, voir les systèmes d’exploitation et les plateformes pris en charge par tvm. | Windows 10
RbacGroupName | string | Groupe de contrôle d’accès basé sur un rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur sera « Unassigned ». Si l’organisation ne contient aucun groupe RBAC, la valeur sera « None ». | Serveurs
RecommendationReference | string | Référence à l’ID de recommandation associé à ce logiciel. | sca-_-scid-20000
Timestamp | string | Dernière fois que la configuration a été vue sur l’appareil | 2020-11-03 10:13:34.8476880

### <a name="16-examples"></a>1.6 Exemples

#### <a name="161-request-example"></a>1.6.1 Exemple de requête

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
            "osPlatform": "Windows10",
            "osVersion": "NT kernel 6.x",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol – Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "0002a1be533813b9a8c6de739785365bce7910",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol – Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "00044f912345bdaf756492dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663d45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
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

### <a name="21-api-method-description"></a>2.1 Description de la méthode API

Cette réponse API contient l’évaluation de la configuration sécurisée sur vos appareils exposés et renvoie une entrée pour chaque combinaison unique de DeviceId, ConfigurationId.

#### <a name="212-limitations"></a>2.1.2 Limitations

Les limites de taux pour cette API sont de 5 appels par minute et de 20 appels par heure.

### <a name="22-permissions"></a>2.2 Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir Utiliser Microsoft Defender pour les API de point de [terminaison pour plus d’informations.](apis-intro.md)

Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation
---|---|---
Application | Vulnerability.Read.All | \'Lire les informations Gestion des menaces et des vulnérabilités vulnérabilité « Gestion des menaces et des vulnérabilités »\'
Déléguée (compte professionnel ou scolaire) | Vulnerability.Read | \'Lire les informations Gestion des menaces et des vulnérabilités vulnérabilité « Gestion des menaces et des vulnérabilités »\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SecureConfigurationsAssessmentExport
```

### <a name="parameters"></a>Parameters

- sasValidHours : nombre d’heures pendant qui les URL de téléchargement seront valides (maximum 24 heures).

### <a name="25-properties"></a>2.5 Propriétés

>[!Note]
>
>- Les fichiers sont compressés gzip & au format Json multiligne.
>
>- Les URL de téléchargement ne sont valides que pendant 3 heures . Sinon, vous pouvez utiliser le paramètre.
>
>- Pour une vitesse de téléchargement maximale de vos données, vous pouvez vous assurer que vous téléchargez à partir de la même région Azure dans laquelle résident vos données.
>
Propriété (ID) | Type de données | Description | Exemple de valeur renvoyée
:---|:---|:---|:---
Exporter des fichiers | chaîne de \[ tableau\] | Liste des URL de téléchargement pour les fichiers qui contiennent la capture instantanée actuelle de l’organisation | [  Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2” ]
GeneratedTime | string | Heure de la générer. | 2021-05-20T08:00:00Z ]

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

- [Exporter les méthodes et propriétés d’évaluation par appareil](get-assessment-methods-properties.md)

- [Exporter l’évaluation de l’inventaire logiciel par appareil](get-assessment-software-inventory.md)

- [Exporter l’évaluation des vulnérabilités logicielles par appareil](get-assessment-software-vulnerabilities.md)

Autres associés

- [Menaces basées sur les risques & gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)

- [Vulnérabilités dans votre organisation](tvm-weaknesses.md)
