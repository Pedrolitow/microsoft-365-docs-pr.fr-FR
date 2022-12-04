---
title: Utiliser l’Assistant Connecteur Shifts pour connecter Shifts à UKG Dimensions
author: lanachin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: how-to
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez comment utiliser l’Assistant Connecteur Shifts pour intégrer Shifts dans Teams à UKG Dimensions.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: e660bd7aa5cf34498f4c7e590c9eae5d09d23cea
ms.sourcegitcommit: 0ad7edcfdcdd11d02fa8a14ffe4b36e120d92deb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2022
ms.locfileid: "68786780"
---
# <a name="use-the-shifts-connector-wizard-to-connect-shifts-to-ukg-dimensions"></a>Utiliser l’Assistant Connecteur Shifts pour connecter Shifts à UKG Dimensions

## <a name="overview"></a>Vue d’ensemble

[!INCLUDE [preview-feature](includes/preview-feature.md)]

[!INCLUDE [shifts-connector-wizard-intro](includes/shifts-connector-wizard-intro.md)]

## <a name="integrate-shifts-with-ukg-dimensions"></a>Intégrer Shifts aux dimensions UKG

Le [connecteur Microsoft Teams Shifts pour UKG Dimensions](shifts-connectors.md#microsoft-teams-shifts-connector-for-ukg-dimensions) vous permet d’intégrer Shifts à UKG Dimensions pour gérer vos planifications et les tenir à jour. Dans cet article, nous vous guiderons tout au long de l’exécution de l’Assistant pour configurer une connexion à UKG Dimensions via le connecteur.

> [!NOTE]
> Vous pouvez également utiliser PowerShell pour intégrer Shifts à UKG Dimensions. Pour en savoir plus, consultez [Utiliser PowerShell pour connecter Shifts à UKG Dimensions](shifts-connector-ukg-powershell-setup.md).

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être administrateur général de Microsoft 365 pour exécuter l’Assistant.

<a name="prerequisites"> </a>
### <a name="prerequisites"></a>Conditions préalables
[!INCLUDE [shifts-connector-ukg-prerequisites](includes/shifts-connector-ukg-prerequisites.md)]

- Les équipes que vous souhaitez mapper n’ont pas de planification. Si une équipe a une planification existante, [supprimez la planification de l’équipe](#remove-schedules-from-teams-you-want-to-map) avant de lui mapper une instance UKG Dimensions. Sinon, vous verrez des shifts en double.

<a name="remove_schedules"> </a>
## <a name="remove-schedules-from-teams-you-want-to-map"></a>Supprimer les planifications des équipes que vous souhaitez mapper

> [!NOTE]
> Effectuez cette étape si vous mappez des instances UKG Dimensions à des équipes existantes qui ont des planifications. Si vous mappez à des équipes qui n’ont pas de planification ou si vous créez de nouvelles équipes à mapper, vous pouvez ignorer cette étape.

Utilisez PowerShell pour supprimer des planifications des équipes.

1. Tout d’abord, vous devez installer les modules PowerShell et être configuré. Suivez les étapes pour [configurer votre environnement](shifts-connector-ukg-powershell-manage.md#set-up-your-environment)
1. Exécutez la commande suivante :

    ```powershell
    Remove-CsTeamsShiftsScheduleRecord -TeamId <Teams team ID> -DateRangeStartDate <start time> -DateRangeEndDate <end time> -ClearSchedulingGroup:$false -EntityType <the scenario entities that you want to remove, the format is @(scenario1, scenario2, ...)> -DesignatedActorId <Teams team owner ID>
    ```

    Pour obtenir la liste des scénarios pour le paramètre `EntityType`, exécutez [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector). Les données de planification seront supprimées pour l’intervalle de date et d’heure que vous spécifiez.

Pour en savoir plus, consultez la rubrique [Remove-CsTeamsShiftsScheduleRecord](/powershell/module/teams/remove-csteamsshiftsschedulerecord).

## <a name="run-the-wizard"></a>Lancer l’Assistant Installation

### <a name="get-started"></a>Prise en main

1. Dans le volet de navigation gauche du [Centre d’administration Microsoft 365](https://admin.microsoft.com/), choisissez **Configurer**, puis accédez à la section **Applications et e-mail** .
1. Sélectionnez **Connecter votre système de gestion du personnel**. Ici, vous pouvez en savoir plus sur les connecteurs Shifts et l’expérience de travail et de gestionnaire de première ligne lorsque vous connectez Shifts à votre système WFM.
    :::image type="content" source="media/shifts-connector-wizard-get-started.png" alt-text="Capture d’écran de la page de détails de l’Assistant Connecteur Shifts dans le Centre d’administration Microsoft 365." lightbox="media/shifts-connector-wizard-get-started.png":::
1. Lorsque vous êtes prêt, sélectionnez **Démarrage**.
1. Dans la page Choisir votre connecteur, choisissez **Dimensions UKG**, puis sélectionnez **Suivant** pour créer une connexion UKG Dimensions.

<a name="connection_details"> </a>
### <a name="enter-connection-details"></a>Entrer les détails de la connexion

1. Dans la page Détails de la connexion, donnez un nom unique à votre connexion. Il ne peut pas dépasser 128 caractères ou comporter des caractères spéciaux.
    :::image type="content" source="media/shifts-connector-wizard-ukg-connection-details.png" alt-text="Capture d’écran de la page Détails de la connexion de l’Assistant, montrant les paramètres de connexion." lightbox="media/shifts-connector-wizard-ukg-connection-details.png":::
1. Entrez le nom de votre compte de service UKG Dimensions (qui permet d’accéder à toutes les instances créées dans UKG Dimensions) et le mot de passe et les URL de service.
1. Lorsque vous avez terminé, sélectionnez **Suivant** pour tester la connexion avec les paramètres que vous avez entrés.

<a name="sync"> </a>
### <a name="choose-sync-settings"></a>Choisir les paramètres de synchronisation

Dans la page Paramètres de synchronisation, vous choisissez les informations à synchroniser entre ukG Dimensions et Shifts, la fréquence de synchronisation et indique si les utilisateurs shifts peuvent apporter des modifications aux données.

1. Entrez votre compte système Microsoft 365.
    :::image type="content" source="media/shifts-connector-wizard-ukg-sync-settings.png" alt-text="Capture d’écran de la page Synchroniser les paramètres de l’Assistant, montrant les paramètres de synchronisation." lightbox="media/shifts-connector-wizard-ukg-sync-settings.png":::
<a name="email"> </a>
1. Sous **Destinataires des notifications par e-mail**, choisissez qui reçoit les notifications par e-mail concernant cette connexion. Vous pouvez ajouter des utilisateurs et des groupes individuels. Les notifications par e-mail contiennent des informations sur l’état de l’installation de la connexion et sur les éventuels problèmes ou erreurs susceptibles de se produire après la configuration de la connexion.
1. Choisissez vos paramètres de synchronisation :
    1. Sous **Planification et shifts**, choisissez les données de dimensions UKG que les utilisateurs shifts peuvent voir ou modifier, puis définissez la fréquence de synchronisation.
    1. Sous **Carte de temps**, choisissez l’action Shifts que les utilisateurs peuvent faire avec les entrées de temps.
    1. Sous **Demandes**, choisissez les types de demandes que les utilisateurs Shifts peuvent voir et créer.

    > [!IMPORTANT]
    > Si vous avez choisi l’une des options suivantes pour désactiver les shifts ouverts, les demandes de shift ouverts, les demandes d’échange ou les demandes de congé, vous devez effectuer une autre étape pour masquer la fonctionnalité dans Shifts.
    >
    > - Équipes ouvertes : **les utilisateurs shifts ne verront pas les données de dimensions UKG**
    > - Demandes d’échange : **la fonctionnalité est désactivée pour tous les utilisateurs**
    > - Demandes de congé : **la fonctionnalité est désactivée pour tous les utilisateurs**
    >
    > Après avoir exécuté l’Assistant, veillez à suivre les étapes décrites dans la section [Désactiver les shifts ouverts, les demandes de shifts ouverts, les demandes de permutation et les demandes de congés](#disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests) plus loin dans cet article.
 
1. Lorsque vous avez fini de choisir vos paramètres, sélectionnez **Créer une connexion**.

<a name="instances"> </a>
### <a name="map-ukg-dimensions-instances-to-teams"></a>Mapper des instances UKG Dimensions à des équipes

Choisissez les instances UKG Dimensions que vous souhaitez connecter à Shifts, puis mappez chaque instance à une équipe dans Teams. Vous pouvez mapper jusqu’à 100 instances. Vous pouvez procéder de deux manières :

- [Mapper manuellement des instances à des équipes](#manually-map-instances-to-teams)
- [Préparer et charger un fichier CSV qui définit vos mappages](#use-a-csv-file-to-map-instances-to-teams)

<a name="map_manual"> </a>
#### <a name="manually-map-instances-to-teams"></a>Mapper manuellement des instances à des équipes

Sélectionnez les instances que vous souhaitez mapper.

:::image type="content" source="media/shifts-connector-wizard-ukg-sites.png" alt-text="Capture d’écran de l’Assistant, montrant la liste des instances UKG Dimensions." lightbox="media/shifts-connector-wizard-ukg-sites.png":::

 Ensuite, mappez chaque instance à une équipe dans Teams. Vous pouvez mapper une instance à une équipe existante ou créer une équipe.
:::image type="content" source="media/shifts-connector-wizard-ukg-search-team.png" alt-text="Capture d’écran du volet montrant l’option d’équipe de recherche et créer une option d’équipe." lightbox="media/shifts-connector-wizard-ukg-search-team.png":::

[!INCLUDE [shifts-connector-manually-map-instances](includes/shifts-connector-manually-map-instances.md)]

<a name="map_csv"> </a>
#### <a name="use-a-csv-file-to-map-instances-to-teams"></a>Utiliser un fichier CSV pour mapper des instances à des équipes

1. Sélectionnez **passer en mode bloc**.
1. Sélectionnez **télécharger un fichier de modèle** pour télécharger un modèle de mappage que vous pouvez utiliser pour définir vos mappages.

    :::image type="content" source="media/shifts-connector-wizard-ukg-mapping-file.png" alt-text="Capture d’écran de la page Charger le fichier de mappage de l’Assistant." lightbox="media/shifts-connector-wizard-ukg-mapping-file.png":::

1. Utilisez le modèle pour créer votre fichier de mappage. Il contient ces colonnes, dans l’ordre suivant, en commençant par la première colonne. Un astérisque (*) indique une colonne obligatoire.

    |Nom de colonne  |Description  |
    |---------|---------|
    |**ID d’instance de dimensions UKG*** |L’ID d’instance ukG Dimensions WFM.|
    |**Nom de l’instance dimensions UKG**|Nom de l’instance UKG Dimensions WFM.|
    |**ID d’équipe*** |ID d’équipe.|
    |**Nom de l’équipe**|Nom de l’équipe.|
    |**Fuseau horaire*** |Fuseau horaire au format de base de données tz. Par exemple, Europe/Londres.|

    > [!NOTE]
    > Vous devez uniquement remplir les colonnes requises (ID d’instance de dimensions UKG, ID d’équipe, fuseau horaire) pour mapper les instances aux équipes.

    Pour vous aider à créer votre fichier de mappage, le modèle inclut une liste de toutes vos instances UKG Dimensions, suivie d’une liste de vos équipes (jusqu’à 1 000) et de leurs ID d’équipe correspondants.

    Voici un exemple de ce à quoi ressemble un fichier de mappage.

    |ID d’instance de dimensions UKG|Nom de l’instance dimensions UKG|ID d’équipe|Nom de l’équipe|Fuseau horaire|
    |---------|---------|---------|---------|---------|
    |4201|CO/Australie|ee0bbc99-7120||Australie/Sydney|
    |4203|CO/US|90db4db7-be44|Équipe des États-Unis|Amérique/New_York|
    |4251||c88b4ead-c965||Europe/Londres|

1. Une fois que vous avez créé votre fichier de mappage, sélectionnez **Parcourir** pour le charger. L’Assistant valide votre fichier. S’il détecte des erreurs, vous verrez une liste des erreurs et un message vous demandant de les corriger. Sinon, vous verrez un message pour passer à l’étape suivante.  
1. Sélectionnez **Suivant**.

### <a name="review-and-finish"></a>Vérifier et terminer

Revoir vos paramètres. Si vous devez apporter des modifications aux mappages d’équipe, choisissez **Modifier** pour ce faire. Lorsque vous êtes prêt, sélectionnez **Terminer**.

:::image type="content" source="media/shifts-connector-wizard-ukg-review.png" alt-text="Capture d’écran de la page Révision de l’Assistant, montrant les mappages." lightbox="media/shifts-connector-wizard-ukg-review.png":::

Vous verrez un message pour confirmer que nous avons reçu votre demande ainsi qu’un ID d’opération. Notez l’ID d’opération. Vous en aurez besoin pour vérifier l’état d’installation de votre connexion.

:::image type="content" source="media/shifts-connector-wizard-ukg-operation-id.png" alt-text="Capture d’écran de la page de l’Assistant, montrant le message de confirmation et l’ID d’opération." lightbox="media/shifts-connector-wizard-ukg-operation-id.png":::

L’Assistant démarre le processus pour configurer la connexion et mapper les instances aux équipes que vous avez sélectionnées. Ce processus peut prendre un certain temps. Les destinataires que vous avez choisis recevront des notifications par e-mail concernant l’état de l’installation.

Sélectionnez **Terminé** pour quitter l’Assistant.

Vous êtes sur la bonne voie, mais vous n’avez pas encore terminé ! Veillez à vérifier votre adresse e-mail. Vous recevrez une confirmation que nous avons reçu votre demande, ainsi qu’un [lien](shifts-connector-ukg-powershell-manage.md#check-connection-setup-status) vers la façon dont vous pouvez vérifier l’état de l’installation.

> [!NOTE]
> Si un problème ou une erreur se produit dans une connexion après sa configuration, vous êtes averti par e-mail. Suivez les instructions de l’e-mail pour résoudre le problème.

## <a name="disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests"></a>Désactiver les shifts ouverts, les demandes de shifts ouverts, les demandes de permutation et les demandes de congés.

> [!IMPORTANT]
> Suivez ces étapes uniquement si vous avez choisi l’une des options suivantes pour désactiver les shifts ouverts, les demandes de shift ouverts, les demandes d’échange ou les demandes de congé dans l’Assistant. L’exécution de cette étape masque la fonctionnalité dans Shifts.
>
> - Équipes ouvertes : **les utilisateurs shifts ne verront pas les données de dimensions UKG**
> - Demandes d’échange : **la fonctionnalité est désactivée pour tous les utilisateurs**
> - Demandes de congé : **la fonctionnalité est désactivée pour tous les utilisateurs**
>
> Sans cette deuxième étape, les utilisateurs verront toujours la fonctionnalité dans Shifts et recevront un message d’erreur « opération non prise en charge » s’ils essaient de l’utiliser.

Pour masquer les shifts ouverts, les demandes d’échange et les demandes de congé dans Shifts, utilisez le [type de ressource de planification](/graph/api/resources/schedule) API Graph pour définir les paramètres ```false``` suivants pour chaque équipe que vous avez mappée à une instance UKG Dimensions :

- Ouvrir les shifts : ```openShiftsEnabled```
- Demandes d’échange :  ```swapShiftsRequestsEnabled```
- Demandes de congé : ```timeOffRequestsEnabled```

Pour masquer les demandes de shifts ouverts dans Shifts, accédez à **Paramètres** dans Shifts, puis désactivez le paramètre **Ouvrir les shifts** .

<a name="manage"> </a>
## <a name="manage-your-connection"></a>Gérer votre connexion

Une fois la connexion configurée, vous pouvez la gérer et y apporter des modifications dans le Centre d'administration Microsoft 365 ou à l’aide de PowerShell.

### <a name="use-the-microsoft-365-admin-center"></a>Utiliser le Centre d'administration Microsoft 365

La page Gestion des connecteurs répertorie chaque connexion que vous avez configurée, ainsi que des informations telles que l’état d’intégrité et les détails de l’intervalle de synchronisation. Vous pouvez également accéder à l’Assistant pour apporter des modifications à vos connexions. Par exemple, vous pouvez mettre à jour les paramètres de synchronisation et les mappages d’équipe.

Pour plus d’informations, consultez [Utiliser la Centre d'administration Microsoft 365 pour gérer votre connexion Shifts aux dimensions UKG](shifts-connector-ukg-admin-center-manage.md).

### <a name="use-powershell"></a>Utiliser PowerShell

Vous pouvez utiliser PowerShell pour afficher un rapport d’erreurs, modifier les paramètres de connexion, désactiver la synchronisation, etc. Pour obtenir des instructions pas à pas, consultez [Utiliser PowerShell pour gérer votre connexion Shifts à UKG Dimensions](shifts-connector-ukg-powershell-manage.md).

## <a name="related-articles"></a>Articles connexes

- [Connecteurs de Plannings](shifts-connectors.md)
- [Gérer l’application Shifts pour votre organisation dans Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)