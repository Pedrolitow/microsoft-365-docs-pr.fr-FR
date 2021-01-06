---
title: Différences entre les résultats de recherche de découverte électronique estimée et réelle
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: 8f20ca4f-a908-46ec-99e6-9890d269ecf2
description: Comprendre pourquoi les résultats de recherche estimés et réels peuvent varier en fonction des recherches exécutées avec les outils eDiscovery dans Office 365.
ms.openlocfilehash: a5a66e070bf41cf6b3263dbae1e6ac5d136d9465
ms.sourcegitcommit: 222fb7fe2b26dde3d8591b61cc02113d6135012c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "49760252"
---
# <a name="differences-between-estimated-and-actual-ediscovery-search-results"></a>Différences entre les résultats de recherche de découverte électronique estimée et réelle

Cette rubrique s’applique aux recherches que vous pouvez exécuter à l’aide de l’un des outils eDiscovery Microsoft 365 suivants : 

- Recherche de contenu
- Core eDiscovery 
   
Lorsque vous exécutez une recherche de découverte électronique, l’outil que vous utilisez renvoie une estimation du nombre d’éléments (et leur taille totale) correspondant aux critères de recherche. Par exemple, lorsque vous effectuez une recherche dans le centre de conformité Microsoft 365, les résultats de recherche estimés s’affichent sur la page de menu volant de la recherche sélectionnée.
  
![Estimation des résultats affichés dans le volet de détails de la recherche sélectionnée](../media/74e4ce83-40be-41a9-b60f-5ad447e79fe4.png)
  
Il s’agit de la même estimation de la taille totale et du nombre d’éléments affichés dans l’outil d’exportation de découverte électronique lorsque vous exportez les résultats vers un ordinateur local et dans le rapport de synthèse d’exportation téléchargé avec les résultats de la recherche.
  
**Résultats estimés dans l’outil d’exportation de découverte électronique**

![Résultats estimés dans l’outil d’exportation eDiscovery](../media/d34312a5-0ee6-49aa-9460-7ea0015a6e66.png)
  
**Résultats estimés dans le rapport de synthèse d’exportation**

![Les résultats de recherche estimés sont inclus dans le rapport Résumé d’exportation](../media/44b579da-86c2-4f33-81b5-84d604003eda.png)
  
Toutefois, comme vous pouvez le constater dans la capture d’écran précédente du rapport Résumé de l’exportation, la taille et le nombre de résultats de recherche réels téléchargés diffèrent de la taille et du nombre de résultats de recherche estimés.
  
![Différence entre les résultats de recherche estimés et téléchargés](../media/84aef318-230f-430d-9d9e-02f21342d364.png)
  
Voici les raisons de ces différences :
  
- **La manière dont les résultats sont estimés**. Une estimation des résultats de la recherche est juste, une estimation (et non un nombre réel) des éléments qui répondent aux critères de requête de recherche. Pour compiler l’estimation des éléments Exchange, une liste des ID de message correspondant aux critères de recherche est demandée à partir de la base de données Exchange par l’outil eDiscovery que vous utilisez. Toutefois, lorsque vous exportez les résultats de la recherche, la recherche est réexécutée et les messages réels sont extraits de la base de données Exchange. Par conséquent, ces différences peuvent résulter de la manière dont le nombre d’éléments estimé et le nombre réel d’éléments sont déterminés.

- **Modifications qui se produisent entre le moment où vous évaluez et exportez les résultats** de la recherche. Lorsque vous exportez les résultats de la recherche, la recherche est redémarrée pour collecter les éléments les plus récents dans l’index de recherche qui répondent aux critères de recherche. Il est possible que des éléments supplémentaires ont été créés, envoyés ou reçus et répondent aux critères de recherche entre le moment où les résultats de la recherche estimés ont été collectés et le moment où les résultats de la recherche ont été exportés. Il est également possible que les éléments qui se trouvaient dans l’index de recherche lorsque les résultats de la recherche étaient estimés ne soient plus présents, car ils ont été supprimés de l’emplacement du contenu avant l’exportation des résultats de la recherche. Pour atténuer ce problème, vous pouvez spécifier une plage de dates pour une recherche de découverte électronique. Une autre méthode consiste à placer un blocage sur les emplacements de contenu afin que les éléments soient conservés et ne peuvent pas être purgés. 

   Bien que rare, même si une conservation est appliquée, la maintenance des éléments de calendrier intégrés (qui ne sont pas modifiables par l’utilisateur, mais qui sont inclus dans de nombreux résultats de recherche) peut être supprimée de temps en temps. Cette suppression périodique des éléments de calendrier entraîne l’exportation de moins d’éléments.

- **Éléments non indexés**. Les éléments non indexés pour la recherche peuvent entraîner des différences entre les résultats de recherche estimés et les résultats de recherche réels. Vous pouvez inclure des éléments non indexés lorsque vous exportez les résultats de la recherche. Si vous incluez des éléments non indexés lors de l’exportation des résultats de la recherche, d’autres éléments sont peut-être exportés. Cela entraîne une différence entre les résultats de recherche estimés et exportés.

    Lorsque vous utilisez l’outil de recherche de contenu, vous avez la possibilité d’inclure des éléments non indexés dans l’estimation de la recherche. Le nombre d’éléments non indexés renvoyés par la recherche est affiché sur la page de menu volant avec les autres résultats de recherche estimés. Tous les éléments non indexés seraient également inclus dans la taille totale des résultats de recherche estimés. Lorsque vous exportez des résultats de recherche, vous avez la possibilité d’inclure ou de ne pas inclure les éléments non indexés. La manière dont vous configurez ces options peut entraîner des différences entre les résultats de recherche estimés et ceux qui sont téléchargés.

- **Exportation des résultats d’une recherche de contenu qui inclut tous les emplacements de contenu**. Si la recherche à partir de laquelle vous exportez les résultats est une recherche de tous les emplacements de contenu de votre organisation, seuls les éléments non indexés des emplacements de contenu contenant des éléments qui correspondent aux critères de recherche seront exportés. In other words, if no search results are found in a mailbox or site, then any unindexed items in that mailbox or site won't be exported. Toutefois, les éléments non indexés de tous les emplacements de contenu (même ceux qui ne contiennent pas d’éléments qui correspondent à la requête de recherche) sont inclus dans les résultats de recherche estimés.

    Par ailleurs, si la recherche dont vous exportez les résultats à partir d’emplacements de contenu spécifiques inclus, les éléments non indexés (qui ne sont pas exclus par les critères de recherche) de tous les emplacements de contenu spécifiés dans la recherche seront exportés. Dans ce cas, le nombre estimé d’éléments non indexés et le nombre d’éléments non indexés exportés doivent être identiques.

    La raison de l’impossibilité d’exporter des éléments non indexés de tous les emplacements de l’organisation est qu’elle augmente la probabilité d’erreurs d’exportation et augmente le temps nécessaire pour exporter et télécharger les résultats de la recherche.

- **Formats de fichiers bruts et formats de fichier exportés**. Pour les éléments Exchange, la taille estimée des résultats de recherche est calculée à l’aide de la taille des messages Exchange bruts. Toutefois, les messages électroniques sont exportés dans un fichier PST ou sous forme de messages individuels (qui sont mis en forme en tant que fichiers EML). Ces deux options d’exportation utilisent un autre format de fichier que les messages Exchange bruts, ce qui a pour effet que la taille totale du fichier exporté est différente de la taille estimée du fichier.

- **Versions de document**. Pour les documents SharePoint, plusieurs versions d’un document ne sont pas incluses dans les résultats de recherche estimés. Toutefois, vous avez la possibilité d’inclure toutes les versions de document lorsque vous exportez les résultats de la recherche, ce qui augmente le nombre réel (et la taille totale) des documents exportés. 

- **Déduplication**. Pour les éléments Exchange, la déduplication réduit le nombre d’éléments exportés. Vous avez la possibilité de dédupliquer les résultats de la recherche lorsque vous les exportez. Pour les messages Exchange, cela signifie qu’une seule instance d’un message est exportée, même si ce message est susceptible d’être trouvé dans plusieurs boîtes aux lettres. Les résultats de recherche estimés incluent chaque instance d’un message. Par conséquent, si vous choisissez l’option de déduplication lors de l’exportation des résultats de recherche, le nombre réel d’éléments exportés peut être considérablement inférieur au nombre estimé d’éléments.

    Une autre chose à garder à l’esprit si vous choisissez l’option de déduplication est que tous les éléments Exchange sont exportés dans un fichier PST unique et que la structure de dossiers des boîtes aux lettres source n’est pas conservée. Le fichier PST exporté contient simplement les éléments de courrier électronique. Toutefois, un rapport de résultats de recherche contient une entrée pour chaque message exporté qui identifie la boîte aux lettres source où se trouve le message. Cela vous permet d’identifier toutes les boîtes aux lettres qui contiennent un message en double. Si vous n'activez pas la déduplication, un fichier PST distinct est exporté pour chaque boîte aux lettres incluse dans la recherche. 
 
> [!NOTE]
> Si vous ne sélectionnez pas l’option **inclure les éléments chiffrés ou dont le format n’est pas reconnu** lorsque vous exportez des résultats de recherche ou que vous venez de télécharger les rapports, les rapports d’erreur d’index sont téléchargés, mais ils n’ont aucune entrée. Cela ne signifie pas qu’il n’y a aucune erreur d’indexation. Cela signifie simplement que les éléments non indexés n’ont pas été inclus dans l’exportation. 
