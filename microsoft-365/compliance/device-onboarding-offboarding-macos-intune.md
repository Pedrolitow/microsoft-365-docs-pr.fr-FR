---
title: Intégrer et intégrer des appareils macOS dans Microsoft 365 solutions de conformité à l’aide Microsoft Intune (prévisualisation)
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
description: Découvrez comment intégrer et utiliser des appareils macOS dans des solutions Microsoft 365 conformité à l’aide Microsoft Intune (prévisualisation)
ms.openlocfilehash: fb3e89b303c8c17de3eb6826c25d2b54be364b7e
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60717461"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-intune-preview"></a>Intégration et intégration d’appareils macOS dans des solutions Microsoft 365 conformité à l’aide d’Intune (prévisualisation)

Vous pouvez utiliser Intune pour intégrer des appareils macOS dans Microsoft 365 solutions de conformité.

> [!IMPORTANT]
> Utilisez cette procédure si ***Microsoft*** Defender pour point de terminaison (MDE) n’est pas déployé sur vos appareils macOS

## <a name="get-registered"></a>S’inscrire

Pour accéder à cette fonctionnalité, vous devez inscrire votre client auprès de Microsoft. Voir, [inscrivez-vous à la Microsoft 365 prise en charge macOS.](https://aka.ms/Ignite2021DLP)

**S’applique à :**

- [Microsoft 365 Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>Avant de commencer

- Assurez-vous que vos appareils macOS sont intégrés à [Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) et qu’ils sont inscrits dans [l Portail d'entreprise app.](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp) 
- Assurez-vous que vous avez accès au [centre de Microsoft Endpoint Manager.](https://endpoint.microsoft.com/#home)
- Cela prend en charge macOS version 10.15 et versions supérieures.
- Créez les groupes d’utilisateurs à qui vous allez affecter les mises à jour de configuration.
- Installer le navigateur Edge v95+ sur vos appareils macOS 


## <a name="onboard-macos-devices-into-microsoft-365-compliance-solutions-using-microsoft-intune"></a>Intégrer des appareils macOS dans des solutions Microsoft 365 conformité à l’aide Microsoft Intune

L’intégration d’un appareil macOS aux solutions de conformité est un processus en six phases.

1. [Créer des profils de configuration système](#create-system-configuration-profiles)
1. [Obtenir le package d’intégration d’appareil](#get-the-device-onboarding-package)
1. [Déployer le package d’intégration](#deploy-the-onboarding-package)
1. [Activer l’extension système](#enable-system-extension)
1. [Obtenir le package d’installation](#get-the-installation-package)
1. [Déployer le package d’installation](#deploy-the-microsoft-dlp-installation-package)

### <a name="create-system-configuration-profiles"></a>Créer des profils de configuration système

1. Vous aurez besoin de ces fichiers pour cette procédure.

|fichier nécessaire pour |source |
|---------|---------|
|Package d’intégration    |téléchargé à partir du **package d’intégration du** portail de *conformité,* nom de fichierDeviceComplianceOnboarding.xml |
|accessibilité |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
accès disque complet     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|S filer réseau| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)]
|Extensions système |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/systext.mobileconfig)
|Préférence MDE     |[com.microsoft.wdav.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig)|
|Préférence MAU|[com.microsoft.autoupdate2.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.mobileconfig)|
|Package d’installation     |téléchargé à partir du **package d’installation** du portail de conformité, nom de *\* fichier wdav.pkg*\* |

> [!TIP]
> Vous pouvez télécharger les fichiers *.mobileconfig* individuellement ou dans un seul fichier [combiné qui](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) contient :
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - extensions système
>
>Si l’un de ces fichiers individuels est mis à jour, vous devez télécharger à nouveau le fichier combiné ou le fichier unique mis à jour individuellement.

<!--2. Copy this code and save it in a file named `com.microsoft.autoupdate2.xml`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>B762FF60-6ACB-4A72-9E72-459D00C936F3</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.autoupdate2</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft AutoUpdate settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft AutoUpdate configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
            <key>PayloadUUID</key>
            <string>5A6F350A-CC2C-440B-A074-68E3F34EBAE9</string>
            <key>PayloadType</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadOrganization</key>
            <string>Microsoft</string>
            <key>PayloadIdentifier</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft AutoUpdate configuration settings</string>
            <key>PayloadDescription</key>
            <string/>
            <key>PayloadVersion</key>
            <integer>1</integer>
            <key>PayloadEnabled</key>
            <true/>
            <key>ChannelName</key>
            <string>Production</string>
            <key>HowToCheck</key>
            <string>AutomaticDownload</string>
            <key>EnableCheckForUpdatesButton</key>
            <true/>
            <key>DisableInsiderCheckbox</key>
            <false/>
            <key>SendAllTelemetryEnabled</key>
            <true/>
            </dict>
        </array>
    </dict>
</plist>
```
-->

2. Ouvrez le **centre Microsoft Endpoint Manager**  >  **profils de**  >  **configuration des appareils.**

1. Choose: **Create profile** 

1. Choisissez :
    1. **Plateforme = macOS**
    1. **Type de profil = Modèles**
    1. **Nom du modèle = Personnalisé**

1. Choose **Create**

1. Choisissez un nom pour le profil, comme *AccessibilityformacOS* dans cet exemple. Cliquez sur **Suivant**.

1. Choisissez le **fichier accessibility.mobileconfig** que vous avez téléchargé à l’étape 1 comme fichier de profil de configuration.

1. Choose **Next**

1. Sous **l’onglet Affectations,** ajoutez le groupe sur qui vous souhaitez déployer ces configurations et choisissez **Suivant.**

1. Examinez vos paramètres et choisissez **Créer** pour déployer la configuration.

1. Répétez les étapes 3 à 11 pour créer des profils pour :
    1. **fichier fulldisk.mobileconfig**
    1. **com.microsoft.autoupdate2.xml** fichier
    1. Préférences MDE **com.microsoft.wdav.xml** fichier
        1. définissez le moteur antivirus `passive mode`  =  `true` ou `false` . À `true` utiliser en cas de déploiement de DLP uniquement. Utilisez `false` ou n’affectez pas de valeur si vous déployez DLP et Microsoft Defender pour le point de terminaison (MDE).
    1. **netfilter.mobileconfig**
 
1. Ouvrez **les**  >  **profils de configuration des** appareils , vous devriez voir vos profils créés ici.

1. Dans la page **Profils** de configuration, choisissez le profil que vous  avez créé, dans cet exemple *AccessibilityformacOS,* puis choisissez État de l’appareil pour voir la liste des appareils et l’état de déploiement du profil de configuration.

### <a name="get-the-device-onboarding-package"></a>Obtenir le package d’intégration d’appareil

1. Dans **le Centre de conformité,** **Paramètres**  >  **l’intégration d’appareil** et choisissez **Intégration.**
 
1. Pour **sélectionner le système d’exploitation afin de démarrer le processus d’intégration,** choisissez **macOS.**
 
1. For **Deployment method** choose Mobile Device **Management/Microsoft Intune**.
 
1. Choisissez **Télécharger le package d’intégration.** Il contient le code d’intégration dans *DeviceComplianceOnboarding.xml* fichier.

### <a name="deploy-the-onboarding-package"></a>Déployer le package d’intégration

1. Ouvrez le **centre Microsoft Endpoint Manager**  >  **profils de**  >  **configuration des appareils.**

1. Choose: **Create profile**. 

1. Choisissez :
    1. **Plateforme = macOS**
    1. **Type de profil = Modèles**
    1. **Nom du modèle = Personnalisé**

1. Choose **Create**

1. Choisissez un nom pour le profil, comme *OnboardingPackage* dans cet exemple. Cliquez sur **Suivant**.

1. Choisissez le *DeviceComplianceOnboarding.xml* fichier de profil de configuration.

1. Choose **Next**

1. Sous **l’onglet Affectations,** ajoutez le groupe sur qui vous souhaitez déployer ces configurations et choisissez **Suivant.**

1. Examinez vos paramètres et choisissez **Créer** pour déployer la configuration.

### <a name="enable-system-extension"></a>Activer l’extension système

1. Dans le centre Microsoft Endpoint Manager **sélectionnez Créer un profil sous**  **Profils de configuration**

1. Choisissez :
    1. **Plateforme = macOS**
    1. **Type de profil = Modèles**
    1. **Nom du modèle = Extensions**

1. Choose **Create**

1. Sous **l’onglet Éléments de** base, nommez ce nouveau profil.

1. Dans **l’onglet Paramètres de configuration,** **développez Extensions système.**

1. Sous **l’identificateur d’ensemble** et **l’identificateur** d’équipe, définissez ces valeurs

|Identificateur d’ensemble  |Identificateur d’équipe  |
|---------|---------|
|**com.microsoft.wdav.epsext**|**UBF8T346G9**|
|**com.microsoft.wdav.netext**|**UBF8T346G9**|


1. Sous **l’onglet Affectations,** ajoutez le groupe sur qui vous souhaitez déployer ces configurations et choisissez **Suivant.**

1. Choisissez **Suivant** pour déployer la configuration.

### <a name="get-the-installation-package"></a>Obtenir le package d’installation

1. Dans **le Centre de conformité,** **Paramètres**  >  **l’intégration d’appareil** et choisissez **Intégration.**
 
1. Pour **sélectionner le système d’exploitation afin de démarrer le processus d’intégration,** choisissez **macOS**
 
1. Pour **la méthode Déploiement,** choisissez **Gestion des périphériques mobiles/Microsoft Intune**
 
1. Choisissez **Télécharger le package d’installation.** Cela vous donnera le *fichier wdav.pkg.*

> [!IMPORTANT]
> Avant de pouvoir déployer *le wdav.pkg.* via Intune, il doit être reformaté à l’aide des outils d’habillage d’application *Intune* pour Mac au format *wdav.pkg.intunemac.*
 

### <a name="deploy-the-microsoft-dlp-installation-package"></a>Déployer le package d’installation Microsoft DLP

1. Suivez les procédures de la procédure d’ajout d’applications [métier macOS](/mem/intune/apps/lob-apps-macos) à Microsoft Intune pour convertir le fichier *wdav.pkg* au format approprié et le déployer via Intune.

## <a name="offboard-macos-devices-using-intune"></a>Offboard macOS devices using Intune

> [!NOTE]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant six mois.

2. Dans **Microsoft Endpoint Manager, ouvrez** **les** profils de configuration des appareils, vous devez y voir vos  >  profils créés.

1. Dans la page **Profils de** configuration, choisissez le *profil wdav.pkg.intunemac.*

1. Choose **Device status** to see a list of devices and the deployment status of the configuration profile

1. Ouvrir **les propriétés** et **les affectations**

1. Supprimez le groupe de l’affectation. Cela désinstalle le package *wdav.pkg.intunemac* et désinstalle l’appareil macOS des solutions de conformité.
