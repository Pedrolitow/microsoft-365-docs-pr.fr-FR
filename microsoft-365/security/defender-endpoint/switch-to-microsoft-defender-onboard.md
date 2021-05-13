---
title: Basculer vers Microsoft Defender pour le point de terminaison - Intégré
description: Il s’agit de la phase 3, Onboard, pour la migration d’une solution non-Microsoft vers Microsoft Defender pour Endpoint.
keywords: migration, Microsoft Defender pour point de terminaison, edr
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
ms.date: 05/11/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 66d24f5a479a903c8d42d509f1bbe956293c9ac3
ms.sourcegitcommit: 94e64afaf12f3d8813099d8ffa46baba65772763
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52346339"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-3-onboard"></a>Basculer vers Microsoft Defender pour le point de terminaison - Phase 3 : Intégration

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| [![Phase 1 : Préparer3](images/phase-diagrams/prepare.png)](switch-to-microsoft-defender-prepare.md)<br/>[Phase 1 : préparation](switch-to-microsoft-defender-prepare.md) | [![Phase 2 : configuration](images/phase-diagrams/setup.png)](switch-to-microsoft-defender-setup.md)<br/>[Phase 2 : configuration](switch-to-microsoft-defender-setup.md) | ![Phase 3 : intégration](images/phase-diagrams/onboard.png)<br/>Phase 3 : intégration |
|--|--|--|
|| |*Vous êtes là !* |


**Bienvenue dans la phase 3 du [basculement vers Microsoft Defender pour point de terminaison.](switch-to-microsoft-defender-migration.md#the-migration-process)** Cette phase de migration comprend les étapes suivantes :

1. [Intégrer des appareils à Microsoft Defender pour le point de terminaison.](#onboard-devices-to-microsoft-defender-for-endpoint)

2. [Exécutez un test de détection.](#run-a-detection-test)

3. [Désinstallez votre solution non-Microsoft.](#uninstall-your-non-microsoft-solution)

4. [Assurez-vous que Microsoft Defender pour le point de terminaison est en mode actif.](#make-sure-microsoft-defender-for-endpoint-is-in-active-mode)

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Intégrer des appareils à Microsoft Defender pour point de terminaison

1. Go to the Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ) and sign in.

2. Choose **Paramètres**  >  **Device management**  >  **Onboarding**. 

3. Dans la **liste Sélectionner le système d’exploitation pour démarrer le** processus d’intégration, sélectionnez un système d’exploitation. 

4. Sous **Méthode de déploiement,** sélectionnez une option. Suivez les liens et invites pour intégrer les appareils de votre organisation. Besoin d’aide ? Voir [méthodes d’intégration](#onboarding-methods) (dans cet article).

### <a name="onboarding-methods"></a>Méthodes d’intégration
 
Les méthodes de déploiement varient en fonction du système d’exploitation sélectionné. Reportez-vous aux ressources répertoriées dans le tableau ci-dessous pour obtenir de l’aide sur l’intégration.

|Système d’exploitation  |Méthode  |
|---------|---------|
|Windows 10     |- [Stratégie de groupe](configure-endpoints-gp.md)<br/>- [Configuration Manager](configure-endpoints-sccm.md)<br/>- [Gestion des appareils mobiles (Intune)](configure-endpoints-mdm.md)<br/>- [Script local](configure-endpoints-script.md) <p>**REMARQUE**: un script local est approprié pour une preuve de concept, mais ne doit pas être utilisé pour le déploiement de production. Pour un déploiement de production, nous vous recommandons d’utiliser la stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune.         |
|- Windows 8.1 Entreprise <br/>- Windows 8.1 Professionnel <br/>- Windows 7 SP1 Enterprise <br/>- Windows 7 SP1 Pro     | [Microsoft Monitoring Agent](onboard-downlevel.md)<p>**REMARQUE**: Microsoft Monitoring Agent est désormais l’agent Azure Log Analytics. Pour en savoir plus, consultez la vue [d’ensemble de l’agent Log Analytics.](/azure/azure-monitor/platform/log-analytics-agent)        |
|- Windows Server 2019 et les ultérieures <br/>- Windows Server 2019 core edition <br/>- Windows Server version 1803 et ultérieures |- [Script local](configure-endpoints-script.md) <br/>- [Stratégie de groupe](configure-endpoints-gp.md) <br/>- [Configuration Manager](configure-endpoints-sccm.md) <br/>- [System Center Configuration Manager](configure-endpoints-sccm.md) <br/>- [Scripts d’intégration VDI pour les appareils non persistants](configure-endpoints-vdi.md) <p>**REMARQUE**: un script local est approprié pour une preuve de concept, mais ne doit pas être utilisé pour le déploiement de production. Pour un déploiement de production, nous vous recommandons d’utiliser la stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune.    |
|- Windows Server 2016 <br/>- Windows Server 2012 R2 <br/>- Windows Server 2008 R2 SP1  |- [Centre de sécurité Microsoft Defender](configure-server-endpoints.md)<br/>- [Azure Defender](/azure/security-center/security-center-wdatp) |
|macOS<br/>- 11.3.1 (Big Sur) <br/>- 10.15 (Îles)<br/>- 10.14 (Mojave)<p>iOS<p>Linux :<br/>- RHEL 7.2+<br/>- CentOS Linux 7.2+<br/>- Ubuntu 16 LTS ou un LTS supérieur<br/>- SLES 12+<br/>- Debian 9+<br/>- Oracle Linux 7.2 |[Intégrer des appareils non Windows](configure-endpoints-non-windows.md)  |

## <a name="run-a-detection-test"></a>Exécuter un test de détection

Pour vérifier que vos appareils intégrés sont correctement connectés à Microsoft Defender pour endpoint, vous pouvez exécuter un test de détection.

|Système d’exploitation  |Aide  |
|---------|---------|
|- Windows 10 <br/>- Windows Server 2019 <br/>- Windows Server, version 1803 <br/>- Windows Server 2016 <br/>- Windows Server 2012 R2     |Voir [Exécuter un test de détection.](run-detection-test.md) <p>Visitez le site des scénarios de démonstration Microsoft Defender for Endpoint () et essayez un ou [https://demo.wd.microsoft.com](https://demo.wd.microsoft.com) plusieurs des scénarios. Par exemple, essayez le scénario de démonstration **de la protection** livrée par le cloud.         |
|macOS<br/>- 11.3.1 (Big Sur) <br/>- 10.15 (Îles)<br/>- 10.14 (Mojave)    |Téléchargez et utilisez l’application CASER sur [https://aka.ms/mdatpmacosdiy](https://aka.ms/mdatpmacosdiy) . <p>Pour plus d’informations, [voir Microsoft Defender pour point de terminaison sur macOS.](microsoft-defender-endpoint-mac.md)        |
|Linux :<br/>- RHEL 7.2+<br/>- CentOS Linux 7.2+<br/>- Ubuntu 16 LTS ou un LTS supérieur<br/>- SLES 12+<br/>- Debian 9+<br/>- Oracle Linux 7.2 |1. Exécutez la commande suivante et recherchez le résultat **1**: <br/>`mdatp health --field real_time_protection_enabled`. <p>2. Ouvrez une fenêtre Terminal et exécutez la commande suivante : <br/>`curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`. <p>3. Exécutez la commande suivante pour lister les menaces détectées : <br/>`mdatp threat list`. <p>Pour plus d’informations, [voir Microsoft Defender pour Endpoint sur Linux.](microsoft-defender-endpoint-linux.md) |

## <a name="uninstall-your-non-microsoft-solution"></a>Désinstaller votre solution non-Microsoft

Maintenant que vous avez intégré les appareils de votre organisation à Microsoft Defender pour endpoint, l’étape suivante consiste à désinstaller votre solution de protection des points de terminaison non-Microsoft.

Pour obtenir de l’aide sur cette étape, entrez en charge l’équipe de support technique de votre fournisseur de solutions.

## <a name="make-sure-microsoft-defender-for-endpoint-is-in-active-mode"></a>Assurez-vous que Microsoft Defender pour le point de terminaison est en mode actif

Maintenant que vous avez désinstallé votre solution de protection des points de terminaison non Microsoft, l’étape suivante consiste à vous assurer que Antivirus Microsoft Defender et Microsoft Defender pour endpoint sont activés et en mode actif.

Pour ce faire, visitez le site de démonstration de Microsoft Defender for Endpoint ( [https://demo.wd.microsoft.com](https://demo.wd.microsoft.com) ). Essayez un ou plusieurs scénarios de démonstration sur cette page, y compris au moins les scénarios suivants :
- Protection fournie par le cloud
- Applications potentiellement indésirables (PUA)
- Protection du réseau (NP)

> [!IMPORTANT]
> Si vous utilisez Windows Server 2016, vous de devez démarrer Antivirus Microsoft Defender manuellement. Vous pouvez le faire à l’aide de l’cmdlet PowerShell `mpcmdrun.exe -wdenable` sur l’appareil.

## <a name="next-steps"></a>Prochaines étapes

**Félicitations**! Vous avez terminé votre [migration vers Microsoft Defender pour le point de terminaison](switch-to-microsoft-defender-migration.md#the-migration-process)! 

- [Visitez votre tableau de bord des opérations](security-operations-dashboard.md) de sécurité dans le Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ). 

- [Gérer Microsoft Defender pour le point de terminaison, après la migration.](manage-atp-post-migration.md)
