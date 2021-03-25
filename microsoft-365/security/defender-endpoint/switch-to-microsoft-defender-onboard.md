---
title: Basculer vers Microsoft Defender pour le point de terminaison - Intégré
description: Il s’agit de la phase 3, Onboard, pour la migration d’une solution non-Microsoft vers Microsoft Defender for Endpoint.
keywords: migration, protection avancée contre les menaces Windows Defender, atp, edr
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
ms.custom: migrationguides
ms.topic: article
ms.date: 03/03/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 2916f113f3c26a9c33c6da1f235a9b143667b9cf
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51068473"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-3-onboard"></a>Basculer vers Microsoft Defender pour le point de terminaison - Phase 3 : Intégration

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| [![Phase 1 : Préparer3](images/phase-diagrams/prepare.png)](switch-to-microsoft-defender-prepare.md)<br/>[Phase 1 : Préparer](switch-to-microsoft-defender-prepare.md) | [![Phase 2 : Configurer](images/phase-diagrams/setup.png)](switch-to-microsoft-defender-setup.md)<br/>[Phase 2 : Configurer](switch-to-microsoft-defender-setup.md) | ![Phase 3 : Intégration](images/phase-diagrams/onboard.png)<br/>Phase 3 : Intégration |
|--|--|--|
|| |*Vous êtes là !* |


**Bienvenue dans la phase 3 du [basculement vers Microsoft Defender pour point de terminaison.](switch-to-microsoft-defender-migration.md#the-migration-process)** Cette phase de migration comprend les étapes suivantes :

1. [Intégrer des appareils à Microsoft Defender pour le point de terminaison.](#onboard-devices-to-microsoft-defender-for-endpoint)
2. [Exécutez un test de détection.](#run-a-detection-test)
3. [Désinstallez votre solution non-Microsoft.](#uninstall-your-non-microsoft-solution)
4. [Assurez-vous que Microsoft Defender pour le point de terminaison est en mode actif.](#make-sure-microsoft-defender-for-endpoint-is-in-active-mode)

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Intégrer des appareils à Microsoft Defender pour le point de terminaison

1. Go to the Microsoft Defender Security Center ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ) and sign in.
2. Choose **Settings**  >  **Device management**  >  **Onboarding**. 
3. Dans la **liste Sélectionner le système d’exploitation pour démarrer le** processus d’intégration, sélectionnez un système d’exploitation. 
4. Sous **Méthode de déploiement,** sélectionnez une option. Suivez les liens et invites pour intégrer les appareils de votre organisation. Vous avez besoin d’aide ? Voir [méthodes d’intégration](#onboarding-methods) (dans cet article).

### <a name="onboarding-methods"></a>Méthodes d’intégration
 
Les méthodes de déploiement varient en fonction du système d’exploitation sélectionné. Reportez-vous aux ressources répertoriées dans le tableau ci-dessous pour obtenir de l’aide sur l’intégration.

|Système d’exploitation  |Méthode  |
|---------|---------|
|Windows 10     |- [Stratégie de groupe](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-gp)<br/>- [Configuration Manager](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-sccm)<br/>- [Gestion des appareils mobiles (Intune)](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-mdm)<br/>- [Script local](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-script) <br/><br/>**REMARQUE**: un script local convient pour une preuve de concept, mais ne doit pas être utilisé pour le déploiement de production. Pour un déploiement de production, nous vous recommandons d’utiliser la stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune.         |
|- Windows 8.1 Entreprise <br/>- Windows 8.1 Professionnel <br/>- Windows 7 SP1 Entreprise <br/>- Windows 7 SP1 Professionnel     | [Agent de surveillance Microsoft](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/onboard-downlevel#install-and-configure-microsoft-monitoring-agent-mma-to-report-sensor-data-to-microsoft-defender-atp)<br/><br/>**REMARQUE**: l’Agent de surveillance Microsoft est désormais l’agent Azure Log Analytics. Pour en savoir plus, consultez la vue [d’ensemble de l’agent Log Analytics.](https://docs.microsoft.com/azure/azure-monitor/platform/log-analytics-agent)        |
|- Windows Server 2019 et ultérieur <br/>- Édition principale de Windows Server 2019 <br/>- Windows Server version 1803 et ultérieures |- [Script local](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-script) <br/>- [Stratégie de groupe](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-gp) <br/>- [Configuration Manager](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-sccm) <br/>- [System Center Configuration Manager](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-sccm#onboard-windows-10-devices-using-earlier-versions-of-system-center-configuration-manager) <br/>- [Scripts d’intégration VDI pour les appareils non persistants](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-vdi) <br/><br/>**REMARQUE**: un script local convient pour une preuve de concept, mais ne doit pas être utilisé pour le déploiement de production. Pour un déploiement de production, nous vous recommandons d’utiliser la stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune.    |
|- Windows Server 2016 <br/>- Windows Server 2012 R2 <br/>- Windows Server 2008 R2 SP1  |- [Centre de sécurité Microsoft Defender](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-server-endpoints#option-1-onboard-servers-through-microsoft-defender-security-center)<br/>- [Centre de sécurité Azure](https://docs.microsoft.com/azure/security-center/security-center-wdatp) |
|macOS<br/>- 10.15 (Caserline)<br/>- 10.14 (Mojave)<br/>- 10.13 (High Sierra)<br/><br/>iOS<br/><br/>Linux :<br/>- RHEL 7.2+<br/>- CentOS Linux 7.2+<br/>- Ubuntu 16 LTS ou un LTS supérieur<br/>- SLES 12+<br/>- Debian 9+<br/>- Oracle Linux 7.2 |[Intégrer des appareils autres que Windows](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-endpoints-non-windows)  |

## <a name="run-a-detection-test"></a>Exécuter un test de détection

Pour vérifier que vos appareils intégrés sont correctement connectés à Microsoft Defender pour le point de terminaison, vous pouvez exécuter un test de détection.

|Système d’exploitation  |Aide  |
|---------|---------|
|- Windows 10 <br/>- Windows Server 2019 <br/>- Windows Server, version 1803 <br/>- Windows Server 2016 <br/>- Windows Server 2012 R2     |Voir [Exécuter un test de détection.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/run-detection-test) <br/><br/>Visitez le site des scénarios de démonstration de Microsoft Defender for Endpoint () et [https://demo.wd.microsoft.com](https://demo.wd.microsoft.com) essayez un ou plusieurs des scénarios. Par exemple, essayez le scénario de démonstration **de la protection** cloud.         |
|macOS<br/>- 10.15 (Caserline)<br/>- 10.14 (Mojave)<br/>- 10.13 (High Sierra)     |Téléchargez et utilisez l’application CASER sur [https://aka.ms/mdatpmacosdiy](https://aka.ms/mdatpmacosdiy) . <br/><br/>Pour plus d’informations, [voir Microsoft Defender pour Endpoint pour Mac.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/microsoft-defender-atp-mac)        |
|Linux :<br/>- RHEL 7.2+<br/>- CentOS Linux 7.2+<br/>- Ubuntu 16 LTS ou un LTS supérieur<br/>- SLES 12+<br/>- Debian 9+<br/>- Oracle Linux 7.2 |1. Exécutez la commande suivante et recherchez le résultat **1**: <br/>`mdatp health --field real_time_protection_enabled`. <br/><br/>2. Ouvrez une fenêtre Terminal et exécutez la commande suivante : <br/>`curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`. <br/><br/>3. Exécutez la commande suivante pour lister les menaces détectées : <br/>`mdatp threat list`. <br/><br/>Pour plus d’informations, [voir Microsoft Defender ATP pour Linux.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/microsoft-defender-atp-linux) |

## <a name="uninstall-your-non-microsoft-solution"></a>Désinstaller votre solution non-Microsoft

Maintenant que vous avez intégré les appareils de votre organisation à Microsoft Defender pour endpoint, l’étape suivante consiste à désinstaller votre solution de protection des points de terminaison non-Microsoft.

Pour obtenir de l’aide sur cette étape, entrez en charge l’équipe de support technique de votre fournisseur de solutions.

## <a name="make-sure-microsoft-defender-for-endpoint-is-in-active-mode"></a>Assurez-vous que Microsoft Defender pour le point de terminaison est en mode actif

Maintenant que vous avez désinstallé votre solution de protection de point de terminaison non Microsoft, l’étape suivante consiste à vous assurer que l’Antivirus Microsoft Defender et Microsoft Defender pour le point de terminaison sont activés et en mode actif.

Pour ce faire, visitez le site de démonstration de Microsoft Defender for Endpoint ( [https://demo.wd.microsoft.com](https://demo.wd.microsoft.com) ). Essayez un ou plusieurs scénarios de démonstration sur cette page, y compris au moins les scénarios suivants :
- Protection cloud
- Applications potentiellement indésirables (PUA)
- Protection du réseau (NP)

> [!IMPORTANT]
> Si vous utilisez Windows Server 2016, vous de devez démarrer l’Antivirus Microsoft Defender manuellement. Vous pouvez le faire à l’aide de l’cmdlet PowerShell `mpcmdrun.exe -wdenable` sur l’appareil.

## <a name="next-steps"></a>Étapes suivantes

**Félicitations**! Vous avez terminé votre [migration vers Microsoft Defender pour le point de terminaison](switch-to-microsoft-defender-migration.md#the-migration-process)! 

- [Visitez votre tableau de bord des opérations de](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/security-operations-dashboard) sécurité dans le Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ). 
- [Gérer Microsoft Defender pour le point de terminaison, après la migration.](manage-atp-post-migration.md)
