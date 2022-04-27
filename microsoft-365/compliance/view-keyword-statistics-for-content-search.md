---
title: Afficher les statistiques pour les résultats de la recherche eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.search: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
description: Découvrez comment utiliser la fonctionnalité de statistiques de recherche pour afficher des statistiques pour les recherches de contenu associées à un cas eDiscovery (Standard) dans le portail de conformité Microsoft Purview.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d96ad67a638ab3917743e64462debd9f2c94ef4d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092202"
---
# <a name="view-statistics-for-ediscovery-search-results"></a>Afficher les statistiques pour les résultats de la recherche eDiscovery

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Après avoir créé et exécuté une recherche de contenu ou une recherche associée à un cas Microsoft Purview eDiscovery (Standard), vous pouvez afficher des statistiques sur les résultats estimés de la recherche. Cela inclut un résumé des résultats de la recherche (semblable au résumé des résultats de recherche estimés affichés dans la page de menu volant de recherche), les statistiques de requête telles que le nombre d’emplacements de contenu avec des éléments qui correspondent à la requête de recherche et l’identité des emplacements de contenu qui ont les éléments les plus correspondants.
  
En outre, vous pouvez utiliser la liste de mots clés pour configurer une recherche afin de retourner des statistiques pour chaque mot clé dans une requête de recherche. Cela vous permet de comparer le nombre de résultats retournés par chaque mot clé dans une requête.
  
Vous pouvez également télécharger des statistiques de recherche dans un fichier CSV. Cela vous permet d’utiliser les fonctionnalités de filtrage et de tri dans Excel pour comparer les résultats et préparer des rapports pour vos résultats de recherche.
  
## <a name="get-statistics-for-searches"></a>Obtenir des statistiques pour les recherches

Pour afficher les statistiques d’une recherche de contenu ou d’une recherche associée à un cas eDiscovery (Standard) :
  
1. Dans le portail de conformité Microsoft Purview, cliquez sur **Afficher tout**, puis effectuez l’une des opérations suivantes :

   - Cliquez sur **Recherche de contenu** , puis sélectionnez une recherche pour afficher la page de menu volant.

     OR

   - Cliquez sur **eDiscoveryCore** > , sélectionnez un cas, puis sélectionnez une recherche sous l’onglet **Recherches** pour afficher la page de menu volant.

2. Dans la page volante de la recherche sélectionnée, cliquez sur l’onglet **Statistiques de la recherche** .
  
   ![Onglet Statistiques de recherche.](../media/SearchStatistics1.png)

L’onglet Statistiques de recherche contient **les sections suivantes** qui contiennent différents types de statistiques sur la recherche.

### <a name="search-content"></a>Rechercher du contenu

Cette section affiche un résumé graphique des éléments estimés retournés par la recherche. Cela indique le nombre d’éléments qui correspondent aux critères de recherche. Ces informations vous donnent une idée du nombre estimé d’éléments retournés par la recherche.

![Estimations de recherche pour une recherche.](../media/SearchContentReport.png)

- **Éléments estimés par emplacement :** nombre total d’éléments estimés retournés par la recherche. Le nombre spécifique d’éléments situés dans les boîtes aux lettres et situés dans des sites est également affiché.

- **Emplacements estimés avec accès** : nombre total d’emplacements de contenu qui contiennent des éléments retournés par la recherche. Le nombre spécifique de boîtes aux lettres et d’emplacements de site s’affiche également.

- **Volume de données par emplacement (en Mo)** : taille totale de tous les éléments estimés retournés par la recherche. La taille spécifique des éléments de boîte aux lettres et des éléments de site s’affiche également.

### <a name="condition-report"></a>Rapport de condition

Cette section affiche des statistiques sur la requête de recherche et le nombre d’éléments estimés correspondant à différentes parties de la requête de recherche. Vous pouvez utiliser ces statistiques pour analyser le nombre d’éléments qui correspondent à chaque composant de la requête de recherche. Cela peut vous aider à affiner les critères de recherche et, si nécessaire, à affiner l’étendue de l’étendue. Vous pouvez également télécharger une copie de ce rapport au format CSV.

![Rapport de condition.](../media/SearchContentReportNoKeywordList.png)

- **Type d’emplacement** : type d’emplacement de contenu auquel les statistiques de requête s’appliquent. La valeur de **Exchange** indique un emplacement de boîte aux lettres ; une valeur de **SharePoint** indique un emplacement de site.

- **Partie** : partie de la requête de recherche à qui les statistiques s’appliquent. **Primary** indique l’intégralité de la requête de recherche. **Le mot clé** indique que les statistiques de la ligne concernent un mot clé spécifique. Si vous utilisez une liste de mots clés pour la requête de recherche, les statistiques de chaque composant de la requête sont incluses dans ce tableau. Pour plus d’informations, consultez [Obtenir les statistiques des mots clés pour les recherches](#get-keyword-statistics-for-searches).

- **Condition** : composant réel (mot clé ou condition) de la requête de recherche qui a retourné les statistiques affichées dans la ligne correspondante.

- **Emplacements avec accès** : nombre d’emplacements de contenu (spécifiés par la colonne Type **d’emplacement** ) qui contiennent des éléments qui correspondent à la requête principale ou de mot clé répertoriée dans la colonne **Condition** .

- **Éléments** : nombre d’éléments (à partir de l’emplacement de contenu spécifié) qui correspondent à la requête répertoriée dans la colonne **Condition** . Comme expliqué précédemment, si un élément contient plusieurs instances d’un mot clé recherché, il n’est compté qu’une seule fois dans cette colonne.

- **Taille (Mo)** : taille totale de tous les éléments trouvés (à l’emplacement de contenu spécifié) qui correspondent à la requête de recherche dans la colonne **Condition** .

### <a name="top-locations"></a>Emplacements principaux

Cette section affiche des statistiques sur les emplacements de contenu spécifiques avec le plus d’éléments renvoyés par la recherche. Les 1 000 principaux emplacements sont affichés. Vous pouvez également télécharger une copie de ce rapport au format CSV.

- Nom du nom de l’emplacement (adresse e-mail des boîtes aux lettres et URL des sites).

- Type d’emplacement (boîte aux lettres ou site).

- Nombre estimé d’éléments dans l’emplacement de contenu retourné par la recherche.

- Taille totale des éléments estimés dans chaque emplacement de contenu.

## <a name="get-keyword-statistics-for-searches"></a>Obtenir des statistiques de mots clés pour les recherches

Comme expliqué précédemment, la section **Rapport de condition** affiche la requête de recherche et le nombre (et la taille) des éléments qui correspondent à la requête. Si vous utilisez une liste de mots clés lorsque vous créez ou modifiez une requête de recherche, vous pouvez obtenir des statistiques améliorées qui indiquent le nombre d’éléments correspondant à chaque mot clé ou expression de mot clé. Cela peut vous aider à identifier rapidement les parties de la requête les plus efficaces (et les moins efficaces). Par exemple, si un mot clé retourne un grand nombre d’éléments, vous pouvez choisir d’affiner la requête de mot clé pour affiner les résultats de la recherche.

Pour créer une liste de mots clés et afficher des statistiques de mots clés pour une recherche :
  
1. Dans le portail de conformité, créez une recherche de contenu ou une recherche associée à un cas eDiscovery (Standard).

2. Dans la page **Conditions** de l’Assistant Recherche. cochez la case **Afficher la liste de mots clés** .

   ![Case à cocher Afficher la liste des mots clés.](../media/SearchKeywordsList1.png)

3. Tapez un mot clé ou une phase de mot clé dans une ligne dans la table de mots clés. Par exemple, tapez **budget** dans la première ligne, tapez **sécurité** dans la deuxième ligne et **tapez FY2021** dans la troisième ligne.

   ![Tapez jusqu’à 20 mots clés ou expressions clés dans la liste.](../media/SearchKeywordsList2.png)

   > [!NOTE]
   > Pour réduire les problèmes causés par les listes de mots clés volumineux, vous êtes limité à un maximum de 20 lignes dans la liste de mots clés d’une requête de recherche.

4. Après avoir ajouté les mots clés à la liste pour laquelle vous souhaitez rechercher et obtenir des statistiques, exécutez la recherche.

5. Une fois la recherche terminée, sélectionnez-la pour afficher la page de menu volant.

6. Sous l’onglet **Statistiques** de recherche, cliquez sur le **rapport Condition** pour afficher les statistiques de mot clé pour la recherche.

    ![Les statistiques de chaque mot clé sont affichées.](../media/SearchKeywordsList3.png)
  
    Comme indiqué dans la capture d’écran précédente, les statistiques de chaque mot clé sont affichées ; Cela inclut :

    - Statistiques des mots clés pour chaque type d’emplacement de contenu inclus dans la recherche.

    - Nombre d’éléments de boîte aux lettres non indexés.

    - Requête de recherche et résultats réels pour chaque mot clé (identifié comme **mot clé** dans la colonne **Partie** ), qui inclut toutes les conditions de la requête de recherche.

    - La requête de recherche complète (identifiée comme **primaire** dans la colonne **Part** ) et les statistiques de la requête complète pour chaque type d’emplacement. Notez qu’il s’agit des mêmes statistiques que celles affichées sous l’onglet **Résumé** .
