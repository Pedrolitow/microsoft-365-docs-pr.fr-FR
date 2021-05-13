---
title: Créer et exécuter une recherche de contenu dans le Centre de conformité Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Utilisez l'outil eDiscovery de recherche de contenu dans le centre de conformité pour rechercher du contenu dans différents services Microsoft 365.
ms.openlocfilehash: 5f48418882d5d4c7589b3ef394a0a306c0675f34
ms.sourcegitcommit: 967f64dfa1a05f31179c8316b96bfb7758a5d990
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52332845"
---
# <a name="create-a-content-search"></a>Créer une recherche de contenu

Vous pouvez utiliser l'outil de recherche de contenu eDiscovery dans le Centre de conformité Microsoft 365 pour rechercher du contenu en place tels que des e-mails, des documents et des conversations de messagerie instantanée dans votre organisation. Utilisez cet outil pour rechercher du contenu dans ces sources de données Microsoft 365 :
  
- Echange de boîtes aux lettres en ligne

- Sites SharePoint Online et comptes OneDrive entreprises

- Microsoft Teams

- Groupes Microsoft 365

- Groupes Yammer

Après avoir exécuté une recherche, le nombre d’emplacements de contenu et l’estimation du nombre de résultats de recherche sont affichés sur la page de menu déroulant de recherche. Vous pouvez afficher rapidement des statistiques, telles que les emplacements de contenu qui ont le plus grand nombre d’éléments qui correspondent à la requête de recherche. Une fois que vous avez effectué une recherche, vous pouvez afficher un aperçu des résultats ou les exporter sur un ordinateur local.

## <a name="create-and-run-a-search"></a>Créer et exécuter une recherche

Pour accéder à la page **recherche de contenu** dans le Centre de conformité Microsoft 365 (pour effectuer des recherches et afficher un aperçu des résultats et exporter les résultats), un administrateur, un officier de conformité ou un gestionnaire d’eDiscovery doit être membre du groupe de rôles gestionnaire eDiscovery dans le Centre de conformité & de sécurité. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md).
  
1. Accédez à <https://compliance.microsoft.com> et connectez-vous à l’aide des informations d’identification d’un compte avec les autorisations appropriées.

2. Dans le volet de navigation gauche du centre de conformité Microsoft 365, cliquez sur **Afficher tout** , puis sur **Recherche de contenu**.

3. Sur la **page de recherche** de contenu, cliquez **sur Nouvelle recherche**.

   > [!NOTE]
   > L’option **Recherche par liste d'identification** vous permet de rechercher des messages électroniques spécifiques et d'autres éléments de la boîte aux lettres à l'aide d'une liste d'ID Exchange. Pour créer une recherche de liste d'identification, vous soumettez un fichier CSV (valeur séparée par des virgules) qui identifie les éléments spécifiques de la boîte aux lettres à rechercher. Pour obtenir des instructions, voir [Préparer un fichier CSV pour une recherche de liste d'identification](csv-file-for-an-id-list-content-search.md).

4. Tapez un nom pour la recherche, une description facultative qui vous permet d’identifier la recherche. Le nom de la conservation doit être unique dans toute votre organisation.

5. Dans la page **emplacements**, sélectionnez les emplacements de contenu à rechercher. Vous pouvez rechercher des boîtes aux lettres, les sites et des dossiers publics.

    ![Choisissez les emplacements de contenu à mettre sous conservation](../media/ContentSearchLocations.png)
  
   1. **Boîtes aux lettres Exchange** : définissez le bouton bascule sur **Activé**, puis cliquez sur **Sélectionner des utilisateurs, des groupes ou des équipes** pour spécifier les boîtes aux lettres à mettre en attente. Utilisez la zone de recherche pour rechercher des boîtes aux lettres utilisateur et des groupes de distribution (pour placer les boîtes aux lettres des membres du groupe en conservation) à placer en conservation. Vous pouvez également effectuer une recherche dans la boîte aux lettres associée à une équipe Microsoft (pour les messages de canal), le groupe Office 365 et le groupe Yammer. Pour plus d’informations sur les données d’application stockées dans les boîtes aux lettres, consultez [Contenu stocké dans les boîtes aux lettres pour eDiscovery](what-is-stored-in-exo-mailbox.md).

   2. **Sites SharePoint** : définissez le bouton bascule sur **Activé** puis cliquez sur **Sélectionner des sites** pour spécifier les sites SharePoint et les comptes OneDrive à conserver. Saisissez l’URL de chaque site à placer en conservation. Vous pouvez également ajouter l’URL du site SharePoint d’une équipe Microsoft, d’un groupe Office 365 ou d’un groupe Yammer.
  
   3. **Dossiers publics Exchange** : définissez la bascule sur **Activé** pour mettre tous les dossiers publics en attente dans votre organisation Exchange Online. Vous ne pouvez pas choisir des dossiers publics spécifiques à mettre en attente. Laissez le bouton bascule désactivé si vous ne voulez pas maintenir les dossiers publics en attente.
  
   4. Conservez cette case à cocher sélectionnée pour rechercher du contenu Teams pour des utilisateurs locaux. Par exemple, si vous recherchez toutes les boîtes aux lettres Exchange au niveau de l’organisation et que cette case à cocher est sélectionnée, le stockage cloud utilisé pour stocker les données de conversation Teams des utilisateurs locaux sera inclus dans l’étendue de la recherche. Pour plus d'informations, voir [Recherche de données de conversation des équipes pour les utilisateurs sur site](search-cloud-based-mailboxes-for-on-premises-users.md).

6. Dans la page **Définir vos conditions de recherche**, tapez une requête mot clé et ajoutez des conditions à la requête de recherche si nécessaire.

   ![Configurer la requête de recherche](../media/ContentSearchQuery.png)

   1. Spécifiez des mots clés, des propriétés de message telles que les dates d’envoi et de réception, ou des propriétés de document telles que les noms de fichier ou la date de dernière modification d’un document. Vous pouvez utiliser des requêtes plus complexes qui utilisent un opérateur booléen, tels que **ET**, **OU**, **PAS**, et **PRÈS**. Si vous laissez la zone du mot clé vide, tout le contenu se trouvant dans les emplacements de contenu spécifiés sera inclus dans les résultats de recherche. Si vous souhaitez en savoir plus, consultez la page [Requêtes par mots-clés et conditions de recherche pour eDiscovery](keyword-queries-and-search-conditions.md).

   2. Vous pouvez également cliquer sur la case à cocher **Afficher la liste de mots clés** puis taper un mot clé dans chaque ligne. Si vous procédez ainsi, les mots clés sur chaque ligne sont connectés à l’aide d'un opérateur logique (**c:s**) qui présente les mêmes fonctionnalités que l’opérateur **OU** de la requête de recherche créée.

      Pourquoi utiliser la liste de mots clés ? Vous pouvez obtenir des statistiques qui indiquent le nombre d’éléments qui correspondent à chaque mot clé. Cela peut vous aider à identifier rapidement les mots clés les plus importants (et les moins). Vous pouvez également utiliser une expression de mot clé (entre parenthèses) dans une ligne. Pour plus d’informations sur la liste de mots clés et les statistiques de recherche, consultez [Statistiques par mots clés pour les recherches](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > Pour réduire les problèmes liés aux longues listes de mots clés, vous êtes limité à 20 lignes au maximum dans la liste de mots clés.

   3. Vous pouvez ajouter des conditions dans une requête de recherche pour affiner une recherche et obtenir un ensemble de résultats plus précis. Chaque condition ajoute une clause à la requête de recherche qui est créée et exécutée lorsque vous démarrez la recherche. Une condition est connectée à la requête de mot-clé (spécifiée dans la zone de mot-clé) sur le plan logique par l’opérateur logique (**c:c**), qui est similaire dans son fonctionnement à l’opérateur **ET**. Cela signifie que les éléments doivent satisfaire la requête de mot-clé et une ou plusieurs conditions pour être inclus dans les résultats. C’est ainsi que les conditions contribuent à affiner vos résultats. Pour obtenir la liste et la description des conditions que vous pouvez utiliser dans une requête de recherche, consultez la rubrique [Conditions de recherche](keyword-queries-and-search-conditions.md#search-conditions).

7. Examinez les paramètres de recherche (et modifiez-les si nécessaire), puis envoyez la recherche pour la démarrer.
  
Pour accéder de nouveau à la recherche de contenu ou accéder aux recherches de contenu répertoriées sur la page **recherche de contenu**, sélectionnez la recherche, puis cliquez sur **Ouvrir**.

## <a name="next-steps"></a>Étapes suivantes

Voici la liste des étapes suivantes à effectuer après avoir créé et exécuté une recherche de contenu.

- [Aperçu des résultats de la recherche](preview-ediscovery-search-results.md)

- [Afficher des statistiques pour les résultats de recherche](view-keyword-statistics-for-content-search.md)

- [Exporter les résultats de la recherche](export-search-results.md)

- [Exporter un rapport de recherche](export-a-content-search-report.md)

## <a name="more-information"></a>Plus d’informations

Pour plus d’informations sur la recherche de contenu, telle que la recherche de contenu dans différents services Microsoft 365, consulter [Référence des fonctionnalités pour la recherche du contenu](content-search-reference.md).
