---
title: Gérer les travaux dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Advanced eDiscovery tâches vous aident à suivre l’état des processus de longue durée liés à l’exécution de Advanced eDiscovery tâches.
ms.openlocfilehash: d5b2facdead3be1369cd261392117fc33fa1a4fb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60192198"
---
# <a name="manage-jobs-in-advanced-ediscovery"></a>Gérer les travaux dans Advanced eDiscovery

Voici une liste des travaux (qui sont généralement des processus de  longue durée) qui sont suivis sous l’onglet Travaux d’un cas dans Advanced eDiscovery. Ces travaux sont déclenchés par des actions de l’utilisateur lors de l’utilisation et de la gestion des cas.

| Type du travail            | Description     |
| :----------------- | :----------     |
|Ajout de données à un jeu à réviser | Un utilisateur ajoute une collection à un jeu à réviser. Ce travail se compose de deux sous-travaux : </br>• **Exporter** : une liste d’éléments de la collection est générée. </br>• **Ingestion & Indexation** : les éléments de la collection qui correspondent à la requête de recherche sont copiés à un emplacement stockage Azure (dans un processus appelé *ingestion),* puis ces éléments dans l’emplacement stockage Azure sont réindexés. Ce nouvel index est utilisé lors de l’interrogation et de l’analyse d’éléments dans le jeu de données. </br></br>Pour plus d’informations, voir [Ajouter des résultats de recherche à un jeu à réviser.](add-data-to-review-set.md) |
|Ajout de données à un autre jeu à réviser | Un utilisateur ajoute des documents d’un jeu à réviser à un autre dans le même cas. Pour plus d’informations, voir [Ajouter des données à un jeu à réviser à partir d’un autre ensemble de révision.](add-data-to-review-set-from-another-review-set.md)|
|Ajout de données non Microsoft 365 à un groupe de révision | Un utilisateur télécharge des données non Microsoft 365 dans un groupe de révision. Les données sont également indexées au cours de ce processus. Par exemple, les fichiers provenant d’un serveur de fichiers local ou d’un ordinateur client sont téléchargés vers un groupe de révision. Pour plus d’informations, voir Charger des [données non Microsoft 365 dans un jeu à réviser.](load-non-office-365-data-into-a-review-set.md)| 
|Ajout de données corrigés à un jeu à réviser | Les données avec des erreurs de traitement sont corrigés et chargés à nouveau dans un jeu à réviser. Pour plus d'informations, voir :</br>• [Correction des erreurs lors du traitement des données](error-remediation-when-processing-data-in-advanced-ediscovery.md)</br>• [Correction des erreurs d’élément unique](single-item-error-remediation.md)| 
|Comparaison des ensembles de charge | Un utilisateur examine les différences entre les différents ensembles de charge dans un jeu à réviser. Un jeux de charges est une instance qui permet d’ajouter des données à un groupe de révision. Par exemple, si vous ajoutez les résultats de deux recherches différentes au même jeu à réviser, chacune représente un ensemble de chargement. |
|Reconstruction de conversation|Lorsqu’un utilisateur ajoute les résultats d’une recherche à un groupe de révision de conversation, les conversations par message instantané (également appelées *conversations* threadées) dans des services tels que Microsoft Teams sont reconstruites dans un fichier PDF. Ce travail est également déclenché lorsqu’un utilisateur clique sur Action > créer des **PDF de conversation** dans un jeu à réviser. Pour plus d’informations, [consultez les conversations dans Advanced eDiscovery](conversation-review-sets.md).
|Conversion de documents rédigés au format PDF|Une fois qu’un utilisateur annote un document dans un jeu à réviser et en écrit une partie, il peut choisir de convertir le document rédigé en fichier PDF. Cela garantit que la partie expurgée ne sera pas visible si le document est exporté pour la présentation. Pour plus d’informations, voir [Afficher les documents dans un jeu à réviser.](annotating-and-redacting-documents.md) |
|Estimation des résultats de recherche | Après qu’un utilisateur a créé et réexécuté un brouillon de collection, l’outil de recherche recherche dans l’index les éléments qui correspondent à la requête de recherche et prépare une estimation qui inclut le nombre et la taille totale de tous les éléments par la recherche, ainsi que le nombre de sources de données faisant l’objet de la recherche.  Pour plus d’informations, voir [Collecter des données pour un cas.](collecting-data-for-ediscovery.md) | 
|Préparation des données pour l’exportation | Un utilisateur exporte des documents à partir d’un groupe de révision. Une fois le processus d’exportation terminé, ils peuvent télécharger les données exportées sur un ordinateur local. Pour plus d’informations, voir [Données de cas d’exportation.](exporting-data-ediscover20.md) | 
|Préparation de la résolution des erreurs |Lorsqu’un utilisateur sélectionne un fichier et crée une correction  d’erreur dans l’affichage Erreur sous l’onglet Traitement d’un cas, la première étape du processus consiste à télécharger le fichier qui a l’erreur de traitement vers un emplacement stockage Azure dans le cloud Microsoft. Ce travail suit la progression du processus de chargement. Pour plus d’informations sur le flux de travail de correction des erreurs, voir [Correction des erreurs lors du traitement des données.](error-remediation-when-processing-data-in-advanced-ediscovery.md) | 
|Préparation de la prévisualisation de la recherche | Une fois qu’un utilisateur a créé et lancé un nouveau brouillon de collection (ou réexécuté une collection de brouillons existante), l’outil de recherche prépare un exemple de sous-ensemble d’éléments (qui correspondent à la requête de recherche) qui peuvent être prévisualisations. L’aperçu des résultats de recherche vous permet de déterminer l’efficacité de la recherche.  Pour plus d’informations, voir [Collecter des données pour un cas.](collecting-data-for-ediscovery.md#view-search-results-and-statistics) | 
|Ré-indexation des données des dépositaires | Lorsque vous ajoutez un dépositaire à un cas, tous les éléments partiellement indexés dans les sources de données sélectionnées du dépositaire sont réindexés par un processus appelé *Indexation avancée*. Ce travail est également déclenché lorsque vous  cliquez sur Mettre à jour **l’index** sous l’onglet Traitement d’un cas et lorsque vous mettez à jour l’index d’un dépositaire spécifique dans la page volante des propriétés du dépositaire. Pour plus d’informations, voir [Indexation avancée des données des dépositaires.](indexing-custodian-data.md)
|Exécution de l’analyse | Un utilisateur analyse les données d’un jeu à réviser en exécutant des outils d’analyse Advanced eDiscovery tels que la détection de quasi-doublons, l’analyse du thread de courrier électronique et l’analyse des thèmes. Pour plus d’informations, voir [Analyser les données dans un jeu à réviser.](analyzing-data-in-review-set.md) | 
|Marquage de documents | Ce travail est déclenché lorsqu’un utilisateur clique  sur Démarrer le travail de marquage dans le panneau de marquage lors de la révision de documents dans un jeu à réviser.  Un utilisateur peut démarrer ce travail après avoir balisé des documents dans un jeu à réviser, puis les avoir sélectionnés en bloc dans le panneau d’affichage du document. Pour plus d’informations, voir [Documents de balise dans un jeu à réviser.](tagging-documents.md) | 
|||

## <a name="job-status"></a>État du travail

Le tableau suivant décrit les différents états d’état des travaux.

| État           | Description     |
| :----------------- | :----------     |
| Submitted | Un nouveau travail a été créé.  La date et l’heure d’affichage du travail sont affichées dans la colonne Créé **sous** **l’onglet Travaux.** |
| Échec de l’envoi | Échec de l’envoi du travail.  Vous devez essayer de réexécuter l’action qui a déclenché le travail. |
| En cours | Le travail est en cours, vous pouvez surveiller la progression du travail dans l’onglet **Travaux.** |
| Réussi | Le travail a été terminé. La date et l’heure de fin du travail s’affichent dans la colonne Terminé **sous** **l’onglet Travaux.** |
| Réussite partielle | Le travail a réussi. Cet état est généralement renvoyé lorsque le travail n’a trouvé aucune donnée partiellement indexée (également appelée données *non* indexées) dans certaines sources de données des dépositaires.  |
| Échec | Le travail a échoué.  Vous devez essayer de réexécuter l’action qui a déclenché le travail. Si le travail échoue une deuxième fois, nous vous recommandons de contacter le Support Microsoft et de fournir les informations de support du travail. |
|||
