---
title: Cas importants dans Advanced eDiscovery
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
description: Utilisez de grands cas dans Advanced eDiscovery pour ajouter d’autres éléments aux jeux de révision et tirer parti d’autres limites accrues.
ms.openlocfilehash: d4737b6c715ac96fc9e16c40e2f4fa784a66e5d1
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53542462"
---
# <a name="use-large-cases-in-advanced-ediscovery-preview"></a>Utiliser de grands cas dans Advanced eDiscovery (prévisualisation)

D’autres organisations utilisent la solution Advanced eDiscovery dans Microsoft 365 pour les processus eDiscovery critiques. Cela inclut la réponse aux demandes réglementaires, aux enquêtes et aux litiges. À mesure que l’Advanced eDiscovery augmente, une exigence courante du client consiste à développer la quantité totale de contenu qui peut être gérée dans un cas Advanced eDiscovery unique. Pour vous aider à prendre en compte les augmentations importantes de la taille de cas, à la fois pour le volume total de données et le nombre total d’éléments, vous pouvez désormais choisir un grand format de cas lorsque vous créez un Advanced eDiscovery de données.  

## <a name="create-a-large-case"></a>Créer un cas important

Pour créer un cas important :

1. Accédez à <https://compliance.microsoft.com> et connectez-vous.

2. Dans le volet de navigation gauche du Centre de conformité Microsoft 365, cliquez sur **eDiscovery > Advanced**.

3. Dans la page **Advanced eDiscovery,** cliquez sur **l’onglet Cas,** puis cliquez **sur Créer un cas.**

   La page de présentation du nouveau cas **eDiscovery** s’affiche. La section **Format de** cas offre la possibilité de créer un cas important. Choisissez ce type de cas si vous devez collecter une grande quantité de contenu sur une courte période de temps.

   ![Grande option de cas dans la page Nouveau cas eDiscovery](..\media\AeDLargeCases1.png)

4. Après avoir nommé le  cas, sélectionnez l’option Grand cas, puis cliquez sur **Enregistrer** pour créer le cas important.

## <a name="benefits-of-large-cases"></a>Avantages des cas importants

Le nouveau format de cas de grande taille vous permet de gérer les cas qui contiennent plus de 40 millions d’éléments. Cette fonctionnalité vous permet de gérer efficacement de grands volumes de données de cas via l’ensemble du flux de travail eDiscovery.

Voici une liste des autres avantages des cas importants dans Advanced eDiscovery flux de travail.

- **Collection**: dans le format grand format, vous pouvez collecter jusqu’à 1 To de données pour une seule collection. 

   Pour chaque grand cas, les paramètres de collection collectent par défaut les pièces jointes cloud et les Teams et Yammer contenu. Ces paramètres permettent de recueillir l’image complète des communications numériques au sein d’une enquête. Pour les conversations contextuelles Teams et Yammer, le format de cas élevé convertit les captures instantanées basées sur le temps de 1:1, 1 : N et les conversations de canal en transcriptions html afin de fournir du contexte aux conversations et de réduire le nombre total d’éléments produits par le contenu basé sur la conversation.  

- **Révision**: chaque ensemble de révision prendra en charge jusqu’à 1 To de contenu de pré-expansion. Des métadonnées supplémentaires seront disponibles pour les filtres et les requêtes, notamment le nom de l’équipe, le nom du canal et le nom de conversation pour Teams contenu. Chaque transcription inclut du contenu basé sur le temps avant et après l’élément réactif. Pour les conversations de canal, le billet racine et toutes les réponses sont collectés pour le contenu réactif.  

- **Exporter**: vous pouvez exporter de grands ensembles de contenu en une seule tâche d’exportation. Le format de grande taille vous permet d’exporter 5 millions de documents ou 500 Go, selon la taille la plus petite d’une tâche d’exportation.

En outre, le nouveau format de cas de grande taille inclut une interface utilisateur mise à jour qui affiche la taille totale de chaque jeu à réviser dans le cas. Les tailles des ensembles de révision sont affichées dans une colonne de l’onglet Révision **et** dans un volet volant qui persiste de chaque onglet dans le cas.

![Statistiques de cas de grande taille dans Advanced eDiscovery’interface utilisateur](..\media\LargeCaseUI.png)

## <a name="frequently-asked-questions"></a>Foire aux questions

**Si j’essaie de collecter plus de 1 To dans une seule collection, cela fonctionne-t-il ?**

Les performances seront négativement impactées et peuvent provoquer une instabilité dans certains cas.

**Si les pièces jointes cloud sont incluses par défaut dans le format grand format ; Comment puis-je supprimer ce contenu de mon expérience d’avis ?**  

Utilisez des filtres de jeu à réviser pour filtrer par type de message ou pour exclure les pièces jointes cloud à l’aide du filtre HasAttachment. Pour plus d’informations, voir [Requête et filtrage du contenu dans un jeu à réviser.](review-set-search.md)

**Lors de l’exportation des transcriptions de conversation, le fichier de chargement contiendra-t-il toutes les métadonnées étendues et un seul élément pour chaque transcription ?**

Toutes les métadonnées d’une conversation sont incorporées dans le fichier de transcription HTML.  De nombreux champs communs sont disponibles dans le fichier de chargement. Pour plus d’informations sur les métadonnées exportées, voir Champs de [métadonnées de document Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).
