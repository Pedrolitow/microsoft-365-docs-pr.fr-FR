---
title: Afficher les utilisateurs avec licence et sans licence Microsoft 365 avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/21/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- seo-marvel-apr2020
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Cet article explique comment utiliser PowerShell pour afficher les comptes d’utilisateurs Microsoft 365 licence et sans licence.
ms.openlocfilehash: 0f1b590dade1d07499ac6c9b5f8888d7cab7ecd6
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59202014"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>Afficher les utilisateurs avec licence et sans licence Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les comptes d’utilisateur de votre organisation Microsoft 365 peuvent avoir une partie, l’ensemble ou aucune des licences disponibles qui leur sont attribuées à partir des plans de gestion des licences disponibles dans votre organisation. Vous pouvez utiliser PowerShell pour Microsoft 365 trouver rapidement les utilisateurs sous licence et sans licence dans votre organisation.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
 
Pour afficher la liste de tous les comptes d’utilisateur de votre organisation qui n’ont reçu aucun de vos plans de gestion des licences (utilisateurs sans licence), exécutez la commande suivante :
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Pour afficher la liste de tous les comptes d’utilisateurs de votre organisation qui ont été affectés à l’un de vos plans de gestion des licences (utilisateurs sous licence), exécutez la commande suivante :
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>Pour lister tous les utilisateurs de votre abonnement, utilisez la `Get-AzureAdUser -All $true` commande.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

Pour afficher la liste de tous les comptes d’utilisateurs et leur état de licence dans votre organisation, exécutez la commande suivante dans PowerShell :
  
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
