---
title: Connexion à Microsoft 365 à l’aide de PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- scotvorg
- Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Connectez-vous à votre client Microsoft 365 à l’aide de PowerShell pour Microsoft 365 afin d’effectuer des tâches de Centre d’administration à partir de la ligne de commande.
ms.openlocfilehash: 0192ed18c1c99cd08008570ce4b97a558621761f
ms.sourcegitcommit: edc9d4dec92ca81cff39bbf9590f1cd3a75ec436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2022
ms.locfileid: "68484344"
---
# <a name="connect-to-microsoft-365-with-powershell"></a>Connexion à Microsoft 365 à l’aide de PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

PowerShell pour Microsoft 365 vous permet de gérer vos paramètres Microsoft 365 à partir de la ligne de commande. Pour vous connecter à PowerShell, installez le logiciel requis, puis connectez-vous à votre organisation Microsoft 365.

Il existe deux versions du module PowerShell que vous utilisez pour vous connecter à Microsoft 365 et administrer les comptes d’utilisateurs, les groupes et les licences:

- Azure Active Directory PowerShell pour Graph dont les cmdlets incluent *AzureAD* dans leur nom
- Module Microsoft Azure Active Directory pour Windows PowerShell, dont les cmdlets incluent *Msol* dans leur nom

À l’heure actuelle, le module Azure Active Directory PowerShell pour Graph ne remplace pas complètement la fonctionnalité du Module Microsoft Azure Active Directory pour Windows PowerShell pour l’administration des utilisateurs, des groupes et des licences. Dans certains cas, vous devez utiliser les deux versions. Vous pouvez installer en toute sécurité les deux versions sur le même ordinateur.

>[!Note]
>Vous pouvez également vous connecter à [Azure Cloud Shell](#connect-with-the-azure-cloud-shell) à partir du Centre d’administration Microsoft 365.
>


## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

>[!NOTE]
> Le module Azure Active Directory est remplacé par le SDK PowerShell Microsoft Graph. Vous pouvez utiliser le kit de développement logiciel (SDK) PowerShell Microsoft Graph pour accéder à toutes les API Microsoft Graph. Pour plus d’informations, consultez [Démarrage avec le kit de développement logiciel (SDK) PowerShell Microsoft Graph](/powershell/microsoftgraph/get-started).

**Système d’exploitation**

You must use a 64-bit version of Windows. Support for the 32-bit version of the Microsoft Azure Active Directory Module for Windows PowerShell ended in 2014.

Vous pouvez utiliser les versions de Windows suivantes :
    
  - Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1

>[!Note]
>Pour Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 et Windows Server 2008 R2 SP1, téléchargez et installez [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).

**PowerShell**

- Pour le module Azure Active Directory PowerShell pour Graph, vous devez utiliser PowerShell version 5.1.

- For the Microsoft Azure Active Directory Module for Windows PowerShell module, you must use PowerShell version 5.1 or later, up to PowerShell version 6. You can't use PowerShell version 7.
       
>[!Note]
>These procedures are intended for users who are members of a Microsoft 365 admin role. For more information, see [About admin roles](../admin/add-users/about-admin-roles.md).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Se connecter avec le module PowerShell Azure Active Directory pour Graph

Le nom des cmdlets du module Azure Active Directory PowerShell pour Graph contient la chaîne de caractères *AzureAD*. Vous pouvez installer le module [Azure Active Directory PowerShell pour Graph](/powershell/azure/active-directory/install-adv2) ou [Azure PowerShell](/powershell/azure/install-az-ps).

Si vous devez utiliser les nouvelles cmdlets dans le module Microsoft Azure Active Directory PowerShell pour Graph, veuillez suivre cette procédure pour installer le module et vous connecter à votre abonnement Microsoft 365.

> [!Note]
> Pour les informations sur la prise en charge de différentes versions de Windows, consultez le [Module Microsoft Azure Active Directory PowerShell pour Graph](/powershell/azure/active-directory/install-adv2).

### <a name="step-1-install-the-required-software"></a>Étape 1 : installez le logiciel requis

Ces étapes ne sont requises qu’une fois sur votre ordinateur. Mais vous devrez peut-être mettre à jour le logiciel régulièrement.
  
1. Ouvrez une fenêtre d’invite de commandes Windows PowerShell.
    
2. Ensuite, exécutez la commande suivante :
    
    ```powershell
    Install-Module -Name AzureAD
    ```

  Par défaut, la galerie PowerShell (PSGallery) n'est pas configurée comme un référentiel de confiance pour **PowerShellGet** . La première fois que vous utilisez la PSGallery, vous verrez le message suivant :

```console
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the `Set-PSRepository` cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Répondez **Oui** ou **Oui à Tout** pour continuer l'installation.

3.  Exécutez cette commande pour importer le module :
    
    ```powershell
    Import-Module  AzureAD
    ```
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>Étape 2 : connectez-vous à Azure AD avec votre abonnement Microsoft 365

To connect to Azure Active Directory (Azure AD) for your Microsoft 365 subscription with an account name and password or with multi-factor authentication, run one of these commands from a Windows PowerShell command prompt. (It doesn't have to be elevated.)

| Office 365 dans le cloud | Commande |
|:-------|:-----|
| Office 365 dans le monde (+GCC) | `Connect-AzureAD` |
| Office 365 géré par 21 ViaNet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Allemagne | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 U.S. Government DoD et Office 365 U.S. Government GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

Dans la boîte de dialogue **Connectez-vous à votre compte**, tapez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Microsoft 365, puis sélectionnez **OK**.

Si vous utilisez une authentification multifacteur, suivez les instructions pour fournir des informations d’authentification supplémentaires telles que le code de vérification.

Une fois connecté, vous pouvez utiliser les cmdlets du [module Azure Active Directory PowerShell pour Graph](/powershell/module/azuread).

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Se connecter au Module Microsoft Azure Active Directory pour Windows PowerShell

>[!Note]
>Les cmdlets du Module Microsoft Azure Active Directory pour Windows PowerShell ont *MSol* dans leur nom.

PowerShell version 7 et ultérieures ne prennent pas en charge le Module Microsoft Azure Active Directory pour Windows PowerShell et les cmdlets incluant *Msol* dans leur nom. Pour PowerShell version 7 et ultérieures, vous devez utiliser le SDK Microsoft Graph PowerShell.

PowerShell Core doesn't support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with *Msol* in their name. Run these cmdlets from Windows PowerShell.
    
### <a name="step-1-install-the-required-software"></a>Étape 1 : installez le logiciel requis

Ces étapes ne sont requises qu’une fois sur votre ordinateur. Mais vous devrez peut-être mettre à jour le logiciel régulièrement.
  
1.  Si vous n’exécutez pas Windows 10, installez la version 32 bits de l’Assistant de Connexion Microsoft Online Services : [Assistant de connexion Microsoft Online Services pour les professionnels des Technologies de l'Information RTW](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi).
    
2. Installez le Module Microsoft Azure Active Directory pour Windows PowerShell en suivant ces étapes:
    
   1. Ouvrez une invite de commandes Windows PowerShell avec élévation de privilèges (exécutez Windows PowerShell en tant qu’administrateur).
   1.  Exécutez la commande **Install-Module MSOnline**.
   1. Si vous êtes invité à installer le fournisseur NuGet, tapez **Y**, puis appuyez sur Entrée.
   1. Si vous êtes invité à installer le module à partir de PSGallery, tapez **Y**, puis appuyez sur Entrée.
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>Étape 2 : connectez-vous à Azure AD avec votre abonnement Microsoft 365

To connect to Azure AD for your Microsoft 365 subscription with an account name and password or with multi-factor authentication, run one of these commands from a Windows PowerShell command prompt. (It doesn't have to be elevated.)

| Office 365 dans le cloud | Commande |
|:-------|:-----|
| Office 365 dans le monde (+GCC) | `Connect-MsolService` |
| Office 365 géré par 21 ViaNet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Allemagne | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 U.S. Government DoD et Office 365 U.S. Government GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

Dans la boîte de dialogue **Connectez-vous à votre compte**, tapez le nom d’utilisateur et le mot de passe de votre compte professionnel ou scolaire Microsoft 365, puis sélectionnez **OK**.

Si vous utilisez une authentification multifacteur, suivez les instructions pour fournir des informations d’authentification supplémentaires telles que le code de vérification.

### <a name="how-do-you-know-it-worked"></a>Vérification du bon fonctionnement

Si vous ne recevez pas de message d’erreur, alors vous vous êtes connecté. Pour effectuer un test rapide, exécutez une cmdlet Microsoft 365 telle que, **Get-MsolUser**, et consultez les résultats.
  
Si vous recevez un message d’erreur, vérifiez les problèmes suivants:
  
- **A common problem is an incorrect password**. Run [Step 2](#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) again, and pay close attention to the user name and password that you enter.
    
- **The Microsoft Azure Active Directory Module for Windows PowerShell requires that Microsoft .NET Framework 3.5.* x* is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*). But backward compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following articles:
    
  - Pour Windows Server 2012 ou Windows Server 2012 R2, consultez [Activer .NET Framework 3.5 en utilisant l’Assistant Ajout de Roles et de Fonctionnalités](/previous-versions/windows/it-pro/windows-8.1-and-8/dn482071(v=win.10)).
    
  - For Windows 7 or Windows Server 2008 R2, consultez [Vous ne pouvez pas ouvrir le Module Azure Active Directory pour Windows PowerShell](/troubleshoot/azure/active-directory/cant-open-aad-module-powershell).

  - Pour Windows 10, Windows 8.1 et Windows 8, consultez [Installer .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8](/dotnet/framework/install/dotnet-35-windows-10).

  
- **Votre version du Module Microsoft Azure Active Directory pour Windows PowerShell est peut-être obsolète.** Pour vérifier cela, exécutez la commande suivante dans PowerShell pour Microsoft 365 ou le Module Microsoft Azure Active Directory pour Windows PowerShell :
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Si le numéro de version renvoyé est inférieur à la valeur *1.0.8070.2*, désinstallez le Module Microsoft Azure Active Directory pour Windows PowerShell, puis installez-le à partir de [l’Etape 1](#step-1-install-the-required-software) ci-dessus.

- **Si un message d’erreur de connexion s’affiche**, consultez [Erreur « Connect-MsolService: Une exception de type a été levée »](/office365/troubleshoot/active-directory/connect-msoservice-throw-exception).
    
- **Si vous recevez un message d’erreur «Get-Item : Chemin introuvable»**, exécutez cette commande:


   ```powershell
     (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
   ```

## <a name="connect-with-the-azure-cloud-shell"></a>Se connecter à Azure Cloud Shell

To connect with and use the Azure Cloud Shell from the Microsoft 365 admin center, select the PowerShell window icon from the upper-right corner of the task bar. In the **Welcome to Azure Cloud Shell** pane, select **PowerShell**.

Vous aurez besoin d’un abonnement Azure actif pour votre organisation lié à votre abonnement Microsoft 365. Si vous n’en avez pas encore, vous pouvez en créer un. Une fois que vous disposez d’un abonnement Azure, une fenêtre PowerShell s’ouvre à partir de laquelle vous pouvez exécuter des commandes et des scripts PowerShell.

Pour plus d’informations, consultez [Azure Cloud Shell](/azure/cloud-shell/overview).



## <a name="see-also"></a>Voir aussi

- [Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
- [Connexion à tous les services Microsoft 365 dans une seule fenêtre Windows PowerShell](connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window.md)
