---
title: Créer et modifier des profils AutoPilot
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
ms.assetid: 5cf7139e-cfa1-4765-8aad-001af1c74faa
description: Apprenez à créer, modifier, supprimer ou supprimer des profils AutoPilot.
ms.openlocfilehash: 4305340a2fc5df8202cf4d85f9e2541690bf9ed0
ms.sourcegitcommit: bd52f7b662887f552f90c46f69d6a2a42fb66914
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "37574715"
---
# <a name="create-and-edit-autopilot-profiles"></a>Créer et modifier des profils AutoPilot

## <a name="create-a-profile"></a>Créer un profil

Un profil s'applique à un appareil ou à un groupe d'appareils,
  
1. Dans le centre d’administration de Microsoft 365 Business, sélectionnez **périphériques** \> **AutoPilot**.
  
2. Sur la **page AutoPilot** , sélectionnez l' **** onglet \> profils **Create Profile**.
    
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
    
