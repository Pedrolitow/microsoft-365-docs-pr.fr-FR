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
ms.openlocfilehash: 3643db4b8d255809fc0ad125b76173b7d3b1a3d3
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68188326"
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
