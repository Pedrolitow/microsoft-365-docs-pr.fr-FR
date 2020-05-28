---
title: Activer l'authentification moderne pour Office 2013 sur les appareils Windows
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7dc1c01a-090f-4971-9677-f1b192d6c910
description: Apprenez à définir des clés de Registre pour activer l’authentification moderne pour les appareils sur lesquels Microsoft Office 2013 est installé.
ms.openlocfilehash: 8bf6f50068f1a1435897c49656823302df40235e
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44399169"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>Activer l'authentification moderne pour Office 2013 sur les appareils Windows

[] Pour activer l'authentification moderne pour les appareils Windows sur lesquels Office 2013 est installé, vous devez définir des clés de Registre spécifiques.
  
## <a name="enable-modern-authentication-for-office-2013-clients"></a>Activer l'authentification moderne pour les clients Office 2013

> [!NOTE]
> L'authentification moderne est déjà activée pour les clients Office 2016. Vous n'avez pas besoin de définir de clés de Registre pour Office 2016. 
  
Pour activer l'authentification moderne pour les appareils exécutant Windows (par exemple les ordinateurs portables et tablettes) et sur lesquels Microsoft Office 2013 est installé, vous devez définir les clés de Registre suivantes. Les clés doivent être définies sur chaque appareil pour lequel vous voulez activer l'authentification moderne :
  
|**Clé de Registre**|**Type**|**Valeur** |
|:-------|:------:|--------:|
|Hkcu\software\microsoft\office\15.0\common\identity\enableadal sur  |REG_DWORD  |1   |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1  |
   
Une fois que vous avez défini les clés de Registre, vous pouvez définir les applications de périphériques Office 2013 pour utiliser [l’authentification multifacteur (MFA)](set-up-multi-factor-authentication.md) avec Microsoft 365. 
  
Si vous êtes actuellement connecté avec une application client, vous devez vous déconnecter et vous reconnecter pour que la modification prenne effet. Autrement, les paramètres MRU et d'itinérance ne seront pas disponibles tant que l'identité ADAL n'est pas établie.
  
## <a name="disable-modern-authentication-on-devices"></a>Désactiver l'authentification moderne sur les appareils

Pour désactiver l'authentification moderne sur un appareil, définissez les clés de Registre suivantes sur l'appareil :
  
|**Clé de Registre**|**Type**|**Valeur**|
|:-------|:------:|--------:|
|Hkcu\software\microsoft\office\15.0\common\identity\enableadal sur |REG_DWORD|0|
   
## <a name="related-articles"></a>Articles connexes
[Se connecter à Office 2013 avec une deuxième méthode de vérification](https://support.office.com/article/2b856342-170a-438e-9a4f-3c092394d3cb.aspx)

  

