---
title: Périphériques Windows 10 embarqués via la stratégie de groupe
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Utilisez la stratégie de groupe pour déployer le package de configuration sur les appareils Windows 10 afin qu’ils soient intégrés au service.
ms.openlocfilehash: a9e91f41b6e86e9f75d79d420c0ee830f1e3acf3
ms.sourcegitcommit: 6647055154002c7d3b8f7ce25ad53c9636bc8066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "48769414"
---
# <a name="onboard-windows-10-devices-using-group-policy"></a>Périphériques Windows 10 embarqués à l’aide de la stratégie de groupe 

**S’applique à :**

- [Microsoft 365 protection contre la perte de données (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)
- Stratégie de groupe

> [!NOTE]
> Pour utiliser les mises à jour de la stratégie de groupe pour déployer le package, vous devez être sur Windows Server 2008 R2 ou une version ultérieure.

> Pour Windows Server 2019, il se peut que vous deviez remplacer NT AUTHORITY\Well-Known-System-Account par NT AUTHORITY\SYSTEM du fichier XML créé par la stratégie de groupe.

## <a name="onboard-devices-using-group-policy"></a>Périphériques intégrés à l’aide de la stratégie de groupe

1. Ouvrez le fichier Package. zip de la configuration GP ( *DeviceComplianceOnboardingPackage.zip* ) que vous avez téléchargé à partir de l’Assistant d’intégration de service. Vous pouvez également obtenir le package à partir du [Centre de conformité Microsoft](https://compliance.microsoft.com/compliancesettings/deviceonboarding)

2. Dans le volet de navigation, sélectionnez **paramètres** d’intégration de l'  >  **appareil** .

3. Dans le champ **méthode de déploiement** , sélectionnez stratégie de **groupe** .

4. Cliquez sur **Télécharger le package** et enregistrez le fichier. zip.

5. Extrayez le contenu du fichier. zip vers un emplacement partagé en lecture seule accessible par l’appareil. Vous devez avoir un dossier nommé *OptionalParamsPolicy* et le fichier *DeviceComplianceLocalOnboardingScript. cmd* .

6. Ouvrez la [console de gestion des stratégies de groupe](https://docs.microsoft.com/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), cliquez avec le bouton droit sur l’objet de stratégie de groupe (GPO) que vous souhaitez configurer, puis cliquez sur **modifier** .

7. Dans l' **éditeur de gestion des stratégies de groupe** , accédez à configuration de l’ordinateur, puis **Préférences** , puis **paramètres du panneau** de **configuration** .

8. Cliquez avec le bouton droit sur **tâches planifiées** , pointez sur **nouveau** , puis cliquez sur **tâche immédiate (au moins Windows 7)** .

9. Dans la fenêtre **tâche** qui s’ouvre, accédez à l’onglet **général** . Sous **options de sécurité** , cliquez sur **modifier l’utilisateur ou le groupe** et tapez le système, puis cliquez sur vérifier les **noms** , puis sur **OK** . NT AUTHORITY\SYSTEM apparaît en tant que compte d’utilisateur sous lequel la tâche s’exécutera.

10. Sélectionnez **exécuter si l’utilisateur est connecté ou non** et activez la case à cocher **exécuter avec les privilèges les plus élevés** .

11. Accédez à l’onglet **actions** , puis cliquez sur **nouveau...** Assurez-vous que l’option **Démarrer un programme** est sélectionnée dans le champ **action** . Entrez le nom de fichier et l’emplacement du fichier *WindowsDefenderATPOnboardingScript. cmd* partagé.

12. Cliquez sur **OK** et fermez toutes les fenêtres de la console GPMC ouvertes.


## <a name="offboard-devices-using-group-policy"></a>Appareils débarquement à l’aide de la stratégie de groupe
Pour des raisons de sécurité, le package utilisé pour les appareils débarquement expire 30 jours après la date de téléchargement. Les packages par débarquement expirés envoyés à un appareil seront rejetés. Lors du téléchargement d’un package par débarquement, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et de par débarquement ne doivent pas être déployées sur le même appareil simultanément, sinon cette opération entraîne des collisions imprévisibles.

1. Obtenir le package par débarquement à partir du [Centre de conformité Microsoft](https://compliance.microsoft.com/compliancesettings/deviceonboarding).

2. Dans le volet de navigation, sélectionnez **paramètres**  >  **//Device** de l’intégration de  >  **par débarquement** .

3. Dans le champ **méthode de déploiement** , sélectionnez stratégie de **groupe** .

4. Cliquez sur **Télécharger le package** et enregistrez le fichier. zip.

5. Extrayez le contenu du fichier. zip vers un emplacement partagé en lecture seule accessible par l’appareil. Vous devez avoir un fichier nommé *DeviceComplianceOffboardingScript_valid_until_YYYY-mm-dd. cmd* .

6. Ouvrez la [console de gestion des stratégies de groupe](https://docs.microsoft.com/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), cliquez avec le bouton droit sur l’objet de stratégie de groupe (GPO) que vous souhaitez configurer, puis cliquez sur **modifier** .

7. Dans l' **éditeur de gestion des stratégies de groupe** , accédez à configuration de l' **ordinateur,** puis **Préférences** , puis **paramètres du panneau** de configuration.

8. Cliquez avec le bouton droit sur **tâches planifiées** , pointez sur **nouveau** , puis cliquez sur **tâche immédiate** .

9. Dans la fenêtre **tâche** qui s’ouvre, accédez à l’onglet **général** . Sélectionnez le compte d’utilisateur du système local (BUILTIN\SYSTEM) sous **options de sécurité** .

10. Sélectionnez **exécuter si l’utilisateur est connecté ou non** et activez la case à cocher **exécuter avec les privilèges les plus élevés** .

11. Accédez à l’onglet **actions** , puis cliquez sur **nouveau.** ... Assurez-vous que l’option **Démarrer un programme** est sélectionnée dans le champ **action** . Entrez le nom de fichier et l’emplacement du fichier partagé  *DeviceComplianceOffboardingScript_valid_until_YYYY-mm-dd. cmd* partagé.

12. Cliquez sur **OK** et fermez toutes les fenêtres de la console GPMC ouvertes.

> [!IMPORTANT]
> Par débarquement entraîne l’arrêt de l’appareil à envoyer les données de capteur au portail, mais les données de l’appareil.


## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil
La stratégie de groupe ne permet pas de surveiller le déploiement des stratégies sur les appareils. La surveillance peut être réalisée directement sur le portail ou à l’aide des différents outils de déploiement.

## <a name="monitor-devices-using-the-portal"></a>Surveiller des périphériques à l’aide du portail
1. Accédez au [Centre de conformité Microsoft](https://compliance.microsoft.com/).
2. Cliquez sur liste des **appareils** .
3. Vérifiez que les appareils apparaissent.

> [!NOTE]
> Le démarrage de l’affichage sur la **liste des appareils** peut prendre plusieurs jours. Cela inclut le temps nécessaire à la distribution des stratégies sur l’appareil, le temps nécessaire avant l’ouverture de session de l’utilisateur et le temps nécessaire pour que le point de terminaison commence à créer des rapports.


## <a name="related-topics"></a>Voir aussi
- [Appareils intégrés Windows 10 à l’aide du gestionnaire de configuration de point de terminaison Microsoft](dlp-configure-endpoints-sccm.md)
- [Périphériques Windows 10 intégrés à l’aide des outils de gestion des appareils mobiles](dlp-configure-endpoints-mdm.md)
- [Périphériques Windows 10 embarqués à l’aide d’un script local](dlp-configure-endpoints-script.md)
- [Périphériques VDI (Virtual Desktop Infrastructure) non persistants](dlp-configure-endpoints-vdi.md)
- [Exécuter un test de détection sur un périphérique récemment ATP Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Résoudre les problèmes d’intégration de la protection avancée contre les menaces Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
