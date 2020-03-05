---
title: Créer et modifier des profils AutoPilot
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
- MARVEL_SEO_MAR
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5cf7139e-cfa1-4765-8aad-001af1c74faa
description: Apprenez à créer un profil AutoPilot et à l’appliquer à un appareil, ainsi qu’à modifier ou supprimer un profil ou à supprimer un profil d’un appareil.
ms.openlocfilehash: 6a8057969242d839ebbb4cbef8d26dd3f1858c59
ms.sourcegitcommit: d6c871bf3f94d9299d22695f5dbaf25dc1bd6ff9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "42417333"
---
# <a name="create-and-edit-autopilot-profiles"></a>Créer et modifier des profils AutoPilot

## <a name="create-a-profile"></a>Créer un profil

Un profil s'applique à un appareil ou à un groupe d'appareils,
  
1. Dans le centre d’administration de Microsoft 365 Business, sélectionnez **périphériques** \> **AutoPilot**.
  
2. Sur la **page AutoPilot** , sélectionnez l' **** onglet \> profils **Create Profile**.
    
3. Sur la page **créer un profil** , entrez un nom pour le profil qui vous permet de l’identifier, par exemple marketing. Activez le paramètre souhaité, puis choisissez **Enregistrer**. Pour plus d’informations sur les paramètres du profil AutoPilot, voir [à propos des paramètres du profil AutoPilot](autopilot-profile-settings.md).
    
    ![Enter name and turn on settings in the Create profile panel.](../media/63b5a00d-6a5d-48d0-9557-e7531e80702a.png)
  
### <a name="apply-profile-to-a-device"></a>Appliquer le profil à un appareil

Une fois que vous avez créé un profil, vous pouvez l’appliquer à un appareil ou à un groupe d’appareils. Vous pouvez choisir un profil existant dans le [Guide pas à pas](add-autopilot-devices-and-profile.md) et l’appliquer à de nouveaux appareils ou remplacer un profil existant pour un appareil ou un groupe d’appareils. 
  
1. Sur la page **Préparer Windows**, choisissez l'onglet **Appareils**. 
    
2. Activez la case à cocher en regard du nom d’un appareil, puis dans le panneau **périphérique** , sélectionnez un profil dans la liste \> déroulante **Profil affecté** **Enregistrer**.
    
    ![In the Device panel, select an Assigned profile to apply it.](../media/ed0ce33f-9241-4403-a5de-2dddffdc6fb9.png)
  
## <a name="edit-delete-or-remove-a-profile"></a>Modifier, supprimer ou retirer un profil

Lorsque vous avez affecté un profil à un appareil, vous pouvez le mettre à jour, même si vous avez déjà donné l'appareil à un utilisateur. Lorsque l'appareil se connecte à Internet, il télécharge la dernière version de votre profil pendant le processus de configuration. Si l'utilisateur rétablit les paramètres d'usine par défaut de son appareil, l'appareil télécharge à nouveau les dernières mises à jour de votre profil. 
  
### <a name="edit-a-profile"></a>Modifier un profil

1. Sur la page **Préparer Windows**, choisissez l'onglet **Profils**. 
    
2. Activez la case à cocher en regard du nom d’un appareil, puis, dans le volet **Profil** , mettez \> à jour les paramètres d' **enregistrement**disponibles.
    
    Si vous effectuez cette opération avant qu'un utilisateur connecte l'appareil à Internet, le profil sera appliqué pendant le processus de configuration.
    
### <a name="delete-a-profile"></a>Supprimer un profil

1. Sur la page **Préparer Windows**, choisissez l'onglet **Profils**. 
    
2. Activez la case à cocher en regard du nom d’un appareil, puis, dans le volet **Profil** , sélectionnez Supprimer l' **enregistrement**du **Profil** \> .
    
    Lorsque vous supprimez un profil, il est supprimé de l'appareil ou du groupe d'appareils auquel il a été affecté.
    
### <a name="remove-a-profile"></a>Retirer un profil

1. Sur la page **Préparer Windows**, choisissez l'onglet **Appareils**. 
    
2. Activez la case à cocher en regard du nom d’un appareil, puis, dans le panneau **périphérique** , choisissez **aucun** dans la liste \> déroulante **Profil affecté** **Enregistrer**.
    
