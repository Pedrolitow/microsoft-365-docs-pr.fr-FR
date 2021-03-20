---
title: Gérer les groupes de sécurité avec PowerShell
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
description: Découvrez comment utiliser PowerShell pour gérer les groupes de sécurité.
ms.openlocfilehash: 64a02a1472fdeb0d61cfb4f380cbe61dd7b557b6
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50909501"
---
# <a name="manage-security-groups-with-powershell"></a>Gérer les groupes de sécurité avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez utiliser PowerShell pour Microsoft 365 comme alternative au Centre d’administration Microsoft 365 pour gérer les groupes de sécurité. 

Cet article décrit la liste, la création, la modification des paramètres et la suppression de groupes de sécurité. 

Lorsqu’un bloc de commandes dans cet article nécessite que vous spécifiant des valeurs de variable, utilisez ces étapes.

1. Copiez le bloc de commandes dans le Presse-papiers et collez-le dans le Bloc-notes ou dans l’environnement de script intégré à PowerShell (ISE).
2. Remplissez les valeurs des variables et supprimez les caractères « < » et « > ».
3. Exécutez les commandes dans la fenêtre PowerShell ou powerShell ISE.

Voir [Gérer l’appartenance à un groupe de](maintain-group-membership-with-microsoft-365-powershell.md) sécurité pour gérer l’appartenance à un groupe avec PowerShell.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à votre client Microsoft 365.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)

### <a name="list-your-groups"></a>Lister vos groupes

Utilisez cette commande pour lister tous vos groupes.

```powershell
Get-AzureADGroup
```
Utilisez ces commandes pour afficher les paramètres d’un groupe spécifique par son nom d’affichage.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>Créer un groupe

Utilisez cette commande pour créer un groupe de sécurité.

```powershell
New-AzureADGroup -Description "<group purpose>" -DisplayName "<name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "<email name>"
```

### <a name="change-the-settings-on-a-group"></a>Modifier les paramètres d’un groupe

Affichez les paramètres du groupe avec ces commandes.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Ensuite, utilisez [l’article Set-AzureADGroup](/powershell/module/azuread/set-azureadgroup) pour déterminer comment modifier un paramètre.

### <a name="remove-a-security-group"></a>Supprimer un groupe de sécurité

Utilisez ces commandes pour supprimer un groupe de sécurité.

```powershell
$groupName="<display name of the group>"
Remove-AzureADGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

### <a name="manage-the-owners-of-a-security-group"></a>Gérer les propriétaires d’un groupe de sécurité

Utilisez ces commandes pour afficher les propriétaires actuels d’un groupe de sécurité.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```
Utilisez ces commandes pour ajouter un compte d’utilisateur par son nom **d’utilisateur principal (UPN)** aux propriétaires actuels d’un groupe de sécurité.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```
Utilisez ces commandes pour ajouter un compte d’utilisateur par **son** nom complet aux propriétaires actuels d’un groupe de sécurité.

```powershell
$userName="<Display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```
Utilisez ces commandes pour supprimer un compte d’utilisateur par son **UPN** aux propriétaires actuels d’un groupe de sécurité.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```

Utilisez ces commandes pour supprimer un compte d’utilisateur par **son** nom d’affichage pour les propriétaires actuels d’un groupe de sécurité.

```powershell
$userName="<Display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à votre client Microsoft 365.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

### <a name="list-your-groups"></a>Lister vos groupes

Utilisez cette commande pour lister tous vos groupes.

```powershell
Get-MsolGroup
```
Utilisez ces commandes pour afficher les paramètres d’un groupe spécifique par son nom d’affichage.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>Créer un groupe

Utilisez cette commande pour créer un groupe de sécurité.

```powershell
New-MsolGroup -Description "<group purpose>" -DisplayName "<name>"
```

### <a name="change-the-settings-on-a-group"></a>Modifier les paramètres d’un groupe

Affichez les paramètres du groupe avec ces commandes.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Ensuite, utilisez [l’article Set-MsolGroup](/powershell/module/msonline/set-msolgroup) pour déterminer comment modifier un paramètre.

### <a name="remove-a-security-group"></a>Supprimer un groupe de sécurité

Utilisez ces commandes pour supprimer un groupe de sécurité.

```powershell
$groupName="<display name of the group>"
Remove-MsolGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)