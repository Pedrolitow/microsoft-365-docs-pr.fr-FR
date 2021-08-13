---
title: Créer une demande de classification
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: reference
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: m365initiative-syntex
localization_priority: Priority
description: Utiliser l’API REST pour créer une demande pour classifier un ou plusieurs fichiers à l’aide d’un modèle formé de compréhension de document.
ms.openlocfilehash: 99b4893ace64f802baf8642bf08f916c183e6a3844894561a9e756521599087c
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53891306"
---
# <a name="create-classification-request"></a>Créer une demande de classification

Crée une demande pour classifier un ou plusieurs fichiers à l’aide d’un modèle formé de compréhension de document (voir [exemple](rest-createclassificationrequest.md#examples)).

Le service REST SharePoint Online (et SharePoint 2016 et version ultérieure sur site) prend en charge la combinaison de plusieurs requêtes. Les demandes sont regroupées en un seul appel vers le service en utilisant l’option de requête OData $batch. Vous pouvez utiliser cette méthode pour placer en file d’attente des éléments de travail de classification pour des centaines de documents à la fois.

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
|TargetSiteId|guid|L’ID du site dans lequel se trouve le fichier à classifier.|
|TargetWebId|guid|L’ID du web dans lequel se trouve le fichier à classifier.|
|TargetUniqueId|guid|L’ID du fichier à classifier.|

## <a name="responses"></a>Réponses

| Nom   | Type  | Description|
|--------|-------|------------|
|201 est créé| |Opération réussie|

## <a name="examples"></a>Exemples

### <a name="enqueue-a-request-to-classify-a-file-of-id-e6cff8b7-c90c-4564-b5b8-033449090932"></a>Placer en file d’attente une demande pour classifier un fichier avec l’ID « e6cff8b7-c90c-4564-b5b8-033449090932 »

#### <a name="sample-request"></a>Exemple de demande

```JSON
{
    "__metadata": {
        "type": "Microsoft.Office.Server.ContentCenter.SPMachineLearningWorkItemEntityData"
    },
    "TargetSiteId": "f686e63b-aba7-48e5-97c7-68c4c1df292f",
    "TargetWebId": "66d6b64d-6f88-4dd9-b3db-47e6f00c53e8",
    "TargetUniqueId": "e6cff8b7-c90c-4564-b5b8-033449090932"
}
```

#### <a name="sample-response"></a>Exemple de réponse

**Code d'état :** 201

## <a name="see-also"></a>Voir aussi

[API REST du modèle de compréhension de document Syntex](syntex-model-rest-api.md)
