---
title: Vue d’ensemble des modèles pré-SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.customer: intro-overview
ms.prod: microsoft-365-enterprise
search.appverid: null
ms.collection:
  - enabler-strategic
  - m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez les modèles pré-SharePoint Syntex.
---

# <a name="prebuilt-models-overview-in-microsoft-sharepoint-syntex"></a>Vue d’ensemble des modèles pré-SharePoint Syntex

Outre la [compréhension des modèles de document](document-understanding-overview.md) et des modèles de traitement des formulaires[, SharePoint Syntex](form-processing-overview.md) des modèles pré-écrits pour automatiser l’extraction des informations.

Les modèles pré-conçus sont préentraînés pour reconnaître les documents et les informations structurées dans les documents. Au lieu de devoir créer un modèle personnalisé à partir de zéro, vous pouvez itérer sur un modèle pré-formé existant pour ajouter des champs spécifiques qui correspondent aux besoins de votre organisation. 

Les modèles prédéfincis utilisent la reconnaissance optique de caractères (OCR) associée à des modèles d’apprentissage profond pour identifier et extraire des champs de données et de texte prédéfinés communs à des types de documents spécifiques. Commencez par analyser l’un de vos fichiers par rapport au modèle pré-existant. Vous sélectionnez ensuite les champs détectés qui sont logiques pour votre objectif. Si le modèle ne détecte pas les champs dont vous avez besoin, vous pouvez analyser à nouveau à l’aide d’un autre fichier.

Comme les modèles de compréhension de documents, les modèles pré-créés sont créés et gérés dans le [centre de contenu](create-a-content-center.md). Lorsqu’il est appliqué à SharePoint bibliothèque de documents, le modèle est associé à un type de contenu et possède des colonnes pour stocker les informations en cours d’extraction. 

Une fois que vous avez publié votre modèle, utilisez le centre de contenu pour l’appliquer à toute bibliothèque de documents SharePoint à laquelle vous avez accès.  

## <a name="requirements"></a>Conditions requises

- Formats de fichiers pris en charge : JPEG, PNG, BMP, TIFF et PDF (texte incorporé ou analysé).

- Les PDF textuels sont les meilleurs pour éliminer le risque d’erreur dans l’extraction et l’emplacement des caractères.

- Pour PDF et TIFF, jusqu’à 2 000 pages peuvent être traitées.

- La taille du fichier doit être inférieure à 50 Mo.

- Les dimensions de l’image doivent être entre 50 x 50 pixels et 10 000 x 10 000 pixels.

- Les dimensions PDF sont jusqu’à 17 x 17 pouces, correspondant à la taille de papier Légal ou A3 ou plus petite.

- La taille totale des données de formation est de 500 pages ou moins.

### <a name="file-limitations"></a>Limitations de fichier

Notez les différences suivantes concernant Microsoft Office texte et les fichiers analysés par OCR (PDF, image ou TIFF) :

- Office fichiers : tronqués à 64 000 caractères (lorsqu’ils sont exécutés sur des fichiers d’une bibliothèque de documents).

- Fichiers numérisés par OCR : la limite est de 20 pages.  

## <a name="model-considerations"></a>Considérations sur le modèle

- Si au moins deux modèles pré-pré-préentés sont appliqués à la même bibliothèque, le fichier est classé à l’aide du modèle qui présente le score de confiance moyen le plus élevé. Les entités extraites seront du modèle appliqué uniquement.

- Si un modèle pré-projet est appliqué à une bibliothèque qui possède un modèle de compréhension de document, le fichier est classé à l’aide du modèle de compréhension du document et de tous les extracteurs entraînés pour ce modèle. S’il existe des colonnes vides qui correspondent au modèle pré-projet, les colonnes sont remplies à l’aide de ces valeurs extraites.

- Si un modèle pré-conçu est appliqué à une bibliothèque qui dispose d’un modèle de traitement de formulaire personnalisé, le fichier est classé à l’aide du modèle pré-pré-conçu et des extracteurs détectés pour ce modèle. S’il existe des colonnes vides qui correspondent au modèle de traitement de formulaire, les colonnes sont remplies à l’aide de ces valeurs extraites.

- L’application de plusieurs modèles de traitement de formulaire personnalisés à une bibliothèque n’est pas prise en charge.


## <a name="see-also"></a>Voir aussi

[Utiliser un modèle préétacé pour extraire des informations de factures ou de reçus](prebuilt-overview.md)
 

