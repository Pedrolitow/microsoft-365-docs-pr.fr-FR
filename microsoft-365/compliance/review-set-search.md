---
title: Interroger les données d’un jeu à réviser
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
description: ''
ms.openlocfilehash: 8eadfbeb1a78edd12129c97dc3144a45c5c409cf
ms.sourcegitcommit: caa3f681a68daf5e463093a922c3d6f378143d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "39191269"
---
# <a name="query-the-data-in-a-review-set"></a>Interroger les données d’un jeu à réviser

Dans la plupart des cas, il est utile de pouvoir approfondir les données dans un jeu de révision et d’organiser ces données pour faciliter une révision plus efficace. L’utilisation de requêtes dans un jeu de vérification vous permet de vous concentrer sur un sous-ensemble de documents qui répondent aux critères de votre révision.

## <a name="creating-and-running-a-query-in-a-review-set"></a>Création et exécution d’une requête dans un jeu de révision

Pour créer et exécuter une requête sur les documents d’un jeu de révision, cliquez sur **nouvelle requête** dans l’ensemble de révision. Une fois que vous avez nommé votre requête et défini les conditions, cliquez sur **Enregistrer** pour enregistrer et exécuter la requête. Pour exécuter une requête qui a été précédemment enregistrée, cliquez sur une requête enregistrée. 

![Examiner les requêtes Set](media/AeDReviewSetQueries.png)

## <a name="building-a-review-set-query"></a>Création d’une requête d’ensemble de révision

Vous pouvez créer une requête à l’aide d’une combinaison de cartes de condition et de langage de requête dans la carte de condition de mots-clés. Vous pouvez également regrouper les cartes de condition en tant que bloc (appelé *groupe de conditions*) pour créer une requête plus complexe. Pour obtenir la liste et la description des propriétés de métadonnées que vous pouvez rechercher, voir [document Metadata Fields in Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).

### <a name="condition-cards"></a>Cartes de condition

Chaque champ pouvant faire l’objet d’une recherche dans un jeu de révision dispose d’une carte de condition correspondante que vous pouvez utiliser pour créer votre requête.

Il existe plusieurs types de cartes de condition :

- FREETEXT : une carte de condition FREETEXT est utilisée pour les champs de texte tels que subject. Vous pouvez répertorier plusieurs termes de recherche en les séparant par une virgule.

- Date : une carte de condition de date est utilisée pour les champs de date tels que date de dernière modification.

- Options de recherche : une carte de condition options de recherche fournit une liste des valeurs possibles pour le champ particulier dans votre jeu de révision. Cette valeur est utilisée pour les champs, tels que sender, où il existe un nombre fini de valeurs possibles dans votre ensemble de révision.

- Mot-clé : une carte de condition de mot-clé est une instance spécifique de la carte de condition FREETEXT que vous pouvez utiliser pour rechercher des termes ou utiliser le langage de requête KQL dans. Voir ci-dessous pour plus de détails.

### <a name="query-language"></a>Langage de requête

En plus des cartes de condition, vous pouvez utiliser un langage de requête de type KQL dans la carte de mots-clés pour créer votre requête. Le langage de requête pour les requêtes de jeu de révision prend en charge les opérateurs booléens standard, tels que AND, OR, NOT et NEAR (n). Il prend également en charge un caractère générique ( ?) à un seul caractère et un caractère générique à caractères multiples (*).

## <a name="using-filters"></a>Utilisation de filtres

Outre les requêtes que vous pouvez enregistrer, vous pouvez utiliser les filtres Set Set pour appliquer rapidement des conditions supplémentaires à une requête Set Review. Cela vous permet d’affiner les résultats affichés par une requête d’ensemble de révision. 

![Vérifier les filtres Set](media/AeDReviewSetFilters.png)

Les filtres diffèrent des requêtes de deux façons importantes :

- Les filtres sont transitoires. Elles ne sont pas conservées au-delà de la session existante. En d’autres termes, vous ne pouvez pas enregistrer un filtre. Les requêtes sont enregistrées dans l’ensemble de révision et y accèdent chaque fois que vous ouvrez l’ensemble de révision.

- Les filtres sont toujours additionnés. Les filtres sont appliqués en plus de la requête d’ensemble de révision actuelle. L’application d’une requête différente remplace les résultats renvoyés par la requête actuelle.
