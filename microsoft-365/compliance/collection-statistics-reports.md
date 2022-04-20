---
title: Statistiques et rapports de collection
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment accéder aux statistiques et aux rapports et les utiliser pour les projets de regroupements et de collections qui ont été validés dans un ensemble de révisions dans Microsoft Purview eDiscovery (Premium).
ms.openlocfilehash: 140a6aa2ac0a0ebbff7cf2ab2ee8618cd45cdf07
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995753"
---
# <a name="collection-statistics-and-reports-in-microsoft-purview-ediscovery-premium"></a>Statistiques et rapports de collecte dans Microsoft Purview eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Après avoir créé un brouillon de collection, vous pouvez afficher des statistiques sur les éléments récupérés, tels que les emplacements de contenu qui contiennent le plus d’éléments correspondant aux critères de recherche et le nombre d’éléments retournés par la requête de recherche. Vous pouvez également afficher un aperçu d’un sous-ensemble des résultats.

Une fois que vous avez identifié l’ensemble de documents que vous souhaitez examiner plus en détail, vous pouvez ajouter les résultats de la recherche à un ensemble de révisions à collecter et à traiter.

## <a name="statistics-and-reports-for-draft-collections"></a>Statistiques et rapports pour les projets de regroupements

Cette section décrit les statistiques disponibles pour les brouillons de collections. Ces statistiques sont disponibles sous l’onglet **Statistiques de** recherche de la page volante d’un brouillon de collection.

### <a name="collection-estimates"></a>Estimations de collection

Cette section affiche un résumé graphique des éléments estimés retournés par la collection. Cela indique le nombre d’éléments qui correspondent aux critères de recherche de la collection. Ces informations vous donnent une idée du nombre estimé d’éléments retournés par la collection.

![Estimations de collection pour un brouillon de collection.](../media/AeDCollectionEstimates.png)

- **Éléments estimés par emplacement :** nombre total d’éléments estimés retournés par la collection. Le nombre spécifique d’éléments situés dans les boîtes aux lettres et situés dans des sites est également affiché.

- **Emplacements estimés avec accès** : nombre total d’emplacements de contenu qui contiennent des éléments retournés par la collection. Le nombre spécifique de boîtes aux lettres et d’emplacements de site s’affiche également.

- **Volume de données par emplacement (en Mo)** : taille totale de tous les éléments estimés retournés par la collection. La taille spécifique des éléments de boîte aux lettres et des éléments de site s’affiche également.

### <a name="condition-report"></a>Rapport de condition

Cette section affiche des statistiques sur la requête de recherche de collection et le nombre d’éléments estimés correspondant à différentes parties de la requête de recherche. Vous pouvez utiliser ces statistiques pour analyser le nombre d’éléments qui correspondent à chaque composant de la requête de recherche. Cela peut vous aider à affiner les critères de recherche pour la collection et, si nécessaire, à affiner l’étendue de la collection.

- **Type d’emplacement** : type d’emplacement de contenu auquel les statistiques de requête s’appliquent. La valeur de **Exchange** indique un emplacement de boîte aux lettres ; une valeur de **SharePoint** indique un emplacement de site.

- **Partie** : partie de la requête de recherche à qui les statistiques s’appliquent. **Primary** indique l’intégralité de la requête de recherche. **Le mot clé** indique que les statistiques de la ligne concernent un mot clé spécifique. Si vous utilisez une liste de mots clés lorsque vous utilisez la requête de recherche dans la collection, les statistiques de chaque composant de la requête sont incluses dans ce tableau.

- **Condition** : composant réel (mot clé ou condition) de la requête de recherche exécutée pour la collection brouillon qui a retourné les statistiques affichées dans la ligne correspondante.

- **Emplacements avec accès** : nombre d’emplacements de contenu (spécifiés par la colonne Type **d’emplacement** ) qui contiennent des éléments qui correspondent à la requête principale ou de mot clé répertoriée dans la colonne **Condition** .

- **Éléments** : nombre d’éléments (à partir de l’emplacement de contenu spécifié) qui correspondent à la requête répertoriée dans la colonne **Condition** . Comme expliqué précédemment, si un élément contient plusieurs instances d’un mot clé recherché, il n’est compté qu’une seule fois dans cette colonne.

- **Taille (Mo)** : taille totale de tous les éléments trouvés (à l’emplacement de contenu spécifié) qui correspondent à la requête de recherche dans la colonne **Condition** .

### <a name="top-locations"></a>Emplacements principaux

Cette section affiche des statistiques sur les emplacements de contenu spécifiques avec le plus d’éléments renvoyés par la collection.

- Nom du nom de l’emplacement (adresse e-mail des boîtes aux lettres et URL des sites).

- Type d’emplacement (boîte aux lettres ou site).

- Nombre estimé d’éléments dans l’emplacement de contenu retourné par la collection.

- Taille totale des éléments estimés dans chaque emplacement de contenu.

## <a name="statistics-and-reports-for-committed-collections"></a>Statistiques et rapports pour les collections validées

Cette section décrit les statistiques disponibles après la validation d’un regroupement dans un ensemble de révisions, y compris le nombre réel d’éléments ajoutés à l’ensemble de révisions. Ces statistiques (en plus des informations du jeu de charge) fournissent des informations historiques sur le contenu ajouté à un cas.

Une fois que vous avez validé une collection dans un jeu de révision, les onglets suivants s’affichent sur la page de menu volant de la connexion validée. Chacun de ces onglets contient différents types d’informations sur la collection.

![Onglets sur la page de menu volant de la collection validée.](../media/CommittedCollectionFlyoutPage.png)

### <a name="collection-contents"></a>Contenu de la collection

Cette section de l’onglet **Résumé** contient des statistiques et d’autres informations sur les éléments qui ont été collectés à partir des sources de données de la collection et ajoutés au jeu de révision.

- **Nombre total d’éléments extraits**. Nombre total d’éléments ajoutés au jeu de révision. Ce nombre indique la somme des éléments parents et des éléments enfants ajoutés au jeu de révision.

  > [!TIP]
  > Placez le curseur sur les barres d’éléments parent ou enfant pour afficher le nombre total d’éléments parent ou enfant.

- **Éléments parents**. Nombre d’éléments retournés par la collection qui a été utilisée pour collecter les éléments qui ont été ajoutés au jeu de révision. Ce nombre correspond (et est égal à) le nombre estimé d’éléments affichés dans la section **Paramètres** de collection. Nombre d’éléments parents qu’il collecte des informations qui ont été utilisés pour collecter les éléments qui ont été ajoutés à l’ensemble de révision.
 
   Un élément parent peut contenir plusieurs éléments enfants. Par exemple, un e-mail est un élément parent s’il contient un fichier attaché ou s’il a une pièce jointe cloud. Dans ce cas, le fichier attaché ou le fichier cible de la pièce jointe cloud est considéré comme un élément enfant. Lorsque vous validez une collection, les éléments parents et les éléments enfants correspondants (tels que les fichiers attachés et les pièces jointes cloud) sont ajoutés à l’ensemble de révisions en tant qu’éléments ou fichiers individuels.

- **Éléments enfants**. Nombre d’éléments enfants ajoutés au jeu de révision. Seuls les éléments enfants qui sont des pièces jointes de fichier et des pièces jointes cloud sont ajoutés à l’ensemble de révisions en tant que fichiers individuels. D’autres types d’éléments enfants, tels que les signatures électroniques et les images, sont extraits d’un élément parent, puis traités par reconnaissance optique de caractères (OCR) pour extraire du texte de l’élément enfant. Le texte extrait de ces types d’éléments enfants est ensuite ajouté à son élément parent afin que vous puissiez l’afficher dans le jeu de révision. En n’ajoutant pas d’éléments enfants à l’ensemble de révision en tant que fichier distinct, eDiscovery (Premium) simplifie le processus de révision en limitant le nombre d’éléments potentiellement non pertinents dans l’ensemble de révisions.

- **Éléments uniques**. Nombre d’éléments uniques ajoutés au jeu de révision. Les éléments uniques sont uniques à l’ensemble de révisions. Tous les éléments sont uniques lorsque la première collection est ajoutée à un nouvel ensemble de révisions, car il n’y avait aucun élément précédent dans le jeu de révision.

- **Éléments en double identifiés**. Nombre d’éléments de la collection qui n’ont pas été ajoutés à l’ensemble de révisions, car le même élément existe déjà dans le jeu de révisions. Les statistiques sur les éléments en double peuvent aider à expliquer les différences entre le nombre d’éléments estimés d’une collection brouillon et le nombre réel d’éléments ajoutés à l’ensemble de révisions.

### <a name="indexing"></a>Indexation

La section **Indexation** sous l’onglet **Résumé** d’un jeu de révision validé contient des informations d’indexation sur les éléments ajoutés au jeu de révision.

**Nouveaux éléments indexés**. Nombre d’éléments qui ont été récemment indexés avant d’être ajoutés au jeu de révision. Les éléments enfants extraits d’un élément parent, puis indexés avant d’être ajoutés au jeu de révision sont des exemples d’élément nouvellement indexé. En outre, les éléments qui ne se trouvent pas dans les sources de données de garde et les emplacements de contenu non-custodial répertoriés sous l’onglet **Sources de données** dans le cas sont indexés avant d’être ajoutés à la révision. Par exemple, les éléments nouvellement indexés incluent les éléments collectés à partir d’emplacements supplémentaires.

**Éléments indexés mis à jour**. Nombre d’éléments partiellement indexés qui ont été correctement indexés et ajoutés au jeu de révision. Cette statistique indique les éléments partiellement indexés de **l’onglet Sources** de données des emplacements de contenu custodial et non-custodial qui ont été correctement indexés lorsque la collection a été validée dans le jeu de révision.

**Erreurs d’indexation**. Nombre d’éléments partiellement indexés qui n’ont pas pu être indexés avant d’être ajoutés au jeu de révision. Ces éléments peuvent nécessiter une correction d’erreur.

### <a name="collection-parameters"></a>Paramètres de collection

Cette section affiche les informations de collecte utilisées pour collecter les éléments qui ont été ajoutés à l’ensemble de révisions. Cet onglet affiche des informations similaires à celles de l’onglet **Statistiques de** recherche. Cette section fournit une capture instantanée de la requête de recherche utilisée par la collection, des emplacements de contenu qui ont été recherchés et des résultats estimés de la collection. Comme expliqué précédemment, le nombre d’éléments estimés dans cette section serait égal au nombre d’éléments parents affichés dans la section **Contenu de** la collection.

### <a name="search-statistics-tab"></a>Onglet Statistiques de recherche

Les statistiques affichées sous l’onglet **Statistiques** de recherche sont les mêmes que celles de la dernière exécution d’une collection brouillon. Cela inclut les estimations de collection, le rapport de condition et les emplacements supérieurs. Ces informations sont conservées du projet de collection pour référence historique et peuvent être comparées à la collection réelle qui a été validée dans le jeu d’examens.

## <a name="differences-between-draft-collection-estimates-and-the-actual-committed-collection"></a>Différences entre les estimations de collection provisoires et la collection validée réelle

Lorsque vous exécutez un brouillon de collection, une estimation du nombre d’éléments (et de leur taille totale) qui répondent aux critères de collecte s’affiche sous l’onglet **Résumé** et dans la section **Estimations** de collection de l’onglet **Statistiques** de recherche. Une fois que vous avez validé un brouillon de collection dans un ensemble de révisions, le nombre réel d’éléments (et leur taille totale) ajoutés à l’ensemble de révisions sont souvent différents des estimations. Dans la plupart des cas, plus d’éléments sont ajoutés à l’ensemble d’examens que ce qui a été estimé dans le brouillon de la collection. La liste suivante décrit les raisons les plus courantes de ces différences et des conseils pour les identifier :

- **Éléments enfants**. Éléments enfants (tels que les pièces jointes de fichiers et les pièces jointes cloud) qui sont extraits de leurs éléments parents et ajoutés en tant que fichiers individuels. Le nombre d’éléments enfants peut augmenter le nombre d’éléments réellement ajoutés au jeu de révision. En général, le nombre d’éléments parents identifiés dans la section **Contenu de la collection** sous l’onglet **Résumé** d’une collection validée doit être égal au nombre d’éléments estimés de la collection brouillon.

- **Éléments en double**. Les éléments de la collection brouillon qui ont déjà été ajoutés à l’ensemble de révisions dans une collection précédente ne seront pas ajoutés. Comme expliqué précédemment, le nombre d’éléments en double dans la collection s’affiche dans la section **Contenu de** la collection sous l’onglet **Résumé** .

- **Options de configuration de collection**. Lorsque vous validez un brouillon de collection dans un ensemble de révisions, vous devez choisir d’inclure des threads de conversation, des pièces jointes cloud et des versions de document. Aucun de ces éléments ajoutés à l’ensemble d’examens n’est inclus dans les estimations de la collection brouillon. Ils sont identifiés et collectés uniquement lorsque vous validez la collection. La sélection de ces options augmente probablement le nombre d’éléments ajoutés à l’ensemble de révisions. 

    Par exemple, plusieurs versions de SharePoint documents ne sont pas incluses dans l’estimation de la collection brouillon. Toutefois, si vous sélectionnez l’option permettant d’inclure toutes les versions de document lorsque vous validez un brouillon de collection, le nombre réel (et la taille totale) des éléments ajoutés au jeu de révision augmente.

    Pour plus d’informations sur ces options, consultez [Commit a draft collection to a review set](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set-in-ediscovery-premium).

Voici d’autres raisons pour lesquelles les résultats estimés d’un brouillon peuvent être différents des résultats réels validés.

- **La façon dont les résultats sont estimés pour les brouillons de collections**. Une estimation des résultats de recherche retournés par un brouillon de collection est simplement qu’il s’agit d’une estimation (et non d’un nombre réel) des éléments qui répondent aux critères de requête de collection. Pour compiler l’estimation des éléments de messagerie, une liste des ID de message qui répondent aux critères de recherche est demandée à partir de la base de données Exchange. Toutefois, lorsque vous validez la collection sur un jeu de révision, la collection est réexécutée et les messages réels sont récupérés à partir de la base de données Exchange. Les différences peuvent donc se produire en raison de la façon dont le nombre estimé d’éléments et le nombre réel d’éléments sont déterminés.

- **Modifications qui se produisent entre le moment où l’estimation et la validation des collections provisoires** sont effectuées. Lorsque vous validez un brouillon de collection dans un ensemble de révisions, la recherche est réexécutée pour collecter les éléments les plus récents dans l’index de recherche qui répondent aux critères de recherche. Il est possible que des éléments supplémentaires aient été créés, envoyés ou supprimés qui répondent aux critères de recherche entre la dernière exécution de la collection brouillon et le moment où la collection brouillon est validée dans un ensemble de révisions. Il est également possible que les éléments qui se trouvaient dans l’index de recherche lorsque les résultats de la collection brouillon ont été estimés ne soient plus présents, car ils ont été vidés d’une source de données avant de valider la collection. Une façon d’atténuer ce problème consiste à spécifier une plage de dates pour une collection. Une autre méthode consiste à placer une conservation sur les emplacements de contenu afin que les éléments soient conservés et ne puissent pas être vidés.

- **Éléments non indexés**. Si le brouillon de la collection incluait la recherche de toutes les boîtes aux lettres Exchange ou de tous les sites SharePoint, seuls les éléments non indexés des emplacements de contenu qui contiennent des éléments qui correspondent aux critères de collection seront ajoutés au jeu de révision. En d’autres termes, si aucun résultat n’est trouvé dans une boîte aux lettres ou un site, les éléments non indexés de cette boîte aux lettres ou de ce site ne seront pas ajoutés au jeu de révision. Toutefois, les éléments non indexés de tous les emplacements de contenu (même ceux qui ne contiennent pas d’éléments correspondant à la requête de collection) seront inclus dans les résultats estimés de la collection.

    Sinon, si le brouillon de la collection incluait des emplacements de contenu spécifiques (ce qui signifie que des boîtes aux lettres ou des sites spécifiques spécifiés sur la page **Emplacements supplémentaires** dans l’Assistant De collection brouillon), les éléments non indexés (qui ne sont pas exclus par les critères de collection) des emplacements de contenu spécifiés dans la recherche seront exportés. Dans ce cas, le nombre estimé d’éléments non indexés et le nombre d’éléments non indexés ajoutés au jeu de révision doivent être identiques.
