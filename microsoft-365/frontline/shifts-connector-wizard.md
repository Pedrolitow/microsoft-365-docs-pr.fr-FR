---
title: Utilisez l’Assistant Connecteur Shifts pour connecter Shifts à Blue Yonder Workforce Management
author: lanachin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez comment utiliser l’Assistant Connecteur Shifts pour intégrer Shifts dans Teams à Blue Yonder Workforce Management.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
- highpri
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 6a1062fe9e06e0b73f2c8eebd8f17b87684c0709
ms.sourcegitcommit: 99b174a8d431092b3cf7d650593248671297fd91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68300444"
---
# <a name="use-the-shifts-connector-wizard-to-connect-shifts-to-blue-yonder-workforce-management"></a>Utilisez l’Assistant Connecteur Shifts pour connecter Shifts à Blue Yonder Workforce Management

## <a name="overview"></a>Vue d’ensemble

[!INCLUDE [shifts-connector-wizard-intro](includes/shifts-connector-wizard-intro.md)]

## <a name="integrate-shifts-with-blue-yonder-workforce-management"></a>Intégrer Shifts à Blue Yonder Workforce Management

Le [connecteur Microsoft Teams Shifts pour Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder) vous permet d’intégrer Shifts à Blue Yonder Workforce Management (Blue Yonder WFM) pour gérer vos planifications et les tenir à jour. Dans cet article, nous vous présentons comment exécuter l’Assistant pour configurer une connexion à Blue Yonder WFM via le connecteur.

> [!NOTE]
> Vous pouvez également utiliser PowerShell pour intégrer Shifts à Blue Yonder WFM. Pour en savoir plus, consultez [Utiliser PowerShell pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-blue-yonder-powershell-setup.md).

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être administrateur général de Microsoft 365 pour exécuter l’Assistant.

### <a name="prerequisites"></a>Configuration requise
<a name="prerequisites"> </a>
[!INCLUDE [shifts-connector-prerequisites](includes/shifts-connector-prerequisites.md)]

- Les équipes que vous souhaitez mapper n’ont pas de planification. Si une équipe a une planification existante, [supprimez-la de l’équipe](#remove-schedules-from-teams-you-want-to-map) avant d’y mapper une instance Blue Yonder WFM. Sinon, vous verrez des shifts en double.

## <a name="remove-schedules-from-teams-you-want-to-map"></a>Supprimer les planifications des équipes que vous souhaitez mapper
<a name="remove_schedules"> </a>

> [!NOTE]
> Effectuez cette étape si vous mappez des instances Blue Yonder WFM à des équipes existantes. Si vous mappez à des équipes qui n’ont pas de planification ou si vous créez de nouvelles équipes à mapper, vous pouvez ignorer cette étape.

Utilisez PowerShell pour supprimer des planifications des équipes.

1. Tout d’abord, vous devez installer les modules PowerShell et être configuré. Suivez les étapes pour [configurer votre environnement](shifts-connector-powershell-manage.md#set-up-your-environment)
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
1. Dans la page Choisir votre connecteur, choisissez **Blue Yonder Workforce Management**, puis sélectionnez **Suivant** pour créer une connexion Blue Yonder WFM.

### <a name="enter-connection-details"></a>Entrer les détails de la connexion
<a name="connection_details"> </a>

1. Dans la page Détails de la connexion, donnez un nom unique à votre connexion. Il ne peut pas dépasser 128 caractères ou comporter des caractères spéciaux.
    :::image type="content" source="media/shifts-connector-wizard-connection-details.png" alt-text="Capture d’écran de la page Détails de la connexion de l’Assistant, montrant les paramètres de connexion." lightbox="media/shifts-connector-wizard-connection-details.png":::
1. Entrez le nom de votre compte de service WFM bleu, ainsi que le mot de passe et les URL de service.
1. Lorsque vous avez terminé, sélectionnez **Suivant** pour tester la connexion avec les paramètres que vous avez entrés.

### <a name="choose-sync-settings"></a>Choisir les paramètres de synchronisation
<a name="sync"> </a>

Dans la page Paramètres de synchronisation, vous choisissez les informations à synchroniser de Blue Yonder WFM à Shifts, la fréquence de synchronisation et si les utilisateurs de Shifts peuvent apporter des modifications aux données.

1. Entrez votre compte système Microsoft 365.
    :::image type="content" source="media/shifts-connector-wizard-sync-settings.png" alt-text="Capture d’écran de la page Synchroniser les paramètres de l’Assistant, montrant les paramètres de synchronisation." lightbox="media/shifts-connector-wizard-sync-settings.png":::
<a name="email"> </a>
1. Sous **Destinataires des notifications par e-mail**, choisissez qui reçoit les notifications par e-mail concernant cette connexion. Vous pouvez ajouter des utilisateurs et des groupes individuels. Les notifications par e-mail contiennent des informations sur l’état de l’installation de la connexion et sur les éventuels problèmes ou erreurs susceptibles de se produire après la configuration de la connexion.
1. Choisissez vos paramètres de synchronisation :
    1. Sous **Planification et shifts**, choisissez les données WFM Blue Yonder que les utilisateurs de Shifts peuvent voir ou modifier, puis définissez la fréquence de synchronisation.
    1. Sous **Carte de temps**, choisissez l’action que les utilisateurs peuvent effectuer avec les entrées de temps.
    1. Sous **Demandes**, choisissez les types de demandes que les utilisateurs Shifts peuvent voir et créer.

    > [!IMPORTANT]
    > Si vous avez choisi l’une des options suivantes pour désactiver les shifts ouverts, les demandes de shift ouverts, les demandes d’échange ou les demandes de congé, vous devez effectuer une autre étape pour masquer la fonctionnalité dans Shifts.
    >
    > - Ouvrir les shifts : **les utilisateurs de Shifts ne verront pas les données Blue Yonder WFM**
    > - Demandes d’échange : **la fonctionnalité est désactivée pour tous les utilisateurs**
    > - Demandes de congé : **la fonctionnalité est désactivée pour tous les utilisateurs**
    >
    > Après avoir exécuté l’Assistant, veillez à suivre les étapes décrites dans la section [Désactiver les shifts ouverts, les demandes de shifts ouverts, les demandes de permutation et les demandes de congés](#disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests) plus loin dans cet article.
 
1. Lorsque vous avez fini de choisir vos paramètres, sélectionnez **Créer une connexion**.

### <a name="map-blue-yonder-workforce-management-instances-to-teams"></a>Mapper les instances Blue Yonder Workforce Management aux équipes
<a name="sites"> </a>

Choisissez les instances Blue Yonder WFM que vous souhaitez connecter à Shifts, puis mappez chaque instance à une équipe dans Teams. Vous pouvez mapper jusqu’à 100 instances. Vous pouvez procéder de deux manières :

- [Mapper manuellement des instances à des équipes](#manually-map-instances-to-teams)
- [Préparer et charger un fichier CSV qui définit vos mappages](#use-a-csv-file-to-map-instances-to-teams)

#### <a name="manually-map-instances-to-teams"></a>Mapper manuellement des instances à des équipes

Sélectionnez les instances que vous souhaitez mapper.

:::image type="content" source="media/shifts-connector-wizard-sites.png" alt-text="Capture d’écran de l’Assistant, montrant la liste des instances Blue Yonder WFM." lightbox="media/shifts-connector-wizard-sites.png":::
<a name="mapping"> </a>
<a name="search_teams"> </a> Ensuite, mappez chaque instance à une équipe dans Teams. Vous pouvez mapper une instance à une équipe existante ou créer une équipe.
:::image type="content" source="media/shifts-connector-wizard-search-team.png" alt-text="Capture d’écran du volet montrant l’option d’équipe de recherche et créer une option d’équipe." lightbox="media/shifts-connector-wizard-search-team.png":::

[!INCLUDE [shifts-connector-manually-map-instances](includes/shifts-connector-manually-map-instances.md)]

#### <a name="use-a-csv-file-to-map-instances-to-teams"></a>Utiliser un fichier CSV pour mapper des instances à des équipes

1. Sélectionnez **passer en mode bloc**.
1. Sélectionnez **télécharger un fichier de modèle** pour télécharger un modèle de mappage que vous pouvez utiliser pour définir vos mappages.

    :::image type="content" source="media/shifts-connector-wizard-mapping-file.png" alt-text="Capture d’écran de la page Charger le fichier de mappage de l’Assistant." lightbox="media/shifts-connector-wizard-mapping-file.png":::

1. Utilisez le modèle pour créer votre fichier de mappage. Il contient ces colonnes, dans l’ordre suivant, en commençant par la première colonne. Un astérisque (*) indique une colonne obligatoire.

    |Nom de colonne  |Description  |
    |---------|---------|
    |**ID d’instance Blue Yonder*** |ID d’instance Blue Yonder WFM.|
    |**Nom de l’instance Blue Yonder**|Nom de l’instance Blue Yonder WFM.|
    |**ID d’équipe*** |ID d’équipe.|
    |**Nom de l’équipe**|Nom de l’équipe.|
    |**Fuseau horaire*** |Fuseau horaire au format de base de données tz. Par exemple, Europe/Londres.|

    > [!NOTE]
    > Vous devez uniquement remplir les colonnes requises (ID d’instance Blue Yonder, ID d’équipe, fuseau horaire) pour mapper des instances à des équipes.

    Voici un exemple de ce à quoi ressemble un fichier de mappage.

    |ID d’instance Blue Yonder|Nom de l’instance Blue Yonder|ID d’équipe|Nom de l’équipe|Fuseau horaire|
    |---------|---------|---------|---------|---------|
    |2111|Contoso US Team|3a4d78a-2261|Équipe des États-Unis|Amérique/Los_Angeles|
    |3212|Contoso UK Team|2d1f6c2e-5272|Équipe du Royaume-Uni|Europe/Londres|
    |4865||bfa6o89e-1328||Amérique/Toronto|

1. Une fois que vous avez créé votre fichier de mappage, sélectionnez **Parcourir** pour le charger. L’Assistant valide votre fichier. S’il détecte des erreurs, vous verrez une liste des erreurs et un message vous demandant de les corriger. Sinon, vous verrez un message pour passer à l’étape suivante.  
1. Sélectionnez **Suivant**.

### <a name="review-and-finish"></a>Vérifier et terminer

Revoir vos paramètres. Si vous devez apporter des modifications aux mappages d’équipe, choisissez **Modifier** pour ce faire. Lorsque vous êtes prêt, sélectionnez **Terminer**.

:::image type="content" source="media/shifts-connector-wizard-review.png" alt-text="Capture d’écran de la page Révision de l’Assistant, montrant les mappages." lightbox="media/shifts-connector-wizard-review.png":::

Vous verrez un message pour confirmer que nous avons reçu votre demande ainsi qu’un ID d’opération. Notez l’ID d’opération. Vous en aurez besoin pour vérifier l’état d’installation de votre connexion.

:::image type="content" source="media/shifts-connector-wizard-operation-id.png" alt-text="Capture d’écran de la page de l’Assistant, montrant le message de confirmation et l’ID d’opération." lightbox="media/shifts-connector-wizard-operation-id.png":::

L’Assistant démarre le processus pour configurer la connexion et mapper les instances aux équipes que vous avez sélectionnées. Ce processus peut prendre un certain temps. Les destinataires que vous avez choisis recevront des notifications par e-mail concernant l’état de l’installation.

Sélectionnez **Terminé** pour quitter l’Assistant.

Vous êtes sur la bonne voie, mais vous n’avez pas encore terminé ! Veillez à vérifier votre adresse e-mail. Vous recevrez une confirmation que nous avons reçu votre demande, ainsi qu’un [lien](shifts-connector-powershell-manage.md#check-connection-setup-status) vers la façon dont vous pouvez vérifier l’état de l’installation.

> [!NOTE]
> Si un problème ou une erreur se produit dans une connexion après sa configuration, vous êtes averti par e-mail. Suivez les instructions de l’e-mail pour résoudre le problème.

## <a name="disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests"></a>Désactiver les shifts ouverts, les demandes de shifts ouverts, les demandes de permutation et les demandes de congés.

> [!IMPORTANT]
> Suivez ces étapes uniquement si vous avez choisi l’une des options suivantes pour désactiver les shifts ouverts, les demandes de shift ouverts, les demandes d’échange ou les demandes de congé dans l’Assistant. L’exécution de cette étape masque la fonctionnalité dans Shifts.
>
> - Ouvrir les shifts : **les utilisateurs de Shifts ne verront pas les données Blue Yonder WFM**
> - Demandes d’échange : **la fonctionnalité est désactivée pour tous les utilisateurs**
> - Demandes de congé : **la fonctionnalité est désactivée pour tous les utilisateurs**
>
> Sans cette deuxième étape, les utilisateurs verront toujours la fonctionnalité dans Shifts et recevront un message d’erreur « opération non prise en charge » s’ils essaient de l’utiliser.

Pour masquer les équipes ouvertes, les demandes de permutation et les demandes de congés dans les équipes, utilisez le [type de ressource de planification](/graph/api/resources/schedule) de l’API graphique pour définir les paramètres suivants pour```false``` chaque équipe que vous avez associée à une instance WFM Blue Yonder :

- Ouvrir les shifts : ```openShiftsEnabled```
- Demandes d’échange :  ```swapShiftsRequestsEnabled```
- Demandes de congé : ```timeOffRequestsEnabled```

Pour masquer les demandes de shifts ouverts dans Shifts, accédez à **Paramètres** dans Shifts, puis désactivez le paramètre **Ouvrir les shifts** .

## <a name="manage-your-connection"></a>Gérer votre connexion
<a name="update_connection"> </a>

Une fois la connexion configurée, vous pouvez la gérer et y apporter des modifications dans le Centre d'administration Microsoft 365 ou à l’aide de PowerShell.

### <a name="use-the-microsoft-365-admin-center"></a>Utiliser le Centre d'administration Microsoft 365

La page Gestion des connecteurs répertorie chaque connexion que vous avez configurée, ainsi que des informations telles que l’état d’intégrité et les détails de l’intervalle de synchronisation. Vous pouvez également accéder à l’Assistant pour apporter des modifications à l’une de vos connexions. Par exemple, vous pouvez mettre à jour les paramètres de synchronisation et les mappages d’équipe.

Pour plus d’informations, consultez [Utiliser le Centre d'administration Microsoft 365 pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-blue-yonder-admin-center-manage.md).

### <a name="use-powershell"></a>Utiliser PowerShell

Vous pouvez utiliser PowerShell pour afficher un rapport d’erreurs, modifier les paramètres de connexion, désactiver la synchronisation, etc. Pour obtenir des instructions pas à pas, consultez [Utiliser PowerShell pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-powershell-manage.md).

## <a name="related-articles"></a>Articles connexes

- [Connecteurs de Plannings](shifts-connectors.md)
- [Gérer l’application Shifts pour votre organisation dans Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
