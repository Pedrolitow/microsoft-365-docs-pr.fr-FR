---
title: Gérer les mots de passe avec PowerShell
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
description: Découvrez comment utiliser PowerShell pour gérer les mots de passe.
ms.openlocfilehash: d3f5ebfb7f7171cd45cf5ad1749b7bbb807068f812ee2a37f78ead7f6e8660c6
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53858746"
---
# <a name="manage-passwords-with-powershell"></a>Gérer les mots de passe avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez utiliser PowerShell pour Microsoft 365 comme alternative à l’Centre d’administration Microsoft 365 gérer les mots de passe dans Microsoft 365. 

Lorsqu’un bloc de commandes dans cet article nécessite que vous spécifiant des valeurs de variable, utilisez ces étapes.

1. Copiez le bloc de commandes dans le Presse-papiers et collez-le dans Bloc-notes ou dans l’environnement de script intégré à PowerShell (ISE).
2. Remplissez les valeurs des variables et supprimez les caractères « < » et « > ».
3. Exécutez les commandes dans la fenêtre PowerShell ou powerShell ISE.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)

### <a name="set-a-password"></a>Définir un mot de passe

Utilisez ces commandes pour spécifier un mot de passe pour un compte d’utilisateur.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword
```
### <a name="force-a-user-to-change-their-password"></a>Forcer un utilisateur à modifier son mot de passe

Utilisez ces commandes pour définir un mot de passe et forcer un utilisateur à modifier son nouveau mot de passe.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword -EnforceChangePasswordPolicy $true
```

Utilisez ces commandes pour définir un mot de passe et obliger un utilisateur à modifier son nouveau mot de passe la prochaine fois qu’il se connecte.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword -ForceChangePasswordNextLogin $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

### <a name="set-a-password"></a>Définir un mot de passe

Utilisez ces commandes pour spécifier un mot de passe pour un compte d’utilisateur.

```powershell
$userUPN="<user account sign in name>"
$newPassword="<new password>"
Set-MsolUserPassword -UserPrincipalName $userUPN -NewPassword $newPassword
```

### <a name="force-a-user-to-change-their-password"></a>Forcer un utilisateur à modifier son mot de passe

Utilisez ces commandes pour obliger un utilisateur à modifier son mot de passe.

```powershell
$userUPN="<user account sign in name>"
Set-MsolUserPassword -UserPrincipalName $userUPN -ForceChangePassword $true
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)

