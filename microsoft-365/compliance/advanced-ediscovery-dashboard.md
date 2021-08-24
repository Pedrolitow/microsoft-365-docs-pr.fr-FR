---
title: Advanced eDiscovery tableau de bord pour les ensembles de révision
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez le tableau Advanced eDiscovery tableau de bord pour les ensembles de révision afin d’analyser rapidement votre corpus afin d’identifier les tendances ou les statistiques clés qui vous aideront à développer votre stratégie de révision.
ms.openlocfilehash: 14baa47a73ac3cc4917d6e2f04614a80960ef085
ms.sourcegitcommit: 4582873483bd52bc790bf75b838cc505dc4bbeb4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2021
ms.locfileid: "58502974"
---
# <a name="advanced-ediscovery-dashboard-for-review-sets"></a>Advanced eDiscovery tableau de bord pour les ensembles de révision

Dans certains cas, Advanced eDiscovery, il se peut que vous devrez examiner un grand nombre de documents et de messages électroniques. Avant de commencer le processus de révision, vous pouvez analyser rapidement votre corpus afin d’identifier les tendances ou les statistiques clés qui vous aideront à développer votre stratégie de révision. Pour ce faire, vous pouvez utiliser le tableau de bord Advanced eDiscovery pour les ensembles de révision afin d’analyser rapidement votre corpus.

## <a name="step-1-create-a-widget-on-the-review-set-dashboard"></a>Étape 1 : Créer un widget sur le tableau de bord du jeu à réviser

1. Dans la Centre de conformité Microsoft 365, allez à **eDiscovery > Advanced eDiscovery** pour afficher la liste des cas dans votre organisation.
  
2. Sélectionnez un cas existant.
  
3. Cliquez sur **l’onglet Ensemble** de révision, puis sélectionnez un ensemble de révision.
  
4. Dans la liste déroulante **résultats individuels**, cliquez sur **Rechercher un affichage du profil**. 

   ![DashbordPivot](../media/dashboardpivot.png)

   La page **d’affichage de profil** de recherche s’affiche . La première fois que vous affichez cette page, trois widgets par défaut sont affichés.

   ![Tableau de bord](../media/dashboardonly.png)
  
5. Cliquez sur **le widget Nouveau,** puis sélectionnez l’un des éléments suivants :

   ![Liste de listes des nouveaux widgets](../media/NewWidgetDropdownBox.png)

   - **Choisissez dans la bibliothèque :** Affiche une bibliothèque par défaut de widgets. Vous cliquez sur un widget, puis sur **Ajouter** pour l’ajouter aux widgets dans la page d’affichage **de profil de** recherche.
  
   - **Créez un widget personnalisé :** Affiche une page de présentation que vous pouvez utiliser pour configurer un widget personnalisé. 

6. Pour créer un widget personnalisé, dans la page volant Ajouter un **widget,** vous pouvez :

   ![Créer un widget](../media/addwidget.png)

    a. Tapez un nom pour le widget, qui s’affiche dans la barre de titre du widget. L’attribution d’un nom à un widget est requise, mais il est utile d’identifier les données du widget.

    b. Sélectionnez une propriété dans la **liste de** listes de listes listes de sélection du tableau croisé dynamique qui sera utilisée pour les données du widget. Les éléments de cette liste sont les propriétés utilisables dans une recherche pour les éléments du jeu à réviser. Pour obtenir une description de ces propriétés, voir champs de [métadonnées](document-metadata-fields-in-Advanced-eDiscovery.md)de document Advanced eDiscovery . Les options de tableau croisé dynamique pour le widget sont répertoriées dans la colonne **Nom** de champ utilisable dans une recherche dans cette rubrique.

    c. Sélectionnez un type de graphique pour afficher les données de la propriété de tableau croisé dynamique sélectionnée.

  6. Cliquez **sur Ajouter** pour créer le widget personnalisé et l’afficher sur la page d’affichage de profil **de** recherche.

## <a name="step-2-create-a-review-set-search-query"></a>Étape 2 : Créer une requête de recherche de jeu à réviser

1. Cliquez **sur...** dans la barre de titre du widget, puis cliquez sur **Appliquer la condition.**

   ![Tableau de bord](../media/searchprofilehome.png)

2. Dans la page volante, cliquez sur un élément de la clé du widget ou du graphique de widget pour créer un filtre.

   ![CreateFilter](../media/applyconditionfilter.png)

3. Répétez les étapes 1 à 2 pour d’autres widgets avec plusieurs widgets. 

4. Lorsque vous avez terminé, cliquez sur **Enregistrer** sous la requête pour enregistrer vos conditions en tant que nouvelle requête de recherche pour le jeu à réviser.

   ![Requête](../media/savequery.png)

5. Fermez **l’affichage de profil de** recherche pour revenir à l’affichage des résultats de la recherche.

   Si vous avez créé des filtres visuels, la requête qui en résulte est appliquée aux résultats de recherche qui sont affichés et la requête de recherche que vous avez enregistrée à l’étape 4 s’affiche sous Requêtes **enregistrées.** Pour plus d’informations sur les requêtes de jeu à réviser, voir [Interroger les données dans un jeu à réviser.](review-set-search.md)
