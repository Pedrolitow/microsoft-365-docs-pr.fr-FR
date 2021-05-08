---
title: Étape 1. Utiliser SharePoint Syntex pour identifier les fichiers de contrat et extraire des données
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: 05/10/2021
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment utiliser SharePoint Syntex pour identifier les fichiers de contrat et extraire des données à l’aide d’Microsoft 365 solution.
ms.openlocfilehash: e0d58164d1a12987a4606ef84c15fa3d20c0195f
ms.sourcegitcommit: 8e4c107e4da3a00be0511b05bc655a98fe871a54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52281214"
---
# <a name="step-1-use-sharepoint-syntex-to-identify-contract-files-and-extract-data"></a>Étape 1. Utiliser SharePoint Syntex pour identifier les fichiers de contrat et extraire des données

Votre organisation a besoin d’un moyen d’identifier et de classer tous les documents de contrat parmi les nombreux fichiers que vous recevez. Vous souhaitez également être en mesure d’afficher rapidement plusieurs éléments clés dans chacun des fichiers de contrat identifiés (par exemple, *client,* fournisseur *et* montant *des frais).* Pour ce faire, vous pouvez utiliser [SharePoint Syntex](index.md) pour créer un modèle de compréhension de document et l’appliquer à une bibliothèque de documents.

[La compréhension des documents](document-understanding-overview.md) utilise des modèles d’intelligence artificielle (IA) pour automatiser la classification des fichiers et l’extraction des informations. Les modèles de compréhension des documents sont également optimaux pour extraire des informations à partir de documents non structurés et semi-structurés où les informations dont vous avez besoin ne sont pas contenues dans des tableaux ou des formulaires, tels que des contrats.

1. Tout d’abord, vous devez trouver au moins cinq exemples de fichiers que vous pouvez utiliser pour « former » le modèle afin de rechercher des caractéristiques spécifiques au type de contenu que vous essayez d’identifier (contrat). 

2. À l SharePoint Syntex, créez un modèle de compréhension de document. À l’aide de vos exemples de fichiers, vous devez [créer un classificateur](create-a-classifier.md). En formeant le classifieur avec vos exemples de fichiers, vous lui apprenez à rechercher des caractéristiques spécifiques à ce que vous verrez dans les contrats de votre entreprise. Par exemple, [créez une «](create-a-classifier.md#create-an-explanation) explication » qui recherche des chaînes spécifiques dans vos contrats, telles que le contrat de *service,* les conditions *d’contrat* et la *rémunération.* Vous pouvez même former votre explication pour rechercher ces chaînes dans des sections spécifiques du document ou en regard d’autres chaînes. Lorsque vous pensez avoir formé votre classificateur avec les informations dont il a besoin, vous pouvez tester votre modèle sur un exemple de fichiers d’exemples pour voir son efficacité. Après le test, si nécessaire, vous pouvez choisir d’apporter des modifications à vos explications pour les rendre plus efficaces. 

3. Dans votre modèle, vous pouvez créer [un extracteur](create-an-extractor.md) pour extraire des éléments de données spécifiques de chaque contrat. Par exemple, pour chaque contrat, les informations qui vous intéressent le plus sont qui est le client, le nom de l’indépendant et le coût total.

4. Une fois que vous avez créé votre modèle, appliquez-le à [une bibliothèque SharePoint documents.](apply-a-model.md) Lorsque vous téléchargez des documents dans la bibliothèque de documents, votre modèle de compréhension des documents s’exécute et identifie et classifie tous les fichiers qui correspondent au type de contenu de contrat que vous avez défini dans votre modèle. Tous les fichiers classés en tant que contrats s’affichent dans un affichage bibliothèque personnalisé. Les fichiers affichent également les valeurs de chaque contrat que vous avez défini dans votre extracteur.

   ![Contrats dans la bibliothèque de documents](../media/content-understanding/doc-lib-solution.png)

5. En outre, si vous avez des exigences de rétention [](apply-a-retention-label-to-a-model.md) pour vos contrats, vous pouvez également utiliser votre modèle pour appliquer une étiquette de rétention qui empêchera la suppression de vos contrats pendant une période spécifiée.

## <a name="next-step"></a>Étape suivante

[Étape 2. Utiliser Microsoft Teams pour créer votre canal de gestion de contrat](solution-manage-contracts-step2.md)