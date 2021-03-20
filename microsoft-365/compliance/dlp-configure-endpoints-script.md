---
title: Intégrer les appareils Windows 10 utilisant un script local
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
description: Utilisez un script local pour déployer le package de configuration sur les appareils afin qu’ils soient intégrés au service.
ms.openlocfilehash: 69a8295b170f9186d14862a7247cac3fb4c4ef3d
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50917970"
---
# <a name="onboard-windows-10-devices-using-a-local-script"></a>Intégrer les appareils Windows 10 utilisant un script local

**S’applique à :**

- [Protection contre la perte de données de point de terminaison Microsoft 365 (DLP)](./endpoint-dlp-learn-about.md)

Vous pouvez également intégrer manuellement des appareils individuels à la protection contre la perte de données des points de terminaison Microsoft 365. Vous pouvez d’abord le faire lors du test du service avant de vous engager à intégrer tous les appareils de votre réseau.

> [!IMPORTANT]
> Ce script a été optimisé pour une utilisation sur jusqu’à 10 appareils.
>
> Pour déployer à grande échelle, utilisez [d’autres options de déploiement.](dlp-configure-endpoints.md) Par exemple, vous pouvez déployer un script d’intégration sur plus de 10 appareils en production avec le script disponible sur les appareils [Windows 10](dlp-configure-endpoints-gp.md)intégrés à l’aide de la stratégie de groupe.

## <a name="onboard-devices"></a>Appareils intégrés
 
1.  Ouvrez le fichier .zip du package de configuration *gp (DeviceComplianceOnboardingPackage.zip)* que vous avez téléchargé à partir de l’Assistant d’intégration de service. Vous pouvez également obtenir le package à partir du [Centre de conformité Microsoft](https://compliance.microsoft.com)

2. Dans le volet de navigation, sélectionnez **Intégration de l’appareil**  >  **Paramètres.**

3. Dans le **champ Méthode de** déploiement, sélectionnez Script **local.**

4. Cliquez **sur Télécharger le package** et enregistrez le fichier .zip.
  
5. Extrayez le contenu du package de configuration vers un emplacement sur l’appareil que vous souhaitez intégrer (par exemple, le Bureau). Vous devez avoir un fichier nommé *DeviceOnboardingScript.cmd*.

6.  Ouvrez une invite de ligne de commande avec élévation de niveaux sur l’appareil et exécutez le script :

7.  Accéder à **Démarrer** et taper **cmd**.

8.  Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

![Menu Démarrer de la fenêtre pointant sur Exécuter en tant qu’administrateur](../media/dlp-run-as-admin.png)

9.  Tapez l’emplacement du fichier de script. Si vous avez copié le fichier sur le Bureau, tapez : *%userprofile%\Desktop\WindowsDefenderATPOnboardingScript.cmd*

10.  Appuyez sur **entrée** ou cliquez sur **OK.**

Pour plus d’informations sur la façon dont vous pouvez vérifier manuellement que l’appareil est conforme et signale correctement les données du capteur, consultez La procédure de résolution des problèmes d’intégration de la Protection avancée contre les [menaces Microsoft Defender.](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)

## <a name="offboard-devices-using-a-local-script"></a>Hors-carte des appareils à l’aide d’un script local
Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages de offboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et deboarding ne doivent pas être déployées sur le même appareil en même temps, sinon cela provoquera des collisions imprévisibles.

1. Obtenir le package deboarding à partir du [Centre de conformité Microsoft](https://compliance.microsoft.com)

2. Dans le volet de navigation, sélectionnez **Paramètres** De  >  **l’appareil horsboard.**

3. Dans le **champ Méthode de** déploiement, sélectionnez Script **local.**

4. Cliquez **sur Télécharger le package** et enregistrez le fichier .zip.

5. Extrayez le contenu du fichier .zip dans un emplacement partagé en lecture seule accessible par les appareils. Vous devez avoir un fichier nommé *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6.  Ouvrez une invite de ligne de commande avec élévation de niveaux sur l’appareil et exécutez le script :

7.  Accéder à **Démarrer** et taper **cmd**.

8.  Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

![Menu Démarrer de la fenêtre pointant sur Exécuter en tant qu’administrateur](../media/dlp-run-as-admin.png)

9.  Tapez l’emplacement du fichier de script. Si vous avez copié le fichier sur le Bureau, tapez : *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

10.  Appuyez sur **entrée** ou cliquez sur **OK.**

> [!IMPORTANT]
> Le fait d’arrêter l’envoi de données de capteur au portail par le fait que l’appareil n’est plus à l’origine de laboardage.


## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil
Vous pouvez suivre les différentes étapes de vérification dans [Résoudre les problèmes d’intégration](( pour vérifier que le script s’est correctement terminé et que https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding) l’agent est en cours d’exécution.

La surveillance peut également être effectuée directement sur le portail ou à l’aide des différents outils de déploiement.

### <a name="monitor-devices-using-the-portal"></a>Surveiller les appareils à l’aide du portail
1. Go to [Microsoft 365 Compliance center](https://compliance.microsoft.com).

2. Choose **Settings**  >  **Device onboarding**  >  **Devices**.

3. Vérifiez que les appareils apparaissent.


## <a name="related-topics"></a>Rubriques connexes
- [Intégrer des appareils Windows 10 à l’aide de la stratégie de groupe](dlp-configure-endpoints-gp.md)
- [Intégrer des appareils Windows 10 à l’aide de Microsoft Endpoint Configuration Manager](dlp-configure-endpoints-sccm.md)
- [Intégrer les appareils Windows 10 à l’aide des outils de gestion des appareils mobiles](dlp-configure-endpoints-mdm.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.](dlp-configure-endpoints-vdi.md)
- [Exécuter un test de détection sur un appareil Microsoft Defender ATP nouvellement intégré](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Résoudre les problèmes d’intégration de la Protection avancée contre les menaces Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)