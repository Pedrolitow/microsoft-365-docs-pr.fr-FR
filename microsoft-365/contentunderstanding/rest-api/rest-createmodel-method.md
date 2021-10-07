---
title: Créer un modèle
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
description: Utilisez l’API REST pour créer un modèle et son type de contenu associé.
ms.openlocfilehash: c74eda4e3136e2c391c89fc012628bde2ce172f4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60159567"
---
# <a name="create-model"></a>Créer un modèle

Crée un modèle et son type de contenu associé. Notez que cette opération crée le modèle uniquement. Il devra être formé dans le centre de contenu (voir [exemple](rest-createmodel-method.md#examples)).

## <a name="http-request"></a>Requête HTTP

```http
POST /_api/machinelearning/models HTTP/1.1
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
|_métadonnées|  |Définissez l’objet méta sur le SPO. Utilisez toujours la valeur : {"type": "Microsoft.Office.Server.ContentCenter.SPMachineLearningModelEntityData"}. |
|ContentTypeGroup|chaîne|Le groupe de types associés de contenu associé au modèle. « Types de contenu de document intelligent » par défaut.|
|ContentTypeName|chaîne|Le nom du type de contenu associé. Le fichier de modèle créé portera le même nom.|

## <a name="responses"></a>Réponses

| Nom   | Type  | Description|
|--------|-------|------------|
|201 est créé| |Opération réussie|

## <a name="examples"></a>Exemples

### <a name="create-a-new-document-understanding-model-called-contoso-contract"></a>Crée un modèle de compréhension de document appelé « Contrat Contoso »

#### <a name="sample-request"></a>Exemple de demande

```json
{
    "__metadata": {
        "type": "Microsoft.Office.Server.ContentCenter.SPMachineLearningModelEntityData"
    },
    "ContentTypeGroup": "Intelligent Document Content Types",
    "ContentTypeName": "Contoso Contract"
}
```

#### <a name="sample-response"></a>Exemple de réponse

**Code d'état :** 201

## <a name="see-also"></a>Voir aussi

[API REST du modèle de compréhension de document Syntex](syntex-model-rest-api.md)
