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
description: Utilisez des mots clés et des conditions pour restreindre l’étendue de la recherche lors de la recherche de données à l’aide Advanced eDiscovery dans Microsoft 365.
ms.openlocfilehash: 00a5ab1c009f0c006aba251c770c87c1f7569fc1
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59164153"
---
# <a name="build-search-queries-for-collections-in-advanced-ediscovery"></a>Créer des requêtes de recherche pour les collections dans Advanced eDiscovery

Lors de la configuration de la requête de recherche lors de la création d’une [collection](collections-overview.md) dans un cas Advanced eDiscovery, vous pouvez utiliser des mots clés pour rechercher du contenu et des conditions spécifiques afin de restreindre l’étendue de la recherche afin de renvoyer les éléments les plus pertinents pour votre enquête juridique.

![Utilisez des mots clés et des conditions pour affiner les résultats d’une recherche.](../media/SearchQueryBox.png)

## <a name="keyword-searches"></a>Recherches par mots clés

Tapez une requête de mot clé dans la zone **Mots clés** de la requête de recherche. Vous pouvez spécifier des mots clés, des propriétés de message électronique, telles que des dates d’envoi et de réception, ou des propriétés de document, telles que les noms de fichiers ou la date de la dernière fois où un document a été modifié. Vous pouvez utiliser des requêtes plus complexes qui utilisent un opérateur booléen, tels que **ET**, **OU**, **PAS**, et **PRÈS**. Vous pouvez également rechercher des informations sensibles (telles que des numéros de sécurité sociale) dans des documents en SharePoint et OneDrive (pas dans les messages électroniques) ou rechercher des documents qui ont été partagés en externe. Si vous laissez la zone **Mot clé** vide, tout le contenu se trouvant dans les emplacements de contenu spécifiés est dans les résultats de recherche.

## <a name="keyword-list"></a>Liste de mots clés

Vous pouvez également cocher la case Afficher la liste des mots clés et taper un mot clé ou une expression de mot clé dans chaque ligne.  Les mots clés de chaque ligne sont connectés par un opérateur logique (qui est représenté par *c:s* dans la syntaxe de requête de recherche) qui est similaire en fonctionnalité à l’opérateur **OR** dans la requête de recherche qui est créée. Cela signifie que les éléments qui contiennent un mot clé dans une ligne sont dans les résultats de la recherche. Vous pouvez ajouter jusqu’à 180 lignes dans la liste de mots clés dans Advanced eDiscovery requêtes de recherche.

![Utilisez la liste de mots clés pour obtenir des statistiques sur chaque mot clé dans la requête.](../media/KeywordListSearch.png)

Pourquoi utiliser la liste de mots clés ? Vous pouvez obtenir des statistiques qui indiquent le nombre d’éléments qui correspondent à chaque mot clé dans la liste de mots clés. Cela peut vous aider à identifier rapidement les mots clés les plus (et les moins) efficaces. Vous pouvez également utiliser une expression de mot clé (entre parenthèses) dans une ligne de la liste des mots clés. Pour plus d’informations sur les statistiques de recherche, voir [Statistiques de recherche.](search-statistics-in-advanced-ediscovery.md)

## <a name="conditions"></a>Conditions

Vous pouvez ajouter des conditions de recherche pour restreindre l’étendue d’une recherche et renvoyer un ensemble de résultats plus affiné. Chaque condition ajoute une clause à la requête de recherche qui est créée et exécutée lorsque vous démarrez la recherche. Une condition est connectée logiquement à la requête de mot clé spécifiée dans la zone de mot clé par un opérateur logique (représenté par *c:c* dans la syntaxe de requête de recherche) qui est similaire en fonctionnalité à l’opérateur **AND.** Cela signifie que les éléments doivent satisfaire la requête de mot clé et une ou plusieurs conditions à inclure dans les résultats de la recherche. C’est ainsi que les conditions contribuent à affiner vos résultats. Pour obtenir la liste et la description des conditions que vous pouvez utiliser dans une requête de recherche, consultez la section « Conditions de recherche » dans requêtes par mot clé et [conditions de recherche.](keyword-queries-and-search-conditions.md#search-conditions)
