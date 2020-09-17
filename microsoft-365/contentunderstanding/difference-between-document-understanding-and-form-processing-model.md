---
title: Différence entre la présentation des documents et les modèles de traitement des formulaires (aperçu)
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 8/1/2020
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: Décrit la principale différence entre la présentation des documents et les modèles de traitement des formulaires.
ms.openlocfilehash: ceea3a6e7898d8971ea458222d6164b496fcb8b7
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47950059"
---
# <a name="difference-between-document-understanding-and-form-processing-models-preview"></a>Différence entre la présentation des documents et les modèles de traitement des formulaires (aperçu)

> [!Note] 
> Le contenu de cet article est destiné à Project cortex privé preview. Pour [plus d’informations sur le projet cortex](https://aka.ms/projectcortex).

Content Understanding in Project cortex vous permet d’identifier et de classer les documents qui sont chargés dans les bibliothèques de documents SharePoint, ainsi que d’extraire les informations pertinentes de chaque fichier.  Par exemple, lorsque les fichiers sont téléchargés vers une bibliothèque de documents SharePoint, tous les fichiers identifiés comme *bons de commande* sont classés comme tels et affichés dans un affichage de bibliothèque de documents personnalisé dans lequel ils sont affichés. En outre, vous pouvez extraire des informations spécifiques de chaque fichier (par exemple, le *numéro de bon de commande* et le *total*) et les afficher dans une colonne de votre vue de bibliothèque de documents. 


Content Understanding vous permet de créer des *modèles* pour identifier et extraire les informations dont vous avez besoin.  Il existe deux types de modèles qui peuvent être utilisés :

- [Modèles de présentation des documents](document-understanding-overview.md)
- [Modèles de traitement des formulaires](form-processing-overview.md)

Même si les deux modèles sont utilisés pour le même objectif, il existe des différences clés qui affecteront celle que vous pouvez choisir.


## <a name="structured-versus-unstructured-and-semi-structured-content"></a>Contenu structuré et non structuré et semi-structuré

Utilisez les modèles de présentation de document pour identifier et extraire des données de documents non structurés, tels que des lettres ou des contrats, où les entités de texte que vous souhaitez extraire résident dans des phrases ou dans des régions spécifiques du document. Par exemple, un document non structuré peut être une lettre de renouvellement de contrat qui peut être écrite de différentes manières. Toutefois, il existe des informations qui se trouvent régulièrement dans le corps de chaque document de renouvellement de contrat, comme la chaîne de texte « date de début du service » suivie d’une date réelle.   

Utiliser des modèles de traitement de formulaire pour identifier des fichiers et extraire des données de documents structurés ou semi-structurés, tels que des formulaires ou des factures, où vous avez des paires de valeurs clés claires (par exemple, *Date : 10/1/2020*) * ou données de tableau. Par exemple, un bon candidat pour le traitement des formulaires serait le formulaire de demande d’ordre d’une société dans lequel les clients ont besoin de fournir leurs informations à des champs spécifiques situés dans la même zone de la mise en page du document, tels que le *nom*, le *numéro de téléphone*, le *coût total*, etc.  Un formulaire fiscal constitue un bon exemple de document structuré. 

## <a name="where-they-are-created"></a>Emplacement de création

Les modèles de présentation des documents sont créés et gérés dans un site Centre de contenu SharePoint. Vous devez avoir accès à un site du centre de contenu pour créer un modèle de présentation des documents ou pour l’appliquer à une bibliothèque de documents SharePoint. 

Lorsque vous créez un modèle de présentation de document, vous créez un nouveau [type de contenu SharePoint](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) qui est enregistré dans la Galerie de types de contenu SharePoint. Vous pouvez éventuellement utiliser des types de contenu existants pour définir votre modèle si nécessaire.

Les modèles de traitement de formulaire sont créés dans le [générateur ai](https://docs.microsoft.com/ai-builder/overview)powerapps, mais la création est initiée directement à partir d’une bibliothèque de documents SharePoint. La création du modèle de traitement des formulaires doit être activée sur votre bibliothèque de documents afin qu’un utilisateur puisse créer un modèle de traitement de formulaire pour celui-ci, et un administrateur peut le faire dans les paramètres d’administration content Understanding. Les modèles de traitement de formulaire utilisent des flux PowerAutomate pour traiter les fichiers lorsqu’ils sont téléchargés vers la bibliothèque de documents.

Les modèles de traitement de formulaire créent également de nouveaux [types de contenu SharePoint](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978), qui sont également stockés dans la Galerie des types de contenu SharePoint.

## <a name="where-they-can-be-applied"></a>Emplacement auquel ils peuvent être appliqués

Les modèles de présentation des documents peuvent être appliqués à différentes bibliothèques de documents SharePoint auxquelles vous avez accès. Vous pouvez utiliser le centre de contenu pour créer non seulement un modèle de présentation de document, mais également pour l’appliquer à différentes bibliothèques de documents. Le centre de contenu offre un contrôle plus central sur l’utilisation et l’emplacement des modèles de présentation des documents, étant donné que ces informations doivent être déployées dans un centre de contenu.

Les modèles de traitement de formulaire ne peuvent actuellement être appliqués qu’à la bibliothèque de documents SharePoint à partir de laquelle ils ont été créés. Cela permet à tout utilisateur sous licence ayant accès au site de créer un modèle de traitement de formulaire.




 ## <a name="see-also"></a>Voir aussi
[Formation : améliorer les performances d’entreprise avec le générateur AI](https://docs.microsoft.com/learn/paths/improve-business-performance-ai-builder/?source=learn)</br>
[Créer un classifieur](create-a-classifier.md)</br>
[Créer un extracteur](create-an-extractor.md)</br>
[Appliquer un modèle de présentation des documents](apply-a-model.md)</br>
[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)</br>



  
  



