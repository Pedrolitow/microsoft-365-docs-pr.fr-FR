---
title: API Annuler l’action de l’ordinateur
description: Découvrez comment annuler une action d’ordinateur déjà lancée
keywords: api, api de graphique,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 490ee91d5f2d2c02174be94c52fc83fd0ec0fc5e
ms.sourcegitcommit: 337e8d8a2fee112d799edd8a0e04b3a2f124f900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2021
ms.locfileid: "52879755"
---
#   <a name="cancel-machine-action-api"></a>API Annuler l’action de l’ordinateur 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Annuler une action de l’ordinateur déjà lancée qui n’est pas encore dans l’état final (terminé, annulé, échoué).

## <a name="limitations"></a>Limites

1.  Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, [consultez La mise en place.](apis-intro.md)

|     Type d’autorisation     |     Autorisation     |    Nom d’affichage de l’autorisation     |
|-|-|-|
|    <br>Application    |    <br>Machine.CollectForensic<br>   Machine.Isolate   <br>Machine.RestrictExecution<br>   Machine.Scan<br>   Machine.Offboard<br>   Machine.StopAndQuarantine<br>   Machine.LiveResponse    |    Collecter des données d’investigation   <br>Isoler l’ordinateur<br>Restreindre l’exécution du code<br>  Ordinateur d’analyse<br>  Appareil hors-carte<br>   Arrêter et mettre en quarantaine<br>   Exécuter une réponse en direct sur un ordinateur spécifique    |
|    <br>Délégué (compte scolaire ou scolaire)    |    Machine.CollectForensic<br>   Machine.Isolate    <br>Machine.RestrictExecution<br>   Machine.Scan<br>   Machine.Offboard<br>   Machine.StopAndQuarantineMachine.LiveResponse    |    Collecter des données d’investigation<br>   Isoler l’ordinateur<br>  Restreindre l’exécution du code<br> Ordinateur d’analyse<br>Appareil hors-carte<br> Arrêter et mettre en quarantaine<br> Exécuter une réponse en direct sur un ordinateur spécifique    |


## <a name="http-request"></a>Requête HTTP

```
POST https://api.securitycenter.microsoft.com/api/machineactions/<machineactionid>/cancel  
```


## <a name="request-headers"></a>En-têtes de demande

| Nom      | Type | Description                 |
|---------------|----------|---------------------------------|
| Autorisation | String   | Porteur {token}. Obligatoire.   |
| Content-Type  | string   | application/json. Obligatoire. |

## <a name="request-body"></a>Corps de la demande

| Parameter | Type | Description                        |
|---------------|----------|----------------------------------------|
| Commentaire       | Chaîne   | Commentaire à associer à l’action d’annulation.  |

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie le code de réponse 200, Ok avec une entité Action de l’ordinateur. Si l’entité d’action de l’ordinateur avec l’ID spécifié est in trouvée - 404 - In trouvé.

## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```HTTP
POST
https://api.securitycenter.microsoft.com/api/machineactions/988cc94e-7a8f-4b28-ab65-54970c5d5018/cancel
```


```JSON
{
    "Comment": "Machine action was canceled by automation"
}
```

## <a name="related-topic"></a>Rubrique connexe

- [API Obtenir l’action de l’ordinateur](get-machineaction-object.md)