---
title: Définir le mot de passe d’un utilisateur de façon à ce qu’il n’expire jamais
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
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
description: Découvrez comment définir certains mots de passe utilisateur individuels pour ne jamais expirer à l’aide de Windows PowerShell.
ms.openlocfilehash: f85eb2d3aaf5b19779ea8f293e2cbdc28c1535aa
ms.sourcegitcommit: 5c16d270c7651c2080a5043d273d979a6fcc75c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "46804207"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>Définir le mot de passe d’un utilisateur de façon à ce qu’il n’expire jamais

## <a name="set-the-password-expiration-policy-for-your-organization"></a>Définir la stratégie d’expiration des mots de passe pour votre organisation

1. Dans le centre d’administration, accédez à **Settings** la \> page <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">paramètres</a> des paramètres.
2. En haut de la page Paramètres, sélectionnez **sécurité & confidentialité**.
3. Sélectionnez **Stratégie d’expiration du mot de passe**. 
4. Si les mots de passe sont configurés pour ne jamais expirer, activez la case à cocher en regard de **définir les mots de passe d’utilisateur pour qu’ils expirent après un certain nombre de jours**. Vous aurez la possibilité de spécifier le nombre de jours avant l’expiration des mots de passe.

## <a name="set-the-password-expiration-policy-for-individual-users"></a>Définir la stratégie d’expiration de mot de passe pour les utilisateurs individuels

Un administrateur général pour un service de Cloud Microsoft peut utiliser [Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0) pour définir des mots de passe qui n’expirent pas pour des utilisateurs spécifiques. Vous pouvez également utiliser des applets de commande [AzureAD](https://docs.microsoft.com/powershell/module/Azuread) pour supprimer la configuration qui n’expire jamais ou pour afficher les mots de passe d’utilisateur qui sont configurés pour ne jamais expirer.

Ce guide s’applique aux autres fournisseurs, comme Intune et Microsoft 365, qui reposent également sur Azure AD pour les services d’identité et d’annuaire. L’expiration du mot de passe est la seule partie de la stratégie qui peut être modifiée.

Pour plus d’informations sur Azure AD PowerShell pour Graph, reportez-vous à la rubrique [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).

> [!NOTE]
> Seuls les mots de passe des comptes d’utilisateur qui ne sont pas synchronisés via la synchronisation d’annuaires peuvent être configurés pour ne pas expirer. Pour plus d’informations sur la synchronisation d’annuaires, consultez la rubrique [Connect ad with Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

### <a name="how-to-check-the-expiration-policy-for-a-password"></a>Procédure de vérification de la stratégie d’expiration pour un mot de passe

Pour plus d’informations sur la commande Get-AzureADUser dans le module AzureAD, voir l’article de référence [Get-AzureADUser](https://docs.microsoft.com/powershell/module/Azuread/Get-AzureADUser?view=azureadps-2.0).

Exécutez une des commandes suivantes :

- Pour savoir si le mot de passe d’un utilisateur est configuré pour ne jamais expirer, exécutez l’applet de commande suivante à l’aide du nom d’utilisateur principal (par exemple, *user@contoso.onmicrosoft.com*) ou du nom d’utilisateur de l’utilisateur que vous souhaitez vérifier :

    ```powershell
    Get-AzureADUser -ObjectId <user id or UPN> | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

    Exemple :

    ```powershell
    Get-AzureADUser -ObjectId userUPN@contoso.com | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```  

- Pour afficher le paramètre le **mot de passe n’expire jamais** pour tous les utilisateurs, exécutez l’applet de commande suivante :

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
     }
    ```

- Pour obtenir un rapport de tous les utilisateurs avec empêcher dans le code HTML sur le Bureau de l’utilisateur actuel portant le nom  **ReportPasswordNeverExpires.html**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
    ```  

- Pour obtenir un rapport de tous les utilisateurs avec empêcher dans CSV sur le Bureau de l’utilisateur actuel avec le nom **ReportPasswordNeverExpires.csv**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Csv -NoTypeInformation | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.csv
    ```

### <a name="set-a-password-to-expire"></a>Définir un mot de passe pour qu’il expire

Exécutez une des commandes suivantes :

- Pour définir le mot de passe d’un utilisateur de sorte que le mot de passe expire, exécutez l’applet de commande suivante à l’aide de l’UPN ou de l’ID d’utilisateur de l’utilisateur :

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- Pour définir les mots de passe de tous les utilisateurs de l’organisation afin qu’ils arrivent à expiration, utilisez l’applet de commande suivante :

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

### <a name="set-a-password-to-never-expire"></a>Définir un mot de passe pour qu’il n’expire jamais

Exécutez une des commandes suivantes :

- Pour définir le mot de passe d’un utilisateur de sorte qu’il n’expire jamais, exécutez l’applet de commande suivante à l’aide de l’UPN ou de l’ID d’utilisateur de l’utilisateur :

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies DisablePasswordExpiration
    ```

- Pour définir les mots de passe de tous les utilisateurs d’une organisation pour qu’ils n’expirent jamais, exécutez l’applet de commande suivante :

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> Les comptes d’utilisateur configurés avec le `-PasswordPolicies DisablePasswordExpiration` paramètre vieillissent en fonction de l' `pwdLastSet` attribut de compte d’utilisateur. Par exemple, si vous définissez des mots de passe d’utilisateur qui n’expirent jamais, puis 90 jours ou plus, les mots de passe expirent toujours. En fonction de l' `pwdLastSet` attribut du compte d’utilisateur, pour les comptes d’utilisateur configurés avec le `-PasswordPolicies None` paramètre, tous les mots de passe dont la `pwdLastSet` date est antérieure à 90 jours imposent à l’utilisateur de les modifier la prochaine fois qu’ils se connectent. Cette modification peut affecter un grand nombre d’utilisateurs.
