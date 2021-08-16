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
localization_priority: Priority
description: Utilisez l’API REST pour créer un modèle et son type de contenu associé.
ms.openlocfilehash: ac5a48f92352c2c286323b8a679a975e0dbdca80703f9f727d16a4999b4a2f65
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53899810"
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
