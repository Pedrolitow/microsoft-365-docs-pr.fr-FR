---
title: Attribuer Microsoft 365 licences d’utilisateur à des comptes d’utilisateur avec PowerShell
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
ms.openlocfilehash: b9f076e4856820d9f10e4cf92718dd6ddd3971c5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60186776"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>Attribuer Microsoft 365 licences d’utilisateur à des comptes d’utilisateur avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les utilisateurs ne peuvent utiliser aucun service Microsoft 365 tant que leur compte n’a pas reçu une licence d’un plan de gestion des licences. Vous pouvez utiliser PowerShell pour attribuer rapidement des licences à des comptes sans licence. 

Un emplacement doit d’abord être affecté aux comptes d’utilisateurs. La spécification d’un emplacement est une partie obligatoire de la création d’un compte d’utilisateur dans [le Centre d'administration Microsoft 365](../admin/add-users/add-users.md). 

Les comptes synchronisés à partir de vos services de domaine Active Directory locaux n’ont pas d’emplacement spécifié par défaut. Vous pouvez configurer un emplacement pour ces comptes à partir de :

- Le Centre d’administration Microsoft 365
 - [PowerShell](configure-user-account-properties-with-microsoft-365-powershell.md)
 - Le [portail Azure](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) (**Utilisateurs Active Directory**> compte d’utilisateur > informations de contact du profil Pays ou  >     >    >  **région**).

>[!Note]
>[Découvrez comment attribuer des licences à des comptes d’utilisateurs](../admin/manage/assign-licenses-to-users.md) à l’Centre d'administration Microsoft 365. Pour obtenir la liste des ressources supplémentaires, voir [Gérer les utilisateurs et les groupes.](/admin)
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  

Ensuite, listez les plans de licence pour votre client avec cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, obtenez le nom de la signature du compte auquel vous souhaitez ajouter une licence, également appelée nom d’utilisateur principal (UPN).

Ensuite, assurez-vous qu’un emplacement d’utilisation est affecté au compte d’utilisateur.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

Si aucun emplacement d’utilisation n’est affecté, vous pouvez en attribuer un avec les commandes ci-après :

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Enfin, spécifiez le nom de la signature de l’utilisateur et le nom du plan de licence et exécutez ces commandes.

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

Veuillez noter que nous commencerons à désintépreter ce module lorsque la fonctionnalité de ce module sera disponible dans la nouvelle Azure Active Directory [PowerShell](/powershell/azuread/v2/azureactivedirectory) pour Graph module. Nous conseillons aux clients qui créent des scripts PowerShell d’utiliser le module le plus nouveau au lieu de ce module.

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

Exécutez la commande pour afficher les plans de gestion des licences disponibles et le nombre de `Get-MsolAccountSku` licences disponibles dans chaque plan de votre organisation. Le nombre de licences disponibles dans chaque plan **est ActiveUnits**  -  **WarningUnits**  -  **ConsumedUnits**. Pour plus d’informations sur les plans de gestion des licences, les licences et les services, voir Afficher les [licences et les services avec PowerShell.](view-licenses-and-services-with-microsoft-365-powershell.md)

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Pour rechercher les comptes sans permis dans votre organisation, exécutez cette commande.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Vous pouvez uniquement attribuer des licences à des comptes d’utilisateur dont la propriété **UsageLocation** est définie sur un code pays ISO 3166-1 alpha-2 valide. Par exemple, US pour les États-Unis et FR pour la France. Certains Microsoft 365 ne sont pas disponibles dans certains pays. Pour plus d’informations, voir [à propos des restrictions de licence.](https://go.microsoft.com/fwlink/p/?LinkId=691730)
    
Pour rechercher des comptes qui n’ont pas de valeur **UsageLocation,** exécutez cette commande.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Pour définir la **valeur UsageLocation** sur un compte, exécutez cette commande.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Par exemple :

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre **-All**, seuls les 500 premiers comptes sont renvoyés.

### <a name="assigning-licenses-to-user-accounts"></a>Attribution de licences à des comptes d’utilisateurs
    
Pour attribuer une licence à un utilisateur, utilisez la commande suivante dans PowerShell.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Cet exemple affecte une licence du plan de gestion des licences **litwareinc:ENTERPRISEPACK** (Office 365 Entreprise E3) à l’utilisateur sans licence **belindan \@ litwareinc.com**:
  
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

Cet exemple attribue des licences du plan de gestion des licences **litwareinc:ENTERPRISEPACK** (Office 365 Entreprise E3) à tous les utilisateurs sans licence :
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Cet exemple attribue ces mêmes licences à des utilisateurs sans licence dans le service Sales aux États-Unis :
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Déplacer un utilisateur vers un autre abonnement (plan de licence) avec Azure Active Directory PowerShell pour Graph module

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  
Ensuite, obtenez le nom de la signature du compte d’utilisateur pour lequel vous souhaitez changer d’abonnement, également appelé nom d’utilisateur principal (UPN).

Ensuite, listez les abonnements (plans de licence) de votre client avec cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, listez les abonnements dont dispose actuellement le compte d’utilisateur avec ces commandes.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Identifiez l’abonnement actuel de l’utilisateur (l’abonnement FROM) et l’abonnement vers lequel l’utilisateur est en train de déplacer (l’abonnement TO).

Enfin, spécifiez les noms des abonnements TO et FROM (numéros de partie SKU) et exécutez ces commandes.

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
