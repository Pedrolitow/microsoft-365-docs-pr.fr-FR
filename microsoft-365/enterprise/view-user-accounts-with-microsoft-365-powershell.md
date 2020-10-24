---
title: Afficher les comptes d’utilisateur Microsoft 365 avec PowerShell
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
description: Découvrez comment afficher, répertorier ou afficher vos comptes d’utilisateur Microsoft 365 de différentes manières avec PowerShell.
ms.openlocfilehash: 312e9fb983c4d1f4de8bc74586c88f1e669eb90a
ms.sourcegitcommit: 66b8fc1d8ba4f17487cd2004ac19cf2fff472f3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "48754071"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>Afficher les comptes d’utilisateur Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez utiliser le centre d’administration Microsoft 365 pour afficher les comptes de votre client Microsoft 365. PowerShell pour Microsoft 365 active cela, mais fournit également des fonctionnalités supplémentaires.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Afficher tous les comptes

Pour afficher la liste complète des comptes d’utilisateurs, exécutez la commande suivante :
  
```powershell
Get-AzureADUser
```

Vous devriez obtenir des informations semblables à celles-ci :
  
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

Pour afficher un compte d’utilisateur spécifique, exécutez la commande suivante. Renseignez le nom de compte de connexion du compte d’utilisateur, également appelé nom d’utilisateur principal (UPN). Supprimez les caractères « < » et « > ».
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Voici un exemple :
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Afficher des valeurs de propriétés supplémentaires pour un compte spécifique

Par défaut, la cmdlet **Get-AzureADUser** affiche uniquement les propriétés *ObjectID*, *DisplayName*et *userPrincipalName* des comptes.

Pour être plus sélectif quant aux propriétés à afficher, utilisez l’applet de commande **Select** en combinaison avec la cmdlet **Get-AzureADUser** . Pour combiner les deux cmdlets, utilisez le caractère « pipe » (« | »), qui indique à Azure Active Directory PowerShell pour Graph de prendre les résultats d’une commande et de l’envoyer à la commande suivante. Voici un exemple de commande qui affiche les *DisplayName*, *Department*et *UsageLocation* pour chaque compte d’utilisateur :
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

Cette commande demande à PowerShell de :
  
1. Obtenir toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**) et les envoyer à la commande suivante ( **|** ).
    
1.  Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation (**Sélectionnez DisplayName, Department, UsageLocation**).
  
Pour afficher toutes les propriétés d’un compte d’utilisateur spécifique, utilisez l’applet de commande **Select** et le caractère générique (*). Voici un exemple :
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

En guise d’exemple supplémentaire, exécutez la commande suivante pour vérifier l’état activé d’un compte d’utilisateur spécifique :
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-account-synchronization-status"></a>Afficher l’état de la synchronisation des comptes

Les comptes d’utilisateur ont deux sources : 

- Windows Server Active Directory (AD), qui sont des comptes synchronisés à partir d’AD sur site vers le Cloud.

- Les comptes AD Azure Active Directory (Azure AD), qui sont créés directement dans le Cloud.


La commande suivante indique à PowerShell d’obtenir tous les utilisateurs dont l’attribut *DirSyncEnabled* est défini sur *true*. Vous pouvez l’utiliser pour rechercher les comptes qui sont synchronisés à partir d’AD sur site.

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -eq $true}
```

La commande suivante indique à PowerShell d’obtenir tous les utilisateurs dont l’attribut *DirSyncEnabled* est défini sur *false*. Vous pouvez l’utiliser pour rechercher des comptes en nuage uniquement.

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -ne $false}
```

### <a name="view-accounts-based-on-a-common-property"></a>Afficher les comptes en fonction d’une propriété commune

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez utiliser la cmdlet **Where** en combinaison avec la cmdlet **Get-AzureADUser** . Pour combiner les deux cmdlets, utilisez le caractère « pipe » (« | »), qui indique à Azure Active Directory PowerShell pour Graph de prendre les résultats d’une commande et de l’envoyer à la commande suivante. Voici un exemple de commande qui affiche uniquement les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié :
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

Cette commande demande à Azure Active Directory PowerShell pour Graph d’effectuer les opérations suivantes :
  
1. Obtenir toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser**) et les envoyer à la commande suivante ( **|** ).
    
1. Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié (**où {$ \_ . UsageLocation-EQ $Null}**). À l’intérieur des accolades, la commande demande à PowerShell de trouver uniquement l’ensemble des comptes pour lesquels la propriété de compte d’utilisateur UsageLocation (** $ \_ . UsageLocation**) n’est pas spécifié (**-EQ $null**).
    
La propriété **UsageLocation** n’est que l’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés d’un compte d’utilisateur spécifique, utilisez l’applet de commande **Select** et le caractère générique (*). Voici un exemple :
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Par exemple, **Ville** est le nom d’une propriété de compte d’utilisateur. Vous pouvez utiliser la commande suivante pour répertorier tous les comptes d’utilisateurs vivant à Londres :
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  La syntaxe de la cmdlet **Where** de ces exemples est **where {$ \_ .** [nom de la propriété du compte d’utilisateur] [opérateur de comparaison] valeur **}**. > [opérateur de comparaison] est **-EQ** pour Equals, **-** ne pour « différent de », **-lt** pour inférieur à, **-gt** pour supérieur à, et autres.  [valeur] est généralement une chaîne (une séquence de lettres, de chiffres et d’autres caractères), une valeur numérique ou **$null** pour non spécifié. Pour plus d’informations, voir [Where](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-7).
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Afficher tous les comptes

Pour afficher la liste complète des comptes d’utilisateurs, exécutez la commande suivante :
  
```powershell
Get-MsolUser
```

>[!Note]
>PowerShell Core ne prend pas en charge les applets de commande et le module Microsoft Azure Active Directory pour Windows PowerShell avec *MSOL* dans leur nom. Exécutez ces applets de commande à partir de Windows PowerShell.
>

Vous devriez obtenir des informations semblables à celles-ci :
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

La cmdlet **Get-MsolUser** dispose également d’un jeu de paramètres pour filtrer l’ensemble de comptes utilisateur affichés. Par exemple, pour la liste des utilisateurs sans licence (utilisateurs qui ont été ajoutés à Microsoft 365 mais qui n’ont pas encore été concédés sous licence pour utiliser l’un des services), exécutez la commande suivante :
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

Vous devriez obtenir des informations semblables à celles-ci :
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Pour plus d’informations sur les paramètres supplémentaires permettant de filtrer l’ensemble des comptes d’utilisateur affichés, consultez la rubrique [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).
  
### <a name="view-a-specific-account"></a>Afficher un compte spécifique

Pour afficher un compte d’utilisateur spécifique, exécutez la commande suivante. Renseignez le nom de connexion du compte d’utilisateur, également appelé nom d’utilisateur principal (UPN). Supprimez les caractères « < » et « > ».
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-accounts-based-on-a-common-property"></a>Afficher les comptes en fonction d’une propriété commune

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez utiliser la cmdlet **Where** en combinaison avec la cmdlet **Get-MsolUser** . Pour combiner les deux cmdlets, utilisez le caractère « pipe » (« | »), qui indique à PowerShell de prendre les résultats d’une commande et de l’envoyer à la commande suivante. Voici un exemple qui affiche uniquement les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié :
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

Cette commande demande à PowerShell de :
  
1. Obtenir toutes les informations sur les comptes d’utilisateur (**Get-MsolUser**) et les envoyer à la commande suivante ( **|** ).
    
1. Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié (**où {$ \_ . UsageLocation-EQ $Null}**). À l’intérieur des accolades, la commande demande à PowerShell de rechercher uniquement l’ensemble des comptes pour lesquels la propriété de compte d’utilisateur UsageLocation (** $ \_ . UsageLocation**) n’est pas spécifié (**-EQ $null**).
    
Vous devriez obtenir des informations semblables à celles-ci :
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

La propriété *UsageLocation* n’est que l’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateur, utilisez l’applet de commande **Select** et le caractère générique (*) pour les afficher tous pour un compte d’utilisateur spécifique. Voici un exemple :
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Par exemple, *Ville* est le nom d’une propriété de compte d’utilisateur. Vous pouvez utiliser la commande suivante pour répertorier tous les comptes d’utilisateur pour les utilisateurs qui vivent à Londres :
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  La syntaxe de la cmdlet **Where** de ces exemples est **where {$ \_ .** [nom de la propriété du compte d’utilisateur] [opérateur de comparaison] valeur **}**.  [opérateur de comparaison] est **-EQ** pour Equals, **-** ne pour « différent de », **-lt** pour inférieur à, **-gt** pour supérieur à, et autres.  [valeur] est généralement une chaîne (une séquence de lettres, de chiffres et d’autres caractères), une valeur numérique ou **$null** pour non spécifié. Pour plus d’informations, voir [Where](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-7).
  
Pour vérifier l’État bloqué d’un compte d’utilisateur, utilisez la commande suivante :
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Afficher les valeurs des propriétés supplémentaires des comptes

Par défaut, la cmdlet **Get-MsolUser** affiche ces trois propriétés des comptes d’utilisateur :
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Si vous avez besoin de propriétés supplémentaires, telles que le service dans lequel travaille l’utilisateur et le pays/la région où ils utilisent les services Microsoft 365, vous pouvez exécuter **Get-MsolUser** en combinaison avec l’applet de commande **Select** pour spécifier la liste des propriétés du compte d’utilisateur. Voici un exemple :
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

Cette commande demande à PowerShell de :
  
1. Obtenir toutes les informations sur les comptes d’utilisateur (**Get-MsolUser**) et les envoyer à la commande suivante ( **|** ).
    
1. Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation (**Sélectionnez DisplayName, Department, UsageLocation**).
    
Vous devriez obtenir des informations semblables à celles-ci :
  
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

L’applet de commande **Select** vous permet de choisir les propriétés à afficher. Pour afficher toutes les propriétés d’un compte d’utilisateur spécifique, utilisez le caractère générique (*). Voici un exemple :
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez également utiliser la cmdlet **Where** . Voici un exemple de commande qui affiche uniquement les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié :
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

Cette commande demande à PowerShell de :
  
1. Obtenir toutes les informations sur les comptes d’utilisateur (**Get-MsolUser**) et les envoyer à la commande suivante ( **|** ).
    
1. Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié (**où {$ \_ . UsageLocation-EQ $Null}**) et envoyer les informations obtenues à la commande suivante ( **|** ). À l’intérieur des accolades, la commande demande à PowerShell de trouver uniquement l’ensemble des comptes pour lesquels la propriété de compte d’utilisateur UsageLocation (** $ \_ . UsageLocation**) n’est pas spécifié (**-EQ $null**).
    
1. Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation (**Sélectionnez DisplayName, Department, UsageLocation**).
    
Vous devriez obtenir des informations semblables à celles-ci :
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Si vous utilisez la synchronisation d’annuaires pour créer et gérer vos utilisateurs de Microsoft 365, vous pouvez afficher le compte local à partir duquel un utilisateur de Microsoft 365 a été projeté. L’exemple suivant suppose que :

- Azure AD Connect est configuré pour utiliser l’ancre source par défaut d’ObjectGUID. (Pour plus d’informations sur la configuration d’une ancre source, reportez-vous à la rubrique [Azure ad Connect : Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)).
- Le module des services de domaine Active Directory pour PowerShell a été installé (voir [outils RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)).

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
