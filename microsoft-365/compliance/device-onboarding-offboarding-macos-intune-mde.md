---
title: Intégrer et mettre hors service des appareils macOS dans des solutions de conformité à l’aide Microsoft Intune microsoft Defender pour les clients endpoint (prévisualisation)
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
description: Découvrez comment intégrer et mettre hors service des appareils macOS dans Microsoft 365 solutions de conformité à l’aide Microsoft Intune pour les clients MDE (prévisualisation)
ms.openlocfilehash: a1d647fae55b091b8c12df885ce28aa4f1275a1a
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2021
ms.locfileid: "60962998"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers-preview"></a>Intégration et retrait des appareils macOS dans les solutions de conformité à l'aide d'Intune pour les clients de Microsoft Defender pour point de terminaison (aperçu)

> [!IMPORTANT]
> Utilisez cette procédure ***si vous avez*** déployé Microsoft Defender pour le point de terminaison (MDE) sur vos appareils macOS

<!--## Get registered

To get access to this feature, you must register your tenant with Microsoft. See, [get registered for Microsoft 365 macOS support](https://aka.ms/EndpointDLPIgnite21-Previews).-->

**S’applique à :**

- Clients qui ont déployé MDE sur leurs appareils macOS.
- [Protection contre la perte de données de point de terminaison (DLP) pour Microsoft 365](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)


## <a name="before-you-begin"></a>Avant de commencer

- Assurez-vous que vos appareils macOS sont [intégrés à Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) et inscrits dans [l’application Portail d'entreprise.](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp) 
- Assurez-vous que vous avez accès au [centre Microsoft Endpoint Manager de données](https://endpoint.microsoft.com/#home)
- Cela prend en charge la version macOS De qua l ment 10.15 et les versions supérieures
- Installer le navigateur Edge v95+ sur vos appareils macOS 

## <a name="onboard-macos-devices-into-microsoft-365-compliance-solutions-using-microsoft-intune"></a>Intégrer des appareils macOS dans des solutions Microsoft 365 conformité à l’aide Microsoft Intune

Utilisez ces étapes pour intégrer un appareil macOS aux solutions de conformité si MDE lui est déjà déployé.

1. Vous aurez besoin de ces fichiers pour cette procédure.

|fichier nécessaire pour |source |
|---------|---------|
|accessibilité |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
accès disque complet     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|

> [!TIP]
> Vous pouvez télécharger les fichiers *.mobileconfig* individuellement ou dans un seul fichier [combiné qui](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) contient :
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> 
>
>Si l’un de ces fichiers individuels est mis à jour, vous devez télécharger à nouveau le fichier combiné ou le fichier unique mis à jour individuellement.

### <a name="create-system-configuration-profiles"></a>Créer des profils de configuration système

1. Ouvrez le **centre Microsoft Endpoint Manager**  >  **profils de**  >  **configuration des appareils.**

1. Choose: **Create profile**. 

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

1. Ouvrez **les**  >  **profils de configuration des** appareils , vous devriez voir vos profils créés ici.

1. Dans la page **Profils** de configuration, choisissez le profil que vous  avez créé, dans cet exemple *AccessibilityformacOS,* puis choisissez État de l’appareil pour voir la liste des appareils et l’état de déploiement du profil de configuration.

### <a name="update-configuration-profiles"></a>Mettre à jour les profils de configuration

1. Mettez à jour le profil d’accès disque complet existant avec le **fichier fulldisk.mobileconfig.**

1. Mettre à jour le profil de préférences MDE avec ces valeurs
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```

## <a name="offboard-macos-devices-using-intune"></a>Offboard macOS devices using Intune

> [!IMPORTANT]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois.

1. Dans **Microsoft Endpoint Manager, ouvrez** **les** profils de configuration des appareils, vous devez y voir vos  >  profils créés.

2. Dans la page **Profils de** configuration, choisissez le profil de préférences MDE.

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
3. **Enregistrer**.