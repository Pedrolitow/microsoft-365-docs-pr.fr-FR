---
title: Basculer vers Microsoft Defender pour point de terminaison - Intégrer
description: Passez à Microsoft Defender pour point de terminaison. Intégrer des appareils, puis désinstaller votre solution non-Microsoft.
keywords: migration, Microsoft Defender pour point de terminaison, edr
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- highpri
ms.custom:
- migrationguides
- admindeeplinkDEFENDER
ms.topic: article
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: d675fc32d0fc60e4d0752a10fd9a7de83abe6f1d
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67583537"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-3-onboard"></a>Basculer vers Microsoft Defender pour point de terminaison - Phase 3 : Intégration

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| [![Phase 1 : Préparer 3.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[Phase 1 : préparation](switch-to-mde-phase-1.md) | [![Phase 2 : configuration](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[Phase 2 : configuration](switch-to-mde-phase-2.md) | ![Phase 3 : intégration](images/phase-diagrams/onboard.png#lightbox)<br/>Phase 3 : intégration |
|--|--|--|
|| |*Vous êtes là !* |

**Bienvenue dans la phase 3 du [basculement vers Defender pour point de terminaison](switch-to-mde-overview.md#the-migration-process)**. Cette phase de migration comprend les étapes suivantes :

1. [Intégrer des appareils à Defender pour point de terminaison](#onboard-devices-to-microsoft-defender-for-endpoint).
2. [Exécutez un test de détection](#run-a-detection-test).
3. [Vérifiez que l’Antivirus Microsoft Defender est en mode passif sur vos points de terminaison](#confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints).
4. [Obtenez les mises à jour de l’antivirus Microsoft Defender](#get-updates-for-microsoft-defender-antivirus).
5. [Désinstallez votre solution non-Microsoft](#uninstall-your-non-microsoft-solution).
6. [Vérifiez que Defender pour point de terminaison fonctionne correctement](#make-sure-defender-for-endpoint-is-working-correctly).

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Intégrer des appareils à Microsoft Defender pour point de terminaison

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Choisissez **l’intégration des** \> points **de terminaison** **de paramètres** \> (sous **Gestion des appareils**).

3. Dans la liste **sélectionner un système d’exploitation pour commencer à intégrer la** liste des processus, sélectionnez un système d’exploitation.

4. Sous **Méthode de déploiement**, sélectionnez une option. Suivez les liens et les invites pour intégrer les appareils de votre organisation. Besoin d’aide ? Consultez [méthodes d’intégration](#onboarding-methods) (dans cet article).

> [!NOTE]
> Si un problème se produit lors de l’intégration, consultez [Résolution des problèmes d’intégration Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md). Cet article explique comment résoudre les problèmes d’intégration et les erreurs courantes sur les points de terminaison.

### <a name="onboarding-methods"></a>Méthodes d'embarquement

> [!IMPORTANT]
> Si vous utilisez Microsoft Defender pour le cloud, consultez [Intégration à Microsoft Defender pour cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud).

Les méthodes de déploiement varient en fonction du système d’exploitation et des méthodes préférées. Le tableau suivant répertorie les ressources à intégrer à Defender pour point de terminaison :

|Systèmes d’exploitation  |Méthodes  |
|---------|---------|
|Windows 10 ou version ultérieure<br/><br/>Windows Server 2019 ou version ultérieure<br/><br/>Windows Server, version 1803 ou ultérieure<br/><br/>Windows Server 2012 R2 et 2016<sup>[[1](#fn1)]<sup>  |   [Script local (jusqu’à 10 appareils)](configure-endpoints-script.md)<br><br/>   [Stratégie de groupe](configure-endpoints-gp.md)<br/><br/>[Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)<br/><br/>[Microsoft Endpoint Manager/Mobile Gestion des appareils (Intune)](configure-endpoints-mdm.md)<br>    [Scripts VDI](configure-endpoints-vdi.md) <br><br> **REMARQUE** : Un script local convient à une preuve de concept, mais ne doit pas être utilisé pour le déploiement en production. Pour un déploiement de production, nous vous recommandons d’utiliser stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune. |
|Windows Server 2008 R2 SP1 | [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma)  ou [Microsoft Defender pour le cloud](/azure/security-center/security-center-wdatp) <br><br> **REMARQUE** : Microsoft Monitoring Agent est désormais l’agent Azure Log Analytics. Pour en savoir plus, consultez [la vue d’ensemble de l’agent Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).  |
|Windows 8.1 Entreprise<br/><br/>Windows 8.1 Professionnel<br/><br/>Windows 7 SP1 Professionnel<br/><br/>Windows 7 SP1| [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br><br> **REMARQUE** : Microsoft Monitoring Agent est désormais l’agent Azure Log Analytics. Pour en savoir plus, consultez [la vue d’ensemble de l’agent Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).  
| macOS (voir [Configuration requise](microsoft-defender-endpoint-mac.md) | [Script local](mac-install-manually.md)<br/><br/>[Microsoft Endpoint Manager](mac-install-with-intune.md)<br/><br/>[JAMF Pro](mac-install-with-jamf.md)<br/><br/>[Gestion des appareils mobiles](mac-install-with-other-mdm.md)   |
| Linux (voir [Configuration système requise](microsoft-defender-endpoint-linux.md#system-requirements)) |  [Script local](linux-install-manually.md) <br><br/> [Marionnette](linux-install-with-puppet.md) <br><br/> [Ansible](linux-install-with-ansible.md)|  
| iOS | [Microsoft Endpoint Manager](ios-install.md)     |
|Android  | [Microsoft Endpoint Manager](android-intune.md)  | 

(<a id="fn1">1</a>) Windows Server 2016 et Windows Server 2012 R2 doivent être intégrés à l’aide des instructions fournies dans [les serveurs Windows intégrés](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

## <a name="run-a-detection-test"></a>Exécuter un test de détection

Pour vérifier que vos appareils intégrés sont correctement connectés à Defender pour point de terminaison, vous pouvez exécuter un test de détection.

|Système d’exploitation|Aide|
|---|---|
|Windows 10 ou version ultérieure<br/><br/>Windows Server 2022<br/><br/>Windows Server 2019<br/><br/>Windows Server, version 1803 ou ultérieure<br/><br/>Windows Server 2016<br/><br/>Windows Server 2012 R2|Consultez [Exécuter un test de détection](run-detection-test.md).|
|macOS (voir [Configuration requise](microsoft-defender-endpoint-mac.md)|Téléchargez et utilisez l’application DIY à l’adresse <https://aka.ms/mdatpmacosdiy>. <br/><br/> Pour plus d’informations, consultez [Defender pour point de terminaison sur macOS](microsoft-defender-endpoint-mac.md).|
|Linux (voir [Configuration système requise](microsoft-defender-endpoint-linux.md#system-requirements))|1. Exécutez la commande suivante et recherchez un résultat de **1** : `mdatp health --field real_time_protection_enabled`.<br/><br/>2. Ouvrez une fenêtre terminal et exécutez la commande suivante : `curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`.<br/><br/>3. Exécutez la commande suivante pour répertorier toutes les menaces détectées : `mdatp threat list`.<br/><br/>Pour plus d’informations, consultez [Defender pour point de terminaison sur Linux](microsoft-defender-endpoint-linux.md).|

## <a name="confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints"></a>Vérifiez que l’Antivirus Microsoft Defender est en mode passif sur vos points de terminaison

Maintenant que vos points de terminaison ont été intégrés à Defender pour point de terminaison, l’étape suivante consiste à vous assurer que l’Antivirus Microsoft Defender s’exécute en mode passif. Vous pouvez utiliser l’une des méthodes suivantes, comme décrit dans le tableau suivant :

|Méthode|Procédure|
|---|---|
|Invite de commandes|1. Sur un appareil Windows, ouvrez l’invite de commandes.<br/><br/>2. Tapez `sc query windefend`, puis appuyez sur Entrée.<br/><br/>3. Passez en revue les résultats pour vérifier que l’Antivirus Microsoft Defender s’exécute en mode passif.|
|PowerShell|1. Sur un appareil Windows, ouvrez Windows PowerShell en tant qu’administrateur.<br/><br/>2. Exécutez l’applet de commande PowerShell suivante : `Get-MpComputerStatus|select AMRunningMode`. <br/><br/>3. Passez en revue les résultats. Le **mode passif** doit s’afficher.|
|Ouvrez l’application Sécurité Windows.|1. Sur un appareil Windows, ouvrez l’application Sécurité Windows.<br/><br/>2. Sélectionnez **Virus & protection contre les menaces**.<br/><br/>3. Sous **Qui me protège ?** **sélectionnez Gérer les fournisseurs**.<br/><br/>4. Dans la page **Fournisseurs de sécurité** , sous **Antivirus**, recherchez **l’antivirus Microsoft Defender activé**.|
|Gestionnaire des tâches|1. Sur un appareil Windows, ouvrez l’application Gestionnaire de tâches.<br/><br/>2. Sélectionnez l’onglet **Détails** . Recherchez **MsMpEng.exe** dans la liste.|

> [!NOTE]
> Vous pouvez voir *Antivirus Windows Defender* au lieu de *l’antivirus Microsoft Defender* dans certaines versions de Windows.
> Pour en savoir plus sur le mode passif et le mode actif, consultez [Plus d’informations sur les états de l’Antivirus Microsoft Defender](microsoft-defender-antivirus-compatibility.md#more-details-about-microsoft-defender-antivirus-states).

### <a name="set-microsoft-defender-antivirus-on-windows-server-to-passive-mode-manually"></a>Définir manuellement l’antivirus Microsoft Defender sur Windows Server en mode passif

Pour définir l’antivirus Microsoft Defender en mode passif sur Windows Server, version 1803 ou ultérieure, ou Windows Server 2019 ou Windows Server 2022, procédez comme suit :

1. Ouvrez l’Éditeur du Registre, puis accédez à `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. Modifiez (ou créez) une entrée DWORD appelée **ForceDefenderPassiveMode** et spécifiez les paramètres suivants :

   - Définissez la valeur du DWORD sur **1**.

   - Sous **Base**, sélectionnez **Hexadecimal**.

> [!NOTE]
> Vous pouvez utiliser d’autres méthodes pour définir la clé de Registre, par exemple :
>
> - [préférence stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn581922(v=ws.11))
> - [Outil d’objet stratégie de groupe local](/windows/security/threat-protection/security-compliance-toolkit-10#what-is-the-local-group-policy-object-lgpo-tool)
> - [Un package dans Configuration Manager](/mem/configmgr/apps/deploy-use/packages-and-programs)

### <a name="start-microsoft-defender-antivirus-on-windows-server-2016"></a>Démarrer l’Antivirus Microsoft Defender sur Windows Server 2016

Si vous utilisez Windows Server 2016, vous devrez peut-être démarrer l’Antivirus Microsoft Defender manuellement. Vous pouvez effectuer cette tâche à l’aide de l’applet `mpcmdrun.exe -wdenable` de commande PowerShell sur l’appareil.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Obtenir des mises à jour pour l’antivirus Microsoft Defender

Il est essentiel de maintenir l’Antivirus Microsoft Defender à jour pour garantir que vos appareils disposent des dernières technologies et fonctionnalités nécessaires pour se protéger contre les nouveaux programmes malveillants et les nouvelles techniques d’attaque, même si l’antivirus Microsoft Defender s’exécute en mode passif. (Voir [Compatibilité de l’Antivirus Microsoft Defender](microsoft-defender-antivirus-compatibility.md).)

Il existe deux types de mises à jour liées à la mise à jour des Antivirus Microsoft Defender :

- Mises à jour de la veille de sécurité

- Mises à jour de produit

Pour obtenir vos mises à jour, suivez les instructions fournies dans [Gérer les mises à jour de l’Antivirus Microsoft Defender et appliquez des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="uninstall-your-non-microsoft-solution"></a>Désinstaller votre solution non-Microsoft

Si, à ce stade, vous avez :

- Intégration des appareils de votre organisation à Defender pour point de terminaison, et

- L’antivirus Microsoft Defender est installé et activé,

Ensuite, l’étape suivante consiste à désinstaller votre solution antivirus, anti-programme malveillant et protection des points de terminaison non Microsoft. Lorsque vous désinstallez votre solution non-Microsoft, l’Antivirus Microsoft Defender passe du mode passif au mode actif. Dans la plupart des cas, cela se produit automatiquement. 

> [!IMPORTANT]
> Si, pour une raison quelconque, l’Antivirus Microsoft Defender ne passe pas en mode actif une fois que vous avez désinstallé votre solution antivirus/anti-programme malveillant non Microsoft, consultez [l’antivirus Microsoft Defender qui semble être bloqué en mode passif](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode).

Pour obtenir de l’aide sur la désinstallation de votre solution non-Microsoft, contactez son équipe de support technique.

## <a name="make-sure-defender-for-endpoint-is-working-correctly"></a>Vérifiez que Defender pour point de terminaison fonctionne correctement

Maintenant que vous êtes intégré à Defender pour point de terminaison et que vous avez désinstallé votre ancienne solution non-Microsoft, l’étape suivante consiste à vous assurer que Defender pour point de terminaison fonctionne correctement. 

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **l’inventaire des appareils des points de terminaison** > . Là, vous pourrez voir l’état de protection des appareils.

Pour plus d’informations, consultez [l’inventaire des appareils](machines-view-overview.md).

## <a name="next-steps"></a>Prochaines étapes

**Félicitations**! Vous avez terminé votre [migration vers Defender pour point de terminaison](switch-to-mde-overview.md#the-migration-process) !

- [Visitez votre tableau de bord des opérations de sécurité](security-operations-dashboard.md) dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)).

- [Gérer Defender pour point de terminaison, après la migration](manage-mde-post-migration.md).
