---
title: Intégrer des Windows 10 et des Windows 11 via la stratégie de groupe
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
description: Utilisez la stratégie de groupe pour déployer le package de configuration sur Windows 10 et Windows 11 afin qu’ils soient intégrés au service.
ms.openlocfilehash: fbba73fcf15ee9f71c4caacc57155a64e6cb9e9c
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2021
ms.locfileid: "60950831"
---
# <a name="onboard-windows-10-devices-and-windows-11-using-group-policy"></a>Intégrer des Windows 10 et des Windows 11 à l’aide de la stratégie de groupe 

**S’applique à :**

- [Microsoft 365 protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
- Stratégie de groupe

> [!NOTE]
> Pour utiliser les mises à jour de stratégie de groupe (GP) pour déployer le package, vous devez être sur Windows Server 2008 R2 ou version ultérieure.

> Pour Windows Server 2019, vous devrez peut-être remplacer NT AUTHORITY\Well-Known-System-Account par NT AUTHORITY\SYSTEM du fichier XML créé par la préférence de stratégie de groupe.

## <a name="onboard-devices-using-group-policy"></a>Intégrer des appareils à l’aide d’une stratégie de groupe

1. Ouvrez [le Centre de conformité.](https://compliance.microsoft.com)

2. Dans le volet de navigation, sélectionnez  >  **Paramètres’intégration de l’appareil.**

3. Dans le **champ Méthode de déploiement,** sélectionnez **Stratégie de groupe.**

4. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

5. Extrayez le contenu du .zip vers un emplacement partagé en lecture seule accessible par l’appareil. Vous devez avoir un dossier appelé *OptionalParamsPolicy* et le fichier *DeviceComplianceLocalOnboardingScript.cmd*.

6. Ouvrez [la Console](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) de gestion des stratégies de groupe (GPMC), cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

7. Dans **l’Éditeur de gestion des stratégies** de groupe, allez à **Configuration** ordinateur, puis **Préférences,** puis **paramètres du panneau de configuration.**

8. Cliquez avec le bouton droit **sur Tâches programmées,** pointez sur **Nouveau,** puis cliquez sur **Tâche immédiate (au moins Windows 7).**

9. Dans la **fenêtre** Tâche qui s’ouvre, allez dans **l’onglet** Général. Sous **Options de sécurité,** cliquez **sur Modifier l’utilisateur ou** le groupe, puis tapez SYSTEM, puis cliquez sur Vérifier les **noms,** **puis OK.** NT AUTHORITY\SYSTEM apparaît en tant que compte d’utilisateur que la tâche exécutera.

10. Sélectionnez **Exécuter, que l’utilisateur soit** connecté ou non, puis cochez la case Exécuter avec les **privilèges les plus élevés.**

11. Go to the **Actions** tab and click **New...** **Assurez-vous que démarrer un programme** est sélectionné dans le champ **Action.** Entrez le nom de fichier et l’emplacement du fichier *WindowsDefenderATPOnboardingScript.cmd* partagé.

12. Cliquez **sur OK** et fermez toutes les fenêtres GPMC ouvertes.

## <a name="offboard-devices-using-group-policy"></a>Appareils de tableau de bord à l’aide de la stratégie de groupe
Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages de offboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et deboarding ne doivent pas être déployées sur le même appareil en même temps, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package de mise hors programme à partir du [Centre de conformité Microsoft.](https://compliance.microsoft.com/compliancesettings/deviceonboarding)

2. Dans le volet de navigation, sélectionnez **Paramètres**  >  **//Intégration de** l’appareil hors  >  **intégration.**

3. Dans le **champ Méthode de déploiement,** sélectionnez **Stratégie de groupe.**

4. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

5. Extrayez le contenu du .zip vers un emplacement partagé en lecture seule accessible par l’appareil. Vous devez avoir un fichier nommé *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Ouvrez [la Console](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) de gestion des stratégies de groupe (GPMC), cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

7. Dans **l’Éditeur de gestion des stratégies** de groupe, allez à **Configuration ordinateur,** puis **Préférences,** puis **paramètres du panneau de configuration.**

8. Cliquez avec le bouton droit **sur Tâches programmées,** pointez sur **Nouveau,** puis cliquez sur **Tâche immédiate.**

9. Dans la **fenêtre** Tâche qui s’ouvre, allez dans **l’onglet** Général. Choisissez le compte d’utilisateur SYSTÈME local (BUILTIN\SYSTEM) sous **Options de sécurité.**

10. Sélectionnez **Exécuter, que l’utilisateur soit** connecté ou non, puis cochez la case Exécuter avec les privilèges les plus **élevés.**

11. Go to the **Actions** tab and click **New...**. **Assurez-vous que démarrer un programme** est sélectionné dans le champ **Action.** Entrez le nom de fichier et l’emplacement du fichier *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd.*

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
- [Intégrer des Windows 10 et des Windows 11 à l’aide Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Intégrer des Windows 10 et Windows 11 à l’aide des outils de gestion des périphériques mobiles](device-onboarding-mdm.md)
- [Intégrer Windows 10 et Windows 11 à l’aide d’un script local](device-onboarding-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](device-onboarding-vdi.md)
- [Exécuter un test de détection sur un microsoft Defender pour les appareils de point de terminaison nouvellement intégré](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Résoudre les problèmes d’intégration de la Protection avancée contre les menaces Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)