---
title: Afficher Microsoft 365 comptes d’utilisateurs avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: Découvrez comment afficher, lister ou afficher Microsoft 365 comptes d’utilisateur de différentes manières avec PowerShell.
ms.openlocfilehash: 77219fb89430ed257ef2a68a7b24bf9ebac715b2
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2021
ms.locfileid: "53290170"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>Afficher Microsoft 365 comptes d’utilisateurs avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez utiliser le Centre d’administration Microsoft 365 pour afficher les comptes de votre client Microsoft 365 client. PowerShell pour Microsoft 365 active cette fonctionnalité, mais fournit également des fonctionnalités supplémentaires.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  
### <a name="view-all-accounts"></a>Afficher tous les comptes

Pour afficher la liste complète des comptes d’utilisateurs, exécutez la commande ci-dessous :
  
```powershell
Get-AzureADUser
```

Vous devez obtenir des informations semblables à ceci :
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>Afficher un compte spécifique

Pour afficher un compte d’utilisateur spécifique, exécutez la commande suivante. Remplissez le nom du compte de signature du compte d’utilisateur, également appelé nom d’utilisateur principal (UPN). Supprimez les caractères « < » et « > » .
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Voici un exemple :
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Afficher des valeurs de propriété supplémentaires pour un compte spécifique

Par défaut, la cmdlet **Get-AzureADUser** affiche uniquement les propriétés *ObjectID,* *DisplayName* et *UserPrincipalName* des comptes.

Pour être plus sélectif sur les propriétés à afficher, utilisez l’cmdlet **Select** en combinaison avec l’cmdlet **Get-AzureADUser.** Pour combiner les deux cmdlets, utilisez le caractère « pipe » (« | ») qui indique à Azure Active Directory PowerShell pour Graph de prendre les résultats d’une commande et de l’envoyer à la commande suivante. Voici un exemple de commande qui affiche *displayName,* *Department* et *UsageLocation* pour chaque compte d’utilisateur :
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

Cette commande indique à PowerShell de :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**) et envoyez-les à la commande suivante ( **|** ).
    
1.  Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation (**Sélectionnez DisplayName, Service, UsageLocation**).
  
Pour voir toutes les propriétés d’un compte d’utilisateur spécifique, utilisez la cmdlet **Select** et le caractère générique (*). Voici un exemple :
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Dans un autre exemple, exécutez la commande suivante pour vérifier l’état activé d’un compte d’utilisateur spécifique :
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-account-synchronization-status"></a>Afficher l’état de synchronisation des comptes

Les comptes d’utilisateurs ont deux sources : 

- Windows Server Active Directory (AD), qui sont des comptes qui se synchronisent d’AD local vers le cloud.

- Azure Active Directory (Azure AD) AD, qui sont créés directement dans le cloud.


La commande suivante indique à PowerShell d’obtenir tous les utilisateurs dont l’attribut *DirSyncEnabled* a la valeur *True*. Vous pouvez l’utiliser pour rechercher des comptes qui se synchronisent à partir d’AD local.

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -eq $true}
```

La commande suivante indique à PowerShell d’obtenir tous les utilisateurs dont l’attribut *DirSyncEnabled* a la valeur *False*. Vous pouvez l’utiliser pour rechercher des comptes cloud uniquement.

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -ne $false}
```

### <a name="view-accounts-based-on-a-common-property"></a>Afficher les comptes en fonction d’une propriété commune

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez utiliser l’cmdlet **Where** en combinaison avec l’cmdlet **Get-AzureADUser.** Pour combiner les deux cmdlets, utilisez le caractère « pipe » (« | ») qui indique à Azure Active Directory PowerShell pour Graph de prendre les résultats d’une commande et de l’envoyer à la commande suivante. Voici un exemple de commande qui affiche uniquement les comptes d’utilisateurs dont l’emplacement d’utilisation n’est pas spécifié :
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

Cette commande indique Azure Active Directory PowerShell pour Graph :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**) et envoyez-les à la commande suivante ( **|** ).
    
1. Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié (**Où {$ \_ . UsageLocation -eq $Null}**). À l’intérieur des accolades, la commande indique à PowerShell de rechercher uniquement l’ensemble de comptes pour lesquels la propriété de compte d’utilisateur UsageLocation (**$ \_ . UsageLocation**) n’est pas spécifié (**-eq $Null**).
    
La propriété **UsageLocation** n’est que l’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés d’un compte d’utilisateur spécifique, utilisez la cmdlet **Select** et le caractère générique (*). Voici un exemple :
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Par exemple, **Ville** est le nom d’une propriété de compte d’utilisateur. Vous pouvez utiliser la commande suivante pour lister tous les comptes d’utilisateurs qui habitent à Londres :
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
> La syntaxe de **l’cmdlet Where** dans ces exemples est **Where {$ \_ .** [nom de la propriété du compte d’utilisateur] [opérateur de comparaison] [valeur] **}**.> [opérateur de comparaison] est **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] est généralement une chaîne (une séquence de lettres, de nombres et d’autres caractères), une valeur numérique ou **une $Null** pour non spécifié. Pour plus d’informations, voir [Where](/powershell/module/microsoft.powershell.core/where-object).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

### <a name="view-all-accounts"></a>Afficher tous les comptes

Pour afficher la liste complète des comptes d’utilisateurs, exécutez la commande ci-dessous :
  
```powershell
Get-MsolUser
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour le module Windows PowerShell et les cmdlets incluant *Msol* dans leur nom. Exécutez ces cmdlets à partir de Windows PowerShell.
>

Vous devez obtenir des informations semblables à ceci :
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

La cmdlet **Get-MsolUser** dispose également d’un jeu de paramètres pour filtrer l’ensemble de comptes utilisateur affichés. Par exemple, pour obtenir la liste des utilisateurs sans licence (utilisateurs qui ont été ajoutés à Microsoft 365 mais qui n’ont pas encore reçu de licence pour utiliser les services), exécutez la commande ci-dessous :
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

Vous devez obtenir des informations semblables à ceci :
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Pour plus d’informations sur les paramètres supplémentaires pour filtrer l’ensemble des comptes d’utilisateur qui sont affichés, voir [Get-MsolUser](/previous-versions/azure/dn194133(v=azure.100)).
  
### <a name="view-a-specific-account"></a>Afficher un compte spécifique

Pour afficher un compte d’utilisateur spécifique, exécutez la commande suivante. Remplissez le nom de la signature du compte d’utilisateur, également appelé nom d’utilisateur principal (UPN). Supprimez les caractères « < » et « > » .
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-accounts-based-on-a-common-property"></a>Afficher les comptes en fonction d’une propriété commune

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez utiliser l’cmdlet **Where** en combinaison avec l’cmdlet **Get-MsolUser.** Pour combiner les deux cmdlets, utilisez le caractère « pipe » (« | ») qui indique à PowerShell de prendre les résultats d’une commande et de l’envoyer à la commande suivante. Voici un exemple qui affiche uniquement les comptes d’utilisateurs dont l’emplacement d’utilisation n’est pas spécifié :
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

Cette commande indique à PowerShell de :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-MsolUser**) et envoyez-les à la commande suivante ( **|** ).
    
1. Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié (**Où {$ \_ . UsageLocation -eq $Null}**). À l’intérieur des accolades, la commande indique à PowerShell de rechercher uniquement l’ensemble de comptes pour lesquels la propriété de compte d’utilisateur UsageLocation (**$ \_ . UsageLocation**) n’est pas spécifié (**-eq $Null**).
    
Vous devez obtenir des informations semblables à ceci :
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

La propriété *UsageLocation* n’est que l’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez la cmdlet **Select** et le caractère générique (*) pour afficher toutes les propriétés d’un compte d’utilisateur spécifique. Voici un exemple :
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Par exemple, *Ville* est le nom d’une propriété de compte d’utilisateur. Vous pouvez utiliser la commande suivante pour lister tous les comptes d’utilisateur pour les utilisateurs qui habitent à Londres :
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
> La syntaxe de **l’cmdlet Where** dans ces exemples est **Where {$ \_ .** [nom de la propriété du compte d’utilisateur] [opérateur de comparaison] [valeur] **}**.  [opérateur de comparaison] est **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] est généralement une chaîne (une séquence de lettres, de nombres et d’autres caractères), une valeur numérique ou **une $Null** pour non spécifié. Pour plus d’informations, voir [Where](/powershell/module/microsoft.powershell.core/where-object).
  
Pour vérifier l’état bloqué d’un compte d’utilisateur, utilisez la commande suivante :
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Afficher des valeurs de propriété supplémentaires pour les comptes

Par défaut, la cmdlet **Get-MsolUser** affiche les trois propriétés des comptes d’utilisateurs :
  
- UserPrincipalName

- DisplayName

- isLicensed

Si vous avez besoin de propriétés supplémentaires, telles que le service où travaille l’utilisateur et le pays/la région où il utilise les services Microsoft 365, vous pouvez exécuter **Get-MsolUser** en combinaison avec la cmdlet **Select** pour spécifier la liste des propriétés du compte d’utilisateur. Voici un exemple :
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

Cette commande indique à PowerShell de :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-MsolUser**) et envoyez-les à la commande suivante ( **|** ).
    
1. Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation (**Sélectionnez DisplayName, Service, UsageLocation**).
    
Vous devez obtenir des informations semblables à ceci :
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

L’cmdlet Select vous permet de choisir les propriétés à afficher.  Pour afficher toutes les propriétés d’un compte d’utilisateur spécifique, utilisez le caractère générique (*). Voici un exemple :
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez également utiliser la cmdlet **Where.** Voici un exemple de commande qui affiche uniquement les comptes d’utilisateurs dont l’emplacement d’utilisation n’est pas spécifié :
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

Cette commande indique à PowerShell de :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-MsolUser**) et envoyez-les à la commande suivante ( **|** ).
    
1. Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié (**Où {$ \_ . UsageLocation -eq $Null}**), et envoyer les informations résultantes à la commande suivante ( **|** ). À l’intérieur des accolades, la commande indique à PowerShell de rechercher uniquement l’ensemble de comptes pour lesquels la propriété de compte d’utilisateur UsageLocation (**$ \_ . UsageLocation**) n’est pas spécifié (**-eq $Null**).
    
1. Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation (**Sélectionnez DisplayName, Service, UsageLocation**).
    
Vous devez obtenir des informations semblables à ceci :
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Si vous utilisez la synchronisation d’annuaires pour créer et gérer vos utilisateurs Microsoft 365, vous pouvez afficher le compte local à partir duquel un utilisateur Microsoft 365 été projeté. L’exemple suivant suppose que :

- Azure AD Connecter est configuré pour utiliser l’ancrage source par défaut d’ObjectGUID. (Pour plus d’informations sur la configuration d’une ancre source, voir [Azure AD Connecter: Design concepts](/azure/active-directory/hybrid/plan-connect-design-concepts)).
- Le module Services de domaine Active Directory pour PowerShell a été installé (voir [outils RSAT).](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)