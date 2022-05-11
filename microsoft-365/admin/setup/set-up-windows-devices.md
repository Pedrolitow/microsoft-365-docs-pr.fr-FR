---
title: Configurer des appareils Windows pour les utilisateurs Microsoft 365 Business Premium
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
description: Configurez Windows appareils exécutant Windows 10 Professionnel pour Microsoft 365 Business Premium utilisateurs, en activant la gestion centralisée et les contrôles de sécurité.
ms.openlocfilehash: b9c8a5eb724a74959983e86dcdcb8f2f8f96b540
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65318577"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>Configurer des appareils Windows pour les utilisateurs Microsoft 365 Business Premium

## <a name="before-you-begin"></a>Avant de commencer

Avant de pouvoir configurer Windows appareils pour Microsoft 365 Business Premium utilisateurs, assurez-vous que tous les appareils Windows s’exécutent Windows 10 Professionnel, version 1703 (Creators Update) ou Windows 11 Professionnel. 

Windows 10 Professionnel (ou Windows 11 Professionnel) est un prérequis pour le déploiement de Windows 10 Business, qui est un ensemble de services cloud et de fonctionnalités de gestion des appareils qui complètent Windows 10 Professionnel et Windows 11 Professionnel et activer la gestion centralisée et les contrôles de sécurité de Microsoft 365 Business Premium.

[En savoir plus sur les exigences pour Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Professionnel et Windows 11 Professionnel

Si vous avez Windows appareils exécutant des versions antérieures de Windows, telles que Windows 7 Pro, Windows 8 Professionnel ou Windows 8.1 Professionnel, votre Microsoft 365 Business Premium  l’abonnement vous permet de mettre à niveau ces appareils vers Windows 10 Professionnel ou Windows 11 Professionnel.
  
Pour plus d’informations sur la mise à niveau des appareils Windows, consultez les articles suivants :

- [Mettre à niveau Windows Home vers Windows Pro](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [Mettre à niveau vers Windows 10 Professionnel](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)
  
Une fois la mise à niveau terminée, consultez [Vérifier que l’appareil est connecté à Azure AD](#verify-the-device-is-connected-to-azure-ad) pour vérifier que vous avez effectué la mise à niveau ou pour vous assurer que la mise à niveau a fonctionné.

## <a name="join-windows-devices-to-your-organizations-azure-ad"></a>Joindre Windows appareils à Azure AD de votre organisation

Lorsque tous les appareils Windows de votre entreprise exécutent Windows 10 Professionnel ou Windows 11 Professionnel, vous pouvez joindre ces appareils au Azure Active Directory de votre organisation (Azure AD). 

1. Sur un appareil Windows, sélectionnez le logo Windows, puis l’icône Paramètres.
  
2. Dans **Paramètres**, accédez au **Connecter** **professionnel ou scolaire** \> **AccountsAccess** > .
  
3. Tapez votre adresse e-mail, puis choisissez **Suivant**.

4. Suivez les invites pour terminer le processus.

## <a name="verify-the-device-is-connected-to-azure-ad"></a>Vérifiez que l’appareil est connecté à Azure AD

Pour vérifier votre état de synchronisation, dans la page **Accès professionnel ou scolaire** dans **Paramètres**, sélectionnez la zone **Connecté à** _ \<organization name\> _ pour exposer les boutons **Informations** et **Déconnexion**. Choisissez **Informations** pour obtenir votre état de synchronisation. 
  
Dans la page **État** de synchronisation, choisissez **Synchroniser** pour obtenir les dernières stratégies de gestion des appareils mobiles sur le PC.  
  
## <a name="next-steps"></a>Étapes suivantes

Pour configurer vos appareils mobiles, consultez [Configurer des appareils mobiles pour Microsoft 365 Business Premium utilisateurs](set-up-mobile-devices.md), 

Pour renforcer la protection, consultez [les meilleures pratiques pour sécuriser Microsoft 365 pour les plans d’entreprise](../security-and-compliance/secure-your-business-data.md).
  

