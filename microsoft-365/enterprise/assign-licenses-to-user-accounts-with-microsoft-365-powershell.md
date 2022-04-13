---
title: Attribuer Microsoft 365 licences à des comptes d’utilisateur avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/23/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Dans cet article, découvrez comment utiliser PowerShell pour attribuer une licence Microsoft 365 aux utilisateurs sans licence.
ms.openlocfilehash: 72ad30cb3c8a36a78b3f95699c775b96d959b542
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823033"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>Attribuer Microsoft 365 licences à des comptes d’utilisateur avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les utilisateurs ne peuvent pas utiliser de services Microsoft 365 tant que leur compte n’a pas reçu de licence à partir d’un plan de licence. Vous pouvez utiliser PowerShell pour affecter rapidement des licences à des comptes sans licence. 

Un emplacement doit d’abord être attribué aux comptes d’utilisateur. La spécification d’un emplacement est une partie requise de la création d’un compte d’utilisateur dans le [Centre d'administration Microsoft 365](../admin/add-users/add-users.md). 

Les comptes synchronisés à partir de vos services de domaine Active Directory local n’ont pas par défaut d’emplacement spécifié. Vous pouvez configurer un emplacement pour ces comptes à partir de :

- Le Centre d’administration Microsoft 365
- [PowerShell](configure-user-account-properties-with-microsoft-365-powershell.md)
- Le [Portail Azure](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) (**Active DirectoryUsers** >  > compte d’utilisateur > **ProfileContact** >  **infoCountry** >  ou région).

>[!Note]
>[Découvrez comment attribuer des licences à des comptes d’utilisateur](../admin/manage/assign-licenses-to-users.md) avec le Centre d'administration Microsoft 365. Pour obtenir la liste des ressources supplémentaires, consultez [Gérer les utilisateurs et les groupes](/admin).
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Utiliser le Kit de développement logiciel (SDK) Microsoft Graph PowerShell

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](/graph/powershell/get-started#authentication).

L’attribution et la suppression de licences pour un utilisateur nécessitent l’étendue d’autorisation User.ReadWrite.All ou l’une des autres autorisations répertoriées dans la [page de référence « Attribuer une licence » API Graph](/graph/api/user-assignlicense).

L’étendue d’autorisation Organization.Read.All est nécessaire pour lire les licences disponibles dans le locataire.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Exécutez la `Get-MgSubscribedSku` commande pour afficher les plans de licence disponibles et le nombre de licences disponibles dans chaque plan de votre organisation. Le nombre de licences disponibles dans chaque plan est ActiveUnitsWarningUnitsConsumedUnits -  - . Pour plus d’informations sur les plans de licence, les licences et les services, consultez [Afficher les licences et les services avec PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

Pour rechercher les comptes sans licence dans votre organisation, exécutez cette commande.

```powershell
Get-MgUser -Filter 'assignedLicenses/$count eq 0' -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All
```

Vous pouvez uniquement attribuer des licences à des comptes d’utilisateur dont la propriété **UsageLocation** est définie sur un code de pays ISO 3166-1 alpha-2 valide. Par exemple, US pour les États-Unis et FR pour la France. Certains services Microsoft 365 ne sont pas disponibles dans certains pays. Pour plus d’informations, consultez [À propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).

Pour rechercher des comptes qui n’ont pas de valeur **UsageLocation** , exécutez cette commande.

```powershell
Get-MgUser -Select Id,DisplayName,Mail,UserPrincipalName,UsageLocation,UserType | where { $_.UsageLocation -eq $null -and $_.UserType -eq 'Member' }
```

Pour définir la valeur **UsageLocation** sur un compte, exécutez cette commande.

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"

Update-MgUser -UserId $userUPN -UsageLocation $userLoc
```

Par exemple :

```powershell
Update-MgUser -UserId "belindan@litwareinc.com" -UsageLocation US
```

Si vous utilisez l’applet **de commande Get-MgUser** sans utiliser le paramètre **-All** , seuls les 100 premiers comptes sont retournés.

### <a name="assigning-licenses-to-user-accounts"></a>Affectation de licences à des comptes d’utilisateur

Pour attribuer une licence à un utilisateur, utilisez la commande suivante dans PowerShell.
  
```powershell
Set-MgUserLicense -UserId $userUPN -AddLicenses @{SkuId = "<SkuId>"} -RemoveLicenses @()
```

Cet exemple montre comment attribuer une licence du plan de **licences SPE_E5** (Microsoft 365 E5) à l’utilisateur **sans licence be réstribué\@ litwareinc.com** :
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{SkuId = $e5Sku.SkuId} -RemoveLicenses @()
```

Cet exemple montre comment affecter **SPE_E5** (Microsoft 365 E5) et **EMSPREMIUM** (ENTERPRISE MOBILITY + SECURITY E5) à l’utilisateur **be litwareinc.com\@** :
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$e5EmsSku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'EMSPREMIUM'
$addLicenses = @(
    @{SkuId = $e5Sku.SkuId},
    @{SkuId = $e5EmsSku.SkuId}
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

Cet exemple attribue **des SPE_E5** (Microsoft 365 E5) avec les services **MICROSOFTBOOKINGS** (Microsoft Bookings) et **LOCKBOX_ENTERPRISE** (Customer LockBox) désactivés :
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$disabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("LOCKBOX_ENTERPRISE", "MICROSOFTBOOKINGS") | `
    Select -ExpandProperty ServicePlanId

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

Cet exemple met à jour un utilisateur avec **SPE_E5** (Microsoft 365 E5) et désactive les plans de service Sway et Forms tout en laissant les plans désactivés existants de l’utilisateur dans leur état actuel :
  
```powershell
$userLicense = Get-MgUserLicenseDetail -UserId "belinda@fdoau.onmicrosoft.com"
$userDisabledPlans = $userLicense.ServicePlans | `
    Where ProvisioningStatus -eq "Disabled" | `
    Select -ExpandProperty ServicePlanId

$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$newDisabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("SWAY", "FORMS_PLAN_E5") | `
    Select -ExpandProperty ServicePlanId

$disabledPlans = ($userDisabledPlans + $newDisabledPlans) | Select -Unique

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.onmicrosoft.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

### <a name="assign-licenses-to-a-user-by-copying-the-license-assignment-from-another-user"></a>Attribuer des licences à un utilisateur en copiant l’attribution de licence à partir d’un autre utilisateur

Cet exemple montre comment affecter **jamesp\@ litwareinc.com** avec le même plan de gestion des licences qui a été appliqué à **be litwareinc.com\@** :

```powershell
$mgUser = Get-MgUser -UserId "belindan@litwareinc.com"
Set-MgUserLicense -UserId "jamesp@litwareinc.com" -AddLicenses $mgUser.AssignedLicenses -RemoveLicenses @()
```

### <a name="move-a-user-to-a-different-subscription-license-plan"></a>Déplacer un utilisateur vers un autre abonnement (plan de licence)

Cet exemple met à niveau un utilisateur du plan de **licences SPE_E3** (Microsoft 365 E3) vers le plan de **licences SPE_E5** (Microsoft 365 E5) :

```powershell
$e3Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E3'
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'

# Unassign E3
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{} -RemoveLicenses @($e3Sku.SkuId)
# Assign E5
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{SkuId = $e5Sku.SkuId} -RemoveLicenses @()
```

Vous pouvez vérifier la modification de l’abonnement pour le compte d’utilisateur à l’aide de cette commande.

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

>[!Note]
>L’applet de commande Set-AzureADUserLicense est planifiée pour être mise hors service. Migrez vos scripts vers l’applet de commande Set-MgUserLicense du Kit de développement logiciel (SDK) Microsoft Graph, comme décrit ci-dessus. Pour plus d’informations, consultez [Migrer vos applications pour accéder aux API de gestion des licences à partir de Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Ensuite, répertoriez les plans de licence pour votre locataire avec cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, obtenez le nom de connexion du compte auquel vous souhaitez ajouter une licence, également appelé nom d’utilisateur principal (UPN).

Ensuite, vérifiez que l’emplacement d’utilisation du compte d’utilisateur est affecté.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

Si aucun emplacement d’utilisation n’est affecté, vous pouvez en affecter un avec les commandes suivantes :

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Enfin, spécifiez le nom de connexion de l’utilisateur et le nom du plan de licence et exécutez ces commandes.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

>[!Note]
>Les applets de commande Set-MsolUserLicense et New-MsolUser (-LicenseAssignment) sont planifiées pour être mises hors service. Migrez vos scripts vers l’applet de commande Set-MgUserLicense du Kit de développement logiciel (SDK) Microsoft Graph, comme décrit ci-dessus. Pour plus d’informations, consultez [Migrer vos applications pour accéder aux API de gestion des licences à partir de Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Exécutez la `Get-MsolAccountSku` commande pour afficher les plans de licence disponibles et le nombre de licences disponibles dans chaque plan de votre organisation. Le nombre de licences disponibles dans chaque plan est ActiveUnitsWarningUnitsConsumedUnits -  - . Pour plus d’informations sur les plans de licence, les licences et les services, consultez [Afficher les licences et les services avec PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Pour rechercher les comptes sans licence dans votre organisation, exécutez cette commande.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Vous pouvez uniquement attribuer des licences à des comptes d’utilisateur dont la propriété **UsageLocation** est définie sur un code de pays ISO 3166-1 alpha-2 valide. Par exemple, US pour les États-Unis et FR pour la France. Certains services Microsoft 365 ne sont pas disponibles dans certains pays. Pour plus d’informations, consultez [À propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Pour rechercher des comptes qui n’ont pas de valeur **UsageLocation** , exécutez cette commande.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Pour définir la valeur **UsageLocation** sur un compte, exécutez cette commande.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Par exemple :

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre **-All**, seuls les 500 premiers comptes sont renvoyés.

### <a name="assigning-licenses-to-user-accounts"></a>Affectation de licences à des comptes d’utilisateur
    
Pour attribuer une licence à un utilisateur, utilisez la commande suivante dans PowerShell.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Cet exemple attribue une licence à partir du plan de licence **litwareinc:ENTERPRISEPACK** (Office 365 Entreprise E3) à l’utilisateur **sans licence be urln\@ litwareinc.com** :
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Pour attribuer une licence à tous les utilisateurs sans licence, exécutez cette commande.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>Vous ne pouvez pas attribuer plusieurs licences à un utilisateur à partir du même plan de gestion des licences. Si le nombre de licences disponibles n’est pas suffisant, les licences sont attribuées aux utilisateurs selon leur ordre de renvoi par la cmdlet **Get-MsolUser** jusqu'à ce qu’il n’y ait plus de licence disponible.
>

Cet exemple attribue des licences du plan de licence **litwareinc:ENTERPRISEPACK** (Office 365 Entreprise E3) à tous les utilisateurs sans licence :
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Cet exemple montre comment attribuer ces mêmes licences à des utilisateurs sans licence dans le service Ventes du États-Unis :
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Déplacer un utilisateur vers un autre abonnement (plan de licence) avec le module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Ensuite, obtenez le nom de connexion du compte d’utilisateur pour lequel vous souhaitez changer d’abonnement, également appelé nom d’utilisateur principal (UPN).

Ensuite, répertoriez les abonnements (plans de licence) de votre locataire à l’aide de cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, répertoriez les abonnements dont dispose actuellement le compte d’utilisateur avec ces commandes.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Identifiez l’abonnement dont l’utilisateur dispose actuellement (l’abonnement FROM) et l’abonnement vers lequel l’utilisateur se déplace (l’abonnement TO).

Enfin, spécifiez les noms d’abonnement TO et FROM (numéros de partie de référence SKU) et exécutez ces commandes.

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

Vous pouvez vérifier la modification de l’abonnement pour le compte d’utilisateur avec ces commandes.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
