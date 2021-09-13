---
title: Désactiver l’accès aux services Microsoft 365 avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/27/2020
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- seo-marvel-apr2020
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Dans cet article, découvrez comment utiliser PowerShell pour désactiver l’accès aux services Microsoft 365 pour les utilisateurs.
ms.openlocfilehash: 7caab5fc6bc4522f210d788d0293c4594997f13d
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59165388"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>Désactiver l’accès aux services Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Lorsqu’Microsoft 365 de gestion se voit attribuer une licence à partir d’un plan de gestion des licences, les services Microsoft 365 sont mis à la disposition de l’utilisateur à partir de cette licence. Toutefois, vous pouvez contrôler les services Microsoft 365 que l’utilisateur peut accéder. Par exemple, même si la licence autorise l’accès au service SharePoint Online, vous pouvez désactiver l’accès à celui-ci. Vous pouvez utiliser PowerShell pour désactiver l’accès à n’importe quel nombre de services pour un plan de gestion des licences spécifique pour :

- un compte individuel ;
- un groupe de comptes ;
- tous les comptes de votre organisation.

>[!Note]
>Il existe Microsoft 365 dépendances de service qui peuvent vous empêcher de désactiver un service spécifié lorsque d’autres services en dépendent.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à Microsoft 365 client.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

Ensuite, utilisez cette commande pour afficher vos plans de gestion des licences disponibles, également appelés AccountSkuIds :

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Pour plus d’informations, voir [Afficher les licences et les services avec PowerShell.](view-licenses-and-services-with-microsoft-365-powershell.md)
    
Pour afficher les résultats avant et après des procédures de cette rubrique, voir Afficher la licence de compte et les détails du [service avec PowerShell.](view-account-license-and-service-details-with-microsoft-365-powershell.md)
    
Un script PowerShell est disponible pour automatiser les procédures décrites dans cette rubrique. Plus précisément, le script vous permet d’afficher et de désactiver des services dans votre organisation Microsoft 365, y compris Sway. Pour plus d’informations, voir [Désactiver l’accès à Sway avec PowerShell.](disable-access-to-sway-with-microsoft-365-powershell.md)
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Désactiver des services Microsoft 365 spécifiques pour des utilisateurs spécifiques pour un plan de gestion des licences spécifique
  
Pour désactiver un ensemble spécifique de services Microsoft 365 pour les utilisateurs pour un plan de gestion des licences spécifique, effectuez les étapes suivantes :
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a>Étape 1 : identifiez les services indésirables dans le plan de gestion des licences à l’aide de la syntaxe suivante :
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

L’exemple suivant crée un objet **LicenseOptions** qui désactive les services Office et SharePoint Online dans le plan de gestion des licences nommé `litwareinc:ENTERPRISEPACK` (Office 365 Entreprise E3).
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>Étape 2 : Utilisez **l’objet LicenseOptions** de l’étape 1 sur un ou plusieurs utilisateurs.
    
Pour créer un compte dont les services sont désactivés, utilisez la syntaxe suivante :
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

L’exemple suivant crée un compte pour Allie Bellew qui attribue la licence et désactive les services décrits à l’étape 1.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

Pour plus d’informations sur la création de comptes d’utilisateurs dans PowerShell pour Microsoft 365, voir Créer des comptes d’utilisateurs [avec PowerShell.](create-user-accounts-with-microsoft-365-powershell.md)
    
Pour désactiver les services d’un utilisateur sous licence existant, utilisez la syntaxe suivante :
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

Cet exemple désactive les services de l’utilisateur BelindaN@litwareinc.com.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

Pour désactiver les services décrits à l’étape 1 pour tous les utilisateurs sous licence existants, spécifiez le nom de votre plan Microsoft 365 à partir de l’affichage de la cmdlet **Get-MsolAccountSku** (par **exemple, litwareinc:ENTERPRISEPACK),** puis exécutez les commandes suivantes :
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _All,_ seuls les 500 premiers comptes d’utilisateur sont renvoyés.

Pour désactiver les services pour un groupe d’utilisateurs existants, appliquez l’une des méthodes suivantes pour identifier les utilisateurs :
    
**Méthode 1. Filtrer les comptes en fonction d’un attribut de compte existant** 

Pour ce faire, utilisez la syntaxe suivante :
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

L’exemple suivant désactive les services pour les utilisateurs du service Sales aux États-Unis.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**Méthode 2 : utiliser une liste de comptes spécifiques** 

Pour ce faire, procédez comme suit :
    
1. Créez un fichier texte contenant un seul compte sur chaque ligne comme suit :
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   Dans cet exemple, le fichier texte est C: \\ My Documents \\Accounts.txt.
    
2. Exécutez la commande suivante :
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

Si vous souhaitez désactiver l’accès aux services pour plusieurs plans de gestion des licences, répétez les instructions ci-dessus pour chaque plan de gestion des licences, en vous assurant que :

- Le plan de gestion des licences a été attribué aux comptes d’utilisateurs.
- Les services à désactiver sont disponibles dans le plan de gestion des licences.

Pour désactiver les services Microsoft 365 pour les utilisateurs pendant que vous les affectez à un plan de gestion des licences, voir Désactiver l’accès aux services tout en attribuant des [licences utilisateur.](disable-access-to-services-while-assigning-user-licenses.md)

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a>Affecter tous les services d’un plan de gestion des licences à un compte d’utilisateur

Pour les comptes d’utilisateurs dont les services ont été désactivés, vous pouvez activer tous les services pour un plan de gestion des licences spécifique avec les commandes ci-après :

```powershell
$userUPN="<user account UPN>"
$acctSKU="<AccountSkuId>"
$LO = New-MsolLicenseOptions -AccountSkuId $acctSKU
Set-MsolUserLicense -UserPrincipalName $userUPN -LicenseOptions $LO
```

## <a name="related-topic"></a>Rubrique connexe

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
