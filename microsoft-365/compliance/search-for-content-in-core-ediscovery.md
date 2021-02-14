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
description: Vous pouvez rechercher du contenu qui peut être pertinent pour un cas core eDiscovery.
ms.openlocfilehash: d17a9d16643ec9077e02b5438597237b80f09af5
ms.sourcegitcommit: 6007dbe2cf758c683de399f94023122c678bcada
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "44224621"
---
# <a name="search-for-content-in-a-core-ediscovery-case"></a>Rechercher du contenu dans un cas core eDiscovery

Une fois qu’un cas core eDiscovery est créé et que les personnes qui l’intéressent sont placées en attente, vous pouvez créer et exécuter une ou plusieurs recherches de contenu pertinent pour le cas. Les recherches associées à un cas de découverte électronique principale ne sont pas répertoriées dans la **page** de recherche de contenu du Centre de conformité Microsoft 365. Ces recherches sont répertoriées dans la page **Recherches** du cas core eDiscover à qui les recherches sont associées. Cela signifie également que les recherches associées à un cas sont accessibles uniquement par les membres du cas.

Pour créer une recherche de découverte électronique principale :
  
1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and sign in using the credentials for user account that has been assigned the appropriate eDiscovery permissions.

2. Dans le volet de navigation gauche du Centre de conformité Microsoft 365, cliquez sur Afficher **tout,** puis sur **eDiscovery > Core**.

3. Dans la page **Core eDiscovery,** sélectionnez le cas dans le cas où vous souhaitez créer une recherche associée, puis cliquez sur **Ouvrir le cas**.

4. Dans la page **d’accueil** du cas, cliquez sur **l’onglet Recherches.**
  
5. Dans la page **Recherche,** cliquez sur **Nouvelle recherche.**

6. Sur la page **Nouvelle recherche**, vous pouvez ajouter des mots clés et des conditions pour créer la requête de recherche. 

    ![Nouvelle recherche](../media/0e9954e7-c0ea-4e05-820b-e4b81dc5f81d.png)
  
   a. Vous pouvez spécifier des mots clés, des propriétés de message, telles que des dates d’envoi et de réception, ou des propriétés de document, telles que les noms de fichiers ou la date de la dernière fois où un document a été modifié. Vous pouvez utiliser des requêtes plus complexes qui utilisent un opérateur booléen, tel que **AND**, **OR**, **NOT** ou **NEAR**. Vous pouvez également rechercher des informations sensibles (des numéros de sécurité sociale, par exemple) dans des documents ou rechercher des documents qui ont été partagés en externe. Si vous laissez la zone de mot clé vide, tout le contenu situé dans les emplacements de contenu spécifiés sera inclus dans les résultats de la recherche.

   b. Vous pouvez cliquer sur la **case à** cocher Afficher la liste de mots clés et taper un mot clé dans chaque ligne. Dans ce cas, les mots clés de chaque ligne sont connectés par l’opérateur **OR** dans la requête de recherche créée. Vous pouvez entrer un maximum de 20 mots clés dans la liste.

    ![Liste de mots clés](../media/29cceb5d-2817-4fc4-b91a-ced1c5824a17.png)
  
    Pourquoi utiliser la liste de mots clés ? Vous pouvez obtenir des statistiques qui indiquent le nombre d’éléments qui correspondent à chaque mot clé. Cela peut vous aider à identifier rapidement les mots clés les plus importants (et les moins). Vous pouvez également utiliser une expression de mot clé (entre parenthèses) dans une ligne. Pour plus d’informations sur les statistiques de recherche, voir [afficher les statistiques des mots clés pour les résultats de recherche de contenu](view-keyword-statistics-for-content-search.md).

    Pour plus d’informations sur l’utilisation de la liste des mots clés, voir [Création d’une requête de recherche.](content-search.md#building-a-search-query)

   c. Vous pouvez cliquer **sur Conditions** et ajouter des conditions à une requête de recherche pour affiner une recherche et renvoyer un ensemble de résultats plus affiné. Chaque condition ajoute une clause à la requête de recherche KQL créée et exécutée lors du démarrage de la recherche. Une condition est logiquement connectée à la requête de mot clé (spécifiée dans la zone du mot clé) par l’opérateur **AND** . Cela signifie que les éléments doivent satisfaire la requête de mot clé et chaque condition à inclure dans les résultats. C’est ainsi que les conditions contribuent à affiner vos résultats.

    Pour plus d’informations sur la création d’une requête de recherche et l’utilisation de conditions, voir [Keyword queries for Content Search](keyword-queries-and-search-conditions.md).

7. Sous **Emplacements : emplacements en attente,** choisissez les emplacements de contenu que vous souhaitez rechercher. Vous pouvez rechercher des boîtes aux lettres, des sites et des dossiers publics dans la même recherche.

    ![Emplacements, emplacements en attente](../media/d56398aa-0b20-4500-8e26-494eab92a99f.png)
  
    - **Tous les emplacements**. Sélectionnez cette option pour rechercher tous les emplacements de contenu de votre organisation. Lorsque vous sélectionnez cette option, vous pouvez choisir de rechercher toutes les boîtes aux lettres Exchange (y compris les boîtes aux lettres de toutes les équipes Microsoft Teams, groupes Yammer et groupes Office 365), tous les sites SharePoint et OneDrive Entreprise (qui inclut les sites de toutes les équipes Microsoft, groupes Yammer et groupes Office 365) et tous les dossiers publics.
    
    - **Tous les emplacements en attente**. Sélectionnez cette option pour rechercher tous les emplacements de contenu qui ont été placés en attente eDiscovery dans le cas. Si le cas contient plusieurs cas de non-lieu, les emplacements de contenu de toutes les ententées seront recherchés. En outre, si un emplacement de contenu a été placé en attente basée sur une requête, seuls les éléments en attente seront recherchés lorsque vous exécuterez la recherche de contenu que vous créez au cours de cette étape. Par exemple, si un utilisateur a été placé en conservation de cas basée sur une requête qui conserve les éléments qui ont été envoyés ou créés avant une date spécifique, seuls ces éléments sont recherchés. Pour ce faire, connectez la requête de mise en attente et la requête de recherche de contenu par un **opérateur AND.** Pour plus d’informations, voir Emplacements de recherche en [attente eDiscovery.](create-ediscovery-holds.md#search-locations-on-ediscovery-hold)
    
    - **Emplacements spécifiques**. Sélectionnez cette option pour sélectionner les boîtes aux lettres et les sites que vous souhaitez rechercher. Lorsque vous sélectionnez cette option et cliquez sur **Modifier,** une liste d’emplacements s’affiche. Vous pouvez choisir de rechercher un ou plusieurs utilisateurs, groupes, équipes ou emplacements de site. Vous pouvez également effectuer des recherches dans les dossiers publics de votre organisation.
    
      ![Sélectionner des emplacements spécifiques](../media/97469b15-7be1-4aee-be27-f8343636152c.png)
  
     Si vous sélectionnez cette option et que vous recherchez un emplacement de contenu en attente, toute requête d’une requête en attente de cas basée sur une requête ne sera pas appliquée à la requête de recherche. En d’autres termes, tout le contenu est recherché, et pas seulement le contenu qui est conservé par une conservation de cas basée sur une requête.

8. Après avoir sélectionné les emplacements de contenu à rechercher, cliquez sur **Terminé,** puis sur **Enregistrer.**

9. Dans la page **Nouvelle** recherche, cliquez sur **Enregistrer &'exécuter,** puis tapez un nom pour la recherche. Les recherches associées à un cas core eDiscovery doivent avoir des noms uniques au sein de votre organisation Office 365.

10. Cliquez **sur Enregistrer** pour enregistrer les paramètres de recherche et démarrer la recherche.

  Une fois la recherche terminée, vous pouvez prévisualiser les résultats de recherche. Si nécessaire, cliquez **sur Actualiser** sur la page **Recherches** pour afficher la recherche que vous avez créée dans la liste.

11. Cliquez sur la recherche pour afficher la page volante, qui contient des statistiques sur la recherche et pour effectuer d’autres tâches telles que l’affichage des statistiques de recherche et l’exportation des résultats de la recherche.

## <a name="more-information-about-searching-content-locations"></a>Plus d’informations sur la recherche d’emplacements de contenu

- Lorsque vous cliquez **sur Choisir des utilisateurs,** des groupes ou des équipes pour spécifier les boîtes aux lettres à rechercher, le soche de boîte aux lettres qui s’affiche est vide. Il s’agit d’une conception pour améliorer les performances. Pour ajouter des destinataires à cette liste, cliquez sur Choisir des **utilisateurs,** des groupes ou des équipes, tapez un nom (3 caractères au minimum) dans la zone de recherche, cochez la case en regard du nom, puis cliquez sur **Choisir.**

- Vous pouvez ajouter des boîtes aux lettres inactives, Microsoft Teams, des groupes Yammer, des groupes Office 365 et des groupes de distribution à la liste des boîtes aux lettres à rechercher. L’utilisation de groupes de distribution dynamique n’est pas prise en charge. Si vous ajoutez Microsoft Teams, Yammer groupes de messagerie ou Groupes Office 365, la boîte aux lettres de groupe ou d’équipe est recherché . les boîtes aux lettres des membres du groupe ne sont pas recherchés.

- Pour ajouter des sites, cliquez sur Choisir des **sites,** cliquez à nouveau sur Choisir **des sites,** puis tapez l’URL de chaque site que vous souhaitez rechercher. Vous pouvez également ajouter l’URL du site SharePoint pour une équipe Microsoft, un groupe Yammer ou un groupe Office 365.
