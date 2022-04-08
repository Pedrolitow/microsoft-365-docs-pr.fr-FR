---
title: Choisir entre mobilité et sécurité de base et Intune
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
description: La mobilité et la sécurité de base font partie des plans de Microsoft 365.
ms.openlocfilehash: 0c1c61181d7e8bd5eb0ee000e29285c32a454692
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64713842"
---
# <a name="choose-between-basic-mobility-and-security-or-intune"></a>Choisissez entre mobilité et sécurité de base ou Intune

[Microsoft Intune](/mem/intune/) est un produit autonome inclus dans certains plans Microsoft 365, tandis que Basic Mobility and Security fait partie des plans de Microsoft 365.

 ## <a name="availability-of-basic-mobility-and-security-and-intune"></a>Disponibilité de la mobilité et de la sécurité de base et Intune

La mobilité et la sécurité de base et les Intune sont inclus dans divers plans, décrits dans le tableau suivant.

| Planification | Mobility + Security de Base | Microsoft Intune |
|:-----|:-----|:-----|
|Microsoft 365 Apps|Oui|Non|
|Microsoft 365 Business Basic|Oui|Non|
|Microsoft 365 Business Standard|Oui|Non|
|Office 365 E1 |Oui|Non|
|Office 365 E3 |Oui|Non|
|Office 365 E5 |Oui|Non|
|Microsoft 365 Business Premium |Oui|Oui|
|Microsoft 365 première ligne 3 |Oui|Oui|
|Microsoft 365 Entreprise E3 |Oui|Oui|
|Microsoft 365 Entreprise E5 |Oui|Oui|
|Microsoft 365 Éducation A1 |Oui|Oui|
|Microsoft 365 Éducation A3 |Oui|Oui|
|Microsoft 365 Éducation A5 |Oui|Oui|
|Microsoft Intune |Non|Oui|
|Enterprise Mobility & Security E3 |Non|Oui|
|Enterprise Mobility & Security E5 |Non|Oui|

> [!NOTE]
> Vous ne pouvez pas commencer à utiliser la mobilité et la sécurité de base si vous utilisez déjà Microsoft Intune.

 Pour plus d’informations, consultez [Microsoft 365 et Office 365 descriptions du service de plateforme](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description).

## <a name="differences-in-capabilities"></a>Différences dans les fonctionnalités

Microsoft Intune et la mobilité et la sécurité de base intégrées vous offrent la possibilité de gérer les appareils mobiles de votre organisation, mais il existe des différences clés en matière de fonctionnalités, décrites dans le tableau suivant.

> [!NOTE]
> Vous pouvez gérer les utilisateurs et leurs appareils mobiles à l’aide de Intune et de mobilité et de sécurité de base dans la même organisation Microsoft 365 Business Standard en *configurant d’abord mobilité et sécurité de base, puis en ajoutant Microsoft Intune*. Cela vous permet de choisir la mobilité et la sécurité de base ou la solution Intune plus riche en fonctionnalités. Attribuez une licence Intune pour activer les fonctionnalités de Intune.

| Fonctionnalité | Points forts des fonctionnalités | Mobility + Security de Base | Microsoft Intune |
|:-----|:-----|:-----|:-----|
|Types d’appareil|Gestion des différentes plateformes de système d’exploitation et des variantes principales du mode de gestion. |Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>|Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>mac OS, système d’exploitation iPad|
|Conformité des appareils|Définissez et gérez des stratégies de sécurité, telles que le verrouillage du code confidentiel au niveau de l’appareil et la détection de jailbreak. |Limitations sur les appareils Android. Voir [les détails](capabilities.md). |Oui|
|Accès conditionnel en fonction de la conformité des appareils |Empêchez les appareils non conformes d’accéder à la messagerie et aux données d’entreprise à partir du cloud. |Non pris en charge sur Windows 10.<br/>Limité au contrôle de l’accès aux Exchange Online, SharePoint Online et Outlook. |Oui |
|Configuration des appareils  |Configurer les paramètres de l’appareil (par exemple, désactivation de l’appareil photo)|Ensemble limité de paramètres.|Oui|
|Profils de messagerie  |Provisionnez un profil de messagerie natif sur l’appareil. |Oui|Oui|
|Profils WiFi |Provisionnez un profil Wi-Fi natif sur l’appareil. |Non|Oui|
|Profils VPN |Provisionnez un profil VPN natif sur l’appareil. |Non|Oui|
|Gestion des applications mobiles  |Déployez vos applications métier internes et à partir de magasins d’applications pour les utilisateurs. |Non|Oui|
|Protection des applications mobiles  |Permettre à vos utilisateurs d’accéder en toute sécurité aux informations d’entreprise à l’aide des Office applications mobiles et métier qu’ils connaissent, tout en garantissant la sécurité des données en limitant les actions telles que copier, couper, coller et enregistrer sous, uniquement les applications gérées approuvées pour les données d’entreprise. Fonctionne même si les appareils ne sont pas inscrits à Basic Mobility and Security. Consultez Protéger les données d’application à l’aide de stratégies GAM. |Non|Oui|
|Managed Browser  |Activez la navigation web plus sécurisée à l’aide de l’application Edge. |Non|Oui|
|Programmes d’inscription Zero Touch (AutoPilot) |Inscrivez un grand nombre d’appareils appartenant à l’entreprise, tout en simplifiant la configuration des utilisateurs. |Non|Oui|

Outre les fonctionnalités répertoriées dans le tableau précédent, mobilité et sécurité de base et Intune incluent un ensemble d’actions à distance qui envoient des commandes aux appareils via Internet. Par exemple, vous pouvez supprimer Office données de l’appareil d’un employé tout en laissant les données personnelles en place (mise hors service), supprimer Office applications de l’appareil d’un employé (réinitialisation) ou réinitialiser un appareil à ses paramètres d’usine (réinitialisation complète).

Les actions à distance de mobilité et de sécurité de base incluent la mise hors service, la réinitialisation et la réinitialisation complète. Pour plus d’informations sur les actions de mobilité et de sécurité de base, consultez [les fonctionnalités de mobilité et de sécurité de base](capabilities.md).

Avec Intune vous avez l’ensemble d’actions suivant :

- [Réinitialisation d’AutoPilot](/mem/autopilot/windows-autopilot-reset) (Windows uniquement)
- Récupération   [de clé Bitlocker](https://support.microsoft.com/windows/finding-your-bitlocker-recovery-key-in-windows-6b71ad27-0b89-ea08-f143-056f5ab347d6) (Windows uniquement)
- [Utiliser la réinitialisation, la mise hors service ou la désinscription manuelle de l’appareil](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
- [Désactiver le verrou](/mem/intune/remote-actions/device-activation-lock-disable)  d’activation (iOS uniquement)
- [Nouveau départ](/mem/intune/remote-actions/device-fresh-start)  (Windows uniquement)
- [Analyse](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)  complète (Windows 10 uniquement)
- [Localiser l’appareil](/mem/intune/remote-actions/device-locate)  (iOS uniquement)
- [Mode](/mem/intune/remote-actions/device-lost-mode)  perdu (iOS uniquement)- [Analyse rapide](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) (Windows 10 uniquement)
- [Contrôle à distance pour Android](/mem/intune/remote-actions/teamviewer-support)
- [Verrouiller à distance](/mem/intune/remote-actions/device-remote-lock)
- [Renommer un appareil](/mem/intune/remote-actions/device-rename)
- [Réinitialiser le](/mem/intune/remote-actions/device-passcode-reset) [redémarrage](/mem/intune/remote-actions/device-restart)  du code secret (Windows uniquement)
- [Mettre à jour Windows Defender Security Intelligence](https://www.microsoft.com/en-us/wdsi/defenderupdates) (Windows uniquement)
- [Windows 10 réinitialisation du code confidentiel](/windows/security/identity-protection/hello-for-business/hello-feature-pin-reset) (Windows uniquement)
- [Envoyer des notifications personnalisées](/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device)  (Android, iOS, système d’exploitation iPad)
- [Synchroniser l’appareil](/mem/intune/remote-actions/device-sync)

Pour plus d’informations sur les actions Intune, consultez [Microsoft Intune documentation](/mem/intune/).
