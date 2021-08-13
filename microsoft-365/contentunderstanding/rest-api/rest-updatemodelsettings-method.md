---
title: UpdateModelSettings
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
description: Utilisez l’API REST pour mettre à jour les paramètres des modèles disponibles pour un modèle de compréhension de document SharePoint Syntex.
ms.openlocfilehash: 665fff5e5c9142ce182a44ef2f8abe031f4737ebf74733890e22c70eddfe3495
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53795253"
---
# <a name="updatemodelsettings"></a>UpdateModelSettings

Met à jour les paramètres des modèles disponibles (description du modèle et étiquette de rétention associés) pour un modèle de compréhension de document SharePoint Syntex (voir [exemple](rest-updatemodelsettings-method.md#examples)).

## <a name="http-request"></a>Requête HTTP

```HTTP
POST /_api/machinelearning/models/getbytitle('{modelFileName}')/updatemodelsettings HTTP/1.1
```

## <a name="uri-parameters"></a>Paramètres d’URI

|Nom |Dans le paramètre |Obligatoire|Type|Description|
|-----|---|--------|----|-----------|
|modelFileName|requête|True|string|Nom du fichier de modèle Syntex.|

## <a name="request-headers"></a>En-têtes de demande

| En-tête | Valeur |
|--------|-------|
|Accepter|application/json;odata=verbose|
|Content-Type|application/json;odata=verbose;charset=utf-8|
|x-requestdigest|Résumé approprié pour le site actuel.|

## <a name="request-body"></a>Corps de la demande

|Nom    |Type   |Description |
|--------|-------|-------|
|ModelSettings|chaîne|JSON des paramètres du modèle.|
|Description|string|La description du modèle.|
|ÉtiquetteRétention| |Informations sur l’étiquette associée (nom et ID d’étiquette).|

## <a name="responses"></a>Réponses

| Nom   | Type  | Description|
|--------|-------|------------|
|200 OK| |Opération réussie|

## <a name="examples"></a>Exemples

### <a name="update-model-settings-for-contoso-contract"></a>Mettre à jour les paramètres du modèle pour le Contrat Contoso

Dans cette exemple, la description du modèle et l’étiquette de rétention « Conservation standard » sont mises à jour. L’ID de l’étiquette de rétention est `27c5fcba-abfd-4c34-823d-0b4a48f7ffe6`.

#### <a name="sample-request"></a>Exemple de demande

```HTTP
{
    "ModelSettings": "{\"Description\":\"This model is used to set files classified as Contoso Contracts with a standard hold retention.\", \"RetentionLabel\":{\"Id\":\"27c5fcba-abfd-4c34-823d-0b4a48f7ffe6\",\"Name\":\"Standard Hold\"}}"
}

```

#### <a name="sample-response"></a>Exemple de réponse

**Code d’état :** 200

## <a name="see-also"></a>Voir aussi

[API REST du modèle de compréhension de document Syntex](syntex-model-rest-api.md)
