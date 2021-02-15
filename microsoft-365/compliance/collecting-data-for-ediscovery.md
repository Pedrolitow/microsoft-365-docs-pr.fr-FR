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
description: Découvrez comment identifier un ensemble de documents à réviser dans une enquête à l’aide de l’outil de recherche dans Advanced eDiscovery.
ms.custom: seo-marvel-2020
ms.openlocfilehash: b69127f1a372a9b843b9c7dac1b2909dd80b2988
ms.sourcegitcommit: 98b889e674ad1d5fa37d4b6c5fc3eda60a1d67f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "49751265"
---
# <a name="collect-data-for-a-case-in-advanced-ediscovery"></a>Collecter des données pour un cas dans Advanced eDiscovery

Une fois que vous avez identifié les dépositaires et les sources de données qui sont pertinents pour votre cas, il est temps d’identifier l’ensemble de documents à explorer. Vous pouvez utiliser l’outil de recherche dans Advanced eDiscovery pour identifier les documents pertinents à partir d’emplacements privatives et non privatives dans Microsoft 365.

Après avoir exécuté une recherche, vous pouvez afficher des statistiques sur les éléments récupérés, tels que les emplacements qui ont le plus d’éléments qui correspondent à la requête de recherche. Vous pouvez également afficher un aperçu d’un sous-ensemble des résultats. Une fois que vous avez identifié l’ensemble de documents que vous souhaitez examiner plus en détail, vous pouvez ajouter les résultats de la recherche à un ensemble de révisions à collecter et à traiter.

## <a name="create-a-search"></a>Créer une recherche

La sélection **d’une** nouvelle recherche sous **l’onglet Recherches** démarre un Assistant qui vous guide tout au long de la création d’une recherche. Pour plus d’informations sur la création d’une recherche, voir [Créer une recherche pour collecter des données.](create-search-to-collect-data.md)

Une fois la recherche créée, une page volante avec des détails s’affiche. Les **boutons Statistiques** et **Aperçu** ne sont initialement pas disponibles, car la recherche n’est pas encore terminée. Vous pouvez effectuer le suivi de la progression de la recherche sous **l’onglet Recherches.**

## <a name="view-search-results-and-statistics"></a>Afficher les résultats de recherche et les statistiques

Il existe deux composants d’une recherche de contenu : Statistiques (Estimations) et Aperçu. Lorsque chacun de ces composants est terminé, l’état affiché  dans les colonnes  correspondantes de l’onglet Recherches passe de Soumis à En cours à **Terminé.** 

Une fois l’estimation de la recherche terminée, sélectionnez la recherche pour afficher la page volante, qui affichera des statistiques de haut niveau sur les résultats de la recherche. À ce stade, le bouton **Statistiques** est actif. Vous pouvez le sélectionner pour voir les statistiques de recherche, telles que :

- Résumé
- Emplacements principaux
- Requêtes

Pour plus d’informations sur les statistiques de recherche, voir [Statistiques de recherche.](search-statistics-in-advanced-ediscovery.md)

Une fois l’aperçu terminé, le bouton **Aperçu** est actif. Sélectionnez-le pour afficher un aperçu d’un sous-ensemble échantillondé des résultats.

## <a name="add-search-results-to-a-review-set"></a>Ajouter des résultats de recherche à un jeu à réviser

Lorsque vous êtes prêt à collecter et traiter l’ensemble des résultats d’une recherche, vous pouvez le faire en l’ajoutant à un jeu à réviser. Pour plus d’informations, voir [Ajouter des données à un jeu à réviser.](add-data-to-review-set.md)

## <a name="add-non-microsoft-365-data-to-a-review-set"></a>Ajouter des données non-Microsoft 365 à un jeu à réviser

Dans le cadre du processus de collecte d’un cas, vous pouvez également ajouter des données autres qu’Office 365 à un groupe de révision et examiner et analyser avec les données Office 365 que vous avez collectées à l’aide de l’outil de recherche. Lorsque vous ajoutez un dossier autre qu’Office 365, vous devez l’associer à un dépositaire spécifique dans le cas. Pour plus d’informations, voir Charger des données [non-Microsoft 365 dans un jeu à réviser.](load-non-Office-365-data-into-a-review-set.md)
