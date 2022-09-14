---
title: Afficher les licences et services Microsoft 365 avec PowerShell
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
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Explique comment utiliser PowerShell pour afficher des informations sur les plans de licence, les services et les licences disponibles dans votre organisation Microsoft 365.
ms.openlocfilehash: 739c79fe66871125a5ea9d35226d9acd6f99abf4
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67669780"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>Afficher les licences et services Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Chaque abonnement Microsoft 365 se compose des éléments suivants :

- **Plans de licence** Il s’agit également de plans de licence ou de plans Microsoft 365. Les plans de licence définissent les services Microsoft 365 disponibles pour les utilisateurs. Votre abonnement Microsoft 365 peut contenir plusieurs plans de licence. Un exemple de plan de licence serait Microsoft 365 E3.
    
- **Services** Il s’agit également de plans de service. Les services sont les produits, fonctionnalités et fonctionnalités Microsoft 365 disponibles dans chaque plan de licence, par exemple, Exchange Online et Applications Microsoft 365 pour les grandes entreprises (précédemment nommés Office 365 ProPlus). Des licences issues de différents plans de licence peuvent être attribuées à un même utilisateur, lui accordant l’accès à des services différents.
    
- **Licences** Chaque plan de licence contient le nombre de licences que vous avez achetées. Vous attribuez des licences aux utilisateurs afin qu’ils puissent utiliser les services Microsoft 365 définis par le plan de licences. Chaque compte d’utilisateur nécessite au moins une licence à partir d’un plan de licence pour pouvoir se connecter à Microsoft 365 et utiliser les services.
    
Vous pouvez utiliser PowerShell pour Microsoft 365 pour afficher des détails sur les plans de licence, les licences et les services disponibles dans votre organisation Microsoft 365. Pour plus d’informations sur les produits, fonctionnalités et services disponibles dans différents abonnements Office 365, consultez [Office 365 Options de plan](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).


## <a name="use-the-microsoft-graph-powershell-sdk"></a>Utiliser le Kit de développement logiciel (SDK) Microsoft Graph PowerShell

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](/graph/powershell/get-started#authentication).

La lecture des plans de licence d’abonnement nécessite l’étendue d’autorisation Organization.Read.All ou l’une des autres autorisations répertoriées dans la [page de référence « List subscribedSkus » API Graph](/graph/api/subscribedsku-list).

```powershell
Connect-Graph -Scopes Organization.Read.All
```

Pour afficher des informations récapitulatives sur vos plans de licence actuels et les licences disponibles pour chaque plan, exécutez la commande suivante :
  
```powershell
Get-MgSubscribedSku | Select -Property Sku*, ConsumedUnits -ExpandProperty PrepaidUnits | Format-List
```

Les résultats contiennent :
  
- **SkuPartNumber :** Affiche les plans de licence disponibles pour votre organisation. Par exemple, `ENTERPRISEPACK` est le nom du plan de licence pour Office 365 Entreprise E3.
    
- **Activé:** Nombre de licences que vous avez achetées pour un plan de licence spécifique.
    
- **ConsumedUnits :** Nombre de licences que vous avez attribuées aux utilisateurs à partir d’un plan de licence spécifique.
    
Pour afficher des détails sur les services Microsoft 365 disponibles dans tous vos plans de licence, commencez par afficher la liste de vos plans de licence.

```powershell
Get-MgSubscribedSku
```

Ensuite, stockez les informations sur les plans de licence dans une variable.

```powershell
$licenses = Get-MgSubscribedSku
```

Ensuite, affichez les services dans un plan de licence spécifique.

```powershell
$licenses[<index>].ServicePlans
```

\<index> est un entier qui spécifie le numéro de ligne du plan de licence à partir de l’affichage de la `Get-MgSubscribedSku | Select SkuPartNumber` commande, moins 1.

Par exemple, si l’affichage de la commande est le `Get-MgSubscribedSku | Select SkuPartNumber` suivant :

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Ensuite, la commande permettant d’afficher les services pour le plan de licence ENTERPRISEPREMIUM est la suivante :

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM est la troisième ligne. Par conséquent, la valeur d’index est (3 - 1) ou 2.

Pour obtenir la liste complète des plans de licence (également appelés noms de produits), leurs plans de service inclus et leurs noms conviviaux [correspondants, consultez les noms de produits et les identificateurs de plan de service pour la gestion des licences](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Pour afficher des informations récapitulatives sur vos plans de licence actuels et les licences disponibles pour chaque plan, exécutez la commande suivante :
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Les résultats contiennent :
  
- **SkuPartNumber :** Affiche les plans de licence disponibles pour votre organisation. Par exemple, `ENTERPRISEPACK` est le nom du plan de licence pour Office 365 Entreprise E3.
    
- **Activé:** Nombre de licences que vous avez achetées pour un plan de licence spécifique.
    
- **ConsumedUnits :** Nombre de licences que vous avez attribuées aux utilisateurs à partir d’un plan de licence spécifique.
    
Pour afficher des détails sur les services Microsoft 365 disponibles dans tous vos plans de licence, commencez par afficher la liste de vos plans de licence.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, stockez les informations sur les plans de licence dans une variable.

```powershell
$licenses = Get-AzureADSubscribedSku
```

Ensuite, affichez les services dans un plan de licence spécifique.

```powershell
$licenses[<index>].ServicePlans
```

\<index> est un entier qui spécifie le numéro de ligne du plan de licence à partir de l’affichage de la `Get-AzureADSubscribedSku | Select SkuPartNumber` commande, moins 1.

Par exemple, si l’affichage de la commande est le `Get-AzureADSubscribedSku | Select SkuPartNumber` suivant :

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Ensuite, la commande permettant d’afficher les services pour le plan de licence ENTERPRISEPREMIUM est la suivante :

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM est la troisième ligne. Par conséquent, la valeur d’index est (3 - 1) ou 2.

Pour obtenir la liste complète des plans de licence (également appelés noms de produits), leurs plans de service inclus et leurs noms conviviaux [correspondants, consultez les noms de produits et les identificateurs de plan de service pour la gestion des licences](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à votre locataire Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Un script PowerShell est disponible pour automatiser les procédures décrites dans cette rubrique. Plus précisément, le script vous permet d’afficher et de désactiver les services de votre organisation Microsoft 365, y compris Sway. Pour plus d’informations, consultez [Désactiver l’accès à Sway avec PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
>
    
Pour afficher des informations récapitulatives sur vos plans de licence actuels et les licences disponibles pour chaque plan, exécutez la commande suivante :
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Les résultats contiennent les informations suivantes :
  
- **AccountSkuId :** Affichez les plans de licence disponibles pour votre organisation à l’aide de la syntaxe `<CompanyName>:<LicensingPlan>`.  _\<CompanyName>_ est la valeur que vous avez fournie lorsque vous vous êtes inscrit à Microsoft 365 et est unique pour votre organisation. La _\<LicensingPlan>_ valeur est la même pour tout le monde. Par exemple, dans la valeur`litwareinc:ENTERPRISEPACK`, le nom de la société est `litwareinc`, et le nom `ENTERPRISEPACK`du plan de licence , qui est le nom du système pour Office 365 Entreprise E3.
    
- **ActiveUnits :** Nombre de licences que vous avez achetées pour un plan de licence spécifique.
    
- **WarningUnits :** Nombre de licences dans un plan de licence que vous n’avez pas renouvelé et qui expireront après la période de grâce de 30 jours.
    
- **ConsumedUnits :** Nombre de licences que vous avez attribuées aux utilisateurs à partir d’un plan de licence spécifique.
    
Pour afficher des détails sur les services Microsoft 365 disponibles dans tous vos plans de licence, exécutez la commande suivante :
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Le tableau suivant présente les plans de service Microsoft 365 et leurs noms conviviaux pour les services les plus courants. La liste de vos plans de services peut être différente. 
  
|**Plan de services**|**Description**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Applications Microsoft 365 pour les grandes entreprises *(précédemment nommé Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype Entreprise Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online (plan 2)  <br/> |
   
Pour obtenir la liste complète des plans de licence (également appelés noms de produits), leurs plans de service inclus et leurs noms conviviaux [correspondants, consultez les noms de produits et les identificateurs de plan de service pour la gestion des licences](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Pour afficher des détails sur les services Microsoft 365 disponibles dans un plan de licence spécifique, utilisez la syntaxe suivante.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

Cet exemple montre les services disponibles dans le plan de licence litwareinc:ENTERPRISEPACK (Office 365 Entreprise E3).
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)