---
title: Intégrer les appareils Windows 10 et Windows 11 en utilisant un script local
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
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Utilisez un script local pour déployer le package de configuration sur les appareils afin qu’ils soient intégrés au service.
ms.openlocfilehash: 840573794b447162f917fed162bb1f869585286e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634420"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-a-local-script"></a>Intégrer les appareils Windows 10 et Windows 11 en utilisant un script local

**S’applique à :**

- [Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md)

Vous pouvez également intégrer manuellement des appareils individuels à Microsoft 365. Vous souhaiterez peut-être effectuer cette opération en premier lors du test du service avant de vous engager à intégrer tous les appareils de votre réseau.

> [!IMPORTANT]
> Ce script a été optimisé pour une utilisation sur jusqu’à 10 appareils.
>
> Pour déployer à grande échelle, utilisez [d’autres options de déploiement](device-onboarding-overview.md). Par exemple, vous pouvez déployer un script d’intégration sur plus de 10 appareils en production avec le script disponible dans [Intégrer des appareils Windows 10 à l’aide de stratégie de groupe](device-onboarding-gp.md).

## <a name="onboard-devices"></a>Intégration des appareils
 
1. Obtenir le package de configuration .zip fichier (*DeviceComplianceOnboardingPackage.zip*) à partir de [portail de conformité Microsoft Purview](https://compliance.microsoft.com)

2. Dans le volet de navigation, sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Paramètres**</a> > **d’intégration de l’appareil**.

3. Dans le champ **Méthode de déploiement** , sélectionnez **Script local**.

4. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.
  
5. Extrayez le contenu du package de configuration à un emplacement sur l’appareil que vous souhaitez intégrer (par exemple, le Bureau). Vous devez avoir un fichier nommé *DeviceOnboardingScript.cmd*.

6. Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil et exécutez le script :

7. Accéder à **Démarrer** et taper **cmd**.

8. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

    ![Menu Démarrer de la fenêtre pointant vers Exécuter en tant qu’administrateur.](../media/dlp-run-as-admin.png)

9. Tapez l’emplacement du fichier de script. Si vous avez copié le fichier sur le bureau, *tapez : %userprofile%\Desktop\WindowsDefenderATPOnboardingScript.cmd*

10. Appuyez sur la touche **Entrée** ou cliquez sur **OK**.

Pour plus d’informations sur la façon dont vous pouvez vérifier manuellement que l’appareil est conforme et signale correctement les données de capteur, consultez [Résolution des problèmes d’intégration de Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

## <a name="offboard-devices-using-a-local-script"></a>Désintégrage des appareils à l’aide d’un script local

Pour des raisons de sécurité, le package utilisé pour désintégrez les appareils expirera 30 jours après la date de téléchargement. Les packages de désintégrage expirés envoyés à un appareil seront rejetés. Lors du téléchargement d’un package de désintégrage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et de désintégrage ne doivent pas être déployées simultanément sur le même appareil, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package de désintégrage à partir de <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>.

2. Dans le volet de navigation, sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Paramètres**</a> > **de désintégrage de l’appareil**.

3. Dans le champ **Méthode de déploiement** , sélectionnez **Script local**.

4. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.

5. Extrayez le contenu du fichier .zip à un emplacement partagé en lecture seule accessible par les appareils. Vous devez disposer d’un fichier nommé *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil et exécutez le script :

7. Accéder à **Démarrer** et taper **cmd**.

8. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

    ![Menu Démarrer de la fenêtre pointant vers Exécuter en tant qu’administrateur.](../media/dlp-run-as-admin.png)

9. Tapez l’emplacement du fichier de script. Si vous avez copié le fichier sur le bureau, tapez : *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

10. Appuyez sur la touche **Entrée** ou cliquez sur **OK**.

> [!IMPORTANT]
> Le désintégrage entraîne l’arrêt de l’envoi de données de capteur au portail par l’appareil.

## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil

Vous pouvez suivre les différentes étapes de vérification décrites dans [Résoudre les problèmes d’intégration]((/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding) pour vérifier que le script s’est correctement terminé et que l’agent est en cours d’exécution.

La surveillance peut également être effectuée directement sur le portail ou à l’aide des différents outils de déploiement.

### <a name="monitor-devices-using-the-portal"></a>Surveiller les appareils à l’aide du portail

1. Allez à [portail de conformité Microsoft Purview](https://compliance.microsoft.com).

2. Choisissez **Paramètres Appareils** > **d’intégration d’appareils** > .

1. Accédez à portail de conformité Microsoft Purview, puis sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Paramètres**</a> > **Appareils d’intégration d’appareil** > .

1. Vérifiez que les appareils apparaissent.

## <a name="related-topics"></a>Rubriques connexes
- [Intégrer des appareils Windows 10 et Windows 11 à l’aide de stratégie de groupe](device-onboarding-gp.md)
- [Intégrer des appareils Windows 10 et Windows 11 à l’aide de Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Intégrer les appareils Windows 10 et Windows 11 à l’aide des outils de gestion des périphériques mobiles](device-onboarding-mdm.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](device-onboarding-vdi.md)
- [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Résoudre les problèmes d’intégration de Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
