---
title: Activer l’authentification moderne pour Office 2013 sur les appareils Windows
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
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
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7dc1c01a-090f-4971-9677-f1b192d6c910
description: Découvrez comment définir des clés de Registre pour activer l’authentification moderne pour les appareils sur lesquels Microsoft Office 2013 est installé.
ms.openlocfilehash: 8223b2efb88cd29e57353098ab014b76f52251f2
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68629968"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>Activer l’authentification moderne pour Office 2013 sur les appareils Windows

Microsoft Office 2013 sur les ordinateurs Microsoft Windows prend en charge l’authentification moderne. Toutefois, pour l’activer, vous devez configurer les clés de Registre suivantes :

|Clé du Registre|Type|Valeur|
|:---|:---:|:---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\Version|REG_DWORD|1|

> [!NOTE]
> L’authentification moderne est déjà activée dans Office 2016 ou version ultérieure. Vous n’avez pas besoin de définir ces clés de Registre pour les versions ultérieures d’Office.

>[!IMPORTANT]
> L’authentification de base est désactivée pour Exchange Online boîtes aux lettres sur Microsoft 365. Cela signifie que si Outlook 2013 n’est pas configuré pour utiliser l’authentification moderne, il perd la possibilité de se connecter. Pour plus d’informations, consultez [l’authentification de base dans Exchange Online](https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-authentication-deprecation-in-exchange-online-september/ba-p/3609437).

## <a name="software-requirements"></a>Configuration logicielle requise

Pour activer l’authentification multifacteur pour les applications clientes Office 2013, les logiciels suivants doivent être installés (la version répertoriée ci-dessous ou une version ultérieure) selon que vous disposez d’une [installation basée sur un clic](http://howtomicrosoftofficetutorials.blogspot.com/2016/12/plan-for-multi-factor-authentication.html#bk_clicktorun) ou d’une [installation basée sur MSI](http://howtomicrosoftofficetutorials.blogspot.com/2016/12/plan-for-multi-factor-authentication.html#bk_msi).

Pour déterminer si votre installation d’Office est basée sur Démarrer en un clic ou sur MSI :

1.  Démarrez Outlook 2013.
2.  Dans le menu **Fichier** , sélectionnez **Compte Office**.
3.  Pour les installations « Démarrer en un clic » Outlook 2013, un élément **Options de mise à jour** s’affiche. Pour les installations basées sur MSI, aucun élément **Options de mise à jour** ne s’affiche.

      :::image type="content" source="../../security/defender-endpoint/images/office-2013-run-installation.png" alt-text="Capture d’écran d’Office 2013":::

### <a name="click-to-run-installations"></a>Installations démarrer en un clic

Pour les installations « Démarrer en un clic », les fichiers suivants doivent être installés. Si votre version de fichier n’est pas égale ou supérieure à la version de fichier répertoriée, suivez les étapes ci-dessous pour la mettre à jour.

|Nom de fichier|Chemin d'installation sur votre ordinateur|Version du fichier|
|---|---|---|
|MSO.DLL|C:\Program Files\Microsoft Office 15\root\vfs\ProgramFilesCommonx86\Microsoft Shared\OFFICE15\MSO.DLL|15.0.4753.1001|
|Csi. DLLL|CSI.DLL C:\Program Files\Microsoft Office 15\root\office15\csi.dll|15.0.4753.1000|
|Groove.EXE|C:\Program Files\Microsoft Office 15\root\office15\GROOVE.exe|15.0.4763.1000|
|Outlook.exe|C:\Program Files\Microsoft Office 15\root\office15\OUTLOOK.exe|15.0.4753.1002|
|ADAL.DLL|C:\Program Files\Microsoft Office 15\root\vfs\ProgramFilesCommonx86\Microsoft Shared\OFFICE15\ADAL.DLL|1.0.2016.624|
|Iexplore.exe|C:\Program Files\Internet Explorer|Variables|

### <a name="msi-based-installations"></a>Installations basées sur MSI

Pour les installations basées sur MSI, les fichiers suivants doivent être installés. Si votre version de fichier n’est pas égale ou supérieure à la version de fichier répertoriée, utilisez le lien dans l’emplacement où obtenir la colonne de mise à jour pour la mettre à jour.

|Nom de fichier|Chemin d'installation sur votre ordinateur|Où obtenir la mise à jour|Version|
|---|---|---|---|
|MSO.DLL|C:\Program Files\Microsoft Office 15\root\vfs\ProgramFilesCommonx86\Microsoft Shared\OFFICE15\MSO.DLL|[KB3085480](https://support.microsoft.com/en-us/topic/description-of-the-security-update-for-office-2013-september-10-2019-0d171ba2-2eba-a2ca-a54d-c0f568de6bcc)|15.0.4753.1001|
|Csi. DLLL|CSI.DLL C:\Program Files\Microsoft Office 15\root\office15\csi.dll|[KB3172545](https://support.microsoft.com/en-us/topic/july-11-2017-update-for-office-2013-kb3172545-d6b47054-04d5-5154-40ba-3436d1e0efdb)|15.0.4753.1000|
|Groove.EXE|C:\Program Files\Microsoft Office 15\root\office15\GROOVE.exe|[KB402226](https://support.microsoft.com/en-us/topic/august-7-2018-update-for-onedrive-for-business-for-office-2013-kb4022226-6163bb26-cbde-eb16-ac42-abfda7afbf68)|15.0.4763.1000|
|Outlook.exe|C:\Program Files\Microsoft Office 15\root\office15\OUTLOOK.exe|[KB4484096](https://support.microsoft.com/en-us/topic/october-1-2019-update-for-outlook-2013-kb4484096-6513145a-cc75-1cd1-72b7-78cb62d8476b)|15.0.4753.1002|
|ADAL.DLL|C:\Program Files\Microsoft Office 15\root\vfs\ProgramFilesCommonx86\Microsoft Shared\OFFICE15\ADAL.DLL|[KB3085565](https://support.microsoft.com/en-us/topic/july-5-2016-update-for-office-2013-kb3085565-1d1a6d24-fbd4-1bae-242f-a35e0e2aba40)|1.0.2016.624|
|Iexplore.exe|C:\Program Files\Internet Explorer|[MS14-052](https://support.microsoft.com/en-us/topic/ms14-052-cumulative-security-update-for-internet-explorer-september-9-2014-17d29b71-9e78-0bc1-8961-7b812d04e4e1)|Non applicable|

## <a name="enable-modern-authentication-for-office-2013-clients"></a>Activer l'authentification moderne pour les clients Office 2013

1. Fermez Outlook.

2. Copiez et collez le texte suivant dans le Bloc-notes :

   ```text
   Windows Registry Editor Version 5.00

   [HKEY_CURRENT_USER\Software\Microsoft\Exchange]
   "AlwaysUseMSOAuthForAutoDiscover"=dword:00000001

   [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common]

   [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity]
   "EnableADAL"=dword:00000001
   "Version"=dword:00000001
   ```

3. Enregistrez le fichier avec l’extension de fichier .reg au lieu de .txt dans un emplacement facile à trouver. Par exemple : `C:\Data\Office2013_Enable_ModernAuth.reg`.

4. Ouvrez Explorateur de fichiers (anciennement l’Explorateur Windows), accédez à l’emplacement du fichier .reg que vous venez d’enregistrer, puis double-cliquez dessus.

5. Dans la boîte de **dialogue de contrôle de compte d’utilisateur** qui s’affiche, cliquez sur **Oui** pour autoriser l’application à apporter des modifications à votre appareil.

6. Dans la boîte de dialogue d’avertissement de **l’Éditeur du Registre** qui s’affiche, cliquez sur **Oui** pour accepter les modifications.

Une fois que vous avez défini les clés de Registre, vous pouvez définir des applications Office 2013 pour utiliser l’authentification multifacteur (MFA) avec Microsoft 365. Pour plus d’informations, consultez [Configurer l’authentification multifacteur](set-up-multi-factor-authentication.md).

Si vous êtes actuellement connecté à l’une des applications clientes Office, vous devez vous déconnecter et vous connecter pour que la modification prenne effet. Sinon, les paramètres de MRU et d’itinérance ne seront pas disponibles tant que l’identité n’est pas établie.

## <a name="disable-modern-authentication-on-devices"></a>Désactiver l'authentification moderne sur les appareils

La procédure de désactivation de l’authentification moderne sur un appareil est très similaire, mais moins de clés de Registre sont requises et vous devez définir leurs valeurs sur 0.

|Clé du Registre|Type|Valeur|
|---|:---:|:---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|0|
|HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|0|

```text
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\Exchange]
"AlwaysUseMSOAuthForAutoDiscover"=dword:00000000

[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common]

[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity]
"EnableADAL"=dword:00000000
```

## <a name="related-content"></a>Contenu associé

[Se connecter à Office 2013 avec une deuxième méthode de vérification](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)

[Outlook demande un mot de passe et n’utilise pas l’authentification moderne pour se connecter à Office 365](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled)
