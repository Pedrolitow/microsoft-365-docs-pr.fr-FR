---
title: Choisir entre la mobilité de base et la sécurité et Intune
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: La sécurité et la mobilité de base font partie des plans Microsoft 365.
ms.openlocfilehash: 75fef5bd70d7b8926d31b80f16952aa996bc625c
ms.sourcegitcommit: e53234b1f64ebca00e121da1706c02b3337c35f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "49580660"
---
# <a name="choose-between-basic-mobility-and-security-or-intune"></a>Choisir entre une mobilité de base et une sécurité ou Intune

[Microsoft Intune](https://docs.microsoft.com/mem/intune/) est un produit autonome inclus dans certains plans Microsoft 365, tandis que la sécurité et la mobilité de base font partie des plans Microsoft 365. 

 ## <a name="availability-of-basic-mobility-and-security-and-intune"></a>Disponibilité de la sécurité et de la sécurité de base et Intune
 
La mobilité et la sécurité de base et Intune sont inclus dans un grand nombre de plans, comme décrit dans le tableau suivant.

| Planification | Mobilité et sécurité de base | Microsoft Intune |
|:-----|:-----|:-----|
|Microsoft 365 Apps|Oui|Non|
|Microsoft 365 Business Basic|Oui|Non|
|Microsoft 365 Business Standard|Oui|Non|
|Office 365 E1 |Oui|Non|
|Office 365 E3 |Oui|Non|
|Office 365 E5 |Oui|Non|
|Microsoft 365 Business Premium |Oui|Oui|
|Microsoft 365 terrain 3 |Oui|Oui|
|Microsoft 365 Entreprise E3 |Oui|Oui|
|Microsoft 365 Entreprise E5 |Oui|Oui|
|Microsoft 365 éducation a1 |Oui|Oui|
|Microsoft 365 Éducation A3 |Oui|Oui|
|Microsoft 365 Éducation A5 |Oui|Oui|
|Microsoft Intune |Non|Oui|
|Sécurité & Enterprise Mobility E3 |Non|Oui|
|Enterprise Mobility & sécurité E5 |Non|Oui|

>[!NOTE]
>Vous ne pouvez pas utiliser la mobilité et la sécurité de base si vous utilisez déjà Microsoft Intune.

 Pour plus d’informations, consultez les [descriptions de service de plateforme Microsoft 365 et Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description). 

## <a name="differences-in-capabilities"></a>Différences de fonctionnalités

Microsoft Intune et la mobilité et la sécurité intégrées de base vous permettent de gérer les appareils mobiles de votre organisation, mais il existe des différences clés en matière de capacité, décrites dans le tableau suivant.

>[!NOTE]
>Vous pouvez gérer les utilisateurs et leurs appareils mobiles à l’aide de Intune et de la mobilité et de la sécurité de base dans la même organisation standard entreprise Microsoft 365 *en configurant d’abord les paramètres de sécurité et de mobilité de base, puis en ajoutant Microsoft Intune*. Cela vous permet de choisir mobilité et sécurité de base ou la solution Intune plus riche en fonctionnalités. Attribuez une licence Intune pour activer les fonctionnalités Intune.

| Fonctionnalité | Principales fonctionnalités | Mobilité et sécurité de base | Microsoft Intune |
|:-----|:-----|:-----|:-----|
|Types d’appareil|La gestion de différentes plateformes de système d’exploitation et de variantes de mode de gestion. |Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>|Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>Mac OS, iPad OS|
|Conformité des appareils|Définir et gérer les stratégies de sécurité, telles que le verrouillage du code confidentiel au niveau du périphérique et la détection jailbreak. |Limitations sur les appareils Android 9 et versions ultérieures. Voir les [Détails](capabilities.md). |Oui|
|Accès conditionnel basé sur la conformité des appareils |Empêcher les appareils non conformes d’accéder à la messagerie d’entreprise et aux données à partir du Cloud. |Non pris en charge sur Windows 10.<br/>Limité au contrôle de l’accès à Exchange Online, SharePoint Online et Outlook. |Oui |
|Configuration des appareils  |Configurer les paramètres de l’appareil (par exemple, la désactivation de l’appareil photo)|Ensemble limité de paramètres.|Oui|Conformité des appareils|Définir et gérer les stratégies de sécurité, telles que le verrouillage du code confidentiel au niveau du périphérique et la détection jailbreak. |Limitations sur les appareils Android 9 et versions ultérieures. Voir les [Détails](capabilities.md). |Oui|
|Profils de messagerie  |Mettez en service un profil de messagerie natif sur l’appareil. |Oui|Oui|
|Profils WiFi |Approvisionnez un profil Wi-Fi natif sur l’appareil. |Non|Oui|
|Profils VPN |Approvisionnez un profil VPN natif sur l’appareil. |Non|Oui|
|Gestion des applications MDM |Déployez vos applications métiers internes et à partir des magasins d’applications pour les utilisateurs. |Non|Oui|
|MAM |Assurez-vous que vos utilisateurs peuvent accéder en toute sécurité aux informations d’entreprise à l’aide des applications Office Mobile et métiers, en aidant à limiter les actions telles que copier, couper, coller et enregistrer sous uniquement les applications approuvées pour les données d’entreprise. |Non|Oui|
|Navigateur géré  |Activer la navigation Web plus sécurisée à l’aide de l’application Edge. |Non|Oui|
|AutoPilot des programmes d’inscriptions sans intervention |Inscrire un grand nombre d’appareils appartenant à une entreprise, tout en simplifiant la configuration de l’utilisateur. |Non|Oui|
|||

Outre les fonctionnalités indiquées dans le tableau précédent, la mobilité de base et la sécurité et Intune incluent un ensemble d’actions distantes qui envoient des commandes à des appareils sur Internet. Par exemple, vous pouvez supprimer des données Office à partir de l’appareil d’un employé tout en laissant les données personnelles en place (retirer), supprimer les applications Office de l’appareil d’un employé (effacement) ou réinitialiser un appareil à ses paramètres d’usine (effacement complet). 

Les actions à distance de base et de sécurité incluent la suppression, la réinitialisation et l’effacement complet. Pour plus d’informations sur les actions de sécurité et de mobilité de base, reportez-vous à la rubrique [fonctionnalités de base Mobility and Security](capabilities.md).

Avec Intune, vous disposez de l’ensemble d’actions suivant :

-   AutoPilot Reset (Windows uniquement
-  Rotation de clés [BitLocker](https://docs.microsoft.com/mem/intune/protect/encrypt-devices#rotate-bitlocker-recovery-keys)   (Windows uniquement)
-  [Utilisation de la réinitialisation, de la suppression ou de l’inscription manuelle de l’appareil](https://docs.microsoft.com/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
-  [Désactiver le Loc](https://docs.microsoft.com/mem/intune/remote-actions/device-activation-lock-disable)   d’activation (iOS uniquement)
-  [Nouveau début](https://docs.microsoft.com/mem/intune/remote-actions/device-fresh-start)   (Windows uniquement)
- [Analyse complète](https://docs.microsoft.com/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)   (Windows 10 uniquement)
- [Localiser l’appareil](https://docs.microsoft.com/mem/intune/remote-actions/device-locate)   (iOS uniquement)
- [Mode perdu](https://docs.microsoft.com/mem/intune/remote-actions/device-lost-mode)   (iOS uniquement)- [analyse rapide](https://docs.microsoft.com/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)(Windows 10 uniquement)
- [Contrôle à distance pour Android](https://docs.microsoft.com/mem/intune/remote-actions/teamviewer-support)
- [Verrouiller à distance](https://docs.microsoft.com/mem/intune/remote-actions/device-remote-lock)
- [Renommer l’appareil](https://docs.microsoft.com/mem/intune/remote-actions/device-rename)
-  Réinitialiser le [redémarrage](https://docs.microsoft.com/mem/intune/remote-actions/device-restart)du [code secret](https://docs.microsoft.com/mem/intune/remote-actions/device-passcode-reset)   (Windows uniquement)
-  Mettre à jour l’aide à la sécurité Windows Defender (Windows uniquement)
-  Réinitialisation du code confidentiel Windows 10 (Windows uniquement)
-  [Envoyer des notifications](https://docs.microsoft.com/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device)   personnalisées (Android, iOS, iPad OS)
-  [Synchroniser l’appareil](https://docs.microsoft.com/mem/intune/remote-actions/device-sync)

Pour plus d’informations sur les actions Intune, consultez [la documentation Microsoft Intune](https://docs.microsoft.com/mem/intune/).
