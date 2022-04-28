---
title: Attribuer des rôles à des comptes d’utilisateur Microsoft 365 avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: Dans cet article, découvrez comment utiliser PowerShell rapidement et facilement pour Microsoft 365 pour attribuer des rôles d’administrateur à des comptes d’utilisateur.
ms.openlocfilehash: 8ac98920dd3d2d0487905b001434d73274463f9a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097445"
---
# <a name="assign-admin-roles-to-microsoft-365-user-accounts-with-powershell"></a>Attribuer des rôles d’administrateur à Microsoft 365 comptes d’utilisateur avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez facilement attribuer des rôles à des comptes d’utilisateurs à l’aide de PowerShell pour Microsoft 365.

>[!Note]
>Découvrez comment [attribuer des rôles d’administrateur](../admin/add-users/assign-admin-roles.md) à des comptes d’utilisateur avec le Centre d'administration Microsoft 365.
>
>Pour obtenir la liste des ressources supplémentaires, consultez [Gérer les utilisateurs et les groupes](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout d’abord, utilisez un compte **d’administrateur de contrôleur** de domaine Azure AD, **d’administrateur d’application cloud** ou **d’administrateur général** pour [vous connecter à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](/microsoft-365/admin/add-users/about-admin-roles?).

Ensuite, identifiez le nom de connexion du compte d’utilisateur que vous souhaitez ajouter à un rôle (exemple : fredsm\@ contoso.com). Il s’agit également du nom d’utilisateur principal (UPN).

Ensuite, déterminez le nom du rôle. Consultez [Azure AD rôles intégrés](/azure/active-directory/roles/permissions-reference).

>[!Note]
>Soyez attentif aux notes dans cet article. Certains noms de rôles sont différents pour Azure Active Directory (Azure AD) PowerShell. Par exemple, le rôle *Administrateur SharePoint* dans le Centre d'administration Microsoft 365 est *SharePoint Administrateur de service* dans Azure AD PowerShell.
>

Ensuite, renseignez les noms de connexion et de rôle et exécutez les commandes suivantes :
  
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

Voici un exemple de jeu de commandes terminé qui affecte le rôle d’administrateur de service SharePoint au compte *contoso.com :\@*
  
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

Tout d’abord, utilisez un compte d’administrateur général pour [vous connecter à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
### <a name="for-a-single-role-change"></a>Pour une seule modification de rôle

La méthode la plus courante pour spécifier le compte d’utilisateur consiste à utiliser son nom d’affichage ou son nom de messagerie, également appelé nom de connexion ou nom d’utilisateur principal (UPN).

#### <a name="display-names-of-user-accounts"></a>Afficher les noms des comptes d’utilisateur

Si vous avez l’habitude d’utiliser les noms complets des comptes d’utilisateur, déterminez les informations suivantes :
  
- Compte d’utilisateur que vous souhaitez configurer
    
    Pour spécifier le compte d'utilisateur, vous devez déterminer son nom d'affichage. Pour obtenir la liste complète des comptes, utilisez cette commande :
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Cette commande répertorie le nom d'affichage de vos comptes d'utilisateur, triés par nom d'affichage, un écran à la fois. Vous pouvez filtrer la liste pour réduire l'ensemble à l'aide de la cmdlet **Where**. Voir l’exemple ci-dessous.

   >[!Note]
   >PowerShell Core ne prend pas en charge le Module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande avec *Msol* dans leur nom. Exécutez ces applets de commande à partir de Windows PowerShell.
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Cette commande répertorie uniquement les comptes d’utilisateur dont le nom d’affichage commence par « John ».
    
- Rôle que vous souhaitez attribuer
    
    Pour afficher la liste des rôles d’administrateur disponibles que vous pouvez attribuer à des comptes d’utilisateur, utilisez cette commande :
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Une fois que vous avez déterminé le nom complet du compte et le nom du rôle, utilisez ces commandes pour attribuer le rôle au compte :
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The admin role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Collez les commandes dans Bloc-notes. Pour les variables *$dispName* et *$roleName* , remplacez le texte de description par leurs valeurs. Supprimez les \< and > caractères, mais conservez les guillemets. Collez les lignes modifiées dans le module Microsoft Azure Active Directory pour Windows PowerShell fenêtre afin de les exécuter. Vous pouvez également utiliser l'environnement d'écriture de scripts intégré de Windows PowerShell.
  
Voici un exemple de jeu de commandes terminé :
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>Noms de connexion des comptes d’utilisateur

Si vous avez l’habitude d’utiliser les noms de connexion ou upN des comptes d’utilisateur, déterminez les informations suivantes :
  
- UPN du compte d’utilisateur
    
    Si vous ne connaissez pas l’UPN, utilisez cette commande :
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Cette commande répertorie l’UPN de vos comptes d’utilisateur, trié par UPN, un écran à la fois. Vous pouvez utiliser l’applet de commande **Where** pour filtrer la liste. Voici un exemple :
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Cette commande répertorie uniquement les comptes d’utilisateur dont le nom d’affichage commence par « John ».
    
- Rôle que vous souhaitez attribuer
    
    Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Une fois que vous disposez de l’UPN du compte et du nom du rôle, utilisez ces commandes pour attribuer le rôle au compte :
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

Copiez les commandes et collez-les dans le bloc-notes. Pour les variables **$upnName** et **$roleName** . Remplacez le texte de description par leurs valeurs. Supprimez les \< and > caractères, mais conservez les guillemets. Collez les lignes modifiées dans Microsoft Azure Active Directory Module pour Windows PowerShell fenêtre afin de les exécuter. Vous pouvez également utiliser le Windows PowerShell ISE.
  
Voici un exemple de jeu de commandes terminé :
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>Changements de rôle multiples

Pour plusieurs modifications de rôle, déterminez les informations suivantes :
  
- Les comptes d’utilisateur que vous souhaitez configurer. Vous pouvez utiliser les méthodes de la section précédente pour collecter l’ensemble de noms d’affichage ou d’UPN.
    
- Les rôles que vous souhaitez attribuer à chaque compte d’utilisateur. Pour afficher la liste des rôles disponibles que vous pouvez attribuer aux comptes d’utilisateur, utilisez cette commande :
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Ensuite, créez un fichier texte de valeur séparée par des virgules (CSV) qui a le nom complet ou les champs UPN et nom de rôle. Vous pouvez le faire facilement dans Microsoft Excel.

Voici un exemple de noms d’affichage :
  
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

Voici un exemple pour les UPN :
  
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
- [Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
