---
title: Gérer les tâches dans Advanced eDiscovery
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
description: Advanced eDiscovery travaux vous aident à suivre l’état des processus de longue durée liés à l’exécution de différentes tâches Advanced eDiscovery.
ms.openlocfilehash: 998a59c696779cc2402e18362290e0b82dfde87d
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64758682"
---
# <a name="manage-jobs-in-advanced-ediscovery"></a>Gérer les tâches dans Advanced eDiscovery

Voici une liste des travaux (qui sont généralement des processus de longue durée) suivis sous l’onglet **Travaux** d’un cas dans Advanced eDiscovery. Ces travaux sont déclenchés par des actions de l’utilisateur lors de l’utilisation et de la gestion des cas.

|Type du travail |Description|
|---|---|
|Ajout de données à un jeu de révision|Un utilisateur ajoute une collection à un jeu de révision. Ce travail se compose de deux sous-tâches : <ul><li>**Exportation** : une liste d’éléments de la collection est générée.</li><li>**Ingestion & Indexation** : les éléments de la collection qui correspondent à la requête de recherche sont copiés vers un emplacement stockage Azure (dans un processus appelé *ingestion*), puis ces éléments de l’emplacement stockage Azure sont réindexés. Ce nouvel index est utilisé lors de l’interrogation et de l’analyse d’éléments dans le jeu de données.</li></ul> </br></br> Pour plus d’informations, consultez [Ajouter des résultats de recherche à un ensemble de révisions](add-data-to-review-set.md).|
|Ajout de données à un autre jeu de révision|Un utilisateur ajoute des documents d’un ensemble de révisions à un autre ensemble de révisions dans le même cas. Pour plus d’informations, consultez [Ajouter des données à un jeu de révision à partir d’un autre ensemble de révisions](add-data-to-review-set-from-another-review-set.md).|
|Ajout de données non Microsoft 365 à un jeu de révision|Un utilisateur charge des données non Microsoft 365 dans un ensemble de révisions. Les données sont également indexées pendant ce processus. Par exemple, les fichiers d’un serveur de fichiers local ou d’un ordinateur client sont chargés dans un ensemble de révisions. Pour plus d’informations, consultez [Charger des données non Microsoft 365 dans un ensemble de révisions](load-non-office-365-data-into-a-review-set.md).|
|Ajout de données corrigées à un jeu de révision|Les données avec des erreurs de traitement sont corrigées et chargées dans un jeu de révisions. Pour plus d’informations, reportez-vous aux rubriques suivantes : <ul><li>[Correction d’erreur lors du traitement des données](error-remediation-when-processing-data-in-advanced-ediscovery.md)</li><li>[Correction d’erreur sur élément unique](single-item-error-remediation.md)</li></ul>|
|Comparaison des jeux de charge|Un utilisateur examine les différences entre les différents jeux de charge dans un jeu de révision. Un jeux de charges est une instance qui permet d’ajouter des données à un groupe de révision. Par exemple, si vous ajoutez les résultats de deux recherches différentes au même ensemble de révisions, chacune représenterait un jeu de charge.|
|Reconstruction de conversation|Lorsqu’un utilisateur ajoute les résultats d’une recherche à un ensemble de révisions de conversation, les conversations par message instantané (également appelées *conversations thread*) dans des services tels que Microsoft Teams sont reconstruites dans un fichier PDF. Ce travail est également déclenché lorsqu’un utilisateur clique sur **Action > Créer des fichiers PDF de conversation** dans un jeu de révision. Pour plus d’informations, consultez [Examiner les conversations dans Advanced eDiscovery](conversation-review-sets.md).
|Conversion de documents redéposés au format PDF|Une fois qu’un utilisateur a annoté un document dans un ensemble de révisions et en a rédigé une partie, il peut choisir de convertir le document expurgé en fichier PDF. Cela garantit que la partie expurgée ne sera pas visible si le document est exporté pour présentation. Pour plus d’informations, consultez [Afficher les documents dans un ensemble de révisions](view-documents-in-review-set.md).|
|Estimation des résultats de la recherche|Une fois qu’un utilisateur a créé et exécuté ou réexécuté un brouillon de collection, l’outil de recherche recherche dans l’index les éléments correspondant à la requête de recherche et prépare une estimation qui inclut le nombre et la taille totale de tous les éléments par la recherche, ainsi que le nombre de sources de données recherchées.  Pour plus d’informations, consultez [Collecter des données pour un cas](collecting-data-for-ediscovery.md).|
|Préparation des données pour l’exportation|Un utilisateur exporte des documents à partir d’un ensemble de révisions. Une fois le processus d’exportation terminé, ils peuvent télécharger les données exportées sur un ordinateur local. Pour plus d’informations, consultez [Exporter les données de cas](exporting-data-ediscover20.md).|
|Préparation de la résolution des erreurs|Lorsqu’un utilisateur sélectionne un fichier et crée une correction d’erreur dans l’affichage Erreur sous l’onglet **Traitement** d’un cas, la première étape du processus consiste à charger le fichier qui contient l’erreur de traitement à un emplacement stockage Azure dans le cloud Microsoft. Ce travail suit la progression du processus de chargement. Pour plus d’informations sur le flux de travail de correction des erreurs, consultez [Correction d’erreur lors du traitement des données](error-remediation-when-processing-data-in-advanced-ediscovery.md).|
|Préparation de la préversion de la recherche|Une fois qu’un utilisateur a créé et exécuté un nouveau brouillon de collection (ou réexécuté une collection de brouillons existante), l’outil de recherche prépare un exemple de sous-ensemble d’éléments (qui correspondent à la requête de recherche) qui peuvent être prévisualisables. L’aperçu des résultats de la recherche vous aide à déterminer l’efficacité de la recherche.  Pour plus d’informations, consultez [Collecter des données pour un cas](collecting-data-for-ediscovery.md#view-search-results-and-statistics).|
|Réindexation des données des consignats|Lorsque vous ajoutez un dépositaire à un cas, tous les éléments partiellement indexés dans les sources de données sélectionnées du consignateur sont réindexés par un processus appelé *indexation avancée*. Ce travail est également déclenché lorsque vous cliquez sur **Mettre à jour l’index** sous l’onglet **Traitement** d’un cas, et lorsque vous mettez à jour l’index d’un consignateur spécifique dans la page de menu volant des propriétés du consignateur. Pour plus d’informations, consultez [Indexation avancée des données de consignation](indexing-custodian-data.md).
|Exécution de l’analytique|Un utilisateur analyse les données d’un ensemble de révisions en exécutant Advanced eDiscovery outils d’analytique tels que la détection des doublons proches, l’analyse du thread d’e-mail et l’analyse des thèmes. Pour plus d’informations, consultez [Analyser les données dans un ensemble de révisions](analyzing-data-in-review-set.md).|
|Balisage des documents|Ce travail est déclenché lorsqu’un utilisateur clique sur **Démarrer le balisage** dans le **panneau d’étiquetage** lors de l’examen des documents dans un ensemble de révisions. Un utilisateur peut démarrer ce travail après avoir marqué des documents dans un ensemble de révisions, puis les sélectionner en bloc dans le panneau de document d’affichage. Pour plus d’informations, consultez [Les documents de balise dans un ensemble de révisions](tagging-documents.md).|

## <a name="job-status"></a>État du travail

Le tableau suivant décrit les différents états d’état des travaux.

|État|Description|
|---|---|
|Submitted|Un nouveau travail a été créé.  La date et l’heure d’envoi du travail s’affichent dans la colonne **Créé** sous l’onglet **Travaux** .|
|Échec de l’envoi|Échec de la soumission du travail.  Vous devez tenter de réexécuter l’action qui a déclenché le travail.|
|En cours|Le travail est en cours. Vous pouvez surveiller la progression du travail sous l’onglet **Travaux** .|
|Réussi|Le travail a été terminé avec succès. La date et l’heure de fin du travail s’affichent dans la colonne **Terminé** sous l’onglet **Travaux** .|
|Partiellement réussie|Le travail a réussi. Cet état est généralement retourné lorsque le travail n’a trouvé aucune donnée partiellement indexée (également appelée *données non indexées*) dans certaines sources de données de conservation.|
|Échec|Le travail a échoué.  Vous devez tenter de réexécuter l’action qui a déclenché le travail. Si le travail échoue une deuxième fois, nous vous recommandons de contacter Support Microsoft et de fournir les informations de support du travail.|
