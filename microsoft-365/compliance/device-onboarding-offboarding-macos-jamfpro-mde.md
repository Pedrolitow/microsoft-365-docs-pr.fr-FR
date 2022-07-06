---
title: Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide de JAMF Pro pour les clients de Microsoft Defender pour point de terminaison
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
description: Découvrez comment intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de JAMF Pro pour les clients Microsoft Defender pour point de terminaison
ms.openlocfilehash: 97ab1dbccc28cd1f9d14635c2fa351d0295202c1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622918"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers"></a>Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide de JAMF Pro pour les clients de Microsoft Defender pour point de terminaison

Vous pouvez utiliser JAMF Pro pour intégrer des appareils macOS dans des solutions Microsoft Purview.

> [!IMPORTANT]
> Utilisez cette procédure ***si vous avez*** déployé Microsoft Defender pour point de terminaison (MDE) sur vos appareils macOS

**S’applique à :**

- Les clients qui ont déployé MDE sur leurs appareils macOS.
- [Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md)


## <a name="before-you-begin"></a>Avant de commencer

- Assurez-vous que vos [appareils macOS sont gérés via JAMF pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) et associés à une identité (UPN joint à Azure AD) via JAMF Connect ou Intune.
- Installer le navigateur v95+ Edge sur vos appareils macOS

## <a name="onboard-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>Intégrer des appareils dans des solutions Microsoft Purview à l’aide de JAMF Pro

L’intégration d’un appareil macOS dans les solutions de conformité est un processus en plusieurs phases.

### <a name="download-the-configuration-files"></a>Télécharger les fichiers de configuration

1. Vous aurez besoin de ces fichiers pour cette procédure.

|fichier nécessaire pour |source |
|---------|---------|
|Accessibilité |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
accès au disque complet     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Préférence MDE |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/schema/schema.json)

> [!TIP]
> Vous pouvez télécharger les fichiers *.mobileconfig* individuellement ou dans un [seul fichier combiné](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) contenant :
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
>
>Si l’un de ces fichiers individuels est mis à jour, vous devez télécharger à nouveau le fichier combiné ou le fichier unique mis à jour individuellement.

### <a name="update-the-existing-mde-preference-domain-profile-using-the-jamf-pro-console"></a>Mettre à jour le profil de domaine préférence MDE existant à l’aide de la console JAMF PRO

1. Mettez à jour le profil schema.xml avec le fichier **schema.json** que vous venez de télécharger.

1. Sous **Propriétés de domaine de préférence MDE** , choisissez ces paramètres
    - Fonctionnalités 
        - Utiliser les extensions système : `enabled` requis pour les extensions réseau sur Catalina
        - Utilisez la protection contre la perte de données : `enabled`

1. Choisissez l’onglet **Étendue** .

1. Choisissez les groupes sur lesquels déployer ce profil de configuration.

1. Cliquez sur **Enregistrer**. 

### <a name="update-the-configuration-profile-for-grant-full-disk-access"></a>Mettre à jour le profil de configuration pour accorder l’accès complet au disque

1. Mettez à jour le profil d’accès au disque complet existant avec le fichier **fulldisk.mobileconfig** .

1. Chargez le fichier **fulldisk.mobileconfig** dans JAMF. Reportez-vous au [déploiement de profils de configuration personnalisés à l’aide de JAMF Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="grant-accessibility-access-to-dlp"></a>Accorder l’accès d’accessibilité à DLP

1. Utilisez le fichier accessibility.mobileconfig que vous avez téléchargé précédemment.

1. Chargez sur JAMF comme décrit dans [le déploiement de profils de configuration personnalisés à l’aide de Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="check-the-macos-device"></a>Vérifier l’appareil macOS 

1. Redémarrez l’appareil macOS.

1. Ouvrez **les profils de préférences** >  système.

1. Vous devriez voir :
    - Accessiblity
    - Accès au disque complet
    - Profil d’extension de noyau
    - MAU
    - Intégration MDATP
    - Préférences MDE
    - Profil de gestion
    - Filtre réseau
    - Notifications
    - Profil d’extension système

## <a name="offboard-macos-devices-using-jamf-pro"></a>Désins border des appareils macOS à l’aide de JAMF Pro

> [!IMPORTANT]
> La désintégération entraîne l’arrêt de l’envoi de données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois maximum.

Pour déconnecter un appareil macOS, procédez comme suit

 1. Sous **Propriétés de domaine de préférence MDE** , supprimez les valeurs de ces paramètres
    - Fonctionnalités 
        - Utiliser des extensions système
        - Utiliser la protection contre la perte de données

1. Cliquez sur **Enregistrer**.
