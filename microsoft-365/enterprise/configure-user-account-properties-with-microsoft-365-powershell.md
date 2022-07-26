---
title: Configurer les propriétés du compte d’utilisateur Microsoft 365 avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- admindeeplinkMAC
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: Utilisez PowerShell pour Microsoft 365 pour configurer les propriétés de comptes d’utilisateur individuels ou multiples dans votre locataire Microsoft 365.
ms.openlocfilehash: 14d302bca030b8310c4956c44cccab91d357233f
ms.sourcegitcommit: 6e570b79944862c86735db455349b685d5b903b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2022
ms.locfileid: "67019942"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>Configurer les propriétés du compte d’utilisateur Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez utiliser la <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> pour configurer les propriétés des comptes d’utilisateur de votre locataire Microsoft 365. Dans PowerShell, vous pouvez également effectuer cette opération, ainsi que d’autres choses que vous ne pouvez pas faire dans le Centre d’administration.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Pour configurer les propriétés des comptes d’utilisateur dans le module Azure Active Directory PowerShell pour Graph, utilisez l’applet de commande [**Set-AzureADUser**](/powershell/module/azuread/set-azureaduser) et spécifiez les propriétés à définir ou à modifier.

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d’un compte d’utilisateur spécifique

Vous identifiez le compte avec le paramètre *-ObjectID* et définissez ou modifiez des propriétés spécifiques à l’aide de paramètres supplémentaires. Voici la liste des paramètres les plus courants :
  
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

- -UsageLocation « \<2-character country or region code> »

    Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).

Pour obtenir des paramètres supplémentaires, consultez [Set-AzureADUser](/powershell/module/azuread/set-azureaduser).

> [!NOTE]
> Avant de pouvoir attribuer des licences à un compte d’utilisateur, vous devez attribuer un emplacement d’utilisation.

Pour afficher le nom d’utilisateur principal pour vos comptes d’utilisateur, exécutez la commande suivante.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Cette commande indique à PowerShell d’effectuer les opérations suivantes :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser) et envoyez-les** à la commande suivante (**|**).

1. Triez la liste des noms d’utilisateurs principaux par ordre alphabétique (**Sort UserPrincipalName**) et envoyez-la à la commande suivante (**|**).

1. Affichez uniquement la propriété Nom d’utilisateur principal pour chaque compte (**sélectionnez UserPrincipalName**).

1. Afficher un écran à la fois (**Plus**).

Pour afficher le nom d’utilisateur principal d’un compte en fonction de son nom d’affichage (prénom et nom), exécutez les commandes suivantes. Renseignez la variable *$userName* et supprimez les \< and > caractères :
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple montre comment afficher le nom d’utilisateur principal du compte d’utilisateur qui porte le nom d’affichage *Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En utilisant une variable *$upn*, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple qui définit l’emplacement d’utilisation de *Beayez Newman* sur la France. Mais il spécifie son nom d’affichage plutôt que son nom d’utilisateur principal :
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation FR
```

### <a name="change-properties-for-all-user-accounts"></a>Modification des propriétés de tous les comptes d’utilisateur

Pour modifier les propriétés de tous les utilisateurs, vous pouvez utiliser une combinaison des applets de commande **Get-AzureADUser** et **Set-AzureADUser** . L’exemple suivant modifie l’emplacement d’utilisation de tous les utilisateurs en *France* :
  
```powershell
Get-AzureADUser -All $true | Set-AzureADUser -UsageLocation FR
```

Cette commande indique à PowerShell d’effectuer les opérations suivantes :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser) et envoyez-les** à la commande suivante (**|**).

1. Définissez l’emplacement de l’utilisateur sur France (**Set-AzureADUser -UsageLocation FR**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur

Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateur, vous pouvez utiliser une combinaison des applets de commande **Get-AzureADUser**, **Where** et **Set-AzureADUser** . L’exemple suivant modifie l’emplacement d’utilisation de tous les utilisateurs du service Comptabilité en *France* :
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation FR
```

Cette commande indique à PowerShell d’effectuer les opérations suivantes :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser) et envoyez-les** à la commande suivante (**|**).

1.  Recherchez tous les comptes d’utilisateur dont la propriété *Department* est définie sur « Accounting » (**Où {$_. Department -eq « Accounting"}**), et envoyer les informations obtenues à la commande suivante (**|**).

1. Définissez l’emplacement de l’utilisateur sur France (**Set-AzureADUser -UsageLocation FR**).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Pour configurer les propriétés des comptes d’utilisateur avec le module Microsoft Azure Active Directory pour Windows PowerShell, utilisez l’applet de commande **Set-MsolUser** et spécifiez les propriétés à définir ou à modifier.

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
> [!NOTE]
> PowerShell Core ne prend pas en charge le Module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande avec *Msol* dans leur nom. Exécutez ces applets de commande à partir de Windows PowerShell.

### <a name="change-properties-for-a-specific-user-account"></a>Modification des propriétés d’un compte d’utilisateur spécifique

Pour configurer les propriétés d’un compte d’utilisateur spécifique, utilisez l’applet de commande [**Set-MsolUser**](/previous-versions/azure/dn194136(v=azure.100)) et spécifiez les propriétés à définir ou à modifier. 

Vous identifiez le compte avec le paramètre *-UserPrincipalName* et définissez ou modifiez des propriétés spécifiques à l’aide de paramètres supplémentaires. Voici une liste des paramètres les plus courants.
  
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

- -UsageLocation « \<2-character country or region code> »

    Voici le code de la région ou du pays à deux lettres ISO 3166-1 alpha-2 (A2).

Pour obtenir des paramètres supplémentaires, consultez [Set-MsolUser](/previous-versions/azure/dn194136(v=azure.100)).

Pour afficher les noms d’utilisateur principal de tous vos utilisateurs, exécutez la commande suivante :
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Cette commande indique à PowerShell d’effectuer les opérations suivantes :
  
1. Obtenez toutes les informations pour les comptes d’utilisateur (**Get-MsolUser) et envoyez-les** à la commande suivante (**|**).

1. Triez la liste des noms d’utilisateurs principaux par ordre alphabétique (**Sort UserPrincipalName**) et envoyez-la à la commande suivante (**|**).

1. Affichez uniquement la propriété Nom d’utilisateur principal pour chaque compte (**sélectionnez UserPrincipalName**).

1. Afficher un écran à la fois (**Plus**).

Pour afficher le nom d’utilisateur principal d’un compte en fonction de son nom d’affichage (prénom et nom), exécutez les commandes suivantes. Renseignez la variable *$userName* et supprimez les \< and > caractères.
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Cet exemple montre comment afficher le nom d’utilisateur principal de l’utilisateur nommé Caleb Sills :
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En utilisant une variable *$upn*, vous pouvez apporter des modifications à des comptes individuels en fonction de leur nom d'affichage. Voici un exemple qui définit l’emplacement d’utilisation de *Beayez Newman* sur *la France*, mais spécifie son nom d’affichage plutôt que son nom d’utilisateur principal :
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation FR
```

### <a name="change-properties-for-all-user-accounts"></a>Modification des propriétés de tous les comptes d’utilisateur

Pour modifier les propriétés de tous les utilisateurs, utilisez une combinaison des applets de commande **Get-MsolUser** et **Set-MsolUser** . L’exemple suivant modifie l’emplacement d’utilisation de tous les utilisateurs en *France* :
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation FR
```

Cette commande indique à PowerShell d’effectuer les opérations suivantes :
  
1. Obtenez toutes les informations pour les comptes d’utilisateur (**Get-MsolUser) et envoyez-les** à la commande suivante (**|**).

1. Définissez l’emplacement de l’utilisateur sur France (**Set-MsolUser -UsageLocation FR**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Modification des propriétés d’un ensemble spécifique de comptes d’utilisateur

Pour modifier les propriétés d’un ensemble spécifique de comptes d’utilisateur, vous pouvez utiliser une combinaison des applets de commande **Get-MsolUser**, **Where** et **Set-MsolUser** . L’exemple suivant modifie l’emplacement d’utilisation de tous les utilisateurs du service Comptabilité en *France* :
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation FR
```

Cette commande indique à PowerShell d’effectuer les opérations suivantes :
  
1. Obtenez toutes les informations pour les comptes d’utilisateur (**Get-MsolUser) et envoyez-les** à la commande suivante (**|**).

1. Recherchez tous les comptes d’utilisateur dont la propriété *Department* est définie sur « Accounting » (**Où {$_. Department -eq « Accounting"}**) et envoyer les informations obtenues à la commande suivante (**|**).

1. Définissez l’emplacement de l’utilisateur sur France (**Set-MsolUser -UsageLocation FR**).

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
