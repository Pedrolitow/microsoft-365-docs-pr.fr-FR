---
title: Obtenir des informations sur un modèle et une bibliothèque
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
description: Utilisez l’API REST pour obtenir des informations sur une bibliothèque et un modèle dans laquelle elle est appliquée.
ms.openlocfilehash: 6cd61364ed3b360ef235aaba21a2735002fe481e
ms.sourcegitcommit: 33d19853a38dfa4e6ed21b313976643670a14581
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2021
ms.locfileid: "52904226"
---
# <a name="get-model-and-library-information"></a>Obtenir des informations sur un modèle et une bibliothèque

Obtient des informations sur une bibliothèque et un modèle dans laquelle elle est appliquée (voir [exemple](rest-getmodelandlibraryinfo.md#examples)).

## <a name="http-request"></a>Requête HTTP

```HTTP
GET /_api/machinelearning/publications/getbyuniqueid(‘{modelUniqueId}’) HTTP/1.1
```

## <a name="uri-parameters"></a>Paramètres d’URI

| Nom | Dans le paramètre | Obligatoire | Type | Description |
|--------|-------|--------|------------|
|ModelUniqueId|requête|True|GUID|L'ID unique du fichier modèle.|

## <a name="request-headers"></a>En-têtes de demande

| En-tête | Valeur |
|--------|-------|
|Accepter|application/json;odata=verbose|


## <a name="request-body"></a>Corps de la demande

| Nom | Obligatoire | Type | Description |
|--------|-------|--------|------------|
|ModelUniqueId|oui|chaîne|L'ID unique du fichier modèle.|
|TargetSiteUrl|oui|chaîne|L’URL complète du site cible de bibliothèque.|
|TargetWebServerRelativeUrl|oui|chaîne|L’URL du web relative au serveur pour la bibliothèque cible.|
|TargetLibraryServerRelativeUrl|oui|chaîne|L’URL relative au serveur pour la bibliothèque cible.|
|TargetLibraryRemoved|oui|int|Le drapeau indiquant la suppression ou non de la bibliothèque cible.|

## <a name="response"></a>Réponse

| Nom   | Type  | Description|
|--------|-------|------------|
|200 OK| |Opération réussie|
|201 est créé| |Notez qu’étant donné que cette API prend en charge l’application du modèle à plusieurs bibliothèques, un code 201 peut être renvoyé, même s’il existe une défaillance dans l’application du modèle à l’une des bibliothèque. <br>Vérifiez que le corps de la réponse pour comprendre si le modèle a été correctement appliqué à toutes les bibliothèques spécifiées. Voir [Corps de réponse](rest-getmodelandlibraryinfo.md#request-body) pour obtenir des détails.|

## <a name="examples"></a>Exemples

### <a name="get-information-about-the-contracts-model-and-primed-document-library-in-the-repository-site"></a>Obtenir des informations sur le modèle des contrats et la bibliothèque de document amorcée dans le site du référentiel

Dans cet exemple, l’ID du modèle de compréhension de document du Contrat Contoso est `7645e69d-21fb-4a24-a17a-9bdfa7cb63dc`.

#### <a name="sample-request"></a>Exemple de demande

```HTTP
GET /sites/TestCC/_api/machinelearning/publications/getbymodeluniqueid(‘{7645e69d-21fb-4a24-a17a-9bdfa7cb63dc}’) HTTP/1.1
```
#### <a name="sample-response"></a>Exemple de réponse

**Code d’état :** 200

```JSON
{
    "@odata.context": "https://contoso.sharepoint.com/sites/TestCC/_api/$metadata#publications",
    "value": [
        {
            "@odata.type": "#Microsoft.Office.Server.ContentCenter.SPMachineLearningPublication",
            "@odata.id": "https://contoso.sharepoint.com/sites/repository /_api/machinelearning/publications/getbyuniqueId('7645e69d-21fb-4a24-a17a-9bdfa7cb63dc')",
            "@odata.etag": "\"7645e69d-21fb-4a24-a17a-9bdfa7cb63dc,94\"",
            "@odata.editLink": " https://contoso.sharepoint.com/sites/TestCC /_api/machinelearning/publications/getbyuniqueId('7645e69d-21fb-4a24-a17a-9bdfa7cb63dc')",
            "Created": "2021-04-27T03:05:25Z",
            "CreatedBy": "i:0#.f|membership|meganb@contoso.com",
            "DriveId": "b!O-aG9qer5UiXx2jEwd8pL0221maIb9lNs9tH5vAMU-gPy9BrxT7GTrtXtdtv1Uzb",
            "ID": 26,
            "ModelId": 16,
            "ModelName": "contosocontract.classifier",
            "ModelType": 0,
            "ModelUniqueId": "7645e69d-21fb-4a24-a17a-9bdfa7cb63dc",
            "ModelVersion": "8.0",
            "Modified": "2021-03-17T17:56:42Z",
            "ModifiedBy": "i:0#.f|membership|joedoe@contoso.com",
            "ObjectId": "01ZBWEM5FZRILGLXTEB5CZ2NNNSCTWBJMQ",
            "PublicationType": 1,
            "TargetLibraryRemoved": false,
            "TargetLibraryServerRelativeUrl": "/sites/repository/contracts",
            "TargetLibraryUrl": " https://contoso.sharepoint.com/sites/repository/contracts",
            "TargetSiteUrl": "https://contoso.sharepoint.com/sites/repository",
            "TargetWebServerRelativeUrl": "/sites/repository",
            "UniqueId": "7645e69d-21fb-4a24-a17a-9bdfa7cb63dc",
            "ViewOption": "NewViewAsDefault"
        },
        {
            "@odata.type": "#Microsoft.Office.Server.ContentCenter.SPMachineLearningPublication",
            "@odata.id": "https://contoso.sharepoint.com /sites/legal/_api/machinelearning/publications/getbyuniqueId('7645e69d-21fb-4a24-a17a-9bdfa7cb63dc')",
            "@odata.etag": "\"7645e69d-21fb-4a24-a17a-9bdfa7cb63dc,101\"",
            "@odata.editLink": "https://contoso.sharepoint.com /sites/legal/_api/machinelearning/publications/getbyuniqueId('7645e69d-21fb-4a24-a17a-9bdfa7cb63dc')",
            "Created": "2021-01-27T03:17:44Z",
            "CreatedBy": "i:0#.f|membership|esherman@contoso.com ",
            "DriveId": "b!O-aG9qer5UiXx2jEwd8pL0221maIb9lNs9tH5vAMU-gPy9BrxT7GTrtXtdtv1Uzb",
            "ID": 27,
            "ModelId": 16,
            "ModelName": "dispositions.classifier",
            "ModelType": 0,
            "ModelUniqueId": "7645e69d-21fb-4a24-a17a-9bdfa7cb63dc",
            "ModelVersion": "8.0",
            "Modified": "2021-03-17T23:17:46Z",
            "ModifiedBy": "i:0#.f|membership|esherman@contoso.com ",
            "ObjectId": "01ZBWEM5B3ERSZK4PAARGLFZ7JP6GMXG2R",
            "PublicationType": 1,
            "TargetLibraryRemoved": false,
            "TargetLibraryServerRelativeUrl": "/sites/legal/dispositions",
            "TargetLibraryUrl": "https://contoso.sharepoint.com/sites/legal/dispositions",
            "TargetSiteUrl": " https://contoso.sharepoint.com/sites/legal",
            "TargetWebServerRelativeUrl": "/sites/legal",
            "UniqueId": "7645e69d-21fb-4a24-a17a-9bdfa7cb63dc",
            "ViewOption": "NewViewAsDefault"
        }
    ]
}```
```

## <a name="see-also"></a>Voir aussi

[API REST du modèle de compréhension de document Syntex](syntex-model-rest-api.md)
