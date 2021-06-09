---
title: Gérer les enquêtes judiciaires dans Microsoft 365
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
description: Utilisez les cas eDiscovery dans le Centre de sécurité & conformité dans Office 365 pour gérer l’examen juridique de votre organisation.
ms.openlocfilehash: c052daab8de33e21cccc3c638ab4995a007f60fb
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50903458"
---
# <a name="manage-legal-investigations-in-microsoft-365"></a>Gérer les enquêtes judiciaires dans Microsoft 365

Les organisations ont de nombreuses raisons de répondre à un dossier juridique impliquant certains cadres ou d’autres employés de votre organisation. Cela peut impliquer de trouver et de conserver rapidement des informations spécifiques à l’examen dans le courrier électronique, les documents, les conversations de messagerie instantanée et d’autres emplacements de contenu utilisés par les personnes dans leurs tâches de travail quotidiennes. Vous pouvez effectuer ces activités et de nombreuses autres activités similaires à l’aide des outils de cas eDiscovery dans le centre de sécurité et conformité.
  
**Vous voulez savoir comment Microsoft gère ses enquêtes eDiscovery ?** Voici un livre blanc [technique](https://go.microsoft.com/fwlink/?linkid=852161) que vous pouvez télécharger qui explique comment nous utilisons les mêmes outils de recherche et d’examen pour gérer notre flux de travail eDiscovery interne.

## <a name="manage-legal-investigations-with-ediscovery-cases"></a>Gérer les enquêtes juridiques avec des cas eDiscovery

Les cas eDiscovery vous permet de contrôler qui peut créer, consulter et gérer des cas eDiscovery dans votre organisation. Utilisez des cas pour ajouter des membres et contrôler les types d’actions qu’ils peuvent effectuer, placer en attente les emplacements de contenu pertinents pour un dossier juridique et utiliser l’outil de recherche de contenu pour rechercher dans les emplacements en attente du contenu qui peut répondre à votre cas. Ensuite, vous pouvez également exporter et télécharger ces résultats pour un examen plus approfondie par des réviseurs externes.
  
- [Gérez votre flux de travail eDiscovery](./get-started-core-ediscovery.md) en créant et en utilisant des cas eDiscovery pour chaque enquête juridique que votre organisation doit entreprendre.

- [Attribuez des autorisations eDiscovery](assign-ediscovery-permissions.md) pour contrôler qui peut créer et gérer des cas eDiscovery dans votre organisation.

- [Configurer des limites de conformité pour](set-up-compliance-boundaries.md) contrôler les emplacements de contenu utilisateur que les gestionnaires eDiscovery peuvent rechercher.

- [Recherchez du contenu](search-for-content.md) dans votre organisation.

### <a name="use-scripts-for-advanced-scenarios"></a>Utiliser des scripts pour des scénarios avancés

Comme dans la section précédente qui a répertorié des scripts pour les scénarios de recherche de contenu, nous avons également créé des scripts PowerShell du Centre de sécurité & conformité pour vous aider à gérer les cas eDiscovery.
  
- [Créez un rapport de](create-a-report-on-holds-in-ediscovery-cases.md) la découverte électronique qui contient des informations sur toutes les attentes associées aux cas eDiscovery dans votre organisation.

- [Ajoutez des boîtes aux lettres OneDrive des emplacements](use-a-script-to-add-users-to-a-hold-in-ediscovery.md) pour une liste d’utilisateurs à une boîte aux lettres eDiscovery.
  
## <a name="manage-legal-investigations-with-the-advanced-ediscovery-solution-in-microsoft-365"></a>Gérer les enquêtes juridiques avec la solution Advanced eDiscovery dans Microsoft 365

La Advanced eDiscovery solution Microsoft 365 s’appuie sur les fonctionnalités eDiscovery et d’analyse existantes dans Office 365. Cette nouvelle solution, appelée *Advanced eDiscovery,* fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter du contenu qui répond aux enquêtes internes et externes de votre organisation. Il permet également aux équipes juridiques de gérer l’ensemble du flux de travail de notification de conservation légale pour communiquer avec les dépositaires impliqués dans un cas.

Advanced eDiscovery nécessite un abonnement E5 pour Microsoft 365 ou Office 365 organisation. Pour plus d’informations sur la gestion des licences, [voir Advanced eDiscovery](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

Voici une vue d’ensemble rapide du flux de travail intégré dans Advanced eDiscovery. Pour plus d’informations, [voir Gérer Advanced eDiscovery flux de travail.](create-and-manage-advanced-ediscoveryv2-case.md#manage-the-workflow)

- [Créez un cas](create-and-manage-advanced-ediscoveryv2-case.md#create-a-case) pour commencer.

- [Gérez les dépositaires](managing-custodians.md) en les ajoutant à un cas et en plaçant une conservation légale sur le contenu de leur boîte aux lettres, OneDrive compte Microsoft Teams dont ils sont membres.

- [Gérez les communications](managing-custodian-communications.md) avec les dépositaires en automatisant le processus de notification de conservation légale.

- [Indexez les données du](processing-data-for-case.md) dépositaire et corrigez les erreurs d’indexation afin de pouvoir collecter efficacement des données pour vos enquêtes.

- [Collectez les](collecting-data-for-ediscovery.md) données d’un cas et ajoutez-les à [un groupe de révision pour](collecting-data-for-ediscovery.md#add-search-results-to-a-review-set) un examen plus approfondi.

- [Afficher des](view-documents-in-review-set.md) documents, [des données de](review-set-search.md) requête et des éléments [de](tagging-documents.md) balise dans un jeu à réviser.

- [Analysez les données de cas à](analyzing-data-in-review-set.md) l’aide d’outils d’analyse avancés.

- [Exporter les données de cas pour](exporting-data-ediscover20.md) révision par un conseiller externe.

- [Gérer les travaux de longue durée](managing-jobs-ediscovery20.md) dans Advanced eDiscovery.