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
description: Comprendre pourquoi les résultats de recherche estimés et réels peuvent varier dans les recherches exécutées avec les outils eDiscovery dans Office 365.
ms.openlocfilehash: 5ec234ed698e621a629aecf7adf34fb675b29034
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783840"
---
# <a name="differences-between-estimated-and-actual-ediscovery-search-results"></a>Différences entre les résultats de recherche eDiscovery estimés et réels

Cet article s’applique aux recherches que vous pouvez exécuter à l’aide de l’un des outils eDiscovery Microsoft 365 suivants : 

- Recherche de contenu
- Core eDiscovery

Lorsque vous exécutez une recherche eDiscovery, l’outil que vous utilisez retourne une estimation du nombre d’éléments (et de leur taille totale) qui correspondent aux critères de recherche. Par exemple, lorsque vous exécutez une recherche dans le Centre de conformité Microsoft 365, les résultats estimés de la recherche sont affichés dans la page volante de la recherche sélectionnée.
  
![Estimation des résultats affichés dans la page de menu volant de recherche.](../media/EstimatedSearchResults1.png)
  
Il s’agit de la même estimation de la taille totale et du nombre d’éléments affichés dans l’outil d’exportation eDiscovery lorsque vous exportez des résultats vers un ordinateur local et dans le rapport Résumé de l’exportation téléchargé avec les résultats de la recherche.
  
**Résultats estimés dans l’outil d’exportation eDiscovery**

![Estimation des résultats dans l’outil d’exportation eDiscovery.](../media/d34312a5-0ee6-49aa-9460-7ea0015a6e66.png)
  
**Résultats estimés dans le rapport Résumé de l’exportation**

![Les résultats de recherche estimés sont inclus dans le rapport Résumé de l’exportation.](../media/44b579da-86c2-4f33-81b5-84d604003eda.png)
  
Toutefois, comme vous le remarquerez dans la capture d’écran précédente du rapport Résumé de l’exportation, la taille et le nombre de résultats de recherche réels téléchargés sont différents de la taille et du nombre estimés de résultats de recherche.
  
![Différence entre les résultats de recherche estimés et téléchargés.](../media/84aef318-230f-430d-9d9e-02f21342d364.png)
  
Voici quelques raisons pour ces différences :
  
- **La façon dont les résultats sont estimés**. Une estimation des résultats de la recherche est simplement une estimation (et non un nombre réel) des éléments qui répondent aux critères de requête de recherche. Pour compiler l’estimation des éléments Exchange, une liste des ID de message qui répondent aux critères de recherche est demandée à partir de la base de données Exchange par l’outil eDiscovery que vous utilisez. Toutefois, lorsque vous exportez les résultats de la recherche, la recherche est réexécutée et les messages réels sont récupérés à partir de la base de données Exchange. Ces différences peuvent donc se produire en raison de la façon dont le nombre estimé d’éléments et le nombre réel d’éléments sont déterminés.

- **Modifications qui se produisent entre le moment où l’estimation et l’exportation des résultats de recherche** sont effectuées. Lorsque vous exportez les résultats de la recherche, la recherche est redémarrée pour collecter les éléments les plus récents dans l’index de recherche qui répondent aux critères de recherche. Il est possible que d’autres éléments aient été créés, envoyés ou reçus qui répondent aux critères de recherche entre le moment où les résultats estimés de la recherche ont été collectés et le moment où les résultats de la recherche ont été exportés. Il est également possible que les éléments qui se trouvaient dans l’index de recherche lorsque les résultats de la recherche ont été estimés ne soient plus présents, car ils ont été vidés de l’emplacement de contenu avant l’exportation des résultats de la recherche. Une façon d’atténuer ce problème consiste à spécifier une plage de dates pour une recherche eDiscovery. Une autre méthode consiste à placer une conservation sur les emplacements de contenu afin que les éléments soient conservés et ne puissent pas être vidés.

   Voici d’autres problèmes qui peuvent entraîner des différences entre les résultats de recherche estimés et exportés :

  - Augmentation du nombre d’éléments lors de l’utilisation d’une requête de date. Cela est généralement dû aux deux éléments suivants :

  - Maintenez le contrôle de version en attente dans SharePoint. Si un document est supprimé d'un site suspendu et que la gestion des versions est activée, toutes les versions du document supprimé seront préservées.

  - Éléments de calendrier. Accepter et rejeter des messages et des réunions périodiques continueront automatiquement à créer de nouveaux éléments en arrière-plan avec d’anciennes dates.

  - Avec les conservations, il peut arriver que le même élément soit conservé dans la boîte aux lettres principale d’un utilisateur et dans sa boîte aux lettres d’archivage. Cela peut se produire lorsqu’un utilisateur déplace manuellement un élément vers son archive.

  - Bien que rare, même dans le cas où une conservation est appliquée, la maintenance des éléments de calendrier intégrés (qui ne sont pas modifiables par l’utilisateur, mais qui sont inclus dans de nombreux résultats de recherche) peut être supprimée de temps à autre. Cette suppression périodique des éléments de calendrier entraîne moins d’éléments exportés.

- **Éléments non indexés**. Les éléments qui ne sont pas indexés pour la recherche peuvent entraîner des différences entre les résultats de recherche estimés et réels. Vous pouvez inclure des éléments non indexés lorsque vous exportez les résultats de la recherche. Si vous incluez des éléments non indexés lors de l’exportation des résultats de recherche, d’autres éléments peuvent être exportés. Cela entraîne une différence entre les résultats de recherche estimés et exportés.

    Lorsque vous utilisez l’outil de recherche de contenu, vous avez la possibilité d’inclure des éléments non indexés lorsque vous exportez les résultats de la recherche. Le nombre d’éléments non indexés retournés par la recherche est répertorié dans la page de menu volant avec les autres résultats de recherche estimés. Tous les éléments non indexés seraient également inclus dans la taille totale des résultats de recherche estimés. Lorsque vous exportez des résultats de recherche, vous avez la possibilité d’inclure ou non des éléments non indexés. La façon dont vous configurez ces options peut entraîner des différences entre les résultats de recherche estimés et réels téléchargés.

- **Exportation des résultats d’une recherche de contenu qui inclut tous les emplacements de contenu**. Si la recherche à partir de laquelle vous exportez les résultats était une recherche de tous les emplacements de contenu de votre organisation, seuls les éléments non indexés des emplacements de contenu qui contiennent des éléments qui correspondent aux critères de recherche seront exportés. In other words, if no search results are found in a mailbox or site, then any unindexed items in that mailbox or site won't be exported. Toutefois, les éléments non indexés de tous les emplacements de contenu (même ceux qui ne contiennent pas d’éléments correspondant à la requête de recherche) seront inclus dans les résultats de recherche estimés.

    Sinon, si la recherche que vous exportez à partir d’emplacements de contenu spécifiques inclus, les éléments non indexés (qui ne sont pas exclus par les critères de recherche) de tous les emplacements de contenu spécifiés dans la recherche seront exportés. Dans ce cas, le nombre estimé d’éléments non indexés et le nombre d’éléments non indexés exportés doivent être identiques.

    La raison pour laquelle l’exportation d’éléments non indexés à partir de chaque emplacement de l’organisation peut augmenter la probabilité d’erreurs d’exportation et augmenter le temps nécessaire pour exporter et télécharger les résultats de la recherche.

- **Les éléments non indexés dans SharePoint et OneDrive non inclus dans les estimations de recherche**. Les éléments non indexés des sites SharePoint et des comptes OneDrive Entreprise ne sont pas inclus dans les résultats de recherche estimés. Cela est dû au fait que l’index SharePoint ne contient pas de données pour les éléments non indexés. Seuls les éléments non indexés des boîtes aux lettres sont inclus dans les estimations de recherche. Toutefois, si vous incluez des éléments non indexés lors de l’exportation des résultats de recherche, les éléments non indexés dans SharePoint et OneDrive sont inclus, ce qui augmente le nombre d’éléments réellement exportés. Cela entraîne des différences entre les résultats estimés (qui n’incluent pas les éléments non indexés dans les sites SharePoint et OneDrive) et les éléments réels téléchargés. La règle d’exportation d’éléments non indexés uniquement à partir d’emplacements de contenu qui contiennent des éléments qui correspondent aux critères de recherche s’applique toujours dans cette situation.

- **Documentez les versions dans SharePoint et OneDrive**. Lors de la recherche SharePoint sites et de comptes OneDrive, plusieurs versions d’un document ne sont pas incluses dans le nombre estimé de résultats de recherche. Toutefois, vous avez la possibilité d’inclure toutes les versions de document lorsque vous exportez les résultats de la recherche. Si vous incluez des versions de document lors de l’exportation des résultats de recherche, le nombre réel (et la taille totale) des éléments exportés sera augmenté.

- **SharePoint dossiers**. Si les dossiers dans SharePoint correspondent à une requête de recherche, par exemple, la recherche par date, l’estimation de recherche inclut un nombre de ces dossiers avec la dernière plage de dates modifiées (mais pas les éléments de ces dossiers). Lorsque vous exportez les résultats de la recherche, les éléments du dossier sont exportés, mais le dossier réel n’est pas exporté. Le résultat est que le nombre d’éléments exportés sera supérieur au nombre estimé de résultats de recherche. Si un dossier est vide, le nombre de résultats de recherche réels exportés est réduit d’un élément, car le dossier réel n’est pas exporté.

   > [!NOTE]
   > Lors de l’exécution d’une recherche basée sur une requête, vous pouvez exclure SharePoint dossiers en ajoutant la condition suivante à la requête : `NOT(ContentType:folder)`.

- **SharePoint listes**. Si le nom d’une liste SharePoint correspond à une requête de recherche, l’estimation de recherche inclut un nombre de tous les éléments de la liste. Lorsque vous exportez les résultats de la recherche, la liste (et les éléments de liste) est exportée en tant que fichier CSV unique. Cela réduit le nombre réel d’éléments réellement exportés. Si la liste contient des pièces jointes, les pièces jointes sont exportées en tant que documents distincts, ce qui augmente également le nombre d’éléments exportés.

   > [!NOTE]
   > Lors de l’exécution d’une recherche basée sur une requête, vous pouvez exclure SharePoint listes en ajoutant la condition suivante à la requête : `NOT(ContentType:list)`.

- **Formats de fichiers bruts par rapport aux formats de fichier exportés**. Pour Exchange éléments, la taille estimée des résultats de recherche est calculée à l’aide des tailles de message brutes Exchange. Toutefois, les messages électroniques sont exportés dans un fichier PST ou en tant que messages individuels (qui sont mis en forme en tant que fichiers EML). Ces deux options d’exportation utilisent un format de fichier différent de celui des messages Exchange bruts, ce qui entraîne une taille de fichier exportée totale différente de la taille de fichier estimée.

- **Dédoublement des éléments Exchange pendant l’exportation**. Pour Exchange éléments, la dédoublement réduit le nombre d’éléments exportés. Vous avez la possibilité de dédupliquer les résultats de la recherche lorsque vous les exportez. Pour Exchange messages, cela signifie qu’une seule instance d’un message est exportée, même si ce message peut se trouver dans plusieurs boîtes aux lettres. Les résultats de recherche estimés incluent chaque instance d’un message. Par conséquent, si vous choisissez l’option de dédoublement lors de l’exportation des résultats de recherche, le nombre réel d’éléments exportés peut être considérablement inférieur au nombre estimé d’éléments.

Le rapport de résultats de recherche (fichier Results.csv) contient une entrée pour chaque message en double et identifie la boîte aux lettres source où se trouve un message en double. Cela vous permet d’identifier toutes les boîtes aux lettres qui contiennent un message en double.

> [!NOTE]
> Si vous ne sélectionnez pas les **éléments Include chiffrés ou dont le format n’est pas reconnu** lorsque vous exportez les résultats de la recherche ou téléchargez simplement les rapports, les rapports d’erreur d’index sont téléchargés, mais ils n’ont pas d’entrées. Cela ne signifie pas qu’il n’y a pas d’erreurs d’indexation. Cela signifie simplement que les éléments non indexés n’ont pas été inclus dans l’exportation.
