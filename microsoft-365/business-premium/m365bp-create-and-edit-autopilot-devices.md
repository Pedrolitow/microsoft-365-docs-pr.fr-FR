---
title: Créer et modifier des appareils Autopilot
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: microsoft-365-business
ms.subservice: business-premium
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection: ''
ms.custom:
- MiniMaven
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment charger des appareils à l’aide d’Autopilot dans Microsoft 365 Business Premium. Attribuer un profil à un appareil ou à un groupe d'appareils
ms.openlocfilehash: 977b28949f598d827d03ef569429c599c5632dc7
ms.sourcegitcommit: db89873e22a12705ed313964c1bc2fa19d4fe719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67712555"
---
# <a name="create-and-edit-autopilot-devices"></a>Créer et modifier des appareils Autopilot

## <a name="upload-a-list-of-devices"></a>Charger une liste d'appareils

Pour charger des appareils, vous pouvez utiliser le [guide détaillé](m365bp-add-Autopilot-devices-and-profile.md), mais vous pouvez également le faire à partir de l'onglet **Appareils**. 
  
Les appareils doivent respecter ces exigences :
  
- Windows 10, version 1703 ou supérieure
    
- Nouveaux appareils qui ne sont pas issus d'une expérience Windows prête à l'emploi.

1. Dans le Centre d’administration Microsoft 365, choisissez **Appareils** \> **Autopilot**.
  
2. Sur la page **AutoPilot**, choisissez l'onglet **Appareils** \>**Ajouter des appareils**.
    
    ![In the Devices tab, choose Add devices.](./../media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. Dans le panneau **Ajouter des dispositifs**, naviguez jusqu'à un [fichier CSV de liste de dispositifs](../admin/misc/device-list.md) que vous avez préparé \> **Enregistrer** \> **Fermer**.
    
    Vous pouvez obtenir ces informations auprès de votre fournisseur de matériel ou utiliser le [script PowerShell Get-WindowsAutopilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutopilotInfo) pour générer un fichier CSV. 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>Attribuer un profil à un appareil ou à un groupe d'appareils

1. Sur la page **Préparer Windows**, sélectionnez l'onglet **Appareils** et cochez la case correspondant à un ou plusieurs appareils. 
    
2. Dans le volet **Appareil**, sélectionnez un profil dans la liste déroulante **Profil attribué**. 
    
    Si vous n’avez pas encore de profils, consultez [Créer et modifier des profils Autopilot](../admin/devices/create-and-edit-Autopilot-profiles.md) pour obtenir des instructions. 

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)
