---
title: Périphériques Windows 10 embarqués à l’aide d’un script local
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
description: Utilisez un script local pour déployer le package de configuration sur les appareils de sorte qu’ils soient intégrés au service.
ms.openlocfilehash: 74152f9488623d39e32ee4e47a452bd1daea28c7
ms.sourcegitcommit: 6647055154002c7d3b8f7ce25ad53c9636bc8066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "48769430"
---
# <a name="onboard-windows-10-devices-using-a-local-script"></a>Périphériques Windows 10 embarqués à l’aide d’un script local

**S’applique à :**

- [Microsoft 365 protection contre la perte de données (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)

Vous pouvez également intégrer manuellement des appareils individuels à la protection contre la perte de données de point de terminaison de Microsoft 365. Vous pouvez effectuer cette opération en premier lieu lors du test du service avant de vous valider sur l’intégration de tous les périphériques de votre réseau.

> [!IMPORTANT]
> Ce script a été optimisé pour une utilisation sur un maximum de 10 appareils.
>
> Pour déployer à l’envergure, utilisez d' [autres options de déploiement](dlp-configure-endpoints.md). Par exemple, vous pouvez déployer un script d’intégration sur plus de 10 appareils en production avec le script disponible dans les [appareils Windows 10 embarqués à l’aide](dlp-configure-endpoints-gp.md)de la stratégie de groupe.

## <a name="onboard-devices"></a>Périphériques intégrés
 
1.  Ouvrez le fichier Package. zip de la configuration GP ( *DeviceComplianceOnboardingPackage.zip* ) que vous avez téléchargé à partir de l’Assistant d’intégration de service. Vous pouvez également obtenir le package à partir du [Centre de conformité Microsoft](https://compliance.microsoft.com)

2. Dans le volet de navigation, sélectionnez **paramètres** d’intégration de l'  >  **appareil** .

3. Dans le champ **méthode de déploiement** , sélectionnez **script local** .

4. Cliquez sur **Télécharger le package** et enregistrez le fichier. zip.
  
5. Extrayez le contenu du package de configuration vers un emplacement de l’appareil que vous souhaitez intégrer (par exemple, le bureau). Vous devez avoir un fichier nommé *DeviceOnboardingScript. cmd* .

6.  Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil et exécutez le script :

7.  Accédez à **Démarrer** , puis tapez **cmd** .

8.  Cliquez avec le bouton droit sur **invite de commandes** et sélectionnez **exécuter en tant qu’administrateur** .

![Menu Démarrer de la fenêtre pointant sur Exécuter en tant qu’administrateur](../media/dlp-run-as-admin.png)

9.  Tapez l’emplacement du fichier de script. Si vous avez copié le fichier sur le bureau, tapez : *%UserProfile%\Desktop\WindowsDefenderATPOnboardingScript.cmd*

10.  Appuyez sur la touche **entrée** ou cliquez sur **OK** .

Pour plus d’informations sur la façon dont vous pouvez valider manuellement le fait que l’appareil soit conforme et signale correctement les données de capteur, reportez-vous à la rubrique [Troubleshoot Microsoft Defender Advanced Threat Protection Onboard Problems](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

## <a name="offboard-devices-using-a-local-script"></a>Appareils débarquement à l’aide d’un script local
Pour des raisons de sécurité, le package utilisé pour les appareils débarquement expire 30 jours après la date de téléchargement. Les packages par débarquement expirés envoyés à un périphérique seront rejetés. Lors du téléchargement d’un package par débarquement, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et de par débarquement ne doivent pas être déployées sur le même appareil simultanément, sinon cette opération entraîne des collisions imprévisibles.

1. Obtenir le package par débarquement à partir du [Centre de conformité Microsoft](https://compliance.microsoft.com)

2. Dans le volet de navigation, sélectionnez **paramètres** du  >  **périphérique par débarquement** .

3. Dans le champ **méthode de déploiement** , sélectionnez **script local** .

4. Cliquez sur **Télécharger le package** et enregistrez le fichier. zip.

5. Extrayez le contenu du fichier. zip vers un emplacement partagé, en lecture seule, accessible aux appareils. Vous devez avoir un fichier nommé *DeviceComplianceOffboardingScript_valid_until_YYYY-mm-dd. cmd* .

6.  Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil et exécutez le script :

7.  Accédez à **Démarrer** , puis tapez **cmd** .

8.  Cliquez avec le bouton droit sur **invite de commandes** et sélectionnez **exécuter en tant qu’administrateur** .

![Menu Démarrer de la fenêtre pointant sur Exécuter en tant qu’administrateur](../media/dlp-run-as-admin.png)

9.  Tapez l’emplacement du fichier de script. Si vous avez copié le fichier sur le bureau, tapez la commande suivante : *%userprofile%\desktop\ WindowsDefenderATPOffboardingScript_valid_until_YYYY-mm-dd. cmd*

10.  Appuyez sur la touche **entrée** ou cliquez sur **OK** .

> [!IMPORTANT]
> Par débarquement entraîne l’arrêt de l’envoi des données de capteur au portail.


## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil
Vous pouvez suivre les différentes étapes de vérification décrites dans la procédure [résolution des problèmes liés à l’intégration] (( https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding) pour vérifier que le script s’est exécuté correctement et que l’agent est en cours d’exécution.

La surveillance peut également être réalisée directement sur le portail ou à l’aide des différents outils de déploiement.

### <a name="monitor-devices-using-the-portal"></a>Surveiller des périphériques à l’aide du portail
1. Accédez au [Centre de conformité Microsoft 365](https://compliance.microsoft.com).

2. Choisissez **paramètres** d’intégration de l'  >  **appareil**  >  **Devices** .

3. Vérifiez que les appareils apparaissent.


## <a name="related-topics"></a>Voir aussi
- [Périphériques Windows 10 embarqués à l’aide de la stratégie de groupe](dlp-configure-endpoints-gp.md)
- [Appareils intégrés Windows 10 à l’aide du gestionnaire de configuration de point de terminaison Microsoft](dlp-configure-endpoints-sccm.md)
- [Périphériques Windows 10 intégrés à l’aide des outils de gestion des appareils mobiles](dlp-configure-endpoints-mdm.md)
- [Périphériques VDI (Virtual Desktop Infrastructure) non persistants](dlp-configure-endpoints-vdi.md)
- [Exécution d’un test de détection sur un appareil Microsoft Defender nouvellement intégré](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Résoudre les problèmes d’intégration de la protection avancée contre les menaces Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
