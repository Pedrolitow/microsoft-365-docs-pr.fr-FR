---
title: Définir le mot de passe d'un utilisateur de façon à ce qu'il n'expire jamais
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f493e3af-e1d8-4668-9211-230c245a0466
description: Découvrez comment définir certains mots de passe utilisateur individuels pour ne jamais expirer à l’aide de Windows PowerShell.
ms.openlocfilehash: 1c44f5c4d5966d70b5fed0b1b99e69b2938c6ddd
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42239344"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>Définir le mot de passe d'un utilisateur de façon à ce qu'il n'expire jamais

## <a name="set-the-password-expiration-policy-for-your-organization"></a>Définir la stratégie d’expiration des mots de passe pour votre organisation

1. Dans le centre d’administration, accédez à la page **paramètres** \> de <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">sécurité & de confidentialité</a> .
2. En regard de **stratégie de mot de passe** , sélectionnez **modifier**. 
3. Si les mots de passe sont configurés pour ne jamais expirer, **désactivez**le bouton bascule. Vous aurez la possibilité de spécifier le nombre de jours avant l’expiration des mots de passe. 


## <a name="set-the-password-expiration-policy-for-individual-users"></a>Définir la stratégie d’expiration de mot de passe pour les utilisateurs individuels 

Un administrateur général pour un service de Cloud Microsoft peut utiliser le module Microsoft Azure AD pour Windows PowerShell pour définir des mots de passe qui n’expirent pas pour des utilisateurs spécifiques. Vous pouvez également utiliser les applets de commande Windows PowerShell pour supprimer la configuration sans expiration ou pour voir quels mots de passe utilisateur sont configurés pour ne jamais expirer. 

Ce guide s’applique aux autres fournisseurs, comme Intune et Office 365, qui reposent également sur Azure AD pour les services d’identité et d’annuaire. L’expiration du mot de passe est la seule partie de la stratégie qui peut être modifiée.

> [!NOTE]
> Seuls les mots de passe des comptes d’utilisateur qui ne sont pas synchronisés via la synchronisation d’annuaires peuvent être configurés pour ne pas expirer. Pour plus d’informations sur la synchronisation d’annuaires, consultez la rubrique [Connect ad with Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).


### <a name="how-to-check-the-expiration-policy-for-a-password"></a>Procédure de vérification de la stratégie d’expiration pour un mot de passe

* Exécutez l’une des commandes suivantes :

   * Pour savoir si le mot de passe d’un utilisateur est configuré pour ne jamais expirer, exécutez l’applet de commande suivante à l’aide du nom d’utilisateur principal (par exemple, *user@contoso.onmicrosoft.com*) ou du nom d’utilisateur de l’utilisateur que vous souhaitez vérifier :
```
Get-AzureADUser -ObjectId <user id or UPN> | Select-Object UserprincipalName,@{
    N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
 }
```  
Exemple :
```
Get-AzureADUser -ObjectId userUPN@contoso.com | Select-Object UserprincipalName,@{
    N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
 }
```  

 * Pour afficher le paramètre le **mot de passe n’expire jamais** pour tous les utilisateurs, exécutez l’applet de commande suivante : 
 
```
Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
    N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
 }
```  

* Pour obtenir un rapport de tous les utilisateurs avec empêcher dans le code HTML sur le Bureau de l’utilisateur actuel portant le nom **ReportPasswordNeverExpires. html**


```
Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
    N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
} | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
```  

* Pour obtenir un rapport de tous les utilisateurs avec empêcher dans CSV sur le Bureau de l’utilisateur actuel portant le nom **ReportPasswordNeverExpires. csv**


```
Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
    N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
} | ConvertTo-Csv -NoTypeInformation | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.csv
```  


### <a name="set-a-password-to-expire"></a>Définir un mot de passe pour qu’il expire

Exécutez l’une des commandes suivantes :

   * Pour définir le mot de passe d’un utilisateur de sorte que le mot de passe expire, exécutez l’applet de commande suivante à l’aide de l’UPN ou de l’ID d’utilisateur de l’utilisateur :

```
 Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None

```
   * Pour définir les mots de passe de tous les utilisateurs de l’organisation afin qu’ils arrivent à expiration, utilisez l’applet de commande suivante :

```
 Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None

```
### <a name="set-a-password-to-never-expire"></a>Définir un mot de passe pour qu’il n’expire jamais

Exécutez l’une des commandes suivantes :

   * Pour définir le mot de passe d’un utilisateur de sorte qu’il n’expire jamais, exécutez l’applet de commande suivante à l’aide de l’UPN ou de l’ID d’utilisateur de l’utilisateur : 

```
Set-AzureADUser -ObjectId <user ID> -PasswordPolicies DisablePasswordExpiration

```
   * Pour définir les mots de passe de tous les utilisateurs d’une organisation pour qu’ils n’expirent jamais, exécutez l’applet de commande suivante : 

```
Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration

```
   > [!WARNING]
   > Mots de passe définis `-PasswordPolicies DisablePasswordExpiration` sur Age en fonction de `pwdLastSet` l’attribut. Si vous configurez les mots de passe des utilisateurs de sorte qu’ils n’expirent jamais, les mots de passe expirent dans 90 jours. En fonction de `pwdLastSet` l’attribut, si vous modifiez l’expiration `-PasswordPolicies None`, tous les mots de passe dont `pwdLastSet` le délai d’expiration est antérieur à 90 jours doivent être modifiés par l’utilisateur lors de sa prochaine connexion. Cette modification peut affecter un grand nombre d’utilisateurs. 
