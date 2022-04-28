---
title: Désactiver l’accès aux services Microsoft 365 lors de l’attribution de licences utilisateur
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Découvrez comment attribuer des licences à des comptes d’utilisateur et désactiver des plans de service spécifiques en même temps à l’aide de PowerShell pour Microsoft 365.
ms.openlocfilehash: 6c0c3a3860da8a1935152fcaefb29f2f355cfa49
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095727"
---
# <a name="disable-access-to-microsoft-365-services-while-assigning-user-licenses"></a>Désactiver l’accès aux services Microsoft 365 lors de l’attribution de licences utilisateur

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 abonnements sont fournis avec des plans de service pour des services individuels. Microsoft 365 les administrateurs doivent souvent désactiver certains plans lors de l’attribution de licences aux utilisateurs. Avec les instructions de cet article, vous pouvez attribuer une licence Microsoft 365 tout en désactivant des plans de service spécifiques à l’aide de PowerShell pour un compte d’utilisateur individuel ou plusieurs comptes d’utilisateur.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).


Ensuite, répertoriez les plans de licence pour votre locataire avec cette commande.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, obtenez le nom de connexion du compte auquel vous souhaitez ajouter une licence, également appelé nom d’utilisateur principal (UPN).

Ensuite, compilez la liste des services à activer. Pour obtenir la liste complète des plans de licence (également appelés noms de produits), leurs plans de service inclus et leurs noms conviviaux [correspondants, consultez les noms de produits et les identificateurs de plan de service pour la gestion des licences](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Pour le bloc de commandes ci-dessous, renseignez le nom d’utilisateur principal du compte d’utilisateur, le numéro de la partie référence SKU et la liste des plans de service pour activer et supprimer le texte explicatif et les \< and > caractères. Ensuite, exécutez les commandes qui en résultent à l’invite de commande PowerShell.

```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ensuite, exécutez cette commande pour afficher vos abonnements actuels :

```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Dans l'affichage de la commande  `Get-MsolAccountSku` :

- **AccountSkuId** est un abonnement pour votre organisation au \<OrganizationName>format :\<Subscription> Il \<OrganizationName> s’agit de la valeur que vous avez fournie lorsque vous vous êtes inscrit à Microsoft 365, et elle est unique pour votre organisation. La \<Subscription> valeur est pour un abonnement spécifique. Par exemple, pour litwareinc:ENTERPRISEPACK, le nom de l’organisation est litwareinc, et le nom de l’abonnement est ENTERPRISEPACK (Office 365 Entreprise E3).

- **ActiveUnits** représente le nombre de licences que vous avez achetées pour l'abonnement.

- **WarningUnits** représente le nombre de licences dans un abonnement que vous n'avez pas renouvelées et qui expireront après la période de grâce de 30 jours.

- **ConsumedUnits** représente le nombre de licences que vous avez affectées à des utilisateurs de l'abonnement.

Notez le AccountSkuId de votre abonnement Microsoft 365 qui contient les utilisateurs que vous souhaitez concéder sous licence. En outre, assurez-vous qu’il y a suffisamment de licences à attribuer (soustraire **ConsumedUnits** de **ActiveUnits**).

Ensuite, exécutez cette commande pour afficher les détails sur les plans de service Microsoft 365 disponibles dans tous vos abonnements :

```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

À partir de l’affichage de cette commande, déterminez les plans de service que vous souhaitez désactiver lorsque vous attribuez des licences aux utilisateurs.

Voici une liste partielle des plans de service et de leurs services Microsoft 365 correspondants.

Le tableau suivant présente les plans de service Microsoft 365 et leurs noms conviviaux pour les services les plus courants. La liste de vos plans de services peut être différente.

|**Plan de services**|**Description**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Applications Microsoft 365 pour les grandes entreprises *(précédemment nommé Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype Entreprise Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online (plan 2)  <br/> |

Pour obtenir la liste complète des plans de licence (également appelés noms de produits), leurs plans de service inclus et leurs noms conviviaux [correspondants, consultez les noms de produits et les identificateurs de plan de service pour la gestion des licences](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Maintenant que vous avez le paramètre AccountSkuId et les plans de service à désactiver, vous pouvez attribuer des licences pour un utilisateur ou plusieurs utilisateurs.

### <a name="for-a-single-user"></a>Pour un utilisateur unique

Pour un seul utilisateur, renseignez le nom d’utilisateur principal du compte d’utilisateur, accountSkuId et la liste des plans de service pour désactiver et supprimer le texte explicatif et les \< and > caractères. Ensuite, exécutez les commandes qui en résultent à l’invite de commande PowerShell.

```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

Voici un exemple de bloc de commande pour le compte nommé belindan@contoso.com, pour la licence contoso:ENTERPRISEPACK, et les plans de service à désactiver sont RMS_S_ENTERPRISE, SWAY, INTUNE_O365 et YAMMER_ENTERPRISE :

```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a>Pour plusieurs utilisateurs

Pour effectuer cette tâche d'administration pour plusieurs utilisateurs, créez un fichier texte de valeurs séparées par des virgules (CSV) qui contient les champs UserPrincipalName et UsageLocation. Voici un exemple :

```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

Ensuite, remplissez l’emplacement des fichiers CSV d’entrée et de sortie, l’ID de référence du compte et la liste des plans de service à désactiver, puis exécutez les commandes qui en résultent à l’invite de commande PowerShell.

```powershell
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

Ce bloc de commande PowerShell :

- affiche le nom d’utilisateur principal de chaque utilisateur ;

- attribue des licences personnalisées à chaque utilisateur ;

- crée un fichier CSV avec tous les utilisateurs qui ont été traités et affiche l’état de leur licence.

## <a name="see-also"></a>Voir aussi

[Désactiver l’accès aux services Microsoft 365 avec PowerShell](disable-access-to-services-with-microsoft-365-powershell.md)

[Désactiver l’accès à Sway avec PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md)

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)