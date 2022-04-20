---
title: Désactiver l’accès aux services Microsoft 365 avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/27/2020
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- seo-marvel-apr2020
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Dans cet article, découvrez comment utiliser PowerShell pour désactiver l’accès aux services Microsoft 365 pour les utilisateurs.
ms.openlocfilehash: eeb3c8dc0057318550a956d0d0f4f916f4515fd4
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64915860"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>Désactiver l’accès aux services Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Lorsqu’une licence d’un plan de licence est attribuée à un compte Microsoft 365, Microsoft 365 services sont mis à la disposition de l’utilisateur à partir de cette licence. Toutefois, vous pouvez contrôler les services Microsoft 365 auxquels l’utilisateur peut accéder. Par exemple, même si la licence autorise l’accès au service SharePoint Online, vous pouvez désactiver l’accès à celui-ci. Vous pouvez utiliser PowerShell pour désactiver l’accès à un nombre quelconque de services pour un plan de licence spécifique pour :

- un compte individuel ;
- un groupe de comptes ;
- tous les comptes de votre organisation.

>[!Note]
>Il existe Microsoft 365 dépendances de service qui peuvent vous empêcher de désactiver un service spécifié lorsque d’autres services en dépendent.
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Utiliser le Kit de développement logiciel (SDK) Microsoft Graph PowerShell

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](/graph/powershell/get-started#authentication).

L’attribution et la suppression de licences pour un utilisateur nécessitent l’étendue d’autorisation User.ReadWrite.All ou l’une des autres autorisations répertoriées dans la [page de référence « Attribuer une licence » API Graph](/graph/api/user-assignlicense).

L’étendue d’autorisation Organization.Read.All est nécessaire pour lire les licences disponibles dans le locataire.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Ensuite, utilisez cette commande pour afficher vos plans de licence disponibles, également appelés SkuPartNumber :

```powershell
Get-MgSubscribedSku | Select SkuId, SkuPartNumber, ServicePlans | Sort SkuPartNumber
```

Pour plus d’informations, consultez [Afficher les licences et les services avec PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

Pour afficher les résultats avant et après des procédures de cette rubrique, consultez [Afficher les détails de la licence de compte et du service avec PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md).

### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Désactiver des services Microsoft 365 spécifiques pour des utilisateurs spécifiques pour un plan de licence spécifique
  
Pour désactiver un ensemble spécifique de services Microsoft 365 pour les utilisateurs pour un plan de licence spécifique, effectuez les étapes suivantes :
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>Étape 1 : Identifier les services non désirés dans le plan de licence à l’aide de la syntaxe suivante :

Commencez par répertorier les plans de licence disponibles dans votre locataire à l’aide de la commande suivante.

```powershell
Get-MgSubscribedSku | Select SkuPartNumber

SkuPartNumber
-------------
EMSPREMIUM
SPE_E5
RIGHTSMANAGEMENT_ADHOC

```

Ensuite, utilisez SkuPartNumber à partir de la commande ci-dessus, répertoriez les plans de service disponibles pour un plan de licence (SKU) donné.

L’exemple suivant répertorie tous les plans de service disponibles pour **SPE_E5** (Microsoft 365 E5).

```powershell
Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5' |  select -ExpandProperty ServicePlans
```

```text
AppliesTo ProvisioningStatus ServicePlanId                        ServicePlanName
--------- ------------------ -------------                        ---------------
User      Success            b21a6b06-1988-436e-a07b-51ec6d9f52ad PROJECT_O365_P3
User      Success            64bfac92-2b17-4482-b5e5-a0304429de3e MICROSOFTENDPOINTDLP
User      Success            199a5c09-e0ca-4e37-8f7c-b05d533e1ea2 MICROSOFTBOOKINGS
User      Success            6db1f1db-2b46-403f-be40-e39395f08dbb CUSTOMER_KEY
User      Success            4a51bca5-1eff-43f5-878c-177680f191af WHITEBOARD_PLAN3
User      Success            07699545-9485-468e-95b6-2fca3738be01 FLOW_O365_P3
User      Success            9c0dab89-a30c-4117-86e7-97bda240acd2 POWERAPPS_O365_P3
User      Success            e212cbc7-0961-4c40-9825-01117710dcb1 FORMS_PLAN_E5
User      Success            57ff2da0-773e-42df-b2af-ffb7a2317929 TEAMS1
User      Success            21b439ba-a0ca-424f-a6cc-52f954a5b111 WIN10_PRO_ENT_SUB
User      Success            eec0eb4f-6444-4f95-aba0-50c24d67f998 AAD_PREMIUM_P2
User      Success            c1ec4a95-1f05-45b3-a911-aa3fa01094f5 INTUNE_A
User      Success            7547a3fe-08ee-4ccb-b430-5077c5041653 YAMMER_ENTERPRISE
User      Success            a23b959c-7ce8-4e57-9140-b90eb88a9e97 SWAY
User      Success            e95bec33-7c88-4a70-8e19-b10bd9d0c014 SHAREPOINTWAC
User      Success            5dbe027f-2339-4123-9542-606e4d348a72 SHAREPOINTENTERPRISE
User      Success            b737dad2-2f6c-4c65-90e3-ca563267e8b9 PROJECTWORKMANAGEMENT
User      Success            43de0ff5-c92c-492b-9116-175376d08c38 OFFICESUBSCRIPTION
User      Success            0feaeb32-d00e-4d66-bd5a-43b5b83db82c MCOSTANDARD
User      Success            9f431833-0334-42de-a7dc-70aa40db46db LOCKBOX_ENTERPRISE
User      Success            efb87545-963c-4e0d-99df-69c6916d9eb0 EXCHANGE_S_ENTERPRISE
```

Pour obtenir la liste complète des plans de licence (également appelés noms de produits), leurs plans de service inclus et leurs noms conviviaux [correspondants, consultez les noms de produits et les identificateurs de plan de service pour la gestion des licences](/azure/active-directory/users-groups-roles/licensing-service-plan-reference). (Effectuez une recherche à l’aide de ServicePlanId pour rechercher le nom convivial correspondant du plan de service).

L’exemple suivant affecte **SPE_E5** (Microsoft 365 E5) avec les services **MICROSOFTBOOKINGS** (Microsoft Bookings) et **LOCKBOX_ENTERPRISE** (Customer LockBox) désactivés :
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$disabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("LOCKBOX_ENTERPRISE", "MICROSOFTBOOKINGS") | `
    Select -ExpandProperty ServicePlanId

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

La propriété DisabledPlans du paramètre AddLicenses dans Set-MgUserLicense remplacera la valeur DisabledPlans existante de l’utilisateur. Pour préserver l’état des plans de service existants, l’état actuel des plans de service de l’utilisateur doit être fusionné avec les nouveaux plans qui vont être désactivés.

Si vous n’incluez pas les disabledPlans existants, le plan précédemment désactivé de l’utilisateur sera activé.

L’exemple suivant met à jour un utilisateur avec **SPE_E5** (Microsoft 365 E5) et désactive les plans de service Sway et Forms tout en laissant les plans désactivés existants de l’utilisateur dans leur état actuel :
  
```powershell
## Get the services that have already been disabled for the user.
$userLicense = Get-MgUserLicenseDetail -UserId "belinda@fdoau.onmicrosoft.com"
$userDisabledPlans = $userLicense.ServicePlans | `
    Where ProvisioningStatus -eq "Disabled" | `
    Select -ExpandProperty ServicePlanId

## Get the new service plans that are going to be disabled
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$newDisabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("SWAY", "FORMS_PLAN_E5") | `
    Select -ExpandProperty ServicePlanId

## Merge the new plans that are to be disabled with the user's current state of disabled plans
$disabledPlans = ($userDisabledPlans + $newDisabledPlans) | Select -Unique

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)
## Update user's license
Set-MgUserLicense -UserId "belinda@litwareinc.onmicrosoft.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ensuite, utilisez cette commande pour afficher vos plans de licence disponibles, également appelés AccountSkuIds :

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Pour plus d’informations, consultez [Afficher les licences et les services avec PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).
    
Pour afficher les résultats avant et après des procédures de cette rubrique, consultez [Afficher les détails de la licence de compte et du service avec PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md).
    
Un script PowerShell est disponible pour automatiser les procédures décrites dans cette rubrique. Plus précisément, le script vous permet d’afficher et de désactiver les services de votre organisation Microsoft 365, y compris les Sway. Pour plus d’informations, consultez [Désactiver l’accès à Sway avec PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Désactiver des services Microsoft 365 spécifiques pour des utilisateurs spécifiques pour un plan de licence spécifique
  
Pour désactiver un ensemble spécifique de services Microsoft 365 pour les utilisateurs pour un plan de licence spécifique, effectuez les étapes suivantes :
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>Étape 1 : Identifier les services non désirés dans le plan de licence à l’aide de la syntaxe suivante :
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesiredService1>", "<UndesiredService2>"...
```

L’exemple suivant crée un objet **LicenseOptions** qui désactive les services Office et SharePoint Online dans le plan de licence nommé `litwareinc:ENTERPRISEPACK` (Office 365 Entreprise E3).
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>Étape 2 : Utiliser l’objet **LicenseOptions** de l’étape 1 sur un ou plusieurs utilisateurs.
    
Pour créer un compte dont les services sont désactivés, utilisez la syntaxe suivante :
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

L’exemple suivant crée un compte pour Allie Bellew qui affecte la licence et désactive les services décrits à l’étape 1.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

Pour plus d’informations sur la création de comptes d’utilisateur dans PowerShell pour Microsoft 365, consultez [Créer des comptes d’utilisateur avec PowerShell](create-user-accounts-with-microsoft-365-powershell.md).
    
Pour désactiver les services d’un utilisateur sous licence existant, utilisez la syntaxe suivante :
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

Cet exemple désactive les services de l’utilisateur BelindaN@litwareinc.com.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

Pour désactiver les services décrits à l’étape 1 pour tous les utilisateurs sous licence existants, spécifiez le nom de votre plan Microsoft 365 à partir de l’affichage de l’applet de commande **Get-MsolAccountSku** (par exemple **litwareinc:ENTERPRISEPACK**), puis exécutez les commandes suivantes :
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 Si vous utilisez l’applet **de commande Get-MsolUser** sans utiliser le paramètre _All_ , seuls les 500 premiers comptes d’utilisateur sont retournés.

Pour désactiver les services pour un groupe d’utilisateurs existants, appliquez l’une des méthodes suivantes pour identifier les utilisateurs :
    
**Méthode 1. Filtrer les comptes en fonction d’un attribut de compte existant** 

Pour ce faire, utilisez la syntaxe suivante :
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

L’exemple suivant désactive les services pour les utilisateurs du service Ventes dans le États-Unis.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**Méthode 2 : Utiliser une liste de comptes spécifiques** 

Pour ce faire, procédez comme suit :
    
1. Créez un fichier texte contenant un seul compte sur chaque ligne comme suit :
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   Dans cet exemple, le fichier texte est C:\\My Documents\\Accounts.txt.
    
2. Exécutez la commande suivante :
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

Si vous souhaitez désactiver l’accès aux services pour plusieurs plans de licence, répétez les instructions ci-dessus pour chaque plan de licence, en vous assurant que :

- Le plan de licence a été attribué aux comptes d’utilisateur.
- Les services à désactiver sont disponibles dans le plan de licences.

Pour désactiver Microsoft 365 services pour les utilisateurs pendant que vous les affectez à un plan de licences, consultez [Désactiver l’accès aux services lors de l’attribution de licences utilisateur](disable-access-to-services-while-assigning-user-licenses.md).

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a>Affecter tous les services d’un plan de licence à un compte d’utilisateur

Pour les comptes d’utilisateurs dont les services ont été désactivés, vous pouvez activer tous les services pour un plan de licence spécifique avec les commandes suivantes :

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
