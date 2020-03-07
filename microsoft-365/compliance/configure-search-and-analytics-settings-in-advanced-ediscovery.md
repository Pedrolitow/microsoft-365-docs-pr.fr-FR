---
title: Configurer les paramètres de recherche et d’analyse
f1.keywords:
- NOCSH
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
description: Configurez des paramètres eDiscovery avancés qui s’appliquent à tous les jeux de révision dans un cas. Cela inclut les paramètres d’analyse et de reconnaissance optique de caractères.
ms.openlocfilehash: 9a7568fac91fa9c021d05b255fc0a145002e7f29
ms.sourcegitcommit: b567e946b57697186267cdfe303dfe3463cfd6ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "42552064"
---
# <a name="configure-search-and-analytics-settings"></a>Configurer les paramètres de recherche et d’analyse

Vous pouvez configurer les paramètres de chaque cas de découverte électronique avancée pour contrôler les fonctionnalités suivantes.

- Quasi-doublons et Threading de courrier électronique

- Thèmes

- Requête de jeu de validation autogénéré

- Ignorer le texte

- Reconnaissance optique de caractères

Pour configurer les paramètres de recherche et d’analyse d’un cas :

1. Sur la page **Advanced eDiscovery** , sélectionnez le cas.

2. Dans l’onglet **paramètres** , sous **recherche & Analytics**, cliquez sur **Sélectionner**.

   La page Paramètres de l’incident s’affiche. Ces paramètres sont appliqués à tous les jeux de révision dans un cas.

   ![Configurer les paramètres d’analyse et de recherche pour un cas avancé eDiscovery](../media/AeDCaseSettings.png)

## <a name="near-duplicates-and-email-threading"></a>Quasi-doublons et Threading de courrier électronique

Dans cette section, vous pouvez définir des paramètres pour la détection des doublons, la détection des doublons et le Threading de messagerie. Pour plus d’informations, consultez la rubrique [near Detection Detection](near-duplicates.md) and [email Threading](email-threading.md).

- **Presque en double/Threading de courrier électronique :** Lorsque ce paramètre est activé, la détection des doublons, la détection quasi des doublons et le Threading de messagerie sont inclus dans le flux de travail lorsque vous exécutez Analytics sur les données d’un jeu de révision.

- **Seuil de similarité des documents et des messages électroniques :** Si le niveau de similarité de deux documents est supérieur au seuil, les deux documents sont placés dans le même ensemble presque en double.

- **Nombre minimal/maximum de mots :** Ces paramètres spécifient que les doublons et l’analyse de thread électronique sont effectués uniquement sur les documents qui contiennent au moins le nombre minimal de mots et le nombre maximal de mots.

## <a name="themes"></a>Thèmes

Dans cette section, vous pouvez définir des paramètres pour les thèmes. Pour plus d’informations, consultez la rubrique [Themes](themes-in-advanced-ediscovery.md).

- **Thèmes :** Lorsque ce paramètre est activé, le clustering de thèmes est effectué dans le cadre du flux de travail lorsque vous exécutez Analytics sur les données d’un jeu de révision.

- **Nombre maximal de thèmes :** Spécifie le nombre maximal de thèmes pouvant être générés lorsque vous exécutez Analytics sur les données d’un jeu de révision.

- **Inclure les numéros dans les thèmes :** Lorsque ce paramètre est activé, les numéros (qui identifient un thème) sont inclus lors de la génération de thèmes. 

- **Ajuster le nombre maximal de thèmes de manière dynamique :** Dans certains cas, il se peut qu’il n’y ait pas assez de documents dans un ensemble de révision pour produire le nombre souhaité de thèmes. Lorsque ce paramètre est activé, Advanced eDiscovery ajuste le nombre maximal de thèmes de manière dynamique au lieu de tenter d’appliquer le nombre maximal de thèmes.

## <a name="review-set-query"></a>Examiner la requête Set

Si vous activez la case à cocher **créer automatiquement un pour vérifier les recherches enregistrées après analyse** , Advanced EDiscovery génère automatiquement la requête Set appelée **for Review.** 

![La requête de révision générée automatiquement](../media/AeDForReviewQuery.png)

Cette requête filtre en fait des éléments dupliqués de l’ensemble de révision. Cela vous permet de passer en revue les éléments uniques dans l’ensemble de révision. Cette requête est créée uniquement lorsque vous exécutez Analytics pour un jeu de réexamen dans le cas. Pour plus d’informations sur la vérification des requêtes Set, voir [query the Data in a Review Set](review-set-search.md).

## <a name="ignore-text"></a>Ignorer le texte

Il existe des situations dans lesquelles certains textes réduisent la qualité de l’analyse, tels que les clauses d’exclusion de responsabilité longues qui sont ajoutées aux messages électroniques quel que soit le contenu du courrier électronique. Si vous êtes conscient du texte qui doit être ignoré, vous pouvez l’exclure de l’analyse en spécifiant la chaîne de texte et la fonctionnalité d’analyse (presque-Duplicates, le Threading de courrier électronique, les thèmes et la pertinence) pour lesquels le texte doit être exclu. L’utilisation d’expressions régulières (RegEx) comme texte ignoré est également prise en charge. 

## <a name="optical-character-recognition-ocr"></a>Reconnaissance optique de caractères (OCR)

Lorsque ce paramètre est activé, la reconnaissance optique de caractères est exécutée sur les fichiers d’image ajoutés aux ensembles de révision afin que le texte de l’image puisse être révisé, recherché, balisé et analysé. Vous pouvez afficher le texte extrait dans la visionneuse de texte du fichier image sélectionné dans l’ensemble de révision. Pour plus d’informations, voir :

- [Ajouter des résultats de recherche à un jeu à réviser](add-data-to-review-set.md#optical-character-recognition)

- [Types de fichiers image pris en charge](supported-filetypes-ediscovery20.md#image)
