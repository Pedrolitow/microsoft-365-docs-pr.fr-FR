---
title: Tableau de bord eDiscovery avancé pour les ensembles de révision
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
description: Utilisez le tableau de bord eDiscovery avancé pour les ensembles de vérification pour analyser rapidement votre corpus afin d’identifier des tendances ou des statistiques clés qui vous aideront à développer votre stratégie de révision.
ms.openlocfilehash: 36f30689047eec7ff2c2c49c6b0d54f1a60470e4
ms.sourcegitcommit: 956dd3f87adb4e6173517550a662c3bacc2d2d79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "44741698"
---
# <a name="advanced-ediscovery-dashboard-for-review-sets"></a>Tableau de bord eDiscovery avancé pour les ensembles de révision

Dans certains cas de Advanced eDiscovery, il se peut que vous ayez un grand volume de documents et de messages électroniques qui doivent être vérifiés. Avant de commencer le processus de révision, vous souhaiterez peut-être analyser rapidement votre corpus pour identifier des tendances ou des statistiques clés qui vous aideront à développer votre stratégie de révision. Pour ce faire, vous pouvez utiliser le tableau de bord eDiscovery avancé pour les ensembles de vérification pour analyser rapidement votre corpus.

## <a name="step-1-create-a-widget-on-the-review-set-dashboard"></a>Étape 1 : créer un widget dans le tableau de bord de l’ensemble de révision

1. Dans le centre de sécurité & conformité, accédez à **ediscovery > Advanced eDiscovery** pour afficher la liste des incidents de votre organisation.
  
2. Sélectionnez un cas existant.
  
3. Cliquez sur l’onglet **examiner l’ensemble** , puis sélectionnez un jeu de révision.
  
4. Dans la liste déroulante **résultats individuels** , cliquez sur **affichage du profil de recherche**. 

   ![DashbordPivot](../media/dashboardpivot.png)

   La page **afficher le profil de recherche** s’affiche ; la première fois que vous Affichez cette page, trois widgets par défaut sont affichés.

   ![Tableau de bord](../media/dashboardonly.png)
  
5. Cliquez sur le **nouveau widget** , puis sélectionnez l’un des éléments suivants :

   ![Liste déroulante nouveau widget](../media/NewWidgetDropdownBox.png)

   - **Choisissez dans la bibliothèque :** Affiche une bibliothèque par défaut de widgets. Cliquez sur un widget, puis cliquez sur **Ajouter** pour l’ajouter aux widgets sur la page **mode profil de recherche** .
  
   - **Créer un widget personnalisé :** Affiche une page de menu volant que vous pouvez utiliser pour configurer un widget personnalisé. 

6. Pour créer un widget personnalisé, procédez comme suit sur la page du menu volant **Ajouter un widget** :

   ![Créer un widget](../media/addwidget.png)

    a. Tapez un nom pour le widget, qui s’affiche dans la barre de titre du widget. Il est nécessaire d’attribuer un nom à un widget, mais il est utile d’identifier les données du widget.

    b. Sélectionnez une propriété dans la liste déroulante **choisir un tableau croisé dynamique** qui sera utilisée pour les données du widget. Les éléments de cette liste sont les propriétés pouvant faire l’objet d’une recherche pour les éléments dans l’ensemble de révision. Pour obtenir une description de ces propriétés, voir [document Metadata Fields in Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md). Les options de tableau croisé dynamique pour le widget sont répertoriées dans la colonne **nom de champ pouvant** faire l’objet d’une recherche dans cette rubrique.

    c. Sélectionnez un type de graphique pour afficher les données de la propriété de tableau croisé dynamique sélectionnée.

  6. Cliquez sur **Ajouter** pour créer le widget personnalisé et l’afficher sur la page **mode profil de recherche** .

## <a name="step-2-create-a-review-set-search-query"></a>Étape 2 : créer une requête de recherche Set Review

1. Cliquez sur **...** dans la barre de titre du widget, puis cliquez sur **appliquer la condition**.

   ![Tableau de bord](../media/searchprofilehome.png)

2. Sur la page de la fenêtre volante, cliquez sur un élément dans la touche du widget ou le graphique du widget pour créer un filtre.

   ![CreateFilter](../media/applyconditionfilter.png)

3. Répétez les étapes 1-2 pour d’autres widgets plusieurs widgets. 

4. Lorsque vous avez fini, cliquez sur **enregistrer en tant que requête** pour enregistrer vos conditions en tant que nouvelle requête de recherche pour l’ensemble de révision.

   ![Requête](../media/savequery.png)

5. Fermez l' **affichage profil de recherche** pour revenir à l’affichage des résultats de la recherche.

   Si vous avez créé des filtres visuels, la requête qui en résulte est appliquée aux résultats de la recherche qui sont affichés et la requête de recherche que vous avez enregistrée à l’étape 4 s’affiche sous **requêtes enregistrées**. Pour plus d’informations sur les requêtes Set de révision, voir [query the Data in a Review Set](review-set-search.md).
