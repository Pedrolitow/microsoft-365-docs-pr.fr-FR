---
title: À propos des paramètres du profil AutoPilot
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
ms.custom: OKR_SMB_M365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 99bfbf81-e719-4630-9b0f-c187edfa1f8a
description: Les profils AutoPilot vous permettent de contrôler la manière dont Windows est installé sur les appareils utilisateur. Les profils contiennent des paramètres par défaut et facultatifs, comme ignorer l’installation de Cortana.
ms.openlocfilehash: cd66627943301f4a4f2410bafeff6074919ec29d
ms.sourcegitcommit: 6003d6da0a85c97357eb3dba3918eb145f381fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "37287472"
---
# <a name="about-autopilot-profile-settings"></a>À propos des paramètres du profil AutoPilot

## <a name="autopilot-profile-settings"></a>Paramètres du profil AutoPilot

Vous pouvez contrôler la façon dont Windows est installé sur les appareils utilisateur à l’aide des profils AutoPilot. Les profils contiennent les paramètres suivants.
  
 **Les fonctionnalités de AutoPilot par défaut (obligatoires) qui sont définies automatiquement :**
  
|**Paramètre**|**Description**|
|:-----|:-----|
|Ignorer Cortana, enregistrement OneDrive et OEM  <br/> |Ignore l’installation des applications grand public telles que Cortana et OneDrive personnel. L’utilisateur de l’appareil peut l’installer ultérieurement tant qu’il est administrateur local sur l’appareil. L’enregistrement du fabricant d’origine est ignoré car le périphérique sera géré par Microsoft 365 entreprise.  <br/> |
|Expérience de connexion avec la marque de votre entreprise  <br/> |Si votre société dispose d’une [page de connexion Add Your Company to Office 365 Signing](https://support.office.com/article/a1229cdb-ce19-4da5-90c7-2b9b146aef0a), l’utilisateur de l’appareil obtiendra cette expérience lors de la connexion.  <br/> |
|Auto-inscriptions MDM avec comptes AAD configurés.  <br/> |L’identité de l’utilisateur sera gérée par Azure Active Directory, et les utilisateurs se connecteront à Windows et Office 365 avec leurs informations d’identification d’entreprise Microsoft 365.  <br/> |
   
 **Paramètres facultatifs :**
  
|**Paramètre**|**Description**|
|:-----|:-----|
|Ignorer les paramètres de confidentialité (désactivés par défaut)  <br/> |Si cette option est **activée**, l’utilisateur de l’appareil ne verra pas le contrat de licence du périphérique et de Windows lorsqu’il se connecte pour la première fois.  <br/> |
|Ne pas autoriser l’utilisateur à devenir l’administrateur local  <br/> |Si cette option est **activée**, l’utilisateur de l’appareil ne peut pas installer d’applications personnelles, telles que Cortana.  <br/> |
   
