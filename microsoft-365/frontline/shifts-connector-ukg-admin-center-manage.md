---
title: Utilisez la Centre d'administration Microsoft 365 pour gérer votre connexion Shifts aux dimensions UKG
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez comment gérer votre connexion Shifts aux dimensions UKG dans le Centre d'administration Microsoft 365.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 2cae342f25941347c52b5cf4028976da3ef545c4
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68234219"
---
# <a name="use-the-microsoft-365-admin-center-to-manage-your-shifts-connection-to-ukg-dimensions"></a>Utilisez la Centre d'administration Microsoft 365 pour gérer votre connexion Shifts aux dimensions UKG

[!INCLUDE [preview-feature](includes/preview-feature.md)]

## <a name="overview"></a>Vue d’ensemble

Le [connecteur Microsoft Teams Shifts pour UKG Dimensions](shifts-connectors.md#microsoft-teams-shifts-connector-for-ukg-dimensions) vous permet d’intégrer l’application Shifts dans Microsoft Teams à UKG Dimensions. Après avoir configuré une connexion, vos employés de première ligne peuvent afficher et gérer en toute transparence leurs planifications dans UKG Dimensions à partir de Shifts.

Vous pouvez utiliser [l’Assistant Connecteur Shifts](shifts-connector-wizard-ukg.md) dans le Centre d'administration Microsoft 365 ou [PowerShell](shifts-connector-ukg-powershell-setup.md) pour créer une connexion. Une fois qu’une connexion est configurée, vous pouvez la gérer dans le Centre d'administration Microsoft 365. La page Gestion des connecteurs répertorie chaque connexion que vous avez configurée, ainsi que des informations telles que l’état d’intégrité et les détails de l’intervalle de synchronisation. Vous pouvez également accéder à l’Assistant pour créer une connexion ou apporter des modifications à l’une de vos connexions existantes. Par exemple, vous pouvez mettre à jour les paramètres de synchronisation et les mappages d’équipe.

> [!NOTE]
> Vous pouvez également utiliser PowerShell pour gérer une connexion. Par exemple, vous pouvez afficher un rapport d’erreurs, modifier les paramètres de connexion et désactiver la synchronisation. Pour en savoir plus, consultez [Utiliser PowerShell pour gérer votre connexion Shifts aux dimensions UKG](shifts-connector-ukg-powershell-manage.md).

## <a name="manage-your-connection"></a>Gérer votre connexion

1. Dans le volet de navigation gauche de [l’Centre d'administration Microsoft 365](https://admin.microsoft.com/), choisissez **Configurer**, puis sous **Collections de** fonctionnalités, sélectionnez **Les travailleurs de première ligne**.
2. Sélectionnez **Gérer les connecteurs Shifts**, puis choisissez **Gérer**. N’oubliez pas que cette option n’est disponible que si vous avez configuré au moins une connexion, à l’aide de l’Assistant ou de PowerShell.

    Ici, vous verrez une liste de toutes les connexions que vous avez configurées via l’Assistant ou PowerShell, ainsi que des informations sur chacune d’elles.

    :::image type="content" source="media/shifts-connector-ukg-manage.png" alt-text="Capture d’écran de la page Gestion des connecteurs dans le Centre d'administration Microsoft 365, montrant une liste de connexions." lightbox="media/shifts-connector-ukg-manage.png":::

    - Pour créer une connexion, sélectionnez **Ajouter un connecteur** en haut de la page pour démarrer l’Assistant.

    - Pour afficher plus de détails sur une connexion, cliquez sur le nom de la connexion. Dans la page d’informations, vous verrez des informations d’intégrité, notamment des erreurs de mappage et d’autorisation de compte (le cas échéant), la liste des mappages (le cas échéant) et bien plus encore. Vous pouvez également choisir **Modifier** pour mettre à jour les paramètres de connexion dans l’Assistant.

      :::image type="content" source="media/shifts-connector-ukg-manage-details.png" alt-text="Capture d’écran de la page de détails d’une connexion, montrant les informations d’intégrité et de mappage du connecteur." lightbox="media/shifts-connector-ukg-manage-details.png":::

         Pour obtenir la liste complète des messages d’erreur et comment les résoudre, consultez [La liste des messages d’erreur](#list-of-error-messages) plus loin dans cet article.

    - Pour apporter des modifications à une connexion, **choisissez Modifier** en regard de la connexion. Vous accédez à l’Assistant, où vous pouvez mettre à jour les paramètres souhaités.
  
> [!NOTE]
> Vous pouvez également accéder directement à la page Gestion des connecteurs lorsque vous sélectionnez le bouton **Gestion des connecteurs** sur la dernière page de l’Assistant lors de l’installation de la connexion.

## <a name="list-of-error-messages"></a>Liste des messages d’erreur

Voici la liste des messages d’erreur que vous pouvez rencontrer et des informations pour vous aider à les résoudre.

|Type d’erreur |Détails de l’erreur |Résolution |
|---------|---------|---------|
|Impossible d’authentifier le système de gestion de la main-d’œuvre.|Les informations d’identification du compte du système de gestion du personnel que vous avez fournies ne sont pas valides ou ce compte ne dispose pas des autorisations requises.|Mettez à jour les informations d’identification de votre compte de service WFM dans les paramètres de connexion. Pour cela, appliquez l’une des méthodes suivantes :<ul><li>Dans le Centre d'administration Microsoft 365, choisissez **Modifier** dans la page Gestion des connecteurs ou la page des détails de connexion pour accéder à l’Assistant Connecteur Shifts.</li><li>Utilisez l’applet de commande [Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance) ou Update-CsTeamsShiftConnectionInstance.</li><li>Utilisez [ce script PowerShell](shifts-connector-ukg-powershell-manage.md#change-connection-settings).</li></ul>|
|Impossible d’authentifier Graph. |Échec de l’authentification. Vérifiez que vous avez entré des informations d’identification valides pour l’acteur désigné et que vous disposez des autorisations requises.|Assurez-vous que votre compte système Microsoft 365 (également appelé acteur désigné) est ajouté en tant que propriétaire d’équipe.<br> Vous pouvez également mettre à jour les informations d’identification de votre compte système Microsoft 365 dans les paramètres de connexion.|
|Certains utilisateurs n’ont pas pu mapper correctement|Le mappage a échoué pour certains utilisateurs : \<X\> utilisateurs AAD ayant \<X\> échoué et \<X\> utilisateurs du système de gestion de la main-d’œuvre défaillants.|Utilisez l’applet de commande [Get-CsTeamsShiftsConnectionSyncResult](/powershell/module/teams/get-csteamsshiftsconnectionsyncresult) ou [ce script PowerShell](shifts-connector-ukg-powershell-manage.md#user-mapping-errors) pour identifier les utilisateurs pour lesquels le mappage a échoué. Assurez-vous que les utilisateurs de l’équipe mappée correspondent aux utilisateurs de l’instance WFM.|
|Impossible de mapper une équipe ou des équipes dans ce lot. |Ce profil d’acteur désigné n’a pas de privilèges de propriété d’équipe. |Assurez-vous que votre compte système Microsoft 365 (également appelé acteur désigné) est ajouté en tant que propriétaire d’équipe.<br>Si vous avez modifié votre compte système Microsoft 365, ajoutez ce compte en tant que propriétaire d’équipe et mettez à jour les paramètres de connexion pour utiliser ce compte.|
|    |Cette équipe est déjà mappée à une instance de connecteur existante. |Supprimez l’équipe de la connexion existante à l’aide de l’applet de commande [Remove-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/remove-csteamsshiftsconnectionteammap) . Vous pouvez également créer une connexion pour remapper l’équipe.|
|    |Ce fuseau horaire n’est pas valide. Le fuseau horaire passé n’utilise pas le format de base de données tz.|Vérifiez que le fuseau horaire est correct, puis remapper l’équipe.|
|    |Nous ne trouvons pas cette instance de connecteur.|Mappez l’équipe à une connexion existante.|
|    |Cette équipe AAD est introuvable.|Assurez-vous que l’équipe existe ou créez-en une.|

## <a name="related-articles"></a>Articles connexes

- [Connecteurs de Plannings](shifts-connectors.md)
- [Utiliser l’Assistant Connecteur Shifts pour connecter Shifts aux dimensions UKG](shifts-connector-wizard-ukg.md)
- [Utiliser PowerShell pour connecter shifts aux dimensions UKG](shifts-connector-ukg-powershell-setup.md)
- [Utiliser PowerShell pour gérer votre connexion Shifts aux dimensions UKG](shifts-connector-ukg-powershell-manage.md)
- [Gérer l’application Shifts](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)