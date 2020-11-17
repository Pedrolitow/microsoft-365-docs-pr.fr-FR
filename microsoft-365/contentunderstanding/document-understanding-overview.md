---
title: Présentation de la compréhension de document
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
localization_priority: Priority
description: Obtenez une vue d’ensemble de la compréhension des documents dans Microsoft SharePoint Syntex.
ms.openlocfilehash: b26ed9a9ed9b8d1f332ccf14377660e634349b3d
ms.sourcegitcommit: e7bf23df4852b78912229d1d38ec475223597f34
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "49087366"
---
# <a name="document-understanding-overview"></a>Présentation de la compréhension de document


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSu7] 

</br>

La compréhension de document utilise les modèles de renseignements artificiels pour automatiser la classification des fichiers et l’extraction des informations. Il fonctionne de façon optimale avec les documents non structurés, tels que les lettres ou les contrats. Ces documents doivent comporter du texte qui peut être identifié sur la base de phrases ou de modèles. Le texte identifié désigne à la fois le type de fichier (sa classification) et ce que vous voulez extraire (ses extracteurs).

> [!NOTE]
> Pour plus d’informations sur les exemples de scénarios relatifs aux exemples de scénarios, consultez l’article [SharePoint Syntex adoption : Guide de démarrage](https://docs.microsoft.com/microsoft-365/contentunderstanding/adoption-getstarted#document-understanding-scenario-example).

Les modèles de compréhension de document sont créés et gérés dans un site de type SharePoint appelé un *centre de contenu* . Lorsqu’il est appliqué à une bibliothèque de documents SharePoint, le modèle associé à un type de contenu inclut des colonnes pour stocker les informations extraites. Le type de contenu que vous créez est stocké dans la Galerie de types de contenu SharePoint. Vous pouvez également choisir d’utiliser des types de contenu existants pour utiliser leur schéma.

Ajoutez des *classificateurs* et des *extracteurs* à votre document présentation des modèles pour effectuer les opérations suivantes : 

- Les classificateurs sont utilisés pour identifier et classer les documents téléchargés vers la bibliothèque de documents. Par exemple, un classifieur peut être « exercé » pour identifier tous les documents *renouvellement de contrat* qui sont chargés dans la bibliothèque. Le type de contenu renouvellement contrat est défini par vous lorsque vous créez votre classifieur.

- Les extracteurs extraient des informations de ces documents. Par exemple, pour tous les documents de renouvellement de contrat identifiés dans votre bibliothèque de documents, les colonnes s’affichent dans votre affichage qui indiquent également la *date de début du service* et *client* pour chaque document de renouvellement de contrat. 

Vous pouvez utiliser des fichiers d’exemple pour former et tester vos classificateurs et extracteurs de votre modèle. Les exemples de fichiers fournissent vos exemples de modèles à rechercher lorsque vous essayez d’identifier et d’extraire des données de fichiers. Par exemple, vous devez former vos classificateurs et extracteurs de renouvellement de contrat avec des exemples de documents de renouvellement de contrat que votre entreprise utilise. Vous pouvez également utiliser des exemples de fichiers pour tester l’efficacité de votre modèle.

Une fois que vous avez publié votre modèle, utilisez le centre de contenu pour l’appliquer à toute bibliothèque de documents SharePoint à laquelle vous avez accès.  



## <a name="see-also"></a>Voir aussi
[Créer un classificateur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)

[Créer un centre de contenu](create-a-content-center.md)

[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)

[Appliquer un modèle](apply-a-model.md)   

[Différence entre la compréhension de document et les modèles de traitement de formulaire](difference-between-document-understanding-and-form-processing-model.md)
  
[Vue d’ensemble du traitement des formulaires](form-processing-overview.md)
