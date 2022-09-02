---
title: Supprimer des comptes d’utilisateur Microsoft 365 avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/23/2020
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
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
description: Découvrez comment utiliser différents modules dans PowerShell pour supprimer des comptes d’utilisateurs Microsoft 365.
ms.openlocfilehash: 3ee58698400944b27f6e19d154d7a9d0c8bfccc1
ms.sourcegitcommit: 62368e5a48e569c8e475b07d194d7d8ff7d167ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67560216"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a>Supprimer des comptes d’utilisateur Microsoft 365 avec PowerShell

Vous pouvez utiliser PowerShell pour Microsoft 365 pour supprimer et restaurer des comptes d’utilisateur.

>[!Note]
>Découvrez comment [restaurer un compte d’utilisateur](../admin/add-users/restore-user.md) à l’aide de la Centre d'administration Microsoft 365.
>
>Pour obtenir la liste des ressources supplémentaires, consultez [Gérer les utilisateurs et les groupes](/admin).
>   
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Après vous être connecté, utilisez la syntaxe suivante pour supprimer un compte d’utilisateur individuel :
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

Cet exemple supprime le compte d’utilisateur *fabricec\@litwareinc.com*.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Le paramètre *-ObjectID* dans l’applet de commande **Remove-AzureADUser** accepte le nom de connexion du compte, également appelé nom d’utilisateur principal ou ID d’objet du compte.
  
Pour afficher le nom du compte à partir du nom de l’utilisateur, utilisez les commandes suivantes :
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple montre comment afficher le nom du compte de l’utilisateur *Caleb Sills*.
  
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

Lorsque vous supprimez un compte d’utilisateur via le module Microsoft Azure Active Directory pour Windows PowerShell, le compte n’est pas supprimé définitivement. En effet, vous pouvez le restaurer dans les 30 jours.

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Pour supprimer un compte d’utilisateur, utilisez la syntaxe suivante :
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>PowerShell Core ne prend pas en charge le Module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande avec *Msol* dans leur nom. Exécutez ces applets de commande à partir de Windows PowerShell.
>

Cet exemple montre comment supprimer le compte d’utilisateur *BelindaN@litwareinc.com*.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Pour restaurer un compte d’utilisateur supprimé pendant la période de grâce de 30 jours, utilisez la syntaxe suivante :
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

Cet exemple montre comment restaurer le compte supprimé *Be réinit litwareinc.com\@.*
  
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
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)