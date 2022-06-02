---
title: Vue d’ensemble des collections dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
ms.reviewer: nickrob
manager: laurawi
ms.date: 05/31/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Utilisez des collections dans eDiscovery (Premium) pour rechercher et collecter du contenu relatif à votre cas ou investigation.
ms.openlocfilehash: 7b5c09cd0b8a9f0a2ea0fe75e3ebf82e27223b14
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839380"
---
# <a name="learn-about-collections-in-ediscovery-premium"></a>En savoir plus sur les collections dans eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Lorsque les organisations sont confrontées à la collecte des communications et du contenu susceptibles d’être pertinents pour une enquête ou un litige potentiel, elles sont confrontées à un défi important dans les meilleures circonstances. Dans le milieu de travail moderne d’aujourd’hui, le volume, la variété et la rapidité du contenu permettent l’innovation et le travail à distance, tout en développant les exigences et le processus de gestion des collections pour les enquêtes eDiscovery.

Le flux de travail de collecte pose d’importants défis techniques liés à l’extraction de contenu à partir d’emplacements et de sources natifs. Il s’agit également d’un point critique dans l’évaluation et la stratégie pour les scénarios courants de litiges ou d’enquêtes. À mesure que les organisations commencent à évaluer une enquête, les premières questions posées sont celles qui ont participé à l’enquête. Après avoir identifié les personnes impliquées, ces consignataires peuvent rapidement être mis en attente pour conserver le contenu pertinent. La question suivante est ce qui s’est produit? Pour répondre à cette deuxième question fondamentale de toute enquête, les responsables doivent se tourner vers les données. Pour évaluer rapidement le contenu le plus pertinent à la question de ce qui s’est produit, les gestionnaires commencent à affiner la cible de la question afin de s’assurer que les résultats de la collecte sont complets sans être trop larges.

Les collections dans eDiscovery (Premium) permettent aux responsables eDiscovery d’étendre rapidement une recherche de contenu dans les e-mails, les documents, les réactions Teams et d’autres contenus dans Microsoft 365. Les collections fournissent aux responsables une estimation du contenu qui peut être pertinent pour le cas. Cela permet aux gestionnaires de prendre des décisions rapides et éclairées sur la taille et l’étendue du contenu pertinent pour un cas. Les gestionnaires eDiscovery peuvent créer une collection pour rechercher des sources de données custodiales (telles que des boîtes aux lettres et des sites SharePoint) et en utilisant des critères de recherche spécifiques (tels que des mots clés et des plages de dates) pour définir rapidement l’étendue de leur collection.

Une fois la collection définie, les gestionnaires eDiscovery peuvent enregistrer la collection sous forme de brouillon et obtenir des estimations, notamment des estimations pour le volume de données, les emplacements de contenu qui contiennent des résultats et le nombre d’accès à la condition de requête de recherche. Ces insights peuvent vous aider à déterminer si le regroupement doit être révisé pour affiner ou étendre l’étendue du regroupement avant de passer aux étapes de révision et d’analyse dans le flux de travail eDiscovery.

Lorsque le responsable est satisfait de l’étendue de la collection et de la quantité estimée de contenu susceptible d’être réactif, le gestionnaire peut ajouter ou *valider* le contenu dans un ensemble de révisions. Lors de la validation d’un regroupement dans un ensemble de révisions, ce gestionnaire dispose également des options permettant d’inclure des conversations, des pièces jointes cloud et des versions de document. Le contenu de la collection passe également par un autre niveau de traitement pendant l’ingestion dans le jeu de révision. et la collection sera mise à jour avec le résumé final de la collection. Une fois le contenu ajouté à l’ensemble de révisions, les gestionnaires eDiscovery peuvent continuer à interroger, regrouper et affiner le contenu pour faciliter la réduction et la révision. En outre, la collection est mise à jour avec des informations et des statistiques sur le contenu validé dans le jeu de révision. Cela fournit une référence historique sur le contenu de la collection.

Avec la publication de collections dans une eDiscovery (Premium), l’onglet **Recherches** a été renommé **Collections** dans un cas eDiscovery (Premium) dans le portail de conformité Microsoft Purview. Les étapes permettant de définir l’étendue et la taille de la collection suivent le même processus que la recherche pour définir des emplacements et des conditions. Enregistrer en tant que brouillon et obtenir des estimations en préversion permet une validation rapide de l’étendue ciblée des regroupements avant de valider une recherche et une collecte complètes dans le jeu de révisions. Cela permet d’améliorer la gestion des travaux et d’effectuer des itérations ciblées pour commencer à réduire le contenu pendant le processus de recherche et de collecte.

## <a name="collections-workflow"></a>Flux de travail collections

Pour commencer à utiliser des collections dans eDiscovery (Premium), voici un flux de travail de base et des descriptions de chaque étape du processus.

![Flux de travail collections dans eDiscovery (Premium).](../media/CollectionsWorkflow.png)

1. **Créez et exécutez un brouillon de collection**. La première étape consiste à créer un brouillon de collecte et à définir les sources de données custodiales et non-custodiales à rechercher. Vous pouvez également rechercher d’autres sources de données qui n’ont pas été ajoutées au cas. Après avoir ajouté les sources de données, vous configurez la requête de recherche pour rechercher dans les sources de données du contenu pertinent pour le cas. Vous pouvez utiliser des mots clés, des propriétés et des conditions pour créer des requêtes de recherche qui retournent du contenu probablement le plus pertinent pour le cas. Pour plus d’informations, consultez [Créer un projet de collection](create-draft-collection.md).

2. **Passez en revue les estimations et les statistiques**. Après avoir créé un brouillon de collection et l’avoir exécuté, l’étape suivante consiste à afficher les statistiques de collecte pour vous aider à vérifier si le contenu pertinent est trouvé et les emplacements de contenu ayant le plus d’accès. Vous pouvez également afficher un aperçu d’un exemple des résultats de la recherche pour vous aider à déterminer si le contenu est dans le cadre de votre investigation. Pour plus d’informations, consultez [Statistiques et rapports pour les projets de regroupements](collection-statistics-reports.md#statistics-and-reports-for-draft-collections).

3. **Modifiez et réexécutez un brouillon de collection**. En fonction des estimations et des statistiques retournées par la collection, vous pouvez modifier le brouillon de la collection en modifiant les sources de données recherchées et la requête de recherche pour développer ou affiner la collection. Vous pouvez mettre à jour et réexécuter le brouillon de la collection jusqu’à ce que vous soyez certain que la collection contient le contenu le plus pertinent pour votre cas.

4. **Validez un brouillon de collection dans un jeu de révision**. Lorsque vous êtes convaincu que la collection retourne le contenu de type pertinent pour le cas, vous pouvez valider la collection dans le jeu de révisions. Lorsque vous validez une collection, vous avez la possibilité d’ajouter des threads de conversation, des pièces jointes cloud et des versions de document au jeu de révision, qui peuvent tous être pertinents pour le cas.

   Lorsque vous validez une collection, les éléments enfants tels que les signatures de courrier électronique et les images sont extraits d’un élément parent (tel qu’un e-mail, un message de conversation ou un document), puis traités par reconnaissance optique de caractères (OCR) pour extraire du texte de l’élément enfant. Le texte extrait d’éléments enfants est ensuite ajouté à son élément parent afin que vous puissiez l’afficher dans l’ensemble de révisions. En n’ajoutant pas d’éléments enfants à l’ensemble de révision sous la forme d’un fichier distinct, eDiscovery (Premium) permet de limiter le nombre d’éléments potentiellement immatériaux ajoutés au jeu de révision. Pour plus d’informations sur la façon dont les éléments enfants sont gérés, consultez [statistiques et rapports](collection-statistics-reports.md#collection-contents) de collection.

   Pour plus d’informations, consultez [Commit a draft collection to a review set](commit-draft-collection.md).

5. **Passez en revue le résumé et les statistiques des regroupements**. Après avoir validé une collection dans un jeu de révision, les informations relatives à la collection sont conservées, telles que des statistiques sur les éléments extraits, l’indexation approfondie, la requête de recherche utilisée pour la collection et les emplacements de contenu à partir desquelles les éléments ont été collectés. En outre, les collections validées ne peuvent pas être modifiées ou réexécutées. Vous pouvez uniquement les copier ou les supprimer. La conservation des collections fournit un enregistrement historique des éléments collectés qui ont été ajoutés à un jeu de révision. Pour plus d’informations, consultez [Statistiques et rapports pour les regroupements validés](collection-statistics-reports.md#statistics-and-reports-for-committed-collections).
