---
title: Utilisez le Centre d'administration Microsoft 365 pour gérer votre connexion Shifts à Blue Yonder Workforce Management
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez comment gérer votre connexion Shifts à Blue Yonder Workforce Management dans le Centre d'administration Microsoft 365.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: d89e0c65c22995d10ddadf9e2e8789a2cd2152f9
ms.sourcegitcommit: 3d7dd25abcbf923b45eae84ff4d9d2bb95ef4ca4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68777967"
---
# <a name="use-the-microsoft-365-admin-center-to-manage-your-shifts-connection-to-blue-yonder-workforce-management"></a>Utilisez le Centre d'administration Microsoft 365 pour gérer votre connexion Shifts à Blue Yonder Workforce Management

## <a name="overview"></a>Vue d’ensemble

Le [connecteur Microsoft Teams Shifts pour Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder) vous permet d’intégrer l'application Shifts dans Microsoft Teams avec Blue Yonder Workforce Management (Blue Yonder WFM). Une fois que vous avez configuré une connexion, vos employés de première ligne peuvent afficher et gérer en toute transparence leurs plannings dans le WFM Blue Yonder à partir de Shifts.

Vous pouvez utiliser [l’Assistant Connecteur Shifts](shifts-connector-wizard.md) dans le Centre d'administration Microsoft 365 ou [PowerShell](shifts-connector-blue-yonder-powershell-setup.md) pour créer une connexion. Une fois qu’une connexion est configurée, vous pouvez la gérer dans le Centre d'administration Microsoft 365. La page Gestion des connecteurs répertorie chaque connexion que vous avez configurée, ainsi que des informations telles que l’état d’intégrité et les détails de l’intervalle de synchronisation. Vous pouvez également accéder à l’Assistant pour créer une connexion ou apporter des modifications à l’une de vos connexions existantes. Par exemple, vous pouvez mettre à jour les paramètres de synchronisation et les mappages d’équipe.

> [!NOTE]
> Vous pouvez également utiliser PowerShell pour gérer une connexion. Par exemple, vous pouvez afficher un rapport d’erreurs, modifier les paramètres de connexion et désactiver la synchronisation. Pour en savoir plus, consultez [Utiliser PowerShell pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-powershell-manage.md).

## <a name="manage-your-connection"></a>Gérer votre connexion

1. Dans le volet de navigation gauche du [Centre d'administration Microsoft 365](https://admin.microsoft.com/), choisissez **Configuration**, puis sous **Collections proposées**, sélectionnez **Employés de première ligne**.
2. Sélectionnez **Gérer les connecteurs Shifts**, puis choisissez **Gérer**. Gardez à l’esprit que cette option n’est disponible que si vous avez configuré au moins une connexion, à l’aide de l’Assistant ou de PowerShell.

    Ici, vous verrez une liste de toutes les connexions que vous avez configurées via l’Assistant ou PowerShell, ainsi que des informations sur chacune d’elles. 

    :::image type="content" source="media/shifts-connector-blue-yonder-manage.png" alt-text="Capture d’écran de la page Gestion des connecteurs dans le Centre d'administration Microsoft 365, montrant une liste de connexions." lightbox="media/shifts-connector-blue-yonder-manage.png":::

    - Pour créer une connexion, sélectionnez **Ajouter un connecteur** en haut de la page pour démarrer l’Assistant.
    - Pour afficher plus de détails sur une connexion, cliquez sur le nom de la connexion. Sur la page de détails, vous verrez des informations d’intégrité, notamment des erreurs et des avertissements d’autorisation de mappage et de compte (le cas échéant), la liste des mappages (le cas échéant) et bien plus encore. Vous pouvez également choisir **Modifier** pour mettre à jour les paramètres de connexion dans l’Assistant.

      :::image type="content" source="media/shifts-connector-blue-yonder-manage-details.png" alt-text="Capture d’écran de la page de détails d’une connexion, montrant des informations sur l’intégrité et les mappages du connecteur." lightbox="media/shifts-connector-blue-yonder-manage-details.png":::

        Pour obtenir la liste complète des messages d’erreur et savoir comment les résoudre, consultez [Liste des messages d’erreur](#list-of-error-messages) plus loin dans cet article.

    - Pour apporter des modifications à une connexion, choisissez **Modifier** en regard de la connexion. Vous êtes dirigé vers l’Assistant, où vous pouvez mettre à jour les paramètres souhaités.
  
> [!NOTE]
> Vous pouvez également accéder directement à la page Gestion des connecteurs lorsque vous sélectionnez le bouton **Gestion des connecteurs** dans la dernière page de l’Assistant pendant la configuration de la connexion.

## <a name="list-of-error-messages"></a>Liste des messages d’erreur

Voici la liste des messages d’erreur que vous pouvez rencontrer et des informations pour vous aider à les résoudre.

|Type d’erreur |Détails de l’erreur |Résolution |
|---------|---------|---------|
|Impossible d’authentifier le système de gestion du personnel.|Les informations d’identification du compte système de gestion de la main-d’œuvre que vous avez fournies ne sont pas valides ou ce compte ne dispose pas des autorisations requises.|Mettez à jour les informations d’identification de votre compte de service WFM dans les paramètres de connexion. Pour cela, appliquez l’une des méthodes suivantes :<ul><li>Dans la Centre d'administration Microsoft 365, choisissez **Modifier** dans la page Gestion des connecteurs ou dans la page des détails de connexion pour accéder à l’Assistant Connecteur Shifts.</li><li>Utilisez l’applet de [commande Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance) ou [Update-CsTeamsShiftsConnectionInstance](/powershell/module/teams/update-csteamsshiftsconnectioninstance) .</li><li>Utilisez [ce script PowerShell](shifts-connector-powershell-manage.md#change-connection-settings).</li></ul>|
|Impossible d’authentifier Graph. |Échec de l’authentification. Vérifiez que vous avez entré des informations d’identification valides pour l’acteur désigné et que vous disposez des autorisations requises.|Assurez-vous que votre compte système Microsoft 365 (également appelé acteur désigné) est ajouté en tant que propriétaire d’équipe.<br> Vous pouvez également mettre à jour les informations d’identification de votre compte système Microsoft 365 dans les paramètres de connexion.|
|Certains utilisateurs n’ont pas pu mapper correctement|Le mappage a échoué pour certains utilisateurs : \<X\> réussite, \<X\> échec des utilisateurs AAD et \<X\> échec du ou des utilisateurs du système de gestion de la main-d’œuvre.|Utilisez l’applet de commande [Get-CsTeamsShiftsConnectionSyncResult](/powershell/module/teams/get-csteamsshiftsconnectionsyncresult) ou [ce script PowerShell](shifts-connector-powershell-manage.md#user-mapping-errors) pour identifier les utilisateurs pour lesquels le mappage a échoué. Assurez-vous que les utilisateurs de l’équipe mappée correspondent aux utilisateurs de l’instance WFM.|
|Impossible de mapper une équipe ou des équipes dans ce lot. |Ce profil d’acteur désigné n’a pas de privilèges de propriété d’équipe. |Assurez-vous que votre compte système Microsoft 365 (également appelé acteur désigné) est ajouté en tant que propriétaire d’équipe.<br>Si vous avez modifié votre compte système Microsoft 365, ajoutez ce compte en tant que propriétaire d’équipe et mettez à jour les paramètres de connexion pour utiliser ce compte.|
|    |Cette équipe est déjà mappée à une instance de connecteur existante. |Annulez le mappage de l’équipe de la connexion existante à l’aide de l’applet de commande [Remove-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/remove-csteamsshiftsconnectionteammap) . Vous pouvez également créer une connexion pour remapper l’équipe.|
|    |Ce fuseau horaire n’est pas valide. Le fuseau horaire passé n’utilise pas le format de base de données tz.|Vérifiez que le fuseau horaire est correct, puis remapper l’équipe.|
|    |Nous ne trouvons pas cette instance de connecteur.|Mappez l’équipe à une connexion existante.|
|    |Cette équipe AAD est introuvable.|Assurez-vous que l’équipe existe ou créez-en une.|

## <a name="related-articles"></a>Articles connexes

- [Connecteurs de Plannings](shifts-connectors.md)
- [Utiliser l’Assistant Connecteur Shifts pour connecter Shifts à Blue Yonder Workforce Management](shifts-connector-wizard.md)
- [Utiliser PowerShell pour connecter Shifts à Blue Yonder Workforce Management](shifts-connector-blue-yonder-powershell-setup.md)
- [Utilisez PowerShell pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-powershell-manage.md)
- [Gérer l’application Shifts](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
