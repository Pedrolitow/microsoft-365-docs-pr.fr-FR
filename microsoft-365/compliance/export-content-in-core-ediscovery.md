---
title: Exporter et télécharger du contenu à partir d’un cas de découverte électronique principale
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
description: Cet article explique comment exporter et télécharger du contenu à partir d’un cas de découverte électronique de base.
ms.openlocfilehash: 30fc30943bd570cf4d79ce88b5bef5836b3dfe14
ms.sourcegitcommit: 222fb7fe2b26dde3d8591b61cc02113d6135012c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "49760298"
---
# <a name="export-content-from-a-core-ediscovery-case"></a>Exportation de contenu à partir d’un cas de découverte électronique principale

Une fois la recherche exécutée, vous pouvez exporter les résultats de la recherche. Lorsque vous exportez des résultats de recherche, les éléments de boîte aux lettres sont téléchargés dans des fichiers PST ou des messages individuels. Lorsque vous exportez du contenu à partir de sites SharePoint et OneDrive entreprise, des copies de documents Office natifs et d’autres documents sont exportées. Un fichier de Results.csv qui contient des informations sur chaque élément exporté et un fichier manifeste (au format XML) contenant des informations sur chaque résultat de recherche est également exporté.
  
Vous pouvez exporter les résultats d’une [seule recherche associée à un cas](#export-the-results-of-a-single-search) ou vous pouvez exporter les résultats de [plusieurs recherches associées à un cas](#export-the-results-of-multiple-searches).
  
## <a name="export-the-results-of-a-single-search"></a>Exporter les résultats d’une recherche unique

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) et connectez-vous à l’aide des informations d’identification du compte d’utilisateur auquel ont été attribuées les autorisations eDiscovery appropriées.

2. Dans le volet de navigation de gauche du centre de conformité Microsoft 365, cliquez sur **Afficher tout**, puis sur **découverte électronique > Core**.

3. Sur la page de **découverte électronique principale** , sélectionnez l’incident à partir duquel vous souhaitez exporter les résultats de recherche, puis cliquez sur **ouvrir le cas**.

4. Sur la page d' **Accueil** de l’incident, cliquez sur l’onglet **recherches** .

5. Dans la liste des recherches pour le cas, cliquez sur la recherche à partir de laquelle vous souhaitez exporter les résultats de recherche, puis cliquez sur **Exporter les résultats** dans la fenêtre mobile.

    La page **Exporter les résultats** s’affiche. 

    ![Page exporter les résultats](../media/ab0bb46d-310b-4374-8644-717146df6676.png)
  
    Le flux de travail pour exporter les résultats d’une recherche associée à un cas de découverte électronique principale est le même que pour l’exportation des résultats de recherche pour une recherche sur la page de **recherche de contenu** . Pour obtenir des instructions détaillées, voir [Export content Search Results](export-search-results.md).

    > [!NOTE]
    > Lorsque vous exportez des résultats de recherche, vous avez la possibilité d’activer la déduplication de sorte qu’une seule copie d’un message électronique soit exportée même si plusieurs instances du même message ont pu être trouvées dans les boîtes aux lettres qui ont été recherchées. Pour plus d’informations sur la déduplication et sur l’identification des éléments dupliqués, voir [déduplication dans les résultats de recherche de découverte électronique](de-duplication-in-ediscovery-search-results.md).

    Une fois que vous avez démarré l’exportation, les résultats de la recherche sont préparés pour le téléchargement, ce qui signifie qu’ils sont téléchargés vers un emplacement de stockage Azure fourni par Microsoft dans le Cloud Microsoft.
  
6. Cliquez sur l’onglet **Exporter** pour afficher la liste des travaux d’exportation pour le cas.
  
    Vous devrez peut-être cliquer sur **Actualiser** pour mettre à jour la liste des travaux d’exportation afin qu’elle affiche la tâche d’exportation que vous avez créée. Les travaux d’exportation portent le même nom que la recherche correspondante, avec des **_Export** ajoutés au nom de la recherche.

7. Cliquez sur le travail d’exportation que vous avez créé pour afficher les informations d’État sur la page de menu volant. Ces informations incluent le pourcentage d’éléments qui ont été transférés vers l’emplacement de stockage Azure.

8. Une fois que tous les éléments ont été transférés, cliquez sur **Télécharger les résultats** pour télécharger les résultats de la recherche sur votre ordinateur local. Pour plus d’informations sur le téléchargement des résultats de recherche, voir l’étape 2 dans [exporter des résultats de recherche de contenu](export-search-results.md#step-2-download-the-search-results)

## <a name="export-the-results-of-multiple-searches"></a>Exporter les résultats de plusieurs recherches

En guise d’alternative à l’exportation des résultats d’une recherche unique associée à un cas, vous pouvez exporter les résultats de plusieurs recherches à partir de la même casse dans une seule tâche d’exportation. L’exportation des résultats de plusieurs recherches est plus rapide et plus facile que l’exportation des résultats d’une recherche à la fois.
  
> [!NOTE]
> Vous ne pouvez pas exporter les résultats de plusieurs recherches si l’une de ces recherches a été configurée sur des emplacements de recherche en attente.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) et connectez-vous à l’aide des informations d’identification du compte d’utilisateur auquel ont été attribuées les autorisations eDiscovery appropriées.

2. Dans le volet de navigation de gauche du centre de conformité Microsoft 365, cliquez sur **Afficher tout**, puis sur **découverte électronique > Core**.

3. Sur la page de **découverte électronique principale** , sélectionnez l’incident à partir duquel vous souhaitez exporter les résultats de recherche, puis cliquez sur **ouvrir le cas**.

4. Sur la page d' **Accueil** de l’incident, cliquez sur l’onglet **recherches** .
    
5. Dans la liste des recherches pour le cas, activez la case à cocher en regard de deux ou plusieurs recherches dont vous souhaitez exporter les résultats de recherche. 

   La page de menu volant des **actions en bloc** s’affiche. 

    ![Dans la page actions en bloc, cliquez sur Exporter les résultats](../media/f34e3707-a9c1-494f-91a4-da1165aa730a.png)
  
6. Cliquez sur **Exporter les résultats**.

   La page **Exporter les résultats** s’affiche. 

    ![Page exporter les résultats](../media/ab0bb46d-310b-4374-8644-717146df6676.png)
  
    À ce stade, le flux de travail pour exporter les résultats de plusieurs recherches associées à un cas de découverte électronique principale est le même que pour l’exportation des résultats de recherche pour une seule recherche. Voir l’étape 5 de la section précédente.

### <a name="more-information-about-exporting-the-results-of-multiple-searches"></a>Plus d’informations sur l’exportation des résultats de plusieurs recherches

- Lorsque vous exportez les résultats de plusieurs recherches, les requêtes de recherche de toutes les recherches sont combinées à l’aide d’opérateurs **or** , puis la recherche combinée est démarrée. Les résultats estimés de la recherche combinée sont affichés dans la page de sélection de la tâche d’exportation sélectionnée. Les résultats de la recherche sont ensuite copiés dans l’emplacement de stockage Azure dans le Cloud Microsoft. L’état de la tâche de copie s’affiche également sur la page de menu volant. Comme indiqué précédemment, une fois tous les résultats de la recherche copiés, vous pouvez les télécharger sur un ordinateur local.

- Le nombre maximal de mots clés dans les requêtes pour toutes les recherches que vous souhaitez exporter est 500. Il s’agit de la même limite pour une seule recherche. Cela est dû au fait que le travail d’exportation combine toutes les requêtes de recherche à l’aide de l’opérateur **or** . Si vous dépassez cette limite, une erreur est renvoyée. Dans ce cas, vous devez exporter les résultats à partir d’un nombre réduit de recherches ou simplifier les requêtes de recherche des recherches d’origine que vous souhaitez exporter.

- Les résultats de recherche exportés sont organisés par l’emplacement de contenu dans lequel l’élément a été trouvé. Cela signifie qu’un emplacement de contenu dans les résultats d’exportation peut avoir des éléments renvoyés par des recherches différentes. Par exemple, si vous choisissez d’exporter les messages électroniques dans un fichier PST pour chaque boîte aux lettres, le fichier PST peut avoir des résultats provenant de plusieurs recherches.

- Si le même élément ou document de courrier à partir du même emplacement de contenu est renvoyé par plusieurs des recherches que vous exportez, seule une copie de l’élément sera exportée.

- Vous ne pouvez pas modifier une exportation pour plusieurs recherches une fois que vous l’avez créée. Par exemple, vous ne pouvez pas ajouter ou supprimer des recherches à partir de la tâche d’exportation. Vous devez créer une tâche d’exportation pour modifier les résultats de la recherche qui sont exportés. Une fois qu’une tâche d’exportation est créée, vous pouvez uniquement télécharger les résultats sur un ordinateur, redémarrer l’exportation ou supprimer le travail d’exportation.

- Si vous redémarrez l’exportation, toute modification apportée aux requêtes des recherches qui composent la tâche d’exportation n’affecte pas les résultats de la recherche qui sont extraits. Lorsque vous redémarrez une exportation, le même travail de requête de recherche combiné qui a été exécuté lors de la création du travail d’exportation sera réexécuté.

- En outre, si vous redémarrez une exportation, les résultats de la recherche copiés dans l’emplacement de stockage Azure remplacent les résultats précédents. Les résultats précédents qui ont été copiés ne peuvent pas être téléchargés.
