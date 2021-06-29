---
title: Appliquer un modèle par lots
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
description: Utilisez l’API REST pour appliquer un modèle de compréhension de document à une ou plusieurs bibliothèques.
ms.openlocfilehash: 24ea9a480bc3ce5a7745857de17a6fab6ed97685
ms.sourcegitcommit: cfd7644570831ceb7f57c61401df6a0001ef0a6a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2021
ms.locfileid: "53177260"
---
# <a name="batch-apply-model"></a>Appliquer un modèle par lots

Applique (ou synchronise) un modèle de compréhension de document formé à une ou plusieurs bibliothèques (voir [exemple](rest-applymodel-method.md#examples)).

## <a name="http-request"></a>Requête HTTP

```HTTP
POST /_api/machinelearning/publications HTTP/1.1
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
|_métadonnées|oui|chaîne|Définissez l’objet méta sur le SPO. Utilisez toujours la valeur : {"type": "Microsoft.Office.Server.ContentCenter.SPMachineLearningPublicationsEntityData"}.|
|Publications|oui|MachineLearningPublicationEntityData[]|La collection de chaque MachineLearningPublicationEntityData qui spécifie le modèle et la bibliothèque de documents cible.|

### <a name="machinelearningpublicationentitydata"></a>MachineLearningPublicationEntityData
| Nom | Obligatoire | Type | Description |
|--------|-------|--------|------------|
|ModelUniqueId|oui|chaîne|L'ID unique du fichier modèle.|
|TargetSiteUrl|oui|chaîne|L’URL complète du site cible de bibliothèque.|
|TargetWebServerRelativeUrl|oui|chaîne|L’URL du web relative au serveur pour la bibliothèque cible.|
|TargetLibraryServerRelativeUrl|oui|chaîne|L’URL relative au serveur pour la bibliothèque cible.|
|ViewOption|Non|string|Spécifie s’il faut définir l’affichage du nouveau modèle comme bibliothèque par défaut.|

## <a name="response"></a>Réponse

| Nom   | Type  | Description|
|--------|-------|------------|
|201 est créé||Il s’agit d’une API personnalisée pour prendre en charge l’application d’un modèle à plusieurs bibliothèques de documents. Dans le cas d’une réussite partielle, 201 créé peut encore être renvoyé et l’appelant doit inspecter le corps de la réponse pour savoir si le modèle a été correctement appliqué à une bibliothèque de documents.|

## <a name="response-body"></a>Corps de la réponse
| Nom   | Type  | Description|
|--------|-------|------------|
|TotalSuccesses|int|Le nombre total d’applications réussies d’un modèle à une bibliothèque de documents.|
|TotalFailures|int|Le nombre total d’applications défaillantes d’un modèle à une bibliothèque de documents.|
|Détails|MachineLearningPublicationResult[]|La collection de chaque MachineLearningPublicationResult qui spécifie le résultat détaillé de l’application du modèle à la bibliothèque de documents.|

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

### <a name="apply-a-model-to-the-contracts-document-library-in-the-repository-site"></a>Appliquer un modèle à la bibliothèque de documents concernant les contrats dans le site du référentiel

Dans cet exemple, l’ID du modèle de compréhension de document du Contrat Contoso est `7645e69d-21fb-4a24-a17a-9bdfa7cb63dc`.

#### <a name="sample-request"></a>Exemple de demande

```HTTP
{
    "__metadata": {
        "type": "Microsoft.Office.Server.ContentCenter.SPMachineLearningPublicationsEntityData"
    },
    "Publications": {
        "results": [
            {
                "ModelUniqueId": "7645e69d-21fb-4a24-a17a-9bdfa7cb63dc",
                "TargetSiteUrl": "https://contoso.sharepoint.com/sites/repository/",
                "TargetWebServerRelativeUrl": "/sites/repository",
                "TargetLibraryServerRelativeUrl": "/sites/repository/contracts",
                "ViewOption": "NewViewAsDefault"
            }
        ]
    }
}
```


#### <a name="sample-response"></a>Exemple de réponse

Dans la réponse, TotalFailures et TotalSuccesses font référence au nombre d’échecs et de réussite du modèle qui s’applique aux bibliothèques spécifiées.

**Code d'état :** 201

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
            "StatusCode": 201
        }
    ],
    "TotalFailures": 0,
    "TotalSuccesses": 1
}
```

## <a name="see-also"></a>Voir aussi

[API REST du modèle de compréhension de document Syntex](syntex-model-rest-api.md)
