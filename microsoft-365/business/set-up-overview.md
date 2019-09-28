---
title: Vue d’ensemble de la configuration
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
ms.custom: OKR_SMB_M365
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: Vue d’ensemble des étapes de configuration pour Microsoft 365 Business.
ms.openlocfilehash: f156d236a783942ec06d457c9b7ca087d12d6f58
ms.sourcegitcommit: 6003d6da0a85c97357eb3dba3918eb145f381fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "37288572"
---
# <a name="overview-of-setup"></a>Vue d’ensemble de la configuration

La plupart des étapes de configuration peuvent être effectuées dans l’Assistant Installation, mais les autres options sont également répertoriées.


## <a name="step-1-add-your-domain-and-users"></a>Étape 1 : ajouter votre domaine et vos utilisateurs

   - **[Ajoutez votre domaine](set-up.md#add-your-domain-to-personalize-sign-in)** (si vous avez acheté votre domaine lors de l' [inscription](sign-up.md), cette étape est déjà terminée).

    - **Ajouter des utilisateurs**. Pour ce faire, vous pouvez procéder de l’une des manières suivantes :
        - Dans l' [Assistant](set-up.md#add-users-in-the-wizard).
        - Utilisez la synchronisation d’annuaires pour [Ajouter des utilisateurs à l’aide d’Azure ad Connect](https://docs.microsoft.com/office365/enterprise/set-up-directory-synchronization) si vous disposez d’un annuaire Active Directory local.
        - Vous pouvez également [Ajouter des utilisateurs ultérieurement](add-users-m365b.md) dans le centre d’administration.
## <a name="step-2-set-up-security-policies-and-configure-devices"></a>Étape 2 : configurer les stratégies de sécurité et configurer les appareils 

  - Utilisez l' [Assistant Installation](set-up.md#set-up-security-policies-and-device-configurations) pour configurer les stratégies d’appareil et de sécurité. 
  - Vous pouvez également en ajouter ou les modifier ultérieurement dans le [Centre d’administration](view-policies-and-devices.md) et dans le [portail Intune](https://docs.microsoft.com/intune/tutorial-walkthrough-intune-portal).
  - Outre les paramètres de sécurité de l’Assistant Installation, vous pouvez augmenter votre sécurité en ajoutant les paramètres suivants :

      - **Protection contre les programmes malveillants**
      - **Liens fiables de protection avancée contre les menaces**
      - **Pièces jointes fiables ATP**
      - **Protection contre le hameçonnage (ATP)**
      - **Archivage Exchange Online**
      - **Data Loss Prevention (DLP)**
      - **Azure information protection (plan1**)

          Pour commencer, consultez la rubrique [configurer des stratégies de sécurité avancées](set-up-advanced-security.md).

        Consultez également les [10 meilleures façons de sécuriser votre entreprise Microsoft 365](https://docs.microsoft.com/office365/admin/security-and-compliance/secure-your-business-data) pour obtenir une feuille de route des meilleures pratiques en matière de sécurité.

## <a name="step-3-set-up-and-manage-windows-10-devices"></a>Étape 3 : configurer et gérer les appareils Windows 10

   Lorsque vous joignez un appareil Windows 10 à Azure AD, les stratégies que vous avez configurées à l' [étape 2](#step-2-set-up-security-policies-and-configure-devices) sont appliquées.

   - Windows 10 professionnel est une [condition préalable](pre-requisites-for-data-protection.md) pour Microsoft 365 Business, mais si vous disposez de Windows 7 professionnel, Windows 8 professionnel ou Windows 8,1 Pro, votre abonnement vous donne droit à une [mise à niveau vers Windows 10 professionnel](https://docs.microsoft.com/microsoft-365/business/upgrade-to-windows-pro-creators-update).
    - Utilisez l' [Assistant Installation](set-up.md#set-up-security-policies-and-device-configurations) pour configurer des stratégies pour les appareils Windows 10.

## <a name="stes-4-install-office-365-business"></a>Stes 4 : installer Office 365 Business
- Vous pouvez installer automatiquement Office sur les appareils Windows à l’aide de l' [Assistant Installation](set-up.md#deploy-office-365-client-apps).
- [Installer automatiquement Office](auto-install-or-uninstall-office.md) à partir du centre d’administration.
- Autorisez les utilisateurs à [installer les applications Office](https://docs.microsoft.com/office365/admin/setup/install-applications) pour Windows et les appareils.
     
## <a name="advanced"></a>Avancé
- **Utiliser AutoPilot pour configurer de nouveaux appareils**
            
     Vous pouvez utiliser [Windows AutoPilot](add-autopilot-devices-and-profile.md) pour préconfigurer automatiquement les **nouveaux** appareils Windows 10 pour un utilisateur, mais il peut être plus facile d’obtenir un [partenaire](https://www.microsoft.com/solution-providers/search) qui peut le faire pour vous. Vous pouvez également accéder à [Microsoft Store](https://go.microsoft.com/fwlink/?linkid=874598) et demander à un spécialiste de la technologie Cloud de configurer de nouveaux appareils que vous achetez pour vous.

- **Accéder aux ressources locales**

     - Si votre organisation utilise Windows Server Active Directory en local, vous pouvez configurer Microsoft 365 entreprise pour protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale. Suivez les étapes de la procédure [activer les appareils Windows 10 appartenant à un domaine pour qu’ils soient gérés par Microsoft 365 Business](manage-windows-devices.md) pour le configurer. Il s’agit de la méthode préférée et les appareils dans cet État sont appelés appareils hybrides Azure AD.

    - Si votre entreprise dispose d’un annuaire local Active Directory qui contient certaines ressources locales (telles que des partages de fichiers et des imprimantes), vous pouvez donner à vos appareils joints à Azure AD l’accès à ces ressources en suivant les étapes ci-dessous : accéder à des [ressources locales à partir d’un Appareil rejoint Azure AD dans Microsoft 365 Business](access-resources.md).

  