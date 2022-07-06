---
title: Intégrer les appareils Windows 10 et Windows 11 via une stratégie de groupe
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Utilisez stratégie de groupe pour déployer le package de configuration sur des appareils Windows 10 et Windows 11 afin qu’ils soient intégrés au service.
ms.openlocfilehash: 6c8c70d1bfdf3de0bc3848069a22b8610d445e42
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623250"
---
# <a name="onboard-windows-10-devices-and-windows-11-using-group-policy"></a>Intégrer des appareils et des Windows 11 Windows 10 à l’aide de stratégie de groupe 

**S’applique à :**

- [Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md)
- Stratégie de groupe

> [!NOTE]
> Pour utiliser les mises à jour stratégie de groupe (GP) pour déployer le package, vous devez être sur Windows Server 2008 R2 ou version ultérieure.

> Pour Windows Server 2019, vous devrez peut-être remplacer NT AUTHORITY\Well-Known-System-Account par NT AUTHORITY\SYSTEM du fichier XML créé par la préférence stratégie de groupe.

## <a name="onboard-devices-using-group-policy"></a>Intégrer des appareils à l’aide d’une stratégie de groupe

1. Ouvrez le [Centre de conformité](https://compliance.microsoft.com).

2. Dans le volet de navigation, sélectionnez **Paramètres** > **de l’intégration des appareils**.

3. Dans le champ **Méthode de déploiement** , sélectionnez **Stratégie de groupe**.

4. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.

5. Extrayez le contenu du fichier .zip à un emplacement partagé en lecture seule accessible par l’appareil. Vous devez disposer d’un dossier appelé *OptionalParamsPolicy* et du fichier *DeviceComplianceLocalOnboardingScript.cmd*.

6. Ouvrez la [console de gestion stratégie de groupe](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), cliquez avec le bouton droit sur l’objet stratégie de groupe (GPO) que vous souhaitez configurer, puis cliquez sur **Modifier**.

7. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **Configuration de l’ordinateur**, puis **Préférences**, puis **aux paramètres du Panneau de configuration**.

8. Cliquez avec le bouton droit sur **Tâches planifiées**, **pointez sur Nouveau**, puis cliquez sur **Tâche immédiate (Au moins Windows 7).**

9. Dans la fenêtre **Tâche** qui s’ouvre, accédez à l’onglet **Général** . Sous **Options de sécurité** , cliquez sur **Modifier l’utilisateur ou le groupe** et tapez SYSTEM, puis cliquez sur **Vérifier les noms** , puis **SUR OK**. NT AUTHORITY\SYSTEM apparaît sous la forme du compte d’utilisateur sous lequel la tâche s’exécutera.

10. Sélectionnez **Exécuter si l’utilisateur est connecté ou non** et cochez la case **Exécuter avec les privilèges les plus élevés** .

11. Accédez à l’onglet **Actions** , puis cliquez sur **Nouveau...** Vérifiez que **démarrer un programme** est sélectionné dans le champ **Action** . Entrez le nom et l’emplacement du fichier *WindowsDefenderATPOnboardingScript.cmd* partagé.

12. Cliquez sur **OK** et fermez toutes les fenêtres GPMC ouvertes.

## <a name="offboard-devices-using-group-policy"></a>Désintégrage des appareils à l’aide de stratégie de groupe
Pour des raisons de sécurité, le package utilisé pour déconnecter les appareils expirera 30 jours après la date de téléchargement. Les packages de désintégrage expirés envoyés à un appareil seront rejetés. Lors du téléchargement d’un package de désintégrage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et de désintégrage ne doivent pas être déployées simultanément sur le même appareil, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package de désintégrage à partir de [portail de conformité Microsoft Purview](https://compliance.microsoft.com/compliancesettings/deviceonboarding).

2. Dans le volet de navigation, sélectionnez **Paramètres** > **//Désintégrage de l’intégration de l’appareil** > .

3. Dans le champ **Méthode de déploiement** , sélectionnez **Stratégie de groupe**.

4. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.

5. Extrayez le contenu du fichier .zip à un emplacement partagé en lecture seule accessible par l’appareil. Vous devez disposer d’un fichier nommé *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Ouvrez la [console de gestion stratégie de groupe](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), cliquez avec le bouton droit sur l’objet stratégie de groupe (GPO) que vous souhaitez configurer, puis cliquez sur **Modifier**.

7. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **Configuration de l’ordinateur,** puis **Préférences**, puis **aux paramètres du Panneau de configuration**.

8. Cliquez avec le bouton droit sur **Tâches planifiées**, **pointez sur Nouveau**, puis cliquez sur **Tâche immédiate**.

9. Dans la fenêtre **Tâche** qui s’ouvre, accédez à l’onglet **Général** . Choisissez le compte d’utilisateur SYSTEM local (BUILTIN\SYSTEM) sous **Options de sécurité**.

10. Sélectionnez **Exécuter si l’utilisateur est connecté ou non** et cochez la case **Exécuter avec les privilèges les plus élevés** .

11. Accédez à l’onglet **Actions** , puis cliquez sur **Nouveau...**. Vérifiez que **démarrer un programme** est sélectionné dans le champ **Action** . Entrez le nom de fichier et l’emplacement du fichier  *partagé DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd* .

12. Cliquez sur **OK** et fermez toutes les fenêtres GPMC ouvertes.

> [!IMPORTANT]
> Le désintégrage entraîne l’arrêt de l’envoi de données de capteur au portail, mais à partir de l’appareil.


## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil
Avec stratégie de groupe il n’existe pas d’option permettant de surveiller le déploiement de stratégies sur les appareils. La surveillance peut être effectuée directement sur le portail ou à l’aide des différents outils de déploiement.

## <a name="monitor-devices-using-the-portal"></a>Surveiller les appareils à l’aide du portail
1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>.
2. Cliquez sur **La liste Des appareils** .
3. Vérifiez que les appareils apparaissent.

> [!NOTE]
> L’affichage des appareils dans la **liste Des** appareils peut prendre plusieurs jours. Cela inclut le temps nécessaire à la distribution des stratégies sur l’appareil, le temps nécessaire à l’ouverture de session de l’utilisateur et le temps nécessaire au point de terminaison pour démarrer la création de rapports.


## <a name="related-topics"></a>Rubriques connexes
- [Intégrer des appareils Windows 10 et Windows 11 à l’aide de Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Intégrer les appareils Windows 10 et Windows 11 à l’aide des outils de gestion des périphériques mobiles](device-onboarding-mdm.md)
- [Intégrer les appareils Windows 10 et Windows 11 en utilisant un script local](device-onboarding-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](device-onboarding-vdi.md)
- [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Résoudre les problèmes d’intégration de Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
