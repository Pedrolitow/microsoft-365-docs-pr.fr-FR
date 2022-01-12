---
title: Différences entre les résultats de recherche eDiscovery estimés et réels
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: 8f20ca4f-a908-46ec-99e6-9890d269ecf2
description: Comprendre pourquoi les résultats de recherche estimés et réels peuvent varier dans les recherches qui s’exécutent avec les outils eDiscovery Office 365.
ms.openlocfilehash: 16b63b96421cfbf3f9d67e1373061b49ff5db225
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61938912"
---
# <a name="differences-between-estimated-and-actual-ediscovery-search-results"></a>Différences entre les résultats de recherche eDiscovery estimés et réels

Cette rubrique s’applique aux recherches que vous pouvez exécuter à l’aide de l’un des Microsoft 365 eDiscovery suivants : 

- Recherche de contenu
- Core eDiscovery

Lorsque vous exécutez une recherche de découverte électronique, l’outil que vous utilisez retourne une estimation du nombre d’éléments (et de leur taille totale) qui correspondent aux critères de recherche. Par exemple, lorsque vous exécutez une recherche dans le Centre de conformité Microsoft 365, les résultats estimés de la recherche sont affichés sur la page de présentation de la recherche sélectionnée.
  
![Estimation des résultats affichés sur la page volante de recherche.](../media/EstimatedSearchResults1.png)
  
Il s’agit de la même estimation de la taille totale et du nombre d’éléments affichés dans l’outil d’exportation eDiscovery lorsque vous exportez les résultats vers un ordinateur local et dans le rapport de synthèse de l’exportation qui est téléchargé avec les résultats de la recherche.
  
**Résultats estimés dans l’outil d’exportation eDiscovery**

![Résultats estimés dans l’outil d’exportation eDiscovery.](../media/d34312a5-0ee6-49aa-9460-7ea0015a6e66.png)
  
**Résultats estimés dans le rapport de synthèse de l’exportation**

![Les résultats de recherche estimés sont inclus dans le rapport de synthèse de l’exportation.](../media/44b579da-86c2-4f33-81b5-84d604003eda.png)
  
Toutefois, comme vous pouvez le constater dans la capture d’écran précédente du rapport de synthèse d’exportation, la taille et le nombre de résultats de recherche réels téléchargés sont différents de la taille et du nombre estimés de résultats de recherche.
  
![Différence entre les résultats de recherche estimés et téléchargés.](../media/84aef318-230f-430d-9d9e-02f21342d364.png)
  
Voici quelques raisons à ces différences :
  
- **La façon dont les résultats sont estimés**. Une estimation des résultats de la recherche est simplement une estimation (et non un nombre réel) des éléments qui répondent aux critères de requête de recherche. Pour compiler l’estimation des éléments Exchange, une liste des ID de message qui répondent aux critères de recherche est demandée à partir de la base de données Exchange par l’outil eDiscovery que vous utilisez. Toutefois, lorsque vous exportez les résultats de la recherche, la recherche est réexécutée et les messages réels sont récupérés à partir de la base Exchange données. Par conséquent, ces différences peuvent être dues à la façon dont le nombre estimé d’éléments et le nombre réel d’éléments sont déterminés.

- **Modifications qui se produisent entre le moment où l’estimation et l’exportation des résultats de recherche**. Lorsque vous exportez des résultats de recherche, la recherche est redémarré pour collecter les éléments les plus récents dans l’index de recherche qui répondent aux critères de recherche. Il est possible que des éléments supplémentaires ont été créés, envoyés ou reçus, qui répondent aux critères de recherche entre le moment où les résultats de recherche estimés ont été collectés et le moment où les résultats de la recherche ont été exportés. Il est également possible que les éléments qui seraient dans l’index de recherche lorsque les résultats de la recherche ont été estimés ne soient plus là, car ils ont été purgés de l’emplacement de contenu avant l’exportation des résultats de la recherche. Pour atténuer ce problème, vous pouvez spécifier une plage de dates pour une recherche de découverte électronique. Une autre façon consiste à placer une conservation sur les emplacements de contenu afin que les éléments soient conservés et ne soient pas purgés. 

   Bien que cela soit rare, même si une mise en attente est appliquée, la maintenance des éléments de calendrier intégrés (qui ne sont pas modifiables par l’utilisateur, mais qui sont inclus dans de nombreux résultats de recherche) peut être supprimée de temps à autre. Cette suppression périodique des éléments de calendrier entraîne un nombre réduit d’éléments exportés.

- **Éléments nonndexés.** Les éléments nonndex pour la recherche peuvent provoquer des différences entre les résultats de recherche estimés et réels. Vous pouvez inclure des éléments nonndex lorsque vous exportez les résultats de la recherche. Si vous incluez des éléments nonndes lors de l’exportation des résultats de recherche, il se peut que d’autres éléments soient exportés. Cela provoque une différence entre les résultats de recherche estimés et exportés.

    Lorsque vous utilisez l’outil de recherche de contenu, vous avez la possibilité d’inclure des éléments nonndex lorsque vous exportez des résultats de recherche. Le nombre d’éléments nonndex renvoyés par la recherche est répertorié sur la page volante avec les autres résultats de recherche estimés. Tous les éléments nonndex sont également inclus dans la taille totale des résultats de recherche estimés. Lorsque vous exportez des résultats de recherche, vous avez la possibilité d’inclure ou de ne pas inclure d’éléments nonndex. La configuration de ces options peut entraîner des différences entre les résultats estimés et les résultats de recherche réels téléchargés.

- **Exportation des résultats d’une recherche de contenu qui inclut tous les emplacements de contenu.** Si la recherche dont vous exportez les résultats était une recherche de tous les emplacements de contenu de votre organisation, seuls les éléments nonndex provenant d’emplacements de contenu qui contiennent des éléments qui correspondent aux critères de recherche seront exportés. In other words, if no search results are found in a mailbox or site, then any unindexed items in that mailbox or site won't be exported. Toutefois, les éléments nonndex provenant de tous les emplacements de contenu (même ceux qui ne contiennent pas d’éléments qui correspondent à la requête de recherche) seront inclus dans les résultats de recherche estimés.

    Par ailleurs, si la recherche que vous exportez à partir d’emplacements de contenu spécifiques est incluse, les éléments nonndex (qui ne sont pas exclus par les critères de recherche) de tous les emplacements de contenu spécifiés dans la recherche seront exportés. Dans ce cas, le nombre estimé d’éléments nonndex et le nombre d’éléments nonndex exportés doivent être identiques.

    La raison pour laquelle vous n’exportez pas d’éléments nonndes à partir de chaque emplacement de l’organisation est qu’elle peut augmenter la probabilité d’erreurs d’exportation et augmenter le temps qu’il faut pour exporter et télécharger les résultats de la recherche.

- **Les éléments nonndex dans les SharePoint et OneDrive ne sont** pas inclus dans les estimations de recherche. Les éléments nonndex provenant SharePoint sites et OneDrive Entreprise ne sont pas inclus dans les résultats de recherche estimés. Cela est dû au fait que SharePoint index ne contient pas de données pour les éléments non indexés. Seuls les éléments nonndex provenant de boîtes aux lettres sont inclus dans les estimations de recherche. Toutefois, si vous incluez des éléments nonndes lors de l’exportation des résultats de recherche, les éléments nonndes dans SharePoint et OneDrive sont inclus, ce qui augmente le nombre d’éléments réellement exportés. Cela se traduit par des différences entre les résultats estimés (qui n’incluent pas les éléments nonndex dans les sites SharePoint et OneDrive) et les éléments réels téléchargés. La règle concernant l’exportation d’éléments nonndes uniquement à partir d’emplacements de contenu qui contiennent des éléments qui correspondent aux critères de recherche s’applique toujours dans cette situation.

- **Versions de document SharePoint et OneDrive**. Lorsque vous recherchez SharePoint sites et OneDrive comptes de recherche, plusieurs versions d’un document ne sont pas incluses dans le nombre de résultats de recherche estimés. Toutefois, vous avez la possibilité d’inclure toutes les versions de document lorsque vous exportez les résultats de la recherche. Si vous incluez des versions de documents lors de l’exportation des résultats de recherche, le nombre réel (et la taille totale) des éléments exportés sera augmenté.

- **SharePoint dossiers**. Si le nom des dossiers dans SharePoint correspond à une requête de recherche, l’estimation de la recherche inclut le nombre de ces dossiers (mais pas les éléments de ces dossiers). Lorsque vous exportez les résultats de la recherche, les éléments du dossier sont exportés, mais le dossier réel n’est pas exporté. Le résultat est que le nombre d’éléments exportés exportés est supérieur au nombre estimé de résultats de recherche. Si un dossier est vide, le nombre de résultats de recherche réels exportés sera réduit d’un élément, car le dossier réel n’est pas exporté.

- **SharePoint listes**. Si le nom d’une SharePoint correspond à une requête de recherche, l’estimation de la recherche inclut le nombre de tous les éléments de la liste. Lorsque vous exportez les résultats de la recherche, la liste (et les éléments de liste) est exportée en tant que fichier CSV unique. Cela permet de réduire le nombre réel d’éléments réellement exportés. Si la liste contient des pièces jointes, elles sont exportées en tant que documents distincts, ce qui augmente également le nombre d’éléments exportés.

- **Formats de fichiers bruts et formats de fichiers exportés.** Pour Exchange éléments, la taille estimée des résultats de la recherche est calculée à l’aide de la taille brute Exchange messages. Toutefois, les messages électroniques sont exportés dans un fichier PST ou sous forme de messages individuels (qui sont formatés en tant que fichiers EML). Ces deux options d’exportation utilisent un format de fichier différent de celui des messages Exchange bruts, ce qui entraîne une différence entre la taille totale des fichiers exportés et la taille de fichier estimée.

- **Dédoplication des éléments Exchange lors de l’exportation.** Pour Exchange, la déduplication réduit le nombre d’éléments exportés. Vous avez la possibilité de dupliquer les résultats de la recherche lorsque vous les exportez. Pour Exchange messages, cela signifie qu’une seule instance d’un message est exportée, même si ce message peut se trouver dans plusieurs boîtes aux lettres. Les résultats de recherche estimés incluent chaque instance d’un message. Ainsi, si vous choisissez l’option de dédoplication lors de l’exportation des résultats de recherche, le nombre réel d’éléments exportés peut être considérablement inférieur au nombre estimé d’éléments.

Le rapport des résultats de la recherche (Results.csv fichier) contient une entrée pour chaque message en double et identifie la boîte aux lettres source où se trouve un message en double. Cela vous permet d’identifier toutes les boîtes aux lettres qui contiennent un message en double.

> [!NOTE]
> Si vous ne sélectionnez pas l’option Inclure des éléments chiffrés ou dont le **format** n’est pas reconnu lorsque vous exportez des résultats de recherche ou téléchargez simplement les rapports, les rapports d’erreur d’index sont téléchargés, mais ils n’ont aucune entrée. Cela ne signifie pas qu’il n’y a aucune erreur d’indexation. Cela signifie simplement que les éléments nonndex n’ont pas été inclus dans l’exportation.
