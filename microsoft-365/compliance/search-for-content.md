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
description: Utilisez l’outil eDiscovery de recherche de contenu dans le portail de conformité Microsoft Purview pour rechercher rapidement des e-mails dans des boîtes aux lettres Exchange, des documents dans des sites SharePoint et des emplacements OneDrive, ainsi que des conversations de messagerie instantanée dans Skype Entreprise.
ms.openlocfilehash: 4efe2f4b4735005c10fd59e618bb6ecc8be51ec0
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993642"
---
# <a name="search-for-content-using-the-content-search-tool"></a>Rechercher du contenu à l’aide de l’outil de recherche de contenu

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Utilisez l'outil de recherche de contenu dans le portail de conformité Microsoft Purview pour rechercher rapidement des e-mails dans les boîtes aux lettres Exchange, des documents dans des sites SharePoint et des emplacements OneDrive, et des conversations de messagerie instantanée dans Skype Entreprise. Vous pouvez utiliser l'outil de recherche de contenu pour rechercher des e-mails, des documents et des conversations de messagerie instantanée dans des outils de collaboration tels que Microsoft Teams et Microsoft 365 Groups.
  
## <a name="search-for-content"></a>Recherche de contenu

La première étape consiste à commencer à utiliser l’outil de recherche de contenu pour choisir des emplacements de contenu à rechercher et configurer une requête de mot clé pour rechercher des éléments spécifiques. Vous pouvez également laisser la requête vide et retourner tous les éléments dans les emplacements cibles.
  
- [Créer et exécuter](content-search.md) une recherche de contenu

- [Créer des requêtes de recherche et utiliser des conditions](keyword-queries-and-search-conditions.md) pour affiner votre recherche

- [Informations de référence sur les fonctionnalités](content-search-reference.md) de recherche de contenu

- [Configurer le filtrage des autorisations de recherche](permissions-filtering-for-content-search.md) afin qu’un gestionnaire eDiscovery puisse uniquement rechercher un sous-ensemble de boîtes aux lettres ou de sites dans votre organisation

- [Rechercher des boîtes aux lettres basées](search-cloud-based-mailboxes-for-on-premises-users.md) sur le cloud pour les utilisateurs locaux dans Microsoft 365

- [Afficher les statistiques des mots clés](view-keyword-statistics-for-content-search.md) pour les résultats d’une recherche, puis affiner la requête si nécessaire

- [Recherchez des données tierces](use-content-search-to-search-third-party-data-that-was-imported.md) que votre organisation a importées dans Microsoft 365

- [Conservez les destinataires CCI](/exchange/policy-and-compliance/holds/preserve-bcc-recipients-and-group-members) afin de pouvoir les rechercher

## <a name="perform-actions-on-content-you-find"></a>Effectuer des actions sur le contenu que vous trouvez

Après avoir exécuté une recherche et l’avoir affinée si nécessaire, l’étape suivante consiste à effectuer une opération avec les résultats retournés par la recherche. Vous pouvez exporter et télécharger les résultats sur votre ordinateur local ou, en cas d’attaque par e-mail sur votre organisation, vous pouvez supprimer les résultats d’une recherche dans les boîtes aux lettres des utilisateurs.
  
- [Exporter les résultats d’une recherche de contenu](export-search-results.md) et les télécharger sur votre ordinateur local

- [Rechercher et supprimer des messages électroniques](search-for-and-delete-messages-in-your-organization.md), tels que des messages qui contenunt un virus, des pièces jointes dangereuses ou des messages de hameçonnage

- [Exporter un rapport](export-a-content-search-report.md) sur les résultats d’une recherche de contenu, sans exporter les résultats réels

## <a name="learn-more-about-content-search"></a>En savoir plus sur la recherche de contenu

La recherche de contenu est facile à utiliser, mais il s’agit également d’un outil puissant. En arrière-plan, il y a beaucoup de choses qui se passent. Plus vous en savez et comprenez son comportement et ses limitations, plus vous l’utiliserez avec succès pour les besoins de recherche et d’investigation de votre organisation. Pour en savoir plus, approfondissez les sujets suivants :
  
- [Limites de recherche](limits-for-content-search.md) de contenu, telles que le nombre maximal de recherches que vous pouvez exécuter en une seule fois et le nombre maximal d’emplacements de contenu que vous pouvez inclure dans une recherche unique

- [Résultats de recherche estimés et réels](differences-between-estimated-and-actual-ediscovery-search-results.md) , ainsi que les raisons pour lesquelles il peut y avoir des différences entre eux lorsque vous exportez et téléchargez des résultats de recherche

- [Éléments partiellement indexés dans Exchange et SharePoint](partially-indexed-items-in-content-search.md) et comment les inclure ou les exclure lorsque vous exportez et téléchargez des résultats de recherche

- [Examiner les éléments partiellement indexés](investigating-partially-indexed-items-in-ediscovery.md) et déterminer l’exposition de votre organisation à ces éléments

- [Dédoublement des résultats de recherche](de-duplication-in-ediscovery-search-results.md) que vous pouvez activer lorsque vous exportez des messages électroniques qui sont les résultats d’une recherche

## <a name="use-scripts-for-advanced-scenarios"></a>Utiliser des scripts pour des scénarios avancés

Parfois, vous devez effectuer des tâches de recherche de contenu plus avancées, complexes et répétitives. Dans ce cas, il est plus facile et plus rapide d’utiliser des commandes dans le Centre de sécurité & conformité PowerShell. Pour faciliter cette tâche, nous avons créé un certain nombre de scripts PowerShell security & Compliance Center pour vous aider à effectuer des tâches complexes liées à la recherche de contenu.

- [Recherchez des dossiers de boîte aux lettres et de site spécifiques (appelés](use-content-search-for-targeted-collections.md)  *regroupements ciblés* ) lorsque vous êtes certain que les éléments sensibles à un cas se trouvent dans ce dossier

- [Rechercher une liste d’utilisateurs dans la boîte aux lettres et l’emplacement OneDrive](search-the-mailbox-and-onedrive-for-business-for-a-list-of-users.md)

- [Créer, signaler et supprimer plusieurs recherches](create-report-on-and-delete-multiple-content-searches.md) pour identifier et éliminer rapidement et efficacement les données de recherche

- [Clonez une recherche de contenu](clone-a-content-search.md) et comparez rapidement les résultats de différentes requêtes de recherche par mot clé exécutées sur les mêmes emplacements de contenu ; ou utilisez le script pour gagner du temps en n’ayant pas à entrer à nouveau un grand nombre d’emplacements de contenu lorsque vous créez une recherche
