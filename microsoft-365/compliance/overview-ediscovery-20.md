---
title: Vue d’ensemble de la solution Advanced eDiscovery dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- m365-security-compliance
- m365solution-ediscovery
- m365initiative-compliance
- m365solution-overview
search.appverid:
- MOE150
- MET150
description: Découvrez la solution Advanced eDiscovery dans Microsoft 365. Cet article fournit une vue d’ensemble d’Advanced eDiscovery dans Microsoft 365, un outil qui vous aide à gérer les enquêtes internes et externes. Il encadre également les raisons professionnelles de l’utilisation d’Advanced eDiscovery pour gérer vos enquêtes juridiques.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 80a1505bf19beb954c0746efb7fb29f99d6a916b
ms.sourcegitcommit: 8f1721de52dbe3a12c11a0fa5ed0ef5972ca8196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2021
ms.locfileid: "50838222"
---
# <a name="overview-of-microsoft-365-advanced-ediscovery"></a>Vue d’ensemble de Microsoft 365 Advanced eDiscovery

La solution Advanced eDiscovery dans Microsoft 365 s’appuie sur les fonctionnalités eDiscovery et d’analyse de Microsoft existantes. Advanced eDiscovery fournit un flux de travail de bout en bout pour conserver, collecter, analyser, examiner, analyser et exporter du contenu qui répond aux enquêtes internes et externes de votre organisation. Il permet également aux équipes juridiques de gérer l’ensemble du flux de travail de notification de conservation légale pour communiquer avec les dépositaires impliqués dans un cas.

Advanced eDiscovery peut aider votre organisation à répondre à des questions juridiques ou à des enquêtes internes en découvrant les données où elle se trouve. Vous pouvez gérer en toute transparence les flux de travail eDiscovery en identifiant les personnes d’intérêt et leurs sources de données, en appliquant en toute transparence des conservations pour conserver les données, puis en gérant le processus de communication de conservation légale. En collectant des données à partir de la source, vous pouvez effectuer des recherches sur la plateforme Microsoft 365 en direct pour trouver rapidement ce dont vous avez besoin. Les fonctionnalités intelligentes d’apprentissage automatique telles que l’indexation approfondie, le thread de courrier électronique et la détection de quasi-doublons vous aident également à réduire les volumes importants de données dans un jeu de données pertinent.

Les sections suivantes décrivent comment ces fonctionnalités Advanced eDiscovery peuvent aider votre organisation.

## <a name="discover-and-collect-data-in-place"></a>Découvrir et collecter des données sur place

En général, les organisations qui s’appuient sur plusieurs solutions eDiscovery tierces nécessitent la copie de grands volumes de données de Microsoft 365 pour traiter et avoir à héberger des données en double. Cette nécessité augmente le temps nécessaire pour trouver des données pertinentes, ainsi que les risques, les coûts et la complexité de la gestion de plusieurs solutions.

Advanced eDiscovery dans Microsoft 365 vous permet de découvrir les données à la source et de rester dans vos limites de sécurité et de conformité Microsoft 365.  En collectant des données sur place à partir du système en direct, Advanced eDiscovery réduit la friction de revenir à la source et réduit le travail inutile d’avoir à trouver le contenu manquant, ce qui se produit souvent lorsque la journaling est en retard dans les solutions eDiscovery traditionnelles.

Les fonctionnalités de recherche et de collecte natives pour les données dans Teams, Yammer, SharePoint Online, OneDrive Entreprise et Exchange Online améliorent davantage la découverte des données. Par exemple, Advanced eDiscovery :

- Reconstruit les conversations Teams (au lieu de renvoyer des messages individuels à partir de conversations).

- Collecte le contenu basé sur le cloud partagé avec les utilisateurs à l’utilisation de liens ou de pièces jointes modernes dans les messages électroniques et les conversations Teams.

- Offre une prise en charge intégrée de centaines de types de fichiers non-Microsoft 365.

- Collecte des données à partir de sources tierces (comme Bloomberg, Facebook, Slack et Zoom Meetings) importées et archivées dans Microsoft 365 par des connecteurs de [données.](archiving-third-party-data.md)

## <a name="manage-ediscovery-workflow-in-one-platform"></a>Gérer le flux de travail eDiscovery dans une plateforme

Advanced eDiscovery peut vous aider à réduire le nombre de solutions eDiscovery dont vous avez besoin. Il fournit un flux de travail simplifié de bout en bout, qui se produit tous dans Microsoft 365. Advanced eDiscovery permet de réduire les points de friction entre l’identification et la collecte des sources potentielles d’informations pertinentes en m mappage automatique des sources de données uniques et partagées avec la personne d’intérêt (appelée *dépositaire),* et en fournissant des rapports et des analyses sur les données potentiellement pertinentes avant de les collecter pour analyse et révision.

En outre, les API Microsoft Graph peuvent vous aider à automatiser le flux de travail eDiscovery et à étendre Advanced eDiscovery pour les solutions personnalisées.

## <a name="cull-data-intelligently"></a>Annuler les données de manière intelligente

Les fonctionnalités intelligentes d’apprentissage automatique dans Advanced eDiscovery vous aident à réduire la quantité de données à réviser. Ces fonctionnalités intelligentes vous aident à réduire et à réduire les volumes de données importants vers un ensemble pertinent. Par exemple, une requête d’ensemble de révision intégrée permet de filtrer uniquement le contenu unique en identifiant les quasi-doublons. Cette fonctionnalité peut considérablement réduire la quantité de données à réviser.

D’autres fonctionnalités d’apprentissage automatique peuvent affiner et identifier les données pertinentes à l’aide de balises intelligentes et d’outils d’examen avec assistance technologique tels que les modules de pertinence.

## <a name="advanced-ediscovery-architecture"></a>Architecture eDiscovery avancée

Voici un diagramme d’architecture Advanced eDiscovery qui montre le flux de travail de bout en bout dans un environnement à une seule géo [](advanced-ediscovery-edrm.md) et dans un environnement multigéo, ainsi que le flux de données de bout en bout aligné sur le modèle de référence de découverte électronique (EDRM).

[![Affiche de modèle : Architecture eDiscovery avancée dans Microsoft 365](../media/solutions-architecture-center/ediscovery-poster-thumb.png)](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Afficher en tant qu’image](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Télécharger en tant que fichier PDF](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.pdf)

[Télécharger en tant que fichier Visio](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.vsdx)

Pour plus d’informations sur le flux de travail de bout en bout dans Advanced eDiscovery, voir cette [vidéo microsoft Mechanics](https://go.microsoft.com/fwlink/?linkid=2066133).

## <a name="advanced-ediscovery-workflow"></a>Flux de travail eDiscovery avancé

Les sections suivantes décrivent chaque étape du flux de travail intégré dans l’outil Advanced eDiscovery du Centre de conformité Microsoft 365. La capture d’écran suivante montre l’onglet Vue d’ensemble d’un cas nommé *2020.11.03 - Contoso v. Fabrikam*. 

![Onglets dans le flux de travail advanced eDiscovery intégré](../media/AeD-Case-Screenshot1.png)

Pour plus d’informations, voir Gérer le flux de [travail Advanced eDiscovery.](create-and-manage-advanced-ediscoveryv2-case.md#manage-the-workflow)

### <a name="managing-custodians-and-non-custodial-data-sources"></a>Gestion des dépositaires et des sources de données non privatives

Utilisez l’onglet **Sources** de données pour ajouter et gérer les personnes que vous avez identifiées comme des personnes d’intérêt dans le cas et d’autres sources de données qui peuvent ne pas être associées à un dépositaire. Lorsque vous ajoutez des dépositaires ou des sources de données non privatives, vous pouvez rapidement effectuer des actions telles que le placement d’une conservation légale sur des sources de données de dépositaire et de non-conservation, la communication avec les dépositaires et la recherche de sources de données non privatives pour collecter du contenu pertinent pour le cas. Au fur et à mesure de l’avancement du cas, il est facile d’ajouter de nouveaux dépositaires ou de nouvelles sources de date sans conservation ou de les libérer du cas. Pour plus d’informations, [voir Travailler avec les dépositaires.](managing-custodians.md)

### <a name="managing-legal-hold-notifications"></a>Gestion des notifications de mise en attente légale

Utilisez **l’onglet Communications** pour gérer le processus de communication avec les dépositaires dans le cas. Une notification de conservation légale demande aux dépositaires de conserver tout contenu pertinent pour le cas. Les équipes juridiques doivent pouvoir suivre les notifications reçues, lues et reconnues par les dépositaires. Le flux de travail de communications dans Advanced eDiscovery vous permet de créer et d’envoyer des notifications initiales, des rappels, des notifications de publication et des escalades si les dépositaires ne reconnaissent pas une notification de conservation. Pour plus d’informations, voir [Travailler avec les communications.](managing-custodian-communications.md)

### <a name="managing-content-preservation"></a>Gestion de la conservation du contenu

Lorsque vous ajoutez un dépositaire à un cas, vous pouvez placer des données en conservation. Utilisez **l’onglet** Conservation pour gérer la conservation créée lorsque vous ajoutez des dépositaires et pour gérer d’autres conservations légales associées au cas . Par exemple, vous pouvez identifier et placer une mise en attente sur des sources de données non privatives. Vous pouvez également modifier n’importe quelle conservation dans le cas et en faire une conservation basée sur une requête pour conserver uniquement le contenu qui correspond à la requête. Par exemple, vous pouvez ajouter une plage de dates à la conservation afin que seul le contenu créé dans une plage de dates spécifique soit conservé. Vous pouvez également obtenir des statistiques sur le contenu en attente, supprimer la attente une fois qu’elle n’est plus pertinente pour le cas ou la supprimer. Pour plus d’informations, voir [Gérer les prises en charge.](managing-holds.md)

### <a name="indexing-custodian-data"></a>Indexation des données des dépositaires

Lorsque vous ajoutez un dépositaire et les sources de données correspondantes à un cas, tout élément partiellement indexé à partir d’une source de données de dépositaire est réindexé par un processus appelé *Indexation avancée*. Cela permet d’effectuer une recherche complète de contenu tel que des images, des types de fichiers non pris en compte et d’autres contenus potentiellement nonndex lorsque vous exécutez des recherches pour collecter des données pour le cas. Utilisez **l’onglet Traitement** pour surveiller l’état de l’indexation avancée et corriger les erreurs de traitement à l’aide d’un processus appelé *correction des erreurs.* Pour plus d’informations, voir [Corriger les erreurs de traitement.](processing-data-for-case.md)

### <a name="collecting-case-data"></a>Collecte des données d’un cas

Utilisez **l’onglet Collections** pour créer des recherches eDiscovery afin de rechercher dans les sources de données privées et non privées sur place le contenu pertinent pour le cas. Vous pouvez créer et exécuter des collections basées sur des requêtes (à l’aide de mots clés et de conditions) pour identifier un ensemble de messages électroniques et de documents pertinents pour le cas et que vous souhaitez examiner et analyser plus en détail dans les étapes suivantes du flux de travail eDiscovery. Vous pouvez créer une ou plusieurs collections associées au cas. Vous pouvez également utiliser l’outil de collecte pour afficher un aperçu des exemples de documents et afficher les statistiques de recherche pour vous aider à affiner et à améliorer les résultats de la recherche. Une fois que vous êtes satisfait que les résultats de la collection contiennent les données pertinentes pour le cas, vous pouvez valider la collection dans un jeu à réviser pour une révision, une analyse et une élimination plus approfondies. Pour plus d’informations, voir [Collecter des données pour un cas.](collecting-data-for-ediscovery.md)

### <a name="reviewing-and-analyzing-case-data"></a>Examen et analyse des données de cas

Utilisez **l’onglet Ensembles** de révision pour examiner et analyser le contenu que vous avez collecté à partir du système en direct et ajouté à un jeu à réviser. Un  ensemble de révision est une collection statique de ces données (en d’autres termes, une copie hors connexion des données) des données privées (et, le cas échéant, les données non privées) que vous avez collectées lors de la phase précédente du flux de travail eDiscovery. Lorsque vous ajoutez des résultats de recherche à un jeu à réviser, un processus est déclenché pour extraire des fichiers à partir de conteneurs, extraire des métadonnées et extraire du texte. Une fois ce processus terminé, le système crée un nouvel index de toutes les données collectées auprès des dépositaires et l’ajoute au jeu à réviser. Une fois que les données sont ajoutées au jeu à réviser, vous pouvez exécuter d’autres requêtes pour affiner les données de cas, afficher les données sous forme de texte ou dans le format de fichier natif, et annoter, créer des articles et baliser des documents dans le jeu à réviser. Vous pouvez également effectuer des analyses avancées, telles que l’identification de la duplication des documents, du thread de messagerie électronique et des thèmes. Une fois que vous avez n’avez fait que ce qui est pertinent pour le cas, vous pouvez télécharger des documents directement ou les exporter avec les métadonnées de fichier, les annotations et toutes les balises. Pour plus d’informations, consultez :

- [Afficher les documents d’un jeu à réviser](view-documents-in-review-set.md)

- [Interroger les données d’un jeu à réviser](review-set-search.md)

- [Étiqueter les documents d’un jeu à réviser](tagging-documents.md)

- [Analyser des données dans un jeu à réviser](analyzing-data-in-review-set.md)

### <a name="exporting-data-for-review-and-presentation"></a>Exportation de données pour révision et présentation

Après avoir exporté les données d’un jeu à réviser, utilisez l’onglet Exportation **pour** gérer une tâche d’exportation et télécharger les données à partir d’un ensemble de révision. Lorsque vous exportez un groupe de révision, les données sont téléchargées vers un emplacement de stockage Azure fourni par Microsoft (ou un emplacement de stockage Azure géré par votre organisation). Une fois téléchargé vers Azure, il est ensuite disponible sur un ordinateur local. Vous pouvez obtenir la clé d’évaluation du stockage nécessaire pour télécharger les données exportées sous **l’onglet Exportation.** Pour plus d’informations, voir [Données de cas d’exportation.](exporting-data-ediscover20.md)

### <a name="managing-jobs"></a>Gestion des travaux

Utilisez **l’onglet Travaux** pour surveiller les processus de longue durée pour les tâches liées à la cas que vous avez initiées. Les travaux liés à la réindexation, à la recherche et à l’exportation de données de cas sont des exemples de travaux. Par exemple, si vous créez une recherche sous l’onglet **Recherches** qui inclut de nombreuses sources de données, l’état de ce processus de recherche s’affiche sous l’onglet **Travaux.** Pour plus d’informations, voir [Gérer les travaux.](managing-jobs-ediscovery20.md)

### <a name="configuring-case-settings"></a>Configuration des paramètres de cas

Utilisez **l’onglet Paramètres** pour configurer les paramètres à l’échelle de la cas. Cela inclut l’ajout de membres à un cas, la fermeture ou la suppression d’un cas, ainsi que la configuration des paramètres de recherche et d’analyse. Pour plus d’informations, consultez :

- [Ajouter des membres à un cas](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

- [Fermer ou supprimer un cas](close-or-delete-case.md)

- [Configurer les paramètres de recherche et d’analyse](configure-search-and-analytics-settings-in-advanced-ediscovery.md)
