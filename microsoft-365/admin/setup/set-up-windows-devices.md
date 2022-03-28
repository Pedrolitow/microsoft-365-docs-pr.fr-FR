---
title: Configurer des Windows pour les Microsoft 365 Business Premium utilisateurs
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: 2d7ff45e-0da0-4caa-89a9-48cabf41f193
description: Configurer des appareils Windows en cours d Windows 10 Professionnel pour Microsoft 365 Business Premium utilisateurs, ce qui permet de centraliser la gestion et les contrôles de sécurité.
ms.openlocfilehash: f64114ac6a117ac3eacc9b6aa9de31366e847f33
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403586"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>Configurer des Windows pour les Microsoft 365 Business Premium utilisateurs

## <a name="before-you-begin"></a>Avant de commencer

Avant de configurer des appareils Windows pour les utilisateurs Microsoft 365 Business Premium, assurez-vous que tous les appareils Windows exécutent Windows 10 Professionnel, version 1703 (Creators Update) ou Windows 11 Professionnel. 

Windows 10 Professionnel (ou Windows 11 Professionnel) est une condition préalable au déploiement de Windows 10 Business, qui est un ensemble de services cloud et de fonctionnalités de gestion des appareils qui complètent Windows 10 Professionnel et Windows 11 Professionnel et activez les contrôles de sécurité et de gestion centralisés des Microsoft 365 Business Premium.

[En savoir plus sur les conditions requises pour Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Professionnel et Windows 11 Professionnel

Si vous avez des Windows exécutant des versions antérieures de Windows, tels que Windows 7 Pro, Windows 8 Professionnel ou Windows 8.1 Professionnel, votre Microsoft 365 Business Premium  vous permet de mettre à niveau ces appareils vers Windows 10 Professionnel ou Windows 11 Professionnel.
  
Pour plus d’informations sur la mise à niveau Windows appareils mobiles, consultez les articles suivants :

- [Mettre à niveau Windows à la page d’Windows Pro](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [Mettre à niveau vers Windows 10 Professionnel](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)
  
Après avoir mis à niveau, voir [Vérifier](#verify-the-device-is-connected-to-azure-ad) que l’appareil est connecté à Azure AD pour vérifier que vous avez bien mis à niveau ou pour vous assurer que la mise à niveau a fonctionné.

## <a name="join-windows-devices-to-your-organizations-azure-ad"></a>Joindre Windows appareils aux appareils de votre Azure AD

Lorsque tous les appareils Windows de votre entreprise exécutent Windows 10 Professionnel ou Windows 11 Professionnel, vous pouvez joindre ces appareils au Azure Active Directory (Azure AD) de votre organisation. 

1. Sur un Windows, sélectionnez le logo Windows, puis l’icône Paramètres’écran.
  
2. In **Paramètres**, go to **AccountsAccess** >  **work or school** \> **Connecter**.
  
3. Tapez votre adresse e-mail, puis choisissez **Suivant**.

4. Suivez les invites pour terminer le processus.

## <a name="verify-the-device-is-connected-to-azure-ad"></a>Vérifiez que l’appareil est connecté à Azure AD

Pour vérifier votre état de synchronisation, sur la page **Access** professionnel ou scolaire dans **Paramètres**, sélectionnez la zone Connecté **à _ _** \<organization name\> pour exposer les boutons **Informations et** **Déconnexion**. Choisissez **Info** pour obtenir votre état de synchronisation. 
  
Dans la page **État de synchronisation** , sélectionnez **Synchroniser** pour obtenir les dernières stratégies de gestion des appareils mobiles sur le PC.  
  
## <a name="next-steps"></a>Étapes suivantes

Pour configurer vos appareils mobiles, voir [Configurer des appareils mobiles pour Microsoft 365 Business Premium utilisateurs](set-up-mobile-devices.md), 

Pour renforcer la protection, consultez [les 10 principales façons de sécuriser Microsoft 365 pour les plans d’entreprise](../security-and-compliance/secure-your-business-data.md).
  
