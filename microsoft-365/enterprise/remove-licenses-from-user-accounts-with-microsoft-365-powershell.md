---
title: Supprimer Microsoft 365 licences des comptes d’utilisateur avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/23/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Explique comment utiliser PowerShell pour supprimer Microsoft 365 licences précédemment attribuées aux utilisateurs.
ms.openlocfilehash: c3317c651c561da4c8650e45ba3b64a135a1f6ce
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823143"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a>Supprimer Microsoft 365 licences des comptes d’utilisateur avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

>[!Note]
>[Découvrez comment supprimer des licences des comptes d’utilisateur](../admin/manage/remove-licenses-from-users.md) avec le Centre d'administration Microsoft 365. Pour obtenir la liste des ressources supplémentaires, consultez [Gérer les utilisateurs et les groupes](/admin).
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Utiliser le Kit de développement logiciel (SDK) Microsoft Graph PowerShell

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](/graph/powershell/get-started#authentication).

L’attribution et la suppression de licences pour un utilisateur nécessitent l’étendue d’autorisation User.ReadWrite.All ou l’une des autres autorisations répertoriées dans la [page de référence « Attribuer une licence » API Graph](/graph/api/user-assignlicense).

L’étendue d’autorisation Organization.Read.All est nécessaire pour lire les licences disponibles dans le locataire.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Pour afficher les informations de plan de licence dans votre organisation, consultez les rubriques suivantes :

- [Afficher les licences et les services avec PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md)

- [Afficher la licence de compte et les détails du service avec PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md)

### <a name="removing-licenses-from-user-accounts"></a>Suppression de licences des comptes d’utilisateur

Pour supprimer des licences à partir d’un compte d’utilisateur existant, utilisez la syntaxe suivante :
  
```powershell
Set-MgUserLicense -UserId "<Account>" -RemoveLicenses @("<AccountSkuId1>") -AddLicenses @{}
```

Cet exemple supprime le plan de licences **SPE_E5** (Microsoft 365 E5) du **BelindaN@litwareinc.com** utilisateur :

```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
Set-MgUserLicense -UserId "belindan@litwareinc.com" -RemoveLicenses @($e5Sku.SkuId) -AddLicenses @{}
```

Pour supprimer toutes les licences d’un groupe d’utilisateurs sous licence existants, utilisez la syntaxe suivante :

```powershell
$licensedUsers = Get-MgUser -Filter 'assignedLicenses/$count ne 0' `
    -ConsistencyLevel eventual -CountVariable licensedUserCount -All `
    -Select UserPrincipalName,DisplayName,AssignedLicenses

foreach($user in $licensedUsers)
{
    $licencesToRemove = $user.AssignedLicenses | Select -ExpandProperty SkuId
    $user = Set-MgUserLicense -UserId $user.UserPrincipalName -RemoveLicenses $licencesToRemove -AddLicenses @{} 
}
```

Une autre façon de libérer une licence consiste à supprimer le compte d’utilisateur. Pour plus d’informations, consultez [Supprimer et restaurer des comptes d’utilisateur avec PowerShell](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

>L’applet de commande Set-AzureADUserLicense est planifiée pour être mise hors service. Migrez vos scripts vers l’applet de commande Set-MgUserLicense du Kit de développement logiciel (SDK) Microsoft Graph, comme décrit ci-dessus. Pour plus d’informations, consultez [Migrer vos applications pour accéder aux API de gestion des licences à partir de Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Ensuite, répertoriez les plans de licence pour votre locataire avec cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, obtenez le nom de connexion du compte pour lequel vous souhaitez supprimer une licence, également appelé nom d’utilisateur principal (UPN).

Enfin, spécifiez les noms de connexion utilisateur et de plan de licence, supprimez les caractères « < » et « > », puis exécutez ces commandes.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

Pour supprimer toutes les licences d’un compte d’utilisateur spécifique, spécifiez le nom de connexion de l’utilisateur, supprimez les caractères « < » et « > », puis exécutez ces commandes.

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

>[!Note]
>Les applets de commande Set-MsolUserLicense et New-MsolUser (-LicenseAssignment) sont planifiées pour être mises hors service. Migrez vos scripts vers l’applet de commande Set-MgUserLicense du Kit de développement logiciel (SDK) Microsoft Graph, comme décrit ci-dessus. Pour plus d’informations, consultez [Migrer vos applications pour accéder aux API de gestion des licences à partir de Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
   
Pour afficher les informations sur le plan de gestion des licences (**AccountSkuID**) dans votre organisation, consultez les rubriques suivantes :
    
  - [Afficher les licences et les services avec PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md)
    
  - [Afficher la licence de compte et les détails du service avec PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md)
    
Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _-All_, seuls les 500 premiers comptes sont renvoyés.
    
### <a name="removing-licenses-from-user-accounts"></a>Suppression de licences des comptes d’utilisateur

Pour supprimer des licences à partir d’un compte d’utilisateur existant, utilisez la syntaxe suivante :
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Cet exemple supprime la licence **litwareinc:ENTERPRISEPACK** (Office 365 Entreprise E3) du compte d’utilisateur BelindaN@litwareinc.com.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>Vous ne pouvez pas utiliser l’applet `Set-MsolUserLicense` de commande pour désaffecter les utilisateurs des licences *annulées* . Vous devez le faire individuellement pour chaque compte d’utilisateur dans le Centre d'administration Microsoft 365.
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

Cet exemple montre comment supprimer toutes les licences de tous les comptes d’utilisateurs du service Ventes du États-Unis.
    
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

Pour supprimer toutes les licences de tous les comptes d’utilisateur existants, utilisez la syntaxe suivante :
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Une autre façon de libérer une licence consiste à supprimer le compte d’utilisateur. Pour plus d’informations, consultez [Supprimer et restaurer des comptes d’utilisateur avec PowerShell](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).
  
## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
