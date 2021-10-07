---
title: Supprimer Microsoft 365 comptes d’utilisateurs avec PowerShell
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
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Découvrez comment utiliser différents modules dans PowerShell pour supprimer Microsoft 365 comptes d’utilisateurs.
ms.openlocfilehash: dc1e5c53f2d356f0585da5a0a5285b9af28dc8f0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60171914"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a>Supprimer Microsoft 365 comptes d’utilisateurs avec PowerShell

Vous pouvez utiliser PowerShell pour Microsoft 365 pour supprimer et restaurer des comptes d’utilisateurs.

>[!Note]
>Découvrez comment restaurer [un compte d’utilisateur à l’aide](../admin/add-users/restore-user.md) du Centre d'administration Microsoft 365.
>
>Pour obtenir la liste des ressources supplémentaires, voir [Gérer les utilisateurs et les groupes.](/admin)
>   
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)

Après vous être connecté, utilisez la syntaxe suivante pour supprimer un compte d’utilisateur individuel :
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

Cet exemple supprime le compte d’utilisateur *fabricec \@ litwareinc.com*.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Le *paramètre -ObjectID* dans la cmdlet **Remove-AzureADUser** accepte le nom de la signature du compte, également appelé nom d’utilisateur principal ou ID d’objet du compte.
  
Pour afficher le nom du compte à partir du nom de l’utilisateur, utilisez les commandes suivantes :
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple affiche le nom du compte de *l’utilisateur Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Pour supprimer un compte à partir du nom de l’utilisateur, utilisez les commandes suivantes:
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.

Lorsque vous supprimez un compte d’utilisateur via Microsoft Azure Active Directory Module Windows PowerShell, le compte n’est pas supprimé définitivement. En effet, vous pouvez le restaurer dans les 30 jours.

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

Pour supprimer un compte d’utilisateur, utilisez la syntaxe suivante :
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour le module Windows PowerShell et les cmdlets incluant *Msol* dans leur nom. Exécutez ces cmdlets à partir de Windows PowerShell.
>

Cet exemple supprime le compte *d’BelindaN@litwareinc.com*.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Pour restaurer un compte d’utilisateur supprimé pendant la période de grâce de 30 jours, utilisez la syntaxe suivante :
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

Cet exemple restaure le compte supprimé *BelindaN \@ litwareinc.com*.
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

>[!Note]
> Pour afficher la liste des utilisateurs supprimés dont la restauration est possible, exécutez la commande suivante:
>    
> ```powershell
> Get-MsolUser -All -ReturnDeletedUsers
> ```
>
> Si le nom d'utilisateur principal d'origine du compte d'utilisateur est utilisé par un autre compte, utilisez le paramètre _NewUserPrincipalName_ à la place de _UserPrincipalName_ pour spécifier un autre nom d'utilisateur principal lorsque vous restaurez le compte.


## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)