---
title: Créer une demande de classification de dossiers
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: reference
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: m365initiative-syntex
ms.localizationpriority: high
description: Utilisez l'API REST pour créer une demande de classification d'un dossier entier à l'aide d'un modèle de compréhension de document formé.
ms.openlocfilehash: ea5748b5eb376872738d30b142927314abfe9d3e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60186872"
---
# <a name="create-folder-classification-request"></a>Créer une demande de classification de dossiers

Crée une demande de classification d’un dossier entier pendant les heures creuses à l’aide du modèle de compréhension de document appliqué. (Pour plus d’informations, voir [l’exemple.)](rest-createfolderclassificationrequest.md#examples) Cette API peut être utilisée pour classer une bibliothèque de documents entière en créant un élément de travail pour son dossier racine.

## <a name="http-request"></a>Requête HTTP

```http
POST /_api/machinelearning/workItems HTTP/1.1
```

## <a name="uri-parameters"></a>Paramètres d’URI

Aucun

## <a name="request-headers"></a>En-têtes de demande

| En-tête | Valeur |
|--------|-------|
|Accepter|application/json;odata=verbose|
|Content-Type|application/json;odata=verbose;charset=utf-8|
|x-requestdigest|Résumé approprié pour le site actuel|

## <a name="request-body"></a>Corps de la demande

|Nom    |Type   |Description |
|--------|-------|------------|
|_métadonnées|chaîne |Définissez l’objet méta sur le SPO. Utilisez toujours la valeur : {"type": "Microsoft.Office.Server.ContentCenter.SPMachineLearningWorkItemEntityData"}. |
|TargetSiteId|guid|L’ID du site dans lequel se trouve le fichier à classifier. Cela peut être omis lorsque TargetSiteUrl a une valeur. |
|TargetSiteUrl|chaîne|L’ID du site dans lequel se trouve le dossier à classifier. Cela peut être omis lorsque TargeSiteId a une valeur.|
|TargetWebId|guid|L’ID du web dans lequel se trouve le fichier à classifier. Cela peut être omis lorsque TargetWebServerRelativeUrl a une valeur. |
|TargetWebServerRelativeUrl|chaîne|L’ID du web dans lequel se trouve le fichier à classifier. Ceci peut être omis lorsque TargetWebId a une valeur.  |
|TargetUniqueId|guid|ID du dossier à classer Cela peut être omis lorsque TargetServerRelativeUrl a une valeur. |
|TargetServerRelativeUrl|chaîne|L’URL relative du serveur du dossier à classer se trouve. Cela peut être omis lorsque TargetUniqueId a une valeur.|
|IsFolder|valeur booléenne|Indicateur qui indique si ce qui sera classé est un dossier. Définissez toujours cette valeur sur True pour créer un élément de travail de classification de dossier. |


## <a name="responses"></a>Réponses

| Nom   | Type  | Description|
|--------|-------|------------|
|201 est créé| |La réponse est personnalisée. En cas d’échec, il peut toujours renvoyer 201 Created. L’appelant doit vérifier davantage le corps de la réponse pour déterminer le résultat exact.|

## <a name="response-body"></a>Corps de la réponse

| Nom   | Type  | Description|
|--------|-------|------------|
|StatusCode |int |Le code d'état HTTP. Si ce n'est pas 200 ou 201, l'API devrait avoir échoué.|
|ErrorMessage |chaîne |Le message d’erreur indiquant le problème lors de l’application du modèle à la bibliothèque de documents.|

## <a name="examples"></a>Exemples

### <a name="enqueue-a-request-to-classify-a-whole-folder-of-id-e6cff8b7-c90c-4564-b5b8-033449090932"></a>Placer en file d’attente une demande pour classifier un dossier compet avec l’ID « e6cff8b7-c90c-4564-b5b8-033449090932 »


#### <a name="sample-request"></a>Exemple de demande

```JSON
{
    "__metadata": {
        "type": "Microsoft.Office.Server.ContentCenter.SPMachineLearningWorkItemEntityData"
    },
    "TargetSiteId": "f686e63b-aba7-48e5-97c7-68c4c1df292f",
    "TargetWebId": "66d6b64d-6f88-4dd9-b3db-47e6f00c53e8",
    "TargetUniqueId": "e6cff8b7-c90c-4564-b5b8-033449090932",
    "IsFolder": true 
}
```

#### <a name="sample-response"></a>Exemple de réponse

**Code d'état :** 201

```JSON
{
    "ErrorMessage":  null,
    "StatusCode":  201
}
```

## <a name="see-also"></a>Voir aussi

[API REST du modèle de compréhension de document Syntex](syntex-model-rest-api.md)
