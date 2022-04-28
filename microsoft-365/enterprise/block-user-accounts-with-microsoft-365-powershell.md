---
title: Bloquer Microsoft 365 comptes d’utilisateur avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Comment utiliser PowerShell pour bloquer et débloquer l’accès aux comptes Microsoft 365.
ms.openlocfilehash: ffeac03f9f48e6531443a8f90a3d5fd3506172fe
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091608"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a>Bloquer Microsoft 365 comptes d’utilisateur avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Lorsque vous bloquez l’accès à un compte Microsoft 365, vous empêchez quiconque d’utiliser le compte pour se connecter et accéder aux services et aux données de votre organisation Microsoft 365. Vous pouvez utiliser PowerShell pour bloquer l’accès à des comptes d’utilisateur individuels ou multiples.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="block-access-to-individual-user-accounts"></a>Bloquer l’accès à des comptes d’utilisateur individuels

Utilisez la syntaxe suivante pour bloquer un compte d’utilisateur individuel :

```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Le paramètre *-ObjectID* dans l’applet de commande **Set-AzureAD** accepte soit le nom de connexion du compte, également appelé nom d’utilisateur principal, soit l’ID d’objet du compte.

Cet exemple bloque l’accès au compte d’utilisateur *fabricec@litwareinc.com*.

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

Cet exemple montre comment afficher l’UPN du compte d’utilisateur pour l’utilisateur  *Caleb Sills*.

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

### <a name="block-multiple-user-accounts"></a>Bloquer plusieurs comptes d’utilisateur

Pour bloquer l’accès à plusieurs comptes d’utilisateur, créez un fichier texte qui contient un nom de connexion de compte sur chaque ligne comme suit :

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

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="block-individual-user-accounts"></a>Bloquer des comptes d’utilisateur individuels

Utilisez la syntaxe suivante pour bloquer l’accès à un compte d’utilisateur individuel :

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell module et les applets de commande qui ont *Msol* dans leur nom. Vous devez exécuter ces applets de commande à partir de Windows PowerShell.

Cet exemple bloque l’accès au compte *d’utilisateur fabricec\@ litwareinc.com*.

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

### <a name="block-access-for-multiple-user-accounts"></a>Bloquer l’accès pour plusieurs comptes d’utilisateur

Tout d’abord, créez un fichier texte qui contient un compte sur chaque ligne comme suit :

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

[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
