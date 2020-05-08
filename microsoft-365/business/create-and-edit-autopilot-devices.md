---
title: Créer et modifier des appareils AutoPilot
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
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0f7b1d7c-4086-4331-8534-45d7886f9f34
description: Découvrez comment télécharger des périphériques à l’aide de AutoPilot dans Microsoft 365 Business Premium. Vous pouvez affecter un profil à un appareil ou à un groupe d’appareils.
ms.openlocfilehash: 83c027cfe019e037518c4ca13eb331e5300fc2c1
ms.sourcegitcommit: 46644f9778bc70ab6d62783e0a1e60ba2eccc27f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "44165858"
---
# <a name="create-and-edit-autopilot-devices"></a>Créer et modifier des appareils AutoPilot

## <a name="upload-a-list-of-devices"></a>Charger une liste d'appareils

Vous pouvez utiliser le [Guide pas à pas](add-autopilot-devices-and-profile.md) pour télécharger des périphériques, mais vous pouvez également télécharger des périphériques dans l’onglet **appareils** . 
  
Les appareils doivent respecter les conditions suivantes :
  
- Windows 10, version 1703 ou ultérieure
    
- Nouveaux appareils qui n’ont pas fait l’expérience de Windows out-of-Box

1. Dans le centre d’administration 365 de Microsoft, sélectionnez **périphériques** \> **AutoPilot**.
  
2. Sur la **page AutoPilot** , sélectionnez l' **Devices** onglet \> appareils **Add Devices**.
    
    ![In the Devices tab, choose Add devices.](../media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. Dans le **panneau ajouter des appareils** , accédez à un [fichier CSV de liste](https://docs.microsoft.com/microsoft-365/admin/misc/device-list) de périphériques \> que vous avez préparé à **Enregistrer** \> **.**
    
    Vous pouvez obtenir ces informations auprès de votre fournisseur de matériel ou vous pouvez utiliser le [script PowerShell Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) pour générer un fichier CSV. 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>Attribuer un profil à un appareil ou à un groupe d'appareils

1. Sur la page **préparer Windows** , sélectionnez l’onglet **appareils** et activez la case à cocher en regard d’un ou de plusieurs appareils. 
    
2. Dans le volet **Appareil**, sélectionnez un profil dans la liste déroulante **Profil attribué**. 
    
    Si vous n'avez pas encore de profil, consultez [Créer et modifier des profils AutoPilot](create-and-edit-autopilot-profiles.md) pour obtenir des instructions. 
    
