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
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment ajouter des résultats de recherche ou des exemples de ces résultats de recherche à un ensemble de cas eDiscovery (Premium).
ms.openlocfilehash: 1649b766c0e7f39122505d3a73574e478373f5b2
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941124"
---
# <a name="add-search-results-to-a-review-set"></a>Ajouter des résultats de recherche à un jeu à réviser

Lorsque vous êtes satisfait des résultats d’une recherche et que vous êtes prêt à examiner et analyser ces résultats de recherche, vous pouvez les ajouter à un ensemble de révisions dans le cas présent. La copie des données d’origine dans le jeu de révision facilite également le processus de révision et d’analyse en vous fournissant des outils d’analyse avancés tels que la détection des thèmes, la détection en quasi-double et l’identification des threads de messagerie. Vous pouvez également ajouter des données provenant de sources de données non Microsoft 365 à un jeu de révision afin de pouvoir examiner ces données en plus des données que vous collectez à partir de Microsoft 365.

Lorsque vous ajoutez les résultats d’une recherche à un ensemble de révisions (les ensembles de révision dans un cas sont répertoriés sous l’onglet **Ensembles** de révision), les éléments suivants se produisent :

- La recherche est réexécutée. Cela signifie que les résultats de recherche réels copiés dans le jeu de révision peuvent être différents des résultats estimés qui ont été retournés lors de la dernière exécution de la recherche.

- Tous les éléments des résultats de la recherche sont copiés à partir de la source de données d’origine dans les services en direct et copiés vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

- Tous les éléments (y compris le contenu et les métadonnées) sont réindexés afin que toutes les données du jeu de révision puissent faire l’objet d’une recherche complète pendant la révision des données de cas. La réindexation des données entraîne des recherches approfondies et rapides lorsque vous effectuez une recherche dans les données de l’ensemble de révisions pendant l’enquête de cas.

- Un fichier chiffré à l’aide d’une [technologie de chiffrement Microsoft](encryption.md) et attaché à un message électronique retourné dans les résultats de la recherche est déchiffré lorsque le message électronique et le fichier joint sont ajoutés au jeu de révision. Vous pouvez examiner et interroger le fichier déchiffré dans l’ensemble de révisions. Le rôle de déchiffrement RMS doit vous être attribué pour ajouter des pièces jointes déchiffrées à un jeu de révision. Pour plus d’informations, consultez [Déchiffrement dans Microsoft 365 outils eDiscovery](ediscovery-decryption.md).

Pour ajouter des données à un ensemble de révisions, cliquez sur une recherche sous l’onglet **Recherches** , puis cliquez sur **Ajouter des résultats pour passer en revue le jeu** dans la page de menu volant.

Vous pouvez ajouter à un jeu de révision existant ou en créer un.  Si vous ajoutez à un nouveau jeu de révision, spécifiez le nom, puis cliquez sur **Ajouter** pour afficher la page de menu volant.

![Sélectionnez un ensemble de révisions et configurez les options de collecte.](../media/AeD_AddToReviewSet.png)

L’ajout de données à un groupe de révision est un processus à long terme. Ce processus inclut la collecte d’éléments à partir des sources de données d’origine dans Microsoft 365 (par exemple, à partir de boîtes aux lettres et de sites), leur copie à l’emplacement stockage Azure (ce processus de copie est également appelé *ingestion*), puis la réindexation des éléments. Vous pouvez suivre la progression de l’onglet **Travaux** ou de l’onglet **Recherches** en surveillant l’état dans les **données ajoutées pour passer en revue** la colonne set. Une fois le traitement du jeu de révision terminé, cliquez sur l’onglet **Ensembles** de révision dans le cas, puis cliquez sur l’ensemble de révisions pour démarrer le processus de filtrage, d’examen, d’étiquetage et d’exportation des données dans l’ensemble de révisions.

## <a name="define-options-to-scope-your-collection-for-review"></a>Définir les options permettant d’étendre votre collection pour révision

Lorsque vous ajoutez le contenu d’une recherche à un ensemble de révisions existant ou nouveau, vous disposez des options suivantes pour collecter le contenu à réviser :

- **Inclure des versions de SharePoint (bêta)** : utilisez cette option pour activer la collecte de toutes les versions d’un document SharePoint en fonction des limites de version et des paramètres de recherche de la collection. La sélection de cette option augmente considérablement la taille des éléments ajoutés à l’ensemble de révision.

- **Options de récupération** de conversation : les éléments ajoutés à l’ensemble de révisions sont activés pour les conversations thread afin d’aider à passer en revue le contenu dans le contexte de la conversation aller-retour. Pour plus d’informations, consultez [Examiner les conversations dans eDiscovery (Premium).](conversation-review-sets.md)

- **Activer la récupération pour les pièces jointes modernes** : utilisez cette option pour inclure des pièces jointes modernes ou des fichiers liés dans la collection pour une révision ultérieure. Pour plus d’informations sur les propriétés pouvant faire l’objet d’une recherche liées aux pièces jointes modernes, consultez [les champs de métadonnées de document dans eDiscovery (Premium).](document-metadata-fields-in-Advanced-eDiscovery.md)

## <a name="add-a-sample-to-a-review-set"></a>Ajouter un exemple à un ensemble de révisions

Si vous souhaitez valider plus précisément les résultats d’une recherche avant de les ajouter à un ensemble de révisions, vous pouvez ajouter un échantillon des résultats de la recherche à un ensemble de révisions au lieu de tout ajouter.

Pour ajouter un exemple à un ensemble de révisions, cliquez sur une recherche sous l’onglet **Recherches** , puis cliquez sur **Exemple** dans la page de menu volant. Dans la page **Paramètres d’échantillonnage** , choisissez l’une des options suivantes :

- **% du niveau de confiance** et **de l’intervalle de confiance %** : les éléments ajoutés à l’ensemble de révision seront déterminés par les paramètres statistiques que vous définissez. Si vous utilisez généralement un niveau de confiance et un intervalle lors de l’échantillonnage des résultats, spécifiez-les dans les zones déroulantes. Sinon, utilisez les paramètres par défaut.

- **% de l’échantillon aléatoire** : les éléments ajoutés au jeu de révision sont basés sur une sélection aléatoire du pourcentage spécifié du nombre total d’éléments retournés par la recherche.

Après avoir sélectionné et configuré l’une des options précédentes, choisissez un ensemble de révisions auquel ajouter l’exemple, puis cliquez sur **Envoyer**. Là encore, vous pouvez suivre la progression de l’onglet **Travaux** ou de l’onglet **Recherches** en surveillant l’état dans les **données ajoutées pour passer en revue** la colonne set.

## <a name="optical-character-recognition"></a>Reconnaissance optique des caractères

Lorsque vous ajoutez des résultats de recherche à un jeu de révision, la fonctionnalité de reconnaissance optique des caractères (OCR) dans eDiscovery (Premium) extrait automatiquement le texte des images et inclut le texte de l’image avec les données ajoutées à un jeu de révision. Vous pouvez afficher le texte extrait dans la visionneuse de texte du fichier image sélectionné dans le jeu de révision. afin de l’examiner et de l’analyser de manière plus approfondie. La reconnaissance optique des caractères est prise en charge pour les fichiers isolés, les pièces jointes et les images incorporées. Pour obtenir la liste des formats de fichier image pris en charge pour OCR, consultez [Types de fichiers pris en charge dans eDiscovery (Premium).](supported-filetypes-ediscovery20.md#image)

Vous devez activer la fonctionnalité OCR pour chaque cas que vous créez dans eDiscovery (Premium). Pour plus d’informations, consultez [Configurer les paramètres de recherche et d’analytique](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
