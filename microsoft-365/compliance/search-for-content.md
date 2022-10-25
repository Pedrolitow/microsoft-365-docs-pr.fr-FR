---
title: Recherche de contenu
description: Utilisez l’outil eDiscovery de recherche de contenu dans le portail de conformité Microsoft Purview pour rechercher rapidement des messages électroniques dans des boîtes aux lettres Exchange, des documents dans des sites SharePoint et des emplacements OneDrive, ainsi que des conversations de messagerie instantanée dans Skype Entreprise.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- highpri
- tier1
- purview-compliance
- content-search
ms.openlocfilehash: 68adc95f2839d1e45957f0ac98cbcf19f9985807
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68687908"
---
# <a name="search-for-content-using-the-content-search-tool"></a>Rechercher du contenu à l’aide de l’outil de recherche de contenu

Utilisez l'outil de recherche de contenu dans le portail de conformité Microsoft Purview pour rechercher rapidement des e-mails dans les boîtes aux lettres Exchange, des documents dans des sites SharePoint et des emplacements OneDrive, et des conversations de messagerie instantanée dans Skype Entreprise. Vous pouvez utiliser l'outil de recherche de contenu pour rechercher des e-mails, des documents et des conversations de messagerie instantanée dans des outils de collaboration tels que Microsoft Teams et Microsoft 365 Groups.
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="search-for-content"></a>Recherche de contenu

La première étape consiste à commencer à utiliser l’outil de recherche de contenu pour choisir les emplacements de contenu à rechercher et à configurer une requête par mot clé pour rechercher des éléments spécifiques. Vous pouvez également laisser la requête vide et retourner tous les éléments dans les emplacements cibles.

- [Créez et exécutez](content-search.md) une recherche de contenu.
- [Créez des requêtes de recherche et utilisez des conditions](keyword-queries-and-search-conditions.md) pour affiner votre recherche.
- [Informations de référence sur les fonctionnalités](content-search-reference.md) pour la recherche de contenu.
- [Configurez le filtrage des autorisations de recherche](permissions-filtering-for-content-search.md) afin qu’un gestionnaire eDiscovery puisse uniquement rechercher des sous-ensembles de boîtes aux lettres ou de sites de votre organisation.
- Recherchez des utilisateurs locaux dans Microsoft 365 dans [les boîtes aux lettres basées](search-cloud-based-mailboxes-for-on-premises-users.md) sur le cloud.
- [Affichez les statistiques de mot clé](view-keyword-statistics-for-content-search.md) pour les résultats d’une recherche, puis affinez la requête si nécessaire.
- [Recherchez les données tierces](use-content-search-to-search-third-party-data-that-was-imported.md) que votre organisation a importées dans Microsoft 365.
- [Conservez les destinataires cci](/exchange/policy-and-compliance/holds/preserve-bcc-recipients-and-group-members) afin de pouvoir les rechercher.

## <a name="perform-actions-on-content-you-find"></a>Effectuer des actions sur le contenu que vous trouvez

Une fois que vous avez exécuté une recherche et que vous l’avez affinée si nécessaire, l’étape suivante consiste à effectuer une opération avec les résultats retournés par la recherche. Vous pouvez exporter et télécharger les résultats sur votre ordinateur local ou, en cas d’attaque par e-mail sur votre organisation, vous pouvez supprimer les résultats d’une recherche dans les boîtes aux lettres des utilisateurs.

- [Exportez les résultats d’une recherche de contenu](export-search-results.md) et téléchargez-les sur votre ordinateur local.
- [Recherchez et supprimez des messages électroniques](search-for-and-delete-messages-in-your-organization.md), tels que des messages contenant un virus, des pièces jointes dangereuses ou des messages d’hameçonnage.
- [Exportez un rapport](export-a-content-search-report.md) sur les résultats d’une recherche de contenu, sans exporter les résultats réels.

## <a name="learn-more-about-content-search"></a>En savoir plus sur la recherche de contenu

La recherche de contenu est facile à utiliser, mais c’est également un outil puissant. En coulisses, il se passe beaucoup de choses. Plus vous en savez à son sujet et comprenez son comportement et ses limitations, plus vous l’utiliserez avec succès pour les besoins de recherche et d’investigation de votre organisation.
  
- [Limites de recherche de contenu](limits-for-content-search.md), telles que le nombre maximal de recherches que vous pouvez exécuter à la fois et le nombre maximal d’emplacements de contenu que vous pouvez inclure dans une seule recherche.
- [Résultats de recherche estimés et réels](differences-between-estimated-and-actual-ediscovery-search-results.md) et les raisons pour lesquelles il peut y avoir des différences entre eux lorsque vous exportez et téléchargez les résultats de recherche.
- [Éléments partiellement indexés dans Exchange et SharePoint et](partially-indexed-items-in-content-search.md) comment les inclure ou les exclure lorsque vous exportez et téléchargez les résultats de recherche.
- [Examinez les éléments partiellement indexés](investigating-partially-indexed-items-in-ediscovery.md) et déterminez l’exposition de votre organisation à ces éléments.
- [Déduplication dans les résultats de recherche](de-duplication-in-ediscovery-search-results.md) que vous pouvez activer lorsque vous exportez des messages électroniques qui sont les résultats d’une recherche.

## <a name="use-scripts-for-advanced-scenarios"></a>Utiliser des scripts pour les scénarios avancés

Parfois, vous devez effectuer des tâches de recherche de contenu plus avancées, complexes et répétitives. Dans ce cas, il est plus facile et plus rapide d’utiliser des commandes dans [PowerShell security & Compliance](/powershell/exchange/scc-powershell).

Pour faciliter cette tâche, nous avons créé plusieurs scripts PowerShell de sécurité & conformité pour vous aider à effectuer des tâches complexes liées à la recherche de contenu.

- [Recherchez des boîtes aux lettres et des dossiers de site spécifiques](use-content-search-for-targeted-collections.md) (appelés collection  *ciblée* ) lorsque vous êtes certain que les éléments répondant à un cas se trouvent dans ce dossier.
- [Recherchez la liste des utilisateurs dans la boîte aux lettres et l’emplacement OneDrive](search-the-mailbox-and-onedrive-for-business-for-a-list-of-users.md) .
- [Créez, créez des rapports et supprimez plusieurs recherches](create-report-on-and-delete-multiple-content-searches.md) pour identifier et supprimer rapidement et efficacement les données de recherche.
- [Clonez une recherche de contenu](clone-a-content-search.md) et comparez rapidement les résultats de différentes requêtes de recherche par mot clé exécutées sur les mêmes emplacements de contenu ; ou utilisez le script pour gagner du temps en n’ayant pas à entrer à nouveau un grand nombre d’emplacements de contenu lorsque vous créez une nouvelle recherche.
