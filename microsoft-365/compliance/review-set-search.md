---
title: Interroger le contenu dans un ensemble de révisions
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
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
description: Découvrez comment créer et exécuter une requête dans un ensemble de révisions afin d’organiser le contenu pour une révision plus efficace dans un cas Microsoft Purview eDiscovery (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 707d6c31567ea7179b0e055abf1108ee4777a7ef
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67819224"
---
# <a name="query-and-filter-content-in-a-review-set"></a>Interroger et filtrer du contenu dans un jeu à réviser

Dans la plupart des cas, il sera utile d’approfondir le contenu d’un ensemble de révisions et de l’organiser pour faciliter une révision plus efficace. L’utilisation de filtres et de requêtes dans un jeu de révision vous permet de vous concentrer sur un sous-ensemble de documents qui répondent aux critères de votre révision.

## <a name="default-filters"></a>Filtres par défaut

Dans un ensemble de révisions, il existe cinq filtres par défaut qui sont pré-chargés dans l’ensemble de révisions :

- Mots-clés
- Date
- Expéditeur/auteur
- Objet/titre
- Balises

![Types de filtres par défaut.](../media/DefaultFilterTypes.png)

Cliquez sur chaque filtre pour le développer et attribuer une valeur. Cliquez en dehors du filtre pour appliquer automatiquement le filtre au jeu de révision. La capture d’écran suivante montre le filtre Date configuré pour afficher les documents dans une plage de dates.

![Filtre par défaut développé.](../media/ExpandedFilter.png)

## <a name="add-or-remove-filters"></a>Ajouter ou supprimer des filtres

Pour ajouter ou supprimer des filtres affichés pour le jeu de révision, sélectionnez **Filtres** pour ouvrir le panneau de filtre, qui s’affiche sur une page de menu volant. 

![Panneau de filtre.](../media/FilterPanel.png)

Les filtres disponibles sont organisés en quatre sections :

- **Recherche** : filtres qui fournissent différentes fonctionnalités de recherche.

- **L’analytique & le codage prédictif** : filtre les propriétés générées et ajoutées aux documents lorsque vous exécutez le travail **d’analyse par e-mail Document &** ou utilisez des modèles de codage prédictif.

- **ID** : filtre toutes les propriétés d’ID des documents.

- **Propriétés de l’élément** : filtre les propriétés du document. 

Développez chaque section et sélectionnez ou désélectionnez les filtres pour les ajouter ou les supprimer dans le jeu de filtres. Lorsque vous ajoutez un filtre, il s’affiche dans le jeu de filtres. 

![Liste des sections et propriétés de filtre dans le panneau de filtre.](../media/FilterPanel2.png)

> [!NOTE]
> Lorsque vous développez une section dans le panneau de filtre, vous remarquerez que les types de filtres par défaut sont sélectionnés. Vous pouvez les conserver sélectionnés ou les désélectionner et les supprimer du jeu de filtres. 

## <a name="filter-types"></a>Types de filtres

Chaque champ pouvant faire l’objet d’une recherche dans un ensemble de révisions dispose d’un filtre correspondant que vous pouvez utiliser pour les éléments de filtre en fonction d’un champ spécifique.

Il existe plusieurs types de filtres :

- **Texte libre** : un filtre de texte libre est appliqué aux champs de texte tels que « Subject ». Vous pouvez répertorier plusieurs termes de recherche en les séparant par une virgule.

- **Date** : un filtre de date est utilisé pour les champs de date tels que « Date de dernière modification ».

- **Options de** recherche : un filtre d’options de recherche fournit une liste des valeurs possibles (chaque valeur est affichée avec une case à cocher que vous pouvez sélectionner) pour des champs particuliers dans la révision. Ce filtre est utilisé pour les champs, tels que « Expéditeur », où il existe un nombre fini de valeurs possibles dans le jeu de révision.

- **Mot clé** : une condition de mot clé est une instance spécifique de condition de texte libre que vous pouvez utiliser pour rechercher des termes. Vous pouvez également utiliser le langage de requête KQL dans ce type de filtre. Pour plus d’informations, consultez les sections Langage de requête et Générateur de requêtes avancé de cet article.

## <a name="include-and-exclude-filter-relationships"></a>Inclure et exclure des relations de filtre

Vous pouvez modifier la relation d’inclusion et d’exclusion pour un filtre particulier. Par exemple, dans le filtre de balises, vous pouvez exclure les éléments marqués avec une balise particulière en sélectionnant **Égal à aucun des éléments du** filtre de liste déroulante. 

![Exclure le filtre de balises.](../media/TagFilterExclude.png)

## <a name="save-filters-as-queries"></a>Enregistrer des filtres en tant que requêtes

Une fois que vous êtes satisfait de vos filtres, vous pouvez enregistrer la combinaison de filtres en tant que requête de filtre. Cela vous permet d’appliquer le filtre dans les prochaines sessions de révision.

Pour enregistrer un filtre, **sélectionnez Enregistrer la requête** et nommez-la. Vous ou d’autres réviseurs pouvez exécuter des requêtes de filtre précédemment enregistrées en sélectionnant la liste déroulante **Des requêtes de filtre enregistrées** et en sélectionnant une requête de filtre à appliquer pour passer en revue les documents définis. 

![Enregistrez une requête de filtre.](../media/SaveFilterQuery.png)

Pour supprimer une requête de filtre, ouvrez le panneau de filtre et sélectionnez l’icône de corbeille en regard de la requête.

![Supprimez une requête de filtre.](../media/DeleteFilterQuery.png)

## <a name="query-language"></a>Langage de requête

En plus d’utiliser des filtres, vous pouvez également utiliser un langage de requête de type KQL dans le filtre Mots clés pour générer votre requête de recherche de jeu de révisions. Le langage de requête pour les requêtes d’ensemble de révision prend en charge les opérateurs booléens standard, tels que **AND**, **OR**, **NOT** et **NEAR**. Il prend également en charge un caractère générique à caractère unique (?) et un caractère générique à caractères multiples (*).

## <a name="advanced-query-builder"></a>Générateur de requêtes avancé

Vous pouvez également créer des requêtes plus avancées pour rechercher des documents dans un ensemble de révisions.

1. Ouvrez le panneau de filtre, sélectionnez **Filtres** et **développez** la section Recherche.

  ![Ajoutez un filtre KQL.](../media/AddKQLFilter.png)

2. Sélectionnez le filtre **KQL** , puis cliquez sur **Ouvrir le générateur de requêtes**.

   Dans ce panneau, vous pouvez créer des requêtes KQL complexes à l’aide du générateur de requêtes. Vous pouvez ajouter des conditions ou ajouter des groupes de conditions constitués de plusieurs conditions qui sont logiquement connectées par des relations **AND** ou **OR** .

   ![Utilisez le générateur de requêtes pour configurer des requêtes de filtre complexes.](../media/ComplexQuery.png)

## <a name="filter-partially-indexed-items"></a>Filtrer les éléments partiellement indexés

Si vous avez sélectionné l’option permettant d’ajouter des éléments partiellement indexés à partir de sources de données supplémentaires lorsque vous avez validé le brouillon de la collection dans un jeu de révision. Vous souhaiterez probablement identifier et afficher ces éléments pour déterminer si un élément peut être pertinent pour votre investigation et si vous devez corriger l’erreur qui a entraîné l’indexation partielle de l’élément.

Pour l’instant, il n’existe pas d’option de filtre dans un ensemble de révisions pour afficher des éléments partiellement indexés. Mais on y travaille. En attendant, voici un moyen de filtrer et d’afficher les éléments partiellement indexés que vous avez ajoutés à un ensemble de révisions.

1. Créez une collection et validez-la dans un nouvel ensemble de *révisions sans* ajouter d’éléments partiellement indexés à partir des sources de données supplémentaires.

2. Créez une collection en copiant la collection à l’étape 1.

3. Validez la nouvelle collection dans le même jeu de révision. Mais cette fois, ajoutez les éléments partiellement indexés à partir des sources de données supplémentaires. Étant donné que les éléments de la collection que vous avez créée à l’étape 1 ont déjà été ajoutés au jeu de révision, seuls les éléments partiellement indexés de la deuxième collection sont ajoutés au jeu de révision.

4. Une fois les deux collections ajoutées au jeu de révision, accédez à l’ensemble de révisions, puis sélectionnez **Gérer** >  les **jeux de charge**.

5. Copiez ou notez **l’ID de chargement** pour la deuxième collection (celle que vous avez créée à l’étape 2). Le nom de la collection est identifié dans la colonne **Informations sources** .

6. De retour dans le jeu de révision, cliquez sur **Filtrer**, développez la section **ID** , puis activez la case à cocher **Charger l’ID** .

7. Développez le filtre **Load Id** , puis cochez la case de l’ID de charge qui correspond à la deuxième collection pour afficher les éléments partiellement indexés.
