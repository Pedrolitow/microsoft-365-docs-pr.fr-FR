---
author: LanaChin
ms.author: v-lanachin
ms.date: ''
ms.topic: include
audience: admin
ms.service: microsoft-365-frontline
ms.openlocfilehash: beabbc18474a4454fbcfa448b76898de8af14c1b
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68223499"
---
Utilisez ce script pour modifier les paramètres de connexion. Les paramètres que vous pouvez modifier incluent votre compte de service et votre mot de passe WFM, le compte système Microsoft 365, les mappages d’équipe et les paramètres de synchronisation.

Les paramètres de synchronisation incluent la fréquence de synchronisation (en minutes) et les données de planification synchronisées entre votre système WFM et Shifts. Les données de planification sont définies dans les paramètres suivants, que vous pouvez afficher en exécutant [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector).

- Le paramètre **enabledConnectorScenarios** définit les données synchronisées entre votre système WFM et Shifts. Les options sont `Shift`, `SwapRequest`, `UserShiftPreferences`, `OpenShift`, `OpenShiftRequest`, `TimeOff`, `TimeOffRequest`.
- Le paramètre **enabledWfiScenarios** définit les données synchronisées entre Shifts et votre système WFM. Les options sont `SwapRequest`, `OpenShiftRequest`, `TimeOffRequest`, `UserShiftPreferences`.

    > [!NOTE]
    > Si vous choisissez de ne pas synchroniser les shifts ouverts, les demandes d’ouverture de décalage, les demandes d’échange ou les demandes de congé entre shifts et votre système WFM, vous devez effectuer une autre étape pour masquer la fonctionnalité dans Shifts. Après avoir exécuté ce script, assurez-vous de suivre les étapes de la section [Désactiver les équipes ouvertes, les demandes d'équipes ouvertes, les demandes de permutation et les demandes de congés](#disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests) plus loin dans cet article.

> [!IMPORTANT]
> Pour les paramètres que vous ne souhaitez pas modifier, vous devez entrer à nouveau les paramètres d’origine lorsque le script vous y invite.
