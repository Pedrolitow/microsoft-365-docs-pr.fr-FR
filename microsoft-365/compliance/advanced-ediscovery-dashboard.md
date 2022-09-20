---
title: Tableau de bord eDiscovery (Premium) pour les jeux de révision
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 04/05/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez le tableau de bord Microsoft Purview eDiscovery (Premium) pour les ensembles de révision afin d’analyser rapidement votre corpus afin d’identifier les tendances ou les statistiques clés qui vous aideront à développer votre stratégie de révision.
ms.openlocfilehash: 5d69f6caceba661546e98c5dd4dd0d52470fe9e8
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67824903"
---
# <a name="ediscovery-premium-dashboard-for-review-sets"></a>Tableau de bord eDiscovery (Premium) pour les jeux de révision

Dans certains cas, dans Microsoft Purview eDiscovery (Premium), vous pouvez avoir un grand volume de documents et de messages électroniques qui doivent être examinés. Avant de commencer le processus de révision, vous souhaiterez peut-être analyser rapidement votre corpus pour identifier les tendances ou les statistiques clés qui vous aideront à développer votre stratégie de révision. Pour ce faire, vous pouvez utiliser le tableau de bord eDiscovery (Premium) pour les ensembles de révision afin d’analyser rapidement votre corpus.

## <a name="step-1-create-a-widget-on-the-review-set-dashboard"></a>Étape 1 : Créer un widget dans le tableau de bord de l’ensemble de révisions

1. Dans le portail de conformité Microsoft Purview, accédez à **eDiscovery > eDiscovery (Premium)** pour afficher la liste des cas dans votre organisation.
  
2. Sélectionnez un cas existant.
  
3. Cliquez sur l’onglet **Ensemble** de révisions, puis sélectionnez un ensemble de révisions.
  
4. Dans la liste déroulante **résultats individuels**, cliquez sur **Rechercher un affichage du profil**. 

   ![DashboardPivot.](../media/dashboardpivot.png)

   La page **d’affichage du profil de recherche** s’affiche ; La première fois que vous affichez cette page, trois widgets par défaut sont affichés.

   ![Bord.](../media/dashboardonly.png)
  
5. Cliquez sur le **nouveau widget** , puis sélectionnez l’un des éléments suivants :

   ![Nouvelle liste déroulante de widgets.](../media/NewWidgetDropdownBox.png)

   - **Choisissez parmi la bibliothèque :** Affiche une bibliothèque de widgets par défaut. Vous cliquez sur un widget, puis cliquez sur **Ajouter** pour l’ajouter aux widgets dans la page **d’affichage du profil de recherche** .
  
   - **Créer un widget personnalisé :** Affiche une page de menu volant que vous pouvez utiliser pour configurer un widget personnalisé. 

6. Pour créer un widget personnalisé, procédez comme suit dans la page de menu volant **Ajouter un widget** :

   ![Créer un widget.](../media/addwidget.png)

    a. Tapez un nom pour le widget, qui s’affiche dans la barre de titre du widget. L’affectation d’un nom à un widget est nécessaire, mais il est utile d’identifier les données du widget.

    b. Sélectionnez une propriété dans la liste **déroulante Choisir un tableau croisé dynamique** qui sera utilisée pour les données du widget. Les éléments de cette liste sont les propriétés pouvant faire l’objet d’une recherche pour les éléments du jeu de révision. Pour obtenir une description de ces propriétés, consultez [les champs de métadonnées de document dans eDiscovery (Premium).](document-metadata-fields-in-Advanced-eDiscovery.md) Les options de tableau croisé dynamique du widget sont répertoriées dans la colonne **nom du champ Pouvant** faire l’objet d’une recherche dans cette rubrique.

    c. Sélectionnez un type de graphique pour afficher les données de la propriété de tableau croisé dynamique sélectionnée.

  6. Cliquez sur **Ajouter** pour créer le widget personnalisé et l’afficher dans la page **d’affichage du profil de recherche** .

## <a name="step-2-create-a-review-set-search-query"></a>Étape 2 : Créer une requête de recherche d’ensemble de révisions

1. Cliquez **sur ...** dans la barre de titre du widget, puis cliquez sur **Appliquer la condition**.

   ![Accueil du tableau de bord.](../media/searchprofilehome.png)

2. Dans la page de menu volant, cliquez sur un élément dans la clé du widget ou le graphique du widget pour créer un filtre.

   ![CreateFilter.](../media/applyconditionfilter.png)

3. Répétez les étapes 1 à 2 pour d’autres widgets. 

4. Lorsque vous avez terminé, cliquez sur **Enregistrer en tant que requête** pour enregistrer vos conditions en tant que nouvelle requête de recherche pour le jeu de révisions.

   ![Requête.](../media/savequery.png)

5. Fermez la **vue Profil de recherche** pour revenir à l’affichage des résultats de la recherche.

   Si vous avez créé des filtres visuels, la requête résultante est appliquée aux résultats de recherche affichés, et la requête de recherche que vous avez enregistrée à l’étape 4 s’affiche sous **Requêtes enregistrées**. Pour plus d’informations sur les requêtes d’ensemble de révision, consultez [Interroger les données d’un jeu de révision](review-set-search.md).
