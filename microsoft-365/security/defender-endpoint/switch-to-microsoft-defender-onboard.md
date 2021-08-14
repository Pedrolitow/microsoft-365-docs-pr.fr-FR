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
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
ms.custom: migrationguides
ms.topic: article
ms.date: 06/14/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 3faa24c8d28fb7f6d8182d58f573679da8c9fb5506d4bd4c5c8b02daeff63549
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53817616"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-3-onboard"></a>Basculer vers Microsoft Defender pour le point de terminaison - Phase 3 : Intégration

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| [![Phase 1 : Préparer3](images/phase-diagrams/prepare.png)](switch-to-microsoft-defender-prepare.md)<br/>[Phase 1 : préparation](switch-to-microsoft-defender-prepare.md) | [![Phase 2 : configuration](images/phase-diagrams/setup.png)](switch-to-microsoft-defender-setup.md)<br/>[Phase 2 : configuration](switch-to-microsoft-defender-setup.md) | ![Phase 3 : intégration](images/phase-diagrams/onboard.png)<br/>Phase 3 : intégration |
|--|--|--|
|| |*Vous êtes là !* |


**Bienvenue dans la phase 3 du [passage à Defender pour Point de terminaison.](switch-to-microsoft-defender-migration.md#the-migration-process)** Cette phase de migration comprend les étapes suivantes :

1. [Intégrer des appareils à Defender pour le point de terminaison.](#onboard-devices-to-microsoft-defender-for-endpoint)
2. [Exécutez un test de détection.](#run-a-detection-test)
3. [Confirmez que Antivirus Microsoft Defender est en mode passif sur vos points de terminaison.](#confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints)
4. [Obtenir les mises à jour de Antivirus Microsoft Defender](#get-updates-for-microsoft-defender-antivirus).
5. [Désinstallez votre solution non-Microsoft.](#uninstall-your-non-microsoft-solution) 
6. [Assurez-vous que Defender pour le point de terminaison fonctionne correctement.](#make-sure-defender-for-endpoint-is-working-correctly)

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Intégrer des appareils à Microsoft Defender pour point de terminaison

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.

2. Choisissez **Paramètres**  >  **l’intégration des points de**  >  **terminaison** (sous **Gestion des appareils).** 

3. Dans la **liste Sélectionner le système d’exploitation pour démarrer le** processus d’intégration, sélectionnez un système d’exploitation. 

4. Sous **Méthode de déploiement,** sélectionnez une option. Suivez les liens et invites pour intégrer les appareils de votre organisation. Besoin d'aide ? Voir [méthodes d’intégration](#onboarding-methods) (dans cet article).

### <a name="onboarding-methods"></a>Méthodes d’intégration
 
Les méthodes de déploiement varient en fonction du système d’exploitation et des méthodes préférées. Le tableau suivant répertorie les ressources pour vous aider à intégrer Defender pour Endpoint :

|Systèmes d’exploitation  |Méthodes  |
|---------|---------|
| Windows 10     | [Stratégie de groupe](configure-endpoints-gp.md)<p>[Gestionnaire de configuration](configure-endpoints-sccm.md)<p>[Gestion des appareils mobiles (Intune)](configure-endpoints-mdm.md)<p>[Script local](configure-endpoints-script.md) <p>**REMARQUE**: un script local est approprié pour une preuve de concept, mais ne doit pas être utilisé pour le déploiement de production. Pour un déploiement de production, nous vous recommandons d’utiliser la stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune.         |
| Windows 8.1 Entreprise <p>Windows 8.1 Professionnel <p>Windows 7 SP1 Enterprise <p>Windows 7 SP1 Pro     | [Microsoft Monitoring Agent](onboard-downlevel.md)<p>**REMARQUE**: Microsoft Monitoring Agent est désormais l’agent Azure Log Analytics. Pour en savoir plus, consultez la vue [d’ensemble de l’agent Log Analytics.](/azure/azure-monitor/platform/log-analytics-agent)        |
| Windows Server 2019 et ultérieur <p>Windows Server 2019 Core Edition <p>Windows Server version 1803 et ultérieures | [Script local](configure-endpoints-script.md) <p>[Stratégie de groupe](configure-endpoints-gp.md) <p>[Gestionnaire de configuration](configure-endpoints-sccm.md) <p>[System Center Configuration Manager](configure-endpoints-sccm.md) <p>[Scripts d’intégration VDI pour les appareils non persistants](configure-endpoints-vdi.md) <p>**REMARQUE**: un script local est approprié pour une preuve de concept, mais ne doit pas être utilisé pour le déploiement de production. Pour un déploiement de production, nous vous recommandons d’utiliser la stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune.    |
| Windows Server 2016 <p>Windows Server 2012 R2 <p>Windows Server 2008 R2 SP1  | [Portail Microsoft 365 Defender](configure-server-endpoints.md)<p>[Azure Defender](/azure/security-center/security-center-wdatp) |
| macOS :<p>11.3.1 (Big Sur) <p>10.15 (Îles)<p>10.14 (Mojave) | [Intégrer des appareils non Windows](configure-endpoints-non-windows.md)  |
| iOS | [Intégrer des appareils non Windows](configure-endpoints-non-windows.md)  |
| Linux :<p>RHEL 7.2+<p>CentOS Linux 7.2+<p>Ubuntu 16 LTS ou un LTS supérieur<p>SLES 12+<p>Debian 9+<p>Oracle Linux 7.2 | [Intégrer des appareils non Windows](configure-endpoints-non-windows.md)  |

## <a name="run-a-detection-test"></a>Exécuter un test de détection

Pour vérifier que vos appareils intégrés sont correctement connectés à Defender for Endpoint, vous pouvez exécuter un test de détection.

|Système d’exploitation  |Aide  |
|---------|---------|
| Windows 10 <p>Windows Server 2019 <p>Windows Serveur, version 1803 <p>Windows Server 2016 <p>Windows Server 2012 R2     | Voir [Exécuter un test de détection.](run-detection-test.md) <p>Visitez le site de démonstration Defender for Endpoint () et essayez un ou [https://demo.wd.microsoft.com](https://demo.wd.microsoft.com) plusieurs des scénarios. Par exemple, essayez le scénario de démonstration **de la protection** livrée par le cloud.    |
| macOS :<p>11.3.1 (Big Sur) <p>10.15 (Îles)<p>10.14 (Mojave)    | Téléchargez et utilisez l’application CASER sur [https://aka.ms/mdatpmacosdiy](https://aka.ms/mdatpmacosdiy) . <p>Pour plus d’informations, [voir Defender pour point de terminaison sur macOS.](microsoft-defender-endpoint-mac.md)        |
| Linux :<p>RHEL 7.2+<p>CentOS Linux 7.2+<p>Ubuntu 16 LTS ou un LTS supérieur<p>SLES 12+<p>Debian 9+<p>Oracle Linux 7.2 | 1. Exécutez la commande suivante et recherchez le résultat **1**: <br/>`mdatp health --field real_time_protection_enabled`. <p>2. Ouvrez une fenêtre Terminal et exécutez la commande suivante : <br/>`curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`. <p>3. Exécutez la commande suivante pour lister les menaces détectées : <br/>`mdatp threat list`. <p>Pour plus d’informations, [voir Defender for Endpoint sur Linux.](microsoft-defender-endpoint-linux.md) |

## <a name="confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints"></a>Vérifier que Antivirus Microsoft Defender est en mode passif sur vos points de terminaison

Maintenant que vos points de terminaison ont été intégrés à Defender pour le point de terminaison, l’étape suivante consiste à vous assurer que Antivirus Microsoft Defender est en cours d’exécution en mode passif. Vous pouvez utiliser l’invite de commandes ou PowerShell pour effectuer cette tâche, comme décrit dans le tableau suivant :

| Méthode  | Procédure  |
|:-------|:-------|
|Invite de commandes     | 1. Sur un Windows, ouvrez l’invite de commandes en tant qu’administrateur.<p>2. `sc query windefend` Tapez, puis appuyez sur Entrée.<p>3. Examinez les résultats pour vérifier que Antivirus Microsoft Defender est en cours d’exécution en mode passif.         |
| PowerShell     | 1. Sur un appareil Windows, ouvrez Windows PowerShell en tant qu’administrateur.<p>2. Exécutez la cmdlet [Get-MpComputerStatus.](/powershell/module/defender/Get-MpComputerStatus) <p>3. Dans la liste des résultats, recherchez **AMRunningMode : Mode passif** ou **AMRunningMode : Mode passif SxS**.    |

> [!NOTE]
> Vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender *dans* certaines versions de Windows.

### <a name="set-microsoft-defender-antivirus-on-windows-server-to-passive-mode-manually"></a>Définir Antivirus Microsoft Defender sur Windows Server en mode passif manuellement

Pour définir Antivirus Microsoft Defender en mode passif sur Windows Server, version 1803 ou plus récente, ou Windows Server 2019, suivez les étapes suivantes :

1. Ouvrez l’Éditeur du Registre, puis accédez à <br/>
   `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. Modifiez (ou créez) une entrée DWORD appelée **ForceDefenderPassiveMode** et spécifiez les paramètres suivants :
   - Définissez la valeur DWORD sur **1**.
   - Sous **Base,** **sélectionnez Hexadécimal**.

> [!NOTE]
> Vous pouvez utiliser d’autres méthodes pour définir la clé de Registre, telles que les suivantes :
>- [Préférence de stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn581922(v=ws.11))
>- [Outil d’objet de stratégie de groupe local](/windows/security/threat-protection/security-compliance-toolkit-10#what-is-the-local-group-policy-object-lgpo-tool)
>- [Un package dans Configuration Manager](/mem/configmgr/apps/deploy-use/packages-and-programs)

### <a name="start-microsoft-defender-antivirus-on-windows-server-2016"></a>Démarrer Antivirus Microsoft Defender sur Windows Server 2016

Si vous utilisez Windows Server 2016, vous de devez démarrer Antivirus Microsoft Defender manuellement. Vous pouvez le faire à l’aide de l’cmdlet PowerShell `mpcmdrun.exe -wdenable` sur l’appareil.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Obtenir les mises à jour de Antivirus Microsoft Defender

Le Antivirus Microsoft Defender à jour est essentiel pour garantir que vos appareils disposent des dernières technologies et fonctionnalités nécessaires pour se protéger contre les nouveaux programmes malveillants et les nouvelles techniques d’attaque, même si Antivirus Microsoft Defender s’exécute en mode passif. (Voir [Antivirus Microsoft Defender compatibilité.)](microsoft-defender-antivirus-compatibility.md)

Il existe deux types de mises à jour liées à la mise Antivirus Microsoft Defender jour :

- Mises à jour de l’intelligence de la sécurité
- Mises à jour de produit

Pour obtenir vos mises à jour, suivez les instructions de la Antivirus Microsoft Defender mises à jour [et appliquez les lignes de base.](manage-updates-baselines-microsoft-defender-antivirus.md)

## <a name="uninstall-your-non-microsoft-solution"></a>Désinstaller votre solution non-Microsoft

Si, à ce stade, vous avez :

- Les appareils de votre organisation ont été intégrés à Defender for Endpoint, et 
- Antivirus Microsoft Defender est installé et activé, 

Ensuite, l’étape suivante consiste à désinstaller votre solution de protection de point de terminaison non-Microsoft. 

Pour obtenir de l’aide sur cette tâche, faites-en la recherche auprès de l’équipe de support technique de votre fournisseur de solutions.

## <a name="make-sure-defender-for-endpoint-is-working-correctly"></a>Assurez-vous que Defender pour le point de terminaison fonctionne correctement

Maintenant que vous avez intégré Defender pour le point de terminaison et que vous avez désinstallé votre ancienne solution non-Microsoft, l’étape suivante consiste à vous assurer que Defender pour le point de terminaison fonctionne correctement. Une bonne façon de le faire consiste à visiter le site de démonstration Defender for Endpoint ( [https://demo.wd.microsoft.com](https://demo.wd.microsoft.com) ). Essayez un ou plusieurs scénarios de démonstration sur cette page, y compris au moins les scénarios suivants :

- Protection fournie par le cloud
- Applications potentiellement indésirables (PUA)
- Protection du réseau (NP)

## <a name="next-steps"></a>Prochaines étapes

**Félicitations**! Vous avez terminé votre [migration vers Defender pour endpoint](switch-to-microsoft-defender-migration.md#the-migration-process)! 

- [Visitez votre tableau de bord des opérations](security-operations-dashboard.md) de sécurité dans le portail Microsoft 365 Defender ( [https://security.microsoft.com](https://security.microsoft.com) ). 
- [Gérer Defender pour le point de terminaison, après la migration.](manage-atp-post-migration.md)
