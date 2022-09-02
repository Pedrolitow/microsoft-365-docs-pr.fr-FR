---
title: Se connecter à tous les services Microsoft 365 dans une seule fenêtre PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/23/2021
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Résumé : se connecter à tous les services Microsoft 365 dans une seule fenêtre PowerShell.'
ms.openlocfilehash: 67ee0831a0d78a971982f75653ca49e760e61692
ms.sourcegitcommit: 62368e5a48e569c8e475b07d194d7d8ff7d167ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67560370"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-powershell-window"></a>Se connecter à tous les services Microsoft 365 dans une seule fenêtre PowerShell

Lorsque vous utilisez PowerShell pour gérer Microsoft 365, plusieurs sessions PowerShell peuvent être ouvertes en même temps. Vous pouvez disposer de différentes fenêtres PowerShell pour gérer les comptes d’utilisateur, SharePoint Online, Exchange Online, Microsoft Teams, les fonctionnalités de Microsoft Defender pour Office 365 (sécurité) et les fonctionnalités de conformité Microsoft Purview.

Ce scénario n’est pas optimal pour gérer Microsoft 365, car vous ne pouvez pas échanger de données entre ces fenêtres pour effectuer une gestion interservices. Cet article explique comment utiliser une seule instance de PowerShell pour gérer les comptes Microsoft 365, Exchange Online, SharePoint Online, Microsoft Teams et les fonctionnalités de conformité de Defender pour Office 365 Microsoft Purview.

>[!Note]
>Cet article contient actuellement uniquement les commandes permettant de se connecter au cloud (+GCC) dans le monde entier. Notes fournit des liens vers des articles pour la connexion aux autres clouds Microsoft 365.

## <a name="before-you-begin"></a>Avant de commencer

Avant de pouvoir gérer l’ensemble de Microsoft 365 à partir d’une seule instance de PowerShell, tenez compte des conditions préalables suivantes :

- Le compte professionnel ou scolaire Microsoft 365 que vous utilisez doit être membre du rôle d’administrateur Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../admin/add-users/about-admin-roles.md). Cette condition est requise pour PowerShell, pour Microsoft 365, mais pas nécessairement pour tous les autres services Microsoft 365.

- Vous pouvez utiliser les versions 64 bits de Windows suivantes :
  - Windows 11
  - Windows 10
  - Windows 8.1 ou Windows 8
  - Windows Server 2019
  - Windows Server 2016
  - Windows Server 2012 R2 ou Windows Server 2012
  - Windows 7 Service Pack 1 (SP1)*
  - Windows Server 2008 R2 SP1*

    \* Vous devez installer Microsoft .NET Framework 4,5.*x* puis Windows Management Framework 3,0 ou 4,0. Pour plus d’informations, consultez [Windows Management Framework](/powershell/scripting/windows-powershell/wmf/overview).

- Vous devez installer les modules requis pour Azure Active Directory (Azure AD), Exchange Online, Defender pour Office 365, la conformité Microsoft Purview, SharePoint Online et Teams :

  - [Azure Active Directory V2](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
  - [Module Teams PowerShell](/microsoftteams/teams-powershell-overview)
  - [Echange en ligne PowerShell V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exchange-online-powershell-v2-module)
  - [Aperçu de Teams PowerShell](/microsoftteams/teams-powershell-overview)

- PowerShell doit être configuré pour exécuter des scripts signés pour Exchange Online, Defender pour Office 365 et la conformité Microsoft Purview. Exécutez cette commande dans une session PowerShell élevée (une session PowerShell que vous **Exécutez en tant qu’administrateur**).

   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

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

   > [!NOTE]
   > PowerShell Core ne prend pas en charge le Module Microsoft Azure Active Directory pour Windows PowerShell et les cmdlets ayant *Msol* dans leur nom. Vous devez exécuter ces cmdlets à partir de PowerShell.

4. Exécutez ces commandes pour vous connecter à SharePoint Online. Spécifiez le nom de l’organisation de votre domaine. Par exemple, pour « litwareinc\.onmicrosoft.com », la valeur nom de l’organisation est « litwareinc ».

   ```powershell
   $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
   Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
   Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $Credential
   ```

5. Exécutez ces commandes pour vous connecter à Exchange Online.

   ```powershell
   Import-Module ExchangeOnlineManagement
   Connect-ExchangeOnline -ShowProgress $true
   ```

   > [!Note]
   > Si vous souhaitez vous connecter à Exchange Online pour les clouds Microsoft 365 autres que Worldwide, veuillez consulter la rubrique [Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

6. Exécutez ces commandes pour vous connecter à l’interface PowerShell Sécurité et conformité.

   ```powershell
   $acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
   Connect-IPPSSession -UserPrincipalName $acctName
   ```

   > [!NOTE]
   > Pour vous connecter à l’interface PowerShell Sécurité et conformité pour les clouds Microsoft 365 autres que mondiaux, voir [Se connecter à l’interface PowerShell Sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

7. Exécutez ces commandes pour vous connecter au PowerShell Teams.

   ```powershell
   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
   ```

   > [!NOTE]
   > Le connecteur Skype Entreprise Online fait actuellement partie du dernier module PowerShell Teams. Si vous utilisez la version publique la plus récente de PowerShell Teams, vous n’avez pas besoin d’installer le connecteur Skype Entreprise Online.
   >
   > Pour vous connecter aux clouds Microsoft Teams autres *que Worldwide*, consultez [Connect-MicrosoftTeams](/powershell/module/teams/connect-microsoftteams).

### <a name="azure-active-directory-powershell-for-graph-module-when-using-just-a-password"></a>Module Azure Active Directory PowerShell pour Graph lors de l’utilisation d’un mot de passe uniquement

Voici les commandes de tous les services dans un bloc unique lors de l’utilisation du module Azure Active Directory PowerShell pour Graph. Spécifiez le nom de votre hôte de domaine et le nom d’utilisateur principal (UPN) pour la connexion, puis exécutez-les en même temps.

```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$credential = Get-Credential -UserName $acctName -Message "Type the account's password."
#Azure Active Directory
Connect-AzureAD -Credential $credential
#SharePoint Online
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module-when-using-just-a-password"></a>Module Microsoft Azure Active Directory pour Windows PowerShell lors de l’utilisation d’un mot de passe uniquement

Voici les commandes de tous les services dans un bloc unique lors de l’utilisation du module Microsoft Azure Active Directory pour Windows PowerShell. Spécifiez le nom de votre hôte de domaine et le nom d’utilisateur principal (UPN) pour la connexion, puis exécutez-les en même temps.

```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$credential = Get-Credential -UserName $acctName -Message "Type the account's password."
#Azure Active Directory
Connect-MsolService -Credential $credential
#SharePoint Online
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
#Exchange Online
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Étapes de connexion lors de l’utilisation de l’authentification multifacteur

### <a name="azure-active-directory-powershell-for-graph-module-when-using-mfa"></a>Module Azure Active Directory PowerShell pour Graph lors de l’utilisation de l’authentification multifacteur

Voici toutes les commandes dans un bloc unique qui vous permettent de vous connecter à plusieurs services Microsoft 365lors de l’utilisation de l’authentification multifacteur avec le module Azure Active Directory PowerShell pour Graph.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Security & Compliance
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module-when-using-mfa"></a>Module Microsoft Azure Active Directory pour Windows PowerShell lors de l’utilisation de l’authentification multifacteur

Voici toutes les commandes dans un bloc unique qui vous permettent de vous connecter à plusieurs services Microsoft 365 lors de l’utilisation de l’authentification multifacteur avec le module Microsoft Azure Active Directory pour Windows PowerShell.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

## <a name="close-the-powershell-window"></a>Fermer la fenêtre PowerShell

Pour fermer la fenêtre PowerShell, exécutez cette commande pour supprimer les sessions actives de SharePoint Online, de Teams, de Defender pour Office 365 et de la conformité Microsoft Purview :

```powershell
Disconnect-SPOService; Disconnect-MicrosoftTeams; Disconnect-ExchangeOnline
```

## <a name="see-also"></a>Voir aussi

- [Connexion à Microsoft 365 à l’aide de PowerShell](connect-to-microsoft-365-powershell.md)
- [Gérer SharePoint Online avec PowerShell](manage-sharepoint-online-with-microsoft-365-powershell.md)
- [Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
