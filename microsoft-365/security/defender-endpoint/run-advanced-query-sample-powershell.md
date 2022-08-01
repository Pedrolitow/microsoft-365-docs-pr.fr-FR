---
title: Advanced Hunting with PowerShell API Basics
ms.reviewer: ''
description: Découvrez les principes de base de l’interrogation de l’API Microsoft Defender for Endpoint à l’aide de PowerShell.
keywords: api, api pris en charge, recherche avancée, requête
search.product: eADQiWindows 10XVcnh
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 24e143eae463d376275242ebf35abd78888de052
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61165977"
---
# <a name="advanced-hunting-using-powershell"></a>Repérage avancé à l’aide de PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Exécutez des requêtes avancées à l’aide de PowerShell, voir [API de recherche avancée.](run-advanced-query-api.md)

Dans cette section, nous partageons des exemples PowerShell pour récupérer un jeton et l’utiliser pour exécuter une requête.

## <a name="before-you-begin"></a>Avant de commencer
Vous devez d’abord [créer une application.](apis-intro.md)

## <a name="preparation-instructions"></a>Instructions de préparation

- Ouvrez une fenêtre PowerShell.
- Si votre stratégie ne vous permet pas d’exécuter les commandes PowerShell, vous pouvez exécuter la commande ci-dessous :
  ```
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

>Pour plus d’informations, [voir la documentation PowerShell](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Obtenir un jeton

- Exécutez la commande suivante :

```
$tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
$appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
$appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here

$resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$body = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$response = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $body -ErrorAction Stop
$aadToken = $response.access_token
```

where
- $tenantId : ID du client pour le compte duquel vous souhaitez exécuter la requête (autrement dit, la requête sera exécuté sur les données de ce client)
- $appId : ID de votre application Azure AD (l’application doit avoir l’autorisation « Exécuter des requêtes avancées » sur Defender for Endpoint)
- $appSecret : secret de votre application Azure AD web

## <a name="run-query"></a>Exécuter la requête

Exécutez la requête suivante :

```
$query = 'RegistryEvents | limit 10' # Paste your own query here

$url = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"
$headers = @{ 
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $aadToken" 
}
$body = ConvertTo-Json -InputObject @{ 'Query' = $query }
$webResponse = Invoke-WebRequest -Method Post -Uri $url -Headers $headers -Body $body -ErrorAction Stop
$response =  $webResponse | ConvertFrom-Json
$results = $response.Results
$schema = $response.Schema
```

- $results contiennent les résultats de votre requête
- $schema contient le schéma des résultats de votre requête

### <a name="complex-queries"></a>Requêtes complexes

Si vous souhaitez exécuter des requêtes complexes (ou des requêtes multilignes), enregistrez votre requête dans un fichier et, au lieu de la première ligne de l’exemple ci-dessus, exécutez la commande ci-dessous :

```
$query = [IO.File]::ReadAllText("C:\myQuery.txt"); # Replace with the path to your file
```

## <a name="work-with-query-results"></a>Travailler avec les résultats de la requête

Vous pouvez désormais utiliser les résultats de la requête.

Pour obtenir les résultats de la requête au format CSV dans le fichier, file1.csv ci-dessous :

```
$results | ConvertTo-Csv -NoTypeInformation | Set-Content file1.csv
```

Pour obtenir les résultats de la requête au format JSON dans file1.json, faites ce qui suit :

```
$results | ConvertTo-Json | Set-Content file1.json
```


## <a name="related-topic"></a>Rubrique connexe
- [API Microsoft Defender pour point de terminaison](apis-intro.md)
- [API de recherche avancée de menaces](run-advanced-query-api.md)
- [Repérage avancé à l’aide de Python](run-advanced-query-sample-python.md)
