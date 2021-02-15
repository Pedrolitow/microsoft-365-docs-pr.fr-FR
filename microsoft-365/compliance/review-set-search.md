---
title: Interroger les données d’un jeu à réviser
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment créer et exécuter une requête dans un jeu à réviser pour organiser les données pour une révision plus efficace dans un cas Advanced eDiscovery.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 1ead897d412af2356d8b57ab8494539a5ed9a019
ms.sourcegitcommit: 3c39866865c8c61bce2169818d8551da65033cfe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "48816567"
---
# <a name="query-the-data-in-a-review-set"></a>Interroger les données d’un jeu à réviser

Dans la plupart des cas, il est utile de pouvoir approfondir les données d’un jeu à réviser et d’organiser ces données pour faciliter une révision plus efficace. L’utilisation de requêtes dans un jeu à réviser vous permet de vous concentrer sur un sous-ensemble de documents qui répondent aux critères de votre révision.

## <a name="creating-and-running-a-query-in-a-review-set"></a>Création et exécution d’une requête dans un jeu à réviser

Pour créer et exécuter une requête sur les documents d’un jeu à réviser, sélectionnez **Nouvelle requête** dans le jeu à réviser. Après avoir nommé votre requête et défini les conditions, sélectionnez **Enregistrer** pour enregistrer et exécuter la requête. Pour exécuter une requête qui a été précédemment enregistrée, sélectionnez une requête enregistrée.

![Examiner les requêtes définies](../media/AeDReviewSetQueries.png)

## <a name="building-a-review-set-query"></a>Création d’une requête de jeu à réviser

Vous pouvez créer une requête à l’aide d’une combinaison de mots clés, propriétés et conditions dans la condition Mots clés. Vous pouvez également grouper des conditions en tant que bloc (appelé groupe *de conditions)* pour créer une requête plus complexe. Pour consulter la liste et la description des propriétés de métadonnées que vous pouvez rechercher, consultez [Champs de métadonnées des documents dans Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).

### <a name="conditions"></a>Conditions

Chaque champ utilisable dans une recherche dans un jeu à réviser a une condition correspondante que vous pouvez utiliser pour créer votre requête.

Il existe plusieurs types de conditions :

- Texte libre : une condition de texte libre est utilisée pour les champs de texte tels que l’objet. Vous pouvez lister plusieurs termes de recherche en les séparant par une virgule.

- Date : une condition de date est utilisée pour les champs de date tels que la date de dernière modification.

- Options de recherche : une condition d’options de recherche fournit une liste des valeurs possibles pour le champ particulier dans votre jeu à réviser. Il est utilisé pour les champs, tels que l’expéditeur, où il existe un nombre fini de valeurs possibles dans votre jeu à réviser.

- Mot clé : une condition de mot clé est une instance spécifique de condition de texte libre que vous pouvez utiliser pour rechercher des termes ou utiliser un langage de requête KQL. Pour plus d’informations, voir ci-dessous.

### <a name="query-language"></a>Langage de requête

Outre les conditions, vous pouvez utiliser un langage de requête KQL dans la condition Keywords pour créer votre requête. Le langage de requête pour les requêtes de jeu à réviser prend en charge les opérateurs booléens standard, tels que **AND**, **OR**, **NOT** et **NEAR**. Il prend également en charge un caractère générique à caractère unique (?) et un caractère générique à plusieurs caractères (*).

## <a name="filters"></a>Filtres

Outre les requêtes que vous pouvez enregistrer, vous pouvez utiliser des filtres de jeu à réviser pour appliquer rapidement des conditions supplémentaires à une requête de jeu à réviser. L’utilisation de filtres vous permet d’affiner davantage les résultats affichés par une requête de jeu à réviser.

![Passer en revue les filtres](../media/AeDReviewSetFilters.png)

Les filtres diffèrent des requêtes de deux manières significatives :

- Les filtres sont temporaires. Elles ne persistent pas au-delà de la session existante. En d’autres termes, vous ne pouvez pas enregistrer un filtre. Les requêtes sont enregistrées dans le jeu à réviser et y accèdent chaque fois qu’elles ouvrent le jeu à réviser.

- Les filtres sont toujours additives. Les filtres sont appliqués en plus de la requête de jeu à réviser actuelle. L’application d’une autre requête a pour effet de remplacer les résultats renvoyés par la requête actuelle.
