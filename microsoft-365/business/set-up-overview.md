---
title: Vue d’ensemble de la configuration
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
ms.openlocfilehash: 008a5c51698589667acc0d01649f67dab33b4c58
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52245061"
---
# <a name="overview-of-setup"></a>Vue d’ensemble de la configuration

Regardez une courte vidéo sur Microsoft 365 Business Premium configuration.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4jZwg] 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../business-video/index.yml).

La plupart des étapes de configuration peuvent être réalisées dans l’installation guidée, mais les autres options sont également répertoriées.

## <a name="step-1-add-your-domain-and-users"></a>Étape 1 : Ajouter votre domaine et vos utilisateurs

   - **[Ajoutez votre domaine](set-up.md#add-your-domain-to-personalize-sign-in)** (si vous avez acheté votre domaine lors [de](sign-up.md)l’inscription, cette étape est déjà effectuée).)

   - **Ajouter des utilisateurs**. Vous pouvez ajouter des utilisateurs de l’une des trois manières possibles :
        - Dans la [configuration guidée](set-up.md#add-users-in-the-wizard).
        - Utilisez la synchronisation d’annuaires pour ajouter des utilisateurs à l’aide [d’Azure AD Connecter](../enterprise/set-up-directory-synchronization.md) si vous avez un annuaire Active Directory local.
        - Vous pouvez également ajouter [des utilisateurs ultérieurement](../admin/add-users/add-users.md) dans le Centre d’administration.
## <a name="step-2-set-up-security-policies-and-configure-devices"></a>Étape 2 : Configurer des stratégies de sécurité et des appareils 

  - Utilisez la [configuration guidée pour](set-up.md#protect-your-organization) configurer les stratégies d’appareil. 
  - Vous pouvez également en ajouter ou les modifier ultérieurement dans le [Centre](view-policies-and-devices.md) d’administration et dans le [portail Intune.](/intune/tutorial-walkthrough-intune-portal)
  - L’Assistant Installation configurera également les paramètres de protection contre les menaces de base et de protection contre la perte de données.
  
  Outre les paramètres de sécurité de l’Assistant Installation, vous pouvez renforcer votre sécurité en ajoutant les paramètres suivants :

- **Protection contre les programmes malveillants par courrier électronique**
- **Anti-hameçonnage dans Defender pour Office 365**
- **Archivage Exchange Online**
- **Azure Information Protection (Plan1)**

Pour commencer, voir augmenter la [protection contre les menaces](increase-threat-protection.md) [et configurer les fonctionnalités de conformité.](set-up-compliance.md)

Découvrez également [les 10 principales façons](/office365/admin/security-and-compliance/secure-your-business-data) de sécuriser votre Microsoft 365 Business Premium pour obtenir un plan des meilleures pratiques en matière de sécurité.

## <a name="step-3-set-up-and-manage-windows-10-devices"></a>Étape 3 : Configurer et gérer Windows 10 appareils

Une fois la configuration guidée terminée, vous devez protéger tous les ordinateurs Windows 10 de votre organisation.
  
- Windows 10 Professionnel est une [](pre-requisites-for-data-protection.md) condition préalable pour Microsoft 365 Business Premium, mais si vous avez Windows 7 Pro, Windows 8 Professionnel ou Windows 8.1 Professionnel, votre abonnement vous donne droit à une mise à niveau vers [Windows 10 Professionnel](./upgrade-to-windows-pro-creators-update.md).
- Suivez les étapes de [l’Windows 10 sécurisé pour](secure-win-10-pcs.md) configurer des stratégies pour Windows 10 appareils.

Lorsque vous joignez un Windows 10 à Azure AD, les stratégies que vous définissez pour Windows 10 ordinateurs s’y appliquent. Pour plus d’informations, voir [Configurer des Windows pour les Microsoft 365 utilisateurs.](set-up-windows-devices.md)

## <a name="step-4-install-microsoft-365-apps-for-business"></a>Étape 4 : Installer Applications Microsoft 365 pour les PME
- Vous pouvez installer automatiquement les Office sur les Windows à l’aide de [l’Assistant Installation.](set-up.md#deploy-office-365-client-apps)
- Laissez les [utilisateurs installer Office applications pour](/office365/admin/setup/install-applications) Windows et les appareils.
     
## <a name="advanced"></a>Avancé
- **Utiliser Autopilot pour configurer de nouveaux appareils**
            
     Vous pouvez utiliser [Windows Autopilot](add-autopilot-devices-and-profile.md) pour pré-configurer automatiquement de nouveaux appareils **Windows 10** pour un utilisateur, [](https://www.microsoft.com/solution-providers/search) mais il peut être plus facile d’obtenir un partenaire qui peut le faire pour vous. Vous pouvez également vous [Microsoft Store](https://go.microsoft.com/fwlink/?linkid=874598)et demander à un expert en technologie cloud de configurer de nouveaux appareils que vous achetez.

- **Accès aux ressources locales**

     - Si votre organisation utilise Windows Server Active Directory localement, vous pouvez configurer Microsoft 365 Business Premium pour protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale. Suivez les étapes de [la procédure d’Windows 10 de](manage-windows-devices.md) domaine à gérer par Microsoft 365 Business Premium pour configurer cette procédure. Il s’agit de la méthode préférée, et les appareils dans cet état sont appelés appareils joints à Azure AD hybride.

    - Si votre entreprise possède un Active Directory local qui contient certaines ressources locales (telles que des partages de fichiers et des imprimantes), vous pouvez accorder à vos appareils joints à Azure AD l’accès à ces ressources en suivant les étapes ci-après : Accéder aux ressources locales à partir d’un appareil joint à [Azure AD](access-resources.md)dans Microsoft 365 Business Premium .

## <a name="related-content"></a>Contenu associé

[Microsoft 365 vidéos de formation pour les entreprises](../business-video/index.yml) (page de liens)