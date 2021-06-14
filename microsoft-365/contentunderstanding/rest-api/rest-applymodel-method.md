---
title: Appliquer un modèle
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
ms.openlocfilehash: d4cadad3c45dd7af0cdaeb4e1b367426289db870
ms.sourcegitcommit: 33d19853a38dfa4e6ed21b313976643670a14581
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2021
ms.locfileid: "52904265"
---
# <a name="apply-model"></a>Appliquer un modèle

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
|ModelUniqueId|oui|chaîne|L'ID unique du fichier modèle.|
TargetSiteUrl|oui|chaîne|L’URL complète du site cible de bibliothèque.|
TargetWebServerRelativeUrl|oui|chaîne|L’URL du web relative au serveur pour la bibliothèque cible.|
TargetLibraryServerRelativeUrl|oui|chaîne|L’URL relative au serveur pour la bibliothèque cible.|
ViewOption|Non|string|Spécifie s’il faut définir l’affichage du nouveau modèle comme bibliothèque par défaut.|

## <a name="response"></a>Réponse

| Nom   | Type  | Description|
|--------|-------|------------|
|200 OK| |Opération réussie|
|201 est créé| |Notez qu’étant donné que cette API prend en charge l’application du modèle à plusieurs bibliothèques, un code 201 peut être renvoyé, même s’il existe une défaillance dans l’application du modèle à l’une des bibliothèque. <br>Vérifiez que le corps de la réponse pour comprendre si le modèle a été correctement appliqué à toutes les bibliothèques spécifiées. Voir [Corps de réponse](rest-applymodel-method.md#request-body) pour obtenir des détails.|

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
