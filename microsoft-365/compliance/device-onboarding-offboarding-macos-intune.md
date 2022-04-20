---
title: Intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de Microsoft Intune
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
description: Découvrez comment intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de Microsoft Intune
ms.openlocfilehash: 99a407b2b0c8d6a506cd138078b3f35cf9e5a232
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952971"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-purview-solutions-using-intune"></a>Intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de Intune

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Vous pouvez utiliser Intune pour intégrer des appareils macOS dans des solutions Microsoft Purview.

> [!IMPORTANT]
> Utilisez cette procédure si vous ***n’avez pas*** déployé Microsoft Defender pour point de terminaison (MDE) sur vos appareils macOS

**S’applique à :**

- [Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md)

## <a name="before-you-begin"></a>Avant de commencer

- Assurez-vous que vos [appareils macOS sont intégrés à Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) et inscrits dans l’application [Portail d'entreprise](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Vérifiez que vous avez accès au [centre de Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home).
- Cela prend en charge macOS version Catalina 10.15 et versions ultérieures.
- Créez les groupes d’utilisateurs auxquels vous allez affecter les mises à jour de configuration.
- Installer le navigateur v95+ Edge sur vos appareils macOS 


## <a name="onboard-macos-devices-into-microsoft-purview-solutions-using-microsoft-intune"></a>Intégrer des appareils macOS dans des solutions Microsoft Purview à l’aide de Microsoft Intune

L’intégration d’un appareil macOS dans les solutions de conformité est un processus en six phases.

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
|Package d’intégration    |téléchargé à partir du **package d’intégration** du portail de conformité, nom de fichier *DeviceComplianceOnboarding.xml* |
|Accessibilité |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
accès au disque complet     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Filer réseau| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)]
|Extensions système |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|Préférence MDE     |[com.microsoft.wdav.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig)|
|Préférence MAU|[com.microsoft.autoupdate2.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.mobileconfig)|
|Package d’installation     |téléchargé à partir du **package d’installation** du portail de conformité, nom *\*de fichier wdav.pkg*\* |

> [!TIP]
> Vous pouvez télécharger les fichiers *.mobileconfig* individuellement ou dans un [seul fichier combiné](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) contenant :
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

2. Ouvrez les **profils Microsoft Endpoint Manager** **centerDevicesConfiguration** >  > .

1. Choisir : **Créer un profil** 

1. Choisir:
    1. **Platform = macOS**
    1. **Type de profil = Modèles**
    1. **Nom du modèle = Personnalisé**

1. Choisir **Créer**

1. Choisissez un nom pour le profil, comme *AccessibilityformacOS* dans cet exemple. Cliquez sur **Suivant**.

1. Choisissez le fichier **accessibility.mobileconfig** que vous avez téléchargé à l’étape 1 comme fichier de profil de configuration.

1. Sélectionnez **Suivant**

1. Sous l’onglet **Affectations** , ajoutez le groupe sur lequel vous souhaitez déployer ces configurations et choisissez **Suivant**.

1. Passez en revue vos paramètres et **choisissez Créer** pour déployer la configuration.

1. Répétez les étapes 3 à 11 pour créer des profils pour les éléments :
    1. **fichier fulldisk.mobileconfig**
    1. **fichiercom.microsoft.autoupdate2.xml**
    1. Préférences MDE **com.microsoft.wdav.xml** fichier
        1. définir le moteur `passive mode` = `true` antivirus ou `false`. À utiliser `true`si vous déployez DLP uniquement. Utilisez `false` ou n’affectez pas de valeur si vous déployez DLP et Microsoft Defender pour point de terminaison (MDE).
    1. **netfilter.mobileconfig**
 
1. Ouvrez **les** **profils DevicesConfiguration** > . Vous devez y voir vos profils créés.

1. Dans la page **Profils de configuration**, choisissez le profil que vous venez de créer, dans cet exemple *AccessibilityformacOS*, puis choisissez État de l’appareil pour afficher la liste des appareils et l’état de déploiement du profil de configuration.

### <a name="get-the-device-onboarding-package"></a>Obtenir le package d’intégration d’appareil

1. Dans **le Centre de conformité**, ouvrez **Paramètres** >  **Device Onboarding** et choisissez **Intégration**.
 
1. Pour **sélectionner le système d’exploitation à démarrer le processus d’intégration** , choisissez **macOS**.
 
1. Pour **la méthode Deployment,** choisissez **Mobile Gestion des appareils/Microsoft Intune**.
 
1. Choisissez **Télécharger le package d’intégration**. Il contient le code d’intégration dans le fichier *DeviceComplianceOnboarding.xml* .

### <a name="deploy-the-onboarding-package"></a>Déployer le package d’intégration

1. Ouvrez les **profils Microsoft Endpoint Manager** **centerDevicesConfiguration** >  > .

1. Choisissez : **Créer un profil**. 

1. Choisir:
    1. **Platform = macOS**
    1. **Type de profil = Modèles**
    1. **Nom du modèle = Personnalisé**

1. Choisir **Créer**

1. Choisissez un nom pour le profil, comme *OnboardingPackage* dans cet exemple. Cliquez sur **Suivant**.

1. Choisissez le fichier *DeviceComplianceOnboarding.xml* comme fichier de profil de configuration.

1. Sélectionnez **Suivant**

1. Sous l’onglet **Affectations** , ajoutez le groupe sur lequel vous souhaitez déployer ces configurations et choisissez **Suivant**.

1. Passez en revue vos paramètres et **choisissez Créer** pour déployer la configuration.

### <a name="enable-system-extension"></a>Activer l’extension système

1. Dans le **centre Microsoft Endpoint Manager**, sélectionnez **Créer un profil** sous **Profils de configuration**

1. Choisir:
    1. **Platform = macOS**
    1. **Type de profil = Modèles**
    1. **Nom du modèle = Extensions**

1. Choisir **Créer**

1. Sous l’onglet **De base** , donnez un nom à ce nouveau profil.

1. Dans l’onglet **Paramètres de configuration** , développez **Extensions système**.

1. Sous **Identificateur de bundle** et **identificateur d’équipe**, définissez ces valeurs

|Identificateur de bundle  |Identificateur d’équipe  |
|---------|---------|
|**com.microsoft.wdav.epsext**|**UBF8T346G9**|
|**com.microsoft.wdav.netext**|**UBF8T346G9**|


1. Sous l’onglet **Affectations** , ajoutez le groupe sur lequel vous souhaitez déployer ces configurations et choisissez **Suivant**.

1. Choisissez **Suivant** pour déployer la configuration.

### <a name="get-the-installation-package"></a>Obtenir le package d’installation

1. Dans **le Centre de conformité**, ouvrez **Paramètres** >  **Device Onboarding** et choisissez **Intégration**.
 
1. Pour **sélectionner le système d’exploitation pour commencer le processus d’intégration** , choisissez **macOS**
 
1. Pour **la méthode Déploiement,** choisissez **Mobile Gestion des appareils/Microsoft Intune**
 
1. Choisissez **Télécharger le package d’installation**. Cela vous donnera le fichier *wdav.pkg* .

> [!IMPORTANT]
> Avant de pouvoir déployer *wdav.pkg.* package via Intune, il doit être reformaté à l’aide de *l’Intune App Wrapping Tools pour Mac* au format *wdav.pkg.intunemac*.
 

### <a name="deploy-the-microsoft-dlp-installation-package"></a>Déployer le package d’installation microsoft DLP

1. Suivez les procédures décrites dans [Comment ajouter des applications métier macOS à Microsoft Intune](/mem/intune/apps/lob-apps-macos) pour convertir le fichier *wdav.pkg* au format approprié et le déployer via Intune.

## <a name="offboard-macos-devices-using-intune"></a>Désins border des appareils macOS à l’aide de Intune

> [!NOTE]
> La désintégration entraîne l’arrêt de l’envoi de données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées jusqu’à six mois.

2. Dans **Microsoft Endpoint Manager centre**, ouvrez **les** **profils DevicesConfiguration** > . Vous devez y voir vos profils créés.

1. Dans la page **Profils de configuration** , choisissez le profil *wdav.pkg.intunemac* .

1. Choisir **l’état** de l’appareil pour afficher la liste des appareils et l’état de déploiement du profil de configuration

1. Ouvrir **les propriétés** et **les affectations**

1. Supprimez le groupe de l’affectation. Cela désinstalle le package *wdav.pkg.intunemac* et désinsère l’appareil macOS des solutions de conformité.
