---
title: Afficher les statistiques de mot clé pour les résultats de recherche de contenu
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 1/30/2017
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.collection: M365-security-compliance
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 9701a024-c52e-43f0-b545-9a53478aec04
description: Découvrez comment utiliser la fonctionnalité Statistiques de recherche pour afficher et comparer des statistiques pour plusieurs recherches de contenu dans le Centre de sécurité & conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f7faf956aaec5619655818036b969086e0af0c6a
ms.sourcegitcommit: cbe8724bd71d1c002395d98f1451c5f578c824f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "49987829"
---
# <a name="view-keyword-statistics-for-content-search-results"></a>Afficher les statistiques de mot clé pour les résultats de recherche de contenu

Après avoir créé et exécuté une recherche de contenu, vous pouvez afficher des statistiques sur les résultats de recherche estimés. Cela inclut un résumé des résultats de recherche (semblable au résumé des résultats de recherche estimés affichés dans le volet d’informations), les statistiques de requête telles que le nombre d’emplacements de contenu avec des éléments qui correspondent à la requête de recherche et le nom des emplacements de contenu qui ont le plus d’éléments correspondants. Vous pouvez afficher les statistiques d’une ou plusieurs recherches de contenu. Cela vous permet de comparer rapidement les résultats de plusieurs recherches et de prendre des décisions sur l’efficacité de vos requêtes de recherche.
  
En outre, vous pouvez configurer des recherches nouvelles et existantes pour renvoyer des statistiques pour chaque mot clé dans une requête de recherche. Cela vous permet de comparer le nombre de résultats pour chaque mot clé dans une requête et de comparer les statistiques de mots clés de plusieurs recherches.
  
Vous pouvez également télécharger les statistiques de recherche et les statistiques de mots clés dans un fichier CSV. Cela vous permet d’utiliser les fonctionnalités de filtrage et de tri dans Excel pour comparer les résultats et préparer des rapports pour vos résultats de recherche.
  
## <a name="get-statistics-for-content-searches"></a>Obtenir des statistiques pour les recherches de contenu

Pour afficher des statistiques pour les recherches de contenu :
  
1. Dans le Centre de conformité Microsoft 365, go to **Show all**  >  **Content search**.

2. Dans la liste des recherches, sélectionnez au moins  deux recherches, puis cliquez sur Statistiques de recherche dans la page **volante Actions** en bloc.
    
    ![Sélectionner plusieurs recherches, puis cliquer sur Statistiques de recherche](../media/1195c6c3-2e00-469d-8c29-85c1c7ebe6c7.png)
  
3. Dans la page **Statistiques de** recherche, cliquez sur l’un des liens suivants pour afficher des statistiques sur les recherches sélectionnées. 
    
    **Summary**
    
    Cette page affiche des statistiques similaires à ceux affichés dans le volet d’informations de la page **de recherche de** contenu. Les statistiques de toutes les recherches sélectionnées sont affichées. Notez que vous pouvez également ré-exécuter les recherches sélectionnées à partir de cette page pour mettre à jour les statistiques. 
    
    ![Résumé des statistiques pour les recherches sélectionnées](../media/abb663eb-b3d6-4f4c-a99f-55d20b0848af.png)
  
    a.  Nom de la recherche de contenu. Comme indiqué précédemment, vous pouvez afficher et comparer des statistiques pour plusieurs recherches.
    
    b. Type d’emplacement de contenu recherché. Chaque ligne affiche des statistiques pour les boîtes aux lettres, les sites et les dossiers publics de la recherche spécifiée.
    
    c. Nombre d’emplacements de contenu contenant des éléments qui correspondent à la requête de recherche. Pour les boîtes aux lettres, cette statistique inclut également le nombre de boîtes aux lettres d’archivage qui contiennent des éléments qui correspondent à la requête de recherche.
    
    d. Nombre total d’éléments de tous les emplacements de contenu spécifiés qui correspondent à la requête de recherche. Les messages électroniques, les éléments de calendrier et les documents sont des exemples de types d’éléments. Si un élément contient plusieurs instances d’un mot clé recherché, il n’est compté qu’une seule fois dans le nombre total d’éléments. Par exemple, si vous recherchez des mots « stock » ou « fraude » et qu’un message électronique contient trois instances du mot « stock », il n’est compté qu’une seule fois dans la colonne **Éléments.** 
    
    e. Taille totale de tous les éléments trouvés à l’emplacement de contenu spécifié qui correspondent à la requête de recherche. 
    
    **Queries**
    
    Cette page affiche des statistiques sur la requête de recherche.
    
    ![Statistiques de requête de recherche pour les recherches sélectionnées](../media/dc817526-dfb9-43d3-a14c-4c58077eb7bb.png)
  
    a. Nom de la recherche de contenu pour qui la ligne contient des statistiques de requête.
    
    b. Type d’emplacement de contenu applicable aux statistiques de requête.
    
    c. Cette colonne indique la partie de la requête de recherche à laquelle les statistiques sont applicables. **Primary** indique l’intégralité de la requête de recherche. Si vous utilisez une liste de mots clés lorsque vous créez ou modifiez une requête de recherche, des statistiques pour chaque composant de la requête sont incluses dans ce tableau. Pour plus [d’informations,](#get-keyword-statistics-for-content-searches) voir la section Obtenir des statistiques sur les mots clés pour les recherches de contenu dans cet article. 
    
    d. Cette colonne contient la requête de recherche réelle qui est exécuté par l’outil de recherche de contenu. Notez que l’outil ajoute automatiquement quelques composants supplémentaires à la requête que vous créez. 

    - Lorsque vous recherchez tout le contenu des boîtes aux lettres (en ne spécifiant aucun mot clé), la requête de mot clé réelle est de sorte que tous les  `size>=0` éléments soient renvoyés. 
    
     - Lorsque vous recherchez des sites SharePoint Online et OneDrive Entreprise, les deux composants suivants sont ajoutés :
    
          **NOT IsExternalContent:1** : exclut tout contenu d’une organisation SharePoint sur site. 
    
          **NOT IsOneNotePage:1** - Exclut tous les fichiers OneNote, car il s’agit de doublons de tout document qui correspond à la requête de recherche. 

    
    e. Nombre d’emplacements de contenu (spécifiés par la colonne ** Type d’emplacement ** ) qui contiennent des éléments qui correspondent à la requête de recherche répertoriée dans la colonne **Requête.** 
    
    f. Nombre d’éléments (à partir de l’emplacement de contenu spécifié) qui correspondent à la requête de recherche répertoriée dans la **colonne Requête.** Comme indiqué précédemment, si un élément contient plusieurs instances d’un mot clé recherché, il n’est compté qu’une seule fois dans cette colonne. 
    
    g. Taille totale de tous les éléments trouvés (à l’emplacement de contenu spécifié) qui correspondent à la requête de recherche dans la **colonne Requête.** 
    
    **Emplacements principaux**
    
    Cette page affiche des statistiques sur le nombre d’éléments qui correspondent à la requête de recherche dans chaque emplacement de contenu recherché. Les 1 000 principaux emplacements sont affichés. Si vous affichez des statistiques pour plusieurs recherches, les 1 000 principaux emplacements pour chaque recherche sont affichés. Notez qu’un emplacement de contenu n’est pas inclus sur cette page s’il ne contient pas d’éléments qui correspondent à la requête de recherche.
    
    ![Statistiques sur le nombre d’éléments trouvés dans les emplacements de contenu qui ont fait l’objet d’une recherche](../media/35a820b0-85d9-45d1-9a0c-c74bec803e67.png)
  
    a. Nom de l’emplacement du contenu.
    
    b. Type d’emplacement de contenu applicable aux statistiques d’emplacement.
    
    c. Il existe des colonnes pour chaque recherche pour qui vous affichez des statistiques. Cette colonne indique le nombre (et la taille totale) des éléments qui correspondent à la requête de recherche à chaque emplacement de contenu. Notez que lorsque vous affichez des statistiques pour plusieurs recherches, le « NA » dans cette colonne indique que l’emplacement du contenu n’a pas été inclus dans cette recherche. 

## <a name="get-keyword-statistics-for-content-searches"></a>Obtenir des statistiques sur les mots clés pour les recherches de contenu

Comme expliqué précédemment, la page **Requêtes** affiche la requête de recherche et le nombre (et la taille) d’éléments qui correspondent à la requête. Si vous utilisez une liste de mots clés lorsque vous créez ou modifiez une requête de recherche, vous pouvez obtenir des statistiques améliorées qui indiquent le nombre d’éléments qui correspondent à chaque mot clé ou expression de mot clé. Cela peut vous aider à identifier rapidement les parties de la requête qui sont les plus (et les moins) efficaces. Par exemple, si un mot clé renvoie un grand nombre d’éléments, vous pouvez choisir d’affiner la requête de mot clé pour affiner les résultats de la recherche. Vous pouvez configurer une liste de mots clés lorsque vous créez ou modifiez une recherche de contenu. 

Pour créer une liste de mots clés et afficher des statistiques de mots clés pour une recherche de contenu :
  
1. Dans le Centre de conformité Microsoft 365, go to **Show all**  >  **Content search**.
    
2. Dans la liste des recherches de contenu, cliquez  sur une recherche, puis cliquez sur Modifier ![ l’icône ](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) Modifier.
    
3. Cliquez **sur Requête,** puis faites les choses suivantes : 
    
    ![Cliquez sur la case à cocher Afficher la liste des mots clés et tapez un mot clé dans chaque ligne](../media/73ef46dd-3d5c-415d-b5e7-c3559caaafe2.png)
  
    a. Cliquez sur la **case à cocher Afficher la liste des** mots clés. 
    
    b. Tapez une phase de mot clé ou de mot clé dans une ligne du tableau des mots clés. Par exemple, tapez **budget dans** la première ligne, puis tapez **sécurité** dans la deuxième ligne. 
    
4. Après avoir ajouté les mots clés que vous souhaitez rechercher et obtenir des statistiques, cliquez sur **Rechercher** pour exécuter la recherche révisée. 
    
5. Lorsque la recherche est terminée, sélectionnez-la dans  la liste des recherches, puis cliquez sur le bouton Statistiques de recherche des statistiques ![ de ](../media/9bf56d43-25bf-4f53-a4be-f4d55102310c.png) recherche. Vous pouvez également afficher et comparer des statistiques de mots clés pour plusieurs recherches.
    
6. Dans la page **Statistiques de** recherche, cliquez **sur Requête** pour afficher les statistiques de mot clé pour les recherches sélectionnées. 
    
    ![Les statistiques de chaque mot clé pour les recherches sélectionnées sont affichées](../media/e7910fa9-af93-4df9-92d0-e1e3e089e14f.png)
  
    Comme indiqué dans la capture d’écran précédente, les statistiques de chaque mot clé sont affichées . Cela inclut : 
    
    - Statistiques de mots clés pour chaque type d’emplacement de contenu inclus dans la recherche.
    
    - Requête de recherche réelle pour chaque mot clé, qui inclut toutes les conditions de la requête de recherche. 
    
    - Requête de recherche complète  (identifiée comme principale dans la colonne **Partie)** et statistiques de la requête complète. Notez que ces statistiques sont les mêmes que celles affichées sur la page **Résumé.** 

> [!NOTE]
> Pour réduire les problèmes causés par les grandes listes de mots clés, vous êtes maintenant limité à 20 lignes au maximum dans la liste des mots clés d’une requête de recherche.
