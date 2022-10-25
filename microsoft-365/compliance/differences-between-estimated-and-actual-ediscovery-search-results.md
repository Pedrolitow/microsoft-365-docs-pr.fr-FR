---
title: Résultats de recherche eDiscovery estimés et réels
description: Comprendre pourquoi les résultats de recherche estimés et réels peuvent varier dans les recherches exécutées avec les outils eDiscovery dans Office 365.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
- ediscovery
search.appverid:
- SPO160
- MOE150
- MET150
ms.openlocfilehash: e49226e42681bfa1923c83e73af4e504aa35c79c
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688302"
---
# <a name="differences-between-estimated-and-actual-ediscovery-search-results"></a>Différences entre les résultats de recherche eDiscovery estimés et réels

Cet article s’applique aux recherches que vous pouvez exécuter à l’aide de l’un des outils Microsoft Purview eDiscovery suivants :

- Recherche de contenu
- eDiscovery (Standard)

Lorsque vous exécutez une recherche eDiscovery, l’outil que vous utilisez retourne une estimation du nombre d’éléments (et de leur taille totale) qui correspondent aux critères de recherche. Par exemple, lorsque vous exécutez une recherche dans le portail de conformité Microsoft Purview, les résultats estimés de la recherche s’affichent sur la page volante de la recherche sélectionnée.
  
![Estimation des résultats affichés sur la page de menu volant de recherche.](../media/EstimatedSearchResults1.png)
  
Il s’agit de la même estimation de la taille totale et du nombre d’éléments affichés dans l’outil d’exportation eDiscovery lorsque vous exportez des résultats vers un ordinateur local et dans le rapport Résumé de l’exportation téléchargé avec les résultats de la recherche.
  
**Résultats estimés dans l’outil d’exportation eDiscovery**

![Résultats estimés dans l’outil d’exportation eDiscovery.](../media/d34312a5-0ee6-49aa-9460-7ea0015a6e66.png)
  
**Résultats estimés dans le rapport Résumé de l’exportation**

![Les résultats de la recherche estimés sont inclus dans le rapport Résumé de l’exportation.](../media/44b579da-86c2-4f33-81b5-84d604003eda.png)
  
Toutefois, comme vous le remarquerez dans la capture d’écran précédente du rapport Résumé de l’exportation, la taille et le nombre de résultats de recherche réels téléchargés sont différents de la taille et du nombre de résultats de recherche estimés.
  
![Différence entre les résultats de recherche estimés et téléchargés.](../media/84aef318-230f-430d-9d9e-02f21342d364.png)
  
Voici quelques raisons pour expliquer ces différences :
  
- **La façon dont les résultats sont estimés**. Une estimation des résultats de la recherche est simplement une estimation (et non un nombre réel) des éléments qui répondent aux critères de la requête de recherche. Pour compiler l’estimation des éléments Exchange, une liste des ID de message qui répondent aux critères de recherche est demandée à la base de données Exchange par l’outil eDiscovery que vous utilisez. Toutefois, lorsque vous exportez les résultats de la recherche, la recherche est réexécutée et les messages réels sont récupérés à partir de la base de données Exchange. Ces différences peuvent donc résulter de la façon dont le nombre estimé d’éléments et le nombre réel d’éléments sont déterminés.
- **Modifications qui se produisent entre le moment où l’estimation et l’exportation des résultats de la recherche sont effectuées**. Lorsque vous exportez les résultats de la recherche, la recherche est redémarrée pour collecter les éléments les plus récents de l’index de recherche qui répondent aux critères de recherche. Il est possible qu’il y ait des éléments supplémentaires créés, envoyés ou reçus qui répondent aux critères de recherche entre le moment où les résultats de recherche estimés ont été collectés et le moment où les résultats de la recherche ont été exportés. Il est également possible que les éléments qui se trouvaient dans l’index de recherche lorsque les résultats de la recherche ont été estimés ne soient plus là, car ils ont été vidés de l’emplacement du contenu avant l’exportation des résultats de la recherche. Une façon d’atténuer ce problème consiste à spécifier une plage de dates pour une recherche eDiscovery. Une autre méthode consiste à placer une conservation sur les emplacements de contenu afin que les éléments soient conservés et ne puissent pas être vidés.

   Voici d’autres problèmes qui peuvent entraîner des différences entre les résultats de recherche estimés et exportés :

  - Augmentation du nombre d’éléments lors de l’utilisation d’une requête de date. Cela est généralement dû aux deux facteurs suivants :
      - Conserver le contrôle de version dans SharePoint. Si un document est supprimé d'un site suspendu et que la gestion des versions est activée, toutes les versions du document supprimé seront préservées.
      - Éléments de calendrier. Accepter et rejeter les messages et les réunions périodiques continueront automatiquement à créer de nouveaux éléments en arrière-plan avec d’anciennes dates.
  - Avec les conservations, il peut y avoir des cas où le même élément est conservé dans la boîte aux lettres principale d’un utilisateur et dans sa boîte aux lettres d’archivage. Cela peut se produire lorsqu’un utilisateur déplace manuellement un élément vers son archive.
  - Bien que rare, même dans le cas où une conservation est appliquée, la maintenance des éléments de calendrier intégrés (qui ne sont pas modifiables par l’utilisateur, mais qui sont inclus dans de nombreux résultats de recherche) peut être supprimée de temps en temps. Cette suppression périodique des éléments de calendrier entraîne une diminution du nombre d’éléments exportés.

- **Éléments non indexés**. Les éléments qui ne sont pas indexés pour la recherche peuvent entraîner des différences entre les résultats de recherche estimés et réels. Vous pouvez inclure des éléments non indexés lorsque vous exportez les résultats de la recherche. Si vous incluez des éléments non indexés lors de l’exportation des résultats de recherche, d’autres éléments peuvent être exportés. Cela entraîne une différence entre les résultats de recherche estimés et exportés.

    Lorsque vous utilisez l’outil de recherche de contenu, vous avez la possibilité d’inclure des éléments non indexés lors de l’exportation des résultats de la recherche. Le nombre d’éléments non indexés retournés par la recherche est répertorié dans la page volante avec les autres résultats de recherche estimés. Tous les éléments non indexés sont également inclus dans la taille totale des résultats de recherche estimés. Lorsque vous exportez des résultats de recherche, vous avez la possibilité d’inclure ou non des éléments non indexés. La façon dont vous configurez ces options peut entraîner des différences entre les résultats de recherche estimés et réels téléchargés.

- **Exportation des résultats d’une recherche de contenu qui inclut tous les emplacements de contenu**. Si la recherche à partir de laquelle vous exportez les résultats était une recherche de tous les emplacements de contenu de votre organisation, seuls les éléments non indexés des emplacements de contenu qui contiennent des éléments qui correspondent aux critères de recherche seront exportés. In other words, if no search results are found in a mailbox or site, then any unindexed items in that mailbox or site won't be exported. Toutefois, les éléments non indexés de tous les emplacements de contenu (même ceux qui ne contiennent pas d’éléments qui correspondent à la requête de recherche) seront inclus dans les résultats de recherche estimés.

    Si la recherche que vous exportez contient des emplacements de contenu spécifiques, les éléments non indexés (qui ne sont pas exclus par les critères de recherche) de tous les emplacements de contenu spécifiés dans la recherche sont également exportés. Dans ce cas, le nombre estimé d’éléments non indexés et le nombre d’éléments non indexés exportés doivent être identiques.

    La raison pour laquelle l’exportation d’éléments non indexés à partir de chaque emplacement de l’organisation est due au fait que cela peut augmenter la probabilité d’erreurs d’exportation et augmenter le temps nécessaire à l’exportation et au téléchargement des résultats de recherche.

- **Éléments non indexés dans SharePoint et OneDrive non inclus dans les estimations de recherche**. Les éléments non indexés des sites SharePoint et des comptes OneDrive Entreprise ne sont pas inclus dans les résultats de recherche estimés. Cela est dû au fait que l’index SharePoint ne contient pas de données pour les éléments non indexés. Seuls les éléments non indexés des boîtes aux lettres sont inclus dans les estimations de recherche. Toutefois, si vous incluez des éléments non indexés lors de l’exportation des résultats de recherche, les éléments non indexés dans SharePoint et OneDrive sont inclus, ce qui augmente le nombre d’éléments réellement exportés. Cela entraîne des différences entre les résultats estimés (qui n’incluent pas les éléments non indexés dans les sites SharePoint et OneDrive) et les éléments réels téléchargés. La règle d’exportation des éléments non indexés uniquement à partir d’emplacements de contenu qui contiennent des éléments qui correspondent aux critères de recherche s’applique toujours dans cette situation.

- **Versions de document dans SharePoint et OneDrive**. Lors de la recherche de sites SharePoint et de comptes OneDrive, plusieurs versions d’un document ne sont pas incluses dans le nombre de résultats de recherche estimés. Toutefois, vous avez la possibilité d’inclure toutes les versions de document lorsque vous exportez les résultats de la recherche. Si vous incluez des versions de document lors de l’exportation des résultats de recherche, le nombre réel (et la taille totale) des éléments exportés seront augmentés.

- **Dossiers SharePoint**. Si les dossiers dans SharePoint correspondent à une requête de recherche, par exemple, la recherche par date, l’estimation de la recherche inclut le nombre de dossiers avec la plage de dates de dernière modification (mais pas les éléments de ces dossiers). Lorsque vous exportez les résultats de la recherche, les éléments du dossier sont exportés, mais le dossier réel n’est pas exporté. Le résultat est que le nombre d’éléments exportés sera supérieur au nombre de résultats de recherche estimés. Si un dossier est vide, le nombre de résultats de recherche réels exportés est réduit d’un élément, car le dossier réel n’est pas exporté.

   > [!NOTE]
   > Lors de l’exécution d’une recherche basée sur une requête, vous pouvez exclure des dossiers SharePoint en ajoutant la condition suivante à la requête : `NOT(ContentType:folder)`.

- **Listes SharePoint**. Si le nom d’une liste SharePoint correspond à une requête de recherche, l’estimation de la recherche inclut le nombre de tous les éléments de la liste. Lorsque vous exportez les résultats de la recherche, la liste (et les éléments de liste) sont exportés sous la forme d’un seul fichier CSV. Cela réduit le nombre réel d’éléments réellement exportés. Si la liste contient des pièces jointes, les pièces jointes sont exportées en tant que documents distincts, ce qui augmente également le nombre d’éléments exportés.

   > [!NOTE]
   > Lorsque vous exécutez une recherche basée sur une requête, vous pouvez exclure des listes SharePoint en ajoutant la condition suivante à la requête : `NOT(ContentType:list)`.

- **Formats de fichiers bruts par rapport aux formats de fichier exportés**. Pour les éléments Exchange, la taille estimée des résultats de la recherche est calculée à l’aide des tailles de message Exchange brutes. Toutefois, les messages électroniques sont exportés dans un fichier PST ou en tant que messages individuels (qui sont au format de fichiers EML). Ces deux options d’exportation utilisent un format de fichier différent de celui des messages Exchange bruts, ce qui entraîne une taille de fichier totale exportée différente de la taille de fichier estimée.

- **Déduplication des éléments Exchange lors de l’exportation**. Pour les éléments Exchange, la déduplication réduit le nombre d’éléments exportés. Vous avez la possibilité de dédupliquer les résultats de la recherche lorsque vous les exportez. Pour les messages Exchange, cela signifie qu’une seule instance d’un message est exportée, même si ce message peut se trouver dans plusieurs boîtes aux lettres. Les résultats de recherche estimés incluent chaque instance d’un message. Par conséquent, si vous choisissez l’option de déduplication lors de l’exportation des résultats de recherche, le nombre réel d’éléments exportés peut être considérablement inférieur au nombre estimé d’éléments.

Le rapport des résultats de la recherche (fichier Results.csv) contient une entrée pour chaque message en double et identifie la boîte aux lettres source où se trouve un message en double. Cela vous permet d’identifier toutes les boîtes aux lettres qui contiennent un message en double.

> [!NOTE]
> Si vous ne sélectionnez pas l’option **Inclure les éléments chiffrés ou dont le format n’est pas** reconnu lorsque vous exportez les résultats de recherche ou téléchargez simplement les rapports, les rapports d’erreurs d’index sont téléchargés, mais ils n’ont pas d’entrée. Cela ne signifie pas qu’il n’y a pas d’erreurs d’indexation. Cela signifie simplement que les éléments non indexés n’ont pas été inclus dans l’exportation.
