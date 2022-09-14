---
title: Chasse avancée guide de l’API Repérage avancé avec PowerShell
ms.reviewer: ''
description: Utilisez ces exemples de code, en interrogeant plusieurs API Microsoft Defender pour point de terminaison.
keywords: api, api prises en charge, repérage avancé, requête
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
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
ms.date: 04/27/2022
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 3d05807b0f6bd16b8f1a035411d8144840ef3832
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67690353"
---
# <a name="microsoft-defender-for-endpoint-apis-using-powershell"></a>MICROSOFT DEFENDER POUR POINT DE TERMINAISON API à l’aide de PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/index.yml)

> [!IMPORTANT]
> Les fonctionnalités de chasse avancées ne sont pas incluses dans Defender entreprise. Consultez [Comparer les Microsoft Defender pour entreprises à Microsoft Defender pour point de terminaison plans 1 et 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Scénario complet utilisant plusieurs API de Microsoft Defender pour point de terminaison.

Dans cette section, nous partageons des exemples PowerShell pour 
- Récupérer un jeton 
- Utiliser un jeton pour récupérer les dernières alertes dans Microsoft Defender pour point de terminaison
- Pour chaque alerte, si l’alerte a une priorité moyenne ou élevée et est toujours en cours, vérifiez le nombre de connexions de l’appareil à une URL suspecte.

**Prérequis** : vous devez d’abord [créer une application](apis-intro.md).

## <a name="preparation-instructions"></a>Instructions de préparation

- Ouvrez une fenêtre PowerShell.
- Si votre stratégie ne vous permet pas d’exécuter les commandes PowerShell, vous pouvez exécuter la commande ci-dessous :
  ```
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

Pour plus d’informations, consultez la [documentation PowerShell](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Obtenir un jeton

Exécutez la commande ci-dessous :

- $tenantId : ID du locataire au nom duquel vous souhaitez exécuter la requête (c’est-à-dire que la requête sera exécutée sur les données de ce locataire)
- $appId : ID de votre application AAD (l’application doit avoir l’autorisation « Exécuter des requêtes avancées » sur Defender pour point de terminaison)
- $appSecret : Secret de votre application Azure AD

- $suspiciousUrl : URL


```
$tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
$appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
$appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here
$suspiciousUrl = 'www.suspiciousUrl.com' # Paste your own URL here

$resourceAppIdUri = 'https://securitycenter.onmicrosoft.com/windowsatpservice'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$aadToken = $authResponse.access_token


#Get latest alert
$alertUrl = "https://api.securitycenter.microsoft.com/api/alerts?`$top=10"
$headers = @{ 
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $aadToken" 
}
$alertResponse = Invoke-WebRequest -Method Get -Uri $alertUrl -Headers $headers -ErrorAction Stop
$alerts =  ($alertResponse | ConvertFrom-Json).value

$machinesToInvestigate = New-Object System.Collections.ArrayList

Foreach($alert in $alerts)
{
    #echo $alert.id $alert.machineId    $alert.severity $alert.status

    $isSevereAlert = $alert.severity -in 'Medium', 'High'
    $isOpenAlert = $alert.status -in 'InProgress', 'New'
    if($isOpenAlert -and $isSevereAlert)
    {
        if (-not $machinesToInvestigate.Contains($alert.machineId))
        {
            $machinesToInvestigate.Add($alert.machineId) > $null
        }
    }
}

$commaSeparatedMachines = '"{0}"' -f ($machinesToInvestigate -join '","')

$query = "NetworkCommunicationEvents
| where MachineId in ($commaSeparatedMachines)
| where RemoteUrl  == `"$suspiciousUrl`"
| summarize ConnectionsCount = count() by MachineId"

$queryUrl = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"

$queryBody = ConvertTo-Json -InputObject @{ 'Query' = $query }
$queryResponse = Invoke-WebRequest -Method Post -Uri $queryUrl -Headers $headers -Body $queryBody -ErrorAction Stop
$response =  ($queryResponse | ConvertFrom-Json).Results
$response
```


## <a name="see-also"></a>Voir aussi
- [API Microsoft Defender pour point de terminaison](apis-intro.md)
- [API de recherche avancée de menaces](run-advanced-query-api.md)
- [Repérage avancé à l’aide de Python](run-advanced-query-sample-python.md)
