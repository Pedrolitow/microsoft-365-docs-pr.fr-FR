---
title: Rechercher du contenu dans un cas eDiscovery principal
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Recherchez du contenu qui peut être pertinent pour un cas core eDiscovery.
ms.openlocfilehash: 1637d5dafcf088dd2b069cda5e951aef3a2fcd1e
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58569020"
---
# <a name="search-for-content-in-a-core-ediscovery-case"></a>Rechercher du contenu dans un cas core eDiscovery

Une fois qu’un cas core eDiscovery est créé et que les personnes qui l’intéressent sont placées en attente, vous pouvez créer et exécuter une ou plusieurs recherches de contenu pertinent pour le cas. Les recherches associées à un cas core eDiscovery ne sont pas répertoriées dans la **page** de recherche de contenu du Centre de conformité Microsoft 365. Ces recherches sont répertoriées dans la page **Recherches** du cas core eDiscover à qui les recherches sont associées. Cela signifie également que les recherches associées à un cas sont accessibles uniquement par les membres du cas.

Pour créer une recherche de découverte électronique principale :
  
1. Go to <https://compliance.microsoft.com> and sign in using the credentials for user account that has been assigned the appropriate eDiscovery permissions and is a member of the case.

2. Dans le volet de navigation gauche du Centre de conformité Microsoft 365, cliquez sur Afficher **tout,** puis sur **eDiscovery > Core**.

3. Dans la page **Core eDiscovery,** sélectionnez le cas dans le cas où vous souhaitez créer une recherche associée, puis cliquez sur **Ouvrir le cas**.

4. Dans la page **d’accueil** du cas, cliquez sur **l’onglet Recherches,** puis sur **Nouvelle recherche.**

   ![Cliquez sur Nouvelle recherche pour créer une recherche de découverte électronique principale.](../media/CoreeDiscoverySearch1.png)

   > [!NOTE]
   > L’option **Recherche par liste d'identification** vous permet de rechercher des messages électroniques spécifiques et d'autres éléments de la boîte aux lettres à l'aide d'une liste d'ID Exchange. Pour créer une recherche de liste d'identification, vous soumettez un fichier CSV (valeur séparée par des virgules) qui identifie les éléments spécifiques de la boîte aux lettres à rechercher. Pour obtenir des instructions, voir [Préparer un fichier CSV pour une recherche de liste d'identification](csv-file-for-an-id-list-content-search.md).

5. Dans **l’Assistant Nouvelle recherche,** tapez un nom pour la recherche et une description facultative qui permet d’identifier la recherche. Le nom de la conservation doit être unique dans toute votre organisation.

6. Dans la page **emplacements**, sélectionnez les emplacements de contenu à rechercher. Vous pouvez rechercher des boîtes aux lettres, les sites et des dossiers publics.

    ![Choisissez les emplacements de contenu à placer en attente.](../media/ContentSearchLocations.png)
  
   1. **Boîtes aux lettres Exchange** : définissez le bouton bascule sur **Activé**, puis cliquez sur **Sélectionner des utilisateurs, des groupes ou des équipes** pour spécifier les boîtes aux lettres à mettre en attente. Utilisez la zone de recherche pour rechercher des boîtes aux lettres utilisateur et des groupes de distribution (pour placer les boîtes aux lettres des membres du groupe en conservation) à placer en conservation. Vous pouvez également effectuer une recherche dans la boîte aux lettres associée à une équipe Microsoft (pour les messages de canal), le groupe Office 365 et le groupe Yammer. Pour plus d’informations sur les données d’application stockées dans les boîtes aux lettres, consultez [Contenu stocké dans les boîtes aux lettres pour eDiscovery](what-is-stored-in-exo-mailbox.md).

   2. **Sites SharePoint** : définissez le bouton bascule sur **Activé** puis cliquez sur **Sélectionner des sites** pour spécifier les sites SharePoint et les comptes OneDrive à conserver. Saisissez l’URL de chaque site à placer en conservation. Vous pouvez également ajouter l’URL du site SharePoint d’une équipe Microsoft, d’un groupe Office 365 ou d’un groupe Yammer.
  
   3. **Dossiers publics Exchange** : définissez la bascule sur **Activé** pour mettre tous les dossiers publics en attente dans votre organisation Exchange Online. Vous ne pouvez pas choisir des dossiers publics spécifiques à mettre en attente. Laissez le bouton bascule désactivé si vous ne voulez pas maintenir les dossiers publics en attente.
  
   4. Conservez cette case à cocher sélectionnée pour rechercher du contenu Teams pour des utilisateurs locaux. Par exemple, si vous recherchez toutes les boîtes aux lettres Exchange au niveau de l’organisation et que cette case à cocher est sélectionnée, le stockage cloud utilisé pour stocker les données de conversation Teams des utilisateurs locaux sera inclus dans l’étendue de la recherche. Pour plus d'informations, voir [Recherche de données de conversation des équipes pour les utilisateurs sur site](search-cloud-based-mailboxes-for-on-premises-users.md).

7. Dans la page **Définir vos conditions de recherche**, tapez une requête mot clé et ajoutez des conditions à la requête de recherche si nécessaire.

   ![Configurez la requête de recherche.](../media/ContentSearchQuery.png)

   1. Spécifiez des mots clés, des propriétés de message telles que les dates d’envoi et de réception, ou des propriétés de document telles que les noms de fichier ou la date de dernière modification d’un document. Vous pouvez utiliser des requêtes plus complexes qui utilisent un opérateur booléen, tels que **ET**, **OU**, **PAS**, et **PRÈS**. Si vous laissez la zone du mot clé vide, tout le contenu se trouvant dans les emplacements de contenu spécifiés sera inclus dans les résultats de recherche. Si vous souhaitez en savoir plus, consultez la page [Requêtes par mots-clés et conditions de recherche pour eDiscovery](keyword-queries-and-search-conditions.md).

   2. Vous pouvez également cliquer sur la case à cocher **Afficher la liste de mots clés** puis taper un mot clé dans chaque ligne. Si vous procédez ainsi, les mots clés sur chaque ligne sont connectés à l’aide d'un opérateur logique (**c:s**) qui présente les mêmes fonctionnalités que l’opérateur **OU** de la requête de recherche créée.

      Pourquoi utiliser la liste de mots clés ? Vous pouvez obtenir des statistiques qui indiquent le nombre d’éléments qui correspondent à chaque mot clé. Cela peut vous aider à identifier rapidement les mots clés les plus importants (et les moins). Vous pouvez également utiliser une expression de mot clé (entre parenthèses) dans une ligne. Pour plus d’informations sur la liste de mots clés et les statistiques de recherche, consultez [Statistiques par mots clés pour les recherches](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > Pour réduire les problèmes liés aux longues listes de mots clés, vous êtes limité à 20 lignes au maximum dans la liste de mots clés.

   3. Vous pouvez ajouter des conditions dans une requête de recherche pour affiner une recherche et obtenir un ensemble de résultats plus précis. Chaque condition ajoute une clause à la requête de recherche qui est créée et exécutée lorsque vous démarrez la recherche. Une condition est connectée à la requête de mot-clé (spécifiée dans la zone de mot-clé) sur le plan logique par l’opérateur logique (**c:c**), qui est similaire dans son fonctionnement à l’opérateur **ET**. Cela signifie que les éléments doivent satisfaire la requête de mot-clé et une ou plusieurs conditions pour être inclus dans les résultats. C’est ainsi que les conditions contribuent à affiner vos résultats. Pour obtenir la liste et la description des conditions que vous pouvez utiliser dans une requête de recherche, consultez la rubrique [Conditions de recherche](keyword-queries-and-search-conditions.md#search-conditions).

8. Examinez les paramètres de recherche (et modifiez-les si nécessaire), puis envoyez la recherche pour la démarrer.

Une fois la recherche terminée, vous pouvez prévisualiser les résultats de recherche. Si nécessaire, cliquez **sur Actualiser** sur la page **Recherches** pour afficher la recherche que vous avez créée.

## <a name="more-information-about-searching-content-locations"></a>Plus d’informations sur la recherche d’emplacements de contenu

- Lorsque vous cliquez **sur Choisir des utilisateurs,** des groupes ou des équipes pour spécifier les boîtes aux lettres à rechercher, le soche de boîte aux lettres qui s’affiche est vide. Il s’agit d’une conception pour améliorer les performances. Pour ajouter des destinataires à cette liste, cliquez sur Choisir des **utilisateurs,** des groupes ou des équipes, tapez un nom (un minimum de trois caractères) dans la zone de recherche, cochez la case en regard du nom, puis cliquez sur **Choisir.**

- Vous pouvez ajouter des boîtes aux lettres inactives, des Microsoft Teams, des groupes Yammer, des groupes Office 365 et des groupes de distribution à la liste des boîtes aux lettres à rechercher. L’utilisation de groupes de distribution dynamique n’est pas prise en charge. Si vous ajoutez des groupes Microsoft Teams, Yammer ou des groupes Office 365, la boîte aux lettres de groupe ou d’équipe est recherché . les boîtes aux lettres des membres du groupe ne sont pas recherchés.

- Pour ajouter des sites à la recherche, sélectionnez le bouton bascule, puis cliquez sur **Choisir des sites.** Tapez l’URL de chaque site que vous souhaitez rechercher. Vous pouvez également ajouter l’URL du site SharePoint pour une équipe Microsoft, un groupe Yammer ou un groupe Office 365 web.
