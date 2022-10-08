---
author: LanaChin
ms.author: v-lanachin
ms.date: 03/31/2022
ms.topic: include
audience: admin
ms.service: microsoft-365-frontline
ms.openlocfilehash: 7415d4dfd8d6a7a1935d9aca2e04726f7b929996
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68222603"
---
1. Installez PowerShell version 7 ou ultérieure. Pour obtenir des conseils pas à pas, consultez [l’installation de PowerShell sur Windows](/powershell/scripting/install/installing-powershell-on-windows).

1. Exécutez PowerShell en mode Administrateur.
1. Installez le module PowerShell Microsoft Graph.

    ```powershell
    Install-Module Microsoft.Graph
    Import-Module Microsoft.Graph
    ```

    Vérifiez qu’il s’agit de la version 1.6.1 ou ultérieure.

    ```powershell
    Get-InstalledModule Microsoft.Graph 
    ```

1. Installez le module PowerShell Teams Preview.

    ```powershell
    Install-Module -Name MicrosoftTeams -AllowPrerelease -Force
    Import-Module MicrosoftTeams 
    ```

    Vérifiez qu’il s’agit au moins de la version 4.7.0 et qu’il contient les applets de commande du connecteur Shifts.

    ```powershell
    Get-Command -Module MicrosoftTeams -Name *teamsshiftsconnection* 
    ```

1. Définissez PowerShell pour qu’il s’arrête si une erreur se produit lors de l’exécution du script.

    ```powershell
    $ErrorActionPreference = "Stop" 
    ```

1. Activez l’exécution des scripts dans Windows.

    ```powershell
    Set-ExecutionPolicy bypass 
    ```