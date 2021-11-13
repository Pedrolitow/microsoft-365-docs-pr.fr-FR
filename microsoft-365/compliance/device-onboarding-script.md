---
title: Intégrer Windows 10 et Windows 11 à l’aide d’un script local
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
ms.openlocfilehash: 14412e782cffd597786a4d2c322fe2b8fc20e5ca
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2021
ms.locfileid: "60950889"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-a-local-script"></a>Intégrer Windows 10 et Windows 11 à l’aide d’un script local

**S’applique à :**

- [Microsoft 365 protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

Vous pouvez également intégrer manuellement des appareils individuels à Microsoft 365. Vous pouvez d’abord le faire lors du test du service avant de vous engager à intégrer tous les appareils de votre réseau.

> [!IMPORTANT]
> Ce script a été optimisé pour une utilisation sur jusqu’à 10 appareils.
>
> Pour déployer à grande échelle, utilisez [d’autres options de déploiement.](device-onboarding-overview.md) Par exemple, vous pouvez déployer un script d’intégration sur plus de 10 appareils en production avec le script disponible dans les appareils Windows 10 intégrés à l’aide de la stratégie [de groupe.](device-onboarding-gp.md)

## <a name="onboard-devices"></a>Intégration des appareils
 
1. Obtenir le package de configuration .zip fichier (*DeviceComplianceOnboardingPackage.zip*) à partir du [Centre de conformité Microsoft](https://compliance.microsoft.com)

2. Dans le volet de <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank"></a>navigation, sélectionnez  >  **Paramètres’intégration de l’appareil.**

3. Dans le **champ Méthode de** déploiement, sélectionnez Script **local.**

4. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.
  
5. Extrayez le contenu du package de configuration vers un emplacement sur l’appareil que vous souhaitez intégrer (par exemple, le Bureau). Vous devez avoir un fichier nommé *DeviceOnboardingScript.cmd*.

6. Ouvrez une invite de ligne de commande avec élévation de niveaux sur l’appareil et exécutez le script :

7. Accéder à **Démarrer** et taper **cmd**.

8. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

    ![Fenêtre menu Démarrer pointant sur Exécuter en tant qu’administrateur.](../media/dlp-run-as-admin.png)

9. Tapez l’emplacement du fichier de script. Si vous avez copié le fichier sur le Bureau, tapez : *%userprofile%\Desktop\WindowsDefenderATPOnboardingScript.cmd*

10. Appuyez sur **entrée** ou cliquez sur **OK.**

Pour plus d’informations sur la façon dont vous pouvez vérifier manuellement que l’appareil est conforme et signale correctement les données du capteur, consultez La procédure de résolution des problèmes d’intégration de la Protection avancée contre les [menaces Microsoft Defender.](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)

## <a name="offboard-devices-using-a-local-script"></a>Hors-carte des appareils à l’aide d’un script local

Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages de offboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et deboarding ne doivent pas être déployées sur le même appareil en même temps, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package deboarding à partir <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">de Centre de conformité Microsoft 365</a>.

2. Dans le volet de navigation, sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Paramètres**</a>  >  **de l’appareil.**

3. Dans le **champ Méthode de** déploiement, sélectionnez Script **local.**

4. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

5. Extrayez le contenu du .zip vers un emplacement partagé en lecture seule accessible par les appareils. Vous devez avoir un fichier nommé *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Ouvrez une invite de ligne de commande avec élévation de niveaux sur l’appareil et exécutez le script :

7. Accéder à **Démarrer** et taper **cmd**.

8. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

    ![Fenêtre menu Démarrer pointant sur Exécuter en tant qu’administrateur.](../media/dlp-run-as-admin.png)

9. Tapez l’emplacement du fichier de script. Si vous avez copié le fichier sur le Bureau, tapez : *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

10. Appuyez sur **entrée** ou cliquez sur **OK.**

> [!IMPORTANT]
> Le fait d’arrêter l’envoi de données de capteur au portail par le fait que l’appareil n’est plus à l’origine de laboardage.

## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil

Vous pouvez suivre les différentes étapes de vérification dans [Résoudre les problèmes d’intégration]((/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding) pour vérifier que le script s’est correctement terminé et que l’agent est en cours d’exécution.

La surveillance peut également être effectuée directement sur le portail ou à l’aide des différents outils de déploiement.

### <a name="monitor-devices-using-the-portal"></a>Surveiller les appareils à l’aide du portail

1. Go to [Microsoft 365 Compliance center](https://compliance.microsoft.com).

2. Choose **Paramètres**  >  **Device onboarding**  >  **Devices**.

1. Go to Centre de conformité Microsoft 365, and select <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Paramètres**</a>  >  **Device onboarding**  >  **Devices**.

1. Vérifiez que les appareils apparaissent.

## <a name="related-topics"></a>Voir aussi
- [Intégrer des Windows 10 et Windows 11 à l’aide de la stratégie de groupe](device-onboarding-gp.md)
- [Intégrer des Windows 10 et des Windows 11 à l’aide Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Intégrer des Windows 10 et Windows 11 à l’aide des outils de gestion des périphériques mobiles](device-onboarding-mdm.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](device-onboarding-vdi.md)
- [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Résoudre les problèmes d’intégration de la Protection avancée contre les menaces Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)