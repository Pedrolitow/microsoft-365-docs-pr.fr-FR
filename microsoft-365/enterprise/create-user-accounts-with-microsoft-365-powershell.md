---
title: Créer Microsoft 365 comptes d’utilisateur avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Comment utiliser PowerShell pour créer des comptes d’Microsoft 365 individuels ou multiples.
ms.openlocfilehash: c096b5b4966bfde9973173b9a0a0c5bf1f0d786c
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59207636"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a>Créer Microsoft 365 comptes d’utilisateur avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez utiliser PowerShell pour Microsoft 365 pour créer efficacement des comptes d’utilisateurs, y compris plusieurs comptes.

Lorsque vous créez des comptes d’utilisateurs dans PowerShell, certaines propriétés de compte sont toujours requises. Les autres propriétés ne sont pas obligatoires, mais sont importantes. Reportez-vous au tableau suivant.
  
|**Nom de la propriété**|**Requis ?**|**Description**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |Oui  <br/> |Il s’agit du nom complet utilisé dans Microsoft 365 services. Par exemple, *Caleb Sills*. <br/> |
|**UserPrincipalName** <br/> |Oui  <br/> |Il s’agit du nom de compte utilisé pour se Microsoft 365 services. Par exemple, *CalebS \@ contoso.onmicrosoft.com*.  <br/> |
|**FirstName** <br/> |Non  <br/> ||
|**NomFamille** <br/> |Non  <br/> ||
|**LicenseAssignment** <br/> |Non  <br/> |Il s’agit du plan de gestion des licences (également appelé plan de licence ou référence SKU) à partir duquel une licence disponible est attribuée au compte d’utilisateur. La licence définit les services Microsoft 365 disponibles pour le compte. Vous n’avez pas besoin d’attribuer une licence à un utilisateur lorsque vous créez le compte, mais le compte doit avoir une licence pour accéder aux services Microsoft 365 services. Vous disposez de 30 jours pour attribuer une licence à un compte d'utilisateur après sa création. |
|**Password** <br/> |Non  <br/> | Si vous n'indiquez pas de mot de passe, un mot de passe aléatoire est affecté au compte d'utilisateur et le mot de passe est visible dans les résultats de la commande. Si vous spécifiez un mot de passe, il doit être de 8 à 16 caractères de texte ASCII des types suivants : lettres minuscules, lettres majuscules, chiffres et symboles.<br/> |
|**UsageLocation** <br/> |Non  <br/> |Il s’agit d’un code pays ISO 3166-1 alpha-2 valide. Par exemple, *états-Unis* pour les États-Unis et *FR* pour la France. Il est important de fournir cette valeur, car certains services Microsoft 365 ne sont pas disponibles dans certains pays. Vous ne pouvez pas attribuer de licence à un compte d’utilisateur, sauf si cette valeur est configurée pour le compte. Pour plus d’informations, voir [à propos des restrictions de licence.](https://go.microsoft.com/fwlink/p/?LinkId=691730)<br/> |

>[!Note]
>[Découvrez comment créer des comptes d’utilisateur à l’aide](../admin/add-users/add-users.md) du Centre d'administration Microsoft 365.
> 
> Pour obtenir la liste des ressources supplémentaires, voir [Gérer les utilisateurs et les groupes.](../admin/add-users/index.yml)
>   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)

Après vous être connecté, utilisez la syntaxe suivante pour créer un compte individuel :
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

Cet exemple crée un compte pour l’utilisateur américain *Caleb Sills*:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

### <a name="create-an-individual-user-account"></a>Créez un compte d’utilisateur individuel

Pour créer un compte individuel, utilisez la syntaxe suivante :
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les cmdlets dont le nom comprend *Msol.* Exécutez ces cmdlets à partir de Windows PowerShell.
>

Pour répertorier les noms des plans de gestion des licences disponibles, utilisez la commande suivante :

````powershell
Get-MsolAccountSku
````

Cet exemple crée un compte pour l’utilisateur américain *Caleb Sills* et attribue une licence à partir du plan de gestion des licences `contoso:ENTERPRISEPACK` (Office 365 Entreprise E3).
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>Créez plusieurs comptes d’utilisateurs

1. Créez un fichier CSV (valeurs séparées par des virgules) qui contient les informations de compte d’utilisateur requises. Par exemple :

     ```powershell
     UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
     ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
     LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
     ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
     ```

   >[!NOTE]
   >Les noms de colonne et leur ordre dans la première ligne du fichier CSV sont arbitraires. Toutefois, assurez-vous que l’ordre des données dans le reste du fichier correspond à l’ordre des noms de colonne. Utilisez également les noms de colonne pour les valeurs de paramètre dans PowerShell pour Microsoft 365 commande.
    
2. Utilisez la syntaxe suivante :
    
    ```powershell
     Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
    ```

   Cet exemple crée des comptes d’utilisateur à partir du fichier *C:\My Documents\NewAccounts.csv* et enregistre les résultats dans un fichier nommé *C:\My Documents\NewAccountResults.csv*.
    
    ```powershell
    Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
    ```

3. Passez en revue le fichier de sortie pour afficher les résultats. Comme nous n’avons pas spécifié de mot de passe, les mots de passe aléatoires Microsoft 365 générés sont visibles dans le fichier de sortie.
    
## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)