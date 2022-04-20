---
title: Afficher Microsoft 365 licence de compte et les détails du service avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
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
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explique comment utiliser PowerShell pour déterminer les services Microsoft 365 qui ont été affectés aux utilisateurs.
ms.openlocfilehash: 7e5724acbff571825f1496db5d59e04e11ba3a67
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64915992"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a>Afficher Microsoft 365 licence de compte et les détails du service avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Dans Microsoft 365, les licences des plans de licence (également appelées références SKU ou plans Microsoft 365) permettent aux utilisateurs d’accéder aux services Microsoft 365 définis pour ces plans. Toutefois, un utilisateur ne dispose peut-être pas d’un accès à tous les services disponibles dans une licence qui lui est affectée. Vous pouvez utiliser PowerShell pour Microsoft 365 afin d’afficher l’état des services sur les comptes d’utilisateur.

Pour plus d’informations sur les plans de licence, les licences et les services, consultez [Afficher les licences et les services avec PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Utiliser le Kit de développement logiciel (SDK) Microsoft Graph PowerShell

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](/graph/powershell/get-started#authentication).

La lecture des propriétés de l’utilisateur, y compris les détails de la licence, nécessite l’étendue d’autorisation User.Read.All ou l’une des autres autorisations répertoriées dans la [page de référence « Obtenir un utilisateur » API Graph](/graph/api/user-get).

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Ensuite, répertoriez les plans de licence pour votre locataire avec cette commande.

```powershell
Get-MgSubscribedSku
```

Utilisez ces commandes pour répertorier les services disponibles dans chaque plan de licence.

```powershell

$allSKUs = Get-MgSubscribedSku -Property SkuPartNumber, ServicePlans 
$allSKUs | ForEach-Object {
    Write-Host "Service Plan:" $_.SkuPartNumber
    $_.ServicePlans | ForEach-Object {$_}
}

```

Utilisez ces commandes pour répertorier les licences affectées à un compte d’utilisateur.

```powershell
Get-MgUserLicenseDetail -UserId "<user sign-in name (UPN)>"
```

Par exemple :

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

### <a name="to-view-services-for-a-user-account"></a>Pour afficher les services d’un compte d’utilisateur

Pour afficher tous les services Microsoft 365 auxquels un utilisateur a accès, utilisez la syntaxe suivante :
  
```powershell
(Get-MgUserLicenseDetail -UserId <user account UPN> -Property ServicePlans)[<LicenseIndexNumber>].ServicePlans
```

Cet exemple montre les services auxquels l’utilisateur BelindaN@litwareinc.com a accès. Ceci affiche les services qui sont associés à toutes les licences attribuées à son compte.
  
```powershell
(Get-MgUserLicenseDetail -UserId belindan@litwareinc.com -Property ServicePlans).ServicePlans
```

Cet exemple montre les services auxquels cet utilisateur BelindaN@litwareinc.com a accès à partir de la première licence attribuée à son compte (le numéro d’index est égal à 0).
  
```powershell
(Get-MgUserLicenseDetail -UserId belindan@litwareinc.com -Property ServicePlans)[0].ServicePlans
```

Pour afficher tous les services d’un utilisateur qui a reçu *plusieurs licences*, utilisez la syntaxe suivante :

```powershell
$userUPN="<user account UPN>"
$allLicenses = Get-MgUserLicenseDetail -UserId $userUPN -Property SkuPartNumber, ServicePlans
$allLicenses | ForEach-Object {
    Write-Host "License:" $_.SkuPartNumber
    $_.ServicePlans | ForEach-Object {$_}
}

```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Ensuite, répertoriez les plans de licence pour votre locataire avec cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Utilisez ces commandes pour répertorier les services disponibles dans chaque plan de licence.

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

Utilisez ces commandes pour répertorier les licences affectées à un compte d’utilisateur.

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ensuite, exécutez cette commande pour répertorier les plans de licence disponibles dans votre organisation. 

```powershell
Get-MsolAccountSku
```
>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Ensuite, exécutez cette commande pour répertorier les services disponibles dans chaque plan de licence et l’ordre dans lequel ils sont répertoriés (numéro d’index).

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
Utilisez cette commande pour répertorier les licences affectées à un utilisateur et l’ordre dans lequel elles sont répertoriées (numéro d’index).

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a>Pour afficher les services d’un compte d’utilisateur

Pour afficher tous les services Microsoft 365 auxquels un utilisateur a accès, utilisez la syntaxe suivante :
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

Cet exemple montre les services auxquels l’utilisateur BelindaN@litwareinc.com a accès. Ceci affiche les services qui sont associés à toutes les licences attribuées à son compte.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Cet exemple montre les services auxquels cet utilisateur BelindaN@litwareinc.com a accès à partir de la première licence attribuée à son compte (le numéro d’index est égal à 0).
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Pour afficher tous les services d’un utilisateur qui a reçu *plusieurs licences*, utilisez la syntaxe suivante :

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
