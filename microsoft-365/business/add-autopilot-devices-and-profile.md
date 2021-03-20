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
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: be5b6d90-3344-4c5e-bf40-5733eb845beb
description: Découvrez comment utiliser Windows AutoPilot pour configurer de nouveaux appareils Windows 10 pour votre entreprise afin qu’ils sont prêts à être utilisés par les employés.
ms.openlocfilehash: 75cc51b889f8673de8dba2357c777de47fd0d296
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50913499"
---
# <a name="use-the-step-by-step-guide-to-add-autopilot-devices-and-profile"></a>Utiliser le guide étape par étape pour ajouter des appareils et un profil Autopilot

Vous pouvez utiliser Windows AutoPilot pour configurer de nouveaux appareils **Windows** 10 pour votre entreprise afin qu’ils sont prêts à être utilisés lorsque vous les donnez à vos employés.
  
## <a name="device-requirements"></a>Configuration requise de l’appareil

Les appareils doivent répondre aux exigences ci-après :
  
- Windows 10, version 1703 ou ultérieure
    
- Nouveaux appareils qui n’ont pas fait l’expérience d’utilisation de Windows out-of-box
    
## <a name="use-the-setup-guide-to-create-devices-and-profiles"></a>Utiliser le guide de configuration pour créer des appareils et des profils

[![Étiquette vous informant le centre d’administration est en train de changer et vous pouvez trouver plus de détails à ce sujet à l’adresse aka.ms/aboutM365preview.](../media/m365admincenterchanging.png)](/office365/admin/microsoft-365-admin-center-preview)

Si vous n’avez pas encore créé de groupes d’appareils ou de profils, la meilleure façon de commencer consiste à utiliser le guide pas à pas. Vous pouvez également ajouter [des appareils et](create-and-edit-autopilot-devices.md) leur attribuer des [profils](create-and-edit-autopilot-profiles.md) sans utiliser le guide. 
  
1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

2. Dans le volet de navigation de gauche, **sélectionnez Appareils** \> **AutoPilot**.

    ![Dans le Centre d’administration, choisissez les appareils, puis AutoPilot.](../media/AutoPilot.png)
  
2. Dans la page **AutoPilot,** cliquez ou appuyez sur **Le guide de démarrage.**
    
    ![Click Start guide for step-by-step instructions for Autopilot.](../media/31662655-d1e6-437d-87ea-c0dec5da56f7.png)
  
3. Dans la page **Télécharger le fichier .csv** avec la liste des appareils, accédez à un emplacement où vous avez préparé . Fichier CSV, puis **Ouvrir** \> **suivant**. Le fichier doit avoir trois en-têtes :
    
    - Colonne A : Numéro de série de l'appareil
    
    - Colonne B : ID de produit Windows
    
    - Colonne C : Hachage du matériel
    
    Vous pouvez obtenir ces informations auprès de votre fournisseur de matériel ou utiliser le [script PowerShell Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) pour générer un fichier CSV. 
    
    Pour plus d'informations, voir [Fichier CSV de liste d'appareils](../admin/misc/device-list.md). Vous pouvez également télécharger un exemple de fichier sur la page **Charger un fichier .csv avec la liste des appareils**. 
    
> [!NOTE]
> Ce script utilise WMI pour récupérer les propriétés nécessaires pour qu’un client enregistre un appareil auprès de Windows Autopilot. Notez qu’il est normal que le fichier CSV résultant ne collecte pas de valeur d’ID de produit Windows (PKID), car cela n’est pas obligatoire pour inscrire un appareil et la valeur PKID null dans le fichier CSV de sortie est parfaitement correct. Seuls le numéro de série et le hachage matériel seront remplis.
    
4. Dans la page **Attribuer un profil,** vous pouvez choisir un profil existant ou en créer un nouveau. Si vous n’en avez pas encore, vous serez invité à en créer un. 
    
    Un proﬁl est un ensemble de paramètres qui peuvent être appliqués à un seul appareil ou à un groupe d'appareils.
    
    Les fonctionnalités par défaut sont requises et sont définies automatiquement. Les fonctionnalités par défaut sont :
    
    - Ignorez l’inscription de Cortana, OneDrive et OEM.
    
    - Créez une expérience de connexion avec l'identité de votre entreprise.
    
    - Connectez vos appareils à des comptes Azure Active Directory et inscrivez-les automatiquement pour qu’ils soient gérés par Microsoft 365 Business Premium.
    
    Pour plus d’informations, voir à propos des paramètres de [profil AutoPilot.](autopilot-profile-settings.md) 
    
5. Les autres paramètres sont **Ignorer les paramètres de confidentialité** et **Ne pas autoriser l'utilisateur à devenir administrateur local**. Ils sont tous les deux définis sur **Désactivé** par défaut. 
    
    Sélectionnez **Suivant**.
    
6. Vous avez terminé d’indiquer que le profil que vous avez créé (ou choisi) sera appliqué au groupe **d’appareils** que vous avez créé en téléchargeant la liste des appareils. Les paramètres seront en vigueur lorsque les utilisateurs de l’appareil se connectent ensuite. Sélectionnez **Fermer**.
