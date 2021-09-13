---
title: Obtenir des détails sur les appareils gérés par la mobilité et la sécurité de base
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: Utilisez Windows PowerShell pour obtenir des détails sur les périphériques de mobilité et de sécurité de base dans votre organisation.
ms.openlocfilehash: 231eeb87d3f72ca4107c0ee6bef5bd60c713bb3f
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59176867"
---
# <a name="get-details-about-basic-mobility-and-security-managed-devices"></a>Obtenir des détails sur les appareils gérés par la mobilité et la sécurité de base

Cet article vous montre comment utiliser Windows PowerShell pour obtenir des détails sur les appareils de votre organisation que vous avez mis en place pour basic Mobility and Security.

Voici une répartition des détails de l’appareil à votre disposition.

|**Detail**|**Ce qu’il faut rechercher dans PowerShell**|
|:----------------|:------------------------------------------------------------------------------|
|L’appareil est inscrit à Basic Mobility and Security. Pour plus d’informations, voir [Inscrire votre appareil mobile à l’aide de Basic Mobility and Security](enroll-your-mobile-device.md)|La valeur du *paramètre isManaged*   est :<br/>**True**= l’appareil est inscrit.<br/>**False**= l’appareil n’est pas inscrit. |
|L’appareil est conforme aux stratégies de sécurité de votre appareil. Pour plus d’informations, voir [Créer des stratégies de sécurité d’appareil](create-device-security-policies.md)|La valeur du *paramètre isCompliant*   est :<br/>**True**   = l’appareil est conforme aux stratégies.<br/>**False**   = l’appareil n’est pas conforme aux stratégies.|

:::image type="content" source="../../media/basic-mobility-security/bms-7-powershell-parameters.png" alt-text="Paramètres PowerShell de mobilité et de sécurité de base.":::

> [!NOTE]
> Les commandes et les scripts de cet article retournent également des détails sur les appareils gérés [par Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

## <a name="before-you-begin"></a>Avant de commencer

Vous devez configurer plusieurs éléments pour exécuter les commandes et les scripts décrits dans cet article.

### <a name="step-1-download-and-install-the-azure-active-directory-module-for-windows-powershell"></a>Étape 1 : Télécharger et installer le module Azure Active Directory pour Windows PowerShell

Pour plus d’informations sur ces [étapes, voir Connecter à Microsoft 365 avec PowerShell.](/office365/enterprise/powershell/connect-to-office-365-powershell)

1. Go to [Microsoft Online Services Sign-In Assistant for IT Professionals RTWl](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi)and select Download for Microsoft Online Services    **Sign-in Assistant**.

2. Téléchargez et installez le Module Microsoft Azure Active Directory pour Windows PowerShell en procédant comme suit :

    1. Ouvrez une invite de commandes PowerShell de niveau administrateur.

    2. Exécutez la commande `Install-Module MSOnline`.

    3. Si vous êtes invité à installer le fournisseur NuGet, tapez O, puis appuyez sur Entrée.

    4. Si vous êtes invité à installer le module à partir de PSGallery, tapez O, puis appuyez sur Entrée.

    5. Après l’installation, fermez la fenêtre de commande PowerShell.

### <a name="step-2-connect-to-your-microsoft-365-subscription"></a>Étape 2 : Connecter à votre abonnement Microsoft 365 abonnement

1. Dans le Windows Azure Active Directory module de Windows PowerShell, exécutez la commande suivante.

   ```powershell
   $UserCredential = Get-Credential
   ```

2. Dans la boîte Windows PowerShell demande d’informations d’identification, tapez le nom d’utilisateur et le mot de passe de votre compte Microsoft 365 administrateur global, puis sélectionnez **OK.**

3. Exécutez la commande suivante.

   ```powershell
   Connect-MsolService -Credential $UserCredential
   ```

### <a name="step-3-make-sure-youre-able-to-run-powershell-scripts"></a>Étape 3 : Assurez-vous que vous êtes en mesure d’exécuter des scripts PowerShell

> [!NOTE]
> Vous pouvez ignorer cette étape si vous êtes déjà prêt à exécuter des scripts PowerShell.

Pour exécuter le script Get-MsolUserDeviceComplianceStatus.ps1, vous devez activer l’exécution des scripts PowerShell.

1. À partir de Windows bureau, sélectionnez **Démarrer,** puis tapez Windows PowerShell. Cliquez avec le bouton Windows PowerShell, puis sélectionnez **Exécuter en tant qu’administrateur.**

2. Exécutez la commande suivante.

   ```powershell
   Set-ExecutionPolicy  RemoteSigned
   ```

3. Lorsque vous y invitez, tapez Y, puis appuyez sur Entrée.

#### <a name="run-the-get-msoldevice-cmdlet-to-display-details-for-all-devices-in-your-organization"></a>Exécutez la cmdlet Get-MsolDevice pour afficher les détails de tous les appareils de votre organisation

1. Ouvrez le Module Microsoft Azure Active Directory pour Windows PowerShell.

2. Exécutez la commande suivante.

   ```powershell
   Get-MsolDevice -All -ReturnRegisteredOwners | Where-Object {$_.RegisteredOwners.Count -gt 0}
   ```

Pour plus d’exemples,  [voir Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939).

## <a name="run-a-script-to-get-device-details"></a>Exécuter un script pour obtenir les détails de l’appareil

Tout d’abord, enregistrez le script sur votre ordinateur.

1. Copiez et collez le texte suivant dans Bloc-notes.

   ```powershell
   param (
   [PSObject[]]$users = @(),
   [Switch]$export,
   [String]$exportFileName = "UserDeviceComplianceStatus_" + (Get-Date -Format "yyMMdd_HHMMss") + ".csv",
   [String]$exportPath = [Environment]::GetFolderPath("Desktop")
   )
   [System.Collections.IDictionary]$script:schema = @{
   DeviceId = ''
   DeviceOSType = ''
   DeviceOSVersion = ''
   DeviceTrustLevel = ''
   DisplayName = ''
   IsCompliant = ''
   IsManaged = ''
   ApproximateLastLogonTimestamp = ''
   DeviceObjectId = ''
   RegisteredOwnerUpn = ''
   RegisteredOwnerObjectId = ''
   RegisteredOwnerDisplayName = ''
   }
   function createResultObject
   {
   [PSObject]$resultObject = New-Object -TypeName PSObject -Property $script:schema
   return $resultObject
   }
   If ($users.Count -eq 0)
   {
   $users = Get-MsolUser
   }
   [PSObject[]]$result = foreach ($u in $users)
   {
   [PSObject]$devices = get-msoldevice -RegisteredOwnerUpn $u.UserPrincipalName
   foreach ($d in $devices)
   {
   [PSObject]$deviceResult = createResultObject
   $deviceResult.DeviceId = $d.DeviceId
   $deviceResult.DeviceOSType = $d.DeviceOSType
   $deviceResult.DeviceOSVersion = $d.DeviceOSVersion
   $deviceResult.DeviceTrustLevel = $d.DeviceTrustLevel
   $deviceResult.DisplayName = $d.DisplayName
   $deviceResult.IsCompliant = $d.GraphDeviceObject.IsCompliant
   $deviceResult.IsManaged = $d.GraphDeviceObject.IsManaged
   $deviceResult.DeviceObjectId = $d.ObjectId
   $deviceResult.RegisteredOwnerUpn = $u.UserPrincipalName
   $deviceResult.RegisteredOwnerObjectId = $u.ObjectId
   $deviceResult.RegisteredOwnerDisplayName = $u.DisplayName
   $deviceResult.ApproximateLastLogonTimestamp = $d.ApproximateLastLogonTimestamp
   $deviceResult
   }
   }
   If ($export)
   {
   $result | Export-Csv -path ($exportPath + "\" + $exportFileName) -NoTypeInformation
   }
   Else
   {
   $result
   }
   ```

2. Enregistrez-le en tant que fichier Windows PowerShell script à l’aide de l’extension de .ps1 ; par exemple, Get-MsolUserDeviceComplianceStatus.ps1.

## <a name="run-the-script-to-get-device-information-for-a-single-user-account"></a>Exécutez le script pour obtenir des informations sur l’appareil d’un seul compte d’utilisateur

1. Ouvrez le Module Microsoft Azure Active Directory pour Windows PowerShell.

2. Go to the folder where you saved the script. Par exemple, si vous l’avez enregistré dans C:\PS-Scripts, exécutez la commande suivante.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Exécutez la commande suivante pour identifier l’utilisateur pour qui vous souhaitez obtenir les détails de l’appareil. Cet exemple obtient les détails de bar@example.com.

   ```powershell
   $u = Get-MsolUser -UserPrincipalName bar@example.com
   ```

4. Exécutez la commande suivante pour lancer le script.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Les informations sont exportées vers votre bureau Windows en tant que fichier CSV. Vous pouvez utiliser des paramètres supplémentaires pour spécifier le nom de fichier et le chemin d’accès du fichier CSV.

## <a name="run-the-script-to-get-device-information-for-a-group-of-users"></a>Exécuter le script pour obtenir des informations sur l’appareil d’un groupe d’utilisateurs

1. Ouvrez le Module Microsoft Azure Active Directory pour Windows PowerShell.

2. Go to the folder where you saved the script. Par exemple, si vous l’avez enregistré dans C:\PS-Scripts, exécutez la commande suivante.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Exécutez la commande suivante pour identifier le groupe pour qui vous souhaitez obtenir les détails de l’appareil. Cet exemple obtient des détails pour les utilisateurs du groupe FinanceStaff.

   ```powershell
   $u = Get-MsolGroupMember -SearchString "FinanceStaff" | % { Get-MsolUser -ObjectId $_.ObjectId }
   ```

4. Exécutez la commande suivante pour lancer le script.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Les informations sont exportées vers votre bureau Windows en tant que fichier CSV. Vous pouvez utiliser des paramètres supplémentaires pour spécifier le nom de fichier et le chemin d’accès du fichier CSV.

## <a name="related-topics"></a>Rubriques connexes

[Microsoft Connecter été retiré](/collaborate/connect-redirect)

[Vue d’ensemble de la fonction Mobility + Security de Base](overview.md)

[Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939)
