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
description: Découvrez comment ajouter des résultats de recherche ou des exemples de ces résultats de recherche à un groupe Advanced eDiscovery révision de cas.
ms.openlocfilehash: aeb7942fc12089bd458236221dd7394a8018e780
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59206404"
---
# <a name="add-search-results-to-a-review-set"></a>Ajouter des résultats de recherche à un jeu à réviser

Lorsque vous êtes satisfait des résultats d’une recherche et que vous êtes prêt à passer en revue et à analyser ces résultats de recherche, vous pouvez les ajouter à un groupe de révision dans le cas. La copie des données d’origine dans l’ensemble de révision facilite également le processus de révision et d’analyse en vous fournissant des outils d’analyse avancés tels que la détection de thèmes, la détection de quasi-doublons et l’identification des threads de messagerie. Vous pouvez également ajouter des données provenant de sources de données non Microsoft 365 à un groupe de révision afin de pouvoir passer en revue ces données en plus des données que vous collectez à partir de Microsoft 365.

Lorsque vous ajoutez les résultats d’une recherche à un jeu à  réviser (les ensembles de révision dans un cas sont répertoriés sous l’onglet Ensembles de révision), les éléments suivants se produisent :

- La recherche est de nouveau exécuté. Cela signifie que les résultats de recherche réels copiés dans le jeu à réviser peuvent être différents des résultats estimés qui ont été renvoyés lors de la dernière utilisation de la recherche.

- Tous les éléments des résultats de la recherche sont copiés à partir de la source de données d’origine dans les services en direct et copiés dans un emplacement stockage Azure sécurisé dans le cloud Microsoft.

- Tous les éléments (y compris le contenu et les métadonnées) sont réindexés afin que toutes les données du jeu à réviser soient entièrement accessibles lors de la révision des données de cas. La réindexation des données entraîne des recherches approfondies et rapides lorsque vous recherchez les données dans le jeu à réviser pendant l’examen du cas.

- Un fichier chiffré avec une technologie de chiffrement [Microsoft](encryption.md) et joint à un message électronique renvoyé dans les résultats de la recherche est déchiffré lorsque le message électronique et le fichier joint sont ajoutés au groupe de révision. Vous pouvez examiner et interroger le fichier déchiffré dans le jeu à réviser. Le rôle de déchiffrement RMS doit vous être attribué pour ajouter des pièces jointes de courrier électronique déchiffrées à un groupe de révision. Pour plus d’informations, voir Déchiffrement dans [Microsoft 365 outils eDiscovery](ediscovery-decryption.md).

Pour ajouter des données à un jeu à réviser, cliquez  sur une recherche sous l’onglet **Recherches,** puis cliquez sur Ajouter des résultats à réviser sur la page volante.

Vous pouvez ajouter un jeu à réviser existant ou en créer un nouveau.  Si vous ajoutez un nouveau jeu à réviser, spécifiez le nom, puis cliquez sur **Ajouter** pour afficher la page volante.

![Sélectionnez un jeu à réviser et configurez les options de collection.](../media/AeD_AddToReviewSet.png)

L’ajout de données à un groupe de révision est un processus à long terme. Ce processus comprend la collecte d’éléments à partir des sources de données d’origine dans Microsoft 365 (par exemple, à partir de boîtes aux lettres et de sites), leur copie à l’emplacement stockage Azure (ce processus de copie est également appelé *ingestion),* puis la réindexation des éléments. Vous pouvez suivre l’avancement sous l’onglet **Travaux** ou dans  l’onglet **Recherches** en surveillant l’état dans la colonne Ajout de données à réviser. Une fois le traitement de  l’ensemble de révision terminé, cliquez sur l’onglet Ensembles de révision dans le cas, puis cliquez sur le jeu à réviser pour démarrer le processus de filtrage, de révision, de marquage et d’exportation des données dans le jeu à réviser.

## <a name="define-options-to-scope-your-collection-for-review"></a>Définir des options pour définir l’étendue de votre collection pour révision

Lorsque vous ajoutez le contenu d’une recherche à un groupe de révision existant ou nouveau, vous avez les options suivantes pour collecter le contenu pour révision :

- Inclure les versions de **SharePoint (bêta)**: utilisez cette option pour activer la collection de toutes les versions d’un document SharePoint en fonction des limites de version et des paramètres de recherche de la collection. La sélection de cette option augmente considérablement la taille des éléments ajoutés au jeu à réviser.

- **Options de récupération de conversation**: les éléments ajoutés au jeu à réviser sont activés pour les conversations threadées afin de faciliter la révision du contenu dans le contexte de la conversation de va-et-vient. Pour plus d’informations, [consultez les conversations dans Advanced eDiscovery](conversation-review-sets.md).

- **Activer la récupération des** pièces jointes modernes : utilisez cette option pour inclure des pièces jointes modernes ou des fichiers liés dans la collection pour une révision plus approfondi. Pour plus d’informations sur les propriétés utilisables dans une recherche relatives aux pièces jointes modernes, voir les champs de [métadonnées](document-metadata-fields-in-Advanced-eDiscovery.md)de document Advanced eDiscovery .

## <a name="add-a-sample-to-a-review-set"></a>Ajouter un exemple à un jeu à réviser

Si vous souhaitez valider plus minutieusement les résultats d’une recherche avant de les ajouter tous à un jeu à réviser, vous pouvez ajouter un échantillon des résultats de la recherche à un jeu à réviser au lieu de tout ajouter.

Pour ajouter un exemple à un jeu à réviser, cliquez sur une recherche sous l’onglet **Recherches** et cliquez sur **Exemple** dans la page volante. Dans la page **Paramètres d’échantillonnage,** choisissez l’une des options suivantes :

- **Niveau de confiance %** et **intervalle de confiance %** : les éléments ajoutés au jeu à réviser sont déterminés par les paramètres statistiques que vous définissez. Si vous utilisez généralement un niveau de confiance et un intervalle lors de l’échantillonnage des résultats, spécifiez-les dans les zones de la baisse. Dans le cas contraire, utilisez les paramètres par défaut.

- **Exemple aléatoire %** : les éléments ajoutés au jeu à réviser sont basés sur une sélection aléatoire du pourcentage spécifié du nombre total d’éléments renvoyés par la recherche.

Après avoir sélectionné et configuré l’une des options précédentes, choisissez un jeu à réviser pour ajouter l’exemple, puis cliquez sur **Envoyer**. Là encore, vous pouvez suivre l’avancement sous l’onglet **Travaux**  ou dans l’onglet **Recherches** en surveillant l’état dans la colonne Données ajoutées à réviser.

## <a name="optical-character-recognition"></a>Reconnaissance optique des caractères

Lorsque vous ajoutez des résultats de recherche à un jeu à réviser, la fonctionnalité de reconnaissance optique de caractères (OCR) dans Advanced eDiscovery extrait automatiquement le texte des images et inclut le texte de l’image avec les données ajoutées à un jeu à réviser. Vous pouvez afficher le texte extrait dans la visionneuse de texte du fichier image sélectionné dans le jeu à réviser. afin de l’examiner et de l’analyser de manière plus approfondie. La reconnaissance optique des caractères est prise en charge pour les fichiers isolés, les pièces jointes et les images incorporées. Pour consulter la liste des formats de fichiers image pris en charge par la reconnaissance optique des caractères, voir [Types de fichiers pris en charge dans Advanced eDiscovery](supported-filetypes-ediscovery20.md#image).

Vous devez activer la fonctionnalité de reconnaissance optique des caractères pour chaque cas que vous créez dans Advanced eDiscovery. Pour plus d’informations, voir Configurer les paramètres de recherche [et d’analyse.](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr)
