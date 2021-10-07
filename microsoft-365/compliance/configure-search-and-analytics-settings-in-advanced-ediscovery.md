---
title: Configurer les paramètres de recherche et d’analyse - Advanced eDiscovery
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
description: Configurez Advanced eDiscovery paramètres qui s’appliquent à tous les ensembles de révision dans un cas. Cela inclut les paramètres d’analyse et de reconnaissance optique de caractères.
ms.openlocfilehash: 65175950a430dd6b43cac207e16a17cf02d1bbbf
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60153197"
---
# <a name="configure-search-and-analytics-settings-in-advanced-ediscovery"></a>Configurer les paramètres de recherche et d’analyse dans Advanced eDiscovery

Vous pouvez configurer les paramètres de chaque cas Advanced eDiscovery pour contrôler les fonctionnalités suivantes.

- Quasi-doublons et thread de courrier

- Thèmes

- Requête de jeu à réviser générée automatiquement

- Ignorer le texte

- Reconnaissance optique des caractères

Pour configurer les paramètres de recherche et d’analyse d’un cas :

1. Dans la page **Advanced eDiscovery**, sélectionnez le cas.

2. Sous l’onglet **Paramètres**, sous **Recherche et analyse**, cliquez sur **Sélectionner**.

   La page des paramètres de cas s’affiche. Ces paramètres sont appliqués à tous les ensembles de révision dans un cas.

   ![Configurez les paramètres d’analyse et de recherche pour Advanced eDiscovery cas.](../media/AeDCaseSettings.png)

## <a name="near-duplicates-and-email-threading"></a>Quasi-doublons et thread de courrier

Dans cette section, vous pouvez définir des paramètres pour la détection des doublons, la détection des quasi-doublons et le thread de courrier électronique. Pour plus d’informations, voir Détection des [quasi-doublons et](near-duplicate-detection-in-advanced-ediscovery.md) [thread de messagerie.](email-threading-in-advanced-ediscovery.md)

- **Quasi-doublons/thread de messagerie électronique :** Lorsqu’il est allumé, la détection des doublons, la détection des quasi-doublons et le thread de messagerie électronique sont inclus dans le flux de travail lorsque vous exécutez des analyses sur les données dans un jeu à réviser.

- **Seuil de similarité des documents et des e-mails :** Si le niveau de similarité de deux documents est supérieur au seuil, les deux documents sont placés dans le même jeu de quasi-doublons.

- **Nombre minimal/maximal de mots :** Ces paramètres spécifient que les quasi-doublons et l’analyse du thread de messagerie sont effectués uniquement sur les documents qui ont au moins le nombre minimal de mots et au plus le nombre maximal de mots.

## <a name="themes"></a>Thèmes

Dans cette section, vous pouvez définir des paramètres pour les thèmes. Pour plus d’informations, voir [Thèmes.](themes-in-advanced-ediscovery.md)

- **Thèmes :** Lorsqu’il est allumé, le clustering de thèmes est effectué dans le cadre du flux de travail lorsque vous exécutez des analyses sur les données d’un jeu à réviser.

- **Nombre maximal de thèmes :** Spécifie le nombre maximal de thèmes qui peuvent être générés lorsque vous exécutez des analyses sur les données d’un jeu à réviser.

- **Inclure des nombres dans les thèmes :** Lorsqu’il est allumé, les nombres (qui identifient un thème) sont inclus lors de la génération de thèmes. 

- **Ajustez dynamiquement le nombre maximal de thèmes :** Dans certains cas, il peut y avoir un nombre insuffisant de documents dans un jeu à réviser pour produire le nombre de thèmes souhaité. Lorsque ce paramètre est activé, Advanced eDiscovery ajuste le nombre maximal de thèmes dynamiquement, plutôt que d’essayer d’appliquer le nombre maximal de thèmes.

## <a name="review-set-query"></a>Requête de jeu à réviser

Si vous  sélectionnez la requête Créer automatiquement une recherche pour révision enregistrée après la case à cocher Analyse, Advanced eDiscovery requête de jeu à réviser nommée **Pour révision.** 

![Requête pour révision automatiquement.](../media/AeDForReviewQuery.png)

Cette requête filtre essentiellement les éléments en double du jeu à réviser. Cela vous permet de passer en revue les éléments uniques du jeu à réviser. Elle n’est créée que lorsque vous effectuez une analyse pour un jeu à réviser dans le cas. Pour plus d’informations sur les requêtes de jeu à réviser, voir [Interroger les données dans un jeu à réviser.](review-set-search.md)

## <a name="ignore-text"></a>Ignorer le texte

Dans certains cas, certains textes diminuent la qualité de l’analyse, par exemple les clauses d’exclusion de responsabilité longues qui sont ajoutées aux messages électroniques, quel que soit le contenu de l’e-mail. Si vous souhaitez ignorer un texte donné, vous pouvez l’exclure de l’analyse en spécifiant la chaîne de texte et la fonctionnalité d’analyse (Quasi-doublons, Thread de courrier, Thèmes et Pertinence) pour laquelle le texte doit être exclu. L’utilisation d’expressions régulières (RegEx) en tant que texte ignoré est également prise en charge.

## <a name="optical-character-recognition-ocr"></a>Reconnaissance optique des caractères

Lorsque ce paramètre est désactivé, le traitement ocr est exécuté sur les fichiers image. Le traitement ocr est exécuté dans les situations suivantes :

- Lorsque des dépositaires et des sources de [données non privatives](non-custodial-data-sources.md) sont ajoutés à un cas. Lorsque l’ocr est appliqué aux fichiers image, le texte de ces fichiers est utilisable dans une recherche au cours d’une collection. Le traitement ocr est effectué pendant le [processus d’indexation](indexing-custodian-data.md) avancée. L’ocr est uniquement exécuté sur les éléments qui sont traitées pendant l’indexation avancée. Par exemple, si un fichier PDF de grande taille partiellement indexé ou avec d’autres erreurs d’indexation est traitée pendant l’indexation avancée, l’ocr est également appliqué au fichier. En d’autres termes, le traitement ocr se produit uniquement sur les fichiers qui sont ré-indexés au cours du processus d’indexation avancée. Cela signifie qu’il peut y avoir des situations dans lesquelles des dépositaires sont ajoutés à un cas, mais que certaines pièces jointes de courrier ne sont pas traitées pour l’ocr, car ces fichiers ne sont pas traitées pendant l’indexation avancée.

- Lorsque du contenu provenant d’autres sources de données (qui ne sont pas associés à un dépositaire et ajoutés au cas dans une source de données non liée à la conservation) est ajouté à un groupe de révision.

Une fois les données ajoutées à un jeu à réviser, le texte de l’image peut être révisé, recherché, balisé et analysé. Vous pouvez afficher le texte extrait dans la visionneuse de texte du fichier image sélectionné dans le jeu à réviser. Pour plus d'informations, voir :

- [Indexation avancée des données des consignataires](indexing-custodian-data.md)

- [Ajouter des résultats de recherche à un jeu à réviser](add-data-to-review-set.md#optical-character-recognition)

- [Types de fichiers image pris en charge](supported-filetypes-ediscovery20.md#image)
