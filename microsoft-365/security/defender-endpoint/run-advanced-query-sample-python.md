---
title: Guide de repérage avancé avec l’API Python
ms.reviewer: ''
description: Découvrez comment interroger à l’aide de l’API Microsoft Defender pour point de terminaison, à l’aide de Python, avec des exemples.
keywords: api, api prises en charge, repérage avancé, requête
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
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
ms.openlocfilehash: db5e7ee445a15b98d0b871c397c3dd84a9b0e510
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68226073"
---
# <a name="advanced-hunting-using-python"></a>Repérage avancé à l’aide de Python

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Exécutez des requêtes avancées à l’aide de Python, consultez [l’API De repérage avancé](run-advanced-query-api.md).

Dans cette section, nous partageons des exemples Python pour récupérer un jeton et l’utiliser pour exécuter une requête.

> **Prérequis** : vous devez d’abord [créer une application](apis-intro.md).

## <a name="get-token"></a>Obtenir un jeton

- Exécutez les commandes suivantes :

```python
import json
import urllib.request
import urllib.parse

tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here

url = "https://login.microsoftonline.com/%s/oauth2/token" % (tenantId)

resourceAppIdUri = 'https://api.securitycenter.microsoft.com'

body = {
    'resource' : resourceAppIdUri,
    'client_id' : appId,
    'client_secret' : appSecret,
    'grant_type' : 'client_credentials'
}

data = urllib.parse.urlencode(body).encode("utf-8")

req = urllib.request.Request(url, data)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
aadToken = jsonResponse["access_token"]
```

Où

- tenantId : ID du locataire au nom duquel vous souhaitez exécuter la requête (autrement dit, la requête sera exécutée sur les données de ce locataire)
- appId : ID de votre application Azure AD (l’application doit disposer de l’autorisation « Exécuter des requêtes avancées » pour Microsoft Defender pour point de terminaison)
- appSecret : Secret de votre application Azure AD

## <a name="run-query"></a>Exécuter la requête

 Exécutez la requête suivante :

```python
query = 'DeviceRegistryEvents | limit 10' # Paste your own query here

url = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"
headers = { 
    'Content-Type' : 'application/json',
    'Accept' : 'application/json',
    'Authorization' : "Bearer " + aadToken
}

data = json.dumps({ 'Query' : query }).encode("utf-8")

req = urllib.request.Request(url, data, headers)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
schema = jsonResponse["Schema"]
results = jsonResponse["Results"]
```

- le schéma contient le schéma des résultats de votre requête
- les résultats contiennent les résultats de votre requête

### <a name="complex-queries"></a>Requêtes complexes

Si vous souhaitez exécuter des requêtes complexes (ou des requêtes multilignes), enregistrez votre requête dans un fichier et, au lieu de la première ligne de l’exemple ci-dessus, exécutez la commande ci-dessous :

```python
queryFile = open("D:\\Temp\\myQuery.txt", 'r') # Replace with the path to your file
query = queryFile.read()
queryFile.close()
```

## <a name="work-with-query-results"></a>Travailler avec les résultats de la requête

Vous pouvez maintenant utiliser les résultats de la requête.

Pour itérer sur les résultats, procédez comme suit :

```python
for result in results:
    print(result) # Prints the whole result
    print(result["EventTime"]) # Prints only the property 'EventTime' from the result
```

Pour générer les résultats de la requête au format CSV dans le fichier file1.csv procédez comme suit :

```python
import csv

outputFile = open("D:\\Temp\\file1.csv", 'w')
output = csv.writer(outputFile)
output.writerow(results[0].keys())
for result in results:
    output.writerow(result.values())

outputFile.close()
```

Pour générer les résultats de la requête au format JSON dans le fichier file1.json, procédez comme suit :

```python
outputFile = open("D:\\Temp\\file1.json", 'w')
json.dump(results, outputFile)
outputFile.close()
```

## <a name="related-topic"></a>Rubrique connexe

- [API Microsoft Defender pour point de terminaison](apis-intro.md)
- [API de recherche avancée de menaces](run-advanced-query-api.md)
- [Repérage avancé à l’aide de PowerShell](run-advanced-query-sample-powershell.md)
