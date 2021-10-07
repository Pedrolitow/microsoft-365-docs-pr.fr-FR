---
title: API REST du modèle de compréhension de document SharePoint Syntex
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
description: Vue d’ensemble de l’API REST du modèle de compréhension de document SharePoint Syntex.
ms.openlocfilehash: 882dcdbe3561803d20d698e5d1510dd5232fbbe5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60163372"
---
# <a name="sharepoint-syntex-document-understanding-model-rest-api"></a>API REST du modèle de compréhension de document SharePoint Syntex

Vous pouvez utiliser l’interface SharePoint REST pour créer un modèle de compréhension de document, appliquer ou supprimer le modèle dans une ou plusieurs bibliothèques, ainsi qu’obtenir ou mettre à jour les informations concernant le modèle. 

Le service REST SharePoint Online (et SharePoint sur site 2016 et ultérieur) prend en charge la combinaison de plusieurs requêtes en un seul appel au service à l’aide de l’option de requête $batch OData. 

Pour plus d’informations et des liens vers des exemples de code, consultez la rubrique [Créer des requêtes de lots avec l’API REST](/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis).

## <a name="prerequisites"></a>Conditions préalables

Avant de commencer, assurez-vous que vous connaissez les éléments suivants :

- [Découverte du service REST SharePoint](/sharepoint/dev/sp-add-ins/get-to-know-the-sharepoint-rest-service) 
- [Effectuer des opérations de base à l’aide de terminaux REST SharePoint](/sharepoint/dev/sp-add-ins/complete-basic-operations-using-sharepoint-rest-endpoints)

## <a name="rest-commands"></a>Commandes REST

Les commandes REST suivantes peuvent être utilisées avec les modèles de compréhension de document :

- [Créer un modèle](rest-createmodel-method.md) : Crée un modèle et son type de contenu associé.
- [GetByUniqueId](rest-getbyuniqueid-method.md) : reçoit ou met à jour les informations sur un modèle de compréhension de document SharePoint Syntex.
- [GetByTitle](rest-getbytitle-method.md) : reçoit ou met à jour les informations sur un modèle de compréhension de document utilisant le titre du modèle.
- [Appliquer un modèle](rest-applymodel-method.md) : applique (ou synchronise) un modèle de compréhension de document formé à une ou plusieurs bibliothèques.
- [Obtenir des informations sur des bibliothèques et des modèles](rest-getmodelandlibraryinfo.md) : reçoit des informations sur un modèle et la bibliothèque dans laquelle il est appliqué.
- [UpdateModelSettings](rest-updatemodelsettings-method.md) : met à jour les paramètres des modèles disponibles (description du modèle et étiquette de rétention associés) pour un modèle de compréhension de document SharePoint Syntex.
- [BatchDelete](rest-batchdelete-method.md) : Supprime un modèle appliqué de compréhension de document à partir d’une ou plusieurs bibliothèques.
- [Créer une demande de classification de fichiers](rest-createclassificationrequest.md) : Crée une demande pour classifier un ou plusieurs fichiers spécifiés à l’aide du modèle appliqué.
- [Créer une demande de classification de dossier](rest-createclassificationrequest.md) : Crée une demande pour classifier un dossier entier à l’aide du modèle appliqué.

## <a name="scenarios"></a>Scénarios

Notez que les exemples de scénarios suivants ne sont pas intuitifs par rapport au nom de la méthode. Pour plus d'informations, voir chaque article.

La méthode Créer un modèle crée uniquement l’objet du modèle et son type de contenu associé. Vous devrez d’abord former le modèle dans le centre de contenu avant de pouvoir l’appliquer à une bibliothèque.

La méthode Appliquer un modèle est utilisée pour configurer le modèle sur la bibliothèque cible pour classifier des documents et extraire éventuellement des informations supplémentaires. Cette API prend également en charge le lot appliquant le modèle à plusieurs bibliothèques.

La méthode Supprimer un modèle supprime simplement le modèle d’une ou plusieurs bibliothèques dans lesquelles il a été précédemment appliqué. Si vous souhaitez supprimer le modèle, vous devez d’abord le supprimer de toutes les bibliothèques dans lesquelles il a été appliqué.


## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la compréhension de document](../document-understanding-overview.md)

