---
title: Se connecter à tous les services Microsoft 365 dans une seule fenêtre PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Résumé : se connecter à tous les services Microsoft 365 dans une seule fenêtre PowerShell.'
ms.openlocfilehash: 4266b4f216b4c9df48f0c19d1d2123269eb32cae
ms.sourcegitcommit: 00d231bf0100e843a5a93161695e87ceff9e1349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "49849588"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-powershell-window"></a>Se connecter à tous les services Microsoft 365 dans une seule fenêtre PowerShell

Lorsque vous utilisez PowerShell pour gérer Microsoft 365, plusieurs sessions PowerShell peuvent être ouvertes en même temps. Vous avez peut-être des fenêtres PowerShell différentes pour gérer les comptes d’utilisateurs, SharePoint Online, Exchange Online, Skype Entreprise Online, Microsoft Teams et le centre de Sécurité &amp; de Conformité.
  
Ce scénario n’est pas optimal pour gérer Microsoft 365, car vous ne pouvez pas échanger de données entre ces fenêtres pour effectuer une gestion interservices. Cet article décrit comment utiliser une instance unique de PowerShell pour gérer les comptes Microsoft 365, Skype Entreprise Online, Exchange Online, SharePoint Online, Microsoft Teams et le Centre de sécurité &amp; de conformité.

>[!Note]
>Cet article contient actuellement uniquement les commandes permettant de se connecter au cloud (+GCC) dans le monde entier. Notes fournit des liens vers des articles pour la connexion aux autres clouds Microsoft 365.

## <a name="before-you-begin"></a>Avant de commencer

Avant de pouvoir gérer l’ensemble de Microsoft 365 à partir d’une seule instance de PowerShell, tenez compte des conditions préalables suivantes :
  
- Le compte professionnel ou scolaire Microsoft 365 que vous utilisez doit être membre du rôle d’administrateur Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles). Cette condition est requise pour PowerShell, pour Microsoft 365, mais pas nécessairement pour tous les autres services Microsoft 365.
    
- Vous pouvez utiliser les versions 64 bits de Windows suivantes :
    
  - Windows 10
    
  - Windows 8.1 ou Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 ou Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \* Vous devez installer Microsoft .NET Framework 4,5.*x* puis Windows Management Framework 3,0 ou 4,0. Pour plus d’informations, consultez [Windows Management Framework](https://docs.microsoft.com/powershell/scripting/windows-powershell/wmf/overview?view=powershell-7).
    
    Vous devez utiliser une version 64 bits de Windows en raison de la configuration requise pour le module Skype Entreprise Online et un des modules Microsoft 365.
    
- Vous devez installer les modules requis pour Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype Entreprise Online et les équipes :
    
  - [Azure Active Directory V2](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
  - [Skype Entreprise Online, module Powershell](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  - [Echange en ligne PowerShell V2](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exchange-online-powershell-v2-module)
  - [Aperçu de Teams PowerShell](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  PowerShell doit être configuré afin d’exécuter des scripts signés pour Skype Entreprise Online et le Centre de Sécurité &amp; de Conformité. Exécutez cette commande dans une session PowerShell élevée (une session PowerShell que vous **Exécutez en tant qu’administrateur**).
    
   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="exchange-online-and-security-amp-compliance-center-with-the-exchange-online-powershell-v2-module"></a>Centre de conformité et sécurité &amp;Exchange Online avec le module Exchange Online PowerShell v2

Les procédures contenues dans cet article utilisent le module Exchange Online PowerShell v2 pour se connecter à Exchange Online et au Centre de Sécurité &amp; de Conformité. Mais pour l’instant, vous ne pouvez pas vous connecter aux deux *dans la même fenêtre PowerShell*. Vous devez donc choisir de vous connecter à l’un ou l’autre lorsque vous configurez une fenêtre PowerShell pour plusieurs services Microsoft 365.

## <a name="connection-steps-when-using-just-a-password"></a>Étapes de connexion lors de l’utilisation d’un mot de passe

Voici les étapes à suivre pour vous connecter à tous les services dans une fenêtre unique PowerShell lorsque vous utilisez uniquement un mot de passe pour la connexion.
  
1. Ouvrez Windows PowerShell.
    
2. Exécutez la commande suivante et entrez les informations d’identification de votre compte professionnel ou scolaire Microsoft 365.
    
   ```powershell
   $credential = Get-Credential
   ```

3. Exécutez cette commande pour vous connecter à Azure AD à l’aide du module Azure Active Directory PowerShell pour le module Graph.
    
   ```powershell
   Connect-AzureAD -Credential $credential
   ```
  
   Ou si vous utilisez le Module Microsoft Azure Active Directory pour le module Windows PowerShell, exécutez cette commande.
      
   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!Note]
   > PowerShell Core ne prend pas en charge le Module Microsoft Azure Active Directory pour le module Windows PowerShell et les cmdlets ayant *Msol* dans leur nom. Exécutez ces cmdlets à partir de PowerShell.

4. Exécutez ces commandes pour vous connecter à SharePoint Online. Spécifiez le nom de l’organisation de votre domaine. Par exemple, pour « litwareinc\.onmicrosoft.com », la valeur nom de l’organisation est « litwareinc ».
    
   ```powershell
   $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
   Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $Credential
   ```

5. Exécutez ces commandes pour vous connecter à Skype Entreprise online. Un avertissement relatif à la valeur `WSMan NetworkDelayms` apparaît à la première connexion.  Ignorez.
     
   > [!Note]
   > Le connecteur Skype Entreprise Online fait actuellement partie du dernier module PowerShell Teams. Si vous utilisez la version publique la plus récente de PowerShell Teams, vous n’avez pas besoin d’installer le connecteur Skype Entreprise Online.
   
   ```powershell
   Import-Module MicrosoftTeams
   $sfboSession = New-CsOnlineSession -Credential $credential
   Import-PSSession $sfboSession
   ```

6. Exécutez cette commande pour vous connecter à Exchange Online.
    
   ```powershell
   Import-Module ExchangeOnlineManagement
   Connect-ExchangeOnline -Credential $credential -ShowProgress $true
   ```

   > [!Note]
   > Pour vous connecter à Exchange Online pour les nuages Microsoft 365 autres que le monde, consulter [Se connecter à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

   Vous pouvez également exécuter ces commandes pour vous connecter au Centre de Sécurité &amp; de Conformité.
    
   ```powershell
   $acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
   Import-Module ExchangeOnlineManagement
   Connect-IPPSSession -UserPrincipalName $acctName
   ```

   > [!Note]
   > Pour vous connecter au centre de conformité &amp; de sécurité pour les nuages Microsoft 365 autres que le monde, voir [Se connecter à la sécurité &](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell)PowerShell du centre de conformité.

   Exécutez ces commandes pour vous connecter au PowerShell Teams.
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams -Credential $credential
   ```
  
   > [!Note]
   > Pour vous connecter aux clouds Microsoft Teams autres *que Worldwide*, consultez [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams).


### <a name="azure-active-directory-powershell-for-graph-module"></a>Module Azure Active Directory PowerShell pour Graph

Voici les commandes de tous les services *à l’exception  du Centre de Sécurité &amp; de Conformité* dans un bloc unique lors de l’utilisation de Azure Active Directory PowerShell pour le module Graph. Spécifiez le nom de votre hôte de domaine, puis exécutez-les en même temps.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module MicrosoftTeams
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Voici les commandes de tous les services *à l’exception de Exchange Online* dans un bloc unique lors de l’utilisation de Azure Active Directory PowerShell pour le module Graph. Spécifiez le nom de votre hôte de domaine et le nom d’utilisateur principal (UPN) pour la connexion, puis exécutez-les en même temps.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$credential = Get-Credential -UserName $acctName
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module MicrosoftTeams
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
Import-Module ExchangeOnlineManagement
Connect-IPPSSession -UserPrincipalName $acctName
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module"></a>Module Microsoft Azure Active Directory pour module Windows PowerShell

Voici les commandes de tous les services *à l’exception  du Centre de Sécurité &amp; de Conformité* dans un bloc unique lors de l’utilisation du Module Microsoft Azure Active Directory pour le module Windows PowerShell. Spécifiez le nom de votre hôte de domaine, puis exécutez-les en même temps.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module MicrosoftTeams
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Voici les commandes de tous les services *à l’exception de Exchange Online* dans un bloc unique lors de l’utilisation du Module Microsoft Azure Active Directory pour le module Windows PowerShell. Spécifiez le nom de votre hôte de domaine et le nom d’utilisateur principal (UPN) pour la connexion, puis exécutez-les en même temps.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$credential = Get-Credential -UserName $acctName
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module MicrosoftTeams
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
Import-Module ExchangeOnlineManagement
Connect-IPPSSession -UserPrincipalName $acctName
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```
## <a name="connection-steps-when-using-multi-factor-authentication"></a>Étapes de connexion lors de l’utilisation de l’authentification multifacteur

### <a name="azure-active-directory-powershell-for-graph-module"></a>Module Azure Active Directory PowerShell pour Graph

Voici toutes les commandes dans un bloc unique pour vous connecter à plusieurs services Microsoft 365 *à l’exception du Centre de Sécurité &amp;de conformité* lors de l’utilisation de l’authentification multifacteur à l’aide de Azure Active Directory PowerShell pour le module Graph.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
Import-Module MicrosoftTeams
$sfboSession = New-CsOnlineSession
Import-PSSession $sfboSession
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```
Voici toutes les commandes dans un bloc unique pour vous connecter à plusieurs services Microsoft 365 *à l’exception de Exchange Online* avec l’authentification multifacteur lors de l’utilisation de Azure Active Directory PowerShell pour le module Graph.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
Import-Module MicrosoftTeams
$sfboSession = New-CsOnlineSession
Import-PSSession $sfboSession
#Security & Compliance Center
Import-Module ExchangeOnlineManagement
Connect-IPPSSession -UserPrincipalName $acctName
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```
### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module"></a>Module Microsoft Azure Active Directory pour module Windows PowerShell

Voici toutes les commandes dans un bloc unique pour vous connecter à plusieurs services Microsoft 365 *à l’exception du Centre de Sécurité &amp;de conformité* avec l’authentification multifacteur à l’aide du Module Microsoft Azure Active Directory pour le module Windows PowerShell.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
Import-Module MicrosoftTeams
$sfboSession = New-CsOnlineSession
Import-PSSession $sfboSession
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```
Voici toutes les commandes dans un bloc unique pour vous connecter à plusieurs services Microsoft 365 *à l’exception de Exchange Online* lors de l’utilisation de l’authentification multifacteur avec le Module Microsoft Azure Active Directory pour le module Windows PowerShell.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
Import-Module MicrosoftTeams
$sfboSession = New-CsOnlineSession
Import-PSSession $sfboSession
#Security & Compliance Center
Import-Module ExchangeOnlineManagement
Connect-IPPSSession -UserPrincipalName $acctName
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

## <a name="close-the-powershell-window"></a>Fermer la fenêtre PowerShell

Pour fermer la fenêtre PowerShell, exécutez cette commande afin de supprimer les sessions actives de Skype Entreprise Online, SharePoint Online et Teams :
  
```powershell
Remove-PSSession $sfboSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="see-also"></a>Voir aussi

- [Connexion à Microsoft 365 à l’aide de PowerShell](connect-to-microsoft-365-powershell.md)
- [Gérer SharePoint Online avec PowerShell](manage-sharepoint-online-with-microsoft-365-powershell.md)
- [Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
