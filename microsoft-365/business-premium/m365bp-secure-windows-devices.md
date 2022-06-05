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
ms.openlocfilehash: 5ac09788d609752d12a6ae6efadfa8739c5a4f9a
ms.sourcegitcommit: c216ffa5da8f431e4380bb133a234ae7d94144c7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65893080"
---
# <a name="secure-windows-devices"></a>Sécuriser les appareils Windows

L’objectif ici est de configurer les paramètres qui font partie de la stratégie d’appareil par défaut pour Windows 10 ou 11. Tous les utilisateurs qui connectent un appareil Windows, y compris les appareils mobiles et les PC, en se connectant avec leur compte professionnel reçoivent automatiquement ces paramètres. Nous vous recommandons d’accepter la stratégie par défaut durant l’installation et d’ajouter ultérieurement des stratégies qui ciblent des groupes d’utilisateurs spécifiques.

## <a name="before-you-begin"></a>Avant de commencer

Avant de pouvoir configurer des appareils Windows pour les utilisateurs Microsoft 365 Business Premium, assurez-vous que tous les appareils Windows exécutent Windows 10 Professionnel, version 1703 (Creators Update) ou Windows 11 Professionnel.

Windows 10 Professionnel (ou Windows 11 Professionnel) est un prérequis pour le déploiement de Windows 10 Business, qui est un ensemble de services cloud et de fonctionnalités de gestion des appareils qui complètent Windows 10 Professionnel et Windows 11 Professionnel, et activent la gestion centralisée et les contrôles de sécurité de Microsoft 365 Business Premium.

[En savoir plus sur la configuration requise pour Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Professionnel et Windows 11 Professionnel

Si vous avez des appareils Windows exécutant des versions antérieures de Windows, telles que Windows 7 Professionnel, Windows 8 Pro ou Windows 8.1 Pro, votre abonnement Microsoft 365 Business Premium vous permet de mettre à niveau ces appareils vers Windows 10 Professionnel ou Windows 11 Professionnel.
  
Pour plus d’informations sur la mise à niveau des appareils Windows, consultez les articles suivants :

- [Mettre à niveau Windows Home vers Windows 10 ou Windows 11 Professionnel](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [Mettre à niveau vers Windows 10 Professionnel](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)

<!---
Could not find the Win11 equivalent upgrade link.
---> 
  
## <a name="secure-your-windows-10-and-11-devices"></a>Sécuriser vos appareils Windows 10 et Windows 11

Par défaut, tous les paramètres sont **activés**. Les paramètres suivants sont disponibles :<br/><br/>

|Paramètre  <br/> |Description  <br/> |
|:-----|:-----|
|Protéger les ordinateurs des virus et d'autres menaces à l'aide de l'antivirus Microsoft Defender  <br/> |Exige que l’antivirus Microsoft Defender soit activé pour protéger les PC contre les risques liés à la connexion à Internet.  <br/> |
|Protéger les ordinateurs contre les menaces web dans Microsoft Edge  <br/> |Active les paramètres Microsoft Edge qui protègent les utilisateurs contre les sites et téléchargements malveillants.  <br/> |
|Protéger les fichiers et dossiers sur PC contre un accès non autorisé avec BitLocker  <br/> |BitLocker protège les données en chiffrant les disques durs de l’ordinateur et en les protégeant contre l’exposition des données en cas de perte ou de vol d’un ordinateur. Pour plus d’informations, consultez [FAQ BitLocker](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).<br/> |
|Désactiver l'écran d'un appareil resté inactif pendant  <br/> |Permet d'assurer la protection des données d'entreprise lorsqu'un utilisateur est inactif. Il est possible qu'un utilisateur travaille dans un lieu public, par exemple un café, et s'éloigne ou soit distrait pendant un instant, laissant son appareil à la vue de tous. Ce paramètre vous permet de contrôler la durée pendant laquelle l'utilisateur peut être inactif avant l'extinction de l'écran.  <br/> |

## <a name="next-objective"></a>Objectif suivant

[Gérer les appareils Windows](m365bp-manage-windows-devices.md)
