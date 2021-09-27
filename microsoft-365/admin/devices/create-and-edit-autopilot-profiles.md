---
title: Créer et modifier des profils AutoPilot
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
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5cf7139e-cfa1-4765-8aad-001af1c74faa
description: Apprenez à créer un profil AutoPilot et à l’appliquer à un appareil, ainsi qu’à modifier ou supprimer un profil ou à supprimer un profil d’un appareil.
ms.openlocfilehash: 685773fbdac454af039478c17232e6e88333dc74
ms.sourcegitcommit: 34259ec9b6cccc8f6e29808dbe4796d9f72b651b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2021
ms.locfileid: "59933566"
---
# <a name="create-and-edit-autopilot-profiles"></a>Créer et modifier des profils AutoPilot

## <a name="create-a-profile"></a>Créer un profil

Un profil s'applique à un appareil ou à un groupe d'appareils,
  
1. In the Centre d'administration Microsoft 365, choose **Devices** \> **AutoPilot**.
  
2. Dans la page **AutoPilot,** sélectionnez **l’onglet Profils** \> **Créer un profil.**
    
3. Dans la page **Créer un** profil, entrez un nom pour le profil qui vous permet de l’identifier, par exemple Marketing. Activer le paramètre de votre choix, puis sélectionnez **Enregistrer.** Pour plus d’informations sur les paramètres de profil AutoPilot, voir à propos des paramètres de profil [AutoPilot.](autopilot-profile-settings.md)
    
    ![Enter name and turn on settings in the Create profile panel.](../../media/63b5a00d-6a5d-48d0-9557-e7531e80702a.png)
  
### <a name="apply-profile-to-a-device"></a>Appliquer le profil à un appareil

Après avoir créé un profil, vous pouvez l’appliquer à un appareil ou à un groupe d’appareils. Vous pouvez choisir un profil existant dans le [guide](add-autopilot-devices-and-profile.md) pas à pas et l’appliquer à de nouveaux appareils, ou remplacer un profil existant pour un appareil ou un groupe d’appareils. 
  
1. Sur la page **Préparer Windows**, choisissez l'onglet **Appareils**. 
    
2. Cochez la case en regard d’un nom d’appareil, puis, dans le panneau Appareil, choisissez un profil dans la liste de listes listes des profils affectés   \> **Enregistrer.**
    
    ![In the Device panel, select an Assigned profile to apply it.](../../media/ed0ce33f-9241-4403-a5de-2dddffdc6fb9.png)
  
## <a name="edit-delete-or-remove-a-profile"></a>Modifier, supprimer ou retirer un profil

Lorsque vous avez affecté un profil à un appareil, vous pouvez le mettre à jour, même si vous avez déjà donné l'appareil à un utilisateur. Lorsque l'appareil se connecte à Internet, il télécharge la dernière version de votre profil pendant le processus de configuration. Si l'utilisateur rétablit les paramètres d'usine par défaut de son appareil, l'appareil télécharge à nouveau les dernières mises à jour de votre profil. 
  
### <a name="edit-a-profile"></a>Modifier un profil

1. Sur la page **Préparer Windows**, choisissez l'onglet **Profils**. 
    
2. Cochez la case en regard d’un nom d’appareil et, dans le panneau Profil, mettez à jour l’un des paramètres disponibles  \> **Enregistrer.**
    
    Si vous effectuez cette opération avant qu'un utilisateur connecte l'appareil à Internet, le profil sera appliqué pendant le processus de configuration.
    
### <a name="delete-a-profile"></a>Supprimer un profil

1. Sur la page **Préparer Windows**, choisissez l'onglet **Profils**. 
    
2. Cochez la case en regard d’un nom d’appareil, puis, dans le panneau Profil,  **sélectionnez Supprimer enregistrer le** \> **profil.**
    
    Lorsque vous supprimez un profil, il est supprimé de l'appareil ou du groupe d'appareils auquel il a été affecté.
    
### <a name="remove-a-profile"></a>Retirer un profil

1. Sur la page **Préparer Windows**, choisissez l'onglet **Appareils**. 
    
2. Cochez la case en regard d’un nom d’appareil, puis, dans le panneau Appareil, sélectionnez **Aucun** dans la liste de listes listes de profils affectés   \> **Enregistrer.**
    
