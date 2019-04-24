---
title: Créer et modifier des profils AutoPilot
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5cf7139e-cfa1-4765-8aad-001af1c74faa
description: 'Apprenez à créer, modifier, supprimer ou supprimer des profils autoPilot. '
ms.openlocfilehash: 85fc897b2f428afae8d55feeb577021adaa30f72
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32277103"
---
# <a name="create-and-edit-autopilot-profiles"></a>Créer et modifier des profils AutoPilot

## <a name="create-a-profile"></a>Créer un profil

Un profil s'applique à un appareil ou à un groupe d'appareils,
  
1. dans le centre d'administration de Microsoft 365 Business, sélectionnez **périphériques** \> **autopilot**.
  
2. Sur la **** page AutoPilot, sélectionnez l' **** onglet \> profils **Create Profile**.
    
3. Sur la page **Créer un profil**, entrez un nom de profil qui vous permette de l'identifier, par exemple Marketing, activez le paramètre souhaité (voir [À propos des paramètres de profil AutoPilot](autopilot-profile-settings.md) pour plus d'informations), puis choisissez **Enregistrer**.
    
    ![Enter name and turn on settings in the Create profile panel.](media/63b5a00d-6a5d-48d0-9557-e7531e80702a.png)
  
### <a name="apply-profile-to-a-device"></a>Appliquer le profil à un appareil

Après avoir créé un profil, vous pouvez l'appliquer à un appareil ou à un groupe d'appareils. Vous pouvez sélectionner un profil existant dans la [guide détaillé](add-autopilot-devices-and-profile.md), l'appliquer aux nouveaux appareils ou remplacer un profil existant pour un appareil ou un groupe d'appareils. 
  
1. Sur la page **Préparer Windows**, choisissez l'onglet **Appareils**. 
    
2. Cliquez sur la case à cocher en regard du nom d'un appareil, puis, dans le volet **Appareil**, choisissez un profil dans la liste déroulante **Profil affecté** \> **Enregistrer**.
    
    ![In the Device panel, select an Assigned profile to apply it.](media/ed0ce33f-9241-4403-a5de-2dddffdc6fb9.png)
  
## <a name="edit-delete-or-remove-a-profile"></a>Modifier, supprimer ou retirer un profil

Lorsque vous avez affecté un profil à un appareil, vous pouvez le mettre à jour, même si vous avez déjà donné l'appareil à un utilisateur. Lorsque l'appareil se connecte à Internet, il télécharge la dernière version de votre profil pendant le processus de configuration. Si l'utilisateur rétablit les paramètres d'usine par défaut de son appareil, l'appareil télécharge à nouveau les dernières mises à jour de votre profil. 
  
### <a name="edit-a-profile"></a>Modifier un profil

1. Sur la page **Préparer Windows**, choisissez l'onglet **Profils**. 
    
2. Cliquez sur la case à cocher en regard du nom d'un appareil puis, dans le volet **Profil**, modifiez les paramètres de votre choix \> **Enregistrer**.
    
    Si vous effectuez cette opération avant qu'un utilisateur connecte l'appareil à Internet, le profil sera appliqué pendant le processus de configuration.
    
### <a name="delete-a-profile"></a>Supprimer un profil

1. Sur la page **Préparer Windows**, choisissez l'onglet **Profils**. 
    
2. Cliquez sur la case à cocher en regard du nom d'un appareil puis, dans le volet **Profil**, cliquez sur **Supprimer le profil** \> **Enregistrer**.
    
    Lorsque vous supprimez un profil, il est supprimé de l'appareil ou du groupe d'appareils auquel il a été affecté.
    
### <a name="remove-a-profile"></a>Retirer un profil

1. Sur la page **Préparer Windows**, choisissez l'onglet **Appareils**. 
    
2. Cliquez sur la case à cocher en regard du nom d'un appareil, puis, dans le volet **Appareil**, choisissez **Aucun** dans la liste déroulante **Profil affecté** \> **Enregistrer**.
    
