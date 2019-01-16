---
title: Créer et modifier des appareils AutoPilot
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Adm_O365
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0f7b1d7c-4086-4331-8534-45d7886f9f34
description: Découvrez comment télécharger des périphériques à l’aide de pilote automatique dans Microsoft 365 Business. Vous pouvez affecter un profil à un périphérique ou un groupe de périphériques.
ms.openlocfilehash: cc1f81e9efd9b16e27b8abfbb0927d241535077e
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867088"
---
# <a name="create-and-edit-autopilot-devices"></a>Créer et modifier des appareils AutoPilot

## <a name="upload-a-list-of-devices"></a>Charger une liste d'appareils

Pour charger des appareils, vous pouvez utiliser le [guide détaillé](add-autopilot-devices-and-profile.md), mais vous pouvez également le faire à partir de l'onglet **Appareils**. 
  
Les appareils doivent respecter ces exigences :
  
- Windows 10, version 1703 ou supérieure.
    
- Nouveaux appareils qui ne sont pas issus d'une expérience Windows prête à l'emploi.
    
1. Dans le Centre d'administration Microsoft 365 Entreprise, choisissez **Déployer Windows avec AutoPilot** sur la carte **Actions de l'appareil**. 
    
    ![On the Device actions card, choose Deploy Windows with Autopilot.](media/160d5c2a-11a8-48f9-a8aa-70f084b85448.png)
  
2. Dans la page **Préparation de Windows** , choisissez l’onglet **périphériques** \> **périphériques ajouter**.
    
    ![In the Devices tab, choose Add devices.](media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. Dans le volet **Ajouter périphériques** , accédez à une [liste de périphériques fichier CSV](https://support.office.com/article/932e3676-2491-49f0-9177-d893d2f5276e) que vous avez préparé \> **Enregistrer** \> **Fermer**.
    
    Vous pouvez obtenir ces informations à partir de votre fournisseur de matériel ou vous pouvez utiliser le [script Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) qui génèrera un fichier csv. 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>Attribuer un profil à un appareil ou à un groupe d'appareils

1. Sur la page **Préparer Windows**, sélectionnez l'onglet **Appareils** et cochez la case correspondant à un ou plusieurs appareils. 
    
2. Dans le volet **Appareil**, sélectionnez un profil dans la liste déroulante **Profil attribué**. 
    
    Si vous n'avez pas encore de profil, consultez [Créer et modifier des profils AutoPilot](create-and-edit-autopilot-profiles.md) pour obtenir des instructions. 
    
