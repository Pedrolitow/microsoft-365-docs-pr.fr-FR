---
author: LanaChin
ms.author: v-lanachin
ms.date: ''
ms.topic: include
audience: admin
ms.service: microsoft-365-frontline
ms.openlocfilehash: a411ff6608f09f7c5eff7f83dcc1dd3a98714378
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68223411"
---
> [!IMPORTANT]
> Suivez ces étapes uniquement si vous avez choisi de désactiver les équipes ouvertes, les demandes d’équipes ouvertes, les demandes de permutation ou les demandes de congés à l’aide du script de la section [Modifier les paramètres de connexion](#change-connection-settings) plus haut dans cet article ou à l’aide du cmdlet [Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance). L’exécution de cette étape masque la fonctionnalité dans Shifts. Sans cette deuxième étape, les utilisateurs verront toujours la fonctionnalité dans Shifts et recevront un message d’erreur « opération non prise en charge » s’ils essaient de l’utiliser.

Pour masquer les décalages ouverts, les demandes d’échange et les demandes de congé dans Shifts, utilisez le [type de ressource de planification](/graph/api/resources/schedule) API Graph pour définir les paramètres suivants ```false``` pour chaque équipe que vous avez mappée à une instance WFM :

- Ouvrir les shifts : ```openShiftsEnabled```
- Demandes d’échange :  ```swapShiftsRequestsEnabled```
- Demandes de congé : ```timeOffRequestsEnabled```

Pour masquer les demandes de shifts ouverts dans Shifts, accédez à **Paramètres** dans Shifts, puis désactivez le paramètre **Ouvrir les shifts** .
