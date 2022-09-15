---
title: Créer et modifier des profils Autopilot
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
description: Apprenez à créer un profil Autopilot et à l’appliquer à un appareil, à modifier ou supprimer un profil ou à supprimer un profil d’un appareil.
ms.openlocfilehash: 2a74bf007f0dcac400033248813afe9558f0b2f8
ms.sourcegitcommit: db89873e22a12705ed313964c1bc2fa19d4fe719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67712558"
---
# <a name="create-and-edit-autopilot-profiles"></a>Créer et modifier des profils Autopilot

Vous pouvez appliquer un [profil de déploiement Windows Autopilot](/mem/autopilot/profiles) aux appareils qui se trouvent dans un [groupe d’appareils](m365bp-device-groups-mdb.md). Les profils de déploiement déterminent l’expérience de déploiement et d’inscription de Windows que les utilisateurs auront. 

## <a name="create-a-profile"></a>Créer un profil

Un profil s'applique à un appareil ou à un groupe d'appareils,
  
1. Dans le Centre d’administration Microsoft 365, choisissez **Appareils** \> **Autopilot**.
  
2. Dans la page **AutoPilot** , choisissez l’onglet **Profils** \> **Créer un profil**.

3. Dans la page **Créer un profil** , entrez un nom pour le profil qui vous aide à l’identifier, par exemple Marketing. Activez le paramètre souhaité, puis **choisissez Enregistrer**. Pour plus d’informations sur les paramètres de profil Autopilot, consultez [À propos des paramètres de profil Autopilot](m365bp-Autopilot-profile-settings.md).

    ![Enter name and turn on settings in the Create profile panel.](./../media/63b5a00d-6a5d-48d0-9557-e7531e80702a.png)
  
### <a name="apply-profile-to-a-device"></a>Appliquer le profil à un appareil

Après avoir créé un profil, vous pouvez l’appliquer à un appareil ou à un groupe d’appareils. Vous pouvez choisir un profil existant dans le [guide pas à pas](m365bp-add-Autopilot-devices-and-profile.md) et l’appliquer à de nouveaux appareils, ou remplacer un profil existant pour un appareil ou un groupe d’appareils.
  
1. Sur la page **Préparer Windows**, choisissez l'onglet **Appareils**.

2. Activez la case à cocher en regard d’un nom d’appareil et, dans le panneau **Appareil**, choisissez un profil dans la liste déroulante **Profil affecté**\>**Enregistrer**.

    ![In the Device panel, select an Assigned profile to apply it.](./../media/ed0ce33f-9241-4403-a5de-2dddffdc6fb9.png)
  
## <a name="edit-delete-or-remove-a-profile"></a>Modifier, supprimer ou retirer un profil

Lorsque vous avez affecté un profil à un appareil, vous pouvez le mettre à jour, même si vous avez déjà donné l'appareil à un utilisateur. Lorsque l'appareil se connecte à Internet, il télécharge la dernière version de votre profil pendant le processus de configuration. Si l'utilisateur rétablit les paramètres d'usine par défaut de son appareil, l'appareil télécharge à nouveau les dernières mises à jour de votre profil.
  
### <a name="edit-a-profile"></a>Modifier un profil

1. Sur la page **Préparer Windows**, choisissez l'onglet **Profils**.

2. Activez la case à cocher en regard d’un nom d’appareil et, dans le panneau **Profil**, mettez à jour les paramètres disponibles \>**Enregistrer**.

    Si vous effectuez cette tâche avant qu’un utilisateur connecte l’appareil à Internet, le profil est appliqué au processus d’installation.

### <a name="delete-a-profile"></a>Supprimer un profil

1. Sur la page **Préparer Windows**, choisissez l'onglet **Profils**.

2. Activez la case à cocher en regard d’un nom d’appareil, puis dans le panneau **Profil**, sélectionnez **Supprimer le profil**\>**Enregistrer**.

    Lorsque vous supprimez un profil, il est supprimé de l'appareil ou du groupe d'appareils auquel il a été affecté.

### <a name="remove-a-profile"></a>Retirer un profil

1. Sur la page **Préparer Windows**, choisissez l'onglet **Appareils**.

2. Activez la case à cocher en regard d’un nom d’appareil, puis dans le panneau **Appareil**, choisissez **Aucun** dans la liste déroulante **profil affecté** \>**Enregistrer**.

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)
