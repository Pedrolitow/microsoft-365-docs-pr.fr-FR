---
title: Configurer les propriétés du compte d’utilisateur Microsoft 365 avec PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: Utilisez PowerShell pour Microsoft 365 pour configurer les propriétés de comptes d’utilisateur individuels ou multiples dans votre client Microsoft 365.
ms.openlocfilehash: 6b674641842f89fd8c8e22dc26350cdd53734b9e
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50911083"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>Configurer les propriétés du compte d’utilisateur Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez utiliser le Centre d’administration Microsoft 365 pour configurer les propriétés des comptes d’utilisateur de votre client Microsoft 365. Dans PowerShell, vous pouvez également le faire, ainsi que d’autres choses que vous ne pouvez pas faire dans le Centre d’administration.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Pour configurer les propriétés des comptes d’utilisateurs dans le module Azure Active Directory PowerShell pour Graph, utilisez la cmdlet [**Set-AzureADUser**](/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) et spécifiez les propriétés à définir ou modifier.

Tout [d’abord, connectez-vous à votre client Microsoft 365.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
   
### <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d’un compte d’utilisateur spécifique

Vous identifiez le compte avec le *paramètre -ObjectID* et définissez ou modifiez des propriétés spécifiques à l’aide de paramètres supplémentaires. Voici la liste des paramètres les plus courants :
  
- -Department "\<department name>"
    
- -DisplayName "\<full user name>"
    
- -FacsimilieTelephoneNumber "<numéro de télécopie>"
    
- -GivenName "<prénom de l'utilisateur>"
    
- -Surname "<nom de famille de l'utilisateur>"
    
- -Mobile "<N° de téléphone portable>"
    
- -JobTitle "\<job title>"
    
- -PreferredLanguage "\<language>"
    
- -StreetAddress "\<street address>"
    
- -City "\<city name>"
    
- -State "<nom de l'État>"
    
- -PostalCode "\<postal code>
    
- -Country "\<country name>"
    
- -TelephoneNumber "<numéro de téléphone du bureau>"
    
- -UsageLocation \<2-character country or region code> »
    
    Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).
    
Pour d’autres paramètres, [voir Set-AzureADUser](/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) .

>[!Note]
>Avant de pouvoir attribuer des licences à un compte d’utilisateur, vous devez affecter un emplacement d’utilisation.
>

Pour afficher le nom d’utilisateur principal pour vos comptes d’utilisateur, exécutez la commande suivante.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Cette commande indique à PowerShell de :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**) et envoyez-les à la commande suivante ( **|** ).
    
1. Trier la liste des noms d’utilisateur principaux par ordre alphabétique (**Trier UserPrincipalName**) et l’envoyer à la commande suivante ( **|** ).
    
1. Afficher uniquement la propriété Nom d’utilisateur principal pour chaque compte (**Sélectionnez UserPrincipalName**).

1. Afficher un écran à la fois (**Plus**).
    
Pour afficher le nom d’utilisateur principal d’un compte en fonction de son nom complet (prénom et nom), exécutez les commandes suivantes. Remplissez la *$userName* variable et supprimez les \< and > caractères :
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple affiche le nom d’utilisateur principal du compte d’utilisateur dont le nom complet *est Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En utilisant une variable *$upn*, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple qui définit l’emplacement d’utilisation de *Belinda Newman* en France. Mais il spécifie son nom d’affichage plutôt que son nom d’utilisateur principal :
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Modification des propriétés de tous les comptes d’utilisateur

Pour modifier les propriétés de tous les utilisateurs, vous pouvez utiliser une combinaison des cmdlets **Get-AzureADUser** et **Set-AzureADUser.** L’exemple suivant modifie l’emplacement d’utilisation de tous les utilisateurs en *France*:
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Cette commande indique à PowerShell de :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**) et envoyez-les à la commande suivante ( **|** ).
    
1. Définissez l’emplacement utilisateur sur France (**Set-AzureADUser -UsageLocation « FR »**).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur

Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateurs, vous pouvez utiliser une combinaison des cmdlets **Get-AzureADUser**, **Where** et **Set-AzureADUser.** L’exemple suivant modifie l’emplacement d’utilisation de tous les utilisateurs du service Comptabilité en *France*:
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Cette commande indique à PowerShell de :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**), et envoyez-les à la commande suivante ( **|** ).
    
1.  Recherchez tous les comptes d’utilisateur dont la propriété *Department* est définie sur « Accounting » (**Où {$_. Department -eq « Accounting"}**), et envoyer les informations résultantes à la commande suivante ( **|** ).
    
1. Définissez l’emplacement utilisateur sur France (**Set-AzureADUser -UsageLocation « FR »**).
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Pour configurer les propriétés des comptes d’utilisateur avec le module Microsoft Azure Active Directory pour Windows PowerShell, utilisez l’cmdlet **Set-MsolUser** et spécifiez les propriétés à définir ou modifier.

Tout [d’abord, connectez-vous à votre client Microsoft 365.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)
  
>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour le module Windows PowerShell et les cmdlets incluant *Msol* dans leur nom. Exécutez ces cmdlets à partir de Windows PowerShell.
>

### <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d’un compte d’utilisateur spécifique

Pour configurer les propriétés d’un compte d’utilisateur spécifique, utilisez l’cmdlet [**Set-MsolUser**](/previous-versions/azure/dn194136(v=azure.100)) et spécifiez les propriétés à définir ou à modifier. 

Vous identifiez le compte avec le paramètre *-UserPrincipalName* et définissez ou modifiez des propriétés spécifiques à l’aide de paramètres supplémentaires. Voici la liste des paramètres les plus courants.
  
- -City "\<city name>"
    
- -Country "\<country name>"
    
- -Department "\<department name>"
    
- -DisplayName "\<full user name>"
    
- -Fax "<numéro de fax>"
    
- -FirstName "<prénom de l'utilisateur>"
    
- -LastName "<nom de famille de l'utilisateur>"
    
- -MobilePhone "<numéro de téléphone portable>"
    
- -Office "\<office location>"
    
- -PhoneNumber "<numéro de téléphone du bureau>"
    
- -PostalCode "\<postal code>
    
- -PreferredLanguage "\<language>"
    
- -State "<nom de l'État>"
    
- -StreetAddress "\<street address>"
    
- -Title "<intitulé du poste>"
    
- -UsageLocation \<2-character country or region code> »
    
    Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).
    
Pour d’autres paramètres, [voir Set-MsolUser](/previous-versions/azure/dn194136(v=azure.100)).

Pour voir les noms d’utilisateur principaux de tous vos utilisateurs, exécutez la commande suivante :
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Cette commande indique à PowerShell de :
  
1. Obtenez toutes les informations pour les comptes d’utilisateur (**Get-MsolUser**) et envoyez-les à la commande suivante ( **|** ).
    
1. Trier la liste des noms d’utilisateur principaux par ordre alphabétique (**Trier UserPrincipalName**) et l’envoyer à la commande suivante ( **|** ).
    
1. Afficher uniquement la propriété Nom d’utilisateur principal pour chaque compte (**Sélectionnez UserPrincipalName**).
    
1. Afficher un écran à la fois (**Plus**).
    
Pour afficher le nom d’utilisateur principal d’un compte en fonction de son nom complet (prénom et nom), exécutez les commandes suivantes. Remplissez la *$userName* variable et supprimez les \< and > caractères.
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple montre comment afficher le nom d’utilisateur principal de l’utilisateur nommé Caleb Sills :
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En utilisant une variable *$upn*, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple qui définit l’emplacement d’utilisation de *Belinda Newman* en *France,* mais spécifie son nom d’affichage plutôt que son nom d’utilisateur principal :
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Modification des propriétés de tous les comptes d’utilisateur

Pour modifier les propriétés de tous les utilisateurs, utilisez une combinaison des cmdlets **Get-MsolUser** et **Set-MsolUser.** L’exemple suivant modifie l’emplacement d’utilisation de tous les utilisateurs en *France*:
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Cette commande indique à PowerShell de :
  
1. Obtenez toutes les informations des comptes d’utilisateur (**Get-MsolUser**) et envoyez-les à la commande suivante ( **|** ).
    
1. Définissez l’emplacement utilisateur sur France (**Set-MsolUser -UsageLocation « FR »**).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur

Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateurs, vous pouvez utiliser une combinaison des cmdlets **Get-MsolUser**, **Where** et **Set-MsolUser.** L’exemple suivant modifie l’emplacement d’utilisation de tous les utilisateurs du service Comptabilité en *France*:
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Cette commande indique à PowerShell de :
  
1. Obtenez toutes les informations des comptes d’utilisateur (**Get-MsolUser**) et envoyez-les à la commande suivante ( **|** ).
    
1. Recherchez tous les comptes d’utilisateur dont la propriété *Department* est définie sur « Accounting » (**Where {$_. Department -eq « Accounting"}**) et envoyer les informations résultantes à la commande suivante ( **|** ).
    
1. Définissez l’emplacement utilisateur sur France (**Set-MsolUser -UsageLocation « FR »**).

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)