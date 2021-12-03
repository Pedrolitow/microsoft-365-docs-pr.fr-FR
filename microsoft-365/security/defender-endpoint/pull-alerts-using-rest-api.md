---
title: Détecter Microsoft Defender pour les points de terminaison à l’aide de l’API REST
description: Découvrez comment appeler un point de terminaison de l’API Microsoft Defender for Endpoint pour tirer les détections au format JSON à l’aide de l’API REST SIEM.
keywords: détections, détections de pull, api rest, demande, réponse
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: f4f5dbcde4a80b01c3df7ee7c32b41afc89dbba6
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2021
ms.locfileid: "61301005"
---
# <a name="pull-microsoft-defender-for-endpoint-detections-using-siem-rest-api"></a>Détecter Microsoft Defender pour les points de terminaison à l’aide de l’API REST SIEM

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

> [!NOTE]
>
> - [Microsoft Defender pour l’alerte de point de terminaison](alerts.md) se compose d’une ou de plusieurs détections.
> - [Microsoft Defender pour la détection des points](api-portal-mapping.md) de terminaison est composé de l’événement suspect qui s’est produit sur l’appareil et de ses détails d’alerte associés.
> s-The Microsoft Defender for Endpoint Alert API is the latest API for alert consumption and contain a detailed list of related evidence for each alert. Pour plus d’informations, voir [Méthodes et propriétés d’alerte et](alerts.md) Liste des [alertes.](get-alerts.md)

Microsoft Defender pour le point de terminaison prend en charge le protocole OAuth 2.0 pour tirer les détections de l’API.

En règle générale, le protocole OAuth 2.0 prend en charge quatre types de flux :

- Flux d’octroi d’autorisation
- Flux implicite
- Flux d’informations d’identification du client
- Flux du propriétaire de la ressource

Pour plus d’informations sur les spécifications OAuth, voir le site [web OAuth.](http://www.oauth.net)

Microsoft Defender pour le  point de terminaison prend en charge le flux d’octroi d’autorisation et le flux d’informations d’identification du _client_ pour obtenir l’accès aux détections de pull, avec Azure Active Directory (AAD) comme serveur d’autorisation.

Le _flux d’octroi d’autorisation_ utilise les informations d’identification de l’utilisateur pour obtenir un code d’autorisation, qui est ensuite utilisé pour obtenir un jeton d’accès.

Le _flux d’informations d’identification_ du client utilise les informations d’identification du client pour s’authentifier par rapport à l’URL du point de terminaison Microsoft Defender for Endpoint. Ce flux convient aux scénarios où un client OAuth crée des demandes à une API qui ne nécessite pas d’informations d’identification utilisateur.

Utilisez la méthode suivante dans l’API Microsoft Defender for Endpoint pour tirer les détections au format JSON.

> [!NOTE]
> Centre de sécurité Microsoft Defender fusionne des détections d’alertes similaires en une seule alerte. Cette API tire les détections d’alertes dans sa forme brute en fonction des paramètres de requête que vous définissez, ce qui vous permet d’appliquer vos propres regroupements et filtrages.

## <a name="before-you-begin"></a>Avant de commencer

- Avant d’appeler le point de terminaison Microsoft Defender pour le point de terminaison pour tirer les détections, vous devez activer l’application d’intégration SIEM dans Azure Active Directory (AAD). Pour plus d’informations, voir [Enable SIEM integration in Microsoft Defender for Endpoint](enable-siem-integration.md).

- Prenez note des valeurs suivantes dans l’inscription de votre application Azure. Ces valeurs sont nécessaires pour configurer le flux OAuth dans votre application de service ou de démon.
  - ID d’application (unique pour votre application)
  - Clé d’application ou question secrète de l’application (unique pour votre application)
  - Point de terminaison du jeton OAuth 2.0 de votre application
    - Recherchez cette valeur en cliquant sur **Points de terminaison** en bas du portail de gestion Azure dans la page de votre application. Le point de terminaison ressemblera à `https://login.microsoftonline.com/{tenantId}/oauth2/token`.

## <a name="get-an-access-token"></a>Obtenir un jeton d’accès

Avant de créer des appels au point de terminaison, vous devez obtenir un jeton d’accès.

Vous utiliserez le jeton d’accès pour accéder à la ressource protégée, c’est-à-dire les détections dans Microsoft Defender pour le point de terminaison.

Pour obtenir un jeton d’accès, vous devez faire une demande POST au point de terminaison émettant le jeton. Voici un exemple de requête :

```http
POST /72f988bf-86f1-41af-91ab-2d7cd011db47/oauth2/token HTTP/1.1
Host: login.microsoftonline.com
Content-Type: application/x-www-form-urlencoded

resource=https%3A%2F%2Fgraph.windows.net&client_id=35e0f735-5fe4-4693-9e68-3de80f1d3745&client_secret=IKXc6PxB2eoFNJ%2FIT%2Bl2JZZD9d9032VXz6Ul3D2WyUQ%3D&grant_type=client_credentials
```

La réponse inclura un jeton d’accès et des informations sur l’expiration.

```json
{
  "token_type": "Bearer",
  "expires_in": 3599,
  "ext_expires_in": 0,
  "expires_on": 1488720683,
  "not_before": 1488720683,
  "resource": "https://graph.windows.net",
  "access_token":"eyJ0eXaioJJOIneiowiouqSuzNiZ345FYOVkaJL0625TueyaJasjhIjEnbMlWqP..."
}
```

Vous pouvez désormais utiliser la valeur dans le *champ access_token* dans une demande à l’API Defender for Endpoint.

## <a name="request"></a>Demande

Avec un jeton d’accès, votre application peut effectuer des demandes authentifiées à l’API Microsoft Defender for Endpoint. Votre application doit ajouter le jeton d’accès à l’en-tête Authorization de chaque demande.

### <a name="request-syntax"></a>Syntaxe de la requête

Méthode|URI de demande
---|---
GET|Utilisez l’URI applicable pour votre région. <p> **Pour l’UE**: `https://wdatp-alertexporter-eu.windows.com/api/alerts` <p> **Pour les États-Unis**: `https://wdatp-alertexporter-us.windows.com/api/alerts` <p> **Pour le Royaume-Uni**: `https://wdatp-alertexporter-uk.windows.com/api/alerts`

### <a name="request-header"></a>En-tête de demande

En-tête|Type|Description|
---|---|---
Autorisation|string|Obligatoire. Le Azure AD’accès au formulaire sous forme **de jeton du** &lt; *porteur.* &gt;|

### <a name="request-parameters"></a>Paramètres de la requête

Utilisez des paramètres de requête facultatifs pour spécifier et contrôler la quantité de données renvoyées dans une réponse. Si vous appelez cette méthode sans paramètres, la réponse contient toutes les alertes de votre organisation au cours des 2 dernières heures.

Nom|Valeur|Description
---|---|---
sinceTimeUtc|Date/heure|Définit les alertes liées au temps inférieur à partir de, en fonction du champ : <p> `LastProcessedTimeUtc` <p> L’intervalle de temps sera : de l’heure sinceTimeUtc à l’heure actuelle. <p> **REMARQUE**: lorsqu’elle n’est pas spécifiée, toutes les alertes générées au cours des deux dernières heures sont récupérées.
untilTimeUtc|Date/heure|Définit les alertes liées au temps supérieur qui sont récupérées. <p> L’plage de temps est : de `sinceTimeUtc` temps en `untilTimeUtc` temps. <p> **REMARQUE**: lorsqu’elle n’est pas spécifiée, la valeur par défaut est l’heure actuelle.
ago|string|Pulls alerts in the following time range: from `(current_time - ago)` time to `current_time` time. <p> La valeur doit être définie selon le format de durée **ISO 8601** <p> Exemple : `ago=PT10M` tirera les alertes reçues au cours des 10 dernières minutes.
limit|int|Définit le nombre d’alertes à récupérer. Les alertes les plus récentes sont récupérées en fonction du nombre défini.<p> **REMARQUE**: lorsqu’elle n’est pas spécifiée, toutes les alertes disponibles dans l’plage de temps sont récupérées.
machinegroups|string|Spécifie les groupes d’appareils à partir des appareils à partir des alertes. <p> **REMARQUE**: lorsqu’elle n’est pas spécifiée, les alertes de tous les groupes d’appareils sont récupérées. <p> Exemple : <br><br> `https://wdatp-alertexporter-eu.securitycenter.windows.com/api/alerts/?machinegroups=UKMachines&machinegroups=FranceMachines`
DeviceCreatedMachineTags|string|Balise d’appareil unique à partir du Registre.
CloudCreatedMachineTags|string|Balises de périphérique créées dans Centre de sécurité Microsoft Defender.

### <a name="request-example"></a>Exemple de requête

L’exemple suivant montre comment récupérer toutes les détections dans votre organisation.

```http
GET  https://wdatp-alertexporter-eu.windows.com/api/alerts
Authorization: Bearer <your access token>
```

L’exemple suivant illustre une demande d’obtenir les 20 dernières détections depuis 2016-09-12 00:00:00.

```http
GET  https://wdatp-alertexporter-eu.windows.com/api/alerts?limit=20&sinceTimeUtc=2016-09-12T00:00:00.000
Authorization: Bearer <your access token>
```

## <a name="response"></a>Réponse

La valeur de retour est un tableau d’objets d’alerte au format JSON.

Voici un exemple de valeur de retour :

```json
[
{
        "AlertTime": "2020-09-30T14:09:20.35743Z",
        "ComputerDnsName": "mymachine1.domain.com",
        "AlertTitle": "Suspicious File Activity",
        "Category": "Malware",
        "Severity": "High",
        "AlertId": "da637370718981685665_16349121",
        "Actor": "",
        "LinkToWDATP": "https://securitycenter.windows.com/alert/da637370718981685665_16349121",
        "IocName": "",
        "IocValue": "",
        "CreatorIocName": "",
        "CreatorIocValue": "",
        "Sha1": "aabbccddee1122334455aabbccddee1122334455",
        "FileName": "cmdParent.exe",
        "FilePath": "C:\\WINDOWS\\SysWOW64\\boo3\\qwerty",
        "IpAddress": "",
        "Url": "",
        "IoaDefinitionId": "b20af1d2-5990-4672-87f1-acc2a8ff7725",
        "UserName": "",
        "AlertPart": 0,
        "FullId": "da637370718981685665_16349121:R4xEdgAvDb2LQl3BgHoA3NYqKmRSiIAG7dpxAJCYZhY=",
        "LastProcessedTimeUtc": "2020-09-30T14:11:44.0779765Z",
        "ThreatCategory": "",
        "ThreatFamily": "",
        "ThreatName": "",
        "RemediationAction": "",
        "RemediationIsSuccess": null,
        "Source": "EDR",
        "Md5": "854b85cbff2752fcb88606bca76f83c6",
        "Sha256": "",
        "WasExecutingWhileDetected": null,
        "UserDomain": "",
        "LogOnUsers": "",
        "MachineDomain": "domain.com",
        "MachineName": "mymachine1",
        "InternalIPv4List": "",
        "InternalIPv6List": "",
        "FileHash": "aabbccddee1122334455aabbccddee1122334455",
        "DeviceID": "deadbeef000040830ee54503926f556dcaf82bb0",
        "MachineGroup": "",
        "Description": "Test Alert",
        "DeviceCreatedMachineTags": "",
        "CloudCreatedMachineTags": "",
        "CommandLine": "",
        "IncidentLinkToWDATP": "https://securitycenter.windows.com/incidents/byalert?alertId=da637370718981685665_16349121&source=SIEM",
        "ReportID": 1053729833,
        "LinkToMTP": "https://security.microsoft.com/alert/da637370718981685665_16349121",
        "IncidentLinkToMTP": "https://security.microsoft.com/incidents/byalert?alertId=da637370718981685665_16349121&source=SIEM",
        "ExternalId": "31DD0A845DDA4059FDEDE031014645350AECABD3",
        "IocUniqueId": "R4xEdgAvDb2LQl3BgHoA3NYqKmRSiIAG7dpxAJCYZhY="
}
]
```

## <a name="code-examples"></a>Exemples de code

### <a name="get-access-token"></a>Obtenir un jeton d’accès

Les exemples de code suivants montrent comment obtenir un jeton d’accès pour appeler l’API SIEM de Microsoft Defender for Endpoint.

```csharp
AuthenticationContext context = new AuthenticationContext(string.Format("https://login.microsoftonline.com/{0}", tenantId));
ClientCredential clientCredentials = new ClientCredential(clientId, clientSecret);
AuthenticationResult authenticationResult = context.AcquireTokenAsync(detectionsResource, clientCredentials).GetAwaiter().GetResult();
```

```PowerShell
#Get current working directory
$scriptDir = Split-Path -Path $MyInvocation.MyCommand.Definition -Parent

#Paste below your Tenant ID, App ID and App Secret (App key).
$tenantId = '' ### Paste your tenant ID here
$appId = '' ### Paste your Application ID here
$appSecret = '' ### Paste your Application secret here

$resourceAppIdUri = 'https://graph.windows.net'
$oAuthUri = "https://login.microsoftonline.com/$tenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}

#call API
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$authResponse
Out-File -FilePath "$scriptDir\LatestSIEM-token.txt" -InputObject $authResponse.access_token
```

```Bash
tenantId='' ### Paste your tenant ID here
appId='' ### Paste your Application ID here
appSecret='' ### Paste your Application secret here
resourceAppIdUri='https://graph.windows.net'
oAuthUri="https://login.microsoftonline.com/$tenantId/oauth2/token"
scriptDir=$(pwd)

apiResponse=$(curl -s X POST "$oAuthUri" -d "resource=$resourceAppIdUri&client_id=$appId&client_secret=$appSecret&\
        grant_type=client_credentials"|cut -d "{" -f2|cut -d "}" -f1)
IFS=","
apiResponseArr=($apiResponse)
IFS=":"
tokenArr=(${apiResponseArr[6]})
echo ${tokenArr[1]}|cut -d "\"" -f2|cut -d "\"" -f1 >> $scriptDir/LatestSIEM-token.txt
```

### <a name="use-token-to-connect-to-the-detections-endpoint"></a>Utiliser un jeton pour se connecter au point de terminaison des détections

Les exemples de code suivants montrent comment utiliser un jeton d’accès pour appeler l’API SIEM Defender for Endpoint pour obtenir des alertes.

```csharp
HttpClient httpClient = new HttpClient();
httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue(authenticationResult.AccessTokenType, authenticationResult.AccessToken);
HttpResponseMessage response = httpClient.GetAsync("https://wdatp-alertexporter-eu.windows.com/api/alert").GetAwaiter().GetResult();
string detectionsJson = response.Content.ReadAsStringAsync().Result;
Console.WriteLine("Got detections list: {0}", detectionsJson);
```

```PowerShell
#Get current working directory
$scriptDir = Split-Path -Path $MyInvocation.MyCommand.Definition -Parent

#run the script Get-Token.ps1  - make sure you are running this script from the same folder of Get-SIEMToken.ps1
$token = Get-Content "$scriptDir\LatestSIEM-token.txt"

#Get Alert from the last xx hours 200 in this example. Make sure you have alerts in that time frame.
$dateTime = (Get-Date).ToUniversalTime().AddHours(-200).ToString("o")

#test SIEM API
$url = 'https://wdatp-alertexporter-us.windows.com/api/alerts?limit=20&sinceTimeUtc=2020-01-01T00:00:00.000'

#Set the WebRequest headers
$headers = @{
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $token"
}

#Send the webrequest and get the results.
$response = Invoke-WebRequest -Method Get -Uri $url -Headers $headers -ErrorAction Stop
$response
Write-Host

#Extract the alerts from the results. This works for SIEM API:
$alerts =  $response.Content|ConvertFrom-Json|ConvertTo-Json

#Get string with the execution time. We concatenate that string to the output file to avoid overwrite the file
$dateTimeForFileName = Get-Date -Format o|foreach {$_ -replace ":", "."}

#Save the result as json and as csv
$outputJsonPath = "$scriptDir\Latest Alerts $dateTimeForFileName.json"
$outputCsvPath = "$scriptDir\Latest Alerts $dateTimeForFileName.csv"

Out-File -FilePath $outputJsonPath -InputObject $alerts
Get-Content -Path $outputJsonPath -Raw|ConvertFrom-Json|Select-Object -ExpandProperty value|Export-CSV $outputCsvPath -NoTypeInformation
```

```Bash
#Get current working directory
scriptDir=$(pwd)

#get the token
token=$(<$scriptDir/LatestSIEM-token.txt)

#test the SIEM API, get alerts since 1/1/2020
url='https://wdatp-alertexporter-us.windows.com/api/alerts?limit=20&sinceTimeUtc=2020-01-01T00:00:00.000'

#send web requst to API and echo JSON content
apiResponse=$(curl -s X GET "$url" -H "Content-Type: application/json" -H "Accept: application/json"\
         -H "Authorization: Bearer $token"|cut -d "[" -f2|cut -d "]" -f1)
echo "If you see Alert info in JSON format, congratulations you accessed the MDATP SIEM API!"
echo
echo $apiResponse
```

## <a name="error-codes"></a>Codes d’erreur

L’API REST Microsoft Defender pour point de terminaison renvoie les codes d’erreur suivants causés par une demande non valide.

Code d’erreur HTTP|Description
---|---
401|Demande incorrecte ou jeton non valide.
403|Exception non autorisée : l’un des domaines n’est pas géré par l’administrateur client ou l’état du client est supprimé.
500|Erreur dans le service.

## <a name="related-topics"></a>Voir aussi

- [Activer l’intégration SIEM dans Microsoft Defender pour endpoint](enable-siem-integration.md)
- [Configurer ArcSight pour tirer Microsoft Defender pour les détections de points de terminaison](configure-arcsight.md)
- [Tirer les détections vers vos outils SIEM](configure-siem.md)
- [Champs Microsoft Defender pour la détection des points de terminaison](api-portal-mapping.md)
- [Résoudre des problèmes d’intégration de l’outil SIEM](troubleshoot-siem.md)
