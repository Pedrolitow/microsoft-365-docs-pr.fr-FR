---
title: Vue d’ensemble des collections dans Advanced eDiscovery
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
description: Utilisez des collections dans Advanced eDiscovery pour rechercher et collecter du contenu relatif à votre cas ou à votre enquête.
ms.openlocfilehash: e3f383fab31ec39f22bd781fc84644e3eeee57bb
ms.sourcegitcommit: 8f1721de52dbe3a12c11a0fa5ed0ef5972ca8196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2021
ms.locfileid: "50838879"
---
# <a name="learn-about-collections-in-advanced-ediscovery"></a>En savoir plus sur les collections dans Advanced eDiscovery

> [!NOTE]
> Nous allons déployer une nouvelle expérience de collections dans Advanced eDiscovery, qui est décrite dans cet article. Ce déploiement prendra un certain nombre de semaines avant d’être disponible pour toutes les organisations. Si la nouvelle expérience de collections n’est pas disponible dans votre organisation, vous pouvez toujours collecter du contenu de cas à l’aide de [l Advanced eDiscovery de recherche.](create-search-to-collect-data.md)

Lorsque les organisations sont confrontées à la collecte des communications et du contenu qui peuvent être pertinents pour une enquête ou un litige potentiel, elles rencontrent un défi important dans les meilleures circonstances. Dans l’espace de travail moderne d’aujourd’hui, le volume, la variété et la rapidité du contenu permettent l’innovation et le travail à distance, tout en élargissant les exigences et le processus de gestion des collections pour les examens eDiscovery.

Le flux de travail de collecte pose des défis techniques importants concernant l’extraction de contenu à partir d’emplacements et de sources natifs. Il s’agit également d’un point essentiel dans l’évaluation et la stratégie pour les scénarios courants de litige ou d’enquête. Lorsque les organisations commencent à évaluer un examen, les premières questions posées sont les personnes impliquées ? Après avoir identifié les personnes impliquées, ces dépositaires peuvent rapidement être mis en attente pour conserver le contenu pertinent. La question suivante est la suivante : qu’est-ce qui s’est passé ? Pour répondre à cette deuxième question fondamentale de toute enquête, les responsables doivent se tourner vers les données. Pour évaluer rapidement le contenu le plus pertinent à la question de ce qui a eu lieu, les responsables commencent à affiner la cible de la question pour s’assurer que les résultats de la collection sont complets sans être trop larges.

Les collections dans Advanced eDiscovery permettent aux gestionnaires eDiscovery d’effectuer rapidement une recherche de contenu dans le courrier électronique, les documents et d’autres contenus dans Microsoft 365. Les collections fournissent aux responsables une estimation du contenu qui peut être pertinent pour le cas. Cela permet aux responsables de prendre des décisions rapides et éclairées sur la taille et l’étendue du contenu pertinents pour un cas. Les gestionnaires eDiscovery peuvent créer une collection pour rechercher des sources de données privées (telles que des boîtes aux lettres et des sites SharePoint) et en utilisant des critères de recherche spécifiques (tels que des mots clés et des plages de dates) pour définir rapidement l’étendue de leur collection.

Une fois la collection définie, les gestionnaires eDiscovery peuvent enregistrer la collection en tant que brouillon et obtenir des estimations, y compris des estimations du volume de données, les emplacements de contenu qui contiennent des résultats et le nombre d’occurrences pour la condition de requête de recherche. Ces informations peuvent aider à savoir si la collection doit être révisée pour affiner ou étendre l’étendue de la collection avant de passer aux étapes de révision et d’analyse dans le flux de travail eDiscovery.

Lorsque le responsable est satisfait de l’étendue de la collection et de la quantité estimée  de contenu susceptible d’être réactive, il peut ajouter ou valider le contenu dans un groupe de révision. Lors de la validation d’une collection dans un jeu à réviser, ce responsable a également la possibilité d’inclure des conversations de conversation, des pièces jointes cloud et des versions de document. Le contenu de la collection passe également par un autre niveau de traitement lors de l’ingestion dans le jeu à réviser. et la collection sera mise à jour avec le résumé final de la collection. Une fois le contenu ajouté au jeu à réviser, les responsables eDiscovery peuvent continuer à interroger, grouper et affiner le contenu pour faciliter la réduction et la révision. En outre, la collection est mise à jour avec des informations et des statistiques sur le contenu engagé dans le jeu à réviser. Cela fournit une référence historique sur le contenu de la collection.

Avec la publication de collections dans  une Advanced eDiscovery, l’onglet Recherches a été renommé **Collections** dans un cas Advanced eDiscovery dans le centre de conformité Microsoft 365 recherche. Les étapes de définition de l’étendue et de la taille de la collection suivent le même processus que la recherche pour définir des emplacements et des conditions. Enregistrer en tant que brouillon et obtenir des estimations d’aperçu permet de valider rapidement l’étendue ciblée des collections avant de valider une recherche et une collection complètes dans le jeu à réviser. Cela permet une gestion améliorée des travail et des itérations ciblées pour commencer à réduire le contenu pendant le processus de recherche et de collecte.

## <a name="collections-workflow"></a>Flux de travail collections

Pour commencer à utiliser des collections Advanced eDiscovery, voici un flux de travail de base et des descriptions de chaque étape du processus.

![Flux de travail collections dans Advanced eDiscovery](../media/CollectionsWorkflow.png)

1. **Créez et exécutez un brouillon de collection.** La première étape consiste à créer un brouillon de collection et à définir les sources de données à rechercher. Vous pouvez également rechercher d’autres sources de données qui n’ont pas été ajoutées au cas. Après avoir ajouté les sources de données, vous configurez la requête de recherche pour rechercher dans les sources de données du contenu pertinent pour le cas. Vous pouvez utiliser des mots clés, des propriétés et des conditions pour créer des requêtes de recherche qui retournent du contenu probablement le plus pertinent pour le cas. Pour plus d’informations, [voir Créer un brouillon de collection.](create-draft-collection.md)

2. **Passer en revue les estimations et les statistiques.** Après avoir créé un brouillon de collection et l’avoir exécuté, l’étape suivante consiste à afficher les statistiques de la collection pour vous aider à vérifier si le contenu pertinent est trouvé et les emplacements de contenu ayant le plus d’accès. Vous pouvez également prévisualiser un exemple des résultats de la recherche pour vous aider à déterminer si le contenu est dans le cadre de votre enquête. Pour plus d’informations, voir [Statistiques et rapports pour les collections provisoires.](collection-statistics-reports.md#statistics-and-reports-for-draft-collections)

3. **Révisez et réexécutez une collection de brouillons.** En fonction des estimations et des statistiques renvoyées par la collection, vous pouvez modifier le brouillon de la collection en modifiant les sources de données qui sont recherchés et la requête de recherche pour développer ou affiner la collection. Vous pouvez mettre à jour et réexécuter l’ébauche de collection jusqu’à ce que vous êtes certain que la collection contient le contenu le plus pertinent pour votre cas.

4. **Valider un brouillon de collection dans un jeu à réviser**. Lorsque vous êtes satisfait que la collection renvoie le contenu de type pertinent pour le cas, vous pouvez valider la collection dans le jeu à réviser. Lorsque vous valider une collection, vous avez la possibilité d’ajouter des threads de conversation, des pièces jointes cloud et des versions de document au jeu à réviser, qui peuvent tous être pertinents pour le cas. Les choses suivantes se produisent lors de la validation d’une collection :

   - Les éléments enfants (tels que les pièces jointes, les signatures électroniques et les images) sont extraits d’un élément parent (tel qu’un message électronique, un message de conversation ou un document), indexés (dans un processus appelé *indexation* approfondie) et ajoutés au jeu à réviser en tant que fichiers distincts.

   - L’indexation approfondie est effectuée sur les éléments collectés à partir de sources de données supplémentaires. Ces types de sources de données sont des emplacements de contenu autres que les sources de données privatives et non privatives précédemment ajoutées au cas.

   Pour plus d’informations, voir [Valider un brouillon de collection dans un jeu à réviser.](commit-draft-collection.md)

5. **Passer en revue le résumé et les statistiques de la collection.** Après la validation d’une collection dans un jeu à réviser, les informations relatives à la collection sont conservées, telles que les statistiques sur les éléments extraits, l’indexation approfondie, la requête de recherche utilisée pour la collection et les emplacements de contenu à partir des éléments collectés. En outre, les collections engagées ne peuvent pas être modifiées ou réexécutées. Vous pouvez uniquement les copier ou les supprimer. La conservation des collections fournit un enregistrement historique des éléments collectés qui ont été ajoutés à un jeu à réviser. Pour plus d’informations, voir [Statistiques et rapports pour les collections engagées.](collection-statistics-reports.md#statistics-and-reports-for-committed-collections)
