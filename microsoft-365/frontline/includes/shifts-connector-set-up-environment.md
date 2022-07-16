---
author: LanaChin
ms.author: v-lanachin
ms.date: 03/31/2022
ms.topic: include
audience: admin
ms.service: msteams
ms.openlocfilehash: 3d4ec38f0007460fa119e69eadc79cd9c51887ee
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66822449"
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

    Vérifiez qu’il s’agit au moins de la version 4.1.0 et qu’il contient les applets de commande du connecteur Shifts.

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