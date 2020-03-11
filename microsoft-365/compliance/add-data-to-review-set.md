---
title: Ajouter des résultats de recherche à un jeu à réviser
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
description: Ajoutez les résultats d’une recherche associée à un cas avancé eDiscovery. Les éléments sont copiés à partir de leur emplacement d’origine et copiés dans un emplacement de stockage Azure fourni par Microsoft. Les éléments sont également réindexés et Advanced eDiscovery procède à la reconnaissance optique de caractères (OCR) sur les fichiers image et télécharge le texte de l’image à des fins de révision et d’analyse.
ms.openlocfilehash: 5e4eaa5e83bbca3a80abe0026f3880ce8d3c85c4
ms.sourcegitcommit: 0b2c41dad19da5f0513097c36a4ff32a5868836c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2020
ms.locfileid: "42588817"
---
# <a name="add-search-results-to-a-review-set"></a>Ajouter des résultats de recherche à un jeu à réviser

Lorsque vous êtes satisfait des résultats d’une recherche et que vous êtes prêt à passer en revue et à analyser ces résultats de recherche, vous pouvez les ajouter à un jeu de révision dans le cas. La copie des données d’origine dans l’ensemble de révision facilite également le processus de révision et d’analyse en vous fournissant des outils d’analyse avancés, tels que la détection de thèmes, la détection de proximité et l’identification des threads de messagerie. Vous pouvez également ajouter des données provenant de sources de données autres que Office 365 à un jeu de réexamen afin que vous puissiez examiner ces données en plus des données que vous collectez à partir d’Office 365. 

Lorsque vous ajoutez les résultats d’une recherche à un jeu de réviseur (les jeux de révision d’un cas sont répertoriés sous l’onglet **ensembles de révision** ), les événements suivants se produisent :

- La recherche est réexécutée. Cela signifie que les résultats de recherche réels copiés dans l’ensemble de révision peuvent être différents des résultats estimés qui ont été renvoyés lors de la dernière exécution de la recherche.

- Tous les éléments dans les résultats de la recherche sont copiés à partir de la source de données d’origine dans les services Live Office 365 et copiés dans un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

- Tous les éléments (y compris le contenu et les métadonnées) sont réindexés de sorte que toutes les données du jeu de révision soient entièrement utilisables lors de la révision des données de cas. La réindexation des données entraîne des recherches rapides et rapides lors de la recherche des données dans l’ensemble de vérifications lors de l’enquête de cas.

Pour ajouter des données à un jeu de réexamens, cliquez sur une recherche dans l’onglet **recherches** , puis sur **Ajouter des résultats à examiner le jeu** sur la page de menu volant.

![Ajout de données à un ensemble de révision](../media/c1b4fc00-7a15-4587-b9b0-ce594bb02e4d.png)

Vous pouvez ajouter à un jeu de réexamen existant ou créer un jeu de révision.  Si vous ajoutez à un nouveau jeu de réexamen, spécifiez son nom, puis cliquez sur **Ajouter**.

![Sélectionner un jeu de révision](../media/e8c6ab51-da8d-4c39-9b21-26bfdf453fb9.png)

L’ajout de données à un jeu de révision est un processus long. Ce processus inclut la collecte d’éléments à partir des sources de données d’origine dans Office 365 (par exemple, à partir de boîtes aux lettres et de sites), leur copie vers l’emplacement de stockage Azure (ce processus de copie est *également appelé «* ingestion »), puis la réindexation des éléments. Vous pouvez suivre la progression sous l’onglet **travaux** ou sur l’onglet **recherches** en surveillant l’État dans la colonne **données ajoutées à l’ensemble** de modifications. Une fois le traitement de l’ensemble de vérifications terminé, cliquez sur l’onglet **ensembles** de vérifications dans le cas, puis cliquez sur le jeu de révisions pour démarrer le processus de filtrage, de révision, de marquage et d’exportation des données dans l’ensemble de révision.

## <a name="add-a-sample-to-a-review-set"></a>Ajouter un échantillon à un jeu de révision

Si vous souhaitez valider les résultats d’une recherche plus en détail avant de les ajouter à un jeu de révision, vous pouvez ajouter un échantillon des résultats de la recherche à un jeu de révision au lieu d’ajouter tout.

Pour ajouter un exemple à un jeu de réexamens, cliquez sur une recherche sous l’onglet **recherches** et cliquez sur **exemple** sur la page de la fenêtre volante. Sur la page **paramètres d’échantillonnage** , choisissez l’une des options suivantes :

- **Niveau de confiance%** et **intervalle de confiance%** : les éléments ajoutés au jeu de révision sont déterminés par les paramètres statistiques que vous définissez. Si vous utilisez généralement un niveau de confiance et un intervalle lors de l’échantillonnage des résultats, spécifiez-les dans les zones de liste déroulante. Dans le cas contraire, utilisez les paramètres par défaut.

- **Échantillon aléatoire%** : les éléments ajoutés au jeu de révision sont basés sur une sélection aléatoire du pourcentage spécifié du nombre total d’éléments renvoyés par la recherche.

Après avoir sélectionné et configuré l’une des options précédentes, sélectionnez un jeu de réviseur auquel ajouter l’exemple, puis cliquez sur **Envoyer**. Une fois encore, vous pouvez suivre l’avancement sous l’onglet **travaux** ou sur l’onglet **recherches** en surveillant l’État dans la colonne **données ajoutées à l’ensemble** de modifications.

## <a name="optical-character-recognition"></a>Reconnaissance optique de caractères

Lorsque vous ajoutez des résultats de recherche à un jeu de réviseurs, la fonctionnalité de reconnaissance optique de caractères (OCR) dans Advanced eDiscovery extrait automatiquement le texte des images et inclut le texte de l’image avec les données ajoutées à un jeu de révision. Vous pouvez afficher le texte extrait dans la visionneuse de texte du fichier image sélectionné dans l’ensemble de révision. Cela vous permet d’effectuer une révision et une analyse supplémentaires sur le texte des images. La reconnaissance optique de caractères est prise en charge pour les fichiers libres, les pièces jointes et les images incorporées. Pour obtenir la liste des formats de fichiers image pris en charge pour la reconnaissance optique de caractères, voir [types de fichiers pris en charge dans Advanced eDiscovery](supported-filetypes-ediscovery20.md#image).

Vous devez activer la fonctionnalité OCR pour chaque cas que vous créez dans Advanced eDiscovery. Pour plus d’informations, consultez la rubrique [configurer les paramètres de recherche et d’analyse](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
