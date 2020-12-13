---
title: Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: fd53438a-a760-45f6-9df4-861b50161ae4
description: Découvrez comment Advanced eDiscovery peut vous aider à analyser les données, rationaliser les révisions de documents et prendre des décisions pour une découverte électronique efficace.
ms.openlocfilehash: f8ada5d377e72516ea42d8c5dc5680573daec717
ms.sourcegitcommit: 47de4402174c263ae8d70c910ca068a7581d04ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "49662819"
---
# <a name="advanced-ediscovery-classic"></a>Advanced eDiscovery (classique)

> [!IMPORTANT]
> **Advanced eDiscovery (classique) sera définitivement supprimée le 31 décembre 2020.**<br/>
> À mesure que nous continuons à investir dans les versions plus récentes de la découverte électronique avancée, nous annonçaons le retrait et la suppression permanents des cas et des données de cas de la découverte électronique avancée (classique).
> Si vous utilisez toujours Advanced eDiscovery (Classic), également appelé *Advanced eDiscovery v 1.0*, effectuez une transition vers [Advanced eDiscovery v 2.0](overview-ediscovery-20.md) (également appelée *solution eDiscovery avancée dans Microsoft 365*) dès que possible.  En vue de la suppression de tous les cas et données de cas, vous pouvez archiver les données de cas en [exportant les données à partir d’un cas](https://docs.microsoft.com/microsoft-365/compliance/export-results-in-advanced-ediscovery?view=o365-worldwide).
> Advanced eDiscovery v 2.0 contient des fonctionnalités similaires dans Advanced eDiscovery v 1.0, mais offre également de nombreuses nouvelles fonctionnalités telles que la gestion des dépositaires, la gestion des communications et les ensembles de révision. Pour en savoir plus sur les phases Retirment précédentes de Advanced eDiscovery v 1.0, consultez la rubrique [déclassement des outils eDiscovery hérités](legacy-ediscovery-retirement.md#advanced-ediscovery-v10).

Grâce à Advanced eDiscovery, vous pouvez mieux comprendre vos données et réduire les coûts de découverte électronique. Advanced eDiscovery vous permet d’analyser les données non structurées, d’effectuer une révision des documents plus efficace et de prendre des décisions pour réduire les données de découverte électronique. Vous pouvez utiliser des données stockées dans Exchange Online, SharePoint Online, OneDrive entreprise, Skype entreprise, groupes Microsoft 365 et Microsoft Teams. Vous pouvez effectuer une recherche de découverte électronique dans le centre de sécurité et de conformité pour rechercher du contenu dans des groupes, des boîtes aux lettres et des sites individuels, puis analyser les résultats de la recherche avec Advanced eDiscovery. Lorsque vous préparez des résultats de recherche pour analyse dans Advanced eDiscovery, la reconnaissance optique de caractères permet l’extraction de texte à partir d’images. Cette fonctionnalité permet d’appliquer les puissantes fonctionnalités d’analyse du texte d’Advanced eDiscovery à des fichiers image.
  
Advanced eDiscovery rationalise et accélère le processus de révision des documents en identifiant les informations redondantes avec des fonctionnalités telles que la détection des doublons et l’analyse des threads de messagerie. La fonctionnalité de pertinence applique une technologie de codage prédictive pour identifier les documents pertinents. Advanced eDiscovery apprend vos décisions de marquage sur des exemples de documents et applique des techniques statistiques et d’auto-apprentissage pour calculer la pertinence de chaque document dans l’ensemble de données. Cela vous permet de vous concentrer sur des documents clés, de prendre des décisions rapides mais éclairées sur la stratégie de cas, de sélection de données et de hiérarchiser la révision.
  
 **Pourquoi eDiscovery avancée ?** Advanced eDiscovery repose sur l’ensemble existant de fonctionnalités eDiscovery dans Office 365. Par exemple, vous pouvez utiliser la fonctionnalité de recherche dans le &amp; Centre de sécurité conformité pour effectuer une recherche initiale de toutes les sources de contenu de votre organisation afin d’identifier et de collecter les données susceptibles de concerner un cas juridique spécifique. Vous pouvez ensuite effectuer des analyses sur ces données en appliquant l’analyse de texte, l’apprentissage automatique, ainsi que les fonctionnalités de codage de pertinence/prédictive de Advanced eDiscovery. Cela peut aider votre organisation à traiter rapidement des milliers de messages électroniques, de documents et d’autres types de données pour trouver les éléments les plus pertinents pour un 
 
> [!NOTE]
> Advanced eDiscovery nécessite un abonnement Office 365 E3 avec le complément de conformité avancé ou un abonnement E5 pour votre organisation. Si vous ne disposez pas de ce plan et que vous souhaitez essayer Advanced eDiscovery, vous pouvez vous [inscrire pour obtenir une version d’évaluation d’Office 365 entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279). boitier. Le jeu de données réduit peut ensuite être exporté absent (e) du Bureau à partir d’Office 365 pour être révisé. 
  
## <a name="get-started"></a>Prise en main

Le moyen le plus rapide de commencer à utiliser Advanced eDiscovery est de créer un incident et de préparer les résultats de la recherche dans Security & Centre de conformité, de charger ces résultats dans Advanced eDiscovery, puis d’exécuter l’analyse rapide pour analyser les données de cas, puis d’exporter les résultats pour une révision externe.
  
- [Obtenir une vue d’ensemble rapide](quick-setup-for-advanced-ediscovery.md) du flux de travail eDiscovery avancé 
    
- [Configurer des utilisateurs et des cas](set-up-users-and-cases-in-advanced-ediscovery.md) pour Advanced eDiscovery en créant un cas, en affectant des autorisations eDiscovery et en ajoutant des membres de cas, tout à l’aide du centre de sécurité & conformité 
    
- [Préparer et charger les données de recherche](prepare-data-for-advanced-ediscovery.md) dans le cas d’Advanced eDiscovery 
    
- [Charger les données non-Office 365](import-non-office-365-data-into-advanced-ediscovery.md) dans un cas pour les analyser dans Advanced eDiscovery 
    
- [Utiliser l’analyse rapide](use-express-analysis-in-advanced-ediscovery.md) pour analyser rapidement les données dans un cas, puis exporter facilement les résultats 
    
## <a name="analyze-data"></a>Analyser les données

Une fois que les données de recherche sont chargées dans le cas dans Advanced eDiscovery, vous utiliserez le module analyze pour commencer l’analyse. La première partie du processus d’analyse consiste à organiser des fichiers dans des groupes de fichiers uniques, des doublons et des doublons (également connus sous le titre de similitudes de documents). Ensuite, vous réorganisez les données dans des groupes hiérarchiques de threads et de thèmes de messagerie et, éventuellement, définissez ignorer les filtres de texte pour exclure certains textes de l’analyse. Ensuite, vous exécutez l’analyse et affichez les résultats.
  
- [En savoir plus sur la similarité des documents](understand-document-similarity-in-advanced-ediscovery.md) pour vous préparer à l’analyse des données dans Advanced eDiscovery 
    
- [Configurez les options](set-analyze-options-in-advanced-ediscovery.md) pour les doublons, les thèmes et le thread électronique, puis exécutez le module Analyze. 
    
- [Configurez ignorer les filtres de texte](set-ignore-text-in-advanced-ediscovery.md) pour exclure le texte et les chaînes de texte de l’analyse ; ces filtres ignoreront également le texte lorsque vous exécuterez l’analyse de pertinence. 
    
- [Afficher les résultats](view-analyze-results-in-advanced-ediscovery.md) du processus d’analyse 
    
- [Configurer les paramètres avancés](set-analyze-advanced-settings-in-advanced-ediscovery.md) pour le processus d’analyse 
    
## <a name="set-up-relevance-training"></a>Configuration de l’entraînement de pertinence

Le codage prédictif (appelé pertinence) dans Advanced eDiscovery vous permet de former le système sur ce que vous recherchez en vous permettant de prendre des décisions (indiquant si un élément est pertinent ou non) sur un petit ensemble de documents.
  
- [En savoir plus sur la configuration de la formation pertinente](manage-relevance-setup-in-advanced-ediscovery.md) , le marquage des fichiers pertinents pour un cas et la définition des problèmes liés aux incidents 
    
- [Définition des problèmes de cas](define-issues-and-assign-users.md) et affectation de chaque problème à un utilisateur qui lancera les fichiers 
    
- [Ajouter des fichiers importés à la charge actuelle ou nouvelle](set-up-loads-to-add-imported-files.md) qui sera ajoutée à la formation pertinence. Une charge est un nouveau lot de fichiers qui sont ajoutés à un cas, puis utilisés pour une formation pertinente. 
    
- [Définir les mots clés en surbrillance](define-highlighted-keywords-and-advanced-options.md) qui peuvent être ajoutés à la formation pertinence. Cela vous permet d’identifier plus facilement les fichiers qui sont pertinents pour un cas 
    
## <a name="run-the-relevance-module"></a>Exécuter le module de pertinence

Après avoir configuré la formation, vous êtes prêt à exécuter le module de pertinence et à évaluer l’efficacité des paramètres de formation. Il en résulte un classement de pertinence qui vous permet de déterminer si vous devez effectuer des formations supplémentaires ou si vous êtes prêt à commencer à marquer des fichiers comme il convient à votre cas.
  
- [En savoir plus sur le processus de pertinence](use-relevance-in-advanced-ediscovery.md) et le processus itératif d’évaluation, de marquage, de suivi et de recyclage en fonction de l’ensemble d’exemples de fichiers 
    
- [En savoir plus sur l’évaluation](assessment-in-relevance-in-advanced-ediscovery.md) , lorsqu’un expert connaissant le cas révise un ensemble de fichiers de cas et détermine l’efficacité de la formation à la pertinence 
    
- [Evaluez les fichiers de cas](tagging-and-assessment-in-advanced-ediscovery.md) pour calculer l’efficacité (appelée richesse) des paramètres de formation, puis baliser les fichiers comme pertinents ou non pertinents pour votre cas. Cela vous aide à déterminer si la formation actuelle est suffisante ou si vous devez ajuster les paramètres de formation. 
    
- [Effectuer la formation à la pertinence](tagging-and-relevance-training-in-advanced-ediscovery.md) une fois l’évaluation terminée, puis une nouvelle fois sur les fichiers comme pertinents ou non pertinents pour les problèmes que vous avez définis pour le cas 
    
- [Suivre le](track-relevance-analysis-in-advanced-ediscovery.md) processus d’analyse de pertinence afin de déterminer si la formation à la pertinence a atteint votre objectif d’évaluation (appelé « état de formation ») ou si une formation supplémentaire est nécessaire ; vous pouvez également afficher les résultats de pertinence pour chaque problème de cas 
    
- [Prendre des décisions en fonction de l’analyse de pertinence](decision-based-on-the-results-in-advanced-ediscovery.md) pour déterminer la taille des fichiers de cas résultants pouvant être exportés à des fins de révision 
    
- [Tester la qualité de l’analyse de pertinence](test-relevance-analysis-in-advanced-ediscovery.md) afin de valider les décisions de Culling prises lors du processus de pertinence 
    
## <a name="export-results"></a>Exporter les résultats

La dernière étape de l’analyse des données de cas dans Advanced eDiscovery consiste à exporter les résultats de l’analyse pour la révision externe.
  
- [En savoir plus sur l’exportation de données de cas](export-case-data-in-advanced-ediscovery.md)
    
- [Exporter les données de cas](export-results-in-advanced-ediscovery.md)
    
- [Affichage de l’historique du lot et exportation des résultats antérieurs](view-batch-history-and-export-past-results.md)
    
- [Exportation des champs d’un rapport](export-report-fields-in-advanced-ediscovery.md)
    
## <a name="other-advanced-ediscovery-tools"></a>Autres outils eDiscovery avancés

Advanced eDiscovery offre des outils et des fonctionnalités supplémentaires au-delà de l’analyse des données de cas, de l’analyse de pertinence et de l’exportation de données.
  
- [Exécuter des rapports eDiscovery avancés](run-reports-in-advanced-ediscovery.md)
    
- [Définir les paramètres de cas et de client](define-case-and-tenant-settings-in-advanced-ediscovery.md)
    
- [Utilitaires eDiscovery avancés](use-advanced-ediscovery-utilities.md)
