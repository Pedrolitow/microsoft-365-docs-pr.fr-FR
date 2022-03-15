---
title: Activer l'authentification moderne pour Office 2013 sur les appareils Windows
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
ms.openlocfilehash: 010dce00762e4e73d21a9da668a7ac9606d731f9
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504752"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>Activer l'authentification moderne pour Office 2013 sur les appareils Windows

[] Pour activer l'authentification moderne pour les appareils Windows sur lesquels Office 2013 est installé, vous devez définir des clés de Registre spécifiques.
  
## <a name="enable-modern-authentication-for-office-2013-clients"></a>Activer l'authentification moderne pour les clients Office 2013

> [!NOTE]
> L'authentification moderne est déjà activée pour les clients Office 2016. Vous n'avez pas besoin de définir de clés de Registre pour Office 2016. 
  
Pour activer l'authentification moderne pour les appareils exécutant Windows (par exemple les ordinateurs portables et tablettes) et sur lesquels Microsoft Office 2013 est installé, vous devez définir les clés de Registre suivantes. Les clés doivent être définies sur chaque appareil que vous souhaitez activer pour l’authentification moderne :

<br>

****

|Clé du Registre|Type|Valeur|
|:---|:---:|---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\Version|REG_DWORD|1|

Créez ou modifiez les clés de Registre suivantes pour forcer Outlook à utiliser une méthode d’authentification plus nouvelle pour les services web, tels que EWS et la découverte automatique. Il est recommandé que les utilisateurs forcent Outlook l’authentification moderne.

1. Quittez Outlook.

2. Démarrez l’Éditeur du Registre à l’aide de l’une des procédures suivantes, selon votre version de Windows :

   - **Windows 10, Windows 8.1 et Windows 8 :** appuyez sur Windows touche + R pour ouvrir une boîte **de dialogue Exécuter**. *Tapezregedit.exe*, puis appuyez sur **Entrée.**
   - **Windows 7 :** **cliquez sur** Démarrer, tapez *regedit.exe* dans la zone de recherche, puis appuyez sur **Entrée.**

3. Dans l’Éditeur du Registre, recherchez et cliquez sur la sous-clé de Registre suivante :

   ```console
   HKEY_CURRENT_USER\Software\Microsoft\Exchange\
   ```

4. Si la *clé AlwaysUseMSOAuthForAutoDiscover* est manquante, dans le menu Edition, pointez sur **Nouveau** , puis sélectionnez **Valeur DWORD**. *Tapez AlwaysUseMSOAuthForAutoDiscover*, puis appuyez sur **Entrée.**

5. Cliquez avec le bouton *droit sur AlwaysUseMSOAuthForAutoDiscover*, puis cliquez sur **Modifier.**

6. Dans la **zone Données** de la valeur, **tapez 1**, puis cliquez sur **OK.**

7. Dans l’Éditeur du Registre, recherchez et cliquez sur la sous-clé de Registre suivante :

   ```console
   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\
   ```

8. Si les clés du tableau ci-dessus existent déjà, modifiez les valeurs si nécessaire, puis quittez l’Éditeur du Registre. Si ce n’est pas le cas, dans le menu Édition, pointez sur **Nouveau** , puis sélectionnez **Valeur DWORD** pour créer les clés manquantes. 

9. Par exemple, si la *clé EnableADAL* est manquante, tapez *EnableADAL*, puis appuyez sur **Entrée.**

10. Cliquez avec le bouton *droit sur EnableADAL*, puis cliquez sur **Modifier.**

11. Dans la **zone Données** de la valeur, **tapez 1**, puis cliquez sur **OK.**

12. Si nécessaire, suivez le même processus pour la clé de version. 

13. **Fermez l’Éditeur du Registre.**

Une fois les clés de Registre définies, vous pouvez définir des applications d’appareils Office 2013 pour utiliser l’authentification [multifacteur (MFA)](set-up-multi-factor-authentication.md) avec Microsoft 365. 
  
Si vous êtes actuellement connecté avec une application client, vous devez vous déconnecter et vous reconnecter pour que la modification prenne effet. Dans le cas contraire, le MRU et les paramètres d’itinérance ne seront pas disponibles tant que l’identité n’aura pas été établie.
  
## <a name="disable-modern-authentication-on-devices"></a>Désactiver l'authentification moderne sur les appareils

Pour désactiver l'authentification moderne sur un appareil, définissez les clés de Registre suivantes sur l'appareil :

<br>

****

|Clé du Registre|Type|Valeur|
|:---|:---:|---:|
|HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|0|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|0|
   
## <a name="related-content"></a>Contenu associé

[Connectez-vous Office 2013 avec une deuxième méthode de vérification](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb) (article)\
[Outlook demande de mot de passe et n’utilise pas l’authentification moderne pour se connecter à Office 365](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled) (article)
