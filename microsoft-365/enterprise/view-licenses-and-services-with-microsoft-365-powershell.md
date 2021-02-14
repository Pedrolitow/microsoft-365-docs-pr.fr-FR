---
title: Afficher les licences et services Microsoft 365 avec PowerShell
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
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Explique comment utiliser PowerShell pour afficher des informations sur les plans de gestion des licences, les services et les licences disponibles dans votre organisation Microsoft 365.
ms.openlocfilehash: 3275a513de3c114076e792ab6c5ef86b1413571c
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46689858"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>Afficher les licences et services Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Chaque abonnement Microsoft 365 comprend les éléments suivants :

- **Plans de gestion des licences** Ces plans sont également appelés plans de licence ou plans Microsoft 365. Les plans de gestion des licences définissent les services Microsoft 365 disponibles pour les utilisateurs. Votre abonnement Microsoft 365 peut contenir plusieurs plans de gestion des licences. Microsoft 365 E3 est un exemple de plan de gestion des licences.
    
- **Services** Ces plans sont également appelés plans de service. Les services sont les produits, fonctionnalités et fonctionnalités Microsoft 365 disponibles dans chaque plan de gestion des licences, par exemple, Exchange Online et Microsoft 365 Apps for enterprise (précédemment nommé Office 365 ProPlus). Des licences issues de différents plans de licence peuvent être attribuées à un même utilisateur, lui accordant l’accès à des services différents.
    
- **Licences** Chaque plan de gestion des licences contient le nombre de licences que vous avez achetées. Vous attribuez des licences aux utilisateurs afin qu’ils peuvent utiliser les services Microsoft 365 définis par le plan de gestion des licences. Chaque compte d’utilisateur nécessite au moins une licence d’un plan de gestion des licences pour pouvoir se connecter à Microsoft 365 et utiliser les services.
    
Vous pouvez utiliser PowerShell pour Microsoft 365 pour afficher des détails sur les plans de gestion des licences, les licences et les services disponibles dans votre organisation Microsoft 365. Pour plus d’informations sur les produits, fonctionnalités et services disponibles dans différents abonnements Office 365, voir Options de plan [Office 365.](https://go.microsoft.com/fwlink/p/?LinkId=691147)


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Utilisation du module Azure Active Directory PowerShell pour Graph

Tout [d’abord, connectez-vous à votre client Microsoft 365.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  
Pour afficher des informations récapitulatifs sur vos plans de gestion des licences actuels et les licences disponibles pour chaque plan, exécutez la commande ci-après :
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Les résultats contiennent :
  
- **SkuPartNumber :** Affiche les plans de gestion des licences disponibles pour votre organisation. Par exemple, `ENTERPRISEPACK` est le nom du plan de licence pour Office 365 Entreprise E3.
    
- **Activé :** Nombre de licences que vous avez achetées pour un plan de gestion des licences spécifique.
    
- **ConsumedUnits :** Nombre de licences que vous avez attribuées à des utilisateurs à partir d’un plan de gestion des licences spécifique.
    
Pour afficher des détails sur les services Microsoft 365 disponibles dans tous vos plans de licence, affichez d’abord la liste de vos plans de licence.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ensuite, stockez les informations des plans de licence dans une variable.

```powershell
$licenses = Get-AzureADSubscribedSku
```

Ensuite, affichez les services dans un plan de licence spécifique.

```powershell
$licenses[<index>].ServicePlans
```

\<index> est un nombre total qui spécifie le numéro de ligne du plan de licence à partir de l’affichage de la `Get-AzureADSubscribedSku | Select SkuPartNumber` commande, moins 1.

Par exemple, si l’affichage de la `Get-AzureADSubscribedSku | Select SkuPartNumber` commande est le cas :

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Ensuite, la commande d’affichage des services pour le plan de licence ENTERPRISEPREMIUM est la :

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM est la troisième ligne. Par conséquent, la valeur d’index est (3 - 1) ou 2.

Pour obtenir la liste complète des plans de licence (également appelés noms de produits), leurs plans de service inclus et leurs noms convivial correspondants, voir Noms de produits et identificateurs de plan de service pour la [gestion des licences.](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.

Tout [d’abord, connectez-vous à votre client Microsoft 365.](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

>[!Note]
>Un script PowerShell est disponible pour automatiser les procédures décrites dans cette rubrique. Plus précisément, le script vous permet d’afficher et de désactiver des services dans votre organisation Microsoft 365, y compris Sway. Pour plus d’informations, voir [Désactiver l’accès à Sway avec PowerShell.](disable-access-to-sway-with-microsoft-365-powershell.md)
>
    
Pour afficher des informations récapitulatifs sur vos plans de gestion des licences actuels et les licences disponibles pour chaque plan, exécutez la commande suivante :
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>

Les résultats contiennent les informations suivantes :
  
- **AccountSkuId :** Affichez les plans de gestion des licences disponibles pour votre organisation à l’aide de la `<CompanyName>:<LicensingPlan>` syntaxe.  _\<CompanyName>_ est la valeur que vous avez fournie lorsque vous vous êtes inscrit à Microsoft 365 et est unique pour votre organisation. La _\<LicensingPlan>_ valeur est la même pour tout le monde. Par exemple, dans la valeur , le nom de la société est et le nom du plan de gestion des licences, qui est le nom du système `litwareinc:ENTERPRISEPACK`  `litwareinc` pour Office  `ENTERPRISEPACK` 365 Entreprise E3.
    
- **ActiveUnits :** Nombre de licences que vous avez achetées pour un plan de gestion des licences spécifique.
    
- **WarningUnits :** Nombre de licences dans un plan de gestion des licences que vous n’avez pas renouvelé et qui expireront après la période de grâce de 30 jours.
    
- **ConsumedUnits :** Nombre de licences que vous avez attribuées à des utilisateurs à partir d’un plan de gestion des licences spécifique.
    
Pour afficher des détails sur les services Microsoft 365 disponibles dans tous vos plans de licence, exécutez la commande suivante :
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Le tableau suivant présente les plans de service Microsoft 365 et leurs noms convivial pour les services les plus courants. La liste de vos plans de services peut être différente. 
  
|**Plan de services**|**Description**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Applications Microsoft 365 pour les entreprises *(précédemment nommé Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype Entreprise Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online (plan 2)  <br/> |
   
Pour obtenir la liste complète des plans de licence (également appelés noms de produits), leurs plans de service inclus et leurs noms convivial correspondants, voir Noms de produits et identificateurs de plan de service pour la [gestion des licences.](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)

Pour afficher des détails sur les services Microsoft 365 disponibles dans un plan de gestion des licences spécifique, utilisez la syntaxe suivante.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

Cet exemple montre les services disponibles dans le plan de gestion des licences litwareinc:ENTERPRISEPACK (Office 365 Entreprise E3).
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>Voir aussi

[Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
