---
title: Afficher un aperçu des résultats d’une recherche de découverte électronique
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Afficher l’aperçu d’un exemple de résultats renvoyés par une recherche de contenu ou une recherche eDiscovery (Standard) dans le portail de conformité Microsoft Purview.
ms.openlocfilehash: ebb0a03f9158f868d2dce0f29c246f78126e1721
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67822526"
---
# <a name="preview-ediscovery-search-results"></a>Afficher un aperçu des résultats de la recherche de découverte électronique

Après avoir exécuté une recherche de contenu ou une recherche associée à un cas Microsoft Purview eDiscovery (Standard), vous pouvez afficher un aperçu d’un exemple des résultats renvoyés par la recherche. L’aperçu des éléments renvoyés par la requête de recherche peut vous aider à déterminer si la recherche retourne les résultats que vous espériez, ou si vous devez modifier la requête de recherche et réexécuter la recherche.

Pour afficher l’aperçu d’un exemple de résultats renvoyés par une recherche :

1. Dans le portail de conformité Microsoft Purview, accédez à la page de recherche de contenu ou sur un cas eDiscovery (Standard).

2. Sélectionnez Rechercher pour afficher la page volante.

3. En bas de la page volante, cliquez sur **Échantillon d’évaluation**.

   ![Cliquez sur Exemple de révision dans la page volante pour afficher un aperçu des résultats](../media/PreviewSearchResults1.png)

   Une page s’affiche et contient un échantillon des résultats de la recherche.

4. Sélectionnez un élément pour afficher son contenu dans le volet de lecture.

   ![Afficher un aperçu des éléments dans le volet de lecture](../media/PreviewSearchResults2.png)

   Dans la capture d’écran précédente, notez que les mots clés de la requête de recherche sont mis en évidence lors de l’aperçu des éléments.

## <a name="how-the-search-result-samples-are-selected"></a>Comment les échantillons de résultats de recherche sont sélectionnés

Un maximum de 1 000 éléments sélectionnés de façon aléatoire sont disponibles pour aperçu. Outre une sélection aléatoire, les éléments disponibles pour aperçu doivent également répondre aux critères suivants :

- Un maximum de 100 éléments à partir d’un emplacement de contenu unique (une boîte aux lettres ou un site) peuvent être prévisualiser. Cela signifie qu’il est possible que moins de 1 000 éléments soient disponibles pour l’aperçu. Par exemple, si vous recherchez quatre boîtes aux lettres et que la recherche renvoie 1 500 éléments estimés, seuls 400 seront disponibles pour la prévisualisation, car seuls 100 éléments de chaque boîte aux lettres peuvent être prévisualisés.

- Pour les éléments de boîte aux lettres, seuls les courriers électroniques peuvent être aperçus. Les éléments tels que les tâches, les éléments de calendrier et les contacts ne peuvent pas être aperçus.

- Pour les éléments de site, seuls les documents peuvent être aperçus. Les éléments tels que les dossiers, listes ou pièces jointes de liste ne peuvent pas être prévisualisés.

## <a name="file-types-supported-when-previewing-search-results"></a>Types de fichiers pris en charge lors de l’aperçu des résultats de la recherche

Vous pouvez afficher un aperçu des types de fichiers pris en charge dans le volet de visualisation. Si un type de fichier n’est pas pris en charge, vous devez télécharger une copie du fichier sur votre ordinateur local (en cliquant sur **Télécharger l’élément d’origine**). Pour les pages web .aspx, l’URL de la page est incluse, même si vous n’êtes peut-être pas autorisé à accéder à la page. Les éléments non indexés ne peuvent pas être affichés en aperçu.

Les types de fichiers suivants sont pris en charge et peuvent être prévisualisés dans le volet résultats de la recherche.
  
- .txt, .html, .mhtml

- .eml

- .doc, .docx, .docm

- .pptm, .pptx

- .pdf

De plus, les types de conteneur de fichier suivants sont pris en charge. Vous pouvez afficher la liste des fichiers dans le conteneur dans le volet de visualisation.
  
- .zip

- .gzip