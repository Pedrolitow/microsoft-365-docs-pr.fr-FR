---
title: Gérer les rubriques dans le centre de rubriques dans Rubriques microsoft
description: Comment gérer des rubriques dans le Centre de rubriques.
author: chuckedmonson
ms.author: chucked
manager: pamgreen
ms.reviewer: cjtan
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-topics
localization_priority: None
ms.openlocfilehash: e2cbf62339e2ade240474fed9db86e68dc0b3bb4
ms.sourcegitcommit: 223a36a86753fe9cebee96f05ab4c9a144133677
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51760121"
---
# <a name="manage-topics-in-the-topic-center-in-microsoft-viva-topics"></a>Gérer les rubriques dans le centre de rubriques dans Rubriques microsoft

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LxDx]  

</br>


Dans le centre de rubriques Rubriques, un gestionnaire de connaissances peut afficher la page Gérer les **rubriques** pour passer en revue les rubriques qui ont été identifiées dans les emplacements sources SharePoint comme spécifié par votre administrateur de connaissances.  

   ![Centre de rubriques](../media/knowledge-management/topic-center.png) </br> 



Les gestionnaires de connaissances vous aident à guider les rubriques découvertes tout au long du cycle de vie des rubriques dans lesquelles les rubriques sont les suivants :

- **Suggestion :** une rubrique a été identifiée par l'IA et dispose de ressources, connexions et propriétés de prise en charge suffisantes.
- **Confirmé :** une rubrique suggérée par l'IA est validée. La validation est effectuée par confirmation à partir d'un gestionnaire de connaissances. En outre, une rubrique peut être confirmée si au moins deux utilisateurs donnent des commentaires positifs par le biais de la question de commentaires sur la carte de rubrique.
- **Publié**: une rubrique confirmée qui a été organisée : des modifications manuelles ont été réalisées pour améliorer sa qualité.
- **Supprimé :** une rubrique est rejetée par un gestionnaire de connaissances et n'est plus visible pour les visiteurs. La rubrique peut se trouver dans n'importe quel état lorsqu'elle est supprimée (suggérée, confirmée ou publiée). Lorsqu'une rubrique publiée est supprimée, la page avec les détails organisés doit être supprimée manuellement via la bibliothèque de pages du centre de rubriques.

   ![Graphique du cycle de vie des rubriques](../media/knowledge-management/topic-lifecycle.png) </br> 

> [!Note] 
> Dans la page Gérer les rubriques, chaque gestionnaire de connaissances peut uniquement consulter les rubriques dans laquelle il a accès aux fichiers et aux pages de la rubrique. Cela sera reflété dans les rubriques qui sont répertoriées sous les onglets **Suggéré,** **Confirmé,** Supprimé et Publié.  Les nombres de rubriques, toutefois, indiquent le nombre total dans l'organisation.

## <a name="requirements"></a>Conditions requises

Pour gérer des rubriques dans le centre de rubriques, vous devez :
- Vous avez une licence Topics.

- Avoir [**l'autorisation Qui peut gérer les rubriques.**](./topic-experiences-user-permissions.md) Les administrateurs du savoir peuvent accorder cette autorisation aux utilisateurs dans les paramètres des rubriques Topics. 

Vous ne pourrez pas afficher la page Gérer les rubriques dans le centre de rubriques, sauf si vous avez l'autorisation Qui peut gérer **les rubriques.**

Dans le centre de rubriques, un gestionnaire de connaissances peut consulter les rubriques qui ont été identifiées dans les emplacements sources SharePoint que vous avez spécifiés, et peut les confirmer ou les rejeter. Un gestionnaire de connaissances peut également créer et publier de nouvelles pages de rubriques si aucune page n'a été trouvée dans la découverte de rubrique, ou modifier des pages existantes si elles doivent être mises à jour.


## <a name="review-suggested-topics"></a>Consulter les rubriques suggérées

Dans la page Gérer les rubriques du centre de rubriques, les rubriques qui ont été découvertes dans les emplacements source SharePoint spécifiés sont répertoriées dans **l'onglet Suggestions.** Si nécessaire, un gestionnaire de connaissances peut consulter des rubriques non confirmées et choisir de les confirmer ou de les rejeter.

   ![Rubriques suggérées](../media/knowledge-management/quality-score.png) </br> 

Pour consulter une rubrique suggérée :

1. Dans la page Gérer les  **rubriques,** sélectionnez l'onglet Suggestions, sélectionnez la rubrique à ouvrir.</br>

2. Dans la page de rubrique, examinez la page de rubrique, puis sélectionnez **Modifier** si vous devez apporter des modifications à la page. La publication de toutes les modifications déplace cette rubrique vers **l'onglet** Publié.

3. Après avoir passé en revue la rubrique, revenir à la page Gérer les rubriques. Pour la rubrique sélectionnée, vous pouvez :

   - Cochez la coche pour confirmer la rubrique.
    
   - Sélectionnez **le x** si vous souhaitez rejeter la rubrique.

    Les rubriques confirmées sont supprimées de la liste **Suggérée** et s'affichent désormais dans **la liste** Confirmée.

    Les rubriques rejetées sont supprimées de la liste **Suggérée** et s'affichent désormais dans **l'onglet** Supprimé.

   </br> 

### <a name="quality-score"></a>Score de qualité

Un score de qualité est attribué à chaque rubrique qui apparaît sur votre page Rubriques suggérées. Le score de qualité reflète la quantité d'informations que l'utilisateur moyen verra pour les informations sur le sujet, en gardant à l'esprit que chaque utilisateur peut voir plus ou moins d'informations en raison des autorisations qu'il peut ou non avoir sur les informations d'une rubrique. 

Le score de qualité peut aider à donner un aperçu des rubriques les plus pertinentes et peut être utile pour trouver des rubriques qui peuvent avoir besoin d'être modifiées manuellement. Par exemple, une rubrique avec un score de qualité inférieur peut être le résultat de certains utilisateurs ne disposent pas des autorisations SharePoint pour les fichiers pertinents ou les sites que l'IA a inclus dans la rubrique. Un collaborateur peut ensuite modifier la rubrique pour inclure les informations (le cas échéant), qui seront ensuite consultables par tous les utilisateurs qui peuvent afficher la rubrique.

Le score de qualité peut être de 1 à 100. Une rubrique nouvellement découverte aura un score de qualité de 0 jusqu'à ce que deux utilisateurs ou plus l'ont vue. Le score de qualité de chaque utilisateur est déterminé par un certain nombre de facteurs, tels que la quantité de contenu affichée pour l'utilisateur spécifique, qui est contrôlée par les autorisations de l'utilisateur, car chaque page de rubrique dispose d'un trimming de sécurité pour le contenu généré par l'IA. Le score de qualité affiché sous **l'onglet Rubriques** suggérées est une moyenne de chaque score individuel de chaque utilisateur.

### <a name="impressions"></a>Impressions

La **colonne Impressions** affiche le nombre de fois qu'une rubrique a été présentée aux utilisateurs finaux. Cela inclut les affichages par le biais de cartes de rubrique dans la recherche, par le biais des points forts des rubriques et des affichages du centre de rubriques. Il ne reflète pas le clic sur ces rubriques, mais le fait que la rubrique a été affichée. La **colonne Impressions** s'affiche pour les rubriques des  onglets **Suggéré,** **Confirmé,** Publié et Supprimé de la page Gérer les rubriques.

## <a name="confirmed-topics"></a>Rubriques confirmées

Dans la page Gérer les rubriques, les rubriques qui ont été découvertes dans les emplacements source SharePoint spécifiés et qui ont été confirmées  par un gestionnaire de connaissances ou « en nombre de personnes » confirmées par deux ou plusieurs personnes via le mécanisme de commentaires de carte sont répertoriées dans l'onglet Confirmé. Si nécessaire, un utilisateur autorisé à gérer des rubriques peut passer en revue les rubriques confirmées et choisir de les rejeter.

Pour consulter une rubrique confirmée :

1. Sous **l'onglet Confirmé,** sélectionnez la rubrique pour ouvrir la page de rubrique.</br>

2. Dans la page de rubrique, examinez la page de rubrique, puis sélectionnez **Modifier** si vous devez apporter des modifications à la page.

Notez que vous pouvez toujours choisir de rejeter une rubrique confirmée. Pour ce faire, sélectionnez la  rubrique sélectionnée sous l'onglet Confirmé, puis sélectionnez **le x** si vous souhaitez rejeter la rubrique.

## <a name="published-topics"></a>Rubriques publiées
Les rubriques publiées ont été modifiées afin que des informations spécifiques apparaissent toujours aux personnes qui rencontrent la page. Les rubriques créées manuellement sont également répertoriées ici.

   ![Gérer les rubriques](../media/knowledge-management/manage-topics-new.png) </br>