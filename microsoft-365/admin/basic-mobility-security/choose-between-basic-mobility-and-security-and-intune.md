---
title: Choisir entre Basic Mobility and Security et Intune
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: La mobilité et la sécurité de base font partie des plans Microsoft 365 de sécurité.
ms.openlocfilehash: 0a461bc7462300bb2b27b5d027c2b4d4582b7d14
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60166229"
---
# <a name="choose-between-basic-mobility-and-security-or-intune"></a>Choisir entre Basic Mobility and Security ou Intune

[Microsoft Intune](/mem/intune/) est un produit autonome inclus dans certains plans Microsoft 365, tandis que Basic Mobility and Security fait partie des plans Microsoft 365 de sécurité.

 ## <a name="availability-of-basic-mobility-and-security-and-intune"></a>Disponibilité de Basic Mobility and Security et Intune

Basic Mobility and Security et Intune sont inclus dans une variété de plans, décrits dans le tableau suivant.

| Planification | Mobility + Security de Base | Microsoft Intune |
|:-----|:-----|:-----|
|Microsoft 365 Apps|Oui|Non|
|Microsoft 365 Business Basic|Oui|Non|
|Microsoft 365 Business Standard|Oui|Non|
|Office 365 E1 |Oui|Non|
|Office 365 E3 |Oui|Non|
|Office 365 E5 |Oui|Non|
|Microsoft 365 Business Premium |Oui|Oui|
|Microsoft 365 Première ligne 3 |Oui|Oui|
|Microsoft 365 Entreprise E3 |Oui|Oui|
|Microsoft 365 Entreprise E5 |Oui|Oui|
|Microsoft 365 Éducation A1 |Oui|Oui|
|Microsoft 365 Éducation A3 |Oui|Oui|
|Microsoft 365 Éducation A5 |Oui|Oui|
|Microsoft Intune |Non|Oui|
|Enterprise Mobility & Security E3 |Non|Oui|
|Enterprise Mobility & Security E5 |Non|Oui|

> [!NOTE]
> Vous ne pouvez pas commencer à utiliser Basic Mobility and Security si vous utilisez déjà Microsoft Intune.

 Pour plus d’informations, [voir Microsoft 365 et Office 365 descriptions](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description)du service de plateforme.

## <a name="differences-in-capabilities"></a>Différences de fonctionnalités

Microsoft Intune la mobilité et la sécurité de base intégrées vous donnent la possibilité de gérer les appareils mobiles au sein de votre organisation, mais il existe des différences clés en matière de fonctionnalités, décrites dans le tableau suivant.

> [!NOTE]
> Vous pouvez gérer les utilisateurs et leurs appareils mobiles à l’aide d’Intune et de Basic Mobility and Security dans la même organisation Microsoft 365 Business Standard en mettant d’abord en place basic *Mobility and Security,* puis en ajoutant Microsoft Intune . Cela vous permet de choisir la mobilité et la sécurité de base ou la solution Intune plus riche en fonctionnalités. Attribuez une licence Intune pour activer les fonctionnalités Intune.

| Fonctionnalité | Points forts des fonctionnalités | Mobility + Security de Base | Microsoft Intune |
|:-----|:-----|:-----|:-----|
|Types d’appareil|Gestion des différentes plateformes de système d’exploitation et des principales variantes du mode de gestion. |Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>|Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>mac OS, iPad OS|
|Conformité des appareils|Définir et gérer des stratégies de sécurité, telles que la détection de verrouillage du code confidentiel et de jailbreak au niveau de l’appareil. |Limitations sur les appareils Android 9 et ultérieurs. Voir [les détails.](capabilities.md) |Oui|
|Accès conditionnel basé sur la conformité des appareils |Empêcher les appareils non conformes d’accéder à la messagerie électronique et aux données d’entreprise à partir du cloud. |Non pris en charge sur Windows 10.<br/>Limité au contrôle de l’accès Exchange Online, SharePoint Online et Outlook. |Oui |
|Configuration des appareils  |Configurer les paramètres de l’appareil (par exemple, désactivation de l’appareil photo)|Ensemble limité de paramètres.|Oui|
|Profils de messagerie  |Provisionne un profil de messagerie natif sur l’appareil. |Oui|Oui|
|Profils WiFi |Approvisionnement d’un profil WiFi natif sur l’appareil. |Non|Oui|
|Profils VPN |Approvisionnement d’un profil VPN natif sur l’appareil. |Non|Oui|
|Gestion des applications mobiles  |Déployez vos applications métier internes et des magasins d’applications aux utilisateurs. |Non|Oui|
|Protection des applications mobiles  |Autorisez vos utilisateurs à accéder en toute sécurité aux informations d’entreprise à l’aide des applications mobiles et métiers Office qu’ils connaissent, tout en garantissant la sécurité des données en aidant à limiter les actions telles que copier, couper, coller et enregistrer sous uniquement les applications gérées approuvées pour les données d’entreprise. Fonctionne même si les appareils ne sont pas inscrits à Basic Mobility and Security. Voir Protéger les données d’application à l’aide de stratégies DE GESTION. |Non|Oui|
|Navigateur géré  |Activez la navigation web plus sécurisée à l’aide de l’application Edge. |Non|Oui|
|Programmes d’inscription zero touch (AutoPilot) |Inscrire un grand nombre d’appareils d’entreprise, tout en simplifiant la configuration utilisateur. |Non|Oui|
|||

Outre les fonctionnalités répertoriées dans le tableau précédent, Basic Mobility and Security et Intune incluent un ensemble d’actions à distance qui envoient des commandes à des appareils sur Internet. Par exemple, vous pouvez supprimer des données Office de l’appareil d’un employé tout en laissant des données personnelles en place (mise en retrait), supprimer des applications Office de l’appareil d’un employé (réinitialisation) ou réinitialiser un appareil à ses paramètres d’usine (réinitialisation complète).

Les actions à distance de mobilité et de sécurité de base incluent l’abandon, l’effacement et la effacement complet. Pour plus d’informations sur les actions de mobilité et de sécurité de base, voir les fonctionnalités [de Basic Mobility and Security](capabilities.md).

Avec Intune, vous avez l’ensemble d’actions suivant :

-   Réinitialisation autopilot (Windows uniquement
-  [Rotation de touche Bitlocker](/mem/intune/protect/encrypt-devices#rotate-bitlocker-recovery-keys)   (Windows uniquement)
-  [Utiliser la suppression, la suppression ou la désinscrire manuellement de l’appareil](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
-  [Désactiver loc](/mem/intune/remote-actions/device-activation-lock-disable)   d’activation (iOS uniquement)
-  [Nouveau démarrage](/mem/intune/remote-actions/device-fresh-start)   (Windows uniquement)
- [Analyse complète](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)   (Windows 10 uniquement)
- [Localiser l’appareil](/mem/intune/remote-actions/device-locate)   (iOS uniquement)
- [Mode perdu](/mem/intune/remote-actions/device-lost-mode)   (iOS uniquement)- [Analyse rapide](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)(Windows 10 uniquement)
- [Télécommande pour Android](/mem/intune/remote-actions/teamviewer-support)
- [Verrouiller à distance](/mem/intune/remote-actions/device-remote-lock)
- [Renommer un appareil](/mem/intune/remote-actions/device-rename)
-  [Réinitialiser le redémarrage](/mem/intune/remote-actions/device-passcode-reset) [](/mem/intune/remote-actions/device-restart)du code   secret (Windows uniquement)
-  Mettre à jour Windows Defender Security Intelligence (Windows uniquement)
-  Windows 10 Réinitialisation du code confidentiel (Windows uniquement)
-  [Envoyer des notifications personnalisées](/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device)   (Android, iOS, iPad OS)
-  [Synchroniser l’appareil](/mem/intune/remote-actions/device-sync)

Pour plus d’informations sur les actions Intune, voir [Microsoft Intune documentation.](/mem/intune/)
