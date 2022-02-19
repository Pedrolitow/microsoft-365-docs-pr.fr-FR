---
title: Interroger le contenu d’un jeu à réviser
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment créer et exécuter une requête dans un jeu à réviser pour organiser le contenu pour une révision plus efficace dans Advanced eDiscovery cas.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: ebcb129241565321297b78072a5d02d173552ee1
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2022
ms.locfileid: "62904170"
---
# <a name="query-and-filter-content-in-a-review-set"></a>Interroger et filtrer du contenu dans un jeu à réviser

Dans la plupart des cas, il est utile d’approfondir le contenu d’un jeu à réviser et de l’organiser pour faciliter une révision plus efficace. L’utilisation de filtres et de requêtes dans un ensemble de révision vous permet de vous concentrer sur un sous-ensemble de documents qui répondent aux critères de votre avis.

## <a name="default-filters"></a>Filtres par défaut

Dans un jeu à réviser, il existe cinq filtres par défaut qui sont pré-chargés dans le jeu à réviser :

- Mots clés
- Date
- Sender/Author
- Objet/Titre
- Balises

![Types de filtres par défaut.](../media/DefaultFilterTypes.png)

Cliquez sur chaque filtre pour le développer et attribuer une valeur. Cliquez en dehors du filtre pour appliquer automatiquement le filtre au jeu à réviser. La capture d’écran suivante montre le filtre Date configuré pour afficher les documents dans une plage de dates.

![Filtre par défaut développé.](../media/ExpandedFilter.png)

## <a name="add-or-remove-filters"></a>Ajouter ou supprimer des filtres

Pour ajouter ou supprimer des filtres qui sont affichés pour le jeu à réviser, sélectionnez **Filtres** pour ouvrir le panneau de filtrage, qui s’affiche sur une page volante. 

![Panneau de filtrage.](../media/FilterPanel.png)

Les filtres disponibles sont organisés en quatre sections :

- **Recherche :** filtres qui fournissent différentes fonctionnalités de recherche.

- **Analyse &** codage prédictif : filtre les propriétés générées et ajoutées aux documents lorsque vous exécutez le travail d’analyse du courrier **&** document ou que vous utilisez des modèles de codage prédictifs.

- **ID :** filtre toutes les propriétés d’ID des documents.

- **Propriétés d’élément** : filtre les propriétés de document. 

Développez chaque section et sélectionnez ou désélectionnez des filtres pour les ajouter ou les supprimer dans le jeu de filtres. Lorsque vous ajoutez un filtre, il s’affiche dans le jeu de filtres. 

![Liste des sections et propriétés de filtre dans le panneau de filtrage.](../media/FilterPanel2.png)

> [!NOTE]
> Lorsque vous développez une section dans le panneau de filtrage, vous remarquerez que les types de filtres par défaut sont sélectionnés. Vous pouvez conserver ces éléments sélectionnés ou les désélectionner et les supprimer du jeu de filtres. 

## <a name="filter-types"></a>Types de filtres

Chaque champ utilisable dans une recherche dans un jeu à réviser possède un filtre correspondant que vous pouvez utiliser pour filtrer des éléments en fonction d’un champ spécifique.

Il existe plusieurs types de filtres :

- **Texte libre** : un filtre de texte libre est appliqué à des champs de texte tels que « Subject ». Vous pouvez lister plusieurs termes de recherche en les séparant par une virgule.

- **Date** : un filtre de date est utilisé pour les champs de date tels que « Date de dernière modification ».

- **Options de** recherche : un filtre d’options de recherche fournit une liste des valeurs possibles (chaque valeur est affichée avec une case à cocher que vous pouvez sélectionner) pour des champs particuliers dans l’avis. Ce filtre est utilisé pour les champs, tels que « Expéditeur », où il existe un nombre fini de valeurs possibles dans le jeu à réviser.

- **Mot** clé : une condition de mot clé est une instance spécifique de condition de texte libre que vous pouvez utiliser pour rechercher des termes. Vous pouvez également utiliser un langage de requête de type KQL dans ce type de filtre. Pour plus d’informations, voir les sections Langage de requête et Générateur de requêtes avancé de cet article.

## <a name="include-and-exclude-filter-relationships"></a>Inclure et exclure des relations de filtre

Vous pouvez modifier la relation Inclure et exclure pour un filtre particulier. Par exemple, dans le filtre De balise, vous pouvez exclure les éléments qui sont **marqués** avec une balise particulière en sélectionnant Égal à aucun des éléments dans le filtre de ladown. 

![Exclure le filtre de balise.](../media/TagFilterExclude.png)

## <a name="save-filters-as-queries"></a>Enregistrer des filtres en tant que requêtes

Une fois que vous êtes satisfait de vos filtres, vous pouvez enregistrer la combinaison de filtres en tant que requête de filtre. Cela vous permet d’appliquer le filtre dans les prochaines sessions de révision.

Pour enregistrer un filtre, **sélectionnez Enregistrer la requête et** nommez-la. Vous ou d’autres réviseurs pouvez exécuter des requêtes de filtre précédemment  enregistrées en sélectionnant la dropdown requêtes de filtre enregistrées et en sélectionnant une requête de filtre à appliquer aux documents de l’ensemble de révision. 

![Enregistrez une requête de filtre.](../media/SaveFilterQuery.png)

Pour supprimer une requête de filtre, ouvrez le panneau de filtrage et sélectionnez l’icône de corbeille en côté de la requête.

![Supprimer une requête de filtre.](../media/DeleteFilterQuery.png)

## <a name="query-language"></a>Langage de requête

En plus d’utiliser des filtres, vous pouvez également utiliser un langage de requête KQL dans le filtre Mots clés pour créer votre requête de recherche de jeu à réviser. Le langage de requête pour les requêtes de jeu à réviser prend en charge les opérateurs booléens standard, tels que **AND**, **OR**, **NOT** et **NEAR**. Il prend également en charge un caractère générique à caractère unique (?) et un caractère générique à plusieurs caractères (*).

## <a name="advanced-query-builder"></a>Générateur de requêtes avancé

Vous pouvez également créer des requêtes plus avancées pour rechercher des documents dans un jeu à réviser.

1. Ouvrez le panneau de filtrage, sélectionnez **Filtres** et **développez la** section Recherche.

  ![Ajoutez un filtre KQL.](../media/AddKQLFilter.png)

2. Sélectionnez **le filtre KQL** , puis cliquez **sur Ouvrir le générateur de requêtes**.

   Dans ce panneau, vous pouvez créer des requêtes KQL complexes à l’aide du générateur de requêtes. Vous pouvez ajouter des conditions ou des groupes de conditions composés de plusieurs conditions connectées logiquement par des **relations AND** ou **OR** .

   ![Utilisez le générateur de requêtes pour configurer des requêtes de filtre complexes.](../media/ComplexQuery.png)

## <a name="filter-partially-indexed-items"></a>Filtrer les éléments partiellement indexés

Si vous avez sélectionné l’option d’ajout d’éléments partiellement indexés à partir de sources de données supplémentaires lorsque vous avez engagé le brouillon de collection dans un jeu à réviser. Vous souhaiterez probablement identifier et afficher ces éléments pour déterminer si un élément peut être pertinent pour votre enquête et si vous devez corriger l’erreur qui a entraîné l’indexation partielle de l’élément.

Pour l’instant, il n’existe pas d’option de filtre dans un jeu à réviser pour afficher les éléments partiellement indexés. Mais nous y travaillons. En attendant, voici une façon de filtrer et d’afficher les éléments partiellement indexés que vous avez ajoutés à un jeu à réviser.

1. Créer une collection et la valider dans un nouveau jeu à réviser *sans* ajouter d’éléments partiellement indexés à partir des sources de données supplémentaires.

2. Créez une collection en copiant la collection à l’étape 1.

3. Valider la nouvelle collection dans le même jeu à réviser. Mais cette fois, ajoutez les éléments partiellement indexés à partir des sources de données supplémentaires. Étant donné que les éléments de la collection que vous avez créée à l’étape 1 ont déjà été ajoutés au jeu à réviser, seuls les éléments partiellement indexés de la deuxième collection sont ajoutés au jeu à réviser.

4. Une fois que les deux collections ont été ajoutées au jeu à réviser, allez dans le jeu à réviser, puis sélectionnez **Les jeux ManageLoad** > .

5. Copiez ou notez **l’ID de chargement** de la deuxième collection (celle que vous avez créée à l’étape 2). Le nom de la collection est identifié dans la **colonne Informations sur la** source.

6. De retour dans le jeu à réviser, cliquez sur **Filtrer**, développez la section **ID** , puis cochez la case Charger **l’ID** .

7. Développez **le filtre Load Id** , puis cochez la case correspondant à l’ID de chargement correspondant à la deuxième collection pour afficher les éléments partiellement indexés.
