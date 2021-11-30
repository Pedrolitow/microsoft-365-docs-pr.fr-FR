---
title: Nouveau format de cas dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: ninachen
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Utilisez le nouveau format de cas dans Advanced eDiscovery vous pouvez ajouter d’autres éléments aux jeux de révision et tirer parti d’autres limites accrues et de nouvelles fonctionnalités.
ms.openlocfilehash: 9b0e87e7d24565bb89444fe5b1e5cbf43d915e42
ms.sourcegitcommit: 7f0c5b55e2966c0c1ce6a153a4e6a7ec035bd818
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2021
ms.locfileid: "61137187"
---
# <a name="use-the-new-case-format-in-advanced-ediscovery"></a>Utilisez le nouveau format de cas dans Advanced eDiscovery

D’autres organisations utilisent la solution Advanced eDiscovery dans Microsoft 365 pour les processus eDiscovery critiques. Cela comprend la réponse aux demandes réglementaires, aux enquêtes et aux litiges. À mesure que l’Advanced eDiscovery augmente, une exigence courante du client consiste à développer la quantité totale de contenu qui peut être gérée dans un cas Advanced eDiscovery unique. Pour vous aider à prendre en compte les augmentations significatives de la taille de cas, à la fois pour le volume total de données et le nombre total d’éléments, vous pouvez désormais choisir le nouveau format de cas lorsque vous créez un cas Advanced eDiscovery.  

## <a name="create-a-case"></a>Créer un cas

Pour créer un cas Advanced eDiscovery’aide du nouveau format de cas :

1. Accédez à <https://compliance.microsoft.com> et connectez-vous.

2. Dans le volet de navigation gauche du Centre de conformité Microsoft 365, cliquez sur **eDiscovery > Advanced**.

3. Dans la page **Advanced eDiscovery,** cliquez sur **l’onglet Cas,** puis cliquez **sur Créer un cas.**

   La page de présentation du nouveau cas **eDiscovery** s’affiche. La section **Case permet** de créer un cas à l’aide du nouveau format.

   ![Nouvelle option de format de cas dans la page Nouveau cas eDiscovery.](..\media\AeDNewCaseFormat1.png)

4. Après avoir nommé le  cas, sélectionnez l’option Nouveau, puis cliquez sur **Enregistrer** pour créer le cas à l’aide du nouveau format.

## <a name="benefits-of-the-new-case-format"></a>Avantages du nouveau format de cas

Le nouveau format de cas vous permet de gérer les cas qui contiennent plus de 40 millions d’éléments. Cette fonctionnalité vous permet de gérer efficacement de grands volumes de données de cas via l’ensemble du flux de travail eDiscovery.

Voici une liste des autres avantages des cas importants dans Advanced eDiscovery flux de travail.

- **Collection**: dans le nouveau format de cas, vous pouvez collecter jusqu’à 1 To de données pour une seule collection.

   Pour chaque cas, les paramètres de collection collectent par défaut les pièces jointes cloud et les Teams et Yammer contenu. Ces paramètres permettent de recueillir l’image complète des communications numériques au sein d’une enquête. Pour les conversations contextuelles Teams et Yammer, le nouveau format de cas convertit les captures instantanées basées sur le temps de 1:1, 1 : N et les conversations de canal en transcriptions HTML pour fournir le contexte des conversations et réduire le nombre total d’éléments produits par le contenu basé sur la conversation.  

- **Révision**: chaque ensemble de révision prendra en charge jusqu’à 1 To de contenu de pré-expansion. Des métadonnées supplémentaires seront disponibles pour les filtres et les requêtes, notamment le nom de l’équipe, le nom du canal et le nom de conversation pour Teams contenu. Chaque transcription inclut du contenu basé sur le temps avant et après l’élément réactif. Pour les conversations de canal, le billet racine et toutes les réponses sont collectés pour le contenu réactif. Pour plus d’informations, [voir Advanced eDiscovery flux de travail pour le contenu Microsoft Teams (aperçu)](teams-workflow-in-advanced-ediscovery.md)

- **Exporter**: vous pouvez exporter de grands ensembles de contenu dans une seule tâche d’exportation. Le nouveau format de cas vous permet d’exporter 5 millions de documents ou 500 Go, selon la taille la plus petite d’une tâche d’exportation.

En outre, le nouveau format de cas inclut une interface utilisateur mise à jour qui affiche la taille totale de chaque jeu à réviser dans le cas. Les tailles des ensembles de révision s’affichent dans une colonne de l’onglet **Ensembles de révision.**

![Nouvelles statistiques de jeu à réviser dans Advanced eDiscovery’interface utilisateur.](..\media\LargeCaseUI.png)

## <a name="frequently-asked-questions"></a>Foire aux questions

**Si j’essaie de collecter plus de 1 To dans une seule collection, cela fonctionne-t-il ?**

Les performances seront négativement impactées et peuvent provoquer une instabilité dans certains cas.

**Si les pièces jointes cloud sont incluses par défaut dans le format grand format ; Comment puis-je supprimer ce contenu de mon expérience d’avis ?**  

Utilisez des filtres de jeu à réviser pour filtrer par type de message ou pour exclure les pièces jointes cloud à l’aide du filtre HasAttachment. Pour plus d’informations, voir [Requête et filtrage du contenu dans un jeu à réviser.](review-set-search.md)

**Lors de l’exportation des transcriptions de conversation, le fichier de chargement contiendra-t-il toutes les métadonnées étendues et un seul élément pour chaque transcription ?**

Toutes les métadonnées d’une conversation sont incorporées dans le fichier de transcription HTML.  De nombreux champs communs sont disponibles dans le fichier de chargement. Pour plus d’informations sur les métadonnées exportées, voir Champs de [métadonnées de document Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).