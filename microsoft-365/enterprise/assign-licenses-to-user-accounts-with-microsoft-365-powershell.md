---
title: Attribuez Microsoft 365 licences aux comptes utilisateur avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/23/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
description: Dans cet article, apprenez à utiliser PowerShell pour attribuer une licence Microsoft 365 aux utilisateurs non autorisés.
ms.openlocfilehash: 6d7e005aff018394810082de57c68ea289057f8e
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572620"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>Attribuez Microsoft 365 licences aux comptes utilisateur avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les utilisateurs ne peuvent pas utiliser de services Microsoft 365 tant que leur compte n’a pas reçu une licence d’un plan de licence. Vous pouvez utiliser PowerShell pour attribuer rapidement des licences à des comptes non licenciés. 

Les comptes d’utilisateurs doivent d’abord se voir attribuer un emplacement. Spécifier un emplacement est une partie requise de la création d’un nouveau compte utilisateur dans [le Microsoft 365 d’administration](../admin/add-users/add-users.md). 

Les comptes synchronisés à partir de vos services de domaine d’annuaire actif sur place n’ont pas par défaut de localisation spécifiée. Vous pouvez configurer un emplacement pour ces comptes à partir de :

- Le Centre d’administration Microsoft 365
 - [PowerShell](configure-user-account-properties-with-microsoft-365-powershell.md)
 - Le [portail Azure](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) **(Active Directory**  >  **Users >** compte utilisateur > **Profil**  >  **Contact Pays** ou  >  **région).**

>[!Note]
>[Découvrez comment attribuer des licences à des comptes d’utilisateurs](../admin/manage/assign-licenses-to-users.md) avec le Microsoft 365 d’administration. Pour une liste de ressources supplémentaires, consultez Gérer [les utilisateurs et les groupes](../admin/add-users/index.yml).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à Microsoft 365 locataire.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  

Ensuite, énumérez les plans de licence pour votre locataire avec cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, obtenez le nom de connecteur du compte auquel vous souhaitez ajouter une licence, également connue sous le nom de nom principal de l’utilisateur (UPN).

Ensuite, assurez-vous que le compte utilisateur a un emplacement d’utilisation attribué.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

S’il n’y a pas d’emplacement d’utilisation assigné, vous pouvez en assigner un avec ces commandes :

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Enfin, spécifiez le nom de l’utilisateur et le nom du plan de licence et exécutez ces commandes.

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

Veuillez noter que nous commencerons à déprécier ce module lorsque les fonctionnalités de ce module seront disponibles dans [le nouveau module Azure Active Directory PowerShell pour Graph](/powershell/azuread/v2/azureactivedirectory) module. Nous conseillons aux clients qui créent de nouveaux scripts PowerShell d’utiliser le module plus nouveau au lieu de ce module.

Tout [d’abord, connectez-vous à Microsoft 365 locataire.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

Exécutez `Get-MsolAccountSku` la commande pour afficher les plans de licence disponibles et le nombre de licences disponibles dans chaque plan de votre organisation. Le nombre de licences disponibles dans chaque plan **est ActiveUnits**  -  **WarningUnits**  -  **ConsumedUnits**. Pour plus d’informations sur les plans de licence, les licences et les services, [consultez les licences et services View avec PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Pour trouver les comptes sans licence dans votre organisation, exécutez cette commande.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Vous ne pouvez attribuer des licences qu’aux comptes d’utilisateurs dont **la propriété UtilisationLocation** est définie sur un code iso 3166-1 alpha-2 valide. Par exemple, US pour les États-Unis et FR pour la France. Certains Microsoft 365 services ne sont pas disponibles dans certains pays. Pour plus d’informations, voir [Sur les restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Pour trouver des comptes qui n’ont pas de **valeur UtilisationLocation,** exécutez cette commande.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Pour définir la **valeur UtilisationLocation** sur un compte, exécutez cette commande.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Par exemple :

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre **-All**, seuls les 500 premiers comptes sont renvoyés.

### <a name="assigning-licenses-to-user-accounts"></a>Attribution de licences aux comptes d’utilisateurs
    
Pour attribuer une licence à un utilisateur, utilisez la commande suivante dans PowerShell.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Cet exemple attribue une licence du plan de licence **litwareinc:ENTERPRISEPACK** (Office 365 Entreprise E3) à **l’utilisateur non titulaire d’un permis belindan \@ litwareinc.com**:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Pour attribuer une licence à tous les utilisateurs non titulaires d’un permis, exécutez cette commande.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>Vous ne pouvez pas attribuer plusieurs licences à un utilisateur à partir du même plan de gestion des licences. Si le nombre de licences disponibles n’est pas suffisant, les licences sont attribuées aux utilisateurs selon leur ordre de renvoi par la cmdlet **Get-MsolUser** jusqu'à ce qu’il n’y ait plus de licence disponible.
>

Cet exemple attribue des licences du plan de licence **litwareinc:ENTERPRISEPACK** (Office 365 Entreprise E3) à tous les utilisateurs non titulaires d’un permis :
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Cet exemple attribue ces mêmes licences à des utilisateurs non titulaires d’un permis dans le département des ventes aux États-Unis :
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Déplacez un utilisateur vers un abonnement différent (plan de licence) avec le module Azure Active Directory PowerShell pour Graph vidéo

Tout [d’abord, connectez-vous à Microsoft 365 locataire.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  
Ensuite, obtenez le nom de connecteur du compte d’utilisateur pour lequel vous souhaitez changer d’abonnement, également connu sous le nom de nom principal de l’utilisateur (UPN).

Ensuite, énumérez les abonnements (plans de licence) pour votre locataire avec cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, énumérez les abonnements que le compte utilisateur a actuellement avec ces commandes.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Identifiez l’abonnement que l’utilisateur a actuellement (l’abonnement FROM) et l’abonnement auquel l’utilisateur se déplace (l’abonnement TO).

Enfin, spécifiez les noms d’abonnement TO et FROM (numéros de pièce SKU) et exécutez ces commandes.

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

Vous pouvez vérifier la modification de l’abonnement pour le compte utilisateur avec ces commandes.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
