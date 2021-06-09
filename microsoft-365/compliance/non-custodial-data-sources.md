---
title: Ajouter des sources de données non privatives à un Advanced eDiscovery de données
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
description: Vous pouvez ajouter des sources de données non privatives à un Advanced eDiscovery et placer une mise en attente sur la source de données. Les sources de données non privatives sont réindexées, de sorte que tout contenu marqué comme partiellement indexé est retrait pour le rendre entièrement et rapidement utilisable dans une recherche.
ms.openlocfilehash: 467f0e1167bfebe21bd3f2bbd52acd81529b8685
ms.sourcegitcommit: 36d12e02f6fda199ae7f2fb72fe52d7e2b5b4efd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2020
ms.locfileid: "49740351"
---
# <a name="add-non-custodial-data-sources-to-an-advanced-ediscovery-case"></a>Ajouter des sources de données non privatives à un Advanced eDiscovery de données

Dans Advanced eDiscovery cas, il ne répond pas toujours à vos besoins d’associer une source de données Microsoft 365 à un dépositaire dans le cas. Toutefois, vous devrez peut-être associer ces données à un cas afin de pouvoir les rechercher, les ajouter à un groupe de révision, les analyser et les réviser. La fonctionnalité dans Advanced eDiscovery est appelée sources de données *non* privatives et vous permet d’ajouter des données à un cas sans avoir à les associer à un dépositaire. Il applique également la même fonctionnalité Advanced eDiscovery aux données non privatives disponibles pour les données associées au dépositaire. L’une des choses les plus utiles que vous pouvez appliquer aux données non privatives est de les placer en attente et de les traiter à l’aide de [l’indexation avancée](indexing-custodian-data.md).

## <a name="add-a-non-custodial-data-source"></a>Ajouter une source de données non privative

Suivez ces étapes pour ajouter et gérer des sources de données non privatives dans Advanced eDiscovery cas.

1. Dans la **Advanced eDiscovery** page d’accueil, cliquez sur le cas où vous souhaitez ajouter les données.

2. Cliquez sur **l’onglet Sources** de données, puis sur **Ajouter une source** de données Ajouter des  >  **emplacements de données.**

3. Dans la page **De nouveaux emplacements** de données non privatives, choisissez les sources de données que vous souhaitez ajouter au cas. Vous pouvez ajouter plusieurs boîtes aux lettres et sites en développez les sections **SharePoint** ou **Exchange** puis en cliquant sur **Modifier.**

   ![Ajouter SharePoint sites et boîtes Exchange aux lettres en tant que sources de données non privatives](../media/NonCustodialDataSources1.png)

   - **SharePoint** - Cliquez sur **Modifier** pour ajouter des sites. Sélectionnez un site dans la liste ou vous pouvez rechercher un site en tapant l’URL du site dans la barre de recherche. Sélectionnez les sites que vous souhaitez ajouter en tant que sources de données non dépositaires, puis cliquez sur **Ajouter.**

   - **Exchange** - Cliquez sur **Modifier** pour ajouter des boîtes aux lettres. Tapez un nom ou un alias (un minimum de trois caractères) dans la zone de recherche pour les boîtes aux lettres ou les groupes de distribution. Sélectionnez les boîtes aux lettres que vous souhaitez ajouter en tant que sources de données non dépositaires, puis cliquez sur **Ajouter**.

   > [!NOTE]
   > Vous pouvez utiliser les sections **SharePoint** et **Exchange** pour ajouter des sites et des boîtes aux lettres associés à une équipe ou un groupe Yammer en tant que sources de données non privatives. Vous devez ajouter séparément la boîte aux lettres et le site associés à une équipe ou Yammer groupe.

4. Après avoir ajouté des sources de données non privatives, vous avez la possibilité de placer ou non ces emplacements en attente. Cochez ou désélectionnez la case **à** cocher De hold en regard de la source de données pour la placer en attente.

5. Cliquez **sur Ajouter** au bas de la page volant Nouveaux emplacements de données **non** privatives pour ajouter les sources de données au cas.

   Chaque source de données non privative que vous avez ajoutée est répertoriée dans la page **Sources de** données. Les sources de données non privatives sont identifiées par la valeur **d’emplacement des** données dans la **colonne Type de** source.

   ![Sources de données non privatives sous l’onglet Sources de données](../media/NonCustodialDataSources2.png)

Une fois que vous avez ajouté des sources de données non privatives au cas,  un travail nommé *Réindexation* des données non privatives est créé et affiché sous l’onglet Travaux du cas. Une fois le travail créé, le processus d’indexation avancée est lancé et les sources de données sont réindexées.

## <a name="manage-the-hold-for-non-custodial-data-sources"></a>Gérer la mise en attente pour les sources de données non privatives

Après avoir mis en attente une source de données non privative, une stratégie de mise en attente contenant les sources de données non privatives du cas est automatiquement créée. Lorsque vous placez d’autres sources de données non privatives en attente, elles sont ajoutées à cette stratégie de mise en attente.

1. Ouvrez le Advanced eDiscovery et sélectionnez **l’onglet** Conserver.

2. Cliquez **sur NCDSHold- \<GUID\>**, où la valeur GUID est propre au cas.

   La page volante affiche des informations et des statistiques sur les sources de données qui ne sont pas en attente.

   ![La page de présentation des sources de données non privatives affiche des statistiques](../media/NonCustodialDataSourcesHoldFlyout.png)

3. Cliquez **sur Modifier la** mise en attente pour afficher les sources de données non privatives placées en attente et effectuer les tâches de gestion suivantes :

   - Dans la page **Emplacements,** vous pouvez libérer une source de données qui n’est pas en attente en la supprimant de la mise en attente. La libération d’une source de données ne supprime pas la source de données non privative du cas. Elle supprime uniquement la mise en attente qui a été placée sur la source de données.

   - Dans **la** page Requête, vous pouvez modifier la mise en attente pour créer une mise en attente basée sur une requête qui est appliquée à toutes les sources de données sans mise en attente dans le cas.
