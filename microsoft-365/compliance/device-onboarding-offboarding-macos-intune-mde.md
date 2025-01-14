---
title: Intégrer et déconnecter des appareils macOS dans des solutions de conformité à l’aide de Microsoft Intune pour les clients Microsoft Defender pour point de terminaison
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
- tier1
- purview-compliance
search.appverid:
- MET150
description: Découvrez comment intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de Microsoft Intune pour les clients MDE
ms.openlocfilehash: 7638653c7794270b37c3925f17a64949f1fcae75
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68632269"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers"></a>Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide d'Intune pour les clients de Microsoft Defender pour point de terminaison

> [!IMPORTANT]
> Utilisez cette procédure ***si vous avez*** déployé Microsoft Defender pour point de terminaison (MDE) sur vos appareils macOS

**S’applique à :**

- Les clients qui ont déployé MDE sur leurs appareils macOS.
- [Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md)


[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="before-you-begin"></a>Avant de commencer

- Assurez-vous que vos [appareils macOS sont intégrés à Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) et inscrits dans l’application [Portail d'entreprise](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Assurez-vous d’avoir accès au [Centre microsoft Endpoint Manager](https://endpoint.microsoft.com/#home)
- Cela prend en charge les trois dernières versions de macOS publiées.
- Installer le navigateur v95+ Edge sur vos appareils macOS 

## <a name="onboard-macos-devices-into-microsoft-purview-solutions-using-microsoft-intune"></a>Intégrer des appareils macOS dans des solutions Microsoft Purview à l’aide de Microsoft Intune

Suivez ces étapes pour intégrer un appareil macOS dans les solutions de conformité s’il dispose déjà de MDE déployé sur celui-ci.

1. Vous aurez besoin de ces fichiers pour cette procédure.

|fichier nécessaire pour |source |
|---------|---------|
|Accessibilité |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
accès au disque complet     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|

> [!TIP]
> Vous pouvez télécharger les fichiers *.mobileconfig* individuellement ou dans un [seul fichier combiné](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) contenant :
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> 
>
>Si l’un de ces fichiers individuels est mis à jour, vous devez télécharger à nouveau le fichier combiné ou le fichier unique mis à jour individuellement.

### <a name="create-system-configuration-profiles"></a>Créer des profils de configuration système

1. Ouvrez les **profils de configuration** **des appareils** >  **du centre** >  de Endpoint Manager Microsoft.

1. Choisissez : **Créer un profil**. 

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

1. Ouvrez les **profils de configuration** **des appareils** > . Vous devriez y voir vos profils créés.

1. Dans la page **Profils de configuration**, choisissez le profil que vous venez de créer, dans cet exemple *AccessibilityformacOS*, puis choisissez État de l’appareil pour afficher la liste des appareils et l’état de déploiement du profil de configuration.

### <a name="update-existing-system-configuration-profiles"></a>Mettre à jour les profils de configuration système existants


1. Un profil de configuration d’accès au disque complet doit avoir été précédemment créé et déployé pour MDE.  Consultez [Intune déploiement basé sur Microsoft Defender pour point de terminaison sur Mac](/microsoft-365/security/defender-endpoint/mac-install-with-intune#full-disk-access). La protection contre la perte de données du point de terminaison nécessite une autorisation d’accès au disque complet supplémentaire pour une nouvelle application : `com.microsoft.dlp.daemon`. 
    1. Mettez à jour le profil de configuration Fullfull Disk Access existant avec le fichier fulldisk.mobileconfig. 


1. Recherchez le profil de configuration des préférences MDE existant. Voir, [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](/microsoft-365/security/defender-endpoint/mac-preferences#intune-full-profile)
    1. Ajoutez une nouvelle clé au profil à l’aide des valeurs suivantes :

```xml
<key>features</key> 
<dict> 
    <key>systemExtensions</key> 
    <string>enabled</string> 
    <key>dataLossPrevention</key> 
    <string>enabled</string> 
</dict> 
``` 

Voici un [exemple de mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig)
 
## <a name="offboard-macos-devices-using-intune"></a>Désins border des appareils macOS à l’aide de Intune

> [!IMPORTANT]
> La désintégération entraîne l’arrêt de l’envoi de données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois maximum.

1. Dans **le centre Microsoft Endpoint Manager**, ouvrez les **profils de configuration** **des appareils** > . Vous devez y voir vos profils créés.

2. Dans la page **Profils de configuration** , choisissez le profil de préférences MDE.

1. Supprimez ces paramètres :
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```
3. **Enregistrez**.
