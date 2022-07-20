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
ms.date: 07/19/2022
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment configurer les paramètres de la stratégie d’appareil par défaut que tout appareil Windows recevra lors de la connexion à son compte professionnel ou scolaire.
ms.openlocfilehash: f497dab832b9980225be2e689d2c980860a01454
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2022
ms.locfileid: "66894874"
---
# <a name="secure-windows-devices"></a>Sécuriser les appareils Windows

L’objectif ici est de configurer les paramètres qui font partie de la stratégie d’appareil par défaut pour Windows 10 ou 11. Tous les utilisateurs qui connectent un appareil Windows, y compris les appareils mobiles et les PC, en se connectant avec leur compte professionnel reçoivent automatiquement ces paramètres. Nous vous recommandons d’accepter la stratégie par défaut durant l’installation et d’ajouter ultérieurement des stratégies qui ciblent des groupes d’utilisateurs spécifiques.

## <a name="before-you-begin"></a>Avant de commencer

Avant de pouvoir configurer des appareils Windows pour les utilisateurs de Microsoft 365 Premium, vérifiez que tous les appareils Windows exécutent la version Windows 10 Professionnel.

Windows 10 Professionnel est un prérequis pour le déploiement de Windows 10 Business, qui est un ensemble de services cloud et de fonctionnalités de gestion des appareils qui complètent Windows 10 Professionnel et Windows 11 Professionnel, et activent la gestion centralisée et les contrôles de sécurité de Microsoft 365 Business Premium.

[En savoir plus sur la configuration requise pour Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro"></a>Windows 10 Professionnel

Si vous avez des appareils Windows exécutant des versions antérieures de Windows, telles que Windows 7 Professionnel, Windows 8 Pro ou Windows 8.1 Pro, votre abonnement Microsoft 365 Business Premium vous permet de mettre à niveau ces appareils vers Windows 10 Professionnel ou Windows 11 Professionnel.
  
Pour plus d’informations sur la mise à niveau des appareils Windows, consultez [Mettre à jour les appareils Windows vers Windows 10 Professionnel](m365bp-upgrade-windows-10-pro.md).

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
