---
title: Intégration et désintération des appareils macOS dans des solutions de conformité à l’aide de JAMF Pro pour les clients Microsoft Defender pour endpoint (prévisualisation)
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Découvrez comment intégrer et désinsser des appareils macOS dans des solutions de conformité Microsoft 365 à l’aide de JAMF Pro pour les clients Microsoft Defender pour les points de terminaison (prévisualisation)
ms.openlocfilehash: dd5bedb473de6fa608d1e28ad7a81c3a6d7d5b30
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60648197"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers-preview"></a>Intégration et désintération des appareils macOS dans des solutions de conformité à l’aide de JAMF Pro pour les clients Microsoft Defender pour endpoint (prévisualisation)

Vous pouvez utiliser jamf Pro pour intégrer des appareils macOS dans Microsoft 365 solutions de conformité.

> [!IMPORTANT]
> Utilisez cette procédure ***si vous avez*** déployé Microsoft Defender pour le point de terminaison (MDE) sur vos appareils macOS

## <a name="get-registered"></a>S’inscrire

Pour accéder à cette fonctionnalité, vous devez inscrire votre client auprès de Microsoft. Voir, [inscrivez-vous à la Microsoft 365 prise en charge macOS.](https://aka.ms/Ignite2021DLP)

**S’applique à :**

- Clients qui ont déployé MDE sur leurs appareils macOS.
- [Microsoft 365 Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)


## <a name="before-you-begin"></a>Avant de commencer

- Assurez-vous que vos [appareils macOS sont Azure AD joints](https://docs.jamf.com/10.30.0/jamf-pro/administrator-guide/Azure_AD_Integration.html)
- Assurez-vous que vos [appareils macOS sont gérés via JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) 
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
> Vous pouvez télécharger les fichiers *.mobileconfig* individuellement ou dans un seul fichier [combiné qui](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) contient :
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

1. Mettez à jour le profil d’accès disque intégral existant avec le **fichier fulldisk.mobileconfig.**

1. Télécharger le **fichier fulldisk.mobileconfig** sur JAMF. Reportez-vous [au déploiement de profils de configuration personnalisés à l’aide](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html)de JAMF Pro .

### <a name="grant-accessibility-access-to-dlp"></a>Accorder l’accès à l’accessibilité à la DLP

1. Utilisez le fichier accessibility.mobileconfig que vous avez téléchargé précédemment.

1. Télécharger à JAMF comme décrit dans le déploiement de profils de configuration personnalisés à l’aide de [Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="check-the-macos-device"></a>Vérifier l’appareil macOS 

1. Redémarrez l’appareil macOS.

1. Ouvrez **les profils de préférences**  >  **système.**

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

Pour hors-boarder un appareil macOS, suivez les étapes ci-après.

 1. Sous **MDE Preference Domain Properties,** supprimez les valeurs de ces paramètres
    - Fonctionnalités 
        - Utiliser les extensions système
        - Utiliser la protection contre la perte de données

1. Cliquez sur **Enregistrer**.
