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
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0f7b1d7c-4086-4331-8534-45d7886f9f34
description: Découvrez comment télécharger des appareils à l’aide d’AutoPilot dans Microsoft 365 Business Premium. Vous pouvez affecter un profil à un appareil ou à un groupe d’appareils.
ms.openlocfilehash: 910abb98b94b749177b04cd12c766f82d348e379
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50913395"
---
# <a name="create-and-edit-autopilot-devices"></a>Créer et modifier des appareils AutoPilot

## <a name="upload-a-list-of-devices"></a>Charger une liste d'appareils

Vous pouvez utiliser le [guide pas à](add-autopilot-devices-and-profile.md) pas pour télécharger des appareils, mais vous pouvez également télécharger des appareils dans l’onglet **Appareils.** 
  
Les appareils doivent répondre aux exigences ci-après :
  
- Windows 10, version 1703 ou ultérieure
    
- Nouveaux appareils qui n’ont pas fait l’expérience d’utilisation de Windows out-of-box

1. Dans le Centre d’administration Microsoft 365, sélectionnez **Appareils** \> **AutoPilot**.
  
2. Dans la page **AutoPilot,** sélectionnez **l’onglet Appareils** \> **Ajouter des appareils.**
    
    ![In the Devices tab, choose Add devices.](../media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. Dans le **panneau Ajouter des appareils,** accédez à un fichier [CSV](../admin/misc/device-list.md) de liste d’appareils que vous avez préparé \> **Enregistrer** \> **fermer.**
    
    Vous pouvez obtenir ces informations auprès de votre fournisseur de matériel ou utiliser le [script PowerShell Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) pour générer un fichier CSV. 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>Attribuer un profil à un appareil ou à un groupe d'appareils

1. Dans la page **Préparer Windows,** sélectionnez l’onglet **Appareils,** puis cochez la case en regard d’un ou plusieurs appareils. 
    
2. Dans le volet **Appareil**, sélectionnez un profil dans la liste déroulante **Profil attribué**. 
    
    Si vous n'avez pas encore de profil, consultez [Créer et modifier des profils AutoPilot](create-and-edit-autopilot-profiles.md) pour obtenir des instructions. 
