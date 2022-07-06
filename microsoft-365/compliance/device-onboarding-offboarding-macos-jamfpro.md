---
title: Intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de JAMF Pro
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
description: Découvrez comment intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de JAMF Pro
ms.openlocfilehash: a4f6928098525cf04c2e752b8c6d467800f270da
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635620"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>Intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de JAMF Pro

Vous pouvez utiliser JAMF Pro pour intégrer des appareils macOS dans des solutions Microsoft Purview telles que la protection contre la perte de données de point de terminaison.

> [!IMPORTANT]
> Utilisez cette procédure si vous ***n’avez pas*** déployé Microsoft Defender pour point de terminaison (MDE) sur vos appareils macOS

**S’applique à :**

- [Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md)

## <a name="before-you-begin"></a>Avant de commencer

- Assurez-vous que vos [appareils macOS sont gérés via JAMF pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) et associés à une identité (UPN joint à Azure AD) via JAMF Connect ou Intune.
- Installer le navigateur v95+ Edge sur vos appareils macOS

## <a name="onboard-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>Intégrer des appareils dans des solutions Microsoft Purview à l’aide de JAMF Pro

1. Vous aurez besoin de ces fichiers pour cette procédure.

|Fichier nécessaire pour|Source|
|---|---|
|Package d’intégration|Téléchargé à partir du **package d’intégration** du portail de conformité, nom *de fichier DeviceComplianceOnboarding.plist*|
|Accessibilité|[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
accès au disque complet|[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Filtre réseau| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)
|Extensions système|[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|Préférence MDE|[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/schema.json)|
|Préférence MAU|[com.microsoft.autoupdate2.plist](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.plist)|
|Package d’installation|téléchargé à partir du **package d’installation** du portail de conformité, nom *\*de fichier wdav.pkg*\*|

> [!TIP]
> Vous pouvez télécharger les fichiers *.mobileconfig* individuellement ou dans un [seul fichier combiné](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) contenant :
>
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - sysext.mobileconfig
>
>Si l’un de ces fichiers individuels est mis à jour, vous devez télécharger à nouveau le fichier combiné ou le fichier unique mis à jour individuellement.

L’intégration d’un appareil macOS dans les solutions de conformité est un processus multiphase.

### <a name="get-the-device-onboarding-package"></a>Obtenir le package d’intégration d’appareil

1. Dans **le Centre de conformité** , **ouvrez Paramètres** > **de l’intégration des appareils** et choisissez **Intégration**.

1. Pour **sélectionner le système d’exploitation pour commencer le processus d’intégration** , choisissez **macOS**

1. Pour **la méthode Déploiement,** choisissez **Mobile Gestion des appareils/Microsoft Intune**

1. Choisir **télécharger le package d’intégration**

1. Extrayez le contenu du package d’intégration d’appareil. Dans le dossier JAMF, vous devez voir le fichier *DeviceComplainceOnboarding.plist* .

### <a name="create-a-jamf-pro-configuration-profile-for-the-onboarding-package"></a>Créer un profil de configuration JAMF Pro pour le package d’intégration

1. Créez un profil de configuration dans JAMF Pro. Reportez-vous au [guide des administrateurs JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Utilisez les valeurs suivantes :
    - Nom : `MDATP onboarding for macOS`
    - Description: `MDATP EDR onboarding for macOS`
    - Catégorie: `none`
    - Méthode de distribution : `install automatically`
    - Niveau: `computer level`

2. Dans la console JAMF Pro > **application & paramètres personnalisés**, choisissez **charger** , puis **ajouter**. Utilisez cette valeur :
    - Domaine de préférence : `com.microsoft.wdav.atp`

3. Choisissez **charger** et sélectionner le fichier d’intégration **DeviceComplianceOnboarding.plist**.

4. Choisissez l’onglet **Étendue** .

5. Choisissez les ordinateurs cibles.

6. Cliquez sur **Enregistrer**.

7. Choisissez **OK**.

### <a name="configure-preference-domain-using-the-jamf-pro-console"></a>Configurer le domaine préférence à l’aide de la console JAMF PRO

> [!IMPORTANT]
> Vous devez utiliser ***com.microsoft.wdav** _ comme valeur de domaine de préférence. Microsoft Defender pour point de terminaison utilise ce nom et _ *_com.microsoft.wdav.ext_** pour charger ses paramètres managés.

1. Créez un profil de configuration dans JAMF Pro. Reportez-vous au [guide des administrateurs JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Utilisez les valeurs suivantes :
    - Nom : `MDATP MDAV configuration settings`
    - Description : laissez ce champ vide
    - Catégorie: `none`
    - Méthode de distribution : `install automatically`
    - Niveau: `computer level`

1. Sous l’onglet **Application & Paramètres personnalisés** , choisissez **Applications externes**, **ajoutez** et choisissez **Schéma personnalisé** pour le domaine de préférence. Utilisez cette valeur :
    - Domaine de préférence : `com.microsoft.wdav`

1. Choisissez **Ajouter un schéma** et **Charger** pour charger le fichier *schema.json* .

1. Cliquez sur **Enregistrer**.

1. Sous **Propriétés de domaine de préférence** , choisissez ces paramètres
    - Fonctionnalités
        - Utiliser les extensions système : `enabled` requis pour les extensions réseau sur Catalina
        - Utilisez la protection contre la perte de données : `enabled`
    - Moteur antivirus > mode passif : `true|false`. À utiliser `true`si vous déployez DLP uniquement. Utilisez `false` ou n’affectez pas de valeur si vous déployez DLP et Microsoft Defender pour point de terminaison (MDE).

1. Choisissez l’onglet **Étendue** .

1. Choisissez les groupes sur lesquels déployer ce profil de configuration.

1. Cliquez sur **Enregistrer**.

### <a name="create-and-deploy-a-configuration-profile-for-microsoft-autoupdate-mau"></a>Créer et déployer un profil de configuration pour Microsoft AutoUpdate (MAU)

1. Créez un fichier de configuration JAMF Pro à l’aide de **com.microsoft.autoupdate2.plist**. Reportez-vous au [guide des administrateurs JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Utilisez les valeurs suivantes :
    - Nom : `MDATP MDAV MAU settings`
    - Description: `Microsoft AutoUPdate settings for MDATP for macOS`
    - Catégorie: `none`
    - Méthode de distribution : `install automatically`
    - Niveau: `computer level`

1. Dans **Application & paramètres personnalisés** , **choisissez Charger** et **ajouter**.

1. Dans **Préférences,** entrez `com.microsoft.autoupdate2` le domaine, puis **choisissez Charger**.

1. Choisissez le fichier **com.microsoft.autoupdate2.plist** .

1. Cliquez sur **Enregistrer**.

1. Choisissez l’onglet **Étendue** .

1. Choisissez les ordinateurs cibles.

1. Cliquez sur **Enregistrer**.

1. Choisissez **OK**.

### <a name="create-and-deploy-a-configuration-profile-for-grant-full-disk-access"></a>Créer et déployer un profil de configuration pour accorder l’accès complet au disque

1. Utilisez le fichier **fulldisk.mobileconfig** .

1. Chargez le fichier **fulldisk.mobileconfig** dans JAMF. Reportez-vous au [déploiement de profils de configuration personnalisés à l’aide de JAMF Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="create-and-deploy-a-configuration-profile-for-system-extensions"></a>Créer et déployer un profil de configuration pour les extensions système

1. Créez un fichier de configuration JAMF Pro à l’aide des procédures du [guide des administrateurs JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Utilisez les valeurs suivantes :
    - Nom : `MDATP MDAV System Extensions`
    - Description: `MDATP system extensions`
    - Catégorie: `none`
    - Méthode de distribution : `install automatically`
    - Niveau: `computer level`

1. Dans le profil **d’extensions système** , entrez les valeurs suivantes :
    - Nom d’affichage : `Microsoft Corp. System Extensions`
    - Types d’extensions système : `Allowed System Extensions`
    - Identificateur d’équipe : `UBF8T346G9`
    - Extensions système autorisées : `com.microsoft.wdav.epsext`et `com.microsoft.wdav.netext`

1. Choisissez l’onglet **Étendue** .

1. Choisissez les ordinateurs cibles.

1. Cliquez sur **Enregistrer**.

1. Choisissez **OK**.

### <a name="configure-network-extension"></a>Configurer l’extension réseau

1. Utilisez le fichier **netfilter.mobileconfig**  que vous avez téléchargé à partir de GitHub.

2. Chargez sur JAMF comme décrit dans [le déploiement de profils de configuration personnalisés à l’aide de Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="grant-accessibility-access-to-dlp"></a>Accorder l’accès d’accessibilité à DLP

1. Utilisez le fichier **accessibility.mobileconfig** que vous avez téléchargé à partir de GitHub.

2. Chargez sur JAMF comme décrit dans [le déploiement de profils de configuration personnalisés à l’aide de Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="get-the-installation-package"></a>Obtenir le package d’installation

1. Dans **le Centre de conformité** , **ouvrez Paramètres** > **de l’intégration des appareils** et choisissez **Intégration**.

1. Pour **sélectionner le système d’exploitation pour commencer le processus d’intégration** , choisissez **macOS**

1. Pour **la méthode Déploiement,** choisissez **Mobile Gestion des appareils/Microsoft Intune**

1. Choisissez **Télécharger le package d’installation**. Cela vous donnera le fichier *wdav.pkg* .

### <a name="deploy-the-installation-package"></a>Déployer le package d’installation

1. Accédez à l’emplacement où vous avez enregistré le `wdav.pkg` fichier.

1. Ouvrez le tableau de bord JAMF Pro.

1. Sélectionnez votre ordinateur, cliquez sur l’engrenage en haut, puis choisissez **Gestion de l’ordinateur**.

1. Dans **Packages,** choisissez **+Nouveau**. Entrez les détails suivants :
    - Nom d’affichage : laissez vide, car il sera réinitialisé lorsque vous choisirez le fichier .pkg.
    - Catégorie : Aucun (valeur par défaut)
    - Nom de fichier : choisissez le fichier, dans ce cas le `wdav.pkg` fichier.

1. Sélectionnez **Ouvrir**. Ensemble:
    - **Nom d’affichage** : `Microsoft Endpoint Technology`
    - **Fichier manifeste** : non requis
    - **Onglet Options** : conserver les valeurs par défaut
    - **Onglet Limitations** : conserver les valeurs par défaut

1. Cliquez sur **Enregistrer**. Cela charge le package sur JAMF Pro.

1. Ouvrez la page **Stratégies** .

1. Choisissez **+Nouveau** pour créer une stratégie.

1. Entrez ces valeurs
    - **Nom d’affichage** : `MDATP Onboarding200329 v100.86.92 or later`

1. Choisissez **l’archivage périodique**.

1. Cliquez sur **Enregistrer**.

1. Choisissez **Configurer les packages** > **.**

1. Sélectionnez **Ajouter**.

1. Cliquez sur **Enregistrer**.

1. Choisissez l’onglet **Étendue** .

1. Sélectionnez les ordinateurs cibles.

1. Sélectionnez **Ajouter**.

1. Choisissez **libre-service**.

1. Choisissez **OK**.

### <a name="check-the-macos-device"></a>Vérifier l’appareil macOS

1. Redémarrez l’appareil macOS.

1. Ouvrez **les profils de préférences** >  système.

1. Vous devriez voir :
    - Accessiblity
    - Accès au disque complet
    - MAU
    - Intégration MDATP
    - Préférences MDE
    - Profil de gestion
    - Filtre réseau
    - Profil d’extension système

## <a name="offboard-macos-devices-using-jamf-pro"></a>Désins border des appareils macOS à l’aide de JAMF Pro

1. Désinstaller l’application (si vous n’utilisez pas MDE)
    1. Voir JAMF Pro Docs - Déploiement de package - [Guide des administrateurs JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/)

1. Redémarrer l’appareil macOS : certaines applications risquent de perdre la fonctionnalité d’impression jusqu’à ce qu’elles soient redémarrées

> [!IMPORTANT]
> La désintégération entraîne l’arrêt de l’envoi de données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois maximum.
