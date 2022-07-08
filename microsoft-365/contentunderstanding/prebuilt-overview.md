---
title: Vue d’ensemble des modèles prédéfinis dans Microsoft SharePoint Syntex
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
description: Découvrez les modèles prédéfinis dans Microsoft SharePoint Syntex.
ms.openlocfilehash: 47579f640e02874545177946534d81f1350104cd
ms.sourcegitcommit: ebaa70d0da4a600efe52b5008eaddb511d36df8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2022
ms.locfileid: "66687671"
---
# <a name="prebuilt-models-overview-in-microsoft-sharepoint-syntex"></a>Vue d’ensemble des modèles prédéfinis dans Microsoft SharePoint Syntex

En plus de [documenter la compréhension des modèles](document-understanding-overview.md) et des [modèles de traitement des formulaires](form-processing-overview.md), SharePoint Syntex fournit des modèles prédéfinis pour automatiser l’extraction des informations.

Les modèles prédéfinis sont préentraînés pour reconnaître les documents et les informations structurées dans les documents. Au lieu de devoir créer un modèle personnalisé à partir de zéro, vous pouvez itérer sur un modèle préentraîné existant pour ajouter des champs spécifiques qui répondent aux besoins de votre organisation. 

Les modèles prédéfinis utilisent la reconnaissance optique de caractères (OCR) combinée avec des modèles d’apprentissage profond pour identifier et extraire du texte prédéfini et des champs de données communs à des types de documents spécifiques. Vous commencez par analyser l’un de vos fichiers sur le modèle prédéfini. Vous sélectionnez ensuite les champs détectés qui ont un sens pour votre objectif. Si le modèle ne détecte pas les champs dont vous avez besoin, vous pouvez analyser à nouveau à l’aide d’un autre fichier.

Comme les modèles de compréhension de document, les modèles prédéfinis sont créés et gérés dans le [centre de contenu](create-a-content-center.md). Lorsqu’il est appliqué à une bibliothèque de documents SharePoint, le modèle est associé à un type de contenu et comporte des colonnes pour stocker les informations extraites. 

Une fois que vous avez publié votre modèle, utilisez le centre de contenu pour l’appliquer à toute bibliothèque de documents SharePoint à laquelle vous avez accès.  

## <a name="requirements"></a>Configuration requise

- Formats de fichier pris en charge : JPEG, PNG, BMP, TIFF et PDF (texte incorporé ou analysé).

- Langues prises en charge : seules les factures en anglais de la États-Unis sont actuellement prises en charge. Les recettes de ventes anglaises provenant de l’Australie, du Canada, du États-Unis, de la Grande-Bretagne et de l’Inde sont prises en charge.

- Les fichiers PDF incorporés au texte sont préférables pour éliminer le risque d’erreur dans l’extraction et l’emplacement des caractères.

- Pour PDF et TIFF, jusqu’à 2 000 pages peuvent être traitées.

- La taille du fichier doit être inférieure à 50 Mo.

- Les dimensions de l’image doivent être comprises entre 50 x 50 pixels et 10 000 x 10 000 pixels.

- Les dimensions PDF sont jusqu’à 17 x 17 pouces, correspondant à la taille de papier Legal ou A3, ou plus petite.

- La taille totale des données d’apprentissage est de 500 pages ou moins.

### <a name="file-limitations"></a>Limitations de fichier

Notez les différences suivantes concernant les fichiers texte Microsoft Office et les fichiers analysés par OCR (PDF, image ou TIFF) :

- Fichiers Office : tronqués à 64 000 caractères (lorsqu’ils sont exécutés sur des fichiers dans une bibliothèque de documents).

- Fichiers numérisés par OCR : la limite est de 20 pages.  

## <a name="model-considerations"></a>Considérations relatives au modèle

- Si deux modèles prédéfinis ou plus sont appliqués à la même bibliothèque, le fichier est classé à l’aide du modèle qui a le score de confiance moyen le plus élevé. Les entités extraites proviennent uniquement du modèle appliqué.

- Si un modèle prédéfini est appliqué à une bibliothèque qui a un modèle de traitement de formulaire personnalisé, le fichier est classé à l’aide du modèle prédéfini et des extracteurs détectés pour ce modèle. S’il existe des colonnes vides qui correspondent au modèle de traitement de formulaire, les colonnes sont remplies à l’aide de ces valeurs extraites.

- L’application de plusieurs modèles de traitement de formulaire personnalisés à une bibliothèque n’est pas prise en charge.

## <a name="see-also"></a>Voir aussi

[Utiliser un modèle prédéfini pour extraire des informations à partir de factures ou de reçus](prebuilt-overview.md)
 

