---
title: Configurer les paramètres de recherche et d’analytique - eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
ms.assetid: ''
ms.custom: seo-marvel-mar2020
description: Configurez les paramètres microsoft Purview eDiscovery (Premium) qui s’appliquent à tous les ensembles de révisions dans un cas. Cela inclut des paramètres pour l’analytique et la reconnaissance optique des caractères.
ms.openlocfilehash: c5b542f224e35a6505dca9cbfacb5f1095fa2dbe
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64992301"
---
# <a name="configure-search-and-analytics-settings-in-ediscovery-premium"></a>Configurer les paramètres de recherche et d’analytique dans eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Vous pouvez configurer les paramètres de chaque cas de découverte électronique Microsoft Purview (Premium) pour contrôler les fonctionnalités suivantes.

- Quasi-doublons et thread de courrier

- Thèmes

- Requête de jeu à réviser générée automatiquement

- Ignorer le texte

- Reconnaissance optique des caractères

Pour configurer les paramètres de recherche et d’analyse d’un cas :

1. Dans la page **eDiscovery (Premium),** sélectionnez le cas.

2. Sous l’onglet **Paramètres**, sous **Recherche et analyse**, cliquez sur **Sélectionner**.

   La page des paramètres de cas s’affiche. Ces paramètres sont appliqués à tous les ensembles de révision dans un cas.

   ![Configurez les paramètres d’analytique et de recherche pour un cas eDiscovery (Premium).](../media/AeDCaseSettings.png)

## <a name="near-duplicates-and-email-threading"></a>Quasi-doublons et thread de courrier

Dans cette section, vous pouvez définir des paramètres pour la détection des doublons, la détection des doublons et le threading d’e-mail. Pour plus d’informations, consultez [La détection des doublons proches](near-duplicate-detection-in-advanced-ediscovery.md) et [le threading d’e-mail](email-threading-in-advanced-ediscovery.md).

- **Quasi-doublons/thread de messagerie :** Quand cette option est activée, la détection des doublons, la détection des doublons et le threading de courrier électronique sont inclus dans le flux de travail lorsque vous exécutez des analyses sur les données d’un jeu de révision.

- **Seuil de similarité des documents et des e-mails :** Si le niveau de similarité de deux documents est au-dessus du seuil, les deux documents sont placés dans le même jeu de doublons proche.

- **Nombre minimal/maximal de mots :** Ces paramètres spécifient que les doublons proches et l’analyse du thread de messagerie sont effectués uniquement sur les documents qui ont au moins le nombre minimal de mots et au maximum le nombre maximal de mots.

## <a name="themes"></a>Thèmes

Dans cette section, vous pouvez définir des paramètres pour les thèmes. Pour plus d’informations, consultez [Thèmes](themes-in-advanced-ediscovery.md).

- **Thèmes:** Lorsqu’il est activé, le clustering de thèmes est effectué dans le cadre du flux de travail lorsque vous exécutez des analyses sur les données d’un ensemble de révisions.

- **Nombre maximal de thèmes :** Spécifie le nombre maximal de thèmes qui peuvent être générés lorsque vous exécutez des analyses sur les données d’un ensemble de révisions.

- **Inclure des nombres dans les thèmes :** Lorsqu’ils sont activés, les nombres (qui identifient un thème) sont inclus lors de la génération de thèmes. 

- **Ajustez dynamiquement le nombre maximal de thèmes :** Dans certaines situations, il se peut qu’il n’y ait pas suffisamment de documents dans un ensemble de révisions pour produire le nombre souhaité de thèmes. Lorsque ce paramètre est activé, eDiscovery (Premium) ajuste dynamiquement le nombre maximal de thèmes au lieu de tenter d’appliquer le nombre maximal de thèmes.

## <a name="review-set-query"></a>Requête de jeu à réviser

Si vous sélectionnez la case à cocher **Créer automatiquement une recherche enregistrée pour révision après l’analyse**, eDiscovery (Premium) génère automatiquement la requête d’ensemble de révision nommée **For Review.** 

![Requête for review générée automatiquement.](../media/AeDForReviewQuery.png)

Cette requête filtre essentiellement les éléments en double du jeu de révision. Cela vous permet de passer en revue les éléments uniques de l’ensemble de révision. Elle n’est créée que lorsque vous effectuez une analyse pour un jeu à réviser dans le cas. Pour plus d’informations sur les requêtes d’ensemble de révision, consultez [Interroger les données d’un jeu de révision](review-set-search.md).

## <a name="ignore-text"></a>Ignorer le texte

Dans certains cas, certains textes diminuent la qualité de l’analyse, par exemple les longues clauses d’exclusion de responsabilité qui sont ajoutées aux messages électroniques, quel que soit le contenu de l’e-mail. Si vous souhaitez ignorer un texte donné, vous pouvez l’exclure de l’analyse en spécifiant la chaîne de texte et la fonctionnalité d’analyse (Quasi-doublons, Thread de courrier, Thèmes et Pertinence) pour laquelle le texte doit être exclu. L’utilisation d’expressions régulières (RegEx) comme texte ignoré est également prise en charge.

## <a name="optical-character-recognition-ocr"></a>Reconnaissance optique des caractères

Lorsque ce paramètre est activé, le traitement OCR est exécuté sur les fichiers image. Le traitement OCR est exécuté dans les situations suivantes :

- Lorsque des consignatateurs et des [sources de données non gardiennes](non-custodial-data-sources.md) sont ajoutés à un cas. Lorsque l’OCR est appliqué aux fichiers image, le texte de ces fichiers peut faire l’objet d’une recherche au cours d’une collection. Le traitement OCR est effectué pendant le processus [d’indexation avancé](indexing-custodian-data.md) . L’OCR est exécuté uniquement sur les éléments traités lors de l’indexation avancée. Par exemple, si un fichier PDF volumineux partiellement indexé ou ayant d’autres erreurs d’indexation est traité pendant l’indexation avancée, l’OCR est également appliqué au fichier. En d’autres termes, le traitement OCR se produit uniquement sur les fichiers réindexés pendant le processus d’indexation avancé. Cela signifie qu’il peut arriver que des consignataires soient ajoutés à un cas, mais que certaines pièces jointes de courrier ne soient pas traitées pour l’OCR, car ces fichiers ne sont pas traités pendant l’indexation avancée.

- Lorsque du contenu provenant d’autres sources de données (qui ne sont pas associés à un consignat et ajoutés au cas dans une source de données non gardienne) est ajouté à un jeu de révision.

Une fois les données ajoutées à un jeu de révision, le texte de l’image peut être révisé, recherché, étiqueté et analysé. Vous pouvez afficher le texte extrait dans la visionneuse de texte du fichier image sélectionné dans le jeu de révision. Pour plus d’informations, voir :

- [Indexation avancée des données des consignataires](indexing-custodian-data.md)

- [Ajouter des résultats de recherche à un jeu à réviser](add-data-to-review-set.md#optical-character-recognition)

- [Types de fichiers image pris en charge](supported-filetypes-ediscovery20.md#image)
