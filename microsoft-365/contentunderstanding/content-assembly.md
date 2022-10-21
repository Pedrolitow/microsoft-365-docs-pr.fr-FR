---
title: Vue d’ensemble de l’assembly de contenu dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: anrasto, shrganguly
ms.topic: article
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment créer des documents et d’autres contenus à l’aide d’un modèle moderne dans Microsoft Syntex.
ms.openlocfilehash: 7b03b50be0243117b12ec08dfcc61a4f88ba8034
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68660442"
---
# <a name="overview-of-content-assembly-in-microsoft-syntex"></a>Vue d’ensemble de l’assembly de contenu dans Microsoft Syntex

Vous pouvez utiliser les fonctionnalités d’assembly de contenu dans Microsoft Syntex pour vous aider à générer automatiquement des documents métier standard répétitifs, tels que des contrats, des déclarations de travail, des contrats de service, des lettres de consentement, des arguments de vente et de la correspondance. Vous pouvez effectuer toutes ces actions plus rapidement, de manière plus cohérente et avec moins d’erreurs en créant des modèles modernes et en utilisant ces modèles pour générer des documents.

![Diagramme du flux de création de documents à partir d’un modèle moderne.](../media/content-understanding/content-assembly-diagram.png)

Vous chargez un document existant pour créer un modèle moderne, puis utilisez ce modèle pour générer automatiquement du nouveau contenu à l’aide de listes SharePoint ou d’entrées manuelles comme source de données.

> [!NOTE]
> Vous devez être un utilisateur Syntex sous licence pour accéder aux fonctionnalités d’assembly de contenu et les utiliser. Vous devez également disposer des autorisations nécessaires pour gérer les listes SharePoint.

## <a name="requirements-and-limitations"></a>Configuration requise et limitations

### <a name="supported-file-types"></a>Types de fichiers pris en charge

Seuls les documents Microsoft Word (.docxl’extension /.doc) sont actuellement pris en charge pour la création d’un modèle.

### <a name="file-limitations"></a>Limitations de fichier

- Le document Word que vous souhaitez utiliser comme modèle moderne ne doit pas inclure de commentaires ni activer le suivi des modifications.

- Étant donné que les contrôles de contenu sont utilisés dans Word pour créer des champs pour le modèle moderne, assurez-vous que les espaces réservés de texte pour les images ne sont pas encapsulés. Si le document contient déjà des contrôles de contenu, supprimez-les avant de l’utiliser pour créer un modèle moderne.

### <a name="current-release-limitations"></a>Limitations actuelles de la version

- Le modèle et le document sont associés à une bibliothèque de documents. Pour utiliser le modèle dans une autre bibliothèque de documents, vous devez recréer le modèle dans cette bibliothèque de documents.

- Le document chargé utilisé pour créer le modèle moderne est enregistré en tant que copie distincte et placé dans le répertoire /forms de la bibliothèque de documents. Le fichier d’origine sur le disque n’est pas affecté.

- Vous pouvez créer des champs pour du texte, ainsi que des champs pour du texte dans des cellules d’un tableau. Toutefois, les images, les illustrations intelligentes, les tableaux complets et les listes à puces ne sont actuellement pas pris en charge.

- Une fois qu’un document est créé à partir d’un modèle, il n’est pas associé au modèle.

## <a name="differences-between-modern-templates-and-other-document-templates"></a>Différences entre les modèles modernes et les autres modèles de document

|Fonctionnalité  |Modèles modernes  |Autres modèles  |
|---------|---------|---------|
|Licences      |Licence Syntex nécessaire pour accéder à cette offre.  |Proposé dans le cadre d’une licence Microsoft E3 ou E5.  |
|Quand utiliser chaque            | Vous devez utiliser pour générer des documents transactionnels standard tels que des contrats de service et des énoncés de travail lorsque seules des parties spécifiques du document changent. Les documents générés à partir de modèles modernes garantissent la cohérence et moins de risques d’erreurs manuelles et de fautes de frappe qui se produisent lorsque les utilisateurs modifient des sections du document en flux libre.  |Vous devez utiliser cette méthode lorsque vous souhaitez définir un document comme exemple pour d’autres utilisateurs. Vous pouvez envisager d’utiliser des modèles standard pour les documents non transactionnels tels que les arguments de vente ou les résumés exécutifs.  |
|Normalisation de la génération de contenu |Vous pouvez ajouter des champs, puis les associer à différentes sources de données uniquement pour des sections spécifiques du contenu afin de permettre aux utilisateurs de générer facilement des documents une fois le modèle publié.  |Une fois chargé, le fichier est conservé tel qu’il est dans le modèle. Tout utilisateur utilisant le modèle doit modifier le contenu en conséquence.   |
|Sources de données prises en charge     |Vous pouvez associer des champs à des listes SharePoint et à un magasin de termes lors de la création de modèles.   |Non applicable   |
|Types de documents pris en charge    |Seuls les documents Microsoft Word (.docxl’extension /.doc) sont actuellement pris en charge pour la création d’un modèle.  |Vous pouvez utiliser n’importe quel fichier pour le charger en tant que modèle.   |
|Gestion des modèles    |Une fois le modèle créé, vous pouvez modifier ou gérer les champs du modèle, renommer le modèle et le republier pour l’utiliser.  |Non applicable   |
|Version brouillon des modèles |Vous pouvez créer des brouillons de versions de modèles avant de les publier pour une utilisation par d’autres utilisateurs.   |Il n’existe aucune possibilité de créer des brouillons de modèles standard.  |
|Flux de travail   |Vous pouvez automatiser la génération de documents à partir de modèles [en configurant des workflows Power Automate](automate-document-generation.md).  |Les workflows ne peuvent pas être configurés avec des modèles standard.  |

> [!div class="nextstepaction"]
> [Prise en main > Créer un modèle moderne](content-assembly-modern-template.md)



 
