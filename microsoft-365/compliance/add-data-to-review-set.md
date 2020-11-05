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
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment ajouter des résultats de recherche ou des exemples de ces résultats de recherche à un ensemble de vérification de cas eDiscovery avancé.
ms.openlocfilehash: 25ea5fe076753d4a5685f1224b98a2005d334f5f
ms.sourcegitcommit: d7975c391e03eeb96e29c1d02e77d2a1433ea67c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "48919976"
---
# <a name="add-search-results-to-a-review-set"></a>Ajouter des résultats de recherche à un jeu à réviser

Lorsque vous êtes satisfait des résultats d’une recherche et que vous êtes prêt à passer en revue et à analyser ces résultats de recherche, vous pouvez les ajouter à un jeu de révision dans le cas. La copie des données d’origine dans l’ensemble de révision facilite également le processus de révision et d’analyse en vous fournissant des outils d’analyse avancés, tels que la détection de thèmes, la détection de proximité et l’identification des threads de messagerie. Vous pouvez également ajouter des données provenant de sources de données non-Microsoft 365 à un jeu de vérification afin que vous puissiez examiner ces données en plus des données que vous collectez à partir de Microsoft 365.

Lorsque vous ajoutez les résultats d’une recherche à un jeu de réviseur (les jeux de révision d’un cas sont répertoriés sous l’onglet **ensembles de révision** ), les événements suivants se produisent :

- La recherche est réexécutée. Cela signifie que les résultats de recherche réels copiés dans l’ensemble de révision peuvent être différents des résultats estimés qui ont été renvoyés lors de la dernière exécution de la recherche.

- Tous les éléments des résultats de la recherche sont copiés à partir de la source de données d’origine dans les services Live et copiés dans un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

- Tous les éléments (y compris le contenu et les métadonnées) sont réindexés de sorte que toutes les données du jeu de révision soient entièrement utilisables lors de la révision des données de cas. La réindexation des données entraîne des recherches rapides et rapides lorsque vous recherchez des données dans l’ensemble de vérifications lors de l’enquête de cas.

- Un fichier chiffré avec une [technologie de chiffrement Microsoft](encryption.md) et joint à un message électronique renvoyé dans les résultats de la recherche est déchiffré lorsque le message électronique et le fichier joint sont ajoutés à l’ensemble de révision. Vous pouvez passer en revue et interroger le fichier déchiffré dans l’ensemble de révision. Le rôle de déchiffrement RMS doit vous être attribué pour ajouter des pièces jointes déchiffrées à un jeu de révision. Pour plus d’informations, consultez la rubrique [déchiffrement dans les outils eDiscovery de Microsoft 365](ediscovery-decryption.md).

Pour ajouter des données à un jeu de réexamens, cliquez sur une recherche dans l’onglet **recherches** , puis sur **Ajouter des résultats à examiner le jeu** sur la page de menu volant.

Vous pouvez ajouter à un jeu de réexamen existant ou créer un jeu de révision.  Si vous ajoutez à un nouveau jeu de réexamen, spécifiez son nom, puis cliquez sur **Ajouter** pour afficher la page de menu volant.

![Sélectionner un jeu de révision et configurer les options de la collection](../media/AeD_AddToReviewSet.png)

L’ajout de données à un groupe de révision est un processus à long terme. Ce processus inclut la collecte d’éléments à partir des sources de données d’origine dans Microsoft 365 (par exemple, à partir de boîtes aux lettres et de sites), leur copie vers l’emplacement de stockage Azure (ce processus de copie est *également appelé «* ingestion »), puis la réindexation des éléments. Vous pouvez suivre la progression sous l’onglet **travaux** ou sur l’onglet **recherches** en surveillant l’État dans la colonne **données ajoutées à l’ensemble** de modifications. Une fois le traitement de l’ensemble de vérifications terminé, cliquez sur l’onglet **réviser les ensembles** dans le cas, puis cliquez sur le jeu de révision pour démarrer le processus de filtrage, de révision, de marquage et d’exportation des données dans l’ensemble de révision.

## <a name="define-options-to-scope-your-collection-for-review"></a>Définir les options d’étendue de votre collection à des fins de révision

Lorsque vous ajoutez le contenu d’une recherche à un jeu de réexamen existant ou nouveau, les options suivantes vous permettent de collecter le contenu à des fins de révision :

- **Inclure des versions à partir de SharePoint (version bêta)** : utilisez cette option pour activer la collection de toutes les versions d’un document SharePoint en fonction des limites de version et des paramètres de recherche de la collection. La sélection de cette option augmentera considérablement la taille des éléments ajoutés à l’ensemble de révision.

- **Options de récupération** de la conversation : les éléments ajoutés à l’ensemble de révision sont activés pour les conversations thématiques afin de vous aider à consulter le contenu dans le contexte de la conversation d’avant et d’une conversation. Pour plus d’informations, consultez la rubrique [Review conversations in Advanced eDiscovery](conversation-review-sets.md).

- **Activer la récupération pour les pièces jointes modernes** : utilisez cette option pour inclure les pièces jointes modernes ou les fichiers liés dans la collection à des fins de révision. Pour plus d’informations sur les propriétés pouvant faire l’objet d’une recherche concernant les pièces jointes modernes, voir [document Metadata Fields in Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).

## <a name="add-a-sample-to-a-review-set"></a>Ajouter un échantillon à un jeu de révision

Si vous souhaitez valider les résultats d’une recherche plus en détail avant de les ajouter à un jeu de révision, vous pouvez ajouter un échantillon des résultats de la recherche à un jeu de révision au lieu d’ajouter tout.

Pour ajouter un exemple à un jeu de réexamens, cliquez sur une recherche sous l’onglet **recherches** et cliquez sur **exemple** sur la page de la fenêtre volante. Sur la page **paramètres d’échantillonnage** , choisissez l’une des options suivantes :

- **Niveau de confiance%** et **intervalle de confiance%** : les éléments ajoutés au jeu de révision sont déterminés par les paramètres statistiques que vous définissez. Si vous utilisez généralement un niveau de confiance et un intervalle lors de l’échantillonnage des résultats, spécifiez-les dans les zones de liste déroulante. Dans le cas contraire, utilisez les paramètres par défaut.

- **Échantillon aléatoire%** : les éléments ajoutés au jeu de révision sont basés sur une sélection aléatoire du pourcentage spécifié du nombre total d’éléments renvoyés par la recherche.

Après avoir sélectionné et configuré l’une des options précédentes, sélectionnez un jeu de réviseur auquel ajouter l’exemple, puis cliquez sur **Envoyer**. Une fois encore, vous pouvez suivre l’avancement sous l’onglet **travaux** ou sur l’onglet **recherches** en surveillant l’État dans la colonne **données ajoutées à l’ensemble** de modifications.

## <a name="optical-character-recognition"></a>Reconnaissance optique des caractères

Lorsque vous ajoutez des résultats de recherche à un jeu de réviseurs, la fonctionnalité de reconnaissance optique de caractères (OCR) dans Advanced eDiscovery extrait automatiquement le texte des images et inclut le texte de l’image avec les données ajoutées à un jeu de révision. Vous pouvez afficher le texte extrait dans la visionneuse de texte du fichier image sélectionné dans l’ensemble de révision. afin de l’examiner et de l’analyser de manière plus approfondie. La reconnaissance optique des caractères est prise en charge pour les fichiers isolés, les pièces jointes et les images incorporées. Pour consulter la liste des formats de fichiers image pris en charge par la reconnaissance optique des caractères, voir [Types de fichiers pris en charge dans Advanced eDiscovery](supported-filetypes-ediscovery20.md#image).

Vous devez activer la fonctionnalité de reconnaissance optique des caractères pour chaque cas que vous créez dans Advanced eDiscovery. Pour plus d’informations, consultez la rubrique [configurer les paramètres de recherche et d’analyse](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
