---
title: 'Exemple de script pour les paramètres EOP : plusieurs locataires'
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: e87e84e1-7be0-44bf-a414-d91d60ed8817
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous apprendrez à utiliser PowerShell pour appliquer des paramètres de configuration à vos clients dans Microsoft Exchange Online Protection (EOP).
ms.openlocfilehash: dbb4135c89ac8d351c40bd7d9ce5301500a9b81b
ms.sourcegitcommit: 20d1158c54a5058093eb8aac23d7e4dc68054688
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "49376566"
---
# <a name="sample-script-for-applying-eop-settings-to-multiple-tenants"></a>Exemple de script pour l’application de paramètres EOP à plusieurs clients

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


L’exemple de script suivant permet aux administrateurs de Microsoft Exchange Online Protection (EOP) qui gèrent plusieurs locataires (entreprises) d’utiliser Exchange Online PowerShell pour afficher et/ou appliquer des paramètres de configuration à leurs clients.

## <a name="to-run-a-script-or-cmdlet-on-multiple-tenants"></a>Pour exécuter un script ou une cmdlet sur plusieurs locataires

1. Si vous ne l’avez pas encore fait, [Installez le module Exchange Online v2](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

2. À l’aide d’une application de feuille de calcul (par exemple, Excel), créez un fichier. csv avec les détails suivants :

   - Colonne UserName : compte que vous utiliserez pour vous connecter (par exemple, `admin@contoso.onmicrosoft.com` ).
   - Colonne cmdlet : cmdlet ou commande à exécuter (par exemple, `Get-AcceptedDomain` ou `Get-AcceptedDomain | FT Name` ).

   Le fichier se présente comme suit :

   ```text
   UserName,Cmdlet
   admin@contoso.onmicrosoft.com,Get-AcceptedDomain | FT Name
   admin@fabrikam.onmicrosoft.com,Get-AcceptedDomain | FT Name
   ```

3. Enregistrez le fichier. csv à un emplacement facile à trouver (par exemple, c:\scripts\inputfile.csv).

4. Copiez le [RunCmdletOnMultipleTenants.ps1](#runcmdletonmultipletenantsps1) script dans le bloc-notes, puis enregistrez le fichier dans un emplacement facile à trouver (par exemple, c:\Scripts).

5. Exécutez le script à l'aide de la syntaxe suivante :

   ```powershell
   & "<file path>\RunCmdletOnMultipleTenants.ps1" "<file path>\inputfile.csv"
   ```

   Voici un exemple :

   ```powershell
   & "c:\scripts\RunCmdletOnMultipleTenants.ps1" "c:\scripts\inputfile.csv"
   ```

6. Chaque client est connecté à, et le script est exécuté.

## <a name="runcmdletonmultipletenantsps1"></a>RunCmdletOnMultipleTenants.ps1

> [!NOTE]
> Vous devrez peut-être modifier la `Connect-IPPSSession` ligne dans le script pour qu’elle corresponde à votre environnement. Par exemple, Office 365 Germany requiert une valeur _ConnectionUri_ différente de la valeur actuelle d’un script. Pour plus d’informations, consultez la rubrique connexion à [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

```powershell
# This script runs Windows PowerShell cmdlets on multiple tenants.
#
# Usage: RunCmdletOnMultipleTenants.ps1 inputfile.csv
#
# .csv input file sample:
#
# UserName,Cmdlet
# admin@contoso.onmicrosoft.com,Get-AcceptedDomain | FT Name
# admin@fabrikam.onmicrosoft.com,Get-AcceptedDomain | FT Name

# Get the .csv file name as an argument to this script.
$FilePath = $args[0]

# Import the UserName and Cmdlet values from the .csv file.
$CompanyList = Import-CSV $FilePath

# Load the EXO V2 module
Import-Module ExchangeOnlineManagement

# Loop through each entry from the .csv file.
ForEach ($Company in $CompanyList) {
  
# Get the current entry's UserName.
$UserName = $Company.UserName

# Get the current entry's Cmdlet.
$Cmdlet = $Company.Cmdlet

# Connect to EOP PowerShell by using the current entry's UserName. Prompt for the password.
Connect-IPPSSession -UserPrincipalName $UserName -ConnectionUri https://ps.protection.outlook.com/powershell-liveid/

# Here's where the script to be run on the tenant goes.
# In this example, the cmdlet in the .csv file runs.
Invoke-Expression $Cmdlet

# End the current PowerShell session.
Disconnect-ExchangeOnline -Confirm:$false
}
```
