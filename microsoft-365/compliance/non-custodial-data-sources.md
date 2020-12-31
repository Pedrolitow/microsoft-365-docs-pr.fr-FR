---
title: Ajout de sources de données non privatives de Troie à un cas avancé eDiscovery
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
description: Vous pouvez ajouter des sources de données non privatives de Troie à un cas avancé eDiscovery et mettre en attente la source de données. Les sources de données non privatives de cœur sont réindexées, de sorte que tout contenu marqué comme partiellement indexé est retraité afin de pouvoir faire l’objet d’une recherche complète et rapide.
ms.openlocfilehash: 467f0e1167bfebe21bd3f2bbd52acd81529b8685
ms.sourcegitcommit: 36d12e02f6fda199ae7f2fb72fe52d7e2b5b4efd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2020
ms.locfileid: "49740351"
---
# <a name="add-non-custodial-data-sources-to-an-advanced-ediscovery-case"></a>Ajout de sources de données non privatives de Troie à un cas avancé eDiscovery

Dans les cas de découverte électronique avancée, il ne répond pas toujours à vos besoins pour associer une source de données Microsoft 365 à un dépositaire dans le cas. Toutefois, vous devrez peut-être toujours associer ces données à un cas afin de pouvoir les Rechercher, de les ajouter à un jeu de révision et de les analyser et de les consulter. La fonctionnalité de Advanced eDiscovery est appelée *sources de données non privatives* et vous permet d’ajouter des données à un cas sans avoir à l’associer à un dépositaire. Elle applique également la même fonctionnalité eDiscovery avancée aux données non privatives de Troie qui sont disponibles pour les données associées aux dépositaires. Deux des éléments les plus utiles que vous pouvez appliquer à des données non privatives de temps sont mis en attente et traités à l’aide de l' [indexation avancée](indexing-custodian-data.md).

## <a name="add-a-non-custodial-data-source"></a>Ajouter une source de données non-privatives de cœur

Procédez comme suit pour ajouter et gérer des sources de données non privatives de Troie dans un cas avancé de découverte électronique.

1. Sur la page d’accueil de la **découverte électronique avancée** , cliquez sur le cas auquel vous souhaitez ajouter les données.

2. Cliquez sur l’onglet **sources de données** , puis cliquez sur **Ajouter une source** de données pour ajouter des  >  **emplacements de données**.

3. Sur la nouvelle page de menu volant **emplacements des données non privatives** de personnes, choisissez les sources de données que vous souhaitez ajouter à l’incident. Vous pouvez ajouter plusieurs boîtes aux lettres et sites en développant les sections **SharePoint** ou **Exchange** , puis en cliquant sur **modifier**.

   ![Ajouter des sites SharePoint et des boîtes aux lettres Exchange en tant que sources de données non privatives de cœur](../media/NonCustodialDataSources1.png)

   - **SharePoint** : cliquez sur **modifier** pour ajouter des sites. Sélectionnez un site dans la liste ou recherchez un site en tapant l’URL du site dans la barre de recherche. Sélectionnez les sites que vous souhaitez ajouter en tant que sources de données autres que les dépositaires, puis cliquez sur **Ajouter**.

   - **Exchange** -cliquez sur **modifier** pour ajouter des boîtes aux lettres. Tapez un nom ou un alias (un minimum de trois caractères) dans la zone de recherche pour les boîtes aux lettres ou les groupes de distribution. Sélectionnez les boîtes aux lettres que vous souhaitez ajouter en tant que sources de données autres que les dépositaires, puis cliquez sur **Ajouter**.

   > [!NOTE]
   > Vous pouvez utiliser les sections **SharePoint** et **Exchange** pour ajouter des sites et des boîtes aux lettres associés à une équipe ou un groupe yammer en tant que sources de données non-privatives de cœur. Vous devez ajouter séparément la boîte aux lettres et le site associés à une équipe ou un groupe Yammer.

4. Une fois que vous avez ajouté des sources de données non-privatives de place, vous avez la possibilité de placer ces emplacements en conservation. Activez ou désactivez la case à cocher **maintenir** en regard de la source de données pour la placer en conservation.

5. Cliquez sur **Ajouter** au bas de la nouvelle page de menu volant **emplacements des données non privatives** pour ajouter les sources de données au cas.

   Chaque source de données qui n’est pas une source de données non privatives ajoutée est indiquée dans la page **sources de données** . Les sources de données non privatives de cœur sont identifiées par la valeur d' **emplacement des données** dans la colonne **type de source** .

   ![Sources de données non privatives de Troie sous l’onglet sources de données](../media/NonCustodialDataSources2.png)

Une fois que vous avez ajouté des sources de données non-privatives de Troie, une tâche nommée *réindexation des données non privatives* est créée et affichée sous l’onglet **travaux** de l’incident. Une fois le travail créé, le processus d’indexation avancé dans initié et les sources de données sont réindexés.

## <a name="manage-the-hold-for-non-custodial-data-sources"></a>Gérer la conservation pour les sources de données non-privatives de cœur

Une fois que vous avez placé une conservation sur une source de données non privatives de place, une stratégie de blocage contenant les sources de données non privatives de l’incident est automatiquement créée. Lorsque vous placez d’autres sources de données qui ne sont pas privatives de place en conservation, elles sont ajoutées à cette stratégie de blocage.

1. Ouvrez le cas eDiscovery avancé et sélectionnez l’onglet **blocage** .

2. Cliquez sur **NCDSHold \<GUID\> -**, où la valeur GUID est unique pour le cas.

   La page de menu volant affiche des informations et des statistiques sur les sources de données non-privatives de stock en attente.

   ![La page de menu volant pour les sources de données non-privatives de ressources contient les statistiques](../media/NonCustodialDataSourcesHoldFlyout.png)

3. Cliquez sur **modifier le blocage** pour afficher les sources de données qui ne sont pas privatives de place et effectuez les tâches de gestion suivantes :

   - Sur la page **emplacements** , vous pouvez libérer une source de données non privatives de ressources en la supprimant de la conservation. La libération d’une source de données ne supprime pas la source de données non privatives de la casse. Il supprime uniquement le blocage passé sur la source de données.

   - Sur la page de **requête** , vous pouvez modifier la conservation pour créer une conservation basée sur une requête qui est appliquée à toutes les sources de données non-privatives Tha dans le cas.
