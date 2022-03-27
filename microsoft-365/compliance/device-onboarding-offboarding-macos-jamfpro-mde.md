---
title: Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide de JAMF Pro pour les clients de Microsoft Defender pour point de terminaison (aperçu)
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Découvrez comment intégrer et désinsser des appareils macOS dans des solutions de conformité Microsoft 365 à l’aide de JAMF Pro pour les clients Microsoft Defender pour les points de terminaison (prévisualisation)
ms.openlocfilehash: f260d901f8f02c2c02007b2cc0d49ab9ee57dafd
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716318"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers-preview"></a>Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide de JAMF Pro pour les clients de Microsoft Defender pour point de terminaison (aperçu)

Vous pouvez utiliser jamf Pro pour intégrer des appareils macOS dans Microsoft 365 solutions de conformité.

> [!IMPORTANT]
> Utilisez cette procédure ***si vous avez*** déployé Microsoft Defender pour le point de terminaison (MDE) sur vos appareils macOS

**S’applique à :**

- Clients qui ont déployé MDE sur leurs appareils macOS.
- [Protection contre la perte de données de point de terminaison (DLP) pour Microsoft 365](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)


## <a name="before-you-begin"></a>Avant de commencer

- Assurez-vous que vos appareils macOS sont gérés via [JAMF pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) et sont associés à une identité (Azure AD UPN jointe) via JAMF Connecter ou Intune.
- Installer le navigateur Edge v95+ sur vos appareils macOS

## <a name="onboard-devices-into-microsoft-365-compliance-solutions-using-jamf-pro"></a>Intégrer des appareils dans des solutions Microsoft 365 conformité à l’aide de JAMF Pro

L’intégration d’un appareil macOS dans des solutions de conformité est un processus en plusieurs phases.

### <a name="download-the-configuration-files"></a>Télécharger les fichiers de configuration

1. Vous aurez besoin de ces fichiers pour cette procédure.

|fichier nécessaire pour |source |
|---------|---------|
|accessibilité |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
accès disque complet     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Préférence MDE |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/schema/schema.json)

> [!TIP]
> Vous pouvez télécharger les fichiers *.mobileconfig* individuellement ou dans un [seul fichier combiné qui](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) contient :
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
>
>Si l’un de ces fichiers individuels est mis à jour, vous devez télécharger à nouveau le fichier combiné ou le fichier unique mis à jour individuellement.

### <a name="update-the-existing-mde-preference-domain-profile-using-the-jamf-pro-console"></a>Mettre à jour le profil de domaine de préférence MDE existant à l’aide de la console JAMF PRO

1. Mettez à jour schema.xml profil avec le **fichier schema.json** que vous avez téléchargé.

1. Sous **MDE Preference Domain Properties** choose these settings
    - Fonctionnalités 
        - Utiliser les extensions système : `enabled` - requis pour les extensions réseau sur Contrôle
        - Utilisez la protection contre la perte de données : `enabled`

1. Sélectionnez **l’onglet** Étendue.

1. Choisissez les groupes vers qui déployer ce profil de configuration.

1. Cliquez sur **Enregistrer**. 

### <a name="update-the-configuration-profile-for-grant-full-disk-access"></a>Mettre à jour le profil de configuration pour accorder un accès disque total

1. Mettez à jour le profil d’accès disque complet existant avec le **fichier fulldisk.mobileconfig** .

1. Télécharger **le fichier fulldisk.mobileconfig** sur JAMF. Reportez-vous [au déploiement de profils de configuration personnalisés à l’aide de jamf Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="grant-accessibility-access-to-dlp"></a>Accorder l’accès à l’accessibilité à la DLP

1. Utilisez le fichier accessibility.mobileconfig que vous avez téléchargé précédemment.

1. Télécharger jamf comme décrit dans [Deploying Custom Configuration Profiles using Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="check-the-macos-device"></a>Vérifier l’appareil macOS 

1. Redémarrez l’appareil macOS.

1. **Ouvrez System PreferencesProfiles** > .

1. Vous devriez voir :
    - Accessiblity
    - Accès disque total
    - Profil d’extension du noyau
    - MAU
    - Intégration MDATP
    - Préférences MDE
    - Profil de gestion
    - Filtre réseau
    - Notifications
    - Profil d’extension système

## <a name="offboard-macos-devices-using-jamf-pro"></a>Désinséboarder des appareils macOS à l’aide de jamf Pro

> [!IMPORTANT]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois.

Pour utiliser un appareil macOS, suivez les étapes ci-après.

 1. Sous **MDE Preference Domain Properties** , supprimez les valeurs de ces paramètres
    - Fonctionnalités 
        - Utiliser les extensions système
        - Utiliser la protection contre la perte de données

1. Cliquez sur **Enregistrer**.
