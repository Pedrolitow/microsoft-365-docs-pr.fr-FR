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
ms.openlocfilehash: f71cc8f5ef0a0d9a251dca0b8da5e7797f553e0f
ms.sourcegitcommit: ab32c6e19af08837aaa84a058653c3a209d366ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2022
ms.locfileid: "67444960"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-purview-solutions-using-intune"></a>Intégrer et déconnecter des appareils macOS dans les solutions Microsoft Purview à l’aide d’Intune

Vous pouvez utiliser Intune pour intégrer des appareils macOS dans des solutions Microsoft Purview.

> [!IMPORTANT]
> Utilisez cette procédure si vous ***n’avez pas*** déployé Microsoft Defender pour point de terminaison (MDE) sur vos appareils macOS

**S’applique à :**

- [Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md)

## <a name="before-you-begin"></a>Avant de commencer

- Assurez-vous que vos [appareils macOS sont intégrés à Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) et inscrits dans l’application [Portail d'entreprise](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Assurez-vous d’avoir accès au [Centre microsoft Endpoint Manager](https://endpoint.microsoft.com/#home).
- Cela prend en charge trois versions majeures les plus récentes de macOS.
- Créez les groupes d’utilisateurs auxquels vous allez affecter les mises à jour de configuration.
- Installer le navigateur v95+ Edge sur vos appareils macOS 


## <a name="onboard-macos-devices-into-microsoft-purview-solutions-using-microsoft-intune"></a>Intégrer des appareils macOS dans des solutions Microsoft Purview à l’aide de Microsoft Intune

L’intégration d’un appareil macOS dans les solutions de conformité est un processus en plusieurs phases.

1. [Créer des profils de configuration système](#create-system-configuration-profiles)
1. [Obtenir le package d’intégration d’appareil](#get-the-device-onboarding-package)
1. [Déployer les packages mobileconfig et d’intégration](#deploy-the-mobileconfig-and-onboarding-packages)
1. [Publier l'application](#publish-application)
<!--1. [Enable system extension](#enable-system-extension)-->


### <a name="create-system-configuration-profiles"></a>Créer des profils de configuration système

1. Vous aurez besoin de ces fichiers pour cette procédure. 

|fichier nécessaire pour |source |
|---------|---------|
Fichier de configuration mobile système | [mdatp-nokext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) Copiez et collez le contenu dans un fichier texte. Enregistrez le fichier avec l’extension **mobileconfig** uniquement. Il ne sera pas reconnu s’il a l’extension .txt.|
Préférences MDE| [com.microsoft.wdav.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig). Copiez et collez le contenu dans un fichier texte. Enregistrez le fichier avec l’extension **mobileconfig** uniquement. Il ne sera pas reconnu s’il a l’extension .txt.

### <a name="get-the-device-onboarding-package"></a>Obtenir le package d’intégration d’appareil

1. Dans le **Centre de conformité Microsoft Purview** , **ouvrez Paramètres** > **de l’intégration des appareils** et choisissez **Intégration**.
 
1. Pour **sélectionner le système d’exploitation à démarrer le processus d’intégration** , choisissez **macOS**.
 
1. Pour **la méthode Deployment,** choisissez **Mobile Gestion des appareils/Microsoft Intune**.
 
1. Choisissez **Télécharger le package d’intégration**. 

1. Extrayez le fichier zip et ouvrez le dossier *Intune*. Il contient le code d’intégration dans le fichier *DeviceComplianceOnboarding.xml* .

<!--|accessibility |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
full disk access     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Network filer| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)]
|System extensions |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|MDE preference     |[com.microsoft.wdav.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig)|
|MAU preference|[com.microsoft.autoupdate2.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.mobileconfig)|
|Installation package     |downloaded from the compliance portal **Installation package**, file name *\*wdav.pkg*\* |

> [!TIP]
> You can download the *.mobileconfig* files individually or in [single combined file](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) that contains:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - system extensions
>
>If any of these individual files is updated, you'd need to download the either the combined file again or the single updated file individually.-->

### <a name="deploy-the-mobileconfig-and-onboarding-packages"></a>Déployer les packages mobileconfig et d’intégration

1. Ouvrez les **profils de configuration** **des appareils** >  **du centre** >  de Endpoint Manager Microsoft.

1. Choisir : **Créer un profil** 

1. Choisir:
    1. **Platform = macOS**
    1. **Type de profil = Modèles**
    1. **Nom du modèle = Personnalisé**

1. Choisir **Créer**

1. Choisissez un nom pour le profil, comme *SystemMobileConfig* dans cet exemple. Cliquez sur **Suivant**.

1. Choisissez le fichier **mdatp-nokext.mobileconfig** que vous avez copié et enregistré à l’étape 1 comme fichier de profil de configuration.

1. Sélectionnez **Suivant**

1. Sous l’onglet **Affectations** , ajoutez le groupe sur lequel vous souhaitez déployer ces configurations et choisissez **Suivant**.

1. Passez en revue vos paramètres et **choisissez Créer** pour déployer la configuration.

1. Répétez les étapes 2 à 9 pour créer des profils pour les éléments :
    1. **fichierDeviceComplianceOnboarding.xml** . Nommez-le *Purview Device Onboarding Package*
    1. **fichier com.microsoft.wdav.mobileconfig** . Nommez-le *Préférences d’appareil de point de terminaison*
 
1. Ouvrez les **profils de configuration** **des appareils** > . Vous devriez y voir vos profils créés.

1. Dans la page **Profils de configuration** , choisissez le profil que vous venez de créer, par exemple *SystemMobileConfig* , puis choisissez **l’état de l’appareil** pour afficher la liste des appareils et l’état de déploiement du profil de configuration.

### <a name="publish-application"></a>Publier l'application

Microsoft Endpoint DLP est installé en tant que composant de Microsoft Defender pour point de terminaison (MDE) sur macOS. Cette procédure s’applique à l’intégration d’appareils dans des solutions Microsoft Purview

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://endpoint.microsoft.com/), ouvrez **Applications**.

1. Sélectionnez By platform > macOS > Add.

1. Choisissez **le type d’application**=**macOS**, puis cliquez sur **Sélectionner**.

1. Conservez les valeurs par défaut, cliquez sur **Suivant**.

1. Ajoutez des affectations, cliquez sur **Suivant**.

1. Vérifier et **créer**.

1. Vous pouvez visiter La **plateforme** \> **Apps** \> By **macOS** pour la voir dans la liste de toutes les applications.

<!--## Offboard macOS devices using Intune PINGING PG FOR THIS PROCEDURE

> [!NOTE]
> Offboarding causes the device to stop sending sensor data to the portal but data from the device, including reference to any alerts it has had will be retained for up to six months.

1. In **Microsoft Endpoint Manager center**, open **Devices** > **Configuration profiles**, you should see your created profiles there.

1. In the **Configuration profiles** page, choose the *wdav.pkg.intunemac* profile.

1. Choose **Device status** to see a list of devices and the deployment status of the configuration profile

1. Open **Properties** and **Assignments**

1. Remove the group from the assignment. This will uninstall the *wdav.pkg.intunemac* package and offboard the macOS device from Compliance solutions.-->
