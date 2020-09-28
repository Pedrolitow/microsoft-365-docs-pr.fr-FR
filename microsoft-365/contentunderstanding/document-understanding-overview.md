---
title: Présentation de l’explication des documents
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 08/1/2020
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: Obtenir une vue d’ensemble de la compréhension des documents dans Microsoft SharePoint Syntex.
ms.openlocfilehash: dd8731759d8f1cbea57d171fa7a803ffc4f1baa7
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48294759"
---
# <a name="document-understanding-overview"></a>Présentation de l’explication des documents


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSu7] 

</br>

Le mémorandum d’accord sur les documents utilise les modèles d’intelligence artificielle pour automatiser la classification des fichiers et l’extraction des informations. Il fonctionne de manière optimale avec des documents non structurés, tels que des lettres ou des contrats. Ces documents doivent contenir du texte qui peut être identifié en fonction d’expressions ou de modèles. Le texte identifié désigne à la fois le type de fichier dont il est (sa classification) et ce que vous souhaitez extraire (ses extracteurs).

Les modèles de présentation des documents sont créés et gérés dans un type de site SharePoint appelé *Centre de contenu*. Lorsqu’il est appliqué à une bibliothèque de documents SharePoint, le modèle associé à un type de contenu comporte des colonnes pour stocker les informations extraites. Le type de contenu que vous créez est stocké dans la Galerie de types de contenu SharePoint. Vous pouvez également choisir d’utiliser des types de contenu existants pour utiliser leur schéma.

Ajoutez des *classifieurs* et des *extracteurs* à vos documents de présentation des modèles pour effectuer les opérations suivantes : 

- Les classifieurs sont utilisés pour identifier et classer les documents qui sont chargés dans la bibliothèque de documents. Par exemple, un classifieur peut être « formé » pour identifier tous les documents de *renouvellement de contrat* téléchargés dans la bibliothèque. Le type de contenu renouvellement de contrat est défini par vous lors de la création de votre classifieur.

- Les extracteurs extraient des informations de ces documents. Par exemple, pour tous les documents de renouvellement de contrat identifiés dans votre bibliothèque de documents, les colonnes s’affichent dans votre vue, qui indiquent également la *Date de début du service* et le  *client* pour chaque document de renouvellement de contrat. 

Vous pouvez utiliser des fichiers d’exemple pour former et tester vos classifieurs et extracteurs dans votre modèle. Les fichiers d’exemple fournissent des exemples de modèles de ce que vous pouvez rechercher lorsque vous essayez d’identifier et d’extraire des données à partir de fichiers. Par exemple, vous allez former vos classifieurs et extracteurs de renouvellement de contrat avec des exemples de documents de renouvellement de contrat avec lesquels votre société travaille. Vous pouvez également utiliser des fichiers d’exemple pour tester l’efficacité de votre modèle.

Après avoir publié votre modèle, utilisez le centre de contenu pour l’appliquer à n’importe quelle bibliothèque de documents SharePoint à laquelle vous avez accès.  


## <a name="see-also"></a>Voir aussi
[Créer un classifieur](create-a-classifier.md)</br>
[Créer un extracteur](create-an-extractor.md)</br>
[Créer un centre](create-a-content-center.md) 
 de contenu [Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)</br>
[Appliquer un modèle](apply-a-model.md)   
[Différence entre une présentation de document et un modèle de traitement de formulaire](difference-between-document-understanding-and-form-processing-model.md)  
[Vue d’ensemble du traitement des formulaires](form-processing-overview.md)
