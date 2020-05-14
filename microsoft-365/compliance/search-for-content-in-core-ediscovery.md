---
title: Rechercher du contenu dans un cas de découverte électronique principale
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
description: Vous pouvez rechercher du contenu qui peut être pertinent à un cas de découverte électronique de base.
ms.openlocfilehash: d17a9d16643ec9077e02b5438597237b80f09af5
ms.sourcegitcommit: 6007dbe2cf758c683de399f94023122c678bcada
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "44224621"
---
# <a name="search-for-content-in-a-core-ediscovery-case"></a>Rechercher du contenu dans un cas de découverte électronique principale

Une fois qu’un cas de découverte électronique de base est créé et que les personnes concernées par le cas sont placées en conservation, vous pouvez créer et exécuter une ou plusieurs recherches pour le contenu pertinent pour le cas. Les recherches associées à un cas de découverte électronique principale ne sont pas indiquées sur la page de **recherche de contenu** dans le centre de conformité Microsoft 365. Ces recherches sont répertoriées dans la page **recherches** du cas EDiscover de base dans laquelle les recherches sont associées. Cela signifie également que les recherches associées à un cas sont accessibles uniquement par les membres du cas.

Pour créer une recherche de découverte électronique principale :
  
1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) et connectez-vous à l’aide des informations d’identification du compte d’utilisateur auquel ont été attribuées les autorisations eDiscovery appropriées.

2. Dans le volet de navigation de gauche du centre de conformité Microsoft 365, cliquez sur **Afficher tout**, puis sur **découverte électronique > Core**.

3. Sur la page de **découverte électronique principale** , sélectionnez le cas pour lequel vous souhaitez créer une recherche associée, puis cliquez sur **ouvrir le cas**.

4. Sur la page d' **Accueil** de l’incident, cliquez sur l’onglet **recherches** .
  
5. Sur la page **recherche** , cliquez sur **nouvelle recherche**.

6. Sur la page **Nouvelle recherche**, vous pouvez ajouter des mots clés et des conditions pour créer la requête de recherche. 

    ![Nouvelle recherche](../media/0e9954e7-c0ea-4e05-820b-e4b81dc5f81d.png)
  
   a. Vous pouvez spécifier des mots clés, des propriétés de message, telles que des dates d’envoi et de réception, ou des propriétés de document, telles que des noms de fichiers ou la date de la dernière modification d’un document. Vous pouvez utiliser des requêtes plus complexes qui utilisent un opérateur booléen, comme **and**, **or**, **not**ou **near**. Vous pouvez également rechercher des informations sensibles (des numéros de sécurité sociale, par exemple) dans des documents ou rechercher des documents qui ont été partagés en externe. Si vous laissez la zone mot clé vide, tout le contenu situé dans les emplacements de contenu spécifiés sera inclus dans les résultats de la recherche.

   b. Vous pouvez activer la case à cocher **afficher la liste des mots clés** et taper un mot clé dans chaque ligne. Dans ce cas, les mots clés de chaque ligne sont connectés par l’opérateur **or** dans la requête de recherche qui est créée. Vous pouvez entrer un maximum de 20 Mots clés dans la liste.

    ![Liste de mots clés](../media/29cceb5d-2817-4fc4-b91a-ced1c5824a17.png)
  
    Pourquoi utiliser la liste de mots clés ? Vous pouvez obtenir des statistiques qui indiquent le nombre d’éléments qui correspondent à chaque mot clé. Cela peut vous aider à identifier rapidement les mots clés les plus importants (et les moins). Vous pouvez également utiliser une expression de mot clé (entre parenthèses) dans une ligne. Pour plus d’informations sur les statistiques de recherche, voir [afficher les statistiques des mots clés pour les résultats de recherche de contenu](view-keyword-statistics-for-content-search.md).

    Pour plus d’informations sur l’utilisation de la liste des mots clés, voir [création d’une requête de recherche](content-search.md#building-a-search-query).

   c. Vous pouvez cliquer sur **conditions** et ajouter des conditions à une requête de recherche pour affiner une recherche et renvoyer un ensemble de résultats plus raffiné. Chaque condition ajoute une clause à la requête de recherche KQL créée et exécutée lors du démarrage de la recherche. Une condition est logiquement connectée à la requête de mot clé (spécifiée dans la zone du mot clé) par l’opérateur **AND** . Cela signifie que les éléments doivent répondre à la fois à la requête de mot clé et à chaque condition à inclure dans les résultats. C’est ainsi que les conditions contribuent à affiner vos résultats.

    Pour plus d’informations sur la création d’une requête de recherche et l’utilisation de conditions, voir [Keyword queries for Content Search](keyword-queries-and-search-conditions.md).

7. Sous **emplacements : emplacements en attente**, choisissez les emplacements de contenu sur lesquels vous souhaitez effectuer la recherche. Vous pouvez rechercher des boîtes aux lettres, des sites et des dossiers publics dans la même recherche.

    ![Emplacements, en attente](../media/d56398aa-0b20-4500-8e26-494eab92a99f.png)
  
    - **Tous les emplacements**. Sélectionnez cette option pour rechercher tous les emplacements de contenu de votre organisation. Lorsque vous sélectionnez cette option, vous pouvez choisir d’effectuer une recherche dans toutes les boîtes aux lettres Exchange (qui inclut les boîtes aux lettres de tous les groupes Microsoft Teams, Yammer Groups et Office 365), tous les sites SharePoint et OneDrive entreprise (qui incluent les sites de tous les groupes Microsoft Teams, Yammer Groups et Office 365), ainsi que tous les dossiers publics.
    
    - **Tous les emplacements en attente**. Sélectionnez cette option pour rechercher tous les emplacements de contenu qui ont été mis en attente eDiscovery dans le cas. Si le cas contient plusieurs suspensions, les emplacements de contenu de toutes les suspensions feront l’objet d’une recherche. En outre, si un emplacement de contenu a été placé sur une conservation basée sur une requête, seuls les éléments en attente feront l’objet d’une recherche lors de l’exécution de la recherche de contenu que vous créez au cours de cette étape. Par exemple, si un utilisateur a été placé sur une conservation de casse basée sur une requête qui conserve les éléments qui ont été envoyés ou créés avant une date spécifique, seuls ces éléments seraient recherchés. Pour ce faire, vous connectez la requête de suspension de la casse et la requête de recherche de contenu par un opérateur **and** . Pour plus d’informations, consultez la rubrique [emplacements de recherche sur le blocage eDiscovery](create-ediscovery-holds.md#search-locations-on-ediscovery-hold).
    
    - **Emplacements spécifiques**. Sélectionnez cette option pour sélectionner les boîtes aux lettres et les sites dans lesquels vous souhaitez effectuer une recherche. Lorsque vous sélectionnez cette option et que vous cliquez sur **modifier**, une liste d’emplacements apparaît. Vous pouvez choisir d’effectuer une recherche sur un ou l’ensemble des utilisateurs, des groupes, des équipes ou des emplacements de site. Vous pouvez également effectuer des recherches dans les dossiers publics de votre organisation.
    
      ![Sélectionner des emplacements spécifiques](../media/97469b15-7be1-4aee-be27-f8343636152c.png)
  
     Si vous sélectionnez cette option et que vous recherchez tout emplacement de contenu en conservation, aucune requête d’une conservation de casse basée sur une requête ne sera appliquée à la requête de recherche. En d’autres termes, tout le contenu fait l’objet d’une recherche, pas seulement du contenu conservé par une suspension de casse basée sur une requête.

8. Une fois que vous avez sélectionné les emplacements de contenu à rechercher, cliquez sur **Terminer** , puis sur **Enregistrer**.

9. Sur la page **nouvelle recherche** , cliquez sur **Enregistrer & exécuter** , puis tapez un nom pour la recherche. Les recherches associées à un cas de découverte électronique principale doivent avoir des noms uniques au sein de votre organisation Office 365.

10. Cliquez sur **Enregistrer** pour enregistrer les paramètres de recherche et lancer la recherche.

  Une fois la recherche terminée, vous pouvez prévisualiser les résultats de recherche. Si nécessaire, cliquez sur **Actualiser** sur la page **recherches** pour afficher la recherche que vous avez créée dans la liste.

11. Cliquez sur la recherche pour afficher la page de menu volant, qui contient des statistiques sur la recherche et d’effectuer d’autres tâches, telles que l’affichage des statistiques de recherche et l’exportation des résultats de la recherche.

## <a name="more-information-about-searching-content-locations"></a>Plus d’informations sur la recherche d’emplacements de contenu

- Lorsque vous cliquez sur **choisir les utilisateurs, les groupes ou les équipes** pour spécifier les boîtes aux lettres à rechercher, le sélecteur de boîtes aux lettres affiché est vide. Il s’agit d’une conception qui améliore les performances. Pour ajouter des destinataires à cette liste, cliquez sur **choisir les utilisateurs, les groupes ou les équipes**, tapez un nom (un minimum de 3 caractères) dans la zone de recherche, activez la case à cocher en regard du nom, puis cliquez sur **choisir**.

- Vous pouvez ajouter des boîtes aux lettres inactives, Microsoft Teams, des groupes Yammer, des groupes Office 365 et des groupes de distribution à la liste des boîtes aux lettres à rechercher. L’utilisation de groupes de distribution dynamique n’est pas prise en charge. Si vous ajoutez des groupes Microsoft Teams, Yammer ou Office 365, la boîte aux lettres de groupe ou d’équipe fait l’objet d’une recherche ; les boîtes aux lettres des membres du groupe ne sont pas recherchées.

- Pour ajouter des sites, cliquez sur **choisir des sites**, cliquez sur **choisir des sites** , puis tapez l’URL de chaque site sur lequel vous souhaitez effectuer la recherche. Vous pouvez également ajouter l’URL du site SharePoint pour une équipe Microsoft, un groupe Yammer ou un groupe Office 365.
