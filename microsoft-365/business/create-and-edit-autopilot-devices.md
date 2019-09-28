---
title: Créer et modifier des appareils AutoPilot
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
ms.custom: OKR_SMB_M365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0f7b1d7c-4086-4331-8534-45d7886f9f34
description: Découvrez comment télécharger des périphériques à l’aide de AutoPilot dans Microsoft 365 Business. Vous pouvez affecter un profil à un appareil ou à un groupe d’appareils.
ms.openlocfilehash: 9ae94266f5a41d8d115fc92f0f080a6fdbdc9f15
ms.sourcegitcommit: 6003d6da0a85c97357eb3dba3918eb145f381fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "37288012"
---
# <a name="create-and-edit-autopilot-devices"></a>Créer et modifier des appareils AutoPilot

## <a name="upload-a-list-of-devices"></a>Charger une liste d'appareils

Pour charger des appareils, vous pouvez utiliser le [guide détaillé](add-autopilot-devices-and-profile.md), mais vous pouvez également le faire à partir de l'onglet **Appareils**. 
  
Les appareils doivent respecter ces exigences :
  
- Windows 10, version 1703 ou supérieure.
    
- Nouveaux appareils qui ne sont pas issus d'une expérience Windows prête à l'emploi.

1. Dans le centre d’administration de Microsoft 365 Business, sélectionnez **périphériques** \> **AutoPilot**.
  
2. Sur la **page AutoPilot** , sélectionnez l' **** onglet \> appareils **Add Devices**.
    
    ![In the Devices tab, choose Add devices.](media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. Dans le panneau **Ajouter des appareils** , accédez à un [fichier CSV de liste de périphériques](https://support.office.com/article/932e3676-2491-49f0-9177-d893d2f5276e) que vous \> avez préparé **Enregistrer** \> **Fermer**.
    
    Vous pouvez obtenir ces informations à partir de votre fournisseur de matériel ou vous pouvez utiliser le [script Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) qui génèrera un fichier csv. 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>Attribuer un profil à un appareil ou à un groupe d'appareils

1. Sur la page **Préparer Windows**, sélectionnez l'onglet **Appareils** et cochez la case correspondant à un ou plusieurs appareils. 
    
2. Dans le volet **Appareil**, sélectionnez un profil dans la liste déroulante **Profil attribué**. 
    
    Si vous n'avez pas encore de profil, consultez [Créer et modifier des profils AutoPilot](create-and-edit-autopilot-profiles.md) pour obtenir des instructions. 
    
