---
title: BatchDelete
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
description: Utilisez l’API REST pour supprimer un modèle appliqué de compréhension de document à partir d’une ou plusieurs bibliothèques.
ms.openlocfilehash: 52154c5f963ddb466b1544925ffe225fd6b8ff67
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60187052"
---
# <a name="batchdelete"></a>BatchDelete

Supprime un modèle appliqué de compréhension de document à partir d’une ou plusieurs bibliothèques. Notez qu’un modèle doit être supprimé de toutes les bibliothèques avant de pouvoir le supprimer (voir [exemple](rest-batchdelete-method.md#examples)).

## <a name="http-request"></a>Requête HTTP

```HTTP
POST /_api/machinelearning/publications/batchdelete HTTP/1.1
```

## <a name="uri-parameters"></a>Paramètres d’URI

Aucun

## <a name="request-headers"></a>En-têtes de demande

| En-tête | Valeur |
|--------|-------|
|Accepter|application/json;odata=verbose|
|Content-Type|application/json;odata=verbose;charset=utf-8|
|x-requestdigest|Résumé approprié pour le site actuel.|

## <a name="request-body"></a>Corps de la demande

| Nom | Obligatoire | Type | Description |
|--------|-------|--------|------------|
|Publications|oui|MachineLearningPublicationEntityData[]|La collection de chaque MachineLearningPublicationEntityData qui spécifie le modèle et la bibliothèque de documents cible.|

### <a name="machinelearningpublicationentitydata"></a>MachineLearningPublicationEntityData

| Nom | Obligatoire | Type | Description |
|--------|-------|--------|------------|
|ModelUniqueId|oui|chaîne|L'ID unique du fichier modèle.|
|TargetSiteUrl|oui|chaîne|L’URL complète du site cible de bibliothèque.|
|TargetWebServerRelativeUrl|oui|chaîne|L’URL du web relative au serveur pour la bibliothèque cible.|
|TargetLibraryServerRelativeUrl|oui|chaîne|L’URL relative au serveur pour la bibliothèque cible.|

## <a name="response"></a>Réponse

| Nom   | Type  | Description|
|--------|-------|------------|
|200 OK||Il s’agit d’une API personnalisée pour prendre en charge la suppression d’un modèle de plusieurs bibliothèques de documents. Dans le cas d’une réussite partielle, 200 OK créé peut encore être renvoyé et l’appelant doit inspecter le corps de la réponse pour savoir si le modèle a été correctement supprimé d’une bibliothèque de documents.|

## <a name="response-body"></a>Corps de la réponse

| Nom   | Type  | Description|
|--------|-------|------------|
|TotalSuccesses|int|Le nombre total de suppressions réussies d’un modèle dans une bibliothèque de documents.|
|TotalFailures|int|Le nombre total de suppressions défaillantes d’un modèle dans une bibliothèque de documents.|
|Détails|MachineLearningPublicationResult[]|La collection de chaque MachineLearningPublicationResult qui spécifie le résultat détaillé de la suppression du modèle dans une bibliothèque de documents.|

### <a name="machinelearningpublicationresult"></a>MachineLearningPublicationResult

| Nom   | Type  | Description|
|--------|-------|------------|
|StatusCode|int|Le code d’état HTTP.|
|ErrorMessage|chaîne|Le message d’erreur indiquant le problème lors de l’application du modèle à la bibliothèque de documents.|
|Publication|MachineLearningPublicationEntityData|Il s’agit des informations sur le modèle et la bibliothèque de documents cible.| 

### <a name="machinelearningpublicationentitydata"></a>MachineLearningPublicationEntityData

| Nom | Type | Description |
|--------|--------|------------|
|ModelUniqueId|chaîne|L'ID unique du fichier modèle.|
|TargetSiteUrl|chaîne|L’URL complète du site cible de bibliothèque.|
|TargetWebServerRelativeUrl|chaîne|L’URL du web relative au serveur pour la bibliothèque cible.|
|TargetLibraryServerRelativeUrl|chaîne|L’URL relative au serveur pour la bibliothèque cible.|

## <a name="examples"></a>Exemples

### <a name="remove-a-model-from-the-contracts-document-library-in-the-repository-site"></a>Supprimer un modèle de la bibliothèque de documents concernant les contrats dans le site du référentiel

Dans cet exemple, l’ID du modèle de compréhension de document du Contrat Contoso est `7645e69d-21fb-4a24-a17a-9bdfa7cb63dc`.

#### <a name="sample-request"></a>Exemple de demande

```HTTP
{ 
    "publications": [ 
        { 
            "ModelUniqueId": "7645e69d-21fb-4a24-a17a-9bdfa7cb63dc", 
            "TargetSiteUrl": "https://constco.sharepoint-df.com/sites/docsite", 
            "TargetWebServerRelativeUrl": "/sites/docsite ", 
            "TargetLibraryServerRelativeUrl": "/sites/dcocsite/joedcos" 
        } 
    ] 
} 
```

#### <a name="sample-response"></a>Exemple de réponse

Dans la réponse, TotalFailures et TotalSuccesses font référence au nombre d’échecs et de réussites de la suppression du modèle dans les bibliothèques spécifiées.

**Code d’état :** 200

```JSON
{
    "Details": [
        {
            "ErrorMessage": null,
            "Publication": {
                "ModelUniqueId": "7645e69d-21fb-4a24-a17a-9bdfa7cb63dc",
                "TargetSiteUrl": "https://contoso.sharepoint.com/sites/repository/",
                "TargetWebServerRelativeUrl": "/sites/repository",
                "TargetLibraryServerRelativeUrl": "/sites/repository/contracts",
                "ViewOption": "NewViewAsDefault"
            },
            "StatusCode": 200
        }
    ],
    "TotalFailures": 0,
    "TotalSuccesses": 1
}
```

## <a name="see-also"></a>Voir aussi

[API REST du modèle de compréhension de document Syntex](syntex-model-rest-api.md)
