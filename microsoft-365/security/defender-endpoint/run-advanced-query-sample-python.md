---
title: Guide de l’API de recherche avancée avec Python
ms.reviewer: ''
description: Découvrez comment interroger à l’aide de l’API Microsoft Defender for Endpoint, à l’aide de Python, avec des exemples.
keywords: api, api pris en charge, recherche avancée, requête
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 78b6097ea9c3a83f35585f3b13fec4d9056ac25a
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51199716"
---
# <a name="advanced-hunting-using-python"></a>Recherche avancée à l’aide de Python

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Exécutez des requêtes avancées à l’aide de Python, voir [API de recherche avancée.](run-advanced-query-api.md)

Dans cette section, nous partageons des exemples Python pour récupérer un jeton et l’utiliser pour exécuter une requête.

>**Conditions préalables**: vous devez d’abord [créer une application.](apis-intro.md)

## <a name="get-token"></a>Obtenir un jeton

- Exécutez les commandes suivantes :

```

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

where
- tenantId : ID du client pour le compte duquel vous souhaitez exécuter la requête (autrement dit, la requête sera exécuté sur les données de ce client)
- appId : ID de votre application Azure AD (l’application doit avoir l’autorisation « Exécuter des requêtes avancées » sur Microsoft Defender pour le point de terminaison)
- appSecret : secret de votre application Azure AD

## <a name="run-query"></a>Exécuter la requête

 Exécutez la requête suivante :

```
query = 'RegistryEvents | limit 10' # Paste your own query here

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

- contient le schéma des résultats de votre requête
- les résultats contiennent les résultats de votre requête

### <a name="complex-queries"></a>Requêtes complexes

Si vous souhaitez exécuter des requêtes complexes (ou des requêtes multilignes), enregistrez votre requête dans un fichier et, au lieu de la première ligne de l’exemple ci-dessus, exécutez la commande suivante :

```
queryFile = open("D:\\Temp\\myQuery.txt", 'r') # Replace with the path to your file
query = queryFile.read()
queryFile.close()
```

## <a name="work-with-query-results"></a>Travailler avec les résultats de la requête

Vous pouvez désormais utiliser les résultats de la requête.

Pour itérer sur les résultats, faites les choses suivantes :

```
for result in results:
    print(result) # Prints the whole result
    print(result["EventTime"]) # Prints only the property 'EventTime' from the result


```


Pour obtenir les résultats de la requête au format CSV dans un fichier, file1.csv ci-dessous :

```
import csv

outputFile = open("D:\\Temp\\file1.csv", 'w')
output = csv.writer(outputFile)
output.writerow(results[0].keys())
for result in results:
    output.writerow(result.values())

outputFile.close()
```

Pour obtenir les résultats de la requête au format JSON au file1.jssur :

```
outputFile = open("D:\\Temp\\file1.json", 'w')
json.dump(results, outputFile)
outputFile.close()
```


## <a name="related-topic"></a>Rubrique connexe
- [API Microsoft Defender pour point de terminaison](apis-intro.md)
- [API de recherche avancée de menaces](run-advanced-query-api.md)
- [Recherche avancée à l’aide de PowerShell](run-advanced-query-sample-powershell.md)
