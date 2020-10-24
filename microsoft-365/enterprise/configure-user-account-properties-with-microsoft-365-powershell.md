---
title: Configuration des propriétés de compte d’utilisateur Microsoft 365 avec PowerShell
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
description: Utilisez PowerShell pour Microsoft 365 pour configurer les propriétés d’un ou de plusieurs comptes d’utilisateur dans votre client Microsoft 365.
ms.openlocfilehash: 830cede93a6c14db2dcc5626d41d0dd296b9ac29
ms.sourcegitcommit: 66b8fc1d8ba4f17487cd2004ac19cf2fff472f3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "48754327"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>Configuration des propriétés de compte d’utilisateur Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez utiliser le centre d’administration Microsoft 365 pour configurer les propriétés des comptes d’utilisateurs de votre client Microsoft 365. Dans PowerShell, vous pouvez également effectuer cette opération, ainsi que d’autres actions que vous ne pouvez pas effectuer dans le centre d’administration.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Pour configurer les propriétés des comptes d’utilisateur dans le module Azure Active Directory PowerShell pour Graph, utilisez l’applet de commande [**Set-AzureADUser**](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) et spécifiez les propriétés à définir ou à modifier.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
   
### <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d’un compte d’utilisateur spécifique

Vous identifiez le compte avec le paramètre *-ObjectID* et définissez ou modifiez des propriétés spécifiques à l’aide de paramètres supplémentaires. Voici une liste des paramètres les plus courants :
  
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
    
- -UsageLocation " \<2-character country or region code> "
    
    Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).
    
Pour d’autres paramètres, voir [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) .

>[!Note]
>Avant de pouvoir attribuer des licences à un compte d’utilisateur, vous devez affecter un emplacement d’utilisation.
>

Pour afficher le nom d’utilisateur principal pour vos comptes d’utilisateur, exécutez la commande suivante.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Cette commande demande à PowerShell de :
  
1. Obtenir toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**) et les envoyer à la commande suivante ( **|** ).
    
1. Trier par ordre alphabétique la liste des noms d’utilisateur principaux (**sort userPrincipalName**) et l’envoyer à la commande suivante ( **|** ).
    
1. Afficher uniquement la propriété nom d’utilisateur principal pour chaque compte (**Sélectionnez userPrincipalName**).

1. Afficher un écran à la fois (**Plus**).
    
Pour afficher le nom d’utilisateur principal d’un compte en fonction de son nom d’affichage (prénom et nom), exécutez les commandes suivantes. Renseignez la variable *$username* et supprimez les \< and > caractères suivants :
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple montre comment afficher le nom d’utilisateur principal du compte d’utilisateur dont le nom complet est *Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En utilisant une variable *$upn*, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple qui définit l’emplacement d’utilisation de *Belinda Newman*sur France. Mais il spécifie son nom d’affichage au lieu de son nom d’utilisateur principal :
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Modification des propriétés de tous les comptes d’utilisateur

Pour modifier les propriétés de tous les utilisateurs, vous pouvez utiliser une combinaison des cmdlets **Get-AzureADUser** et **Set-AzureADUser** . L’exemple suivant montre comment modifier l’emplacement d’utilisation de tous les utilisateurs en *France*:
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Cette commande demande à PowerShell de :
  
1. Obtenir toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**) et les envoyer à la commande suivante ( **|** ).
    
1. Définissez la France comme emplacement de l’utilisateur (**Set-AzureADUser-UsageLocation "fr"**).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur

Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateur, vous pouvez utiliser une combinaison des cmdlets **Get-AzureADUser**, **Where**et **Set-AzureADUser** . L’exemple suivant montre comment modifier l’emplacement d’utilisation de tous les utilisateurs du service de comptabilité en *France*:
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Cette commande demande à PowerShell de :
  
1. Obtenir toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**) et les envoyer à la commande suivante ( **|** ).
    
1.  Recherchez tous les comptes d’utilisateur dont la propriété *Department* est définie sur « Accounting » (**where {$ _. Department-EQ "Accounting"}**) et envoyer les informations obtenues à la commande suivante ( **|** ).
    
1. Définissez la France comme emplacement de l’utilisateur (**Set-AzureADUser-UsageLocation "fr"**).
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Pour configurer les propriétés des comptes d’utilisateur avec le module Microsoft Azure Active Directory pour Windows PowerShell, utilisez la cmdlet **Set-MsolUser** et spécifiez les propriétés à définir ou à modifier.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
>[!Note]
>PowerShell Core ne prend pas en charge les applets de commande et le module Microsoft Azure Active Directory pour Windows PowerShell avec *MSOL* dans leur nom. Exécutez ces applets de commande à partir de Windows PowerShell.
>

### <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d’un compte d’utilisateur spécifique

Pour configurer les propriétés d’un compte d’utilisateur spécifique, utilisez la cmdlet [**Set-MsolUser**](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) et spécifiez les propriétés à définir ou à modifier. 

Vous identifiez le compte à l’aide du paramètre *-userPrincipalName* et définissez ou modifiez des propriétés spécifiques en utilisant des paramètres supplémentaires. Voici une liste des paramètres les plus courants.
  
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
    
- -UsageLocation " \<2-character country or region code> "
    
    Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).
    
Pour d’autres paramètres, voir [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)).

Pour afficher les noms d’utilisateur principaux de tous vos utilisateurs, exécutez la commande suivante :
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Cette commande demande à PowerShell de :
  
1. Obtenir toutes les informations pour les comptes d’utilisateur (**Get-MsolUser**) et les envoyer à la commande suivante ( **|** ).
    
1. Trier par ordre alphabétique la liste des noms d’utilisateur principaux (**sort userPrincipalName**) et l’envoyer à la commande suivante ( **|** ).
    
1. Afficher uniquement la propriété nom d’utilisateur principal pour chaque compte (**Sélectionnez userPrincipalName**).
    
1. Afficher un écran à la fois (**Plus**).
    
Pour afficher le nom d’utilisateur principal d’un compte en fonction de son nom d’affichage (prénom et nom), exécutez les commandes suivantes. Renseignez la variable *$username* et supprimez les \< and > caractères.
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple montre comment afficher le nom d’utilisateur principal de l’utilisateur nommé Caleb Sills :
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En utilisant une variable *$upn*, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple qui définit l’emplacement d’utilisation de *Belinda Newman*sur *France*, mais spécifie son nom d’affichage au lieu de son nom d’utilisateur principal :
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Modification des propriétés de tous les comptes d’utilisateur

Pour modifier les propriétés de tous les utilisateurs, utilisez une combinaison des cmdlets **Get-MsolUser** et **Set-MsolUser** . L’exemple suivant montre comment modifier l’emplacement d’utilisation de tous les utilisateurs en *France*:
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Cette commande demande à PowerShell de :
  
1. Obtenir toutes les informations pour les comptes d’utilisateur (**Get-MsolUser**) et les envoyer à la commande suivante ( **|** ).
    
1. Définissez la France comme emplacement de l’utilisateur (**Set-MsolUser-UsageLocation "fr"**).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur

Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateur, vous pouvez utiliser une combinaison des cmdlets **Get-MsolUser**, **Where**et **Set-MsolUser** . L’exemple suivant montre comment modifier l’emplacement d’utilisation de tous les utilisateurs du service de comptabilité en *France*:
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Cette commande demande à PowerShell de :
  
1. Obtenir toutes les informations pour les comptes d’utilisateur (**Get-MsolUser**) et les envoyer à la commande suivante ( **|** ).
    
1. Recherchez tous les comptes d’utilisateur dont la propriété *Department* est définie sur « Accounting » (**where {$ _. Department-EQ "Accounting"}**) et envoyer les informations obtenues à la commande suivante ( **|** ).
    
1. Définissez la France comme emplacement de l’utilisateur (**Set-MsolUser-UsageLocation "fr"**).

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
