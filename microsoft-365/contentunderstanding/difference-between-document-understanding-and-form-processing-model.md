---
title: Différence entre la compréhension de document et les modèles de traitement de formulaire
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
localization_priority: Priority
description: Décrit la principale différence entre la compréhension de document et les modèles de traitement de formulaire
ms.openlocfilehash: e847ed9b7a00e0ff0542ad3b9ba35c314070837d
ms.sourcegitcommit: e7bf23df4852b78912229d1d38ec475223597f34
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "49087630"
---
# <a name="difference-between-document-understanding-and-form-processing-models"></a>Différence entre la compréhension de document et les modèles de traitement de formulaire 


La compréhension de contenu dans Microsoft SharePoint Syntex vous permet d’identifier et de classer les documents téléchargés dans les bibliothèques de documents SharePoint, ainsi que d’extraire les informations pertinentes de chaque fichier.  Par exemple, lorsque les fichiers sont téléchargés vers une bibliothèque de documents SharePoint, tous les fichiers identifiés comme *Bons de commande* sont classés comme tels, puis affichés dans une vue personnalisée de la bibliothèque de documents. De plus, vous pouvez extraire des informations spécifiques de chaque fichier (par exemple, le *Numéro de bon de commande* et le *Total*) et les afficher sous forme de colonne dans la vue de votre bibliothèque de documents. 

La compréhension de contenu vous permet de créer des *modèles* pour identifier et extraire les informations dont vous avez besoin. Les modèles peuvent vous aider à résoudre des problèmes commerciaux liés à la recherche, aux processus commerciaux, à la conformité et bien d’autres.

Il existe deux types de modèles que vous pouvez utiliser :

- les [modèles de compréhension de document](document-understanding-overview.md)
- les [modèles de traitement de formulaire](form-processing-overview.md)

Bien que les deux modèles soient généralement utilisés dans le même but, les principales différences répertoriées ci-dessous affectent ceux que vous pouvez utiliser.

> [!NOTE]
> Pour plus d’informations sur les exemples de scénarios de traitement de formulaires et de présentation de documents, consultez l'article [SharePoint Syntex adoption : guide de mise en route](https://docs.microsoft.com/microsoft-365/contentunderstanding/adoption-getstarted#form-processing-scenario-example).


## <a name="structured-versus-unstructured-and-semi-structured-content"></a>Contenu structuré, contenu non structuré ou contenu semi-structuré

Utilisez des modèles de compréhension de document pour identifier et extraire des données de documents non structurés, comme des lettres ou des contrats, dans lesquels les entités de texte que vous souhaitez extraire se trouvent dans des phrases ou des zones spécifiques du document. Par exemple, un document non structuré peut être une lettre de renouvellement de contrat, qui peut être rédigée de différentes manières. Cependant, des informations existent systématiquement dans le corps de chaque document de renouvellement de contrat, telles que la chaîne de caractères *Date de début du service de* suivi d’une date réelle.   

Utilisez des modèles de traitement de formulaire pour identifier les fichiers et extraire des données de documents structurés ou semi-structurés, tels que des formulaires ou des factures. Les modèles de traitement de formulaire sont formés pour comprendre la mise en page de votre formulaire à partir d’exemples de documents et apprendre à rechercher les données que vous devez extraire à partir d’emplacements similaires. En effet, les formulaires ont une mise en page plus structurée et les entités se trouvent à la même place (par exemple, un numéro de sécurité sociale sur un formulaire fiscal). 

> [!NOTE]
> Vous devez avoir accès à un site de type centre de contenu pour créer un modèle de compréhension de document ou pour en appliquer un à une bibliothèque de documents SharePoint. 


## <a name="where-they-are-created"></a>Où sont-ils créés ?

Les modèles de compréhension de document sont créés et gérés dans un site de type centre de contenu SharePoint. 

> [!NOTE]
> Si vous souhaitez en savoir plus sur les documents input, consultez l’article [Configuration requise et limitations du modèle de traitement de formulaire](https://docs.microsoft.com/ai-builder/form-processing-model-requirements). 

Les modèles de traitement de formulaire sont créés dans [AI Builder](https://docs.microsoft.com/ai-builder/overview) de PowerApps, mais la création est lancée directement à partir d’une bibliothèque de documents SharePoint. La création de modèle de traitement de formulaire doit être activée sur votre bibliothèque de documents pour qu’un utilisateur puisse créer un modèle de traitement de formulaire pour celle-ci. Un administrateur peut activer cette option dans les paramètres d’administration du contenu. Les modèles de traitement de formulaire utilisent des flux PowerAutomate pour traiter les fichiers lorsqu’ils sont téléchargés dans la bibliothèque de documents.

Lorsque vous créez un modèle de compréhension de document, vous créez un nouveau [type de contenu SharePoint](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978), qui est enregistré dans la galerie Types de contenu SharePoint. Vous pouvez également utiliser des types de contenu existants pour définir votre modèle si nécessaire.

Les modèles de traitement de formulaire créent également de nouveaux [types de contenu SharePoint](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) et sont, eux aussi, stockés dans la galerie Types de contenu SharePoint.

## <a name="where-they-can-be-applied"></a>Où peuvent-ils être appliqués ?

Vous pouvez appliquer des modèles de compréhension de document aux bibliothèques de documents SharePoint auxquelles vous avez accès. Utilisez le centre de contenu pour créer un modèle de compréhension de document et appliquer celui-ci à différentes bibliothèques de documents. Le centre de contenu offre un contrôle plus central concernant l’utilisation des modèles de compréhension de document ainsi que leur application. Notez que ces informations doivent également être transmises à un centre de contenu.

Actuellement, les modèles de traitement de formulaire ne peuvent être appliqués qu’à la bibliothèque de documents SharePoint à partir de laquelle ils sont créés. Cela permet aux utilisateurs sous licence, ayant accès au site, de pouvoir créer un modèle de traitement de formulaire. Notez que votre administrateur doit activer le traitement de formulaire sur une bibliothèque de documents SharePoint pour que les utilisateurs sous licence puissent l’utiliser.

 ## <a name="see-also"></a>Voir aussi
[Formation : Améliorer les performances de votre entreprise avec AI Builder](https://docs.microsoft.com/learn/paths/improve-business-performance-ai-builder/?source=learn)



[Vue d’ensemble de la compréhension de document](document-understanding-overview.md)

[Vue d’ensemble du traitement des formulaires](form-processing-overview.md)

[Introduction à SharePoint Syntex](index.md)
