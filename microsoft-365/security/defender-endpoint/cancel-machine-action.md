---
title: API Annuler l’action de l’ordinateur
description: Découvrez comment annuler une action de machine déjà lancée
keywords: api, api graphe,
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: mde
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
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.custom: api
ms.openlocfilehash: 9db5698699385cafe02ab74c49e8070e3cd92678
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68621845"
---
# <a name="cancel-machine-action-api"></a>API Annuler l’action de l’ordinateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/defender-endpoint)
- [Microsoft Defender pour point de terminaison Plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Annuler une action de machine déjà lancée qui n’est pas encore dans un état final (terminé, annulé, échoué).

## <a name="limitations"></a>Limites

1. Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Prise en main](apis-intro.md).

|Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation|
|---|---|---|
|Application|Machine.CollectForensics <br> Machine.Isolate <br> Machine.RestrictExecution <br> Machine.Scan <br> Machine.Offboard <br> Machine.StopAndQuarantine <br> Machine.LiveResponse|Collecter des données d’investigation <br>Isoler l’ordinateur<br>Restreindre l'exécution de code<br>  Machine d’analyse<br>  Annuler l’intégration de l’ordinateur<br> Arrêter et mettre en quarantaine<br> Exécuter une réponse en direct sur un ordinateur spécifique|
|Déléguée (compte professionnel ou scolaire)|Machine.CollectForensics<br> Machine.Isolate  <br>Machine.RestrictExecution<br> Machine.Scan<br> Machine.Offboard<br> Machine.StopAndQuarantineMachine.LiveResponse|Collecter des données d’investigation<br> Isoler l’ordinateur<br>  Restreindre l'exécution de code<br> Machine d’analyse<br>Annuler l’intégration de l’ordinateur<br> Arrêter et mettre en quarantaine<br> Exécuter une réponse en direct sur un ordinateur spécifique|

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machineactions/<machineactionid>/cancel
```

## <a name="request-headers"></a>En-têtes de demande

|Nom|Type|Description|
|---|---|---|
|Autorisation|Chaîne|Bearer {token}. Required.|
|Content-Type|string|application/json. Required.|

## <a name="request-body"></a>Corps de la demande

|Paramètre|Type|Description|
|---|---|---|
|Commentaire|Chaîne|Commentaire à associer à l’action d’annulation.|

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie 200, code de réponse OK avec une entité Machine Action. Si l’entité d’action de machine avec l’ID spécifié est introuvable - 404 Introuvable.

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

- [Obtenir l’API d’action de machine](get-machineaction-object.md)
