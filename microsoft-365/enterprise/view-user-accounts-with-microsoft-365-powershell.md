---
title: Afficher les comptes d’utilisateur Microsoft 365 avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
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
ms.openlocfilehash: bf3e8841272cfd744a41675a6b3bca1c81586116
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67672774"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>Afficher les comptes d’utilisateur Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez utiliser le Centre d'administration Microsoft 365 pour afficher les comptes de votre locataire Microsoft 365. PowerShell pour Microsoft 365 l’active, mais fournit également des fonctionnalités supplémentaires.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Afficher tous les comptes

Pour afficher la liste complète des comptes d’utilisateur, exécutez la commande suivante :
  
```powershell
Get-AzureADUser
```

Vous devez obtenir des informations similaires à ceci :
  
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

Pour afficher un compte d’utilisateur spécifique, exécutez la commande suivante. Renseignez le nom du compte de connexion du compte d’utilisateur, également appelé nom d’utilisateur principal (UPN). Supprimez les caractères « < » et « > ».
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Voici un exemple :
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Afficher des valeurs de propriété supplémentaires pour un compte spécifique

Par défaut, l’applet de commande **Get-AzureADUser** affiche uniquement les propriétés *ObjectID*, *DisplayName* et *UserPrincipalName* des comptes.

Pour être plus sélectif sur les propriétés à afficher, utilisez l’applet de commande **Select** en combinaison avec l’applet **de commande Get-AzureADUser** . Pour combiner les deux applets de commande, utilisez le caractère « pipe » (« | ») qui indique à Azure Active Directory PowerShell pour Graph de prendre les résultats d’une commande et de l’envoyer à la commande suivante. Voici un exemple de commande qui affiche *displayName*, *Department* et *UsageLocation* pour chaque compte d’utilisateur :
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

Cette commande indique à PowerShell d’effectuer les opérations suivantes :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser) et envoyez-les** à la commande suivante (**|**).
    
1.  Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation (**Select DisplayName, Department, UsageLocation**).
  
Pour afficher toutes les propriétés d’un compte d’utilisateur spécifique, utilisez l’applet de commande **Select** et le caractère générique (*). Voici un exemple :
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Dans un autre exemple, exécutez la commande suivante pour vérifier l’état activé d’un compte d’utilisateur spécifique :
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-account-synchronization-status"></a>Afficher l’état de synchronisation du compte

Les comptes d’utilisateur ont deux sources : 

- Windows Server Active Directory (AD), qui sont des comptes qui se synchronisent entre AD local et le cloud.

- Comptes Azure Active Directory (Azure AD), qui sont créés directement dans le cloud.

Vous pouvez utiliser la commande suivante pour rechercher les comptes qui se synchronisent à partir d’AD **local** . Il demande à PowerShell d’obtenir la *valeur True* pour tous les utilisateurs dont l’attribut *DirSyncEnabled est* défini. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -eq $true}
```

Vous pouvez utiliser la commande suivante pour rechercher **des comptes cloud uniquement** . Il indique à PowerShell d’obtenir tous les utilisateurs dont l’attribut *DirSyncEnabled a* la valeur *False* ou non défini (*Null*).
Un compte qui n’a jamais été synchronisé à partir d’AD local a *DirSyncEnabled* défini sur *Null*. Un compte qui a été synchronisé initialement à partir d’AD local mais qui n’est plus synchronisé a la valeur *False* pour *DirSyncEnabled*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -ne $true}
```

### <a name="view-accounts-based-on-a-common-property"></a>Afficher les comptes en fonction d’une propriété commune

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez utiliser l’applet de commande **Where** en combinaison avec l’applet de commande **Get-AzureADUser** . Pour combiner les deux applets de commande, utilisez le caractère « pipe » (« | ») qui indique à Azure Active Directory PowerShell pour Graph de prendre les résultats d’une commande et de l’envoyer à la commande suivante. Voici un exemple de commande qui affiche uniquement les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié :
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

Cette commande indique à Azure Active Directory PowerShell pour Graph de :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-AzureADUser) et envoyez-les** à la commande suivante (**|**).
    
1. Recherchez tous les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifié (**Où {$\_. UsageLocation -eq $Null}**). À l’intérieur des accolades, la commande indique à PowerShell de rechercher uniquement l’ensemble de comptes pour lesquels la propriété de compte d’utilisateur UsageLocation (**$\_. UsageLocation**) n’est pas spécifié (**-eq $Null**).
    
La propriété **UsageLocation** n’est que l’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés d’un compte d’utilisateur spécifique, utilisez l’applet de commande **Select** et le caractère générique (*). Voici un exemple :
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Par exemple, **Ville** est le nom d’une propriété de compte d’utilisateur. Vous pouvez utiliser la commande suivante pour répertorier tous les comptes d’utilisateurs qui vivent à Londres :
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
> La syntaxe de l’applet de commande **Where** dans ces exemples est **Where {$\_.** [nom de la propriété du compte d’utilisateur] [opérateur de comparaison] [valeur] **}**.> [opérateur de comparaison] est **-eq** for equals, **-ne** for not equals, **-lt** for inférieur à, **-gt** for great than, and others.  [value] est généralement une chaîne (une séquence de lettres, de nombres et d’autres caractères), une valeur numérique ou **$Null** pour les caractères non spécifiés. Pour plus d’informations, consultez [Where](/powershell/module/microsoft.powershell.core/where-object).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Afficher tous les comptes

Pour afficher la liste complète des comptes d’utilisateur, exécutez la commande suivante :
  
```powershell
Get-MsolUser
```

>[!Note]
>PowerShell Core ne prend pas en charge le Module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande avec *Msol* dans leur nom. Exécutez ces applets de commande à partir de Windows PowerShell.
>

Vous devez obtenir des informations similaires à ceci :
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

La cmdlet **Get-MsolUser** dispose également d’un jeu de paramètres pour filtrer l’ensemble de comptes utilisateur affichés. Par exemple, pour la liste des utilisateurs sans licence (utilisateurs qui ont été ajoutés à Microsoft 365 mais qui n’ont pas encore obtenu de licence pour utiliser les services), exécutez la commande suivante :
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

Vous devez obtenir des informations similaires à ceci :
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Pour plus d’informations sur les paramètres supplémentaires permettant de filtrer l’ensemble des comptes d’utilisateur affichés, consultez [Get-MsolUser](/previous-versions/azure/dn194133(v=azure.100)).
  
### <a name="view-a-specific-account"></a>Afficher un compte spécifique

Pour afficher un compte d’utilisateur spécifique, exécutez la commande suivante. Renseignez le nom de connexion du compte d’utilisateur, également appelé nom d’utilisateur principal (UPN). Supprimez les caractères « < » et « > ».
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-accounts-based-on-a-common-property"></a>Afficher les comptes en fonction d’une propriété commune

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez utiliser l’applet de commande **Where** en combinaison avec l’applet **de commande Get-MsolUser** . Pour combiner les deux applets de commande, utilisez le caractère « pipe » (« | »), qui indique à PowerShell de prendre les résultats d’une commande et de l’envoyer à la commande suivante. Voici un exemple qui affiche uniquement les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié :
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

Cette commande indique à PowerShell d’effectuer les opérations suivantes :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-MsolUser) et envoyez-les** à la commande suivante (**|**).
    
1. Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié (**Où {$\_. UsageLocation -eq $Null}**). À l’intérieur des accolades, la commande indique à PowerShell de rechercher uniquement l’ensemble de comptes pour lesquels la propriété de compte d’utilisateur UsageLocation (**$\_. UsageLocation**) n’est pas spécifié (**-eq $Null**).
    
Vous devez obtenir des informations similaires à ceci :
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

La propriété *UsageLocation* n’est que l’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateur, utilisez l’applet de commande **Select** et le caractère générique (*) pour les afficher toutes pour un compte d’utilisateur spécifique. Voici un exemple :
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Par exemple, *Ville* est le nom d’une propriété de compte d’utilisateur. Vous pouvez utiliser la commande suivante pour répertorier tous les comptes d’utilisateur pour les utilisateurs qui vivent à Londres :
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
> La syntaxe de l’applet de commande **Where** dans ces exemples est **Where {$\_.** [nom de la propriété du compte d’utilisateur] [opérateur de comparaison] [valeur] **}**.  [opérateur de comparaison] est **-eq** for equals, **-ne** for not equals, **-lt** for inférieur à, **-gt** for great than, and others.  [value] est généralement une chaîne (une séquence de lettres, de nombres et d’autres caractères), une valeur numérique ou **$Null** pour les caractères non spécifiés. Pour plus d’informations, consultez [Where](/powershell/module/microsoft.powershell.core/where-object).
  
Pour vérifier l’état bloqué d’un compte d’utilisateur, utilisez la commande suivante :
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Afficher des valeurs de propriété supplémentaires pour les comptes

Par défaut, l’applet **de commande Get-MsolUser** affiche les trois propriétés des comptes d’utilisateur :
  
- UserPrincipalName

- DisplayName

- isLicensed

Si vous avez besoin de propriétés supplémentaires, telles que le service où l’utilisateur travaille et le pays/région où il utilise les services Microsoft 365, vous pouvez exécuter **Get-MsolUser** en combinaison avec l’applet de commande **Select** pour spécifier la liste des propriétés du compte d’utilisateur. Voici un exemple :
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

Cette commande indique à PowerShell d’effectuer les opérations suivantes :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-MsolUser) et envoyez-les** à la commande suivante (**|**).
    
1. Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation (**Select DisplayName, Department, UsageLocation**).
    
Vous devez obtenir des informations similaires à ceci :
  
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

Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez également utiliser l’applet de commande **Where** . Voici un exemple de commande qui affiche uniquement les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié :
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

Cette commande indique à PowerShell d’effectuer les opérations suivantes :
  
1. Obtenez toutes les informations sur les comptes d’utilisateur (**Get-MsolUser) et envoyez-les** à la commande suivante (**|**).
    
1. Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié (**Où {$\_. UsageLocation -eq $Null}**) et envoyer les informations obtenues à la commande suivante (**|**). À l’intérieur des accolades, la commande indique à PowerShell de rechercher uniquement l’ensemble de comptes pour lesquels la propriété de compte d’utilisateur UsageLocation (**$\_. UsageLocation**) n’est pas spécifié (**-eq $Null**).
    
1. Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation (**Select DisplayName, Department, UsageLocation**).
    
Vous devez obtenir des informations similaires à ceci :
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Si vous utilisez la synchronisation d’annuaires pour créer et gérer vos utilisateurs Microsoft 365, vous pouvez afficher le compte local à partir duquel un utilisateur Microsoft 365 a été projeté. L’exemple suivant suppose que :

- Azure AD Connect est configuré pour utiliser l’ancre source par défaut d’ObjectGUID. (Pour plus d’informations sur la configuration d’une ancre source, consultez [Azure AD Connect : Concepts de conception](/azure/active-directory/hybrid/plan-connect-design-concepts)).
- Le module services de domaine Active Directory pour PowerShell a été installé (voir [outils RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)).

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
