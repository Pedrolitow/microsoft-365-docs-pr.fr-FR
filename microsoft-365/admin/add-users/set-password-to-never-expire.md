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
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f493e3af-e1d8-4668-9211-230c245a0466
description: Connectez-vous à votre compte d Microsoft 365 pour définir certains mots de passe utilisateur individuels de sorte qu’ils n’expirent jamais à l’aide Windows PowerShell.
ms.openlocfilehash: 12c717d8d625b0135f185b1af131db00e9762c73
ms.sourcegitcommit: 17f0aada83627d9defa0acf4db03a2d58e46842f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52635557"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>Configurer les mots de passe utilisateur pour qu'ils n'expirent jamais

Cet article explique comment définir un mot de passe pour qu’un utilisateur individuel n’expire pas. Vous devez effectuer ces étapes à l’aide de PowerShell.

## <a name="before-you-begin"></a>Avant de commencer

Cet article s’adresse aux personnes responsables de la stratégie d’expiration des mots de passe au sein d’une entreprise, d’une école ou d’une association. Pour effectuer ces étapes, vous devez vous connecter avec votre compte d’administrateur Microsoft 365. [Qu’est-ce qu’un compte d’administrateur ?](../../business-video/admin-center-overview.md) 

Vous devez être administrateur général ou administrateur de [mot de](about-admin-roles.md) passe pour effectuer ces étapes.

Un administrateur global d’un service cloud Microsoft peut utiliser la Azure Active Directory [PowerShell pour Graph](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0) pour définir les mots de passe de ne pas expirer pour des utilisateurs spécifiques. Vous pouvez également utiliser des cmdlets [AzureAD](/powershell/module/Azuread) pour supprimer la configuration qui n’expire jamais ou pour voir les mots de passe utilisateur qui ne doivent jamais expirer.

Ce guide s’applique à d’autres fournisseurs, tels que Intune et Microsoft 365, qui s’appuient également sur Azure AD pour les services d’identité et d’annuaire. L’expiration du mot de passe est la seule partie de la stratégie qui peut être modifiée.

> [!NOTE]
> Seuls les mots de passe des comptes d’utilisateur qui ne sont pas synchronisés par le biais de la synchronisation d’annuaires peuvent être configurés pour ne pas expirer. Pour plus d’informations sur la synchronisation d’annuaires, [voir Connecter AD avec Azure AD](/azure/active-directory/connect/active-directory-aadconnect).

## <a name="how-to-check-the-expiration-policy-for-a-password"></a>Comment vérifier la stratégie d’expiration pour un mot de passe

Pour plus d’informations sur Get-AzureADUser commande dans le module AzureAD, consultez l’article de référence [Get-AzureADUser](/powershell/module/Azuread/Get-AzureADUser?view=azureadps-2.0).

Exécutez une des commandes suivantes :

- Pour voir si le mot de passe d’un seul utilisateur est définie pour ne jamais expirer, exécutez l’cmdlet suivante à l’aide de l’UPN (par exemple, *user@contoso.onmicrosoft.com*) ou de l’ID utilisateur de l’utilisateur que vous souhaitez vérifier :

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

- Pour voir le paramètre Mot de passe n’expire jamais pour tous les **utilisateurs,** exécutez l’cmdlet suivante :

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
     }
    ```

- Pour obtenir un rapport de tous les utilisateurs avec PasswordNeverExpires en Html sur le bureau de l’utilisateur actuel avec le  **nomReportPasswordNeverExpires.html**

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

- Pour définir les mots de passe de tous les utilisateurs d’une organisation de sorte qu’ils n’expirent jamais, exécutez l’cmdlet suivante :

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> Les comptes d’utilisateur configurés avec le `-PasswordPolicies DisablePasswordExpiration` paramètre sont toujours basés sur l’attribut. `pwdLastSet` En fonction de l’attribut, si vous modifiez l’expiration en , tous les mots de passe qui ont un `pwdLastSet` pwdLastSet plus de 90 jours nécessitent que l’utilisateur les modifie la prochaine fois qu’ils se `-PasswordPolicies None` connectent. Cette modification peut affecter un grand nombre d’utilisateurs.

### <a name="set-a-password-to-expire"></a>Définir un mot de passe pour expirer

Exécutez une des commandes suivantes :

- Pour définir le mot de passe d’un utilisateur afin qu’il expire, exécutez la cmdlet suivante à l’aide de l’UPN ou de l’ID utilisateur de l’utilisateur :

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- Pour définir les mots de passe de tous les utilisateurs de l’organisation afin qu’ils expirent, utilisez la cmdlet suivante :

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

## <a name="related-content"></a>Contenu connexe

[Autoriser les utilisateurs à réinitialiser leur mot de passe](../add-users/let-users-reset-passwords.md) (article)\
[Réinitialiser les mots de passe](../add-users/reset-passwords.md) (article)\
[Définir la stratégie d’expiration de mot de passe pour votre organisation](../manage/set-password-expiration-policy.md) (article)