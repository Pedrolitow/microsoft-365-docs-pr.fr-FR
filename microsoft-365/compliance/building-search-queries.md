---
title: Générer des requêtes de recherche dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom: seo-marvel-mar2020
description: Utilisez des mots clés et des conditions pour limiter l’étendue de la recherche lors de la recherche de données à l’aide d’eDiscovery (Premium) dans Microsoft 365.
ms.openlocfilehash: afb033a014528b7e79a6ce192896f4b2b3eef054
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096135"
---
# <a name="build-search-queries-for-collections-in-ediscovery-premium"></a>Créer des requêtes de recherche pour les collections dans eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Lors de la configuration de la requête de recherche lors de la création d’une [collection](collections-overview.md) dans un cas eDiscovery (Premium), vous pouvez utiliser des mots clés pour rechercher du contenu et des conditions spécifiques afin de limiter l’étendue de la recherche afin de renvoyer les éléments les plus pertinents pour votre enquête légale.

![Utilisez des mots clés et des conditions pour affiner les résultats d’une recherche.](../media/SearchQueryBox.png)

## <a name="keyword-searches"></a>Recherches par mots clés

Tapez une requête de mot clé dans la zone **Mots clés** de la requête de recherche. Vous pouvez spécifier des mots clés, des propriétés de message électronique, telles que des dates envoyées et reçues, ou des propriétés de document, telles que des noms de fichiers ou la date de dernière modification d’un document. Vous pouvez utiliser des requêtes plus complexes qui utilisent un opérateur booléen, tels que **ET**, **OU**, **PAS**, et **PRÈS**. Vous pouvez également rechercher des informations sensibles (par exemple, des numéros de sécurité sociale) dans des documents dans SharePoint et OneDrive (pas dans les e-mails) ou rechercher des documents qui ont été partagés en externe. Si vous laissez la zone **Mot clé** vide, tout le contenu se trouvant dans les emplacements de contenu spécifiés est dans les résultats de recherche.

## <a name="keyword-list"></a>Liste de mots clés

Vous pouvez également cocher la case **Afficher la liste de mots clés** et taper un mot clé ou une expression clé dans chaque ligne. Les mots clés de chaque ligne sont connectés par un opérateur logique (représenté sous forme *de c:s* dans la syntaxe de requête de recherche) qui est similaire en termes de fonctionnalité à l’opérateur **OR** dans la requête de recherche créée. Cela signifie que les éléments qui contiennent n’importe quel mot clé dans une ligne figurent dans les résultats de la recherche. Vous pouvez ajouter jusqu’à 180 lignes dans la liste de mots clés dans les requêtes de recherche eDiscovery (Premium).

![Utilisez la liste de mots clés pour obtenir des statistiques sur chaque mot clé dans la requête.](../media/KeywordListSearch.png)

Pourquoi utiliser la liste de mots clés ? Vous pouvez obtenir des statistiques qui indiquent le nombre d’éléments correspondant à chaque mot clé dans la liste des mots clés. Cela peut vous aider à identifier rapidement les mots clés les plus efficaces (et les moins efficaces). Vous pouvez également utiliser une expression clé (entourée de parenthèses) dans une ligne dans la liste des mots clés. Pour plus d’informations sur les statistiques de recherche, consultez [statistiques et rapports](collection-statistics-reports.md) de collecte

## <a name="conditions"></a>Conditions

Vous pouvez ajouter des conditions de recherche pour restreindre l’étendue d’une recherche et retourner un ensemble de résultats plus affiné. Chaque condition ajoute une clause à la requête de recherche qui est créée et exécutée lorsque vous démarrez la recherche. Une condition est logiquement connectée à la requête de mot clé spécifiée dans la zone de mot clé par un opérateur logique (représenté sous la forme *c:c* dans la syntaxe de requête de recherche) qui est similaire en termes de fonctionnalité à l’opérateur **AND** . Cela signifie que les éléments doivent satisfaire à la fois à la requête de mot clé et à une ou plusieurs conditions à inclure dans les résultats de la recherche. C’est ainsi que les conditions contribuent à affiner vos résultats. Pour obtenir la liste et la description des conditions que vous pouvez utiliser dans une requête de recherche, consultez la section « Conditions de recherche » dans [les requêtes de mots clés et les conditions de recherche](keyword-queries-and-search-conditions.md#search-conditions).
