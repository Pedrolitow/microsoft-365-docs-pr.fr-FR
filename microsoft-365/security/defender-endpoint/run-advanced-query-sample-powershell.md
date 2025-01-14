---
title: Repérage avancé avec les concepts de base de l’API PowerShell
ms.reviewer: ''
description: Découvrez les principes de base de l’interrogation de l’API Microsoft Defender pour point de terminaison à l’aide de PowerShell.
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
ms.topic: conceptual
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: b4fc422194aca1615c8a1b365ea7b9b34a67551c
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68644436"
---
# <a name="advanced-hunting-using-powershell"></a>Repérage avancé à l’aide de PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Exécutez des requêtes avancées à l’aide de PowerShell, consultez [l’API De repérage avancé](run-advanced-query-api.md).

Dans cette section, nous partageons des exemples PowerShell pour récupérer un jeton et l’utiliser pour exécuter une requête.

## <a name="before-you-begin"></a>Avant de commencer
Vous devez d’abord [créer une application](apis-intro.md).

## <a name="preparation-instructions"></a>Instructions de préparation

- Ouvrez une fenêtre PowerShell.

- Si votre stratégie ne vous permet pas d’exécuter les commandes PowerShell, vous pouvez exécuter la commande suivante :

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

Pour plus d’informations, consultez la [documentation PowerShell](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Obtenir un jeton

- Exécutez la commande suivante :

```powershell
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

Où
- $tenantId : ID du locataire pour lequel vous souhaitez exécuter la requête (autrement dit, la requête sera exécutée sur les données de ce locataire)
- $appId : ID de votre application Azure AD (l’application doit disposer de l’autorisation « Exécuter des requêtes avancées » sur Defender pour point de terminaison)
- $appSecret : Secret de votre application Azure AD

## <a name="run-query"></a>Exécuter la requête

Exécutez la requête suivante :

```powershell
$query = 'DeviceRegistryEvents | limit 10' # Paste your own query here

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

Si vous souhaitez exécuter des requêtes complexes (ou des requêtes multilignes), enregistrez votre requête dans un fichier et, au lieu de la première ligne de l’exemple ci-dessus, exécutez la commande suivante :

```powershell
$query = [IO.File]::ReadAllText("C:\myQuery.txt"); # Replace with the path to your file
```

## <a name="work-with-query-results"></a>Travailler avec les résultats de la requête

Vous pouvez maintenant utiliser les résultats de la requête.

Pour générer les résultats de la requête au format CSV dans le fichier file1.csv, exécutez la commande suivante :

```powershell
$results | ConvertTo-Csv -NoTypeInformation | Set-Content file1.csv
```

Pour générer les résultats de la requête au format JSON dans le fichier file1.json, exécutez la commande suivante :

```powershell
$results | ConvertTo-Json | Set-Content file1.json
```


## <a name="related-topic"></a>Rubrique connexe
- [API Microsoft Defender pour point de terminaison](apis-intro.md)
- [API de recherche avancée de menaces](run-advanced-query-api.md)
- [Repérage avancé à l’aide de Python](run-advanced-query-sample-python.md)
