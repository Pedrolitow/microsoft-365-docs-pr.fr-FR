---
title: Exporter l’évaluation des extensions de navigateur
description: Retourne une table avec une entrée pour chaque combinaison unique de DeviceId, BrowserName, ExtensionID.
keywords: api, api, évaluation des exportations, évaluation par appareil, rapport d’évaluation des vulnérabilités, évaluation des vulnérabilités des appareils, rapport de vulnérabilité des appareils, évaluation des extensions de navigateur
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: b4830362aa975274651a27568fa1221d1ef0bc41
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67696856"
---
# <a name="export-browser-extensions-assessment-per-device"></a>Exporter l’évaluation des extensions de navigateur par appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des vulnérabilités de Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> Vous voulez découvrir Gestion des vulnérabilités Microsoft Defender ? En savoir plus sur la façon dont vous pouvez vous inscrire à la [Gestion des vulnérabilités Microsoft Defender préversion publique](../defender-vulnerability-management/get-defender-vulnerability-management.md).

Retourne toutes les extensions de navigateur installées connues et leurs détails pour tous les appareils, sur une base par appareil.

Les différents appels d’API obtiennent différents types de données. Étant donné que la quantité de données peut être importante, il existe deux façons de les récupérer :

- [Exporter la **réponse JSON** d’évaluation des extensions de navigateur](#1-export-browser-extensions-assessment-json-response) L’API extrait toutes les données de votre organisation en tant que réponses Json. Cette méthode est idéale pour _les petites organisations avec moins de 100 K d’appareils_. La réponse étant paginée, vous pouvez utiliser le \@champ odata.nextLink de la réponse pour extraire les résultats suivants.

- [Exporter l’évaluation des extensions **de navigateur via des fichiers**](#2-export-browser-extension-assessment-via-files) Cette solution d’API permet d’extraire de plus grandes quantités de données plus rapidement et de manière plus fiable. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 000 appareils. Cette API extrait toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir du stockage Azure. Cette API vous permet de télécharger toutes vos données à partir du Stockage Azure comme suit :
  - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.
  - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traitez les données comme vous le souhaitez.

Les données collectées (à l’aide d’une _réponse Json_ ou _de fichiers_) sont l’instantané actuel de l’état actuel. Il ne contient pas de données historiques. Pour collecter des données historiques, les clients doivent enregistrer les données dans leurs propres stockages de données.

> [!NOTE]
> Sauf indication contraire, toutes les méthodes d’évaluation d’exportation répertoriées sont **_l’exportation complète_** et **_par appareil_** (également appelée **_par appareil_**).

## <a name="1-export-browser-extensions-assessment-json-response"></a>1. Exporter l’évaluation des extensions de navigateur (réponse JSON)

### <a name="11-api-method-description"></a>Description de la méthode d’API 1.1

Cette réponse d’API contient toutes les données pour les extensions de navigateur installées par appareil. Retourne une table avec une entrée pour chaque combinaison unique de DeviceId, BrowserName, ExtensionId.

#### <a name="111-limitations"></a>1.1.1 Limitations

- La taille maximale de la page est de 200 000.
- Les limites de débit pour cette API sont de 30 appels par minute et de 1 000 appels par heure.

### <a name="12-permissions"></a>1.2 Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Software.Read.All|« Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire)|Software.Read|« Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »

### <a name="13-url"></a>URL 1.3

```http
GET api/Machines/BrowserExtensionsInventoryByMachine
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

Propriété (ID)|Type de données|Description
:---|:---|:---
BrowserName|chaîne|Nom du navigateur dans lequel l’extension est installée.
DeviceId|chaîne|Identificateur unique de l’appareil.
DeviceName|string|Nom de domaine complet (FQDN) de l’appareil.
ExtensionDescription|string| Description d’une extension de navigateur spécifique.
ExtensionId|chaîne|Identificateur unique pour une extension de navigateur spécifique.
ExtensionName|chaîne|Nom d’une extension de navigateur spécifique.
ExtensionRisk|string|Niveau de risque le plus élevé généré par l’extension de navigateur. Les valeurs possibles sont : « None », « Low », « Medium », « High », « Critical ».
ExtensionVersion|string|Numéro de version d’une extension de navigateur spécifique.
IsActivated|Boolean|Indique si une extension de navigateur est active.
RbacGroupId|entier|ID de groupe de contrôle d’accès en fonction du rôle (RBAC).
RbacGroupName|chaîne|Groupe de contrôle d’accès en fonction du rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur est « Non affecté ». Si l’organisation ne contient aucun groupe RBAC, la valeur est « None ».
InstallationTime|string|Heure d’installation de l’extension de navigateur.
Autorisations|Array[string]|Ensemble d’autorisations demandé par une extension de navigateur spécifique.

### <a name="16-examples"></a>1.6 Exemples

#### <a name="161-request-example"></a>Exemple de demande 1.6.1

```http
GET https://api.securitycenter.microsoft.com/api/Machines/BrowserExtensionsInventoryByMachine?pageSize=5  &sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="162-response-example"></a>1.6.2 Exemple de réponse

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(contoso.windowsDefenderATP.api.AssetSoftware)",
    "value": [
        {
            "DeviceId": "1c32162b42e9efa1f5de42f951775f22f435c997",
            "DeviceName": "computerpii_1363c2e016e2225cb03974df58f14e6968067aa8.domainpii_f260e982985f7e8eee198b4332e0ae5b2a069cd6.corp.microsoft.com",
            "RbacGroupId": 86,
            "RbacGroupName": "UnassignedGroup",
            "InstallationTime": "2022-05-26T18:46:27.000Z",
            "BrowserName": "chrome",
            "ExtensionId": "dkpejdfnpdkhifgbancbammdijojoffk",
            "ExtensionName": "Logitech Smooth Scrolling",
            "ExtensionDescription": "Buttery-smooth scrolling for Logitech mice and touchpads.",
            "ExtensionVersion": "6.65.62",
            "ExtensionRisk": "High",
            "IsActivated": true,
            "Permissions": [
                        {
                                    "Id": "tabs",
                                    "IsRequired": true,
                                    "Risk": "High"
                        },
                        {
                                    "Id": http://*/*,
                                    "IsRequired": true,
                                    "Risk": "High"
                        },
                        {
                                    "Id": https://*/*,
                                    "IsRequired": true,
                                    "Risk": "High"
                        }
            ]
}
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/Machines/BrowserExtensionsInventoryByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0yNS8wMjAwLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-browser-extension-assessment-via-files"></a>2. Exporter l’évaluation de l’extension de navigateur (via des fichiers)

### <a name="21-api-method-description"></a>Description de la méthode API 2.1

Cette réponse d’API contient toutes les données pour les extensions de navigateur installées par appareil. Retourne une table avec une entrée pour chaque combinaison unique de DeviceId, BrowserName, ExtensionId.

#### <a name="211-limitations"></a>2.1.1 Limitations

Les limites de débit pour cette API sont de 5 appels par minute et de 20 appels par heure.

### <a name="22-permissions"></a>2.2 Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Software.Read.All|« Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire)|Software.Read|« Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »

### <a name="23-url"></a>URL 2.3

```http
GET /api/Machines/BrowserExtensionsInventoryByMachine
```

### <a name="24-parameters"></a>2.4 Paramètres

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

### <a name="26-examples"></a>2.6 Exemples

#### <a name="261-request-example"></a>2.6.1 Exemple de requête

```http
GET https://api.securitycenter.microsoft.com/api/machines/BrowserExtensionsExport
```

#### <a name="262-response-example"></a>2.6.2 Exemple de réponse

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/BrowserExtensions/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/BrowserExtensions/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/BrowserExtensions/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>Voir aussi

- [Obtenir les informations d’autorisation des extensions de navigateur](get-browser-extensions-permission-info.md)
- [Évaluation des extensions de navigateur](../defender-vulnerability-management/tvm-browser-extensions.md)

## <a name="other-related"></a>Autres éléments connexes

- [Gestion des vulnérabilités](../defender-vulnerability-management/defender-vulnerability-management.md)
- [Vulnérabilités dans votre organisation](../defender-vulnerability-management/tvm-weaknesses.md)
