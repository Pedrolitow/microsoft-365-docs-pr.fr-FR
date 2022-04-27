---
title: Rechercher du contenu dans un cas eDiscovery (Standard)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Recherchez du contenu qui peut être pertinent pour un cas eDiscovery (Standard).
ms.openlocfilehash: 372f8beba2567c24e8af75acf4d11e3fe6220f2c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090404"
---
# <a name="search-for-content-in-a-ediscovery-standard-case"></a>Rechercher du contenu dans un cas eDiscovery (Standard)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Une fois qu’un cas Microsoft Purview eDiscovery (Standard) est créé et que des personnes intéressées par le cas sont mises en attente, vous pouvez créer et exécuter une ou plusieurs recherches de contenu pertinents pour le cas. Les recherches associées à un cas eDiscovery (Standard) ne sont pas répertoriées dans la page **Recherche de contenu** dans le portail de conformité Microsoft Purview. Ces recherches sont répertoriées dans la page **Recherches** du cas eDiscover principal à lequel les recherches sont associées. Cela signifie également que les recherches associées à un cas sont accessibles uniquement par les membres du cas.

Pour créer une recherche eDiscovery (Standard) :
  
1. Accédez et <https://compliance.microsoft.com> connectez-vous à l’aide des informations d’identification du compte d’utilisateur qui a reçu les autorisations eDiscovery appropriées et qui est membre du cas.

2. Dans le volet de navigation gauche du portail de conformité, cliquez sur **Afficher tout**, puis sur **eDiscovery > Core**.

3. Dans la page **eDiscovery (Standard),** sélectionnez le cas auquel vous souhaitez créer une recherche associée, puis cliquez sur **Ouvrir la casse**.

4. Dans la page **d’accueil** du cas, cliquez sur l’onglet **Recherches** , puis sur **Nouvelle recherche**.

   ![Cliquez sur Nouvelle recherche pour créer une recherche eDiscovery (Standard).](../media/CoreeDiscoverySearch1.png)

5. Dans l’Assistant **Nouvelle recherche** , tapez un nom pour la recherche et une description facultative qui permet d’identifier la recherche. Le nom de la conservation doit être unique dans toute votre organisation.

6. Dans la page **emplacements**, sélectionnez les emplacements de contenu à rechercher. Vous pouvez rechercher des boîtes aux lettres, les sites et des dossiers publics.

    ![Choisissez les emplacements de contenu à mettre sous conservation.](../media/ContentSearchLocations.png)
  
   1. **Boîtes aux lettres Exchange** : définissez le bouton bascule sur **Activé**, puis cliquez sur **Sélectionner des utilisateurs, des groupes ou des équipes** pour spécifier les boîtes aux lettres à mettre en attente. Utilisez la zone de recherche pour rechercher des boîtes aux lettres utilisateur et des groupes de distribution (pour placer les boîtes aux lettres des membres du groupe en conservation) à placer en conservation. Vous pouvez également effectuer une recherche dans la boîte aux lettres associée à une équipe Microsoft (pour les messages de canal), le groupe Office 365 et le groupe Yammer. Pour plus d’informations sur les données d’application stockées dans les boîtes aux lettres, consultez [Contenu stocké dans les boîtes aux lettres pour eDiscovery](what-is-stored-in-exo-mailbox.md).

   2. **Sites SharePoint** : définissez le bouton bascule sur **Activé** puis cliquez sur **Sélectionner des sites** pour spécifier les sites SharePoint et les comptes OneDrive à conserver. Saisissez l’URL de chaque site à placer en conservation. Vous pouvez également ajouter l’URL du site SharePoint d’une équipe Microsoft, d’un groupe Office 365 ou d’un groupe Yammer.
  
   3. **Dossiers publics Exchange** : définissez la bascule sur **Activé** pour mettre tous les dossiers publics en attente dans votre organisation Exchange Online. Vous ne pouvez pas choisir des dossiers publics spécifiques à mettre en attente. Laissez le bouton bascule désactivé si vous ne voulez pas maintenir les dossiers publics en attente.
  
   4. Conservez cette case à cocher sélectionnée pour rechercher du contenu Teams pour des utilisateurs locaux. Par exemple, si vous recherchez toutes les boîtes aux lettres Exchange au niveau de l’organisation et que cette case à cocher est sélectionnée, le stockage cloud utilisé pour stocker les données de conversation Teams des utilisateurs locaux sera inclus dans l’étendue de la recherche. Pour plus d'informations, voir [Recherche de données de conversation des équipes pour les utilisateurs sur site](search-cloud-based-mailboxes-for-on-premises-users.md).

7. Dans la page **Définir vos conditions de recherche**, tapez une requête mot clé et ajoutez des conditions à la requête de recherche si nécessaire.

   ![Configurer la requête de recherche.](../media/ContentSearchQuery.png)

   1. Spécifiez des mots clés, des propriétés de message telles que les dates d’envoi et de réception, ou des propriétés de document telles que les noms de fichier ou la date de dernière modification d’un document. Vous pouvez utiliser des requêtes plus complexes qui utilisent un opérateur booléen, tels que **ET**, **OU**, **PAS**, et **PRÈS**. Si vous laissez la zone du mot clé vide, tout le contenu se trouvant dans les emplacements de contenu spécifiés sera inclus dans les résultats de recherche. Si vous souhaitez en savoir plus, consultez la page [Requêtes par mots-clés et conditions de recherche pour eDiscovery](keyword-queries-and-search-conditions.md).

   2. Vous pouvez également cliquer sur la case à cocher **Afficher la liste de mots clés** puis taper un mot clé dans chaque ligne. Si vous procédez ainsi, les mots clés sur chaque ligne sont connectés à l’aide d'un opérateur logique (**c:s**) qui présente les mêmes fonctionnalités que l’opérateur **OU** de la requête de recherche créée.

      Pourquoi utiliser la liste de mots clés ? Vous pouvez obtenir des statistiques qui indiquent le nombre d’éléments qui correspondent à chaque mot clé. Cela peut vous aider à identifier rapidement les mots clés les plus importants (et les moins). Vous pouvez également utiliser une expression de mot clé (entre parenthèses) dans une ligne. Pour plus d’informations sur la liste de mots clés et les statistiques de recherche, consultez [Statistiques par mots clés pour les recherches](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > Pour réduire les problèmes liés aux longues listes de mots clés, vous êtes limité à 20 lignes au maximum dans la liste de mots clés.

   3. Vous pouvez ajouter des conditions de recherche pour affiner une recherche et retourner un ensemble plus affiné de résultats. Chaque condition ajoute une clause à la requête de recherche qui est créée et exécutée lorsque vous démarrez la recherche. Une condition est connectée logiquement à la requête de mot clé (spécifiée dans la zone de mot clé) par un opérateur logique (**c:c**) qui est similaire en termes de fonctionnalité à l’opérateur **AND** . Cela signifie que les éléments doivent satisfaire à la fois à la requête de mot clé et à une ou plusieurs conditions à inclure dans les résultats. C’est ainsi que les conditions aident à affiner vos résultats. Pour obtenir la liste et la description des conditions que vous pouvez utiliser dans une requête de recherche, consultez [Conditions de recherche](keyword-queries-and-search-conditions.md#search-conditions).

8. Examinez les paramètres de recherche (et modifiez-les si nécessaire), puis envoyez la recherche pour la démarrer.

Une fois la recherche terminée, vous pouvez prévisualiser les résultats de recherche. Si nécessaire, cliquez sur **Actualiser** dans la page **Recherches** pour afficher la recherche que vous avez créée.

## <a name="more-information-about-searching-content-locations"></a>Plus d’informations sur la recherche d’emplacements de contenu

- Lorsque vous cliquez sur **Choisir des utilisateurs, des groupes ou des équipes** pour spécifier des boîtes aux lettres à rechercher, le sélecteur de boîtes aux lettres affiché est vide. C’est par conception pour améliorer les performances. Pour ajouter des destinataires à cette liste, cliquez sur **Choisir des utilisateurs, des groupes ou des équipes**, **tapez** un nom (au moins trois caractères) dans la zone de recherche, activez la case à cocher en regard du nom, puis cliquez sur Choisir.

- Vous pouvez ajouter des boîtes aux lettres inactives, des Microsoft Teams, des groupes Yammer, des groupes Office 365 et des groupes de distribution à la liste des boîtes aux lettres à rechercher. L’utilisation de groupes de distribution dynamique n’est pas prise en charge. Si vous ajoutez Microsoft Teams, groupes Yammer ou groupes Office 365, la boîte aux lettres du groupe ou de l’équipe est recherchée ; les boîtes aux lettres des membres du groupe ne sont pas recherchées.

- Pour ajouter des sites à la recherche, activez le bouton bascule, puis cliquez sur **Choisir des sites**. Tapez l’URL de chaque site que vous souhaitez rechercher. Vous pouvez également ajouter l’URL du site SharePoint pour une équipe Microsoft, un groupe Yammer ou un groupe Office 365.
