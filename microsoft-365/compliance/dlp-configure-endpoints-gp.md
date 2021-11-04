---
title: Appareils Windows 10 intégrés via une stratégie de groupe
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Utilisez la stratégie de groupe pour déployer le package de configuration sur Windows 10 afin qu’ils soient intégrés au service.
ms.openlocfilehash: 3329d21b4e0ba55c4b91a56a26af890b1199fb56
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2021
ms.locfileid: "60755733"
---
# <a name="onboard-windows-10-devices-using-group-policy"></a>Intégrer des Windows 10 à l’aide de la stratégie de groupe 

**S’applique à :**

- [Microsoft 365 Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- Stratégie de groupe

> [!NOTE]
> Pour utiliser les mises à jour de stratégie de groupe (GP) pour déployer le package, vous devez être sur Windows Server 2008 R2 ou version ultérieure.

> Pour Windows Server 2019, vous devrez peut-être remplacer NT AUTHORITY\Well-Known-System-Account par NT AUTHORITY\SYSTEM du fichier XML créé par la préférence de stratégie de groupe.

## <a name="onboard-devices-using-group-policy"></a>Intégrer des appareils à l’aide d’une stratégie de groupe

1. Ouvrez le fichier de package de configuration de .zip de groupe (*DeviceComplianceOnboardingPackage.zip*) que vous avez téléchargé à partir de l’Assistant d’intégration de service. Vous pouvez également obtenir le package à partir du [Centre de conformité Microsoft](https://compliance.microsoft.com/compliancesettings/deviceonboarding)

2. Dans le volet de navigation, sélectionnez  >  **Paramètres’intégration de l’appareil.**

3. Dans le **champ Méthode de déploiement,** sélectionnez **Stratégie de groupe.**

4. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

5. Extrayez le contenu du .zip vers un emplacement partagé en lecture seule accessible par l’appareil. Vous devez avoir un dossier appelé *OptionalParamsPolicy* et le fichier *DeviceComplianceLocalOnboardingScript.cmd*.

6. Ouvrez [la Console](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) de gestion des stratégies de groupe (GPMC), cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

7. Dans **l’Éditeur de gestion des stratégies** de groupe, allez à **Configuration** ordinateur, puis **Préférences,** puis **paramètres du panneau de configuration.**

8. Cliquez avec le bouton droit **sur Tâches programmées,** pointez sur **Nouveau,** puis cliquez sur **Tâche immédiate (au moins Windows 7).**

9. Dans la **fenêtre** Tâche qui s’ouvre, allez dans **l’onglet** Général. Sous **Options de sécurité,** **cliquez sur Modifier** l’utilisateur ou le groupe, puis tapez SYSTEM, puis cliquez sur Vérifier **les noms,** **puis OK.** NT AUTHORITY\SYSTEM apparaît en tant que compte d’utilisateur que la tâche exécutera.

10. Sélectionnez **Exécuter, que l’utilisateur soit** connecté ou non, puis cochez la case Exécuter avec les **privilèges les plus élevés.**

11. Go to the **Actions** tab and click **New...** **Assurez-vous que démarrer un programme** est sélectionné dans le champ **Action.** Entrez le nom de fichier et l’emplacement du fichier *WindowsDefenderATPOnboardingScript.cmd* partagé.

12. Cliquez **sur OK** et fermez toutes les fenêtres GPMC ouvertes.

## <a name="offboard-devices-using-group-policy"></a>Appareils de tableau de bord à l’aide de la stratégie de groupe

Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages deboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et deboarding ne doivent pas être déployées sur le même appareil en même temps, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package deboarding à partir du [Centre de conformité Microsoft.](https://compliance.microsoft.com/compliancesettings/deviceonboarding)

2. Dans le volet de navigation, sélectionnez **Paramètres**  >  **//Intégration de** l’appareil hors  >  **intégration.**

3. Dans le **champ Méthode de déploiement,** sélectionnez **Stratégie de groupe.**

4. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

5. Extrayez le contenu du .zip vers un emplacement partagé en lecture seule accessible par l’appareil. Vous devez avoir un fichier nommé *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Ouvrez [la Console](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) de gestion des stratégies de groupe (GPMC), cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

7. Dans **l’Éditeur de gestion des stratégies** de groupe, allez à **Configuration ordinateur,** puis **Préférences,** puis **paramètres du panneau de configuration.**

8. Cliquez avec le bouton droit **sur Tâches programmées,** pointez sur **Nouveau,** puis cliquez sur **Tâche immédiate.**

9. Dans la **fenêtre** Tâche qui s’ouvre, allez dans **l’onglet** Général. Choisissez le compte d’utilisateur SYSTÈME local (BUILTIN\SYSTEM) sous **Options de sécurité.**

10. Sélectionnez **Exécuter, que l’utilisateur soit** connecté ou non, puis cochez la case Exécuter avec les privilèges les plus **élevés.**

11. Go to the **Actions** tab and click **New...**. **Assurez-vous que démarrer un programme** est sélectionné dans le champ **Action.** Entrez le nom de fichier et l’emplacement du fichier  *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd* partagé.

12. Cliquez **sur OK** et fermez toutes les fenêtres GPMC ouvertes.

> [!IMPORTANT]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais à partir de l’appareil.


## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil
Avec la stratégie de groupe, il n’existe pas d’option pour surveiller le déploiement des stratégies sur les appareils. La surveillance peut être effectuée directement sur le portail ou à l’aide des différents outils de déploiement.

## <a name="monitor-devices-using-the-portal"></a>Surveiller les appareils à l’aide du portail
1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">centre de conformité Microsoft 365</a>.
2. Cliquez sur **La liste** Appareils.
3. Vérifiez que les appareils apparaissent.

> [!NOTE]
> L’affichage des appareils dans la liste Appareils peut prendre plusieurs **jours.** Cela inclut le temps qu’il faut pour que les stratégies soient distribuées à l’appareil, le temps qu’il faut avant que l’utilisateur se connecte et le temps qu’il faut au point de terminaison pour commencer à créer des rapports.


## <a name="related-topics"></a>Voir aussi
- [Intégrer Windows 10 appareils à l’aide Microsoft Endpoint Configuration Manager](dlp-configure-endpoints-sccm.md)
- [Intégrer les appareils Windows 10 à l’aide des outils de gestion des appareils mobiles](dlp-configure-endpoints-mdm.md)
- [Intégrer les appareils Windows 10 utilisant un script local](dlp-configure-endpoints-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](dlp-configure-endpoints-vdi.md)
- [Exécuter un test de détection sur un microsoft Defender pour les appareils de point de terminaison nouvellement intégré](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Résoudre les problèmes d’intégration de la Protection avancée contre les menaces Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)