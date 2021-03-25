---
title: Exemple de script pour les paramètres EOP - plusieurs locataires
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
ms.assetid: e87e84e1-7be0-44bf-a414-d91d60ed8817
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous allez apprendre à utiliser PowerShell pour appliquer des paramètres de configuration à vos locataires dans Microsoft Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 77a1dce25901845628f8148c44a0d0783088255e
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204686"
---
# <a name="sample-script-for-applying-eop-settings-to-multiple-tenants"></a>Exemple de script pour l’application de paramètres EOP à plusieurs clients

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
-  [Exchange Online Protection autonome](exchange-online-protection-overview.md)

L’exemple de script suivant permet aux administrateurs Microsoft Exchange Online Protection (EOP) qui gèrent plusieurs locataires (sociétés) d’utiliser Exchange Online PowerShell pour afficher et/ou appliquer des paramètres de configuration à leurs locataires.

## <a name="to-run-a-script-or-cmdlet-on-multiple-tenants"></a>Pour exécuter un script ou une cmdlet sur plusieurs locataires

1. Si ce n’est pas déjà fait, [installez le module Exchange Online V2.](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module)

2. À l’aide d’une application de feuille de calcul (par exemple, Excel), créez un fichier .csv avec les détails suivants :

   - Colonne UserName : compte que vous utiliserez pour vous connecter (par exemple, `admin@contoso.onmicrosoft.com` ).
   - Colonne de cmdlet : cmdlet ou commande à exécuter (par exemple, `Get-AcceptedDomain` ou `Get-AcceptedDomain | FT Name` ).

   Le fichier se présentera comme ceci :

   ```text
   UserName,Cmdlet
   admin@contoso.onmicrosoft.com,Get-AcceptedDomain | FT Name
   admin@fabrikam.onmicrosoft.com,Get-AcceptedDomain | FT Name
   ```

3. Enregistrez le fichier .csv à un emplacement facile à trouver (par exemple, c:\scripts\inputfile.csv).

4. Copiez le script [RunCmdletOnMultipleTenants.ps1](#runcmdletonmultipletenantsps1) dans le Bloc-notes, puis enregistrez le fichier à un emplacement facile à trouver (par exemple, c:\scripts).

5. Exécutez le script à l'aide de la syntaxe suivante :

   ```powershell
   & "<file path>\RunCmdletOnMultipleTenants.ps1" "<file path>\inputfile.csv"
   ```

   Voici un exemple :

   ```powershell
   & "c:\scripts\RunCmdletOnMultipleTenants.ps1" "c:\scripts\inputfile.csv"
   ```

6. Chaque client est connecté et le script est exécuté.

## <a name="runcmdletonmultipletenantsps1"></a>RunCmdletOnMultipleTenants.ps1

> [!NOTE]
> Vous devrez peut-être modifier `Connect-IPPSSession` la ligne dans le script pour qu’elle corresponde à votre environnement. Par exemple, Office 365 Germany requiert une valeur _ConnectionUri_ différente de la valeur actuelle dans un script. Pour plus d’informations, voir Se connecter [à Exchange Online PowerShell.](/powershell/exchange/connect-to-exchange-online-protection-powershell)

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