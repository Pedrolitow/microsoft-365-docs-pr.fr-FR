---
title: Vue d’ensemble de la compréhension de document dans Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.customer: intro-overview
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez la compréhension de document dans Microsoft SharePoint Syntex.
ms.openlocfilehash: 639decf383e534253b014366d9d8c51a83a76675
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822735"
---
# <a name="document-understanding-overview-in-microsoft-sharepoint-syntex"></a>Vue d’ensemble de la compréhension de document dans Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSu7]

</br>

La compréhension de document utilise les modèles de renseignements artificiels pour automatiser la classification des fichiers et l’extraction des informations. Il fonctionne de façon optimale avec les documents non structurés, tels que les lettres ou les contrats. Ces documents doivent comporter du texte qui peut être identifié sur la base de phrases ou de modèles. Le texte identifié désigne à la fois le type de fichier (sa classification) et ce que vous voulez extraire (ses extracteurs).

> [!NOTE]
> Pour plus d’informations sur les exemples de scénarios relatifs aux exemples de scénarios, consultez l’article [SharePoint Syntex adoption : Guide de démarrage](./adoption-getstarted.md).

Les modèles de compréhension de document sont créés et gérés dans un site de type SharePoint appelé un *centre de contenu* . Lorsqu’il est appliqué à une bibliothèque de documents SharePoint, le modèle associé à un type de contenu inclut des colonnes pour stocker les informations extraites. Le type de contenu que vous créez est stocké dans la Galerie de types de contenu SharePoint. Vous pouvez également choisir d’utiliser des types de contenu existants pour utiliser leur schéma.

> [!NOTE]
> Les types de contenus scellés ou en lecture seule ne peuvent pas être mis à jour. Ils ne peuvent donc pas être utilisés dans un modèle.

Ajoutez *des classifieurs* et *des extracteurs* à vos modèles de compréhension de document pour effectuer les actions suivantes :

- Les classificateurs sont utilisés pour identifier et classer les documents téléchargés vers la bibliothèque de documents. Par exemple, un classifieur peut être « exercé » pour identifier tous les documents *renouvellement de contrat* qui sont chargés dans la bibliothèque. Le type de contenu renouvellement contrat est défini par vous lorsque vous créez votre classifieur.

- Les extracteurs extraient des informations de ces documents. Par exemple, pour chaque document de renouvellement de contrat identifié dans votre bibliothèque de documents, les colonnes affichent la *date de début du service* et le *client* pour chaque document. 

Vous pouvez utiliser des fichiers d’exemple pour former et tester vos classificateurs et extracteurs de votre modèle. Les exemples de fichiers fournissent vos exemples de modèles à rechercher lorsque vous essayez d’identifier et d’extraire des données de fichiers. Par exemple, vous devez former vos classificateurs et extracteurs de renouvellement de contrat avec des exemples de documents de renouvellement de contrat que votre entreprise utilise. Vous pouvez également utiliser des exemples de fichiers pour tester l’efficacité de votre modèle.

Une fois que vous avez publié votre modèle, utilisez le centre de contenu pour l’appliquer à toute bibliothèque de documents SharePoint à laquelle vous avez accès.  

## <a name="file-limitations"></a>Limitations de fichier

Les modèles de compréhension de document utilisent la technologie de reconnaissance optique de caractères (OCR) pour analyser les fichiers PDF, les images et les fichiers TIFF. Les fichiers sont analysés lorsque vous entraînez un modèle avec des exemples de fichiers et lorsque vous exécutez le modèle sur des fichiers dans une bibliothèque de documents.

Notez les différences suivantes concernant Microsoft Office fichiers textuels et les fichiers analysés par OCR (PDF, image ou TIFF) :

- Fichiers Office : nous avons tronqué à 64 000 caractères (lors de la formation et de l’exécution sur des fichiers dans une bibliothèque de documents).

- Fichiers numérisés par OCR : la limite est de 20 pages.  

### <a name="requirements"></a>Conditions requises

Le traitement OCR fonctionne mieux sur des documents respectant les conditions requises suivantes :

- Format JPG, PNG ou PDF (texte ou numérisé). Les PDF à texte incorporé sont meilleurs car il n’existe aucune erreur d’emplacement et d’extraction de caractères.

- Si vos PDF sont verrouillés par mot de passe, vous devez supprimer le verrou avant de les envoyer.

- La taille de fichier combinée des documents par collection utilisés pour la formation ne doit pas dépasser 50 Mo et les documents PDF ne doivent pas contenir plus de 500 pages.

- Pour les images, les dimensions doivent être comprises entre 50 x 50 et 10 000 x 10 000 pixels.
   > [!NOTE]
   > Les images très larges ou ayant des dimensions spéciales (par exemple, des plans au sol) peuvent être tronquées dans le processus OCR et perdre en précision.

- Pour les fichiers PDF, les dimensions doivent se situer à 17 x 17 pouces au maximum, ce qui correspond à des tailles de papier A3 ou Légal, ou plus petites.

- S’ils sont numérisés à partir de documents sur papier, les numérisations devraient être des images de qualité supérieure.

- Doit utiliser l’alphabet latin (caractères anglais).

> [!NOTE]
> Le générateur d’intelligence artificielle ne prend actuellement pas en charge les types suivants de formulaires traitant des données entrantes :
>
> - Cases à cocher ou cases d’option
> - Signatures
> - FICHIERS PDF fillables

### <a name="supported-file-types"></a>Types de fichiers pris en charge

Les modèles de compréhension des documents suivent les types de fichiers suivants :

- doc
- docx
- eml
- heic
- heif
- htm
- html
- jpeg
- jpg
- Markdown
- md
- msg
- pdf
- png
- ppt
- pptx
- rtf
- tif
- tiff
- txt
- xls
- xlsx

### <a name="supported-languages"></a>Langues prises en charge

Les modèles de compréhension des documents prennent en charge *toutes les* langues latines, notamment :

- Anglais
- Français
- Allemand
- Italien
- Espagnol

## <a name="see-also"></a>Voir aussi

[Créer un classifieur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)

[Créer un centre de contenu](create-a-content-center.md)

[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)

[Appliquer un modèle](apply-a-model.md)

[Différence entre la compréhension de document et les modèles de traitement de formulaire](difference-between-document-understanding-and-form-processing-model.md)
  
[Vue d’ensemble du traitement des formulaires](form-processing-overview.md)

[Mode d’accessibilité Syntex de SharePoint](accessibility-mode.md)
