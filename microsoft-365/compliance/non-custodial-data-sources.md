---
title: Ajouter des sources de données non liées à la garde à un cas eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Vous pouvez ajouter des sources de données non liées à la garde à un cas eDiscovery (Premium) et placer une conservation sur la source de données. Les sources de données non liées à la garde sont réindexées. Par conséquent, tout contenu marqué comme partiellement indexé est retraité pour le rendre entièrement et rapidement consultable.
ms.openlocfilehash: bb5ff8a4a58e62d3f4bf36f7c7e1e9001d829036
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625124"
---
# <a name="add-non-custodial-data-sources-to-an-ediscovery-premium-case"></a>Ajouter des sources de données non liées à la garde à un cas eDiscovery (Premium)

Dans Microsoft Purview eDiscovery cas (Premium), il ne répond pas toujours à vos besoins d’associer une source de données Microsoft 365 à un consignateur dans le cas. Toutefois, vous devrez peut-être toujours associer ces données à un cas afin de pouvoir les rechercher, les ajouter à un ensemble de révisions et les analyser et les examiner. La fonctionnalité dans eDiscovery (Premium) est appelée *sources de données non gardiennes* et vous permet d’ajouter des données à un cas sans avoir à l’associer à un consignateur. Il applique également la même fonctionnalité eDiscovery (Premium) aux données non gardiennes qui sont disponibles pour les données associées au consignateur. L’une des choses les plus utiles que vous pouvez appliquer aux données non liées à la garde consiste à les mettre en attente et à les traiter à l’aide de [l’indexation avancée](indexing-custodian-data.md).

## <a name="add-a-non-custodial-data-source"></a>Ajouter une source de données non custodiale

Suivez ces étapes pour ajouter et gérer des sources de données non liées à la garde dans un cas eDiscovery (Premium).

1. Dans la page d’accueil **eDiscovery (Premium),** cliquez sur le cas auquel vous souhaitez ajouter les données.

2. Cliquez sur l’onglet **Sources** de données, puis sur **Ajouter une source de** > **données Ajouter des emplacements de données**.

3. Dans la page de menu volant **Nouveaux emplacements de données non liés** à la garde, choisissez les sources de données que vous souhaitez ajouter au cas. Vous pouvez ajouter plusieurs boîtes aux lettres et sites en développant les sections **SharePoint** ou **Exchange** , puis en cliquant sur **Modifier**.

   ![Ajoutez des sites SharePoint et des boîtes aux lettres Exchange en tant que sources de données non liées à la garde.](../media/NonCustodialDataSources1.png)

   - **SharePoint** - Cliquez sur **Modifier** pour ajouter des sites. Sélectionnez un site dans la liste ou vous pouvez rechercher un site en tapant l’URL du site dans la barre de recherche. Sélectionnez les sites que vous souhaitez ajouter en tant que sources de données non gardiennes, puis cliquez sur **Ajouter**.

   - **Exchange** - Cliquez sur **Modifier** pour ajouter des boîtes aux lettres. Tapez un nom ou un alias (au moins trois caractères) dans la zone de recherche des boîtes aux lettres ou des groupes de distribution. Sélectionnez les boîtes aux lettres que vous souhaitez ajouter en tant que sources de données non gardiennes, puis cliquez sur **Ajouter**.

   > [!NOTE]
   > Vous pouvez utiliser les sections **SharePoint** et **Exchange** pour ajouter des sites et des boîtes aux lettres associés à un groupe Team ou Yammer en tant que sources de données non liées à la garde. Vous devez ajouter séparément la boîte aux lettres et le site associés à un groupe Team ou Yammer.<br/><br/> En outre, l’ajout d’une URL de site racine (telle que `https://contoso-my.sharepoint.com/personal/` ou  `https://contoso-my.sharepoint.com/`) en tant que source de données SharePoint n’est pas pris en charge. Vous devez ajouter des sites spécifiques.

4. Une fois que vous avez ajouté des sources de données non liées à la garde, vous avez la possibilité de mettre ces emplacements en attente ou non. Cochez ou désélectionnez la case à cocher **En** regard de la source de données pour la mettre en attente.

5. Cliquez sur **Ajouter** en bas de la page volant **Nouveaux emplacements de données non liés** à la garde pour ajouter les sources de données au cas.

   Chaque source de données non liée à la garde que vous avez ajoutée est répertoriée dans la page **Sources de données** . Les sources de données non liées à la garde sont identifiées par la valeur **d’emplacement des données** dans la colonne **de type source** .

   ![Sources de données non liées à la garde sous l’onglet Sources de données.](../media/NonCustodialDataSources2.png)

Une fois que vous avez ajouté des sources de données non liées à la garde au cas, un travail nommé *Réindexation des données non liées à la garde* est créé et affiché sous l’onglet **Travaux** du cas. Une fois le travail créé, le processus d’indexation avancé lancé et les sources de données sont réindexés.

## <a name="manage-the-hold-for-non-custodial-data-sources"></a>Gérer la conservation des sources de données non liées à la garde

Une fois que vous avez placé une conservation sur une source de données non-custodiale, une stratégie de conservation qui contient les sources de données non-custodiales pour le cas est automatiquement créée. Lorsque vous mettez en attente d’autres sources de données non liées à la conservation, elles sont ajoutées à cette stratégie de conservation.

1. Ouvrez le cas eDiscovery (Premium) et **sélectionnez** l’onglet Maintenir.

2. Cliquez sur **NCDSHold-\<GUID\>**, où la valeur GUID est unique au cas.

   La page de menu volant affiche des informations et des statistiques sur les sources de données non liées à la garde en attente.

   ![La page de menu volant pour les sources de données non liées à la conservation affiche des statistiques.](../media/NonCustodialDataSourcesHoldFlyout.png)

3. Cliquez sur **Modifier la conservation** pour afficher les sources de données non liées à la conservation et effectuer les tâches de gestion suivantes :

   - Dans la page **Emplacements** , vous pouvez libérer une source de données non gardienne en la supprimant de la conservation. La libération d’une source de données ne supprime pas la source de données non gardienne du cas. Il supprime uniquement la conservation qui a été placée sur la source de données.

   - Dans la page **Requête** , vous pouvez modifier la conservation pour créer une conservation basée sur une requête qui est appliquée à toutes les sources de données non-custodiales tha dans le cas.
