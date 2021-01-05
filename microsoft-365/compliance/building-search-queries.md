---
title: Créer des requêtes de recherche dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom: seo-marvel-mar2020
description: Utilisez des mots clés et des conditions pour limiter l’étendue de la recherche lors de la recherche de données à l’aide de Advanced eDiscovery dans Microsoft 365.
ms.openlocfilehash: 8ec1e099625bb081f8a915f08ac818fddcc2b60d
ms.sourcegitcommit: 98b889e674ad1d5fa37d4b6c5fc3eda60a1d67f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "49751111"
---
# <a name="build-search-collection-queries-in-advanced-ediscovery"></a>Créer des requêtes de collection de recherche dans Advanced eDiscovery

Lors de la création de requêtes de recherche pour collecter des données dans un cas avancé de découverte électronique, vous pouvez utiliser des mots clés pour rechercher du contenu et des conditions spécifiques afin de limiter l’étendue de la recherche afin de renvoyer les éléments les plus pertinents pour votre enquête légale.

![Utiliser des mots clés et des conditions pour affiner les résultats d’une recherche](../media/SearchQueryBox.png)

## <a name="keyword-searches"></a>Recherches par mots clés

Tapez une requête de mot clé dans la zone **Mots clés** de la requête de recherche. Vous pouvez spécifier des mots clés, des propriétés de message électronique, tels que des dates d’envoi et de réception, ou des propriétés de document, telles que des noms de fichiers ou la date de la dernière modification d’un document. Vous pouvez utiliser des requêtes plus complexes qui utilisent un opérateur booléen, tels que **ET**, **OU**, **PAS**, et **PRÈS**. Vous pouvez également rechercher des informations sensibles (telles que des numéros de sécurité sociale) dans des documents dans SharePoint et OneDrive (pas dans les messages électroniques) ou Rechercher des documents qui ont été partagés en externe. Si vous laissez la zone **Mot clé** vide, tout le contenu se trouvant dans les emplacements de contenu spécifiés est dans les résultats de recherche.

## <a name="keyword-list"></a>Liste de mots clés

Vous pouvez également activer la case à cocher **afficher la liste des mots clés** et taper un mot clé ou une phrase de mots clés dans chaque ligne. Les mots clés de chaque ligne sont connectés par un opérateur logique (représenté par *c :s* dans la syntaxe de requête de recherche) qui est semblable à l’opérateur **or** de la requête de recherche qui est créée. Cela signifie que les éléments qui contiennent un mot clé dans n’importe quelle ligne se trouvent dans les résultats de la recherche. Vous pouvez ajouter jusqu’à 180 lignes dans la liste de mots clés dans les requêtes de recherche avancée de découverte électronique.

![Utiliser la liste de mots clés pour obtenir des statistiques sur chaque mot clé dans la requête](../media/KeywordListSearch.png)

Pourquoi utiliser la liste de mots clés ? Vous pouvez obtenir des statistiques qui indiquent le nombre d’éléments qui correspondent à chaque mot clé dans la liste de mots clés. Cela peut vous aider à identifier rapidement les mots clés qui sont les plus efficaces (et les moins). Vous pouvez également utiliser une phrase de mots clés (entourée de parenthèses) dans une ligne de la liste des mots-clés. Pour plus d’informations sur les statistiques de recherche, voir statistiques de la [recherche](search-statistics-in-advanced-ediscovery.md).

## <a name="conditions"></a>Conditions

Vous pouvez ajouter des conditions de recherche pour affiner l’étendue d’une recherche et renvoyer un ensemble de résultats plus raffiné. Chaque condition ajoute une clause à la requête de recherche qui est créée et exécutée lorsque vous démarrez la recherche. Une condition est logiquement connectée à la requête de mot-clé spécifiée dans la zone de mot clé par un opérateur logique (représenté par *c :c* dans la syntaxe de requête de recherche) qui est similaire à la fonctionnalité de l’opérateur **and** . Cela signifie que les éléments doivent satisfaire à la fois la requête de mot clé et une ou plusieurs conditions à inclure dans les résultats de la recherche. C’est ainsi que les conditions contribuent à affiner vos résultats. Pour obtenir la liste et la description des conditions que vous pouvez utiliser dans une requête de recherche, consultez la section « conditions de recherche » dans la rubrique [requêtes de mots clés et conditions de recherche](keyword-queries-and-search-conditions.md#search-conditions).
