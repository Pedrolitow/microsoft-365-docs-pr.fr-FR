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
description: Découvrez comment charger des appareils à l’aide d’AutoPilot dans Microsoft 365 Business Premium. Attribuer un profil à un appareil ou à un groupe d'appareils
ms.openlocfilehash: 2ae149744198803e7cd5441421b93147c965f256
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095227"
---
# <a name="create-and-edit-autopilot-devices"></a>Créer et modifier des appareils AutoPilot

> [!NOTE]
> Microsoft Defender pour les PME est déployée pour les clients Microsoft 365 Business Premium, à compter du 1er mars 2022. Cette offre fournit des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender for Business](../security/defender-business/mdb-overview.md).

## <a name="upload-a-list-of-devices"></a>Charger une liste d'appareils

Pour charger des appareils, vous pouvez utiliser le [guide détaillé](m365bp-add-autopilot-devices-and-profile.md), mais vous pouvez également le faire à partir de l'onglet **Appareils**. 
  
Les appareils doivent respecter ces exigences :
  
- Windows 10, version 1703 ou supérieure
    
- Nouveaux appareils qui ne sont pas issus d'une expérience Windows prête à l'emploi.

1. Dans le Centre d'administration Microsoft 365, choisissez **Appareils** \> **AutoPilot**.
  
2. Sur la page **AutoPilot**, choisissez l'onglet **Dispositifs** \>**Ajouter des dispositifs**.
    
    ![In the Devices tab, choose Add devices.](./../media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. Dans le panneau **Ajouter des dispositifs**, naviguez jusqu'à un [fichier CSV de liste de dispositifs](../admin/misc/device-list.md) que vous avez préparé \> **Enregistrer** \> **Fermer**.
    
    Vous pouvez obtenir ces informations à partir de votre fournisseur de matériel ou vous pouvez utiliser le [script Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) qui générera un fichier CSV. 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>Attribuer un profil à un appareil ou à un groupe d'appareils

1. Sur la page **Préparer Windows**, sélectionnez l'onglet **Appareils** et cochez la case correspondant à un ou plusieurs appareils. 
    
2. Dans le volet **Appareil**, sélectionnez un profil dans la liste déroulante **Profil attribué**. 
    
    Si vous n'avez pas encore de profil, consultez [Créer et modifier des profils AutoPilot](../admin/devices/create-and-edit-autopilot-profiles.md) pour obtenir des instructions. 

## <a name="see-also"></a>Voir aussi

[10 principales façons de sécuriser les plans Microsoft 365 pour les entreprises](../admin/security-and-compliance/secure-your-business-data.md)
