---
title: API Annuler l’action de l’ordinateur
description: Découvrez comment annuler une action d’ordinateur déjà lancée
keywords: api, api de graphique,
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fc4191043e19df7fea4f350d85acd78d2eca1551
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322910"
---
# <a name="cancel-machine-action-api"></a>API Annuler l’action de l’ordinateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Annuler une action d’ordinateur déjà lancée qui n’est pas encore dans l’état final (terminé, annulé, échoué).

## <a name="limitations"></a>Limitations

1. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, [consultez La mise en place](apis-intro.md).

|Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation|
|---|---|---|
|Application|Machine.CollectForensics <br> Machine.Isolate <br> Machine.RestrictExecution <br> Machine.Scan <br> Machine.Offboard <br> Machine.StopAndQuarantine <br> Machine.LiveResponse|Collecter des données d’investigation <br>Isoler l’ordinateur<br>Restreindre l'exécution de code<br>  Ordinateur d’analyse<br>  Annuler l’intégration de l’ordinateur<br> Arrêter et mettre en quarantaine<br> Exécuter une réponse en direct sur un ordinateur spécifique|
|Déléguée (compte professionnel ou scolaire)|Machine.CollectForensics<br> Machine.Isolate  <br>Machine.RestrictExecution<br> Machine.Scan<br> Machine.Offboard<br> Machine.StopAndQuarantineMachine.LiveResponse|Collecter des données d’investigation<br> Isoler l’ordinateur<br>  Restreindre l'exécution de code<br> Ordinateur d’analyse<br>Annuler l’intégration de l’ordinateur<br> Arrêter et mettre en quarantaine<br> Exécuter une réponse en direct sur un ordinateur spécifique|

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machineactions/<machineactionid>/cancel
```

## <a name="request-headers"></a>En-têtes de demande

|Nom|Type|Description|
|---|---|---|
|Autorisation|String|Porteur {token}. Obligatoire.|
|Content-Type|string|application/json. Obligatoire.|

## <a name="request-body"></a>Corps de la demande

|Paramètre|Type|Description|
|---|---|---|
|Commentaire|Chaîne|Commentaire à associer à l’action d’annulation.|

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie le code de réponse 200, OK avec une entité Machine Action. Si l’entité d’action de l’ordinateur avec l’ID spécifié est in trouvée - 404 - In trouvé.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

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
