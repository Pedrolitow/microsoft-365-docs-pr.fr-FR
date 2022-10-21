---
title: Vue d’ensemble du traitement de documents non structurés dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.custom: intro-overview
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez le modèle de traitement de document non structuré dans Microsoft Syntex.
ms.openlocfilehash: 93ca7e2900098f9067f8c63ea9eae857f61bb7a0
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662355"
---
# <a name="overview-of-unstructured-document-processing-in-microsoft-syntex"></a>Vue d’ensemble du traitement de documents non structurés dans Microsoft Syntex

> [!NOTE]
> *Le traitement des documents non structurés* était connu sous le nom *de compréhension de document* dans les versions précédentes.

<!---
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSu7]

</br>
--->

Utilisez le modèle de traitement de document non structuré ([méthode d’apprentissage](create-syntex-model.md#train-a-custom-model)) pour classifier automatiquement les fichiers et extraire des informations. Il fonctionne mieux pour les documents non structurés, tels que les lettres ou les contrats. 

Le modèle de traitement de documents non structuré (anciennement appelé modèle de compréhension de document) utilise l’intelligence artificielle (IA) pour traiter les documents. Ces documents doivent comporter du texte qui peut être identifié sur la base de phrases ou de modèles. Le texte identifié désigne à la fois le type de fichier (sa classification) et ce que vous voulez extraire (ses extracteurs).

> [!NOTE]
> Pour plus d’informations sur l’utilisation de Syntex et des exemples de scénarios, consultez [Prise en main de l’adoption de Microsoft Syntex](./adoption-getstarted.md) et [Scénarios et cas d’usage pour Microsoft Syntex](./adoption-scenarios.md).

Les modèles de traitement de documents non structurés sont créés et gérés dans un type de site SharePoint appelé [centre de contenu](create-a-content-center.md). Lorsqu’il est appliqué à une bibliothèque de documents SharePoint, le modèle associé à un type de contenu inclut des colonnes pour stocker les informations extraites. Le type de contenu que vous créez est stocké dans la Galerie de types de contenu SharePoint. Vous pouvez également choisir d’utiliser des types de contenu existants pour utiliser leur schéma.

> [!NOTE]
> Les types de contenu en lecture seule ou scellés ne pouvant pas être mis à jour, ils ne peuvent pas être utilisés dans un modèle.

Ajoutez [des classifieurs](create-a-classifier.md) et [des extracteurs](create-an-extractor.md) à vos modèles de traitement de documents non structurés pour effectuer les actions suivantes :

- Les classificateurs sont utilisés pour identifier et classer les documents téléchargés vers la bibliothèque de documents. Par exemple, un classifieur peut être « exercé » pour identifier tous les documents *renouvellement de contrat* qui sont chargés dans la bibliothèque. Le type de contenu renouvellement contrat est défini par vous lorsque vous créez votre classifieur.

- Les extracteurs extraient des informations de ces documents. Par exemple, pour chaque document de renouvellement de contrat identifié dans votre bibliothèque de documents, les colonnes affichent la *date de début du service* et le *client* pour chaque document. 

Vous pouvez utiliser des fichiers d’exemple pour former et tester vos classificateurs et extracteurs de votre modèle. Les exemples de fichiers fournissent vos exemples de modèles à rechercher lorsque vous essayez d’identifier et d’extraire des données de fichiers. Par exemple, vous devez former vos classificateurs et extracteurs de renouvellement de contrat avec des exemples de documents de renouvellement de contrat que votre entreprise utilise. Vous pouvez également utiliser des exemples de fichiers pour tester l’efficacité de votre modèle.

Une fois que vous avez publié votre modèle, utilisez le centre de contenu pour l’appliquer à toute bibliothèque de documents SharePoint à laquelle vous avez accès.  

## <a name="requirements"></a>Conditions requises

Pour plus d’informations sur les exigences à prendre en compte lors du choix de ce modèle, consultez [Configuration requise et limitations des modèles dans Microsoft Syntex](requirements-and-limitations.md#unstructured-document-processing).

## <a name="see-also"></a>Voir aussi

[Comparer des modèles personnalisés](difference-between-document-understanding-and-form-processing-model.md)

