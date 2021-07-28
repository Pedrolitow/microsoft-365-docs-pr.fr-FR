---
title: Statistiques et rapports de collection
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
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
description: Découvrez comment accéder et utiliser des statistiques et des rapports pour les collections provisoires et les collections qui ont été engagés dans un jeu à réviser dans Advanced eDiscovery.
ms.openlocfilehash: e9be02f0c1c1d20639c7120bc0f357a381411b31
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53541024"
---
# <a name="collection-statistics-and-reports-in-advanced-ediscovery"></a>Statistiques et rapports de collecte dans Advanced eDiscovery

Après avoir créé un brouillon de collection, vous pouvez afficher des statistiques sur les éléments récupérés, tels que les emplacements de contenu qui contiennent le plus d’éléments qui correspondent aux critères de recherche et le nombre d’éléments renvoyés par la requête de recherche. Vous pouvez également afficher un aperçu d’un sous-ensemble des résultats.

Une fois que vous avez identifié l’ensemble de documents que vous souhaitez examiner plus en détail, vous pouvez ajouter les résultats de la recherche à un ensemble de révisions à collecter et à traiter.

## <a name="statistics-and-reports-for-draft-collections"></a>Statistiques et rapports pour les collections provisoires

Cette section décrit les statistiques disponibles pour les brouillons de collections. Ces statistiques sont disponibles sous **l’onglet Statistiques** de recherche sur la page volante d’un brouillon de collection.

### <a name="collection-estimates"></a>Estimations de collection

Cette section affiche un résumé graphique des éléments estimés renvoyés par la collection. Cela indique le nombre d’éléments qui correspondent aux critères de recherche de la collection. Ces informations vous donnent une idée du nombre estimé d’éléments renvoyés par la collection.

![Estimations de collection pour un brouillon de collection](../media/AeDCollectionEstimates.png)

- **Éléments estimés par emplacement**: nombre total d’éléments estimés renvoyés par la collection. Le nombre spécifique d’éléments situés dans des boîtes aux lettres et dans des sites est également affiché.

- **Emplacements estimés avec occurrences**: nombre total d’emplacements de contenu qui contiennent des éléments renvoyés par la collection. Le nombre spécifique d’emplacements de boîtes aux lettres et de sites est également affiché.

- **Volume de données par emplacement (en Mo)**: taille totale de tous les éléments estimés renvoyés par la collection. La taille spécifique des éléments de boîte aux lettres et des éléments de site est également affichée.

### <a name="condition-report"></a>Rapport de condition

Cette section affiche des statistiques sur la requête de recherche de collection et le nombre d’éléments estimés qui correspondent à différentes parties de la requête de recherche. Vous pouvez utiliser ces statistiques pour analyser le nombre d’éléments qui correspondent à chaque composant de la requête de recherche. Cela peut vous aider à affiner les critères de recherche de la collection et, si nécessaire, à affiner l’étendue de la collection.

- **Type d’emplacement**: type d’emplacement de contenu applicable aux statistiques de requête. La valeur **de** Exchange indique un emplacement de boîte aux lettres ; une valeur de **SharePoint** indique un emplacement de site.

- **Partie**: partie de la requête de recherche à qui les statistiques s’appliquent. **Le** principal indique l’intégralité de la requête de recherche. **Le** mot clé indique que les statistiques de la ligne sont pour un mot clé spécifique. Si vous utilisez une liste de mots clés pour la requête de recherche dans la collection, les statistiques de chaque composant de la requête sont incluses dans ce tableau.

- **Condition**: composant réel (mot clé ou condition) de la requête de recherche qui a été exécuté pour le brouillon de collection qui a renvoyé les statistiques affichées dans la ligne correspondante.

- **Emplacements** avec accès : nombre d’emplacements  de contenu (spécifiés par la colonne Type d’emplacement) qui contiennent des éléments qui correspondent à la requête principale ou de mot clé répertoriée dans la colonne **Condition.**

- **Éléments**: nombre d’éléments (à partir de l’emplacement de contenu spécifié) qui correspondent à la requête répertoriée dans la **colonne Condition.** Comme indiqué précédemment, si un élément contient plusieurs instances d’un mot clé recherché, il n’est compté qu’une seule fois dans cette colonne.

- **Taille (Mo)**: taille totale de tous les éléments trouvés (à l’emplacement de contenu spécifié) qui correspondent à la requête de recherche dans la colonne **Condition.**

### <a name="top-locations"></a>Emplacements principaux

Cette section affiche des statistiques sur les emplacements de contenu spécifiques avec le plus d’éléments renvoyés par la collection.

- Nom du nom de l’emplacement (adresse de messagerie des boîtes aux lettres et URL des sites).

- Type d’emplacement (boîte aux lettres ou site).

- Nombre estimé d’éléments dans l’emplacement de contenu renvoyé par la collection.

- Taille totale des éléments estimés dans chaque emplacement de contenu.

## <a name="statistics-and-reports-for-committed-collections"></a>Statistiques et rapports pour les collections engagées

Cette section décrit les statistiques disponibles après la validation d’une collection dans un jeu à réviser, y compris le nombre réel d’éléments ajoutés au jeu à réviser. Ces statistiques (en plus des informations sur les ensembles de charge) fournissent des informations historiques sur le contenu ajouté à un cas.

Après la validation d’une collection dans un jeu à réviser, les onglets suivants s’affichent sur la page volante de la connexion dédiée. Chacun de ces onglets contient différents types d’informations sur la collection.

![Onglets sur la page volante d’une collection dédiée](../media/CommittedCollectionFlyoutPage.png)

### <a name="collection-contents"></a>Contenu de la collection

Cette section de **l’onglet** Résumé contient des statistiques et d’autres informations sur les éléments qui ont été collectés à partir des sources de données de la collection et ajoutés au jeu à réviser.

- **Nombre total d’éléments extraits.** Nombre total d’éléments ajoutés au jeu à réviser. Ce nombre indique la somme des éléments parents et des éléments enfants ajoutés au jeu à réviser.

  > [!TIP]
  > Placez le curseur sur les barres d’éléments parent ou enfant pour afficher le nombre total d’éléments parents ou enfants.

- **Éléments parents**. Nombre d’éléments renvoyés par la collection utilisée pour collecter les éléments qui ont été ajoutés au jeu à réviser. Ce nombre correspond (et est égal à) le nombre estimé d’éléments affichés dans la section **Paramètres de la** collection. Nombre d’éléments parents qu’il collectionne d’informations qui ont été utilisés pour collecter les éléments qui ont été ajoutés au jeu à réviser.
 
   Un élément parent peut contenir plusieurs éléments enfants. Par exemple, un message électronique est un élément parent s’il contient un fichier joint ou s’il a une pièce jointe dans le cloud. Dans ce cas, le fichier joint ou la cible de la pièce jointe cloud sont considérés comme des éléments enfants. Lorsque vous valider une collection, les éléments parents et les éléments enfants correspondants sont ajoutés au jeu à réviser en tant qu’éléments ou fichiers individuels.

- **Éléments enfants**. Nombre d’éléments enfants ajoutés au jeu à réviser. Les éléments enfants sont des pièces jointes ou d’autres parties d’un élément parent. Les éléments enfants incluent les fichiers joints, les pièces jointes cloud, les images et les signatures électroniques. Lorsque vous valider une collection dans un jeu à réviser, les éléments enfants sont extraits, indexés et ajoutés au jeu à réviser en tant que fichiers individuels.

- **Éléments uniques**. Nombre d’éléments uniques ajoutés au jeu à réviser. Les éléments uniques sont propres au jeu à réviser. Tous les éléments sont uniques lorsque la première collection est ajoutée à un nouveau jeu à réviser, car il n’y avait pas d’éléments précédents dans le jeu à réviser.

- **Éléments en double identifiés.** Nombre d’éléments de la collection qui n’ont pas été ajoutés au jeu à réviser, car le même élément existe déjà dans le jeu à réviser. Les statistiques sur les éléments en double peuvent aider à expliquer les différences entre le nombre d’éléments estimés d’une collection de brouillons et le nombre réel d’éléments ajoutés au jeu à réviser.

### <a name="indexing"></a>Indexation

La section **Indexation** de l’onglet **Résumé** d’un jeu à réviser engagé contient des informations d’indexation sur les éléments ajoutés au jeu à réviser.

**Nouveaux éléments indexés.** Nombre d’éléments qui ont été récemment indexés avant d’être ajoutés au jeu à réviser. Les éléments enfants extraits d’un élément parent, puis indexés avant d’être ajoutés au jeu à réviser, sont un exemple d’élément nouvellement indexé. En outre, les éléments qui ne sont pas situés dans des sources de données et des emplacements de contenu non privables répertoriés sous l’onglet **Sources** de données dans le cas sont indexés avant d’être ajoutés à la révision. Par exemple, les éléments nouvellement indexés incluent les éléments collectés à partir d’emplacements supplémentaires.

**Éléments indexés mis à jour.** Nombre d’éléments partiellement indexés qui ont été correctement indexés et ajoutés au jeu à réviser. Cette statistique indique les éléments partiellement indexés à partir d’emplacements de contenu privatives et non privatives Onglet **Sources** de données qui ont été correctement indexés lors de la engagement de la collection dans le jeu à réviser.

**Erreurs d’indexation.** Nombre d’éléments partiellement indexés qui n’ont pas pu être indexés avant d’être ajoutés au jeu à réviser. Ces éléments peuvent nécessiter une correction des erreurs.

### <a name="collection-parameters"></a>Paramètres de collection

Cette section affiche les informations de collection utilisées pour collecter les éléments qui ont été ajoutés au jeu à réviser. Cet onglet affiche des informations similaires aux informations de l’onglet **Statistiques de** recherche. Cette section fournit un instantané rapide de la requête de recherche utilisée par la collection, des emplacements de contenu qui ont été recherchés et des résultats estimés de la collection. Comme indiqué précédemment, le nombre d’éléments estimés dans cette section est égal au nombre d’éléments parents affichés dans la section Contenu **de la** collection.

### <a name="search-statistics-tab"></a>Onglet Statistiques de recherche

Les statistiques affichées sous **l’onglet** Statistiques de recherche sont identiques à la dernière fois qu’une collection provisoire a été exécuté. Cela inclut les estimations de collection, le rapport de condition et les principaux emplacements. Ces informations sont conservées à partir de l’ébauche de collection pour référence historique et peuvent être comparées à la collection réelle qui a été engagé dans le jeu à réviser.

## <a name="differences-between-draft-collection-estimates-and-the-actual-committed-collection"></a>Différences entre les estimations de collection provisoire et la collection réellement attachée

Lorsque vous exécutez une collection provisoire, une estimation du nombre d’éléments (et de  leur taille totale) qui répondent aux critères de collection est affichée sous l’onglet Résumé et dans la section **Estimations** de la collection de l’onglet Statistiques de recherche.  Après la validation d’un brouillon de collection dans un jeu à réviser, le nombre réel d’éléments (et leur taille totale) ajoutés à l’ensemble de révision sont souvent différents des estimations. Dans la plupart des cas, le nombre d’éléments ajoutés à l’ensemble de révision est supérieur à celui estimé dans le brouillon de la collection. La liste suivante décrit les raisons les plus courantes de ces différences et des conseils pour les identifier :

- **Éléments enfants**. Éléments enfants qui sont extraits de leurs éléments parents et ajoutés en tant que fichiers individuels. Le nombre d’éléments enfants peut augmenter considérablement le nombre d’éléments réellement ajoutés au jeu à réviser. En règle générale, le nombre d’éléments parents  identifiés dans la **section** Contenu de la collection sous l’onglet Résumé d’une collection engagée doit être égal au nombre d’éléments estimés de la collection provisoire.

- **Éléments en double.** Les éléments de la collection brouillon qui ont déjà été ajoutés au jeu à réviser d’une collection précédente ne seront pas ajoutés. Comme indiqué précédemment, le nombre d’éléments en double dans la collection est affiché dans la section Contenu de la **collection** sous **l’onglet Résumé.**

- **Options de configuration de collection.** Lorsque vous valider un brouillon de collection dans un jeu à réviser, vous devez inclure des threads de conversation, des pièces jointes cloud et des versions de document. Tous ces éléments ajoutés au jeu à réviser ne sont pas inclus dans les estimations de la collection provisoire. Ils sont identifiés et collectés uniquement lorsque vous validerez la collection. La sélection de ces options augmente probablement le nombre d’éléments ajoutés au jeu à réviser. 

    Par exemple, plusieurs versions de SharePoint documents ne sont pas incluses dans l’estimation de la collection provisoire. Toutefois, si vous sélectionnez l’option d’inclure toutes les versions de document lorsque vous exportez les résultats de la recherche, cela augmente le nombre réel (et la taille totale) des éléments ajoutés au jeu à réviser. 

    Pour plus d’informations sur ces options, voir [Valider un brouillon de collection dans un jeu à réviser.](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set-in-advanced-ediscovery) 

Voici d’autres raisons pour lesquelles les résultats estimés d’une collection provisoire peuvent être différents des résultats réellement engagés.

- **La façon dont les résultats sont estimés pour les collections de brouillons**. Une estimation des résultats de recherche renvoyés par un brouillon de collection est simplement une estimation (et non un nombre réel) des éléments qui répondent aux critères de requête de collection. Pour compiler l’estimation des éléments de courrier, une liste des ID de message qui répondent aux critères de recherche est demandée à partir de la base Exchange données. Mais lorsque vous valider la collection dans un jeu à réviser, la collection est réexécutée et les messages réels sont récupérés à partir de la base Exchange données. Par conséquent, des différences peuvent se faire en raison de la façon dont le nombre estimé d’éléments et le nombre réel d’éléments sont déterminés.

- **Modifications qui se produisent entre le moment où l’estimation et la validation des collections de brouillons**. Lorsque vous valider un brouillon de collection dans un jeu à réviser, la recherche est réexécutée pour collecter les éléments les plus récents dans l’index de recherche qui répondent aux critères de recherche. Il est possible que des éléments supplémentaires ont été créés, envoyés ou supprimés, qui répondent aux critères de recherche entre le moment où la collection provisoire a été exécuté pour la dernière fois et le moment où la collection de brouillons est engagée dans un jeu à réviser. Il est également possible que les éléments qui seraient dans l’index de recherche lorsque les résultats provisoires de la collection ont été estimés ne soient plus là, car ils ont été purgés d’une source de données avant la validation de la collection. Pour atténuer ce problème, vous pouvez spécifier une plage de dates pour une collection. Une autre façon consiste à placer une conservation sur les emplacements de contenu afin que les éléments soient conservés et ne soient pas purgés.

- **Éléments nonndexés.** Si la collection provisoire incluait la recherche dans toutes les boîtes aux lettres Exchange ou tous les sites SharePoint, seuls les éléments nonndes provenant d’emplacements de contenu qui contiennent des éléments qui correspondent aux critères de la collection seront ajoutés au jeu à réviser. En d’autres termes, si aucun résultat n’est trouvé dans une boîte aux lettres ou un site, les éléments nonndex de cette boîte aux lettres ou de ce site ne seront pas ajoutés au jeu à réviser. Toutefois, les éléments nonndex provenant de tous les emplacements de contenu (même ceux qui ne contiennent pas d’éléments qui correspondent à la requête de collection) seront inclus dans les résultats estimés de la collection.

    Par ailleurs, si la collection provisoire inclut des emplacements de contenu spécifiques (ce qui signifie que des boîtes aux lettres ou des sites spécifiques spécifiés dans la **page** Emplacements supplémentaires dans l’Assistant Brouillon de collection), alors les éléments nonndes (qui ne sont pas exclus par les critères de collection) des emplacements de contenu spécifiés dans la recherche seront exportés. Dans ce cas, le nombre estimé d’éléments nonndex et le nombre d’éléments nonndex ajoutés au jeu à réviser doivent être identiques.
