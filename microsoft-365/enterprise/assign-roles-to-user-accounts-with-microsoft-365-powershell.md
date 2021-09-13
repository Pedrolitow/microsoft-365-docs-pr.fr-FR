---
title: Attribuer des rôles Microsoft 365 comptes d’utilisateur avec PowerShell
ms.author: kvice
author: kelleyvice-msft
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: Dans cet article, découvrez comment utiliser rapidement et facilement PowerShell pour Microsoft 365 attribuer des rôles d’administrateur à des comptes d’utilisateur.
ms.openlocfilehash: 4174877bed9accacc3a61de576fa6e54060678bf
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204096"
---
# <a name="assign-admin-roles-to-microsoft-365-user-accounts-with-powershell"></a>Attribuer des rôles d’administrateur Microsoft 365 comptes d’utilisateurs avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez facilement attribuer des rôles à des comptes d’utilisateurs à l’aide de PowerShell pour Microsoft 365.

>[!Note]
>Découvrez comment attribuer [des rôles d’administrateur](../admin/add-users/assign-admin-roles.md) à des comptes d’utilisateurs à l’Centre d'administration Microsoft 365.
>
>Pour obtenir la liste des ressources supplémentaires, voir [Gérer les utilisateurs et les groupes.](../admin/add-users/index.yml)
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout d’abord, utilisez un administrateur Azure  **AD DC,** un administrateur d’application **cloud** ou un compte d’administrateur global pour vous connecter à Microsoft 365 [client.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
 
Pour plus d’informations, consultez [À propos des rôles d’administrateur](/microsoft-365/admin/add-users/about-admin-roles?).

Ensuite, identifiez le nom de la signature du compte d’utilisateur que vous souhaitez ajouter à un rôle (exemple : fredsm \@ contoso.com). Il s’agit également du nom d’utilisateur principal (UPN).

Ensuite, déterminez le nom du rôle. Voir [rôles intégrés à Azure AD.](/azure/active-directory/roles/permissions-reference)

>[!Note]
>Soyez attentif aux notes dans cet article. Certains noms de rôles sont différents pour Azure Active Directory (Azure AD) PowerShell. Par exemple, le *rôle SharePoint administrateur* principal dans le Centre d'administration Microsoft 365 est administrateur SharePoint *service* dans Azure AD PowerShell.
>

Ensuite, remplissez les noms de la signature et du rôle, puis exécutez les commandes suivantes :
  
```powershell
$userName="<sign-in name of the account>"
$roleName="<admin role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

Voici un exemple d’un jeu de commandes terminé qui attribue le rôle Administrateur de service SharePoint au compte contoso.com *belindan \@* :
  
```powershell
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

Pour afficher la liste des noms d’utilisateur pour un rôle d’administrateur spécifique, utilisez ces commandes.

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, utilisez un compte d’administrateur général pour vous [connecter à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)
  
### <a name="for-a-single-role-change"></a>Pour une seule modification de rôle

Les méthodes les plus courantes pour spécifier le compte d’utilisateur sont d’utiliser son nom complet ou son nom d’e-mail, également appelé nom de la signature ou nom d’utilisateur principal (UPN).

#### <a name="display-names-of-user-accounts"></a>Afficher les noms des comptes d’utilisateur

Si vous avez l’habitude d’utiliser les noms d’affichage des comptes d’utilisateur, déterminez les informations suivantes :
  
- Le compte d’utilisateur que vous souhaitez configurer
    
    Pour spécifier le compte d'utilisateur, vous devez déterminer son nom d'affichage. Pour obtenir la liste complète des comptes, utilisez la commande ci-dessous :
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Cette commande répertorie le nom d'affichage de vos comptes d'utilisateur, triés par nom d'affichage, un écran à la fois. Vous pouvez filtrer la liste pour réduire l'ensemble à l'aide de la cmdlet **Where**. Voir l’exemple ci-dessous.

   >[!Note]
   >PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour le module Windows PowerShell et les cmdlets incluant *Msol* dans leur nom. Exécutez ces cmdlets à partir de Windows PowerShell.
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Cette commande répertorie uniquement les comptes d’utilisateur dont le nom d’affichage commence par « John ».
    
- Rôle que vous souhaitez attribuer
    
    Pour afficher la liste des rôles d’administrateur disponibles que vous pouvez attribuer aux comptes d’utilisateurs, utilisez cette commande :
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Après avoir déterminez le nom complet du compte et le nom du rôle, utilisez les commandes ci-après pour attribuer le rôle au compte :
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The admin role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Collez les commandes dans Bloc-notes. Pour les *$dispName* et *$roleName* variables, remplacez le texte de description par leurs valeurs. Supprimez les \< and > caractères, mais conservez les guillemets. Collez les lignes modifiées dans Microsoft Azure Active Directory module de Windows PowerShell fenêtre pour les exécuter. Vous pouvez également utiliser l'environnement d'écriture de scripts intégré de Windows PowerShell.
  
Voici un exemple de jeu de commandes terminé :
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>Noms de la signature des comptes d’utilisateur

Si vous avez l’habitude d’utiliser les noms de la signature ou les UPN des comptes d’utilisateur, déterminez les informations suivantes :
  
- UpN du compte d’utilisateur
    
    Si vous ne connaissez pas l’UPN, utilisez la commande ci-après :
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Cette commande répertorie l’UPN de vos comptes d’utilisateur, triés par nom d’utilisateur principal, un écran à la fois. Vous pouvez utiliser la cmdlet **Where** pour filtrer la liste. Voici un exemple :
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Cette commande répertorie uniquement les comptes d’utilisateur dont le nom d’affichage commence par « John ».
    
- Rôle que vous souhaitez attribuer
    
    Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Une fois que vous avez l’UPN du compte et le nom du rôle, utilisez les commandes ci-après pour attribuer le rôle au compte :
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

Copiez les commandes et collez-les dans le bloc-notes. Pour les **variables $upnName** et **$roleName** variables. Remplacez le texte de description par leurs valeurs. Supprimez les \< and > caractères, mais conservez les guillemets. Collez les lignes modifiées dans Microsoft Azure Active Directory module de Windows PowerShell fenêtre pour les exécuter. Vous pouvez également utiliser l’Windows PowerShell ISE.
  
Voici un exemple de jeu de commandes terminé :
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>Modifications multiples de rôle

Pour plusieurs modifications de rôle, déterminez les informations suivantes :
  
- Les comptes d’utilisateur que vous souhaitez configurer. Vous pouvez utiliser les méthodes de la section précédente pour collecter l’ensemble de noms d’affichage ou d’UPN.
    
- Les rôles que vous souhaitez attribuer à chaque compte d’utilisateur. Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Ensuite, créez un fichier texte de valeurs séparées par des virgules (CSV) avec le nom d’affichage ou les champs UPN et nom de rôle. Vous pouvez le faire facilement en Microsoft Excel.

Voici un exemple pour les noms d’affichage :
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

Ensuite, remplissez l’emplacement du fichier CSV et exécutez les commandes qui en résultent à l’invite de commande PowerShell.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

Voici un exemple pour les upns :
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

Ensuite, remplissez l’emplacement du fichier CSV et exécutez les commandes qui en résultent à l’invite de commande PowerShell.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>Voir aussi

- [Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
- [Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
