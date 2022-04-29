---
title: Sécuriser les appareils Windows
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
f1_keywords:
- O365E_BCSSetup4WindowsConfig
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ROBOTS: NO INDEX, NO FOLLOW
ms.assetid: 21e5551f-fa35-4f13-9418-f80d668b6a2b
description: Découvrez comment configurer les paramètres de la stratégie d’appareil par défaut que tout appareil Windows recevra lors de la connexion à son compte professionnel ou scolaire.
ms.openlocfilehash: d8a32dd5378ed1b16e6126e9091f2bd2bb8515f5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094635"
---
# <a name="secure-windows-devices"></a>Sécuriser les appareils Windows

Cet article s’applique à Microsoft 365 Business Premium.

Les paramètres que vous configurez ici font partie de la stratégie de périphérique par défaut pour Windows 10 ou 11. Tous les utilisateurs qui connectent un appareil Windows, y compris les appareils mobiles et les PC, en se connectant avec leur compte professionnel recevront automatiquement ces paramètres. Nous vous recommandons d'accepter la stratégie par défaut lors de la configuration et d'ajouter ultérieurement des stratégies ciblant des groupes spécifiques d'utilisateurs.
  
## <a name="settings-to-secure-windows-10-devices"></a>Paramètres de sécurisation des appareils Windows 10

Par défaut, tous les paramètres sont **activés**. Les paramètres suivants sont disponibles :<br/><br/>

|Paramètre  <br/> |Description  <br/> |
|:-----|:-----|
|Protéger les ordinateurs des virus et d'autres menaces à l'aide de l'antivirus Windows Defender  <br/> |L'antivirus Windows Defender doit être activé pour protéger les ordinateurs contre les risques liés à la connexion à internet.  <br/> |
|Protéger les ordinateurs contre les menaces web dans Microsoft Edge  <br/> |Active les paramètres Microsoft Edge qui protègent les utilisateurs contre les sites et téléchargements malveillants.  <br/> |
|Protéger les fichiers et dossiers sur PC contre un accès non autorisé avec BitLocker  <br/> |BitLocker protège les données en chiffrant les disques durs de l’ordinateur et en les protégeant contre l’exposition des données en cas de perte ou de vol d’un ordinateur. Pour plus d’informations, consultez [FAQ BitLocker](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).<br/> |
|Désactiver l'écran d'un appareil resté inactif pendant  <br/> |Permet d'assurer la protection des données d'entreprise lorsqu'un utilisateur est inactif. Il est possible qu'un utilisateur travaille dans un lieu public, par exemple un café, et s'éloigne ou soit distrait pendant un instant, laissant son appareil à la vue de tous. Ce paramètre vous permet de contrôler la durée pendant laquelle l'utilisateur peut être inactif avant l'extinction de l'écran.  <br/> |
