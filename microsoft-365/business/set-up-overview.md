---
title: Vue d’ensemble de la configuration
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
f1_keywords:
- O365E_M365SetupBanner
- BCS365_M365SetupBanner
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: Découvrez les étapes de configuration de Microsoft 365 Business Premium, de l’abonnement, à l’ajout d’un domaine et des utilisateurs, à la configuration de stratégies de sécurité, etc.
ms.openlocfilehash: 9d92aefb3b5666bb7c2fd2e13c9a00f074f107a7
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50912487"
---
# <a name="overview-of-setup"></a>Vue d’ensemble de la configuration

Regardez une courte vidéo sur la configuration de Microsoft 365 Business Premium.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4jZwg] 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816).

La plupart des étapes de configuration peuvent être réalisées dans l’installation guidée, mais les autres options sont également répertoriées.

## <a name="step-1-add-your-domain-and-users"></a>Étape 1 : Ajouter votre domaine et vos utilisateurs

   - **[Ajoutez votre domaine](set-up.md#add-your-domain-to-personalize-sign-in)** (si vous avez acheté votre domaine lors [de](sign-up.md)l’inscription, cette étape est déjà effectuée).)

   - **Ajouter des utilisateurs**. Vous pouvez ajouter des utilisateurs de l’une des trois manières possibles :
        - Dans la [configuration guidée](set-up.md#add-users-in-the-wizard).
        - Utilisez la synchronisation d’annuaires pour ajouter des utilisateurs à l’aide [d’Azure AD Connect](../enterprise/set-up-directory-synchronization.md) si vous avez un annuaire Active Directory local.
        - Vous pouvez également ajouter [des utilisateurs ultérieurement](../admin/add-users/add-users.md) dans le Centre d’administration.
## <a name="step-2-set-up-security-policies-and-configure-devices"></a>Étape 2 : Configurer des stratégies de sécurité et des appareils 

  - Utilisez la [configuration guidée pour](set-up.md#protect-your-organization) configurer les stratégies d’appareil. 
  - Vous pouvez également en ajouter ou les modifier ultérieurement dans le Centre d’administration [et](view-policies-and-devices.md) dans le [portail Intune.](/intune/tutorial-walkthrough-intune-portal)
  - L’Assistant Installation configurera également les paramètres de protection contre les menaces de base et de protection contre la perte de données.
  
  Outre les paramètres de sécurité de l’Assistant Installation, vous pouvez renforcer votre sécurité en ajoutant les paramètres suivants :

- **Protection contre les programmes malveillants par courrier électronique**
- **Anti-hameçonnage dans Defender pour Office 365**
- **Archivage Exchange Online**
- **Azure Information Protection (Plan1)**

Pour commencer, voir augmenter la [protection contre les menaces](increase-threat-protection.md) [et configurer les fonctionnalités de conformité.](set-up-compliance.md)

Consultez également les 10 principales façons de sécuriser [votre Microsoft 365 Business Premium](/office365/admin/security-and-compliance/secure-your-business-data) pour obtenir une feuille de route des meilleures pratiques en matière de sécurité.

## <a name="step-3-set-up-and-manage-windows-10-devices"></a>Étape 3 : Configurer et gérer les appareils Windows 10

Une fois l’installation guidée terminée, vous devez protéger tous les ordinateurs Windows 10 de votre organisation.
  
- Windows 10 Professionnel [](pre-requisites-for-data-protection.md) est une condition préalable pour Microsoft 365 Business Premium, mais si vous avez Windows 7 Professionnel, Windows 8 Professionnel ou Windows 8.1 Professionnel, votre abonnement vous donne droit à une mise à niveau vers [Windows 10 Professionnel.](./upgrade-to-windows-pro-creators-update.md)
- Suivez les étapes de [la sécurisation des PC Windows 10](secure-win-10-pcs.md) pour configurer des stratégies pour les appareils Windows 10.

Lorsque vous joignez un appareil Windows 10 à Azure AD, les stratégies que vous définissez pour les ordinateurs Windows 10 s’y appliquent. Pour plus d’informations, voir [Configurer des appareils Windows pour les utilisateurs de Microsoft 365.](set-up-windows-devices.md)

## <a name="step-4-install-microsoft-365-apps-for-business"></a>Étape 4 : Installer Microsoft 365 Apps for business
- Vous pouvez installer automatiquement Office sur les appareils Windows à l’aide de [l’Assistant Installation.](set-up.md#deploy-office-365-client-apps)
- Permet aux [utilisateurs d’installer des applications Office](/office365/admin/setup/install-applications) pour Windows et les appareils.
     
## <a name="advanced"></a>Avancé
- **Utiliser Autopilot pour configurer de nouveaux appareils**
            
     Vous pouvez utiliser [Windows Autopilot](add-autopilot-devices-and-profile.md) pour pré-configurer automatiquement de nouveaux appareils **Windows** 10 [](https://www.microsoft.com/solution-providers/search) pour un utilisateur, mais il peut être plus facile d’obtenir un partenaire qui peut le faire pour vous. Vous pouvez également vous rendre dans [le Microsoft Store](https://go.microsoft.com/fwlink/?linkid=874598)et demander à un expert en technologie cloud de configurer les nouveaux appareils que vous achetez.

- **Accès aux ressources locales**

     - Si votre organisation utilise Windows Server Active Directory en local, vous pouvez configurer Microsoft 365 Business Premium pour protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale. Suivez les étapes de l’étape Activer les appareils Windows 10 joints à un domaine pour qu’ils soient gérés par [Microsoft 365 Business Premium](manage-windows-devices.md) pour le configurer. Il s’agit de la méthode préférée, et les appareils dans cet état sont appelés appareils joints à Azure AD hybride.

    - Si votre entreprise possède un Active Directory local qui contient certaines ressources locales (telles que des partages de fichiers et des imprimantes), vous pouvez accorder à vos appareils joints à Azure AD un accès à ces ressources en suivant les étapes ci-après : Accéder aux ressources locales à partir d’un appareil joint à Azure AD dans [Microsoft 365 Business Premium](access-resources.md).

## <a name="see-also"></a>Voir aussi

[Vidéos de formation Microsoft 365 Entreprise](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816)