---
title: À propos des paramètres du profil AutoPilot
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
f1.keywords:
- ZTDProfileSettings
- O365E_ZTDProfileSettings
- BCS365_ZTDProfileSettings
ms.service: o365-administration
ms.localizationpriority: medium
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
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 99bfbf81-e719-4630-9b0f-c187edfa1f8a
description: Les profils AutoPilot vous aident à contrôler Windows l’installation sur les appareils des utilisateurs. Les profils contiennent des paramètres par défaut et facultatifs tels que ignorer Cortana’installation.
ms.openlocfilehash: d0b1a15ef8279234868b94ab5c16e449a54cf62f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313872"
---
# <a name="about-autopilot-profile-settings"></a>À propos des paramètres du profil AutoPilot

## <a name="autopilot-profile-settings"></a>Paramètres de profil AutoPilot

> [!NOTE]
> Microsoft Defender for Business est en déploiement Microsoft 365 Business Premium clients, à partir du 1er mars 2022. Cette offre offre des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender pour les entreprises](../../security/defender-business/mdb-overview.md).

Vous pouvez utiliser les profils AutoPilot pour contrôler Windows sur les appareils des utilisateurs. Les profils contiennent les paramètres suivants.
  
 **Fonctionnalités autoPilot par défaut (obligatoires) qui sont définies automatiquement :**
  
|**Paramètre**|**Description**|
|:-----|:-----|
|Ignorer Cortana, OneDrive et l’inscription OEM  <br/> |Ignore l’installation d’applications grand public telles que Cortana et les OneDrive. L’utilisateur de l’appareil peut les installer ultérieurement tant que l’utilisateur est un administrateur local sur l’appareil. L’inscription du fabricant d’origine est ignorée, car l’appareil sera géré par Microsoft 365 Business Premium.  <br/> |
|Expérience de signature avec la marque de votre entreprise  <br/> |Si votre entreprise dispose d’une marque d’Microsoft 365 [page](../setup/customize-sign-in-page.md) de Microsoft 365, l’utilisateur de l’appareil pourra l’utiliser lors de la signature.  <br/> |
|Inscription automatique mdm avec des comptes AAD configurés.  <br/> |L’identité de l’utilisateur est gérée par Azure Active Directory et les utilisateurs se connectent à Windows et Microsoft 365 à l’Microsoft 365 Business Premium leurs informations d’identification.  <br/> |
   
 **Paramètres facultatifs :**
  
|**Paramètre**|**Description**|
|:-----|:-----|
|Ignorer les paramètres de confidentialité (par défaut)  <br/> |Si cette option est définie sur **On**, l’utilisateur de l’appareil ne verra pas le contrat de licence de l’appareil et ne Windows la première fois qu’il se connecté.  <br/> |
|Ne pas autoriser l’utilisateur à devenir l’administrateur local  <br/> |Si cette option est définie sur **On**, l’utilisateur de l’appareil ne peut pas installer d’applications personnelles, telles que Cortana.<br/> |

## <a name="see-also"></a>Voir aussi

[10 principales façons de sécuriser les Microsoft 365 pour les plans d’entreprise](../security-and-compliance/secure-your-business-data.md)