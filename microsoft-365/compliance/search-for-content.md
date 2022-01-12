---
title: Recherche de contenu
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
description: Utilisez l’outil eDiscovery de recherche de contenu dans le Centre de conformité Microsoft 365 pour trouver rapidement des messages électroniques dans des boîtes aux lettres Exchange, des documents dans des sites SharePoint et des emplacements OneDrive, ainsi que des conversations de messagerie instantanée dans Skype Entreprise.
ms.openlocfilehash: 21e07f09c21bbf0196b6ba113b82ec3030aada32
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61936497"
---
# <a name="search-for-content-using-the-content-search-tool"></a>Rechercher du contenu à l’aide de l’outil de recherche de contenu

Utilisez l'outil de recherche de contenu dans le centre de conformité Microsoft 365 pour rechercher rapidement des e-mails dans les boîtes aux lettres Exchange, des documents dans des sites SharePoint et des emplacements OneDrive, et des conversations de messagerie instantanée dans Skype Entreprise. Vous pouvez utiliser l'outil de recherche de contenu pour rechercher des e-mails, des documents et des conversations de messagerie instantanée dans des outils de collaboration tels que Microsoft Teams et Microsoft 365 Groups.
  
## <a name="search-for-content"></a>Recherche de contenu

La première étape consiste à commencer à utiliser l’outil de recherche de contenu pour choisir les emplacements de contenu à rechercher et configurer une requête de mot clé pour rechercher des éléments spécifiques. Vous pouvez également laisser la requête vide et renvoyer tous les éléments aux emplacements cibles.
  
- [Créer et exécuter une](content-search.md) recherche de contenu

- [Créer des requêtes de recherche et utiliser des conditions pour](keyword-queries-and-search-conditions.md) affiner votre recherche

- [Référence des fonctionnalités](content-search-reference.md) pour la recherche de contenu

- [Configurer le filtrage des autorisations](permissions-filtering-for-content-search.md) de recherche afin qu’un gestionnaire eDiscovery ne puisse rechercher que le sous-ensemble de boîtes aux lettres ou de sites de votre organisation

- [Rechercher des boîtes aux lettres dans le cloud](search-cloud-based-mailboxes-for-on-premises-users.md) pour les utilisateurs locaux dans Microsoft 365

- [Afficher les statistiques de](view-keyword-statistics-for-content-search.md) mot clé pour les résultats d’une recherche, puis affiner la requête si nécessaire

- [Rechercher des données tierces que](use-content-search-to-search-third-party-data-that-was-imported.md) votre organisation a importées dans Microsoft 365

- [Conserver les destinataires Bcc](/exchange/policy-and-compliance/holds/preserve-bcc-recipients-and-group-members) afin de pouvoir les rechercher

## <a name="perform-actions-on-content-you-find"></a>Effectuer des actions sur le contenu que vous trouvez

Une fois que vous avez exécuté une recherche et que vous l’avez affinée si nécessaire, l’étape suivante consiste à effectuer une opération avec les résultats renvoyés par la recherche. Vous pouvez exporter et télécharger les résultats sur votre ordinateur local ou, en cas d’attaque par courrier électronique sur votre organisation, vous pouvez supprimer les résultats d’une recherche dans les boîtes aux lettres des utilisateurs.
  
- [Exporter les résultats d’une recherche de contenu et](export-search-results.md) les télécharger sur votre ordinateur local

- [Rechercher et supprimer des messages](search-for-and-delete-messages-in-your-organization.md)électroniques, tels que des messages qui contentent un virus, des pièces jointes dangereuses ou des messages de hameçonnage

- [Exporter un rapport sur](export-a-content-search-report.md) les résultats d’une recherche de contenu, sans exporter les résultats réels

## <a name="learn-more-about-content-search"></a>En savoir plus sur la recherche de contenu

La recherche de contenu est facile à utiliser, mais il s’agit également d’un outil puissant. En arrière-plan, il se passe beaucoup de choses. Plus vous en sconnaissez et que vous comprenez son comportement et ses limitations, plus vous l’utiliserez pour répondre aux besoins de recherche et d’examen de votre organisation. Pour en savoir plus, approfondissez les sujets suivants :
  
- [Limites de recherche de](limits-for-content-search.md)contenu, telles que le nombre maximal de recherches que vous pouvez exécuter en même temps et le nombre maximal d’emplacements de contenu que vous pouvez inclure dans une recherche unique

- [Résultats de recherche estimés](differences-between-estimated-and-actual-ediscovery-search-results.md) et réels et raisons pour lesquelles il peut y avoir des différences entre eux lorsque vous exportez et téléchargez des résultats de recherche

- [Éléments partiellement indexés](partially-indexed-items-in-content-search.md) dans Exchange et SharePoint et comment les inclure ou les exclure lorsque vous exportez et téléchargez des résultats de recherche

- [Examiner les éléments partiellement indexés et](investigating-partially-indexed-items-in-ediscovery.md) déterminer l’exposition de votre organisation à ces éléments

- [Dédoplication dans les résultats de recherche](de-duplication-in-ediscovery-search-results.md) que vous pouvez activer lorsque vous exportez des messages électroniques qui sont les résultats d’une recherche

## <a name="use-scripts-for-advanced-scenarios"></a>Utiliser des scripts pour des scénarios avancés

Parfois, vous devez effectuer des tâches de recherche de contenu plus avancées, complexes et répétitives. Dans ce cas, il est plus facile et plus rapide d’utiliser les commandes dans le Centre de sécurité & conformité PowerShell. Pour faciliter cette tâche, nous avons créé un certain nombre de scripts powerShell du Centre de sécurité et conformité & pour vous aider à effectuer des tâches complexes liées à la recherche de contenu.

- [Rechercher des dossiers de](use-content-search-for-targeted-collections.md) boîte  aux lettres et de site spécifiques (appelés collection ciblée) lorsque vous êtes certain que les éléments qui répondent à un cas se trouvent dans ce dossier

- [Rechercher une liste d’utilisateurs dans OneDrive boîte](search-the-mailbox-and-onedrive-for-business-for-a-list-of-users.md) aux lettres et dans l’emplacement de l’utilisateur

- [Créer, créer des rapports et supprimer plusieurs recherches](create-report-on-and-delete-multiple-content-searches.md) pour identifier et éliminer rapidement et efficacement les données de recherche

- [Clonez une recherche de contenu](clone-a-content-search.md) et comparez rapidement les résultats de différentes requêtes de recherche par mot clé qui s’exécutent sur les mêmes emplacements de contenu ; ou utiliser le script pour gagner du temps en n’ayant pas à entrer à nouveau un grand nombre d’emplacements de contenu lorsque vous créez une recherche
