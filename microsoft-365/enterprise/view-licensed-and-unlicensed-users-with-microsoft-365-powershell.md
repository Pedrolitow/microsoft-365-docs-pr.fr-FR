---
title: Afficher les utilisateurs Microsoft 365 sous licence et sans licence avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/21/2020
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- seo-marvel-apr2020
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Cet article explique comment utiliser PowerShell pour afficher les comptes d’utilisateurs Microsoft 365 sous licence et sans licence.
ms.openlocfilehash: cd33a9ef5eaadd9c8ccf03dfb9c2f0c283016ebe
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68194486"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>Afficher les utilisateurs Microsoft 365 sous licence et sans licence avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les comptes d’utilisateur de votre organisation Microsoft 365 peuvent avoir une partie, la totalité ou l’aucune des licences disponibles qui leur sont attribuées à partir des plans de licence disponibles dans votre organisation. Vous pouvez utiliser PowerShell pour Microsoft 365 pour rechercher rapidement les utilisateurs sous licence et sans licence dans votre organisation.

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Utiliser le Kit de développement logiciel (SDK) Microsoft Graph PowerShell

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](/graph/powershell/get-started#authentication).

La lecture des propriétés de l’utilisateur, y compris les détails de la licence, nécessite l’étendue d’autorisation User.Read.All ou l’une des autres autorisations répertoriées dans la [page de référence « Obtenir un utilisateur » API Graph](/graph/api/user-get).

L’étendue d’autorisation Organization.Read.All est nécessaire pour lire les licences disponibles dans le locataire.

```powershell
Connect-Graph -Scopes User.Read.All, Organization.Read.All
```

Pour afficher les détails de licence d’un compte d’utilisateur spécifique, exécutez la commande suivante :
  
```powershell
Get-MgUserLicenseDetail -UserId "<user sign-in name (UPN)>"
```

Par exemple :

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

Pour afficher la liste de tous les comptes d’utilisateurs de votre organisation qui n’ont REÇU AUCUN de vos plans de licence (utilisateurs sans licence), exécutez la commande suivante :
  
```powershell
Get-MgUser -Filter 'assignedLicenses/$count eq 0' -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All

Write-Host "Found $unlicensedUserCount unlicensed users."
```

Pour afficher la liste de tous les comptes d’utilisateurs membres (à l’exclusion des invités) de votre organisation qui n’ont reçu aucun de vos plans de licence (utilisateurs sans licence), exécutez la commande suivante :
  
```powershell
Get-MgUser -Filter "assignedLicenses/`$count eq 0 and userType eq 'Member'" -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All

Write-Host "Found $unlicensedUserCount unlicensed users (excluding guests)."
```

Pour afficher la liste de tous les comptes d’utilisateurs de votre organisation qui ont reçu l’un de vos plans de licence (utilisateurs sous licence), exécutez la commande suivante :
  
```powershell
Get-MgUser -Filter 'assignedLicenses/$count ne 0' -ConsistencyLevel eventual -CountVariable licensedUserCount -All -Select UserPrincipalName,DisplayName,AssignedLicenses | Format-Table -Property UserPrincipalName,DisplayName,AssignedLicenses

Write-Host "Found $licensedUserCount licensed users."
```

Pour afficher la liste de tous les comptes d’utilisateurs de votre organisation auxquels une licence E5 est attribuée, exécutez la commande suivante :

```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'

Get-MgUser -Filter "assignedLicenses/any(x:x/skuId eq $($e5sku.SkuId) )" -ConsistencyLevel eventual -CountVariable e5licensedUserCount -All

Write-Host "Found $e5licensedUserCount E5 licensed users."
```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Pour afficher la liste de tous les comptes d’utilisateurs de votre organisation qui n’ont REÇU AUCUN de vos plans de licence (utilisateurs sans licence), exécutez la commande suivante :
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Pour afficher la liste de tous les comptes d’utilisateurs de votre organisation qui ont reçu l’un de vos plans de licence (utilisateurs sous licence), exécutez la commande suivante :
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>Pour répertorier tous les utilisateurs de votre abonnement, utilisez la `Get-AzureAdUser -All $true` commande.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Pour afficher la liste de tous les comptes d’utilisateur et leur état de licence dans votre organisation, exécutez la commande suivante dans PowerShell :
  
```powershell
Get-MsolUser -All
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Pour afficher la liste de tous les comptes d’utilisateurs sans licence dans votre organisation, exécutez la commande suivante :
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Pour afficher la liste de tous les comptes d’utilisateurs avec licence dans votre organisation, exécutez la commande suivante :
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
