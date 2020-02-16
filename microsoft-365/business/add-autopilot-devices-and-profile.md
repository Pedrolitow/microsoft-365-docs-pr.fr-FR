---
title: Utiliser le guide étape par étape pour ajouter des appareils et un profil Autopilot
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.collection:
- M365-subscription-management
- M365-identity-device-management
localization_priority: Normal
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: be5b6d90-3344-4c5e-bf40-5733eb845beb
description: Découvrez comment utiliser Windows AutoPilot pour configurer de nouveaux appareils Windows 10 pour votre entreprise.
ms.openlocfilehash: e5774b1e2079a5249e0f6e9e7142de19268253b5
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42068528"
---
# <a name="use-the-step-by-step-guide-to-add-autopilot-devices-and-profile"></a>Utiliser le guide étape par étape pour ajouter des appareils et un profil Autopilot

Vous pouvez utiliser Windows AutoPilot pour configurer de **nouveaux** appareils Windows 10 pour votre entreprise afin qu’ils soient prêts à être utilisés lorsque vous les communiquez à vos employés.
  
## <a name="device-requirements"></a>Configuration requise de l’appareil

Les appareils doivent respecter les conditions suivantes :
  
- Windows 10, version 1703 ou ultérieure
    
- Nouveaux appareils qui n’ont pas fait l’expérience de Windows out-of-Box
    
## <a name="use-the-setup-guide-to-create-devices-and-profiles"></a>Utiliser le guide de configuration pour créer des appareils et des profils

[![Étiquette vous informant le centre d’administration est en train de changer et vous pouvez trouver plus de détails à ce sujet à l’adresse aka.ms/aboutM365preview.](../media/m365admincenterchanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview)

Si vous n’avez pas encore créé de groupes d’appareils ou de profils, la meilleure façon de commencer est d’utiliser le guide pas à pas. Vous pouvez également [Ajouter des appareils](create-and-edit-autopilot-devices.md) et leur [affecter des profils](create-and-edit-autopilot-profiles.md) sans utiliser le guide. 
  
1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

2. Dans le volet de navigation de gauche, choisissez **appareils** \> **AutoPilot**.

    ![Dans le centre d’administration, sélectionnez périphériques, puis AutoPilot.](../media/AutoPilot.png)
  
2. Sur la page **AutoPilot** , cliquez ou appuyez sur **Guide de démarrage**.
    
    ![Click Start guide for step-by-step instructions for Autopilot.](../media/31662655-d1e6-437d-87ea-c0dec5da56f7.png)
  
3. Sur la page **Télécharger le fichier. csv avec la liste des périphériques** , accédez à l’emplacement où vous avez préparé. Fichier CSV, puis **ouvrez** \> **suivant**. Le fichier doit avoir trois en-têtes :
    
    - Colonne A : Numéro de série de l'appareil
    
    - Colonne B : ID de produit Windows
    
    - Colonne C : Hachage du matériel
    
    Vous pouvez obtenir ces informations auprès de votre fournisseur de matériel ou vous pouvez utiliser le [script PowerShell Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) pour générer un fichier CSV. 
    
    Pour plus d'informations, voir [Fichier CSV de liste d'appareils](https://support.office.com/article/932e3676-2491-49f0-9177-d893d2f5276e). Vous pouvez également télécharger un exemple de fichier sur la page **Charger un fichier .csv avec la liste des appareils**. 
    
4. Sur la page **attribuer un profil** , vous pouvez choisir un profil existant ou en créer un nouveau. Si vous n’en avez pas encore, vous serez invité à en créer un. 
    
    Un proﬁl est un ensemble de paramètres qui peuvent être appliqués à un seul appareil ou à un groupe d'appareils.
    
    Les fonctionnalités par défaut sont obligatoires et sont définies automatiquement. Les fonctionnalités par défaut sont :
    
    - Ignorez l’enregistrement de Cortana, OneDrive et OEM.
    
    - Créez une expérience de connexion avec l'identité de votre entreprise.
    
    - Connectez vos appareils aux comptes Azure Active Directory et inscrivez-les automatiquement pour qu’ils soient gérés par Microsoft 365 Business.
    
    Pour plus d’informations, consultez la rubrique [à propos des paramètres du profil AutoPilot](autopilot-profile-settings.md). 
    
5. Les autres paramètres sont **Ignorer les paramètres de confidentialité** et **Ne pas autoriser l'utilisateur à devenir administrateur local**. Ils sont tous les deux définis sur **Désactivé** par défaut. 
    
    Sélectionnez **Suivant**.
    
6. **Vous avez fini** d’indiquer que le profil que vous avez créé (ou choisi) sera appliqué au groupe de périphériques que vous avez créé en téléchargeant la liste des périphériques. Les paramètres seront appliqués lors de la prochaine connexion des utilisateurs de l’appareil. Sélectionnez **Fermer**.
    
