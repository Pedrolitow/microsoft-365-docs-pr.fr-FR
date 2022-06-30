---
title: Créer et modifier des appareils Autopilot
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
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
description: Découvrez comment charger des appareils à l’aide d’Autopilot dans Microsoft 365 Business Premium. Attribuer un profil à un appareil ou à un groupe d'appareils
ms.openlocfilehash: 994eab29d4b04e2de21d3e42a4abc174270f67f7
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66486564"
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
