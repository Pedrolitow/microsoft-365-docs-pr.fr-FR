---
title: Symantec vers Microsoft Defender pour le point de terminaison - Phase 3, Intégration
description: Il s'agit de la phase 3, intégration, de la migration de Symantec vers Microsoft Defender pour endpoint
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
- m365solution-symantecmigrate
ms.topic: article
ms.date: 03/03/2021
ms.custom: migrationguides
ms.reviewer: depicker, yongrhee, chriggs
ms.openlocfilehash: b42a33d975e1368ad25d4a7102ef44bf8b9824a8
ms.sourcegitcommit: 72ae1b49e7a3d3199272fcb4c39f5daec0d66f1a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51698279"
---
# <a name="migrate-from-symantec---phase-3-onboard-to-microsoft-defender-for-endpoint"></a>Migrer de Symantec - Phase 3 : intégration à Microsoft Defender pour le point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![Phase 1 : préparation](images/phase-diagrams/prepare.png)](symantec-to-microsoft-defender-atp-prepare.md)<br/>[Phase 1 : préparation](symantec-to-microsoft-defender-atp-prepare.md) |[![Phase 2 : configuration](images/phase-diagrams/setup.png)](symantec-to-microsoft-defender-atp-setup.md)<br/>[Phase 2 : configuration](symantec-to-microsoft-defender-atp-setup.md) |![Phase 3 : intégration](images/phase-diagrams/onboard.png)<br/>Phase 3 : intégration |
|--|--|--|
|| |*Vous êtes là !* |


**Bienvenue dans la phase 3 de [la migration de Symantec vers Microsoft Defender pour endpoint.](symantec-to-microsoft-defender-endpoint-migration.md#the-migration-process)** Cette phase de migration comprend les étapes suivantes :

1. [Intégrer des appareils à Microsoft Defender pour le point de terminaison.](#onboard-devices-to-microsoft-defender-for-endpoint)
2. [Exécutez un test de détection.](#run-a-detection-test)
3. [Désinstaller Symantec](#uninstall-symantec).
4. [Assurez-vous que Microsoft Defender pour le point de terminaison est en mode actif.](#make-sure-microsoft-defender-for-endpoint-is-in-active-mode)

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Intégrer des appareils à Microsoft Defender pour point de terminaison

1. Go to the Microsoft Defender Security Center ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ) and sign in.
2. Choose **Settings**  >  **Device management**  >  **Onboarding**. 
3. Dans la **liste Sélectionner le système d'exploitation pour démarrer le** processus d'intégration, sélectionnez un système d'exploitation. 
4. Sous **Méthode de déploiement,** sélectionnez une option. Suivez les liens et invites pour intégrer les appareils de votre organisation. Vous avez besoin d’aide ? Voir [méthodes d'intégration](#onboarding-methods) (dans cet article).

### <a name="onboarding-methods"></a>Méthodes d'intégration
 
Les méthodes de déploiement varient en fonction du système d'exploitation sélectionné. Reportez-vous aux ressources répertoriées dans le tableau ci-dessous pour obtenir de l'aide sur l'intégration.

|Système d’exploitation  |Méthode  |
|---------|---------|
|Windows 10     |- [Stratégie de groupe](configure-endpoints-gp.md)<br/>- [Configuration Manager](configure-endpoints-sccm.md)<br/>- [Gestion des appareils mobiles (Intune)](configure-endpoints-mdm.md)<br/>- [Script local](configure-endpoints-script.md) <br/><br/>**REMARQUE**: un script local est approprié pour une preuve de concept, mais ne doit pas être utilisé pour le déploiement de production. Pour un déploiement de production, nous vous recommandons d'utiliser la stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune.         |
|- Windows 8.1 Entreprise <br/>- Windows 8.1 Professionnel <br/>- Windows 7 SP1 Entreprise <br/>- Windows 7 SP1 Professionnel     | [Agent de surveillance Microsoft](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma-to-report-sensor-data-to-microsoft-defender-for-endpoint)<br/><br/>**REMARQUE**: l'Agent de surveillance Microsoft est désormais l'agent Azure Log Analytics. Pour en savoir plus, consultez la vue [d'ensemble de l'agent Log Analytics.](https://docs.microsoft.com/azure/azure-monitor/platform/log-analytics-agent)        |
|- Windows Server 2019 et ultérieur <br/>- Édition principale de Windows Server 2019 <br/>- Windows Server version 1803 et ultérieures |- [Script local](configure-endpoints-script.md) <br/>- [Stratégie de groupe](configure-endpoints-gp.md) <br/>- [Configuration Manager](/configure-endpoints-sccm.md) <br/>- [System Center Configuration Manager](configure-endpoints-sccm.md#onboard-devices-using-system-center-configuration-manager)<br/>- [Scripts d'intégration VDI pour les appareils non persistants](configure-endpoints-vdi.md) <br/><br/>**REMARQUE**: un script local convient pour une preuve de concept, mais ne doit pas être utilisé pour le déploiement de production. Pour un déploiement de production, nous vous recommandons d'utiliser la stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune.    |
|- Windows Server 2016 <br/>- Windows Server 2012 R2 <br/>- Windows Server 2008 R2 SP1  |- [Centre de sécurité Microsoft Defender](configure-server-endpoints.md)<br/>- [Centre de sécurité Azure](https://docs.microsoft.com/azure/security-center/security-center-wdatp) |
|macOS<br/>- 10.15 (Caserline)<br/>- 10.14 (Mojave)<br/>- 10.13 (High Sierra)<br/><br/>iOS<br/><br/>Linux :<br/>- RHEL 7.2+<br/>- CentOS Linux 7.2+<br/>- Ubuntu 16 LTS ou un LTS supérieur<br/>- SLES 12+<br/>- Debian 9+<br/>- Oracle Linux 7.2 |[Intégrer des appareils non Windows](configure-endpoints-non-windows.md)  |

## <a name="run-a-detection-test"></a>Exécuter un test de détection

Pour vérifier que vos appareils intégrés sont correctement connectés à Microsoft Defender pour endpoint, vous pouvez exécuter un test de détection.

|Système d’exploitation  |Aide  |
|---------|---------|
|- Windows 10 <br/>- Windows Server 2019 <br/>- Windows Server, version 1803 <br/>- Windows Server 2016 <br/>- Windows Server 2012 R2     |Voir [Exécuter un test de détection.](run-detection-test.md) <br/><br/>Visitez le site des scénarios de démonstration Microsoft Defender for Endpoint () et essayez un ou [https://demo.wd.microsoft.com](https://demo.wd.microsoft.com) plusieurs des scénarios. Par exemple, essayez le scénario de démonstration **de la protection** livrée par le cloud.         |
|macOS<br/>- 10.15 (Îles)<br/>- 10.14 (Mojave)<br/>- 10.13 (High Sierra)     |Téléchargez et utilisez l'application CASER sur [https://aka.ms/mdatpmacosdiy](https://aka.ms/mdatpmacosdiy) . <br/><br/>Pour plus d'informations, [voir Microsoft Defender pour point de terminaison sur macOS.](microsoft-defender-endpoint-mac.md)        |
|Linux :<br/>- RHEL 7.2+<br/>- CentOS Linux 7.2+<br/>- Ubuntu 16 LTS ou un LTS supérieur<br/>- SLES 12+<br/>- Debian 9+<br/>- Oracle Linux 7.2 |1. Exécutez la commande suivante et recherchez le résultat **1**: <br/>`mdatp health --field real_time_protection_enabled`. <br/><br/>2. Ouvrez une fenêtre Terminal et exécutez la commande suivante : <br/>`curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`. <br/><br/>3. Exécutez la commande suivante pour lister les menaces détectées : <br/>`mdatp threat list`. <br/><br/>Pour plus d'informations, [voir Microsoft Defender pour Endpoint sur Linux.](microsoft-defender-endpoint-linux.md) |

## <a name="uninstall-symantec"></a>Désinstaller Symantec

Maintenant que vous avez intégré les appareils de votre organisation à Microsoft Defender pour endpoint, l'étape suivante consiste à désinstaller Symantec.

1. [Désactiver la protection contre les falsifications](https://knowledge.broadcom.com/external/article?legacyId=tech192023) dans Symantec.
2. Supprimez le mot de passe de désinstallation de Symantec :<br/>
   1. Sur vos appareils Windows, ouvrez l'Éditeur du Registre en tant qu'administrateur.
   2. Accédez à `HKEY_LOCAL_MACHINE\SOFTWARE\Symantec\Symantec Endpoint Protection\SMC`.
   3. Recherchez une entrée nommée **SmcInstData**. 
   4. Cliquez avec le bouton droit sur l'élément, puis choisissez **Supprimer.** 
3. Supprimez Symantec de vos appareils. Si vous avez besoin d'aide, consultez la documentation de Broadcom. Voici quelques ressources Broadcom : 
   - [Désinstaller Symantec Endpoint Protection](https://knowledge.broadcom.com/external/article/156148/uninstall-symantec-endpoint-protection.html)
   - Appareils Windows : [désinstaller manuellement les clients Endpoint Protection 14 sur Windows](https://knowledge.broadcom.com/external/article?articleId=170040)
   - Ordinateurs macOS : supprimer le logiciel Symantec pour Mac à [l'aide de RemoveSymantecMacFiles](https://knowledge.broadcom.com/external/article?articleId=151387)
   - Appareils Linux : [questions fréquemment posées sur Endpoint Protection sur Linux](https://knowledge.broadcom.com/external/article?articleId=162054)

## <a name="make-sure-microsoft-defender-for-endpoint-is-in-active-mode"></a>Assurez-vous que Microsoft Defender pour le point de terminaison est en mode actif

Maintenant que vous avez désinstallé Symantec, l'étape suivante consiste à vous assurer que l'Antivirus Microsoft Defender et Microsoft Defender pour le point de terminaison sont activés et en mode actif.

Pour ce faire, visitez le site de démonstration de Microsoft Defender for Endpoint ( [https://demo.wd.microsoft.com](https://demo.wd.microsoft.com) ). Essayez un ou plusieurs scénarios de démonstration sur cette page, y compris au moins les scénarios suivants :
- Protection cloud
- Applications potentiellement indésirables (PUA)
- Protection du réseau (NP)

> [!IMPORTANT]
> Si vous utilisez Windows Server 2016, vous de devez démarrer l'Antivirus Microsoft Defender manuellement. Vous pouvez le faire à l'aide de l'cmdlet PowerShell `mpcmdrun.exe -wdenable` sur l'appareil.

## <a name="next-steps"></a>Étapes suivantes

**Félicitations**! Vous avez terminé votre [migration de Symantec vers Microsoft Defender pour endpoint](symantec-to-microsoft-defender-endpoint-migration.md#the-migration-process)! 
- [Visitez votre tableau de bord des opérations de](security-operations-dashboard.md) sécurité dans le Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ). 
- [Gérer Microsoft Defender pour le point de terminaison, après la migration.](manage-atp-post-migration.md)
