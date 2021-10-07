---
title: Bloquer Microsoft 365 comptes d’utilisateurs avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/16/2020
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
- Ent_Office_Other
- PowerShell
- seo-marvel-apr2020
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Comment utiliser PowerShell pour bloquer et débloquer l’accès Microsoft 365 comptes.
ms.openlocfilehash: 0ecfdfb8f99175ce5312769593c7637a7d1ae25b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60189188"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a>Bloquer Microsoft 365 comptes d’utilisateurs avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Lorsque vous bloquez l’accès à un compte Microsoft 365, vous empêchez quiconque d’utiliser le compte pour se connecter et accéder aux services et données de votre organisation Microsoft 365. Vous pouvez utiliser PowerShell pour bloquer l’accès à des comptes d’utilisateurs individuels ou multiples.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)

### <a name="block-access-to-individual-user-accounts"></a>Bloquer l’accès à des comptes d’utilisateurs individuels

Utilisez la syntaxe suivante pour bloquer un compte d’utilisateur individuel :

```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Le *paramètre -ObjectID* dans la cmdlet **Set-AzureAD** accepte soit le nom de la signature du compte, également appelé nom d’utilisateur principal, soit l’ID d’objet du compte.

Cet exemple bloque l’accès au compte *d’fabricec@litwareinc.com*.

```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Pour débloquer ce compte, exécutez la commande suivante :

```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Pour afficher l’UPN du compte d’utilisateur en fonction du nom d’affichage de l’utilisateur, utilisez les commandes suivantes :

```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

Cet exemple affiche l’UPN du compte d’utilisateur  *pour l’utilisateur Caleb Sills*.

```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Pour bloquer un compte en fonction du nom complet de l’utilisateur, utilisez les commandes suivantes :

```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

Pour vérifier l’état bloqué d’un compte d’utilisateur, utilisez la commande suivante :

```powershell
Get-AzureADUser  -ObjectID <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-multiple-user-accounts"></a>Bloquer plusieurs comptes d’utilisateurs

Pour bloquer l’accès à plusieurs comptes d’utilisateurs, créez un fichier texte qui contient un nom de signature de compte sur chaque ligne comme ceci :

  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

Dans les commandes suivantes, l’exemple de fichier texte est *C:\My Documents\Accounts.txt*. Remplacez ce nom de fichier par le chemin d’accès et le nom de fichier de votre fichier texte.

Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $false}
```

Pour débloquer les comptes répertoriés dans le fichier texte, exécutez la commande suivante :

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $true}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

### <a name="block-individual-user-accounts"></a>Bloquer des comptes d’utilisateurs individuels

Utilisez la syntaxe suivante pour bloquer l’accès à un compte d’utilisateur individuel :

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les cmdlets dont le nom comprend *Msol.* Vous devez exécuter ces cmdlets à partir Windows PowerShell.

Cet exemple bloque l’accès au compte d’utilisateur *fabricec \@ litwareinc.com*.

```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Pour débloquer le compte, exécutez la commande suivante :

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

Pour vérifier l’état bloqué d’un compte d’utilisateur, exécutez la commande suivante :

```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-for-multiple-user-accounts"></a>Bloquer l’accès à plusieurs comptes d’utilisateurs

Tout d’abord, créez un fichier texte qui contient un compte sur chaque ligne comme ceci :

```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

Dans les commandes suivantes, l’exemple de fichier texte est *C:\My Documents\Accounts.txt*. Remplacez ce nom de fichier par le chemin d’accès et le nom de fichier de votre fichier texte.

Pour bloquer l’accès aux comptes répertoriés dans le fichier texte, exécutez la commande suivante :

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
