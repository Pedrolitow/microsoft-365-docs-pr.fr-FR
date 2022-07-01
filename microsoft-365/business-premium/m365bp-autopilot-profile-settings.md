---
title: À propos des paramètres du profil AutoPilot
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
f1.keywords:
- ZTDProfileSettings
- O365E_ZTDProfileSettings
- BCS365_ZTDProfileSettings
ms.service: o365-administration
ms.localizationpriority: high
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
description: Les profils AutoPilot vous aident à contrôler la façon dont Windows est installé sur les appareils utilisateur. Les profils contiennent des paramètres par défaut et facultatifs, comme ignorer l’installation de Cortana.
ms.openlocfilehash: 387346c68ad9ff85c3f97e4d8ca8b0ccdb28dcbd
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490247"
---
# <a name="about-autopilot-profile-settings"></a>À propos des paramètres du profil AutoPilot

## <a name="autopilot-profile-settings"></a>Paramètres du profil de pilote automatique

Vous pouvez utiliser des profils AutoPilot pour contrôler la façon dont Windows est installé sur les appareils utilisateur. Les profils contiennent les paramètres suivants.
  
## <a name="autopilot-default-features-required-that-are-set-automatically"></a>Fonctionnalités par défaut AutoPilot (obligatoires) définies automatiquement
  
| Setting | Description |
|:-----|:-----|
|Ignorer l’inscription Cortana, OneDrive et OEM  |Ignore l’installation d’applications grand public telles que Cortana et OneDrive personnel. L’utilisateur de l’appareil peut les installer ultérieurement tant que l’utilisateur est un administrateur local sur l’appareil. L’inscription du fabricant d’origine est ignorée, car l’appareil sera géré par Microsoft 365 Business Premium.  |
|Expérience de connexion avec votre marque d’entreprise  |Si votre entreprise dispose d’un [Ajouter la marque de votre entreprise à la page de connexion Microsoft 365](../admin/setup/customize-sign-in-page.md), l’utilisateur de l’appareil bénéficiera de cette expérience lors de la connexion.  |
|Inscription automatique MDM avec des comptes AAD configurés.  |L’identité de l’utilisateur est gérée par Azure Active Directory et les utilisateurs se connectent à Windows et Microsoft 365 avec leurs informations d’identification Microsoft 365 Business Premium.  |

## <a name="optional-settings"></a>Paramètres facultatifs
  
| Paramètre | Description |
|:-----|:-----|
|Ignorer les paramètres de confidentialité (désactivé par défaut)  |Si cette option est **activée,** l’utilisateur de l’appareil ne voit pas le contrat de licence de l’appareil et Windows lorsqu’il se connecte pour la première fois.  |
|Ne pas autoriser l’utilisateur à devenir l’administrateur local  |Si cette option est **activée,** l’utilisateur de l’appareil ne pourra pas installer d’applications personnelles, comme Cortana.|

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)