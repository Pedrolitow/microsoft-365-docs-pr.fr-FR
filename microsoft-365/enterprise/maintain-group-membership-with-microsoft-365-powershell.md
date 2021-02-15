---
title: Conserver l’appartenance à un groupe de sécurité avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Découvrez comment utiliser PowerShell pour maintenir l’appartenance aux groupes Microsoft 365.
ms.openlocfilehash: b47f501c9726e1d4dcb2e9d61108224db0408b8e
ms.sourcegitcommit: fcc1b40732f28f075d95faffc1655473e262dd95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2020
ms.locfileid: "49073060"
---
# <a name="maintain-security-group-membership-with-powershell"></a>Conserver l’appartenance à un groupe de sécurité avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez utiliser PowerShell pour Microsoft 365 comme alternative au Centre d’administration Microsoft 365 pour conserver l’appartenance au groupe de sécurité dans Microsoft 365. 

>[!Note]
>[Découvrez comment maintenir l’appartenance au groupe Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/create-groups/add-or-remove-members-from-groups) avec le Centre d’administration Microsoft 365. Pour obtenir la liste des ressources supplémentaires, voir [Gérer les utilisateurs et les groupes.](https://docs.microsoft.com/microsoft-365/admin/add-users/)
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph
Tout [d’abord, connectez-vous à votre client Microsoft 365.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Ajouter ou supprimer des comptes d’utilisateur en tant que membres d’un groupe

Pour ajouter un compte d’utilisateur par son **UPN,** indiquez le nom d’utilisateur principal (UPN) du compte d’utilisateur (par exemple : belindan@contoso.com) et le nom complet du groupe de sécurité, en supprimant les caractères « < » et « > », puis exécutez ces commandes dans la fenêtre PowerShell ou dans l’environnement de script intégré De PowerShell .

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Pour ajouter un compte d’utilisateur par son nom d’affichage, remplissez le nom complet du compte d’utilisateur (exemple : Belinda Newman) et le nom complet du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou powerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Pour supprimer un compte d’utilisateur par son **UPN,** remplissez le nom d’utilisateur upN du compte d’utilisateur (exemple : belindan@contoso.com) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou powerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Pour supprimer un compte d’utilisateur par son nom d’affichage, remplissez le nom complet du compte d’utilisateur (exemple : Belinda Newman) et le nom complet du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou powerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Ajouter ou supprimer des groupes en tant que membres d’un groupe

Les groupes de sécurité peuvent contenir d’autres groupes en tant que membres. Toutefois, les groupes Microsoft 365 ne le peuvent pas. Cette section contient des commandes PowerShell pour ajouter ou supprimer des groupes uniquement pour un groupe de sécurité.

Pour ajouter un groupe par son nom d’affichage, remplissez le nom complet du groupe que vous allez ajouter et le nom complet du groupe qui contiendra le groupe de membres et exécuterez ces commandes dans la fenêtre PowerShell ou l’ISE PowerShell.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Pour supprimer un groupe par son nom d’affichage, remplissez le nom complet du groupe que vous allez supprimer et le nom complet du groupe qui contiendra le groupe de membres et exécutez ces commandes dans la fenêtre PowerShell ou l’ISE PowerShell.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à votre client Microsoft 365.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Ajouter ou supprimer des comptes d’utilisateur en tant que membres d’un groupe

Pour ajouter un compte d’utilisateur par son **nom** d’utilisateur principal, indiquez le nom d’utilisateur principal (UPN) du compte d’utilisateur (exemple : belindan@contoso.com) et le nom complet du groupe, en supprimant les caractères « < » et « > », puis exécutez ces commandes dans la fenêtre PowerShell ou l’ISE PowerShell.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Pour ajouter un compte d’utilisateur par son nom d’affichage, remplissez le nom complet du compte d’utilisateur (exemple : Belinda Newman) et le nom complet du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou powerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Pour supprimer un compte d’utilisateur par son **UPN,** remplissez le nom d’utilisateur upN du compte d’utilisateur (exemple : belindan@contoso.com) et le nom d’affichage du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou powerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Pour supprimer un compte d’utilisateur par son nom d’affichage, remplissez le nom complet du compte d’utilisateur (exemple : Belinda Newman) et le nom complet du groupe, puis exécutez ces commandes dans la fenêtre PowerShell ou powerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Ajouter ou supprimer des groupes en tant que membres d’un groupe

Les groupes de sécurité peuvent contenir d’autres groupes en tant que membres. Toutefois, les groupes Microsoft 365 ne le peuvent pas. Cette section contient des commandes PowerShell pour ajouter ou supprimer des groupes uniquement pour un groupe de sécurité.

Pour ajouter un groupe par son nom d’affichage, remplissez le nom complet du groupe que vous allez ajouter et le nom complet du groupe qui contiendra le groupe de membres et exécuterez ces commandes dans la fenêtre PowerShell ou l’ISE PowerShell.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

Pour supprimer un groupe par son nom d’affichage, remplissez le nom complet du groupe que vous allez supprimer et le nom complet du groupe qui contiendra le groupe de membres et exécutez ces commandes dans la fenêtre PowerShell ou l’ISE PowerShell.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)

