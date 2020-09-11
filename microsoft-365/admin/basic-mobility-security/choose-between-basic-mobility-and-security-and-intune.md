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
ms.openlocfilehash: df52d500c945275b62170ab16260f0c019340f73
ms.sourcegitcommit: aeb94601a81db3ead8610c2f36cff30eb9fe10e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "47429925"
---
# <a name="choose-between-basic-mobility-and-security-and-intune"></a>Choisir entre la mobilité de base et la sécurité et Intune

Microsoft Intune est un produit autonome inclus dans certains plans Microsoft 365, tandis que la mobilité & la sécurité de base fait partie des plans Microsoft 365. Tous deux sont inclus dans une variété de plans, comme décrit dans le tableau suivant.

|**Plan**|**Mobilité et sécurité de base**|**Microsoft Intune**|
|:-----|:-----|:-----|
|Microsoft 365 Apps|Oui|Non|
|Microsoft 365 Business Basic|Oui|Non|
|Microsoft 365 Business Standard|Oui|Non|
|Office 365 E1 |Oui|Non|
|Office 365 E3 |Oui|Non|
|Office 365 E5 |Oui|Non|
|Microsoft 365 Business Premium |Oui|Oui|
|Microsoft 365 terrain 3 |Oui|Oui|
|Microsoft 365 Entreprise E3 |Oui|Oui|
|Microsoft 365 Entreprise E5 |Oui|Oui|
|Microsoft 365 Eductation a1 |Oui|Oui|
|Microsoft 365 Éducation A3 |Oui|Oui|
|Microsoft 365 Éducation A5 |Oui|Oui|
|Microsoft Intune |Non|Oui|
|Sécurité & Enterprise Mobility E3 |Non|Oui|
|Enterprise Mobility & sécurité E5 |Non|Oui|

>[!NOTE]
>Vous ne pouvez pas utiliser la mobilité et la sécurité de base si vous utilisez déjà Microsoft Intune.

## <a name="differences-in-capabilities"></a>Différences de fonctionnalités

Microsoft Intune et la mobilité et la sécurité intégrées de base vous permettent de gérer les appareils mobiles de votre organisation, mais il existe des différences clés en matière de capacité, décrites dans le tableau suivant.

>[!NOTE]
>Vous pouvez gérer les utilisateurs et leurs appareils mobiles à l’aide de Intune et de la mobilité et de la sécurité de base dans la même organisation standard entreprise Microsoft 365 en configurant d’abord les paramètres de sécurité et de mobilité de base, puis en ajoutant Microsoft Intune. Cela vous permet de choisir si vous gérez les appareils d’un utilisateur avec une mobilité et une sécurité de base ou avec une solution Intune plus riche en fonctionnalités. Dans le mode, l’attribution de licence détermine le service avec lequel l’appareil est utilisé. Attribuez une licence Intune pour activer les fonctionnalités Intune uniquement.

|**Fonctionnalités**|**Principales fonctionnalités**|**Mobilité et sécurité de base**|**Microsoft Intune**|
|:-----|:-----|:-----|:-----|
|Types d’appareil|Différentes plateformes de système d’exploitation et variantes de mode de gestion majeures. |Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>|Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>Mac OS<br/>système d’exploitation iPad|
|Conformité des appareils|Définir et gérer les stratégies de sécurité, telles que le verrouillage du code confidentiel au niveau du périphérique et la détection jailbreak. |Limitations sur les appareils Android 9 et versions ultérieures. Pour plus d’informations, reportez-vous à la rubrique [fonctionnalités de base Mobility and Security](capabilities.md).|Oui|
|Accès conditionnel basé sur la conformité des appareils |Empêcher les appareils non conformes d’accéder à la messagerie d’entreprise et aux données à partir du Cloud. |-Non pris en charge sur Windows 10.<br/>Limité à la gestion de l’accès à Exchange Online, SharePoint Online et Outlook services. |Non|
|Configuration des appareils  |Configurez les paramètres des appareils (par exemple, la désactivation de l’appareil photo). |Ensemble limité de paramètres.Pour plus d’informations, reportez-vous à la rubrique [fonctionnalités de base Mobility and Security](capabilities.md). |Oui|
|Actions à distance.  |Envoyer des commandes aux appareils sur Internet. Par exemple, supprimez les données Office de l’appareil d’un employé tout en laissant les données personnelles en place (retrait). |Mettre hors service<br/>Réinitialisation<br/>Supprimer|-Réinitialisation automatique du pilote (Windows uniquement)<br/>- Rotation de clés [BitLocker](https://docs.microsoft.com/mem/intune/protect/encrypt-devices#rotate-bitlocker-recovery-keys)   (Windows uniquement)<br/>- [Supprimer](https://docs.microsoft.com/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)<br/>- [Désactiver le Loc](https://docs.microsoft.com/mem/intune/remote-actions/device-activation-lock-disable)   d’activation (iOS uniquement)<br/>- [Nouveau début](https://docs.microsoft.com/mem/intune/remote-actions/device-fresh-start)   (Windows uniquement)<br/>- [Analyse complète](https://docs.microsoft.com/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)   (Windows 10 uniquement)<br/>- [Localiser l’appareil](https://docs.microsoft.com/mem/intune/remote-actions/device-locate)   (iOS uniquement)<br/>- [Mode perdu](https://docs.microsoft.com/mem/intune/remote-actions/device-lost-mode)   (iOS uniquement)<br/>- [Analyse rapide](https://docs.microsoft.com/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)(Windows 10 uniquement)<br/>- [Contrôle à distance pour Android](https://docs.microsoft.com/mem/intune/remote-actions/teamviewer-support)<br/>- [Verrou à distance](https://docs.microsoft.com/mem/intune/remote-actions/device-remote-lock)<br/>- [Renommer l’appareil](https://docs.microsoft.com/mem/intune/remote-actions/device-rename)<br/>- [Réinitialiser le code secret](https://docs.microsoft.com/mem/intune/remote-actions/device-passcode-reset)<br/>- [Redémarrer](https://docs.microsoft.com/mem/intune/remote-actions/device-restart)   (Windows uniquement)<br/>- [Totalement](https://docs.microsoft.com/mem/intune/remote-actions/devices-wipe#retire)<br/>-Mettre à jour l’aide à la sécurité Windows Defender (Windows uniquement)<br/>-Réinitialisation du code confidentiel Windows 10 (Windows uniquement)<br/>- [Réinitialisation](https://docs.microsoft.com/mem/intune/remote-actions/devices-wipe#wipe)<br/>- [Envoyer des notifications](https://docs.microsoft.com/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device)   personnalisées (Android, iOS, iPad OS)<br/>- [Synchroniser l’appareil](https://docs.microsoft.com/mem/intune/remote-actions/device-sync)|
|Profils de messagerie  |Mettez en service un profil de messagerie natif sur l’appareil. |Oui|Oui|
|Profils WIFI |Approvisionnez un profil Wi-Fi natif sur l’appareil. |Non|Oui|
|Profils VPN |Approvisionnez un profil VPN natif sur l’appareil. |Non|Oui|
|Gestion des applications MDM  |Déployez vos applications métiers internes et à partir des magasins d’applications pour les utilisateurs. |Non|Oui|
|Protection des applications mobiles  |Permettez aux utilisateurs d’accéder en toute sécurité aux informations d’entreprise en utilisant les applications Office Mobile et métiers qu’ils connaissent, tout en garantissant la sécurité des données en aidant à limiter les actions telles que copier, couper, coller et enregistrer sous, uniquement aux applications gérées approuvées pour les données d’entreprise. Fonctionne même si les appareils ne sont pas s’inscrire à MDM. Voir protéger les données d’application à l’aide des stratégies MAM. |Non|Oui|
|Navigateur géré  |Activer la navigation Web plus sécurisée à l’aide de l’application Edge. |Non|Oui|
|Programmes d’inscriptions à Zero Touch |Inscrire un grand nombre d’appareils appartenant à une entreprise, tout en simplifiant la configuration de l’utilisateur. |Non|Oui|
