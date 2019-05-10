---
title: Utiliser le guide étape par étape pour ajouter des appareils et un profil Autopilot
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: be5b6d90-3344-4c5e-bf40-5733eb845beb
description: Découvrez comment utiliser Windows AutoPilot pour configurer de nouveaux appareils Windows 10 pour votre entreprise.
ms.openlocfilehash: 8c4a14b4b9dcbf7a30c1e6e0bdd53418a1ab8a03
ms.sourcegitcommit: db1dfb2df2c2f7beced3b57bc772d106c189e88a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "33660663"
---
# <a name="use-the-step-by-step-guide-to-add-autopilot-devices-and-profile"></a>Utiliser le guide étape par étape pour ajouter des appareils et un profil Autopilot

Vous pouvez utiliser Windows AutoPilot pour configurer de **nouveaux** appareils Windows 10 pour votre entreprise afin qu’ils soient prêts à être utilisés dès que vous les fournissez à vos employés.
  
## <a name="device-requirements"></a>Configuration requise de l’appareil

Les appareils doivent respecter ces exigences :
  
- Windows 10, version 1703 ou supérieure.
    
- Nouveaux appareils qui ne sont pas issus d'une expérience Windows prête à l'emploi.
    
## <a name="use-the-setup-guide-to-create-devices-and-profiles"></a>Utiliser le guide de configuration pour créer des appareils et des profils

![Bannière pointant vers https://aka.ms/aboutM365preview.](media/m365admincenterchanging.png)

Si vous n'avez pas encore créé de groupes d'appareils et de profils, la meilleure façon de commencer consiste à utiliser le guide détaillé, mais vous pouvez également [ajouter des appareils](create-and-edit-autopilot-devices.md) et leur [attribuer des profils](create-and-edit-autopilot-profiles.md) sans utiliser le guide. 
  
1. Accédez au centre d’administration à <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>l’adresse.

2. Sur le côté gauche, sélectionnez **périphériques** \> **AutoPilot**.

    ![Dans le centre d’administration, sélectionnez périphériques, puis AutoPilot.](media/AutoPilot.png)
  
2. Sur la **** page AutoPilot, cliquez ou appuyez sur **Guide de démarrage**.
    
    ![Click Start guide for step-by-step instructions for Autopilot.](media/31662655-d1e6-437d-87ea-c0dec5da56f7.png)
  
3. Sur la page **Charger un fichier .csv avec une liste d'appareils**, recherchez l'emplacement où vous avez préparé le fichier .csv, puis cliquez sur **Ouvrir** \> **Suivant**. Le fichier doit avoir trois en-têtes :
    
  - Colonne A : Numéro de série de l'appareil
    
  - Colonne B : ID de produit Windows
    
  - Colonne C : Hachage du matériel
    
    Vous pouvez obtenir ces informations à partir de votre fournisseur de matériel ou vous pouvez utiliser le [script Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) qui génèrera un fichier CSV. 
    
    Pour plus d'informations, voir [Fichier CSV de liste d'appareils](https://support.office.com/article/932e3676-2491-49f0-9177-d893d2f5276e). Vous pouvez également télécharger un exemple de fichier sur la page **Charger un fichier .csv avec la liste des appareils**. 
    
4. Sur la page **Attribuer un profil**, vous pouvez choisir un profil existant ou en créer un. Si vous n'en avez pas encore, vous êtes invité à en créer un nouveau. 
    
    Un proﬁl est un ensemble de paramètres qui peuvent être appliqués à un seul appareil ou à un groupe d'appareils.
    
    Les fonctionnalités par défaut sont obligatoires et seront définies automatiquement. Les fonctionnalités par défaut sont :
    
  - L'inscription Cortana, OneDrive et OEM est ignorée.
    
  - Créez une expérience de connexion avec l'identité de votre entreprise.
    
  - Vos appareils vont être connectés à des comptes Azure Active Directory et automatiquement inscrits pour être gérés par Microsoft 365 Entreprise.
    
    Pour plus d'informations, voir
    
    [À propos des paramètres du profil AutoPilot](autopilot-profile-settings.md) 
    
5. Les autres paramètres sont **Ignorer les paramètres de confidentialité** et **Ne pas autoriser l'utilisateur à devenir administrateur local**. Ils sont tous les deux définis sur **Désactivé** par défaut. 
    
    Sélectionnez **Suivant**.
    
6. La page **Vous avez terminé** indique que le profil que vous avez créé (ou choisi) sera appliqué au groupe d'appareils que vous avez créé en chargeant la liste d'appareils. Ces paramètres seront appliqués lors de la prochaine connexion des utilisateurs de l'appareil. Choisissez **Fermer**.
    