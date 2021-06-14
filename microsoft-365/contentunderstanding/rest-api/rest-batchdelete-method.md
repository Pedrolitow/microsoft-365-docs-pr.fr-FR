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
localization_priority: Priority
description: Utilisez l’API REST pour supprimer un modèle appliqué de compréhension de document à partir d’une ou plusieurs bibliothèques.
ms.openlocfilehash: 8c7aeb449da161fe49050631643c63c93268a13f
ms.sourcegitcommit: 33d19853a38dfa4e6ed21b313976643670a14581
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2021
ms.locfileid: "52904209"
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
|ModelUniqueId|oui|chaîne|L'ID unique du fichier modèle.|
TargetSiteUrl|oui|chaîne|L’URL complète du site cible de bibliothèque.|
TargetWebServerRelativeUrl|oui|chaîne|L’URL du web relative au serveur pour la bibliothèque cible.|
TargetLibraryServerRelativeUrl|oui|chaîne|L’URL relative au serveur pour la bibliothèque cible.|
ViewOption|Non|string|Spécifie s’il faut définir l’affichage du nouveau modèle comme bibliothèque par défaut.|

## <a name="response"></a>Réponse

| Nom   | Type  | Description|
|--------|-------|------------|
|200 OK| |Opération réussie|


## <a name="examples"></a>Exemples

### <a name="remove-a-model-from-the-contracts-document-library-in-the-repository-site"></a>Supprimer un modèle de la bibliothèque de documents concernant les contrats dans le site du référentiel

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
