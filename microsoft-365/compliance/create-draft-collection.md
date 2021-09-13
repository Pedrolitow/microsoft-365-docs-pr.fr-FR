---
title: Créer une collection au brouillon
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Un brouillon de collection est une recherche eDiscovery de sources de données privées et non privées dans un cas Advanced eDiscovery qui renvoie une estimation de recherche qui correspond à la requête de recherche de la collection. Vous pouvez passer en revue les statistiques de recherche, prévisualiser un échantillonnage d’éléments et réviser et réexécuter la collection avant de valider les résultats dans un jeu à réviser.
ms.openlocfilehash: 0354f2a04dfff82f995fe74663633f42ed01e677
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59163972"
---
# <a name="create-a-draft-collection-in-advanced-ediscovery"></a>Créer un brouillon de collection dans Advanced eDiscovery

Une fois que vous avez identifié des dépositaires et des sources de données non dépositaires pour le cas, vous êtes prêt à identifier et à localiser un ensemble de documents pertinents. Pour ce faire, utilisez l’outil Collections pour rechercher du contenu pertinent dans les sources de données. Pour ce faire, vous créez une collection qui recherche le contenu qui correspond à vos critères de recherche dans les sources de données spécifiées. Vous avez la possibilité de créer un brouillon *de collection*, qui est une estimation des éléments trouvés ou vous pouvez créer une collection qui ajoute automatiquement les éléments à un jeu à réviser. Lorsque vous créez un brouillon de collection, vous pouvez voir des informations sur les résultats estimés qui correspondent à la requête de recherche, telles que le nombre total et la taille des éléments trouvés, les différentes sources de données où ils ont été trouvés et les statistiques sur la requête de recherche. Vous pouvez également afficher un aperçu d’un exemple d’éléments qui ont été renvoyés par la collection. À l’aide de ces statistiques, vous pouvez modifier la requête de recherche et réexécuter la collection provisoire pour affiner vos résultats. Une fois que vous êtes satisfait des résultats de la collection, vous pouvez valider la collection dans un jeu à réviser. Lorsque vous valider un brouillon de collection, les éléments renvoyés par la collection sont ajoutés à un jeu à réviser pour révision, analyse et exportation.

## <a name="before-you-create-a-draft-collection"></a>Avant de créer un brouillon de collection

- Ajoutez des dépositaires et des sources de données non privatives au cas avant de créer un brouillon de collection. Ceci est obligatoire pour que vous pouvez sélectionner les sources de données lorsque vous créez un brouillon de collection. Pour plus d’informations, consultez :

  - [Ajouter des consignataires à un cas](add-custodians-to-case.md)

  - [Ajout de sources de données non consignataires à un cas](non-custodial-data-sources.md)

- Vous pouvez rechercher des sources de données supplémentaires (qui n’ont pas été ajoutées au cas en tant qu’emplacements de garde ou non) dans un brouillon de collection pour le contenu qui peut être pertinent pour le cas. Ces sources de données peuvent inclure des boîtes aux lettres, SharePoint sites et Teams. Si cette situation s’applique à votre cas, compilez une liste de ces sources de données afin de pouvoir les ajouter à la collection.

## <a name="create-a-draft-collection"></a>Créer une collection au brouillon

1. Dans la Centre de conformité Microsoft 365, ouvrez Advanced eDiscovery cas, puis sélectionnez **l’onglet Collections.**

2. Dans la page **Collections,** **sélectionnez Nouvelle collection**  >  **Standard.**

3. Tapez un nom (obligatoire) et une description (facultatif) pour la collection. Une fois la collection créée, vous ne pouvez pas modifier le nom, mais vous pouvez modifier la description.

4. Dans la page **Des sources de** données de garde, faites l’une des choses suivantes pour identifier les sources de données de garde à partir des éléments suivants :

   - Cliquez **sur Sélectionner des dépositaires** pour rechercher des dépositaires spécifiques qui ont été ajoutés au cas. Si vous utilisez cette option, une liste des dépositaires de cas s’affiche. Sélectionnez un ou plusieurs dépositaires. Après avoir sélectionné et ajouté les dépositaires, vous pouvez également sélectionner les sources de données spécifiques pour rechercher chaque dépositaire. Ces sources de données affichées ont été spécifiées lorsque le dépositaire a été ajouté au cas.

   - Cliquez sur **le bouton bascule** Sélectionner tout pour rechercher tous les dépositaires qui ont été ajoutés au cas. Lorsque vous sélectionnez cette option, toutes les sources de données de tous les dépositaires sont interrogées.

5. Dans la page **Sources** de données non privatives, faites l’une des choses suivantes pour identifier les sources de données non privatives à partir des sources de données à partir des éléments suivants :

   - Cliquez **sur Sélectionner les sources de données** non privatives pour sélectionner des sources de données spécifiques qui n’ont pas été ajoutées au cas. Si vous utilisez cette option, une liste de sources de données s’affiche. Sélectionnez une ou plusieurs de ces sources de données.

   - Cliquez sur **le bouton bascule** Sélectionner tout pour sélectionner toutes les sources de données qui n’ont pas été ajoutées au cas.

6. Dans la page **Sources de données** supplémentaires, vous pouvez sélectionner d’autres boîtes aux lettres et sites à rechercher dans le cadre de la collection. Ces types de sources de données n’ont pas été ajoutés en tant qu’emplacements de données privatives ou non dans le cas. Vous avez également deux options pour rechercher des sources de données supplémentaires :

   - Pour rechercher tous les emplacements de contenu pour un service spécifique (boîtes aux lettres Exchange, sites SharePoint  et OneDrive ou  dossiers publics Exchange), cliquez sur le bouton bascule Sélectionner tout dans la colonne État. Cette option recherche tous les emplacements de contenu dans le service sélectionné.

   - Pour rechercher un emplacement de contenu  spécifique pour un service, cliquez sur le bouton bascule Sélectionner tout dans la colonne État, puis cliquez sur  **Utilisateurs,** groupes ou équipes (pour les boîtes aux lettres Exchange) ou choisissez des **sites** pour (sites SharePoint et OneDrive) pour rechercher des emplacements de contenu spécifiques.

7. Dans la page **Conditions,** vous pouvez créer la requête de recherche utilisée pour collecter des éléments à partir des sources de données que vous avez identifiées dans les pages précédentes de l’Assistant. Vous pouvez rechercher des mots clés, des paires property:value ou utiliser une liste de mots clés. Vous pouvez également ajouter différentes conditions de recherche pour restreindre l’étendue de la collection. Pour plus d’informations, [voir Créer des requêtes de recherche pour les collections.](building-search-queries.md)

8. On the **Save as draft or add to review set** page, select Save collection as **draft**.

   > [!NOTE]
   > L’autre option de cette page vous permet de collecter des éléments et de les ajouter directement à un jeu à réviser. Au lieu de créer un brouillon de collection que vous pouvez consulter et afficher un aperçu des résultats de la collection, cette option ignore ce processus et ajoute automatiquement la collection à un jeu à réviser. Si vous sélectionnez la deuxième option pour ajouter la collection à un jeu à réviser, vous avez des paramètres supplémentaires à configurer, tels que la collecte de threads de conversation complets dans Microsoft Teams et Yammer et la collecte de pièces jointes cloud (également appelées pièces *jointes modernes).* Pour plus d’informations sur ces paramètres, voir [Valider un brouillon de collection dans un jeu à réviser.](commit-draft-collection.md)

9. Dans la page **Examiner votre collection,** vous pouvez passer en revue et mettre à jour les paramètres de collection que vous avez configurés sur les pages précédentes.

   - **Onglet Résumé** : Examinez et modifiez le nom et la description de la collection, les critères de recherche de la collection, les emplacements de données supplémentaires et le type de collection.

   - **Onglet Sources** : examiner et modifier les sources de données de la collection.

10. Cliquez **sur Envoyer** pour créer le brouillon de la collection. Une page s’affiche confirmant que la collection a été créée.

## <a name="what-happens-after-you-create-a-draft-collection"></a>Que se passe-t-il après la création d’une collection provisoire ?

Une fois que vous avez créé un brouillon de collection, il est répertorié dans la page **Collections** dans le cas et l’état indique qu’il est en cours. Un travail nommé **Préparation de l’aperçu** de recherche et des estimations est également créé et affiché sur la page **Travaux** dans le cas.

Pendant le processus de collecte provisoire, Advanced eDiscovery une estimation de la recherche à l’aide des critères de recherche et des sources de données que vous avez spécifiés dans la collection. Advanced eDiscovery prépare également un échantillonnage des éléments que vous pouvez prévisualiser. Une fois la collection terminée, les colonnes suivantes et les valeurs correspondantes sur la page **Collection** sont mises à jour :

![États d’état d’une collection de brouillons.](../media/DraftCollectionStatus.png)

- **Status**: indique l’état et le type de collection. La valeur **Estimated** indique qu’une collection provisoire est terminée. Cette même valeur indique également que la collection est un brouillon de collection et qu’elle n’a pas été ajoutée à un jeu à réviser. La valeur **Committed** dans la colonne **Status** indique que la collection a été ajoutée à un jeu à réviser.

- **État de l’estimation**: indique l’état des résultats de recherche estimés et si les estimations de recherche et les statistiques sont prêtes à être évaluées. La valeur **Réussite** indique que les résultats de l’ébauche de collection sont prêts pour révision. Une fois que vous avez soumis un brouillon de collection pour la première fois, la valeur **En cours** s’affiche pour indiquer que la collection est toujours en cours d’exécution.

- **État de l’aperçu**: indique l’état des exemples d’éléments que vous pouvez prévisualiser. La valeur **Réussite** indique que les éléments sont prêts pour la prévisualisation. Une fois que vous avez soumis un brouillon de collection pour la première fois, la valeur **En cours** s’affiche pour indiquer que la collection est toujours en cours d’exécution.

## <a name="next-steps-after-a-draft-collection-is-complete"></a>Étapes suivantes après la fin d’une collection de brouillons

Une fois l’ébauche de collection terminée, vous pouvez effectuer diverses tâches. Pour effectuer la plupart de ces tâches, il vous suffit d’aller dans l’onglet **Collections** et de cliquer sur le nom de la collection provisoire pour afficher la page volante.

![Page volante d’une collection de brouillons.](../media/DraftCollectionFlyoutPage.png)

Voici la liste des choses que vous pouvez faire à partir de la page volante de collection :

- Sélectionnez **l’onglet Résumé** pour afficher des informations récapitulatifs sur la collection et les résultats de recherche estimés renvoyés par la collection. Cela inclut le nombre total d’éléments et la taille des résultats de recherche estimés, le nombre de boîtes aux lettres et de sites contenant des résultats de recherche et les conditions de recherche (si utilisées) utilisées pour limiter la collection.

- Sélectionnez **l’onglet Sources** de données pour afficher la liste des dépositaires et des sources de données qui n’ont pas été recherchés dans la collection. Tous les emplacements de contenu supplémentaires qui ont fait l’objet d’une recherche sont répertoriés sous **Emplacements** sous **l’onglet** Résumé.

- Sélectionnez **l’onglet Statistiques de** recherche pour afficher les statistiques sur la collection. Cela inclut le nombre total et la taille des éléments trouvés dans chaque service (par exemple, les boîtes aux lettres Exchange ou les sites SharePoint) et un rapport de condition qui affiche des statistiques sur le nombre d’éléments renvoyés par différents composants de la requête de recherche utilisée par la collection. Pour plus d’informations, voir [statistiques et rapports de collecte.](collection-statistics-reports.md)

- Cliquez **sur Examiner l’exemple** (situé au bas de la page volante) pour afficher un aperçu des éléments renvoyés par la collection.

- Valider l’ébauche de collection dans un jeu à réviser (en cliquant sur **Actions**  >  **Modifier la collection**). Cela signifie que vous réexécutez la collection (à l’aide des paramètres actuels) et ajoutez les éléments renvoyés par la collection à un jeu à réviser. Comme indiqué précédemment, vous pouvez également configurer des paramètres supplémentaires (tels que les threads de conversation et les pièces jointes basées sur le cloud) lorsque vous ajoutez la collection à un jeu à réviser. Pour plus d’informations et des instructions pas à pas, voir Valider un brouillon [de collection dans un jeu à réviser.](commit-draft-collection.md)

## <a name="manage-a-draft-collection"></a>Gérer un brouillon de collection

Vous pouvez utiliser les options du menu **Actions** de la page volante d’un brouillon de collection pour effectuer différentes tâches de gestion.

![Options du menu Actions pour la collection brouillon.](../media/DraftCollectionActionsMenu.png)

Voici des descriptions des options de gestion.

- **Modifier la collection**: modifier les paramètres de la collection brouillon. Après avoir apporté des modifications, vous pouvez réexécuter la collection et mettre à jour les estimations et statistiques de recherche. Comme indiqué précédemment, vous utilisez cette option pour valider un brouillon de collection dans un jeu à réviser.  

- **Supprimer une collection**: supprimer une collection brouillon. Notez qu’une fois qu’un brouillon de collection est engagé dans un jeu à réviser, il ne peut pas être supprimé.

- **Actualiser les estimations**: réexécutez la requête (par rapport aux sources de données) spécifiées dans le brouillon de la collection pour mettre à jour les estimations de recherche et les statistiques.

- **Exporter en tant que** rapport : exporte des informations sur le brouillon de collection dans un fichier CSV que vous pouvez télécharger sur votre ordinateur local. Le rapport d’exportation contient les informations suivantes :

  - Identité de chaque emplacement de contenu qui contient les éléments qui correspondent à la requête de recherche dans la collection provisoire. Ces emplacements sont généralement des boîtes aux lettres ou des sites.
  
  - Nombre total d’éléments dans chaque emplacement de contenu.
  
  - Taille totale (en octets) des éléments de chaque emplacement de contenu.

  - Service (par exemple, Exchange ou SharePoint) dans lequel se trouve l’emplacement du contenu.

- **Copier une collection**: créez un brouillon de collection en copiant les paramètres d’une collection existante. Vous devez utiliser un nom différent pour la nouvelle collection. Vous avez également la possibilité de modifier les paramètres avant d’envoyer la nouvelle collection. Une fois que vous l’avez soumis, la requête de recherche est exécuté et de nouvelles estimations et statistiques sont générées. Il s’agit d’un bon moyen de créer rapidement une collection de brouillons supplémentaire, puis de modifier les paramètres sélectionnés si nécessaire tout en conservant les informations de la collection d’origine. Cela vous permet également de comparer facilement les résultats de deux collections similaires.

> [!NOTE]
> Une fois qu’un brouillon de collection est engagé dans un jeu à réviser, vous pouvez uniquement copier la collection et exporter un rapport.
