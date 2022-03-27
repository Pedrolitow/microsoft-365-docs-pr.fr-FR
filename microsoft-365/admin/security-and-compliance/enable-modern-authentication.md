---
title: Activer l’authentification moderne Office 2013 sur Windows appareils
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
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
description: Découvrez comment définir des clés de Registre pour activer l’authentification moderne pour les appareils sur Microsoft Office 2013.
ms.openlocfilehash: 468658c3b346c7923937ff9595699a20306ed6a9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754183"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>Activer l’authentification moderne Office 2013 sur Windows appareils

Microsoft Office 2013 sur les ordinateurs microsoft Windows prend en charge l’authentification moderne. Toutefois, pour l’activer, vous devez configurer les clés de Registre suivantes :

|Clé du Registre|Type|Valeur|
|:---|:---:|:---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\Version|REG_DWORD|1|

> [!NOTE]
> L’authentification moderne est déjà activée Office 2016 ou version ultérieure. Vous n’avez pas besoin de définir ces clés de Registre pour les versions ultérieures de Office.

## <a name="enable-modern-authentication-for-office-2013-clients"></a>Activer l'authentification moderne pour les clients Office 2013

1. Fermez Outlook.

2. Copiez et collez le texte suivant dans Bloc-notes :

   ```text
   Windows Registry Editor Version 5.00

   [HKEY_CURRENT_USER\Software\Microsoft\Exchange]
   "AlwaysUseMSOAuthForAutoDiscover"=dword:00000001

   [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common]

   [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity]
   "EnableADAL"=dword:00000001
   "Version"=dword:00000001
   ```

3. Enregistrez le fichier avec l’extension de fichier .reg .txt à un emplacement facile à trouver. Par exemple, `C:\Data\Office2013_Enable_ModernAuth.reg`.

4. Ouvrez l’Explorateur de fichiers (anciennement Windows Explorer), accédez à l’emplacement du fichier .reg que vous avez enregistré, puis double-cliquez dessus.

5. Dans la **boîte de dialogue Contrôle de compte d’utilisateur** qui s’affiche, cliquez sur **Oui** pour permettre à l’application d’apporter des modifications à votre appareil.

6. Dans la boîte **de dialogue d’avertissement de l’Éditeur** du Registre qui s’affiche, cliquez sur **Oui** pour accepter les modifications.

Une fois les clés de Registre définies, vous pouvez configurer Office 2013 pour utiliser l’authentification multifacteur (MFA) avec Microsoft 365. Pour plus d’informations, voir [Configurer l’authentification multifacteur](set-up-multi-factor-authentication.md).

Si vous êtes actuellement connectez à l’une des applications clientes Office, vous devez vous résigner et vous ré-inscrire pour que la modification prenne effet. Dans le cas contraire, le MRU et les paramètres d’itinérance ne seront pas disponibles tant que l’identité n’aura pas été établie.

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

[Outlook demande de mot de passe et n’utilise pas l’authentification moderne pour se connecter à Office 365](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled)
