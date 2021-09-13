---
title: Valider une collection au brouillon vers un ensemble de révisions
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Après avoir créé et itérer sur un brouillon de collection, vous pouvez la valider dans un jeu à réviser. Lorsque vous valider un brouillon de collection, les éléments collectés sont ajoutés au jeu à réviser dans le cas. Une fois que les éléments collectés sont dans l’ensemble de révision, vous pouvez les analyser, les examiner et les exporter.
ms.openlocfilehash: 9b63117a90f6373e485f74e2edccfa0992ca2ded
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59164033"
---
# <a name="commit-a-draft-collection-to-a-review-set-in-advanced-ediscovery"></a>Valider un brouillon de collection dans un jeu à réviser dans Advanced eDiscovery

Lorsque vous êtes satisfait des éléments que vous avez collectés dans un brouillon de collection et que vous êtes prêt à les analyser, les baliser et les passer en revue, vous pouvez ajouter une collection à un jeu à réviser dans le cas. Lorsque vous valider un brouillon de collection dans un jeu à réviser, les éléments collectés sont copiés à partir de leur emplacement de contenu d’origine dans Microsoft 365 dans un ensemble de révision. Un groupe de révision est un emplacement sécurisé fourni par Microsoft stockage Azure dans le cloud Microsoft.

## <a name="commit-a-draft-collection-to-a-review-set"></a>Valider une collection au brouillon vers un ensemble de révisions

1. Dans la Centre de conformité Microsoft 365, ouvrez Advanced eDiscovery cas, puis sélectionnez l’onglet **Collections** pour afficher la liste des collections dans le cas.

   ![Liste des collections dans un cas.](../media/CommitDraftCollections1.png)

   > [!TIP]
   > Une valeur de la colonne État identifie les collections provisoires qui peuvent `Estimated` être ajoutées à un jeu à  réviser. L’état indique qu’une collection a déjà été ajoutée à un `Committed` jeu à réviser.

2. Dans la page **Collections,** sélectionnez le brouillon de collection que vous souhaitez valider dans un jeu à réviser.

3. En bas de la page volante, sélectionnez La collection **Actions**  >  **Modifier.**

4. Dans l’Assistant Modification de collection, cliquez sur **Suivant** jusqu’à ce que la page Enregistrer le brouillon **ou** Collecter s’affiche.

5. Configurez les paramètres suivants :

   1. Sélectionnez **Collecter les éléments et ajoutez-les au jeu à réviser.**

   2. Décidez s’il faut ajouter la collection à un nouvel ensemble de révision (qui est créé après l’avoir soumis) ou l’ajouter à un groupe de révision existant. Complétez cette section en fonction de votre décision.

   3. Configurez les paramètres de collection supplémentaires :

       - **Teams** et Yammer messages : sélectionnez cette option pour ajouter des threads de conversation à la collection qui incluent les éléments de conversation renvoyés par la requête de recherche dans la collection. Cela signifie que la conversation qui contient les éléments qui correspondent aux critères de recherche est reconstruite. Cela vous permet de passer en revue les éléments de conversation dans le contexte de la conversation de va-et-vient. Pour plus d’informations, [voir Threads de conversation dans Advanced eDiscovery](conversation-review-sets.md).

       - **Pièces jointes dans le cloud**: sélectionnez cette option pour inclure des pièces jointes modernes ou des fichiers liés lorsque les résultats de la collection sont ajoutés au jeu à réviser. Cela signifie que le fichier cible d’une pièce jointe moderne ou d’un fichier lié est ajouté au jeu à réviser.

       - **SharePoint versions**: sélectionnez cette option pour activer la collection de toutes les versions d’un document SharePoint selon les limites de version et les paramètres de recherche de la collection. La sélection de cette option augmente considérablement la taille des éléments ajoutés au jeu à réviser.

   4. Configurez les paramètres pour définir l’échelle de la collection à ajouter au jeu à réviser :

      - **Ajouter tous les résultats de la collection**: sélectionnez cette option pour ajouter tous les éléments qui correspondent aux critères de recherche de la collection au jeu à réviser.

      - **Ajoutez un exemple des résultats** de la collection : sélectionnez cette option pour ajouter un échantillon des résultats de la collection au jeu à réviser au lieu d’ajouter tous les résultats. Si vous sélectionnez cette option, cliquez sur **Modifier les exemples de paramètres** et choisissez l’une des options suivantes :

         - **Exemple basé sur la confiance**: les éléments de la collection sont ajoutés au jeu à réviser sont déterminés par les paramètres statistiques que vous définissez. Si vous utilisez généralement un niveau de confiance et un intervalle lors de l’échantillonnage des résultats, spécifiez-les dans les zones de la baisse. Dans le cas contraire, utilisez les paramètres par défaut.

         - **Exemple aléatoire :** les éléments de la collection sont ajoutés au jeu à réviser en fonction d’une sélection aléatoire du pourcentage spécifié du nombre total d’éléments renvoyés par la recherche.

6. Dans la page **Examiner votre collection,** vous pouvez passer en revue les paramètres de collection que vous avez configurés sur la page précédente. Cliquez **sur Modifier** si vous souhaitez les modifier.

7. Cliquez **sur Envoyer** pour créer le brouillon de la collection. Une page s’affiche confirmant que la collection a été créée.

## <a name="what-happens-after-you-commit-a-draft-collection"></a>Que se passe-t-il après la validation d’un brouillon de collection ?

Lorsque vous valider un brouillon de collection dans un groupe de révision, les choses suivantes se produisent :

- Si vous avez créé un nouveau jeu à réviser pour valider la  collection, le jeu à réviser est créé et affiché sous l’onglet Ensembles de révision dans le cas. L’état du nouvel ensemble de révision est **prêt.** Cette valeur d’état signifie que le jeu à réviser a été créé ; Cela ne signifie pas que la collection a été ajoutée au jeu à réviser. L’état de l’ajout d’éléments dans la collection au jeu à réviser s’affiche sous **l’onglet Collections.**

- La requête de recherche de collection est à nouveau exécuté. Cela signifie que les résultats de recherche réels copiés dans le jeu à réviser peuvent être différents des résultats estimés qui ont été renvoyés lors de la dernière utilisation de la recherche de collection.

- Tous les éléments des résultats de la recherche sont copiés à partir de la source de données d’origine dans le service en direct et copiés dans un emplacement stockage Azure sécurisé dans le cloud Microsoft.

- Tous les éléments (y compris le contenu et les métadonnées) qui ne se trouvent pas dans des sources de données de dépositaire ou non dépositaire sont réindexés (dans un processus appelé *indexation* approfondie) afin que toutes les données du jeu à réviser soient entièrement utilisables dans une recherche pendant l’examen des données de cas. La réindexation du contenu d’une collection entraîne des recherches approfondies et rapides lorsque vous recherchez ou filtrez le contenu du jeu à réviser au cours de l’examen du cas.

- Les documents SharePoint et OneDrive chiffrés et les messages électroniques joints qui sont renvoyés dans les résultats de la recherche sont déchiffrés lorsque vous validerez la collection dans un groupe de révision. Vous pouvez examiner et interroger les fichiers déchiffrés dans le jeu à réviser. Pour plus d’informations, voir Déchiffrement dans [Microsoft 365 outils eDiscovery](ediscovery-decryption.md).

- La fonctionnalité de reconnaissance optique de caractères (OCR) extrait le texte des images et inclut le texte de l’image avec le contenu ajouté à un jeu à réviser. Pour plus d’informations, voir la section [Reconnaissance optique de](#optical-character-recognition) caractères de cet article.

- Une fois la validation terminée, la valeur de la colonne d’état de l’onglet **Collections** est modifiée en `Committed` .

## <a name="optical-character-recognition"></a>Reconnaissance optique des caractères

Lorsque vous valider une collection dans un jeu à réviser, la fonctionnalité de reconnaissance optique de caractères (OCR) dans Advanced eDiscovery extrait automatiquement le texte des images et inclut le texte de l’image avec le contenu ajouté à un jeu à réviser. Vous pouvez afficher le texte extrait dans la visionneuse de texte du fichier image sélectionné dans le jeu à réviser. afin de l’examiner et de l’analyser de manière plus approfondie. La reconnaissance optique des caractères est prise en charge pour les fichiers isolés, les pièces jointes et les images incorporées. Pour consulter la liste des formats de fichiers image pris en charge par la reconnaissance optique des caractères, voir [Types de fichiers pris en charge dans Advanced eDiscovery](supported-filetypes-ediscovery20.md#image).

Vous devez activer la fonctionnalité de reconnaissance optique des caractères pour chaque cas que vous créez dans Advanced eDiscovery. Pour plus d’informations, voir Configurer les paramètres de recherche [et d’analyse.](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr)
