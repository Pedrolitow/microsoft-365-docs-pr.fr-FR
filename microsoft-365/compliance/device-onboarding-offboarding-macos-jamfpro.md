---
title: Intégration et désintération des appareils macOS dans Microsoft 365 solutions de conformité à l’aide de JAMF Pro (prévisualisation)
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
description: Découvrez comment intégrer et désinséboarder des appareils macOS dans des solutions de conformité Microsoft 365 à l’aide de JAMF Pro (prévisualisation)
ms.openlocfilehash: c1fefa8263b2bee9b11156ae18c218520eeae5a8
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60701319"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-jamf-pro-preview"></a>Intégration et désintération des appareils macOS dans Microsoft 365 solutions de conformité à l’aide de JAMF Pro (prévisualisation)

Vous pouvez utiliser jamf Pro pour intégrer des appareils macOS dans Microsoft 365 solutions de conformité telles que la protection contre la perte de données de point de terminaison.

> [!IMPORTANT]
> Utilisez cette procédure si ***Microsoft*** Defender pour point de terminaison (MDE) n’est pas déployé sur vos appareils macOS

## <a name="get-registered"></a>S’inscrire

Pour accéder à cette fonctionnalité, vous devez inscrire votre client auprès de Microsoft. Voir, [inscrivez-vous à la Microsoft 365 prise en charge macOS.](https://aka.ms/Ignite2021DLP)

**S’applique à :**

- [Microsoft 365 Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>Avant de commencer

- Assurez-vous que vos [appareils macOS sont Azure AD joints](https://docs.jamf.com/10.30.0/jamf-pro/administrator-guide/Azure_AD_Integration.html)
- Assurez-vous que vos [appareils macOS sont gérés via JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/)
- Installer le navigateur Edge v95+ sur vos appareils macOS 

## <a name="onboard-devices-into-microsoft-365-compliance-solutions-using-jamf-pro"></a>Intégrer des appareils dans des solutions Microsoft 365 conformité à l’aide de JAMF Pro

1. Vous aurez besoin de ces fichiers pour cette procédure.

|fichier nécessaire pour |source |
|---------|---------|
|Package d’intégration    |téléchargé à partir du **package d’intégration** du portail de conformité , nom de *fichier DeviceComplianceOnboarding.plist* |
|accessibilité |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
accès disque complet     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Filtre réseau| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)
|Extensions système |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/systext.mobileconfig)
|Préférence MDE     |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/schema.json)|
|Préférence MAU|[com.microsoft.autoupdate2.plist](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.plist)|
|Package d’installation     |téléchargé à partir du **package d’installation** du portail de conformité, nom de *\* fichier wdav.pkg*\* |

> [!TIP]
> Vous pouvez télécharger les fichiers *.mobileconfig* individuellement ou dans un seul fichier [combiné qui](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) contient :
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - sysext.mobileconfig
>
>Si l’un de ces fichiers individuels est mis à jour, vous devez télécharger à nouveau le fichier combiné ou le fichier unique mis à jour individuellement.

L’intégration d’un appareil macOS dans des solutions de conformité est un processus en plusieurs phases.

### <a name="get-the-device-onboarding-package"></a>Obtenir le package d’intégration d’appareil

1. Dans **le Centre de conformité,** **Paramètres**  >  **l’intégration d’appareil** et choisissez **Intégration.**
 
1. Pour **sélectionner le système d’exploitation afin de démarrer le processus d’intégration,** choisissez **macOS**
 
1. Pour **la méthode Déploiement,** choisissez **Gestion des périphériques mobiles/Microsoft Intune**
 
1. Choose **Download onboarding package**
 
1. Extraire le contenu du package d’intégration d’appareil. Dans le **dossier JAMF,** vous devez voir le *fichier DeviceCompcompcompceOnboarding.plist.*

### <a name="create-a-jamf-pro-configuration-profile-for-the-onboarding-package"></a>Créer un profil de configuration Pro JAMF pour le package d’intégration

1. Créez un profil de configuration dans JAMF Pro. Reportez-vous [au guide jamf Pro administrateurs.](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Utilisez les valeurs ci-après :
    - Nom : `MDATP onboarding for macOS`
    - Description : `MDATP EDR onboarding for macOS`
    - Catégorie : `none`
    - Méthode de distribution : `install automatically`
    - Niveau : `computer level`

2. Dans la console JAMF Pro **> Application & paramètres personnalisés,** choisissez télécharger, puis **ajoutez**.  Utilisez cette valeur :
    - Domaine de préférence : `com.microsoft.wdav.atp`

3. Choisissez **télécharger** et sélectionnez le fichier d’intégration **DeviceComplianceOnboarding.plist**.

4. Choisissez **l’onglet d’étendue.**

5. Choisissez les ordinateurs cibles.

6. Cliquez sur **Enregistrer**.

7. Choisissez **OK**.

### <a name="configure-preference-domain-using-the-jamf-pro-console"></a>Configurer le domaine de préférence à l’aide de la console JAMF PRO

> [!IMPORTANT]
> Vous devez utiliser ***com.microsoft.wdav** _ comme valeur de domaine de préférence. Microsoft Defender utilise ce nom et _ *_com.microsoft.wdav.ext_** pour charger ses paramètres gérés.

1. Créez un profil de configuration dans JAMF Pro. Reportez-vous [au guide jamf Pro administrateurs.](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Utilisez les valeurs ci-après :
    - Nom : `MDATP MDAV configuration settings`
    - Description : laissez ce vide
    - Catégorie : `none`
    - Méthode de distribution : `install automatically`
    - Niveau : `computer level`

1. Sous **l’onglet & application** Paramètres, choisissez **Applications** externes,  Ajouter et choisir Un schéma personnalisé pour le domaine de préférence.  Utilisez cette valeur :
    - Domaine de préférence : `com.microsoft.wdav`

1. Choose **Add Schema** and **Télécharger** to upload the *schema.json* file.

1. Cliquez sur **Enregistrer**.

1. Sous **Préférences, les propriétés de domaine** choisissent ces paramètres
    - Fonctionnalités 
        - Utiliser les extensions système : `enabled` - requis pour les extensions réseau sur Contrôle
        - Utilisez la protection contre la perte de données : `enabled`
    - Moteur antivirus > mode passif : `true|false` . À `true` utiliser en cas de déploiement de DLP uniquement. Utilisez `false` ou n’affectez pas de valeur si vous déployez DLP et Microsoft Defender pour le point de terminaison (MDE).

1. Sélectionnez **l’onglet** Étendue.

1. Choisissez les groupes vers qui déployer ce profil de configuration.

1. Cliquez sur **Enregistrer**. 


### <a name="create-and-deploy-a-configuration-profile-for-microsoft-autoupdate-mau"></a>Créer et déployer un profil de configuration pour la mise à jour automatique Microsoft (AutoUpdate)

1. Créez un fichier de configuration Pro JAMF à l’aide de **com.microsoft.autoupdate2.plist.** Reportez-vous [au guide jamf Pro administrateurs.](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Utilisez les valeurs ci-après :
    - Nom : `MDATP MDAV MAU settings`
    - Description : `Microsoft AutoUPdate settings for MDATP for macOS`
    - Catégorie : `none`
    - Méthode de distribution : `install automatically`
    - Niveau : `computer level`

1. In **Application & Custom Paramètres** choose **Télécharger** and **Add**.

1. In **Preferences Domain** enter `com.microsoft.autoupdate2` and then choose **Télécharger**.

1. Choisissez le **fichier com.microsoft.autoupdate2.plist.**

1. Cliquez sur **Enregistrer**.

1. Sélectionnez **l’onglet** Étendue.

1. Choisissez les ordinateurs cibles.

1. Cliquez sur **Enregistrer**.

1. Choisissez **OK**.


### <a name="create-and-deploy-a-configuration-profile-for-grant-full-disk-access"></a>Créer et déployer un profil de configuration pour accorder un accès disque total

1. Utilisez le **fichier fulldisk.mobileconfig.**

1. Télécharger le **fichier fulldisk.mobileconfig** sur JAMF. Reportez-vous [au déploiement de profils de configuration personnalisés à l’aide](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html)de JAMF Pro .

### <a name="create-and-deploy-a-configuration-profile-for-system-extensions"></a>Créer et déployer un profil de configuration pour les extensions système

1. Créez un fichier de configuration Pro JAMF à l’aide des procédures de [JAMF Pro guide des administrateurs.](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Utilisez les valeurs ci-après :
    - Nom : `MDATP MDAV System Extensions`
    - Description : `MDATP system extensions`
    - Catégorie : `none`
    - Méthode de distribution : `install automatically`
    - Niveau : `computer level`

1. Dans le **profil d’étendues système,** entrez les valeurs ci-après :
    - Nom complet : `Microsoft Corp. System Extensions`
    - Types d’extenstion système : `Allowed System Extensions`
    - Identificateur d’équipe : `UBF8T346G9`
    - Extensions système autorisées `com.microsoft.wdav.epsext` : et `com.microsoft.wdav.netext`

1. Sélectionnez **l’onglet** Étendue.

1. Choisissez les ordinateurs cibles.

1. Cliquez sur **Enregistrer**.

1. Choisissez **OK**.

### <a name="configure-network-extension"></a>Configurer l’extension réseau

1.  Utilisez le **fichier netfilter.mobileconfig**  que vous avez téléchargé à partir de Github.

2.  Télécharger à JAMF comme décrit dans le déploiement de profils de configuration personnalisés à l’aide de [Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="grant-accessibility-access-to-dlp"></a>Accorder l’accès à l’accessibilité à la DLP

1. Utilisez le **fichier accessibility.mobileconfig** que vous avez téléchargé à partir de Github.

2.  Télécharger à JAMF comme décrit dans le déploiement de profils de configuration personnalisés à l’aide de [Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="get-the-installation-package"></a>Obtenir le package d’installation

1. Dans **le Centre de conformité,** **Paramètres**  >  **l’intégration d’appareil** et choisissez **Intégration.**
 
1. Pour **sélectionner le système d’exploitation afin de démarrer le processus d’intégration,** choisissez **macOS**
 
1. Pour **la méthode Déploiement,** choisissez **Gestion des périphériques mobiles/Microsoft Intune**
 
1. Choisissez **Télécharger le package d’installation.** Cela vous donnera le *fichier wdav.pkg.*


### <a name="deploy-the-installation-package"></a>Déployer le package d’installation

1. Accédez à l’endroit où vous avez enregistré le `wdav.pkg` fichier.

1. Ouvrez le tableau de bord Pro JAMF.

1. Sélectionnez votre ordinateur et cliquez sur l’engrenage en haut, puis choisissez **Gestion de l’ordinateur.**

1. Dans **les packages,** **choisissez +Nouveau**. Entrez les détails ci-après :
    - Nom complet : laissez vide, car il sera réinitialisé lorsque vous choisirez le fichier .pkg.
    - Catégorie : Aucun (par défaut)
    - Filname : choisissez le fichier, dans ce cas, le `wdav.pkg` fichier.

1. Sélectionnez **Ouvrir**. Set:
    - **Nom complet**: `Microsoft Endpoint Technology`
    - **Fichier manifeste :** non requis
    - **Onglet Options :** laisser les valeurs par défaut
    - **Onglet Limitations :** laisser les valeurs par défaut

1. Cliquez sur **Enregistrer**. Cela télécharge le package vers JAMF Pro.

1. Ouvrez la page **Stratégies.**

1. Choisissez **+Nouveau** pour créer une stratégie.

1. Entrez ces valeurs
    - **Nom d’affichage**: `MDATP Onboarding200329 v100.86.92 or later`

1. Choose **Recurring Check-in**.

1. Cliquez sur **Enregistrer**.

1. Choose **Packages**  >  **Configure**.

1. Sélectionnez **Ajouter**.

1. Cliquez sur **Enregistrer**. 

1. Sélectionnez **l’onglet** Étendue.

1. Sélectionnez les ordinateurs cibles.

1. Sélectionnez **Ajouter**.

1. Choisissez **libre-service.**

1. Choisissez **OK**.

### <a name="check-the-macos-device"></a>Vérifier l’appareil macOS 

1. Redémarrez l’appareil macOS.

1. Ouvrez **les profils de préférences**  >  **système.**

1. Vous devriez voir :
    - Accessiblity
    - Accès disque total
    - MAU
    - Intégration MDATP
    - Préférences MDE
    - Profil de gestion
    - Filtre réseau
    - Profil d’extension système

## <a name="offboard-macos-devices-using-jamf-pro"></a>Désinséboarder des appareils macOS à l’aide de jamf Pro

1. Désinstaller l’application (si vous n’utilisez pas MDE)
    1. Voir JAMF Pro Documents - Déploiement de packages - [Guide jamf](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/)Pro administrateurs jamf Pro administrateur

1. Redémarrer l’appareil macOS : certaines applications peuvent perdre des fonctionnalités d’impression jusqu’à ce qu’elles soient redémarrés

> [!IMPORTANT]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois.

