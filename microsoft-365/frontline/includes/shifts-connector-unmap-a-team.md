---
author: LanaChin
ms.author: v-lanachin
ms.date: ''
ms.topic: include
audience: admin
ms.service: microsoft-365-frontline
ms.openlocfilehash: ec11ee0ed02d05da683caeb025e52522444d8215
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68223433"
---
> [!NOTE]
> Le compte système Microsoft 365 doit être le même pour les deux connexions. Si ce n’est pas le cas, le message d’erreur « Ce profil d’acteur désigné n’a pas de privilèges de propriété d’équipe » s’affiche.

Si vous souhaitez dissocier une équipe d’une connexion et la mapper à une autre connexion :

1. [Configurez votre environnement](#set-up-your-environment) (si vous ne l’avez pas déjà fait).
1. Affichez la liste de tous les mappages d’équipe pour une connexion.

    ```powershell
    Get-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId <ConnectorInstanceId>
    ```

1. Supprimez un mappage d’équipe de la connexion.

    ```powershell
    Remove-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId <ConnectorInstanceId> -TeamId <TeamId>
    ```

1. Mappez l’équipe à une autre connexion.

    ```powershell
    New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId <ConnectorInstanceId> -TeamId <TeamId> -WfmTeamId <SiteId> -TimeZone <TimeZone>
    ```

Pour plus d’informations, consultez [Get-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/get-csteamsshiftsconnectionteammap), [Remove-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/remove-csteamsshiftsconnectionteammap) et [New-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/new-csteamsshiftsconnectionteammap).
