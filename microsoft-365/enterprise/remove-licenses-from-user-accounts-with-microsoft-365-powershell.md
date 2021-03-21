---
title: Supprimer des licences Microsoft 365 des comptes d’utilisateurs avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/23/2020
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
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Explique comment utiliser PowerShell pour supprimer des licences Microsoft 365 précédemment attribuées à des utilisateurs.
ms.openlocfilehash: 9944d1ab056d109b6bf71a44fe01acef78ce1f14
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50920667"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a>Supprimer des licences Microsoft 365 des comptes d’utilisateurs avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

>[!Note]
>[Découvrez comment supprimer des licences de comptes d’utilisateurs](../admin/manage/remove-licenses-from-users.md) à l’aide du Centre d’administration Microsoft 365. Pour obtenir la liste des ressources supplémentaires, voir [Gérer les utilisateurs et les groupes.](../admin/add-users/index.yml)
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à votre client Microsoft 365.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)

Ensuite, listez les plans de licence pour votre client avec cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, obtenez le nom de la signature du compte pour lequel vous souhaitez supprimer une licence, également appelé nom d’utilisateur principal (UPN).

Enfin, spécifiez les noms des plans de licence et de < utilisateur, supprimez les caractères « < » et « > », puis exécutez ces commandes.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

Pour supprimer toutes les licences d’un compte d’utilisateur spécifique, spécifiez le nom de la signature de l’utilisateur, supprimez les caractères « < » et « > », puis exécutez ces commandes.

```powershell
$userUPN="<user sign-in name (UPN)>"
$userList = Get-AzureADUser -ObjectID $userUPN
$Skus = $userList | Select -ExpandProperty AssignedLicenses | Select SkuID
if($userList.Count -ne 0) {
    if($Skus -is [array])
    {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        for ($i=0; $i -lt $Skus.Count; $i++) {
            $Licenses.RemoveLicenses +=  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus[$i].SkuId -EQ).SkuID   
        }
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    } else {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        $Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus.SkuId -EQ).SkuID
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    }
}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à votre client Microsoft 365.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)
   
Pour afficher les informations sur le plan de gestion des licences (**AccountSkuID**) dans votre organisation, consultez les rubriques suivantes :
    
  - [Afficher les licences et les services avec PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md)
    
  - [Afficher les détails de licence de compte et de service avec PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md)
    
Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _-All_, seuls les 500 premiers comptes sont renvoyés.
    
### <a name="removing-licenses-from-user-accounts"></a>Suppression de licences de comptes d’utilisateurs

Pour supprimer des licences à partir d’un compte d’utilisateur existant, utilisez la syntaxe suivante :
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Cet exemple supprime la licence **litwareinc:ENTERPRISEPACK** (Office 365 Entreprise E3) du compte d’BelindaN@litwareinc.com.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>Vous ne pouvez pas utiliser la `Set-MsolUserLicense` cmdlet pour désattribuer des licences *annulées* aux utilisateurs. Vous devez le faire individuellement pour chaque compte d’utilisateur dans le Centre d’administration Microsoft 365.
>

Pour supprimer toutes les licences d’un groupe d’utilisateurs sous licence existants, utilisez l’une des méthodes suivantes :
  
- **Filtrer les comptes en fonction d’un attribut de compte existant** Pour ce faire, utilisez la syntaxe suivante :
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Cet exemple supprime toutes les licences de tous les comptes d’utilisateurs du service Sales aux États-Unis.
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- **Utiliser une liste de comptes spécifiques pour une licence spécifique** Pour ce faire, effectuez les étapes suivantes :
    
1. Créez et enregistrez un fichier texte contenant un seul compte sur chaque ligne comme suit :
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Utilisez la syntaxe suivante :
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
Cet exemple supprime la licence **litwareinc:ENTERPRISEPACK** (Office 365 Entreprise E3) des comptes d’utilisateur définis dans le fichier texte C:\My Documents\Accounts.txt.
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

Pour supprimer toutes les licences de tous les comptes d’utilisateurs existants, utilisez la syntaxe suivante :
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Une autre façon de libérer une licence consiste à supprimer le compte d’utilisateur. Pour plus d’informations, voir [Supprimer et restaurer des comptes d’utilisateurs avec PowerShell.](delete-and-restore-user-accounts-with-microsoft-365-powershell.md)
  
## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)