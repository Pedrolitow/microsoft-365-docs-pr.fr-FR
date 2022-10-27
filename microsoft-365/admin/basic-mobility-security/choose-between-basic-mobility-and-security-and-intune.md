---
title: Choisissez entre Mobilité et sécurité de base et Intune
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier3
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Mobilité et sécurité de base fait partie des plans Microsoft 365, tandis que Microsoft Intune est un produit autonome inclus dans certains plans Microsoft 365.
ms.openlocfilehash: 191fdefdb4ae1af9ca4873c404a78ca6635b9958
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68721183"
---
# <a name="choose-between-basic-mobility-and-security-or-intune"></a>Choisissez entre mobilité de base et sécurité ou Intune

[Microsoft Intune](/mem/intune/) est un produit autonome inclus avec certains plans Microsoft 365, tandis que Mobilité et sécurité de base fait partie des plans Microsoft 365.

 ## <a name="availability-of-basic-mobility-and-security-and-intune"></a>Disponibilité de la mobilité et de la sécurité de base et Intune

Mobilité de base et sécurité et Intune sont inclus dans différents plans, décrits dans le tableau suivant.

| Planification | Mobility + Security de Base | Microsoft Intune |
|:-----|:-----|:-----|
|Microsoft 365 Apps|Oui|Non|
|Microsoft 365 Business Basic|Oui|Non|
|Microsoft 365 Business Standard|Oui|Non|
|Office 365 E1 |Oui|Non|
|Office 365 E3 |Oui|Non|
|Office 365 E5 |Oui|Non|
|Microsoft 365 Business Premium |Oui|Oui|
|Microsoft 365 Firstline 3 |Oui|Oui|
|Microsoft 365 Entreprise E3 |Oui|Oui|
|Microsoft 365 Entreprise E5 |Oui|Oui|
|Microsoft 365 Éducation A1 |Oui|Oui|
|Microsoft 365 Éducation A3 |Oui|Oui|
|Microsoft 365 Éducation A5 |Oui|Oui|
|Microsoft Intune |Non|Oui|
|Enterprise Mobility & Security E3 |Non|Oui|
|Enterprise Mobility & Security E5 |Non|Oui|

> [!NOTE]
> Vous ne pouvez pas commencer à utiliser mobilité et sécurité de base si vous utilisez déjà Microsoft Intune.

 Pour plus d’informations, consultez [Descriptions des services de plateforme Microsoft 365 et Office 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description).

## <a name="differences-in-capabilities"></a>Différences dans les fonctionnalités

Microsoft Intune et la sécurité de base intégrées vous donnent tous deux la possibilité de gérer les appareils mobiles de votre organisation, mais il existe des différences clés en matière de fonctionnalités, décrites dans le tableau suivant.

> [!NOTE]
> Vous pouvez gérer les utilisateurs et leurs appareils mobiles à l’aide de Intune et mobilité et sécurité de base dans la même organisation Microsoft 365 Business Standard en *configurant d’abord Mobilité et sécurité de base, puis en ajoutant Microsoft Intune*. Cela vous permet de choisir mobilité et sécurité de base ou la solution de Intune plus riche en fonctionnalités. Attribuez une licence Intune pour activer les fonctionnalités Intune.

| Fonctionnalité | Mises en évidence des fonctionnalités | Mobility + Security de Base | Microsoft Intune |
|:-----|:-----|:-----|:-----|
|Types d’appareil|Gestion de différentes plateformes de système d’exploitation et des principales variantes du mode de gestion. |Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>|Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>mac OS, iPad OS|
|Conformité des appareils|Définissez et gérez des stratégies de sécurité, telles que le verrouillage du code confidentiel et la détection de jailbreak au niveau de l’appareil. |Limitations sur les appareils Android. Consultez [les détails](capabilities.md). |Oui|
|Accès conditionnel en fonction de la conformité des appareils |Empêcher les appareils non conformes d’accéder à la messagerie et aux données d’entreprise à partir du cloud. |Non pris en charge sur Windows 10.<br/>Limité au contrôle de l’accès à Exchange Online, SharePoint Online et Outlook. |Oui |
|Configuration des appareils  |Configurer les paramètres de l’appareil (par exemple, désactiver la caméra)|Ensemble limité de paramètres.|Oui|
|Profils de messagerie  |Provisionnez un profil de messagerie natif sur l’appareil. |Oui|Oui|
|Profils Wi-Fi |Provisionnez un profil Wi-Fi natif sur l’appareil. |Non|Oui|
|Profils VPN |Provisionnez un profil VPN natif sur l’appareil. |Non|Oui|
|Gestion des applications mobiles  |Déployez vos applications métier internes et des magasins d’applications vers les utilisateurs. |Non|Oui|
|Protection des applications mobiles  |Permettre à vos utilisateurs d’accéder en toute sécurité aux informations d’entreprise à l’aide des applications mobiles et métier Office qu’ils connaissent, tout en garantissant la sécurité des données en aidant à limiter les actions telles que copier, couper, coller et enregistrer sous, aux seules applications gérées approuvées pour les données d’entreprise. Fonctionne même si les appareils ne sont pas inscrits à Mobilité et sécurité de base. Consultez Protéger les données d’application à l’aide de stratégies GAM. |Non|Oui|
|Managed Browser  |Activez une navigation web plus sécurisée à l’aide de l’application Edge. |Non|Oui|
|Programmes d’inscription sans contact (AutoPilot) |Inscrire un grand nombre d’appareils appartenant à l’entreprise, tout en simplifiant la configuration utilisateur. |Non|Oui|

Outre les fonctionnalités répertoriées dans le tableau précédent, Mobilité et sécurité de base et Intune incluent un ensemble d’actions à distance qui envoient des commandes aux appareils via Internet. Par exemple, vous pouvez supprimer des données Office de l’appareil d’un employé tout en laissant les données personnelles en place (mettre hors service), supprimer des applications Office de l’appareil d’un employé (réinitialisation) ou réinitialiser un appareil à ses paramètres d’usine (réinitialisation complète).

Les actions à distance mobilité et sécurité de base incluent la mise hors service, la réinitialisation et la réinitialisation complète. Pour plus d’informations sur les actions de mobilité et de sécurité de base, consultez [Fonctionnalités de Mobilité et sécurité de base](capabilities.md).

Avec Intune vous disposez de l’ensemble d’actions suivant :

- [Réinitialisation d’AutoPilot](/mem/autopilot/windows-autopilot-reset) (Windows uniquement)
- [Récupération de clé BitLocker](https://support.microsoft.com/windows/finding-your-bitlocker-recovery-key-in-windows-6b71ad27-0b89-ea08-f143-056f5ab347d6) (Windows uniquement)
- [Utiliser la réinitialisation, la mise hors service ou la désinscription manuelle de l’appareil](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
- [Désactiver le verrou d’activation](/mem/intune/remote-actions/device-activation-lock-disable) (iOS uniquement)
- [Redémarrage à zéro](/mem/intune/remote-actions/device-fresh-start) (Windows uniquement)
- [Analyse complète](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) (Windows 10 uniquement)
- [Localiser l’appareil](/mem/intune/remote-actions/device-locate) (iOS uniquement)
- [Mode Perdu](/mem/intune/remote-actions/device-lost-mode) (iOS uniquement) - [Analyse rapide](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) (Windows 10 uniquement)
- [Contrôle à distance pour Android](/mem/intune/remote-actions/teamviewer-support)
- [Verrouiller à distance](/mem/intune/remote-actions/device-remote-lock)
- [Renommer un appareil](/mem/intune/remote-actions/device-rename)
- [Réinitialiser le code secret](/mem/intune/remote-actions/device-passcode-reset) [Redémarrer](/mem/intune/remote-actions/device-restart) (Windows uniquement)
- [Mettre à jour Windows Defender Security Intelligence](https://www.microsoft.com/en-us/wdsi/defenderupdates) (Windows uniquement)
- [Réinitialisation du code confidentiel Windows 10](/windows/security/identity-protection/hello-for-business/hello-feature-pin-reset) (Windows uniquement)
- [Envoyer des notifications personnalisées](/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device) (Android, iOS, système d’exploitation iPad)
- [Synchroniser l’appareil](/mem/intune/remote-actions/device-sync)

Pour plus d’informations sur les actions Intune, consultez [Microsoft Intune documentation](/mem/intune/).
