---
title: Gérer les paramètres d’accès aux appareils dans Mobilité et sécurité de base
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: Pour les appareils que vous ne pouvez pas gérer avec La mobilité et la sécurité de base, bloquez Exchange ActiveSync’accès de l’application à la messagerie électronique et utilisez Azure AD PowerShell pour obtenir des détails sur les appareils d’organisation.
ms.openlocfilehash: 22b4afd36043c10b093e3afaf6ff76f337ad5a7d
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68190526"
---
# <a name="manage-device-access-settings-in-basic-mobility-and-security"></a>Gérer les paramètres d’accès aux appareils dans Mobilité et sécurité de base

Si vous utilisez la mobilité et la sécurité de base, il peut y avoir des appareils que vous ne pouvez pas gérer avec la mobilité et la sécurité de base. Si c’est le cas, vous devez bloquer Exchange ActiveSync’accès de l’application à la messagerie Microsoft 365 pour les appareils mobiles qui ne sont pas pris en charge par mobilité et sécurité de base. Cela permet de sécuriser les informations de votre organisation sur d’autres appareils.

Procédez comme suit :

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.

2. Dans votre navigateur, tapez : <https://protection.office.com/>.

    > [!IMPORTANT]
    > S’il s’agit de la première fois que vous utilisez la mobilité et la sécurité de base pour Microsoft 365 Business Standard, [activez-la ici : Activer la sécurité et la mobilité de base](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). Une fois que vous l’avez activé, gérez vos appareils avec [Office 365 Sécurité & Conformité](https://protection.office.com/).

3. Accédez aux stratégies d’appareil de **gestion des** \> appareils de **protection contre la** \> perte de données **, puis** sélectionnez **Gérer les paramètres d’accès aux appareils à l’échelle de l’organisation**.

4. Sélectionnez **Access**.

    :::image type="content" source="../../media/basic-mobility-security/basic-mobility-access.png" alt-text="Case à cocher Mobilité et sécurité de base pour bloquer l’accès.":::

5. Sélectionnez **Enregistrer**.

Pour savoir quels appareils la mobilité et la sécurité de base prennent en charge, consultez [Fonctionnalités de mobilité et de sécurité de base](capabilities.md).

## <a name="get-details-about-basic-mobility-and-security-managed-devices"></a>Obtenir des détails sur les appareils gérés par Mobilité et sécurité de base

En outre, vous pouvez utiliser Azure AD PowerShell pour obtenir des détails sur les appareils de votre organisation que vous avez configurés pour la mobilité et la sécurité de base.

Voici une répartition des détails de l’appareil disponibles.

|Détails|Éléments à rechercher dans PowerShell|
|---|---|
|L’appareil est inscrit à Basic Mobility and Security. Pour plus d’informations, consultez [Inscrire votre appareil mobile à l’aide de mobilité et de sécurité de base](enroll-your-mobile-device.md)|La valeur du paramètre *isManaged* est :<br/>**True**= l’appareil est inscrit.<br/>**False**= l’appareil n’est pas inscrit.|
|L’appareil est conforme aux stratégies de sécurité de votre appareil. Pour plus d’informations, consultez [Créer des stratégies de sécurité d’appareil](create-device-security-policies.md)|La valeur du paramètre *isCompliant* est :<br/>**True** = l’appareil est conforme aux stratégies.<br/>**False** = l’appareil n’est pas conforme aux stratégies.|

:::image type="content" source="../../media/basic-mobility-security/bms-7-powershell-parameters.png" alt-text="Paramètres PowerShell de mobilité et de sécurité de base.":::

> [!NOTE]
> Les commandes et les scripts qui suivent retournent également des détails sur les appareils gérés par [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

Voici quelques éléments que vous devez configurer pour exécuter les commandes et les scripts qui suivent :

### <a name="step-1-download-and-install-the-azure-active-directory-module-for-windows-powershell"></a>Étape 1 : Télécharger et installer le module Azure Active Directory pour Windows PowerShell

Pour plus d’informations sur ces étapes, consultez [Se connecter à Microsoft 365 avec PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell).

1. Accédez à [Microsoft Online Services Sign-In Assistant for IT Professionals RTWl](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi) et **sélectionnez Télécharger pour Microsoft Online Services Sign-in Assistant**.

2. Téléchargez et installez le Module Microsoft Azure Active Directory pour Windows PowerShell en procédant comme suit :

    1. Ouvrez une invite de commandes PowerShell au niveau de l’administrateur.

    2. Exécutez la commande `Install-Module MSOnline`.

    3. Si vous êtes invité à installer le fournisseur NuGet, tapez O, puis appuyez sur Entrée.

    4. Si vous êtes invité à installer le module à partir de PSGallery, tapez O, puis appuyez sur Entrée.

    5. Après l’installation, fermez la fenêtre de commande PowerShell.

### <a name="step-2-connect-to-your-microsoft-365-subscription"></a>Étape 2 : Se connecter à votre abonnement Microsoft 365

1. Dans le module Windows Azure Active Directory pour Windows PowerShell, exécutez la commande suivante.

   ```powershell
   $UserCredential = Get-Credential
   ```

2. Dans la boîte de dialogue Windows PowerShell Demande d’informations d’identification, tapez le nom d’utilisateur et le mot de passe de votre compte d’administrateur général Microsoft 365, puis sélectionnez **OK**.

3. Exécutez la commande suivante :

   ```powershell
   Connect-MsolService -Credential $UserCredential
   ```

### <a name="step-3-make-sure-youre-able-to-run-powershell-scripts"></a>Étape 3 : Vérifier que vous êtes en mesure d’exécuter des scripts PowerShell

> [!NOTE]
> Vous pouvez ignorer cette étape si vous êtes déjà configuré pour exécuter des scripts PowerShell.

Pour exécuter le script Get-MsolUserDeviceComplianceStatus.ps1, vous devez activer l’exécution de scripts PowerShell.

1. Dans votre Bureau Windows, **sélectionnez Démarrer, puis tapez** Windows PowerShell. Cliquez avec le bouton droit sur Windows PowerShell, puis sélectionnez **Exécuter en tant qu’administrateur**.

2. Exécutez la commande suivante :

   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

3. Lorsque vous y êtes invité, tapez Y, puis appuyez sur Entrée.

#### <a name="run-the-get-msoldevice-cmdlet-to-display-details-for-all-devices-in-your-organization"></a>Exécutez l’applet de commande Get-MsolDevice pour afficher les détails de tous les appareils de votre organisation

1. Ouvrez le Module Microsoft Azure Active Directory pour Windows PowerShell.

2. Exécutez la commande suivante :

   ```powershell
   Get-MsolDevice -All -ReturnRegisteredOwners | Where-Object {$_.RegisteredOwners.Count -gt 0}
   ```

Pour plus d’exemples, consultez [Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939).

### <a name="run-a-script-to-get-device-details"></a>Exécuter un script pour obtenir les détails de l’appareil

Tout d’abord, enregistrez le script sur votre ordinateur.

1. Copiez et collez le texte suivant dans le Bloc-notes.

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

2. Enregistrez-le en tant que fichier de script Windows PowerShell à l’aide de l’extension de fichier .ps1 ; par exemple, Get-MsolUserDeviceComplianceStatus.ps1.

### <a name="run-the-script-to-get-device-information-for-a-single-user-account"></a>Exécuter le script pour obtenir des informations sur l’appareil pour un compte d’utilisateur unique

1. Ouvrez le Module Microsoft Azure Active Directory pour Windows PowerShell.

2. Accédez au dossier dans lequel vous avez enregistré le script. Par exemple, si vous l’avez enregistré dans C:\PS-Scripts, exécutez la commande suivante.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Exécutez la commande suivante pour identifier l’utilisateur pour lequel vous souhaitez obtenir les détails de l’appareil. Cet exemple obtient des détails pour bar@example.com.

   ```powershell
   $u = Get-MsolUser -UserPrincipalName bar@example.com
   ```

4. Exécutez la commande suivante pour lancer le script.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Les informations sont exportées vers votre Bureau Windows en tant que fichier CSV. Vous pouvez utiliser des paramètres supplémentaires pour spécifier le nom de fichier et le chemin d’accès du fichier CSV.

### <a name="run-the-script-to-get-device-information-for-a-group-of-users"></a>Exécuter le script pour obtenir des informations sur l’appareil pour un groupe d’utilisateurs

1. Ouvrez le Module Microsoft Azure Active Directory pour Windows PowerShell.

2. Accédez au dossier dans lequel vous avez enregistré le script. Par exemple, si vous l’avez enregistré dans C:\PS-Scripts, exécutez la commande suivante.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Exécutez la commande suivante pour identifier le groupe pour lequel vous souhaitez obtenir les détails de l’appareil. Cet exemple obtient des détails pour les utilisateurs du groupe FinanceStaff.

   ```powershell
   $u = Get-MsolGroupMember -SearchString "FinanceStaff" | % { Get-MsolUser -ObjectId $_.ObjectId }
   ```

4. Exécutez la commande suivante pour lancer le script.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Les informations sont exportées vers votre Bureau Windows en tant que fichier CSV. Vous pouvez utiliser des paramètres supplémentaires pour spécifier le nom de fichier et le chemin d’accès du fichier CSV.

## <a name="related-content"></a>Contenu associé

[Microsoft Connect a été mis hors service](/collaborate/connect-redirect)

[Vue d’ensemble de la fonction Mobility + Security de Base](overview.md)

[Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939)