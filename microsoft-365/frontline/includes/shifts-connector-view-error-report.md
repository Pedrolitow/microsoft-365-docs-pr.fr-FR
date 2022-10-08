---
author: LanaChin
ms.author: v-lanachin
ms.date: ''
ms.topic: include
audience: admin
ms.service: microsoft-365-frontline
ms.openlocfilehash: 30186298f83ea1a1e1721b9dc31a77eb4af33975
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68223477"
---
Vous pouvez exécuter un rapport qui affiche les détails de l’erreur pour une connexion. Le rapport répertorie les mappages d’équipe et d’utilisateur qui ont réussi et échoué. Il fournit également des informations sur les problèmes liés aux comptes associés à la connexion.

1. [Configurez votre environnement](#set-up-your-environment) (si vous ne l’avez pas déjà fait).
1. Obtenez la liste des rapports d’erreurs pour une connexion.

    ``` powershell
    Get-CsTeamsShiftsConnectionErrorReport -ConnectorInstanceId <ConnectorInstanceId>
    ```

1. Pour afficher un rapport d’erreurs spécifique, exécutez la commande suivante :

    ``` powershell
    Get-CsTeamsShiftsConnectionErrorReport -ErrorReportId <ErrorReportId>
    ```

Pour en savoir plus, consultez [Get-CsTeamsShiftsConnectionErrorReport](/powershell/module/teams/get-csteamsshiftsconnectionerrorreport).
