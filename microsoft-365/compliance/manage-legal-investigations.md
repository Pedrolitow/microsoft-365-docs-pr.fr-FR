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
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e
ms.custom:
- seo-marvel-apr2020
description: Utilisez des cas eDiscovery dans le portail de conformité Microsoft Purview pour gérer l’enquête juridique de votre organisation.
ms.openlocfilehash: 28dead35cce2102cfd826fa1505cdd620e4a1b25
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64999781"
---
# <a name="manage-legal-investigations-in-microsoft-365"></a>Gérer les enquêtes judiciaires dans Microsoft 365

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Les organisations ont de nombreuses raisons de répondre à une affaire juridique impliquant certains cadres ou d’autres employés de votre organisation. Cela peut impliquer la recherche et la conservation rapides d’informations spécifiques à l’investigation dans la messagerie, les documents, les conversations par messagerie instantanée et d’autres emplacements de contenu utilisés par les personnes dans leurs tâches quotidiennes. Vous pouvez effectuer ces activités et de nombreuses autres activités similaires à l’aide des outils de cas eDiscovery dans le centre de sécurité et de conformité.
  
**Vous voulez savoir comment Microsoft gère ses investigations eDiscovery ?** Voici un [livre blanc technique](https://go.microsoft.com/fwlink/?linkid=852161) que vous pouvez télécharger qui explique comment nous utilisons les mêmes outils de recherche et d’investigation pour gérer notre flux de travail eDiscovery interne.

## <a name="manage-legal-investigations-with-ediscovery-cases"></a>Gérer les enquêtes juridiques avec les cas eDiscovery

Les cas eDiscovery vous permettent de contrôler qui peut créer, accéder et gérer des cas eDiscovery dans votre organisation. Utilisez des cas pour ajouter des membres et contrôler les types d’actions qu’ils peuvent effectuer, placer une conservation sur les emplacements de contenu pertinents pour une affaire juridique et utiliser l’outil Recherche de contenu pour rechercher dans les emplacements en attente du contenu susceptible de répondre à votre cas. Ensuite, vous pouvez également exporter et télécharger ces résultats pour une investigation plus approfondie par des réviseurs externes.
  
- [Gérez votre flux de travail eDiscovery](./get-started-core-ediscovery.md) en créant et en utilisant des cas eDiscovery pour chaque enquête juridique que votre organisation doit entreprendre.

- [Attribuez des autorisations eDiscovery](assign-ediscovery-permissions.md) pour contrôler qui peut créer et gérer des cas eDiscovery dans votre organisation.

- [Configurez les limites de conformité](set-up-compliance-boundaries.md) pour contrôler les emplacements de contenu utilisateur que les gestionnaires eDiscovery peuvent rechercher.

- [Recherchez du contenu](search-for-content.md) dans votre organisation.

### <a name="use-scripts-for-advanced-scenarios"></a>Utiliser des scripts pour des scénarios avancés

Comme dans la section précédente qui répertorie les scripts pour les scénarios de recherche de contenu, nous avons également créé des scripts PowerShell security & Compliance Center pour vous aider à gérer les cas eDiscovery.
  
- [Créez un rapport de conservation eDiscovery](create-a-report-on-holds-in-ediscovery-cases.md) qui contient des informations sur toutes les conservations associées aux cas eDiscovery dans votre organisation.

- [Ajoutez des boîtes aux lettres et des emplacements OneDrive](use-a-script-to-add-users-to-a-hold-in-ediscovery.md) pour une liste d’utilisateurs à une conservation eDiscovery.
  
## <a name="manage-legal-investigations-with-the-ediscovery-premium-solution-in-microsoft-365"></a>Gérer les enquêtes juridiques avec la solution eDiscovery (Premium) dans Microsoft 365

La solution Microsoft Purview eDiscovery (Premium) dans Microsoft 365 s’appuie sur les fonctionnalités d’eDiscovery et d’analytique existantes dans Office 365. Cette nouvelle solution, appelée *eDiscovery (Premium),* fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter du contenu qui répond aux investigations internes et externes de votre organisation. Il permet également aux équipes juridiques de gérer l’ensemble du flux de travail de notification de conservation légale pour communiquer avec les conservateurs impliqués dans un cas.

eDiscovery (Premium) nécessite un abonnement E5 pour votre organisation Microsoft 365 ou Office 365. Pour plus d’informations sur les licences, consultez [Configurer eDiscovery (Premium).](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses)

Voici une vue d’ensemble rapide du flux de travail intégré dans eDiscovery (Premium). Pour plus d’informations, consultez [Gérer le flux de travail eDiscovery (Premium).](create-and-manage-advanced-ediscoveryv2-case.md#manage-the-workflow)

- [Créez un cas](create-and-manage-advanced-ediscoveryv2-case.md#create-a-case) pour commencer.

- [Gérez les consignats](managing-custodians.md) en les ajoutant à un cas et en plaçant une conservation légale du contenu dans leur boîte aux lettres, leur compte OneDrive et Microsoft Teams dont ils sont membres.

- [Gérez les communications](managing-custodian-communications.md) avec les consignatateurs en automatisant le processus de notification de conservation légale.

- [Indexez les données des consignatateurs](processing-data-for-case.md) et corrigez les erreurs d’indexation afin que vous puissiez collecter efficacement des données pour vos investigations.

- [Collectez des données](collecting-data-for-ediscovery.md) pour un cas et [ajoutez-les à un jeu d’examens](collecting-data-for-ediscovery.md#add-search-results-to-a-review-set) pour une investigation plus approfondie.

- [Affichez les](view-documents-in-review-set.md) documents, [les données de requête](review-set-search.md) et les éléments de [balise](tagging-documents.md) dans un ensemble de révisions.

- [Analysez les données de cas](analyzing-data-in-review-set.md) avec des outils d’analyse avancés.

- [Exporter les données de cas](exporting-data-ediscover20.md) en vue d’un examen par un avocat externe.

- [Gérer les travaux de longue durée](managing-jobs-ediscovery20.md) dans eDiscovery (Premium).