---
title: Obtenir des détails sur les appareils gérés de mobilité et de sécurité de base
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
description: Utilisez Windows PowerShell pour obtenir des détails sur les appareils de sécurité et de mobilité de base dans votre organisation.
ms.openlocfilehash: 7b041e54d512291163616d3b61973cef989cec5c
ms.sourcegitcommit: 2179abfe0b7a8bea917eb1c1057ed3795bdf91e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "47336851"
---
# <a name="get-details-about-basic-mobility-and-security-managed-devices"></a>Obtenir des détails sur les appareils gérés de mobilité et de sécurité de base

Cet article vous explique comment utiliser Windows PowerShell pour obtenir des détails sur les appareils de votre organisation que vous configurez pour une mobilité et une sécurité de base.

Voici une répartition des détails du périphérique à votre disposition.

|**Detail**|**Éléments à rechercher dans PowerShell**|
|:----------------|:------------------------------------------------------------------------------|
|L’appareil est intégré à la sécurité et à la mobilité de base. Pour plus d’informations, consultez [la rubrique inscrire votre appareil mobile à l’aide de la sécurité et de la sécurité de base](enroll-your-mobile-device-using-basic-mobility-and-security.md)|La valeur du paramètre *isManaged*   est la suivante :<br/>**True**= l’appareil est l’enregistrement.<br/>**False**= l’appareil n’est pas inscrire. |
|L’appareil est conforme aux stratégies de sécurité de votre appareil. Pour plus d’informations, consultez la rubrique [créer des stratégies de sécurité des appareils](create-device-security-policies-in-basic-mmobility-and-security.md)|La valeur du paramètre *isCompliant*   est la suivante :<br/>**True**   = l’appareil est conforme aux stratégies.<br/>**Valeur false**   = le périphérique n’est pas compatible avec les stratégies.|

:::image type="content" source="../../media/basic-mobility-security/bms-7-powershell-parameters.png" alt-text="Paramètres PowerShell de la sécurité et de la mobilité de base":::

>[!NOTE]
>Les commandes et les scripts de cet article renvoient également des détails sur les appareils gérés par [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

## <a name="before-you-begin"></a>Avant de commencer

Vous devez configurer plusieurs éléments pour exécuter les commandes et les scripts décrits dans cet article.

### <a name="step-1-download-and-install-the-azure-active-directory-module-for-windows-powershell"></a>Étape 1 : Télécharger et installer le module Azure Active Directory pour Windows PowerShell

Pour plus d’informations sur ces étapes, voir [se connecter à Microsoft 365 avec PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).

1. Accédez à [l’Assistant de connexion Microsoft Online Services pour les professionnels de l’informatique RTWl](https://www.microsoft.com/download/details.aspx?id=41950)   et sélectionnez  **Télécharger pour l’Assistant de connexion Microsoft Online Services**.   

2. Téléchargez et installez le Module Microsoft Azure Active Directory pour Windows PowerShell en procédant comme suit :   

    1. Ouvrez une invite de commandes PowerShell au niveau de l’administrateur.  

    2. Exécutez la commande Install-Module MSOnline.
    
    3. Si vous êtes invité à installer le fournisseur NuGet, tapez O, puis appuyez sur Entrée.   

    4. Si vous êtes invité à installer le module à partir de PSGallery, tapez O, puis appuyez sur Entrée.   

    5. Après l’installation, fermez la fenêtre de commande PowerShell.
    
### <a name="step-2-connect-to-your-microsoft-365-subscription"></a>Étape 2 : Connectez-vous à votre abonnement Microsoft 365

1. Dans le module Windows Azure Active Directory pour Windows PowerShell, exécutez la commande suivante.  

    $UserCredential = Get-Credential

2. Dans la boîte de dialogue demande d’informations d’identification Windows PowerShell, tapez le nom d’utilisateur et le mot de passe de votre compte d’administrateur global Microsoft 365, puis sélectionnez **OK**.
    
3. Exécutez la commande suivante.
    
    Connect-MsolService-Credential $UserCredential

### <a name="step-3-make-sure-youre-able-to-run-powershell-scripts"></a>Étape 3 : vérifier que vous pouvez exécuter des scripts PowerShell

>[!NOTE]
>Vous pouvez ignorer cette étape si vous êtes déjà configuré pour exécuter des scripts PowerShell.

Pour exécuter le script Get-MsolUserDeviceComplianceStatus.ps1, vous devez activer l’exécution des scripts PowerShell.

1. À partir de votre bureau Windows, sélectionnez **Démarrer**, puis tapez Windows PowerShell. Cliquez avec le bouton droit sur Windows PowerShell, puis sélectionnez **exécuter en tant qu’administrateur**.

2. Exécutez la commande suivante.
    
    Set-ExecutionPolicy RemoteSigned

3. Lorsque vous y êtes invité, tapez o, puis appuyez sur entrée.
    
**Exécutez la cmdlet Get-MsolDevice pour afficher les détails de tous les périphériques de votre organisation.**

1. Ouvrez le Module Microsoft Azure Active Directory pour Windows PowerShell.  

2. Exécutez la commande suivante.
    
    Get-MsolDevice-All-ReturnRegisteredOwners | Where-Object {$ _. RegisteredOwners. Count-gt 0}

Pour obtenir plus d’exemples, consultez la rubrique  [Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=841721).

## <a name="run-a-script-to-get-device-details"></a>Exécuter un script pour obtenir des détails sur les périphériques

Tout d’abord, enregistrez le script sur votre ordinateur.

1. Copiez et collez le texte suivant dans le bloc-notes.  

2.  paramètres
    

3.  [PSObject []] $users = @ (),
    

4.  [Commutateur] $export,
    

5.  [String] $exportFileName = "UserDeviceComplianceStatus_" + (get-date-format "yyMMdd_HHMMss") + ". csv",
    

6.  [String] $exportPath = [Environment] :: GetFolderPath ("Desktop")
    

7.  )
    

9.  [System. Collections. IDictionary] $script : Schema = @ {
    

11.  DeviceId = ' '
    

12.  DeviceOSType = ' '
    

13.  DeviceOSVersion = ' '
    

14.  DeviceTrustLevel = ' '
    

15.  DisplayName = ' '
    

16.  IsCompliant = ' '
    

17.  IsManaged = ' '
    

18.  ApproximateLastLogonTimestamp = ' '
    

19.  DeviceObjectId = ' '
    

20.  RegisteredOwnerUpn = ' '
    

21.  RegisteredOwnerObjectId = ' '
    

22.  RegisteredOwnerDisplayName = ' '
    

23.  }
    

25.  fonction createResultObject
    

26.  {
    

28.  [PSObject] $resultObject = New-Object-TypeName PSObject-Property $script : Schema
    

30.  renvoyer $resultObject
    

31.  }
    

33.  Si ($users. Nombre-EQ 0)
    

34.  {
    

35.  $users = Get-MsolUser
    

36.  }
    

38.  [PSObject []] $result = foreach ($u dans $users)
    

39.  {
    

41.  [PSObject] $devices = Get-msoldevice-RegisteredOwnerUpn $u. UserPrincipalName
    

42.  foreach ($d dans $devices)
    

43.  {
    

44.  [PSObject] $deviceResult = createResultObject
    

45.  $deviceResult. DeviceId = $d. DeviceId
    

46.  $deviceResult. DeviceOSType = $d. DeviceOSType
    

47.  $deviceResult. DeviceOSVersion = $d. DeviceOSVersion
    

48.  $deviceResult. DeviceTrustLevel = $d. DeviceTrustLevel
    

49.  $deviceResult. DisplayName = $d. DisplayName
    

50.  $deviceResult. IsCompliant = $d. GraphDeviceObject. IsCompliant
    

51.  $deviceResult. IsManaged = $d. GraphDeviceObject. IsManaged
    

52.  $deviceResult. DeviceObjectId = $d. ObjectId
    

53.  $deviceResult. RegisteredOwnerUpn = $u. UserPrincipalName
    

54.  $deviceResult. RegisteredOwnerObjectId = $u. ObjectId
    

55.  $deviceResult. RegisteredOwnerDisplayName = $u. DisplayName
    

56.  $deviceResult. ApproximateLastLogonTimestamp = $d. ApproximateLastLogonTimestamp
    

58.  $deviceResult
    

59.  }
    

61.  }
    

63.  Si ($export)
    

64.  {
    

65.  $result | Export-CSV-Path ($exportPath + " \" + $exportFileName)-NoTypeInformation
    

66.  }
    

67.  Else
    

68.  {
    

69.  $result
    

70.  }
    

71.  Enregistrez-le en tant que fichier de script Windows PowerShell à l’aide de l’extension de fichier. ps1 ; par exemple, Get-MsolUserDeviceComplianceStatus.ps1.   

## <a name="run-the-script-to-get-device-information-for-a-single-user-account"></a>Exécuter le script pour obtenir des informations sur le périphérique pour un compte d’utilisateur unique

1. Ouvrez le Module Microsoft Azure Active Directory pour Windows PowerShell.
    
2. Accédez au dossier dans lequel vous avez enregistré le script. Par exemple, si vous l’avez enregistré dans C:\PS-Scripts, exécutez la commande suivante.
    
    CD C:\PS-Scripts

3. Exécutez la commande suivante pour identifier l’utilisateur pour lequel vous souhaitez obtenir des détails sur les périphériques. Cet exemple obtient les détails pour bar@example.com.
    
    $u = get-MsolUser-UserPrincipalName bar@example.com

4. Exécutez la commande suivante pour lancer le script.

    .\Get-MsolUserDeviceComplianceStatus.ps1-user $u-Export

Les informations sont exportées vers votre bureau Windows sous forme de fichier CSV. Vous pouvez utiliser des paramètres supplémentaires pour spécifier le nom de fichier et le chemin d’accès au fichier CSV.

## <a name="run-the-script-to-get-device-information-for-a-group-of-users"></a>Exécuter le script pour obtenir des informations sur le périphérique pour un groupe d’utilisateurs

1. Ouvrez le Module Microsoft Azure Active Directory pour Windows PowerShell.
    
2. Accédez au dossier dans lequel vous avez enregistré le script. Par exemple, si vous l’avez enregistré dans C:\PS-Scripts, exécutez la commande suivante.   

    CD C:\PS-Scripts

3. Exécutez la commande suivante pour identifier le groupe pour lequel vous souhaitez obtenir des détails sur les périphériques. Cet exemple obtient les détails pour les utilisateurs dans le groupe FinanceStaff. 

    $u = get-MsolGroupMember-SearchString "FinanceStaff" | % {Get-MsolUser-ObjectId $ _. ObjectID

4. Exécutez la commande suivante pour lancer le script.   

    .\Get-MsolUserDeviceComplianceStatus.ps1-user $u-Export

Les informations sont exportées vers votre bureau Windows sous forme de fichier CSV. Vous pouvez utiliser des paramètres supplémentaires pour spécifier le nom de fichier et le chemin d’accès au fichier CSV.

## <a name="related-topics"></a>Voir aussi

[Microsoft Connect a été retiré](https://docs.microsoft.com/collaborate/connect-redirect)

[Vue d’ensemble de la sécurité et de la mobilité de base](overview-of-basic-mobility-and-security-for-microsoft-365.md)

[Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=841721)