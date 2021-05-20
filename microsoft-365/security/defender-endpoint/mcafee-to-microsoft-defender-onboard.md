---
title: Mc Antivirus vers Microsoft Defender pour le point de terminaison - Intégré
description: Il s’agit de la phase 3, Onboard, pour la migration de Mc Antivirus vers Microsoft Defender pour Endpoint.
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
- m365solution-McAfeemigrate
- m365solution-scenario
ms.custom: migrationguides
ms.topic: article
ms.date: 05/14/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 8a9d1ea36ae0778892768e3b39f4ffbed2a8d732
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52538026"
---
# <a name="migrate-from-mcafee---phase-3-onboard-to-microsoft-defender-for-endpoint"></a>Migrer à partir de Mc Antivirus - Phase 3 : intégration à Microsoft Defender pour le point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


|[![Phase 1 : préparation](images/phase-diagrams/prepare.png)](mcafee-to-microsoft-defender-prepare.md)<br/>[Phase 1 : préparation](mcafee-to-microsoft-defender-prepare.md) |[![Phase 2 : configuration](images/phase-diagrams/setup.png)](mcafee-to-microsoft-defender-setup.md)<br/>[Phase 2 : configuration](mcafee-to-microsoft-defender-setup.md) |![Phase 3 : intégration](images/phase-diagrams/onboard.png)<br/>Phase 3 : intégration |
|--|--|--|
|| |*Vous êtes là !* |

**Bienvenue dans la phase 3 de la migration de [Mc Antivirus Endpoint Security (Mc Antivirus)](mcafee-to-microsoft-defender-migration.md#the-migration-process)** vers Microsoft Defender pour Endpoint . Cette phase de migration comprend les étapes suivantes :

1. [Intégrer des appareils à Microsoft Defender pour le point de terminaison.](#onboard-devices-to-microsoft-defender-for-endpoint)

2. [Exécutez un test de détection.](#run-a-detection-test)

3. [Confirmez que Antivirus Microsoft Defender est en mode passif.](#confirm-that-microsoft-defender-antivirus-is-in-passive-mode)

4. [Obtenir les mises à jour de Antivirus Microsoft Defender](#get-updates-for-microsoft-defender-antivirus).

5. [Désinstaller Mc Antivirus](#uninstall-mcafee).

6. [Assurez-vous que Defender pour le point de terminaison fonctionne correctement.](#make-sure-defender-for-endpoint-is-working-correctly)

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Intégrer des appareils à Microsoft Defender pour point de terminaison

1. Go to the Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ) and sign in.

2. Choose **Paramètres**  >  **Device management**  >  **Onboarding**. 

3. Dans la **liste Sélectionner le système d’exploitation pour démarrer le** processus d’intégration, sélectionnez un système d’exploitation. 

4. Sous **Méthode de déploiement,** sélectionnez une option. Suivez les liens et invites pour intégrer les appareils de votre organisation. Besoin d’aide ? Voir [méthodes d’intégration](#onboarding-methods) (dans cet article).

### <a name="onboarding-methods"></a>Méthodes d’intégration
 
Les méthodes de déploiement varient en fonction du système d’exploitation sélectionné. Reportez-vous aux ressources répertoriées dans le tableau ci-dessous pour obtenir de l’aide sur l’intégration.

| Système d’exploitation  |Méthode  |
|---------|---------|
| Windows 10     | [Stratégie de groupe](configure-endpoints-gp.md)<p>[Gestionnaire de configuration](configure-endpoints-sccm.md)<p>[Gestion des appareils mobiles (Intune)](configure-endpoints-mdm.md)<p>[Script local](configure-endpoints-script.md) <br/>**REMARQUE**: un script local est approprié pour une preuve de concept, mais ne doit pas être utilisé pour le déploiement de production. Pour un déploiement de production, nous vous recommandons d’utiliser la stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune.         |
| Windows 8.1 Entreprise <p>Windows 8.1 Professionnel <p>Windows 7 SP1 Enterprise<p>Windows 7 SP1 Pro     | [Microsoft Monitoring Agent](onboard-downlevel.md)<br/>**REMARQUE**: Microsoft Monitoring Agent est désormais l’agent Azure Log Analytics. Pour en savoir plus, consultez la vue [d’ensemble de l’agent Log Analytics.](/azure/azure-monitor/platform/log-analytics-agent)        |
| Windows Server 2019 et ultérieur<p>Windows Server 2019 Core Edition<p>Windows Server version 1803 et ultérieures | [Script local](configure-endpoints-script.md)<p>[Stratégie de groupe](configure-endpoints-gp.md)<p>[Gestionnaire de configuration](configure-endpoints-sccm.md)<p>[System Center Configuration Manager](configure-endpoints-sccm.md)<p>[Scripts d’intégration VDI pour les appareils non persistants](configure-endpoints-vdi.md) <br/>**REMARQUE**: un script local est approprié pour une preuve de concept, mais ne doit pas être utilisé pour le déploiement de production. Pour un déploiement de production, nous vous recommandons d’utiliser la stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune.    |
| Windows Server 2016 <p>Windows Server 2012 R2<p>Windows Server 2008 R2 SP1  | [Centre de sécurité Microsoft Defender](configure-server-endpoints.md)<p>[Azure Defender](/azure/security-center/security-center-wdatp) |
|macOS :<p>11.3.1 (Big Sur)<p>10.15 (Îles)<p>10.14 (Mojave) |[Intégrer des appareils non Windows](configure-endpoints-non-windows.md)  |
|iOS |[Intégrer des appareils non Windows](configure-endpoints-non-windows.md)  |
|Linux :<p>RHEL 7.2+<p>CentOS Linux 7.2+<p>Ubuntu 16 LTS ou un LTS supérieur<p>SLES 12+<p>Debian 9+<p>Oracle Linux 7.2 |[Intégrer des appareils non Windows](configure-endpoints-non-windows.md)  |

## <a name="run-a-detection-test"></a>Exécuter un test de détection

Pour vérifier que vos appareils intégrés sont correctement connectés à Microsoft Defender pour endpoint, vous pouvez exécuter un test de détection.

|Système d’exploitation  |Aide  |
|---------|---------|
| Windows 10<p>Windows Server 2019 <p>Windows Serveur, version 1803 <p>Windows Server 2016 <p>Windows Server 2012 R2     |Voir [Exécuter un test de détection.](run-detection-test.md) <p>Visitez le site des scénarios de démonstration Microsoft Defender for Endpoint () et essayez un ou [https://demo.wd.microsoft.com](https://demo.wd.microsoft.com) plusieurs des scénarios. Par exemple, essayez le scénario de démonstration **de la protection** livrée par le cloud.         |
|macOS<p>11.3.1 (Big Sur)<p>10.15 (Îles)<p>10.14 (Mojave)     |Téléchargez et utilisez l’application CASER sur [https://aka.ms/mdatpmacosdiy](https://aka.ms/mdatpmacosdiy) . <p>Pour plus d’informations, [voir Microsoft Defender pour Endpoint sur Mac.](microsoft-defender-endpoint-mac.md)        |
|Linux :<p>RHEL 7.2+<p>CentOS Linux 7.2+<p>Ubuntu 16 LTS ou un LTS supérieur<p>SLES 12+<p>Debian 9+<p>Oracle Linux 7.2 |1. Exécutez la commande suivante et recherchez le résultat **1**: <br/>`mdatp health --field real_time_protection_enabled`. <p>2. Ouvrez une fenêtre Terminal et exécutez la commande suivante : <br/>`curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`. <p>3. Exécutez la commande suivante pour lister les menaces détectées : <br/>`mdatp threat list`. <p>Pour plus d’informations, [voir Microsoft Defender pour Endpoint sur Linux.](microsoft-defender-endpoint-linux.md) |

## <a name="confirm-that-microsoft-defender-antivirus-is-in-passive-mode"></a>Vérifier que Antivirus Microsoft Defender est en mode passif

Maintenant que vos points de terminaison ont été intégrés à Defender pour le point de terminaison, l’étape suivante consiste à vous assurer que Antivirus Microsoft Defender est en cours d’exécution en mode passif. Vous pouvez utiliser l’invite de commandes ou PowerShell pour effectuer cette tâche, comme décrit dans le tableau suivant :

|Méthode  |Procédure  |
|---------|---------|
|Invite de commandes     |1. Sur un Windows, ouvrez l’invite de commandes en tant qu’administrateur.<p> 2. `sc query windefend` Tapez, puis appuyez sur Entrée.<p> 3. Examinez les résultats pour vérifier que Antivirus Microsoft Defender est en cours d’exécution en mode passif.         |
|PowerShell     |1. Sur un appareil Windows, ouvrez Windows PowerShell en tant qu’administrateur.<p> 2. Exécutez la cmdlet [Get-MpComputerStatus.](/powershell/module/defender/Get-MpComputerStatus) <p> 3. Dans la liste des résultats, recherchez **AMRunningMode : Mode passif** ou **AMRunningMode : Mode passif SxS**.|

> [!NOTE]
> Vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender *dans* certaines versions de Windows.

### <a name="set-microsoft-defender-antivirus-on-windows-server-to-passive-mode-manually"></a>Définir Antivirus Microsoft Defender sur Windows Server en mode passif manuellement

Pour définir Antivirus Microsoft Defender en mode passif sur Windows Server, version 1803 ou plus récente, ou Windows Server 2019, suivez les étapes suivantes :

1. Ouvrez l’Éditeur du Registre, puis accédez à `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` .

2. Modifiez (ou créez) une entrée DWORD appelée **ForcePassiveMode** et spécifiez les paramètres suivants :

   - Définissez la valeur DWORD sur `1` .
   - Sous **Base,** **sélectionnez Hexadécimal**.
 
   > [!NOTE]
   > Vous pouvez utiliser d’autres méthodes pour définir la clé de Registre, telles que les suivantes :
   > - Préférence de stratégie de groupe
   > - Outil d’objet de stratégie de groupe local
   > - Un package dans Configuration Manager

### <a name="start-microsoft-defender-antivirus-on-windows-server-2016"></a>Démarrer Antivirus Microsoft Defender sur Windows Server 2016

Si vous utilisez Windows Server 2016, vous de devez démarrer Antivirus Microsoft Defender manuellement. Vous pouvez le faire à l’aide de l’cmdlet PowerShell `mpcmdrun.exe -wdenable` sur l’appareil.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Obtenir les mises à jour de Antivirus Microsoft Defender

Le Antivirus Microsoft Defender à jour est essentiel pour garantir que vos appareils disposent des dernières technologies et fonctionnalités nécessaires pour se protéger contre les nouveaux programmes malveillants et les nouvelles techniques d’attaque, même si Antivirus Microsoft Defender s’exécute en mode passif.

Il existe deux types de mises à jour liées à la mise Antivirus Microsoft Defender jour :
- Mises à jour de l’intelligence de la sécurité
- Mises à jour de produit

Pour obtenir vos mises à jour, suivez les instructions de la Antivirus Microsoft Defender mises à jour [et appliquez les lignes de base.](manage-updates-baselines-microsoft-defender-antivirus.md)


## <a name="uninstall-mcafee"></a>Désinstaller Mc Antivirus

Maintenant que vous avez intégré les appareils de votre organisation à Microsoft Defender pour le point de terminaison, l’étape suivante consiste à désinstaller Mc Antivirus. Pour obtenir de l’aide sur cette étape, go to your Mc Antivirus ServicePortal ( [http://mysupport.mcafee.com](http://mysupport.mcafee.com) ).

## <a name="make-sure-defender-for-endpoint-is-working-correctly"></a>Assurez-vous que Defender pour le point de terminaison fonctionne correctement

Maintenant que vous avez désinstallé Mc Antivirus, l’étape suivante consiste à vous assurer que les Antivirus Microsoft Defender et protection évolutive des points de terminaison sont activés et en mode actif.

Pour ce faire, visitez le site de démonstration de Microsoft Defender for Endpoint ( [https://demo.wd.microsoft.com](https://demo.wd.microsoft.com) ). Essayez un ou plusieurs scénarios de démonstration sur cette page, y compris au moins les scénarios suivants :
- Protection fournie par le cloud
- Applications potentiellement indésirables (PUA)
- Protection du réseau (NP)

> [!IMPORTANT]
> Si vous utilisez Windows Server 2016, vous de devez démarrer Antivirus Microsoft Defender manuellement. Vous pouvez le faire à l’aide de l’cmdlet PowerShell `mpcmdrun.exe -wdenable` sur l’appareil.

## <a name="next-steps"></a>Étapes suivantes

**Félicitations**! Vous avez terminé votre [migration de Mc Antivirus vers Microsoft Defender pour le point de terminaison](mcafee-to-microsoft-defender-migration.md#the-migration-process)! 

- [Visitez votre tableau de bord des opérations](security-operations-dashboard.md) de sécurité dans le Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ). 
- [Gérer Microsoft Defender pour le point de terminaison, après la migration.](manage-atp-post-migration.md)
