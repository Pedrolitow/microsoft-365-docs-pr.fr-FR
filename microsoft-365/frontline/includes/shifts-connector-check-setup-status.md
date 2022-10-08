---
author: LanaChin
ms.author: v-lanachin
ms.date: ''
ms.topic: include
audience: admin
ms.service: microsoft-365-frontline
ms.openlocfilehash: 348370981c75fd0ca435b5c7f58a96f5790df11b
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68223455"
---
Pour vérifier l’état de la connexion que vous avez configurée à l’aide de l’ID d’opération que vous avez reçu par e-mail :

1. [Configurez votre environnement](#set-up-your-environment) (si vous ne l’avez pas déjà fait).
1. Exécutez la commande suivante : Cette commande vous donne l’état global des mappages d’équipe pour la connexion.

    ``` powershell
    Get-CsTeamsShiftsConnectionOperation -OperationId <YourOperationId>
    ```

Pour en savoir plus, consultez [Get-CsTeamsShiftsConnectionOperation](/powershell/module/teams/get-csteamsshiftsconnectionoperation).
