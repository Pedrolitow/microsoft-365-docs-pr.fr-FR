---
title: Créer et modifier des appareils AutoPilot
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
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
ms.openlocfilehash: f578e1879d851e7b07129f7a1ba6a1d098cea16a
ms.sourcegitcommit: 34259ec9b6cccc8f6e29808dbe4796d9f72b651b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2021
ms.locfileid: "59933554"
---
# <a name="create-and-edit-autopilot-devices"></a>Créer et modifier des appareils AutoPilot

## <a name="upload-a-list-of-devices"></a>Charger une liste d'appareils

Vous pouvez utiliser le [guide pas à](add-autopilot-devices-and-profile.md) pas pour télécharger des appareils, mais vous pouvez également télécharger des appareils dans l’onglet **Appareils.** 
  
Les appareils doivent répondre aux exigences ci-après :
  
- Windows 10, version 1703 ou ultérieure
    
- Nouveaux appareils qui n’ont pas été Windows l’expérience pré-out-of-box

1. In the Centre d'administration Microsoft 365, choose **Devices** \> **AutoPilot**.
  
2. Dans la page **AutoPilot,** sélectionnez **l’onglet Appareils** \> **Ajouter des appareils.**
    
    ![In the Devices tab, choose Add devices.](../../media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. Dans le **panneau Ajouter des appareils,** accédez à un fichier [CSV](../misc/device-list.md) de liste d’appareils que vous avez préparé \> **Enregistrer** \> **fermer.**
    
    Vous pouvez obtenir ces informations auprès de votre fournisseur de matériel ou utiliser le [script PowerShell Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) pour générer un fichier CSV. 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>Attribuer un profil à un appareil ou à un groupe d'appareils

1. Dans la page **Préparer Windows,**  sélectionnez l’onglet Appareils, puis cochez la case en regard d’un ou plusieurs appareils. 
    
2. Dans le volet **Appareil**, sélectionnez un profil dans la liste déroulante **Profil attribué**. 
    
    Si vous n'avez pas encore de profil, consultez [Créer et modifier des profils AutoPilot](create-and-edit-autopilot-profiles.md) pour obtenir des instructions. 