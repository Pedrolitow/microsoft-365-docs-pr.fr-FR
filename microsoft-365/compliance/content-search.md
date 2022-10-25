---
title: Créer et exécuter une recherche de contenu dans le portail de conformité Microsoft Purview
description: Utilisez l'outil eDiscovery de recherche de contenu dans le centre de conformité pour rechercher du contenu dans différents services Microsoft 365.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- tier1
- purview-compliance
- ediscovery
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: 80049d041bce7c959eb9d0b00d4fec86a94ad1de
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688404"
---
# <a name="create-a-content-search"></a>Créer une recherche de contenu

You can use the Content search eDiscovery tool in the Microsoft Purview compliance portal to search for in-place content such as email, documents, and instant messaging conversations in your organization. Use this tool to search for content in these cloud-based Microsoft 365 data sources:
  
- Echange de boîtes aux lettres en ligne
- Sites SharePoint Online et comptes OneDrive entreprises
- Microsoft Teams
- Groupes Microsoft 365
- Groupes Yammer

Après avoir exécuté une recherche, le nombre d’emplacements de contenu et l’estimation du nombre de résultats de recherche sont affichés sur la page de menu déroulant de recherche. Vous pouvez afficher rapidement des statistiques, telles que les emplacements de contenu qui ont le plus grand nombre d’éléments qui correspondent à la requête de recherche. Une fois que vous avez effectué une recherche, vous pouvez afficher un aperçu des résultats ou les exporter sur un ordinateur local.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="before-you-run-a-search"></a>Avant d’exécuter une recherche

- To access to the Content search tool in the <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">compliance portal</a> (to run searches and preview results and export results), an administrator, compliance officer, or eDiscovery manager must be a member of the eDiscovery Manager role group in the compliance portal. For more information, see [Assign eDiscovery permissions](assign-ediscovery-permissions.md).
- Dans un déploiement Exchange hybride, vous ne pouvez pas utiliser l’outil Recherche de contenu pour rechercher des e-mails des boîtes aux lettres locales. Vous pouvez uniquement utiliser l’outil pour rechercher des boîtes mail dans le cloud.
- Dans un déploiement Exchange hybride, vous pouvez rechercher des données de conversation Teams dans des boîtes aux lettres locales. Pour plus d'informations, consultez [Données de conversation Teams pour les utilisateurs locaux](/microsoft-365/compliance/search-cloud-based-mailboxes-for-on-premises-users).

## <a name="create-and-run-a-search"></a>Créer et exécuter une recherche
  
1. Accédez au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) et connectez-vous à l’aide des informations d’identification d’un compte auquel les autorisations appropriées ont été attribuées.

2. Dans le volet de navigation gauche du portail de conformité, sélectionnez **Recherche de contenu**.

3. Dans la page **Recherche de contenu** , sélectionnez **Nouvelle recherche**.

4. Dans la page **Nom et description** , entrez un nom pour la recherche, une description facultative qui permet d’identifier la recherche. Le nom de la conservation doit être unique dans toute votre organisation.

5. Dans la page **emplacements**, sélectionnez les emplacements de contenu à rechercher. Vous pouvez rechercher des boîtes aux lettres, les sites et des dossiers publics.

    ![Choisissez les emplacements de contenu à rechercher.](../media/ContentSearchLocations.png)
  
   1. **Boîtes aux lettres Exchange** : définissez le bouton bascule sur **Activé** , puis sélectionnez **Choisir des utilisateurs, des groupes ou des équipes** pour spécifier les boîtes aux lettres à rechercher. Utilisez la zone de recherche pour rechercher des boîtes mail d’utilisateur et des groupes de distribution. Vous pouvez également rechercher dans la boîte aux lettres associée à une équipe Microsoft (pour les messages de canal), le groupe Microsoft 365 et le groupe Yammer. Pour plus d’informations sur les données d’application stockées dans les boîtes aux lettres, consultez [Contenu stocké dans les boîtes aux lettres pour eDiscovery](what-is-stored-in-exo-mailbox.md).

   2. **Sites SharePoint** : définissez le bouton bascule sur **Activé** , puis sélectionnez **Choisir des sites** pour spécifier les sites SharePoint et les comptes OneDrive à rechercher. Entrez l’URL de chaque site que vous souhaitez rechercher. Vous pouvez également ajouter l’URL du site SharePoint pour une équipe Microsoft, un groupe Microsoft 365 ou un groupe Yammer.
  
   3. **Dossiers publics Exchange** : définissez le bouton bascule **sur Activé** pour rechercher tous les dossiers publics de votre organisation Exchange Online. Vous ne pouvez pas choisir de dossiers publics spécifiques à rechercher. Laissez le bouton bascule désactivé si vous ne souhaitez pas rechercher dans tous les dossiers publics.
  
   4. Conservez cette case à cocher sélectionnée pour rechercher du contenu Teams pour des utilisateurs locaux. Par exemple, si vous recherchez toutes les boîtes aux lettres Exchange au niveau de l’organisation et que cette case à cocher est sélectionnée, le stockage cloud utilisé pour stocker les données de conversation Teams des utilisateurs locaux sera inclus dans l’étendue de la recherche. Pour plus d'informations, voir [Recherche de données de conversation des équipes pour les utilisateurs sur site](search-cloud-based-mailboxes-for-on-premises-users.md).

6. Dans la page **Conditions** , entrez une requête de mot clé et ajoutez des conditions à la requête de recherche si nécessaire.

   ![Configurer la requête de recherche.](../media/ContentSearchQuery.png)

   1. Spécifiez des mots clés, des propriétés de message telles que les dates d’envoi et de réception, ou des propriétés de document telles que les noms de fichier ou la date de dernière modification d’un document. Vous pouvez utiliser des requêtes plus complexes qui utilisent un opérateur booléen, tels que **ET**, **OU**, **PAS**, et **PRÈS**. Si vous laissez la zone du mot clé vide, tout le contenu se trouvant dans les emplacements de contenu spécifiés sera inclus dans les résultats de recherche. Si vous souhaitez en savoir plus, consultez la page [Requêtes par mots-clés et conditions de recherche pour eDiscovery](keyword-queries-and-search-conditions.md).

   2. Vous pouvez également cocher la case **Afficher la liste de mots clés** et entrer un mot clé dans chaque ligne. Si vous procédez ainsi, les mots clés sur chaque ligne sont connectés à l’aide d'un opérateur logique (**c:s**) qui présente les mêmes fonctionnalités que l’opérateur **OU** de la requête de recherche créée.

      **Pourquoi utiliser la liste de mots clés** ? Vous pouvez obtenir des statistiques qui indiquent le nombre d’éléments qui correspondent à chaque mot clé. Cela peut vous aider à identifier rapidement les mots clés les plus importants (et les moins). Vous pouvez également utiliser une expression de mot clé (entre parenthèses) dans une ligne. Pour plus d’informations sur la liste de mots clés et les statistiques de recherche, consultez [Statistiques par mots clés pour les recherches](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > Pour réduire les problèmes liés aux longues listes de mots clés, vous êtes limité à 20 lignes au maximum dans la liste de mots clés.

   3. You can add search conditions to narrow a search and return a more refined set of results. Each condition adds a clause to the search query that is created and run when you start the search. A condition is logically connected to the keyword query (specified in the keyword box) by a logical operator (**c:c**) that is similar in functionality to the **AND** operator. That means that items have to satisfy both the keyword query and one or more conditions to be included in the results. This is how conditions help to narrow your results. For a list and description of conditions that you can use in a search query, see [Search conditions](keyword-queries-and-search-conditions.md#search-conditions).

7. Passez en revue les paramètres de recherche (et modifiez-les si nécessaire), puis sélectionnez **Envoyer** pour démarrer la recherche.
  
Pour accéder à cette recherche de contenu ou accéder à d’autres recherches de contenu répertoriées dans la page **Recherche de contenu** , sélectionnez une recherche pour afficher le résumé de la recherche et les statistiques de recherche.

Pour plus d’informations sur la recherche de contenu, telle que la recherche de contenu dans différents services Microsoft 365, consulter [Référence des fonctionnalités pour la recherche du contenu](content-search-reference.md).

## <a name="next-steps"></a>Étapes suivantes

Voici la liste des étapes suivantes à effectuer après avoir créé et exécuté une recherche de contenu.

- [Aperçu des résultats de la recherche](preview-ediscovery-search-results.md)
- [Afficher des statistiques pour les résultats de recherche](view-keyword-statistics-for-content-search.md)
- [Exporter les résultats de la recherche](export-search-results.md)
- [Exporter un rapport de recherche](export-a-content-search-report.md)
