---
title: À propos des paramètres du profil AutoPilot
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: conceptual
f1_keywords:
- ZTDProfileSettings
- O365E_ZTDProfileSettings
- BCS365_ZTDProfileSettings
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 99bfbf81-e719-4630-9b0f-c187edfa1f8a
description: Les profils AutoPilot vous aident à contrôler la façon dont Windows est installé sur les appareils des utilisateurs. Les profils contiennent des paramètres par défaut et facultatifs comme ignorer l’installation de Cortana.
ms.openlocfilehash: 100de5e9548f901008d3ae154ac5a237ef265ffb
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44401031"
---
# <a name="about-autopilot-profile-settings"></a>À propos des paramètres du profil AutoPilot

## <a name="autopilot-profile-settings"></a>Paramètres de profil AutoPilot

Vous pouvez utiliser les profils AutoPilot pour contrôler la façon dont Windows est installé sur les appareils des utilisateurs. Les profils contiennent les paramètres suivants.
  
 **Fonctionnalités autoPilot par défaut (obligatoires) qui sont définies automatiquement :**
  
|**Paramètre**|**Description**|
|:-----|:-----|
|Ignorer l’inscription de Cortana, OneDrive et OEM  <br/> |Ignore l’installation d’applications grand public telles que Cortana et OneDrive personnel. L’utilisateur de l’appareil peut les installer ultérieurement tant que l’utilisateur est un administrateur local sur l’appareil. L’inscription du fabricant d’origine est ignorée, car l’appareil sera géré par Microsoft 365 Business Premium.  <br/> |
|Expérience de signature avec la marque de votre entreprise  <br/> |Si votre entreprise dispose d’une marque Ajouter votre marque de société à la page de signature [Microsoft 365,](https://docs.microsoft.com/microsoft-365/admin/setup/customize-sign-in-page)l’utilisateur de l’appareil aura cette expérience lors de la signature.  <br/> |
|Inscription automatique mdm avec des comptes AAD configurés.  <br/> |L’identité de l’utilisateur est gérée par Azure Active Directory et les utilisateurs se connectent à Windows et Microsoft 365 avec leurs informations d’identification Microsoft 365 Business Premium.  <br/> |
   
 **Paramètres facultatifs :**
  
|**Paramètre**|**Description**|
|:-----|:-----|
|Ignorer les paramètres de confidentialité (par défaut)  <br/> |Si cette option est définie sur **On,** l’utilisateur de l’appareil ne verra pas le contrat de licence pour l’appareil et Windows lorsqu’il se connecté pour la première fois.  <br/> |
|Ne pas autoriser l’utilisateur à devenir l’administrateur local  <br/> |Si cette option est définie sur **Activé,** l’utilisateur de l’appareil ne pourra pas installer d’applications personnelles, telles que Cortana.<br/> |
   
