---
title: Méthodes et propriétés d’évaluation de la base de référence de sécurité par appareil
description: Fournit des informations sur les API de base de référence de sécurité qui extraient des données « Gestion des vulnérabilités Microsoft Defender ». Il existe différents appels d’API pour obtenir différents types de données. En général, chaque appel d’API contient les données requises pour les appareils de votre organisation.
keywords: api, api, évaluation d’exportation, évaluation par appareil, évaluation par ordinateur, rapport d’évaluation des vulnérabilités, évaluation des vulnérabilités des appareils, rapport de vulnérabilité des appareils, évaluation de la configuration sécurisée, rapport de configuration sécurisée, évaluation des vulnérabilités logicielles, rapport de vulnérabilité logicielle, rapport de vulnérabilité par ordinateur,
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
- tier2
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 06bdb86961a797b4ca30392e292101cc9e706f99
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68203616"
---
# <a name="export-security-baselines-assessment-per-device"></a>Exporter l’évaluation des bases de référence de sécurité par appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des vulnérabilités de Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Gestion des vulnérabilités Microsoft Defender ? En savoir plus sur la façon dont vous pouvez vous inscrire à la [Gestion des vulnérabilités Microsoft Defender préversion publique](../defender-vulnerability-management/get-defender-vulnerability-management.md).

Il existe différents appels d’API pour obtenir différents types de données. En général, chaque appel d’API contient les données requises pour les appareils de votre organisation.

- **Réponse JSON**  L’API extrait toutes les données de votre organisation en tant que réponses JSON. Cette méthode est idéale pour _les petites organisations avec moins de 100 K d’appareils_. La réponse étant paginée, vous pouvez utiliser le \@champ odata.nextLink de la réponse pour extraire les résultats suivants.

- **via des fichiers** Cette solution d’API permet d’extraire de plus grandes quantités de données plus rapidement et de manière plus fiable. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 000 appareils. Cette API extrait toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir du stockage Azure. Vous pouvez télécharger des données à partir du Stockage Azure comme suit :
  - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.
  - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traitez les données comme vous le souhaitez.

Les données collectées à l’aide de la _« réponse JSON_ ou _par le biais de fichiers_ » sont l’instantané actuel de l’état actuel. Il ne contient pas de données historiques. Pour collecter des données historiques, les clients doivent enregistrer les données dans leurs propres stockages de données.

> [!NOTE]
> Sauf indication contraire, toutes les méthodes d’évaluation de la base de référence de sécurité d’exportation répertoriées sont **_des méthodes d’exportation complètes_** et **_par appareil_** (également appelées **_par appareil_**)

## <a name="1-export-security-baselines-assessment-json-response"></a>1. Exporter l’évaluation des bases de référence de sécurité (réponse JSON)

### <a name="11-api-method-description"></a>Description de la méthode d’API 1.1

Retourne toutes les évaluations des bases de référence de sécurité pour tous les appareils, sur une base par appareil. Elle retourne une table avec une entrée distincte pour chaque combinaison unique de DeviceId, ProfileId et ConfigurationId.

### <a name="12-permissions"></a>1.2 Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md) pour plus d’informations.

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|SecurityBaselinesAssessment.Read.All |« Lire toutes les informations d’évaluation des bases de référence de sécurité »
Déléguée (compte professionnel ou scolaire)|SecurityBaselinesAssessment.Read|« Lire les informations d’évaluation des bases de référence de sécurité »

### <a name="13-limitations"></a>1.3 Limitations

- La taille maximale de la page est de 200 000.
- Les limites de débit pour cette API sont de 30 appels par minute et de 1 000 appels par heure.

### <a name="14-parameters"></a>1.4 Paramètres

- pageSize (valeur par défaut = 50 000) : nombre de résultats en réponse.
- $top : nombre de résultats à retourner (ne retourne pas @odata.nextLink et n’extrait donc pas toutes les données).

### <a name="15-http-request"></a>1.5 Requête HTTP

```http
GET /api/machines/baselineComplianceAssessmentByMachine
```

### <a name="16-properties-json-response"></a>1.6 Propriétés (réponse JSON)

> [!NOTE]
> Chaque enregistrement est d’environ 1 Ko de données. Vous devez en tenir compte lors du choix du paramètre pageSize correct.
>
> Certaines colonnes supplémentaires peuvent être retournées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.
>
> Les propriétés définies dans le tableau suivant sont répertoriées par ordre alphabétique par ID de propriété. Lors de l’exécution de cette API, la sortie résultante ne sera pas nécessairement retournée dans le même ordre que celui répertorié dans ce tableau.

Propriété (ID)|Type de données|Description
:---|:---|:---
|configurationId|Chaîne|Identificateur unique pour une configuration spécifique dans le benchmark de référence.
|profileId|Chaîne|Identificateur unique pour le profil évalué.
|deviceId|Chaîne|Identificateur unique de l’appareil dans le service.
|deviceName|Chaîne|Nom de domaine complet (FQDN) de l’appareil.
|isApplicable|Boolean|Indique si la configuration s’applique à cet appareil.
|isCompliant|Boolean|Indique si l’appareil est conforme à la configuration.
|id|Chaîne|Identificateur unique de l’enregistrement, qui est une combinaison de DeviceId, ProfileId et ConfigurationId.
|osVersion|Chaîne|Version spécifique du système d’exploitation en cours d’exécution sur l’appareil.
|osPlatform|Chaîne|Plateforme de système d’exploitation s’exécutant sur l’appareil. Systèmes d’exploitation spécifiques avec des variantes au sein de la même famille, telles que Windows 10 et Windows 11. Pour plus d’informations, consultez les [systèmes d’exploitation et plateformes pris en charge par MDVM](tvm-supported-os.md) .
|rbacGroupId|Int|ID de groupe de contrôle d’accès en fonction du rôle (RBAC). Si l’appareil n’est affecté à aucun groupe RBAC, la valeur est « Non affecté ». Si l’organisation ne contient aucun groupe RBAC, la valeur est « None ».
|rbacGroupName|Chaîne|Groupe de contrôle d’accès en fonction du rôle (RBAC). Si l’appareil n’est affecté à aucun groupe RBAC, la valeur est « Non affecté ». Si l’organisation ne contient aucun groupe RBAC, la valeur est « None ».
|DataCollectionTimeOffset|Date/heure|Heure à laquelle les données ont été collectées à partir de l’appareil. Ce champ peut ne pas apparaître si aucune donnée n’a été collectée.
|ComplianceCalculationTimeOffset|Date/heure|Heure à laquelle le calcul de l’évaluation a été effectué.
|RecommendedValue|Chaîne|Ensemble de valeurs attendues pour que le paramètre d’appareil actuel soit une réclamation.
|CurrentValue|Chaîne|Ensemble de valeurs détectées trouvées sur l’appareil.
|Source|String|Chemin d’accès du Registre ou autre emplacement utilisé pour déterminer le paramètre d’appareil actuel.

## <a name="17-example"></a>1.7 Exemple

### <a name="171-request-example"></a>Exemple de demande 1.7.1

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentByMachine
```

### <a name="172-response-example"></a>1.7.2 Exemple de réponse

```json
{
"@odata.context": " https://api.securitycenter.microsoft.com /api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetBaselineAssessment)",
"value": [
{
    "id": "0000682575d5d473e82ed4d8680425d152411251_9e1b90be-e83e-485b-a5ec-4a429412e734_1.1.1",
    "configurationId": "1.1.1",
    "deviceId": "0000682575d5d473242222425d152411251",
    "deviceName": " ComputerPII_365f5c0bb7202c163937dad3d017969b2d760eb4.DomainPII_29596 ",
    "profileId": "9e1b90be-e83e-485b-a5ec-4a429412e734",
    "osPlatform": "WindowsServer2019",
    "osVersion": "10.0.17763.2330",
    "rbacGroupId": 86,
    "rbacGroupName": "UnassignedGroup",
    "isApplicable": true,
    "isCompliant": false,
    "dataCollectionTimeOffset": "2021-12-22T00:08:02.478Z",
    "recommendedValue": [
                    "Greater than or equal '24'"
                ],
                "currentValue": [
                    "24"
                ],
                "source": [
                    "password_hist_len"
                ],
}
```

## <a name="2-export-security-baselines-assessment-via-files"></a>2. Exporter l’évaluation des bases de référence de sécurité (via des fichiers)

### <a name="21-api-method-description"></a>Description de la méthode API 2.1

Retourne toutes les évaluations des bases de référence de sécurité pour tous les appareils, sur une base par appareil. Elle retourne une table avec une entrée distincte pour chaque combinaison unique de DeviceId, ProfileId et ConfigurationId.

### <a name="22-limitations"></a>2.2 Limitations

- Les limites de débit pour cette API sont de 5 appels par minute et de 20 appels par heure.

### <a name="23-url"></a>URL 2.3

```http
GET /api/machines/BaselineComplianceAssessmentExport
```

### <a name="24-parameters"></a>2.4 Paramètres

- sasValidHours : nombre d’heures pendant lesquelles les URL de téléchargement sont valides (maximum 24 heures).

### <a name="25-properties-via-files"></a>2.5 Propriétés (via des fichiers)

> [!NOTE]
> Les fichiers sont compressés par gzip & au format Json multiligne.
>
>Les URL de téléchargement ne sont valides que pendant 3 heures ; sinon, vous pouvez utiliser le paramètre.
>
>Pour optimiser les vitesses de téléchargement, assurez-vous que vous téléchargez les données à partir de la même région Azure où se trouvent vos données.
>
>Chaque enregistrement est d’environ 1 Ko de données. Vous devez en tenir compte lors du choix du paramètre pageSize qui vous convient.
>
>Certaines colonnes supplémentaires peuvent être retournées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.

Propriété (ID)|Type de données|Description
:---|:---|:---
|Exporter des fichiers|array[string]|Liste des URL de téléchargement pour les fichiers contenant l’instantané actuel de l’organisation.
|GeneratedTime|Chaîne|Heure à laquelle l’exportation a été générée.

## <a name="26-example"></a>2.6 Exemple

### <a name="261-request-example"></a>2.6.1 Exemple de requête

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentExport
```

### <a name="262-response-example"></a>2.6.2 Exemple de réponse

```json
{
    "@odata.context": "https://api.securitycenter. contoso.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": 
    [
    "https://tvmexportexternalstgeus.blob.core.windows.net/temp-1ebd3d09-d06a-4aad-ab80-ebc536cec61c/2021-12-22/0500/BaselineAssessmentExport/json/OrgId= OrgId=<Org Id>/_RbacGroupId=<Rbac Group Id>/part-00000-c09dfd00-2278-4735-b23a-71733751fcbc.c000.json.gz?sv=ABCD",
   "https://tvmexportexternalstgeus.blob.core.windows.net/temp-1ebd3d09-d06a-4aad-ab80-ebc536cec61c/2021-12-22/0500/BaselineAssessmentExport/json/OrgId=<Org Id>/_RbacGroupId=<Rbac Group Id>/part-00001-c09dfd00-2278-4735-b23a-71733751fcbc.c000.json.gz?sv= ABCD",
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>Voir aussi

- [Obtenir les profils d’évaluation des bases de référence de sécurité](get-security-baselines-assessment-profiles.md)
- [Obtenir les configurations d’évaluation des bases de référence de sécurité](get-security-baselines-assessment-configurations.md)
