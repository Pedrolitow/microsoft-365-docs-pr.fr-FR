---
title: Nouveau format de cas dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
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
description: Utilisez le nouveau format de cas dans eDiscovery (Premium) afin de pouvoir ajouter d’autres éléments pour passer en revue les ensembles et tirer parti d’autres limites accrues et de nouvelles fonctionnalités.
ms.openlocfilehash: 766a9e7b739c911bd001dd1a7de8f0ef1377dc8c
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67824771"
---
# <a name="use-the-new-case-format-in-ediscovery-premium"></a>Utiliser le nouveau format de casse dans eDiscovery (Premium)

De plus en plus d’organisations utilisent la solution eDiscovery (Premium) dans Microsoft Purview pour les processus eDiscovery critiques. Cela comprend la réponse aux demandes réglementaires, aux enquêtes et aux litiges. À mesure que l’utilisation d’eDiscovery (Premium) augmente, une exigence courante du client consiste à développer la quantité totale de contenu qui peut être gérée dans un seul cas eDiscovery (Premium). Pour faciliter la prise en charge des augmentations significatives de la taille des cas, à la fois pour le volume total de données et le nombre total d’éléments, vous pouvez désormais choisir le nouveau format de cas lorsque vous créez un cas eDiscovery (Premium).  

## <a name="create-a-case"></a>Créer un cas

Pour créer un cas eDiscovery (Premium) à l’aide du nouveau format de cas :

1. Accédez à <https://compliance.microsoft.com> et connectez-vous.

2. Dans le volet de navigation gauche de l’portail de conformité Microsoft Purview, cliquez sur **eDiscovery > Avancé**.

3. Dans la page **eDiscovery (Premium),** cliquez sur l’onglet **Cas** , puis sur **Créer un cas**.

   La page de menu volant **Nouveau cas eDiscovery** s’affiche. La section **Format** de cas permet de créer un cas à l’aide du nouveau format.

   ![Option Nouveau format de cas dans la page Nouveau cas eDiscovery.](..\media\AeDNewCaseFormat1.png)

4. Après avoir nommé le cas, sélectionnez l’option **Nouveau** , puis cliquez sur **Enregistrer** pour créer le cas à l’aide du nouveau format.

## <a name="benefits-of-the-new-case-format"></a>Avantages du nouveau format de cas

Le nouveau format de cas vous permet de gérer les cas qui contiennent plus de 40 millions d’éléments. Cette fonctionnalité vous permet de gérer efficacement de grands volumes de données de cas via l’intégralité du flux de travail eDiscovery.

Voici une liste d’autres avantages des cas volumineux dans le flux de travail eDiscovery (Premium).

- **Collection** : dans le nouveau format de cas, vous pouvez collecter jusqu’à 1 To de données pour une collection unique.

   Pour chaque cas, les paramètres de collection collectent par défaut les pièces jointes cloud et le contenu contextuel Teams et Yammer. Ces paramètres permettent de recueillir l’image complète des communications numériques dans le cadre d’une enquête. Pour les conversations contextuelles Teams et Yammer, le nouveau format de cas convertit les instantanés basés sur le temps de 1:1, 1 : N et les conversations de canal en transcriptions HTML afin de fournir le contexte des conversations et de réduire le nombre total d’éléments produits par le contenu basé sur la conversation.  

- **Révision** : chaque ensemble de révisions prend en charge jusqu’à 1 To de contenu pré-expansion. Des métadonnées supplémentaires seront disponibles pour les filtres et les requêtes, notamment le nom de l’équipe, le nom du canal et le nom de conversation pour le contenu Teams. Chaque transcription inclut du contenu basé sur le temps pour avant et après l’élément réactif. Pour les conversations de canal, le billet racine et toutes les réponses seront collectés pour le contenu réactif. Pour plus d’informations, consultez le [flux de travail eDiscovery (Premium) pour le contenu dans Microsoft Teams (préversion)](teams-workflow-in-advanced-ediscovery.md)

- **Exporter** : vous pouvez exporter de grands ensembles de contenu dans une seule tâche d’exportation. Le nouveau format de cas vous permet d’exporter 5 millions de documents ou 500 Go, selon la taille la plus petite d’un travail d’exportation.

En outre, le nouveau format de cas inclut une interface utilisateur mise à jour qui affiche la taille totale de chaque ensemble de révisions dans le cas. Les tailles de jeu de révision sont affichées dans une colonne de l’onglet **Ensembles de révision** .

![Nouvelles statistiques de jeu de révision dans l’interface utilisateur eDiscovery (Premium).](..\media\LargeCaseUI.png)

## <a name="frequently-asked-questions"></a>Foire aux questions

**Si je tente de collecter plus de 1 To dans une collection unique, cela fonctionnera-t-il ?**

Les performances seront négativement affectées et peuvent entraîner une instabilité dans certains cas.

**Si les pièces jointes cloud sont incluses par défaut dans le format grand cas ; comment puis-je supprimer ce contenu de mon expérience de révision ?**  

Utilisez les filtres de jeu de révision pour filtrer par type de message ou pour exclure les pièces jointes cloud à l’aide du filtre HasAttachment. Pour plus d’informations, consultez [Interroger et filtrer du contenu dans un ensemble de révisions](review-set-search.md).

**Lors de l’exportation des transcriptions de conversation de conversation, le fichier de chargement contiendra-t-il toutes les métadonnées développées et un seul élément pour chaque transcription ?**

Toutes les métadonnées d’une conversation sont incorporées dans le fichier de transcription HTML.  La plupart des champs courants sont disponibles dans le fichier de chargement. Pour plus d’informations sur les métadonnées exportées, consultez [Les champs de métadonnées de document dans eDiscovery (Premium).](document-metadata-fields-in-Advanced-eDiscovery.md)
