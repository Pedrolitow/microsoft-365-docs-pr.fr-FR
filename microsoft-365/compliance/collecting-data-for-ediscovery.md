---
title: Collecter des données pour un cas dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment identifier un ensemble de documents à consulter lors d’une enquête à l’aide de l’outil de recherche dans Advanced eDiscovery.
ms.custom: seo-marvel-2020
ms.openlocfilehash: 725c289324a8e4d5bd4d7a7b9ddd9e091b6d6241
ms.sourcegitcommit: a3c2c737995088c1bad3b12ab401a7ef242b0272
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47956197"
---
# <a name="collect-data-for-a-case-in-advanced-ediscovery"></a>Collecter des données pour un cas dans Advanced eDiscovery

Une fois que vous avez identifié les dépositaires et les sources de données intéressantes pour votre cas, il est temps d’identifier l’ensemble des documents dans lesquels vous souhaitez approfondir votre attention. Vous pouvez utiliser l’outil de recherche dans Advanced eDiscovery pour identifier les documents pertinents d’une absence ou d’une absence privative de marchés dans Microsoft 365.

Après avoir exécuté une recherche, vous pouvez afficher des statistiques sur les éléments récupérés, tels que les emplacements qui ont le plus d’éléments qui correspondent à la requête de recherche. Vous pouvez également afficher un aperçu d’un sous-ensemble des résultats. Une fois que vous avez identifié l’ensemble de documents que vous souhaitez examiner, vous pouvez ajouter les résultats de la recherche à un jeu de vérification pour le collecter et le traiter.

## <a name="create-a-search"></a>Créer une recherche

La sélection de **nouvelle recherche** sous l’onglet **recherches** démarre un assistant qui vous guide tout au long de la procédure de création d’une recherche. Pour plus d’informations sur la création d’une recherche, voir [Create a Search to Collect Data](create-search-to-collect-data.md).

Après la création d’une recherche, une page de menu volant contenant des informations s’affiche. Les **statistiques** et les boutons d' **Aperçu** sont initialement indisponibles car la recherche n’a pas encore été effectuée. Vous pouvez suivre la progression de la recherche dans l’onglet **recherches** .

## <a name="view-search-results-and-statistics"></a>Afficher les statistiques et les résultats de la recherche

Il existe deux composants d’une recherche de contenu : statistiques (estimations) et aperçu. À mesure que chacun de ces composants est terminé, l’état affiché dans les colonnes correspondantes de l’onglet **recherches** passe de **soumis** à **en cours** à **terminé**.

Une fois l’estimation de la recherche terminée, sélectionnez la recherche pour afficher la page de menu volant, qui affiche certaines statistiques de haut niveau sur les résultats de la recherche. À ce stade, le bouton **statistiques** est actif. Vous pouvez le sélectionner pour afficher les statistiques de recherche, telles que :

- Résumé
- Emplacements les plus fréquents
- Requêtes

Pour plus d’informations sur les statistiques de recherche, voir statistiques de la [recherche](search-statistics.md).

Une fois l’aperçu terminé, le bouton **Aperçu** est actif. Sélectionnez-le pour afficher un aperçu d’un sous-ensemble de résultats.

## <a name="add-search-results-to-a-review-set"></a>Ajouter des résultats de recherche à un jeu à réviser

Lorsque vous êtes prêt à collecter et à traiter tous les résultats d’une recherche, vous pouvez le faire en l’ajoutant à un jeu de révision. Pour plus d’informations, consultez [la rubrique ajouter des données à un jeu de vérification](add-data-to-review-set.md).

## <a name="add-non-microsoft-365-data-to-a-review-set"></a>Ajouter des données non-Microsoft 365 à un jeu de révision

Dans le cadre du processus de collecte pour un cas, vous pouvez également ajouter des données non Office 365 à un jeu de réexamens et les examiner et les analyser avec les données Office 365 que vous avez collectées à l’aide de l’outil de recherche. Lorsque vous ajoutez un autre non-Office 365, vous devez l’associer à un dépositaire spécifique dans le cas. Pour plus d’informations, voir [charger des données non-Microsoft 365 dans un jeu de révision](load-non-Office-365-data-into-a-review-set.md).
