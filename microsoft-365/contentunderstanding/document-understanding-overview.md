---
title: Vue d’ensemble du document de présentation (aperçu)
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 08/1/2020
audience: admin
ms.topic: article
ms.service: ''
search.appverid: ''
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
description: Obtenez une vue d’ensemble de la compréhension des documents dans le projet cortex.
ms.openlocfilehash: 13b0aa3742c6cf1c0c1123996c683d13c6577876
ms.sourcegitcommit: ea5e2f85bd6b609658545b120c7e08789b9686fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2020
ms.locfileid: "46537134"
---
# <a name="document-understanding-overview-preview"></a>Vue d’ensemble du document de présentation (aperçu)
> [!Note] 
> Le projet cortex est actuellement en préversion. Pour [plus d’informations sur le projet cortex](https://aka.ms/projectcortex).

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSu7] 

</br>

Document comprendre utilise les modèles AI pour automatiser la classification des fichiers et l’extraction des informations. Elle fonctionne mieux avec des documents non structurés, tels que des lettres ou des contrats. Les documents doivent contenir du texte qui peut être identifié en fonction d’expressions ou de modèles. Le texte identifié peut désigner à la fois le type de fichier dont il est (sa classification) et ce que vous souhaitez extraire (ses extracteurs).

Les modèles de présentation des documents sont créés et gérés dans un type de site SharePoint appelé centre de contenu. Lorsqu’il est appliqué à une bibliothèque de documents SharePoint, le modèle est associé à un type de contenu qui contient des colonnes pour stocker les informations extraites. Le type de contenu que vous créez est stocké dans la Galerie de types de contenu SharePoint. Vous pouvez également choisir d’utiliser des types de contenu existants afin d’utiliser leur schéma.

Vous pouvez ajouter des *classifieurs* et des *extracteurs* à vos modèles de présentation de documents pour effectuer les opérations suivantes : 

- Les classifieurs sont utilisés pour identifier et classer les documents qui sont chargés dans la bibliothèque de documents. Par exemple, un classifieur peut être « formé » pour identifier tous les documents de *renouvellement de contrat* téléchargés dans la bibliothèque. Le type de contenu renouvellement de contrat est défini par vous lors de la création de votre classifieur.

- Les extracteurs extraient des informations de ces documents. Par exemple, pour tous les documents de renouvellement de contrat identifiés dans votre bibliothèque de documents, les colonnes s’affichent dans votre affichage qui indique également la *Date de début du service* et le *client* pour chaque document de renouvellement de contrat. 

Vous utilisez des exemples de fichiers pour former et tester vos classifieurs et extracteurs dans votre modèle. Les exemples de fichiers fournissent des exemples de modèles de ce que vous pouvez rechercher lorsque vous essayez d’identifier et d’extraire des données à partir de fichiers. Par exemple, vous allez former vos classifieurs et extracteurs de renouvellement de contrat avec des exemples de documents de renouvellement de contrat avec lesquels votre société travaille. Vous pouvez également utiliser des exemples de fichiers pour tester l’efficacité de votre modèle.

Après avoir publié votre modèle, utilisez le centre de contenu pour l’appliquer à n’importe quelle bibliothèque de documents SharePoint à laquelle vous avez accès.  


## <a name="see-also"></a>Voir aussi
[Créer un classifieur](create-a-classifier.md)</br>
[Créer un extracteur](create-an-extractor.md)</br>
[Créer un centre](create-a-content-center.md) 
 de contenu [Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)</br>
[Appliquer un modèle](apply-a-model.md)   
[Différence entre une présentation de document et un modèle de traitement de formulaire](difference-between-document-understanding-and-form-processing-model.md)  
[Vue d’ensemble du traitement des formulaires](form-processing-overview.md)




