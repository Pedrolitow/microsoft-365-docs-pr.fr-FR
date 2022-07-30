---
title: Configurer les mots de passe utilisateur pour qu'ils n'expirent jamais
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- VSBFY23
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f493e3af-e1d8-4668-9211-230c245a0466
description: Connectez-vous à votre compte d’administrateur Microsoft 365 pour définir certains mots de passe utilisateur individuels pour qu’ils n’expirent jamais à l’aide d’Azure AD PowerShell.
ms.openlocfilehash: bd9960e0da7491b5f2db14618daa17b917310450
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2022
ms.locfileid: "67084606"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>Configurer les mots de passe utilisateur pour qu'ils n'expirent jamais

Cet article explique comment définir un mot de passe pour qu’un utilisateur individuel n’expire pas. Vous devez effectuer ces étapes à l’aide de PowerShell.

## <a name="before-you-begin"></a>Avant de commencer

Cet article s’adresse aux personnes responsables de la stratégie d’expiration des mots de passe au sein d’une entreprise, d’une école ou d’une association. Pour effectuer ces étapes, vous devez vous connecter avec votre compte d’administrateur Microsoft 365. Consultez [la vue d’ensemble de la Centre d'administration Microsoft 365](/microsoft-365/admin/admin-overview/admin-center-overview).

Vous devez être [administrateur général ou administrateur de mot de passe](about-admin-roles.md) pour effectuer ces étapes.

Un administrateur général d’un service cloud Microsoft peut utiliser [Azure Active Directory PowerShell pour Graph pour](/powershell/azure/active-directory/install-adv2) définir des mots de passe qui n’expirent pas pour des utilisateurs spécifiques. Vous pouvez également utiliser des applets de commande [AzureAD](/powershell/module/Azuread) pour supprimer la configuration sans expiration ou pour voir quels mots de passe utilisateur sont définis pour ne jamais expirer.

Ce guide s’applique à d’autres fournisseurs, tels que Intune et Microsoft 365, qui s’appuient également sur Azure AD pour les services d’identité et d’annuaire. L’expiration du mot de passe est la seule partie de la stratégie qui peut être modifiée.

## <a name="how-to-check-the-expiration-policy-for-a-password"></a>Comment vérifier la stratégie d’expiration d’un mot de passe

Pour plus d’informations sur la commande Get-AzureADUser dans le module AzureAD, consultez l’article de référence [Get-AzureADUser](/powershell/module/Azuread/Get-AzureADUser).

Exécutez une des commandes suivantes :

- Pour voir si le mot de passe d’un seul utilisateur est défini pour ne jamais expirer, exécutez l’applet de commande suivante à l’aide de l’UPN (par exemple, *user@contoso.onmicrosoft.com*) ou de l’ID d’utilisateur de l’utilisateur que vous souhaitez vérifier :

    ```powershell
    Get-AzureADUser -ObjectId <user id or UPN> | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

    Exemple :

    ```powershell
    Get-AzureADUser -ObjectId userUPN@contoso.com | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

- Pour que le paramètre **Mot de passe n’expire jamais** pour tous les utilisateurs, exécutez l’applet de commande suivante :

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
     }
    ```

- Pour obtenir un rapport de tous les utilisateurs avec PasswordNeverExpires en Html sur le bureau de l’utilisateur actuel avec le nom  **ReportPasswordNeverExpires.html**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
    ```

- Pour obtenir un rapport de tous les utilisateurs avec PasswordNeverExpires dans CSV sur le bureau de l’utilisateur actuel avec le nom **ReportPasswordNeverExpires.csv**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Csv -NoTypeInformation | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.csv

## Set a password to never expire

Run one of the following commands:

- To set the password of one user to never expire, run the following cmdlet by using the UPN or the user ID of the user:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies DisablePasswordExpiration
    ```

- Pour que les mots de passe de tous les utilisateurs d’une organisation n’expirent jamais, exécutez l’applet de commande suivante :

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> Comptes d’utilisateur configurés avec le `-PasswordPolicies DisablePasswordExpiration` paramètre toujours vieillir en fonction de l’attribut `pwdLastSet` . En fonction de l’attribut `pwdLastSet` , si vous remplacez l’expiration `-PasswordPolicies None`par , tous les mots de passe ayant un pwdLastSet de plus de 90 jours nécessitent que l’utilisateur les modifie la prochaine fois qu’il se connecte. Cette modification peut affecter un grand nombre d’utilisateurs.

### <a name="set-a-password-to-expire"></a>Définir un mot de passe pour expirer

Exécutez une des commandes suivantes :

- Pour définir le mot de passe d’un utilisateur afin que le mot de passe expire, exécutez l’applet de commande suivante à l’aide de l’UPN ou de l’ID utilisateur de l’utilisateur :

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- Pour définir les mots de passe de tous les utilisateurs de l’organisation afin qu’ils expirent, utilisez l’applet de commande suivante :

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

## <a name="related-content"></a>Contenu connexe

[Autoriser les utilisateurs à réinitialiser leur mot de passe](../add-users/let-users-reset-passwords.md) (article)\
[Réinitialiser les mots de passe](../add-users/reset-passwords.md) (article)\
[Définir la stratégie d’expiration du mot de passe pour votre organisation](../manage/set-password-expiration-policy.md) (article)
