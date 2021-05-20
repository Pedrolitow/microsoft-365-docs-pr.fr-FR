---
title: Définir le mot de passe d’un utilisateur de façon à ce qu’il n’expire jamais
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
description: Connectez-vous à votre compte Microsoft 365'administration pour définir certains mots de passe individuels de l’utilisateur pour ne jamais expirer en utilisant Windows PowerShell.
ms.openlocfilehash: 0747e0bfe8a7389db554d5d6a7f685605e013306
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52571924"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>Définir le mot de passe d’un utilisateur de façon à ce qu’il n’expire jamais

Cet article explique comment définir un mot de passe pour qu’un utilisateur individuel n’expire pas. Vous devez compléter ces étapes à l’aide de PowerShell.

## <a name="before-you-begin"></a>Avant de commencer

Cet article s’adresse aux personnes responsables de la stratégie d’expiration des mots de passe au sein d’une entreprise, d’une école ou d’une association. Pour effectuer ces étapes, vous devez vous connecter avec votre compte d’administrateur Microsoft 365. [Qu’est-ce qu’un compte d’administrateur ?](../../business-video/admin-center-overview.md) 

Vous devez être un administrateur [global ou un administrateur de mot de](about-admin-roles.md) passe pour effectuer ces étapes.

Un administrateur global d’un service cloud Microsoft peut utiliser [le Azure Active Directory PowerShell pour Graph définir](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0) des mots de passe à ne pas expirer pour des utilisateurs spécifiques. Vous pouvez également utiliser des cmdlets [AzureAD](/powershell/module/Azuread) pour supprimer la configuration jamais expirée ou pour voir quels mots de passe d’utilisateur sont configurés pour ne jamais expirer.

Ce guide s’applique à d’autres fournisseurs, tels qu’Intune et Microsoft 365, qui comptent également sur Azure AD pour les services d’identité et d’annuaire. L’expiration du mot de passe est la seule partie de la stratégie qui peut être modifiée.

> [!NOTE]
> Seuls les mots de passe pour les comptes utilisateur qui ne sont pas synchronisés par synchronisation d’annuaire peuvent être configurés pour ne pas expirer. Pour plus d’informations sur la synchronisation des répertoires, [Connecter votre annonce avec Azure AD](/azure/active-directory/connect/active-directory-aadconnect).

## <a name="how-to-check-the-expiration-policy-for-a-password"></a>Comment vérifier la stratégie d’expiration d’un mot de passe

Pour plus d’informations sur Get-AzureADUser commande dans le module AzureAD, consultez l’article de [référence Get-AzureADUser](/powershell/module/Azuread/Get-AzureADUser?view=azureadps-2.0).

Exécutez une des commandes suivantes :

- Pour voir si le mot de passe d’un seul utilisateur n’expire jamais, exécutez le cmdlet suivant en utilisant l’UPN *(par exemple, user@contoso.onmicrosoft.com)* ou l’identifiant utilisateur de l’utilisateur que vous souhaitez vérifier :

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

- Pour voir le mot **de passe n’expire** jamais paramètre pour tous les utilisateurs, exécutez le cmdlet suivant:

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
     }
    ```

- Pour obtenir un rapport de tous les utilisateurs avec PasswordNeverExpires en Html sur le bureau de l’utilisateur actuel avec  **le nomReportPasswordNeverExpires.html**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
    ```  

- Pour obtenir un rapport de tous les utilisateurs avec PasswordNeverExpires en CSV sur le bureau de l’utilisateur actuel avec nom **ReportPasswordNeverExpires.csv**

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

- Pour définir les mots de passe de tous les utilisateurs d’une organisation pour qu’ils n’expirent jamais, exécutez le cmdlet suivant :

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> Comptes utilisateur configurés avec le `-PasswordPolicies DisablePasswordExpiration` paramètre encore en fonction de l’attribut. `pwdLastSet` En fonction de `pwdLastSet` l’attribut, si vous modifiez l’expiration `-PasswordPolicies None` à , tous les mots de passe qui ont un pwdLastSet plus de 90 jours exigent de l’utilisateur de les changer la prochaine fois qu’ils se connectent. Ce changement peut affecter un grand nombre d’utilisateurs.

### <a name="set-a-password-to-expire"></a>Définir un mot de passe pour expirer

Exécutez une des commandes suivantes :

- Pour définir le mot de passe d’un utilisateur afin que le mot de passe expire, exécutez le cmdlet suivant en utilisant l’UPN ou l’identifiant utilisateur de l’utilisateur :

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- Pour définir les mots de passe de tous les utilisateurs de l’organisation afin qu’ils expirent, utilisez le cmdlet suivant :

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

## <a name="related-content"></a>Contenu connexe

[Autoriser les utilisateurs à réinitialiser leur mot de passe](../add-users/let-users-reset-passwords.md) (article)

[Réinitialiser les mots de passe](../add-users/reset-passwords.md) (article)