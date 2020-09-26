---
title: Gérer les enquêtes juridiques dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e
ms.custom:
- seo-marvel-apr2020
description: Utilisez des cas eDiscovery dans le centre de sécurité & conformité dans Office 365 pour gérer l’enquête légale de votre organisation.
ms.openlocfilehash: edc9835cdbefa611af4c0906be5d3e1d0404c635
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285650"
---
# <a name="manage-legal-investigations-in-microsoft-365"></a>Gérer les enquêtes juridiques dans Microsoft 365

Les organisations ont de nombreuses raisons de répondre à un cas juridique impliquant certains cadres ou d’autres employés de votre organisation. Cela peut impliquer le recours à l’identification et à la conservation rapides de ces informations dans des e-mails, des documents, des conversations de messagerie instantanée et dans d’autres emplacements de contenu. Vous pouvez effectuer ces opérations et de nombreuses autres activités similaires à l’aide des outils de cas eDiscovery dans le centre de sécurité et de conformité.
  
**Vous souhaitez savoir comment Microsoft gère ses enquêtes eDiscovery ?** Voici un livre [blanc technique](https://go.microsoft.com/fwlink/?linkid=852161) que vous pouvez télécharger et qui explique comment nous utilisons les mêmes outils de recherche et d’enquête pour gérer notre flux de travail eDiscovery interne.
   
## <a name="manage-legal-investigations-with-ediscovery-cases"></a>Gérer les enquêtes juridiques avec des cas eDiscovery

les cas eDiscovery vous permettent de contrôler qui peut créer, consulter et gérer des cas eDiscovery dans votre organisation. Les cas d’utilisation permettent d’ajouter des membres et de contrôler les types d’actions qu’ils peuvent effectuer, de mettre en attente les emplacements de contenu pertinents pour un cas juridique et d’utiliser l’outil de recherche de contenu pour rechercher des contenus susceptibles de répondre à votre cas. Ensuite, vous pouvez également exporter et télécharger ces résultats pour une meilleure analyse par les relecteurs externes.
  
- [Gérer votre flux de travail eDiscovery](ediscovery-cases.md) en créant et en utilisant des cas eDiscovery pour chaque enquête légale que votre organisation doit entreprendre 
    
- [Attribuer des autorisations eDiscovery](assign-ediscovery-permissions.md) pour contrôler qui peut créer et gérer des cas eDiscovery dans votre organisation 
    
- [Configuration des limites de conformité](tagging-and-assessment-in-advanced-ediscovery.md) pour contrôler les emplacements de contenu utilisateur que les gestionnaires eDiscovery peuvent rechercher 
    
- [Rechercher du contenu](search-for-content.md) au sein de votre organisation 
    
### <a name="use-scripts-for-advanced-scenarios"></a>Utiliser des scripts pour les scénarios avancés

Comme dans la section précédente qui répertoriait les scripts pour les scénarios de recherche de contenu, nous avons également créé des scripts PowerShell du centre de sécurité & pour vous aider à gérer les cas eDiscovery.
  
- [Créer un rapport de conservation de découverte électronique](create-a-report-on-holds-in-ediscovery-cases.md) contenant des informations sur toutes les suspensions associées aux cas de découverte électronique dans votre organisation 
    
- [Ajouter des boîtes aux lettres et des emplacements OneDrive](use-a-script-to-add-users-to-a-hold-in-ediscovery.md) pour une liste d’utilisateurs à une conservation eDiscovery 
  
## <a name="manage-legal-investigations-with-the-advanced-ediscovery-solution-in-microsoft-365"></a>Gérer les enquêtes juridiques à l’aide de la solution eDiscovery avancée dans Microsoft 365

La solution eDiscovery avancée de Microsoft 365 repose sur les fonctionnalités d’analyse et de découverte électronique existantes dans Office 365. Cette nouvelle solution, appelée *Advanced eDiscovery*, fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter du contenu réactif aux investigations internes et externes de votre organisation. Il permet également aux équipes juridiques de gérer l’ensemble du flux de travail de notification de suspension légale pour communiquer avec les dépositaires impliqués dans un cas.

Advanced eDiscovery nécessite un abonnement E5 pour votre organisation Microsoft 365 ou Office 365. Pour plus d’informations sur la gestion des licences, voir [Get Started with Advanced eDiscovery](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

Voici une présentation rapide du flux de travail intégré dans Advanced eDiscovery. Pour plus d’informations, consultez [la rubrique explorer le flux de travail EDiscovery avancé](get-started-with-advanced-ediscovery.md#explore-the-advanced-ediscovery-workflow).

- [Création d’un cas](create-new-ediscovery-case.md) pour commencer

- [Gérer les dépositaires](managing-custodians.md) en les ajoutant à un cas et en plaçant un blocage légal sur le contenu de leur boîte aux lettres, du compte OneDrive et de Microsoft teams dont ils sont membres

- [Gérer les communications](managing-custodian-communications.md) avec des dépositaires en automatisant le processus de notification de conservation légale

- [Indexer les données du dépositaire](processing-data-for-case.md) et corriger les erreurs d’indexation afin de pouvoir recueillir efficacement les données de vos investigations

- [Collecter des données](collecting-data-for-ediscovery.md) pour un cas et ajouter l' [Ajouter à un jeu de révision](collecting-data-for-ediscovery.md#add-search-results-to-a-review-set) pour une nouvelle enquête

- [Afficher ](view-documents-in-review-set.md) des documents, des données de [requête](review-set-search.md) et des éléments de [balise](tagging-documents.md) dans un jeu de révision

- [Analyser les données de cas](analyzing-data-in-review-set.md) avec des outils d’analyse avancés

- [Exporter des données de cas](exporting-data-ediscover20.md) pour les consulter par des conseillers externes

- [Gérer les travaux de longue durée](managing-jobs-ediscovery20.md) dans Advanced eDiscovery
