---
title: Basculer vers Microsoft Defender pour point de terminaison - Configuration
description: Passez à Defender pour point de terminaison. Passez en revue le processus d’installation, qui inclut l’installation de l’antivirus Microsoft Defender.
keywords: migration, Microsoft Defender pour point de terminaison, antivirus, mode passif, processus d’installation
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
ms.date: 08/10/2022
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
- highpri
ms.topic: article
ms.custom: migrationguides
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 39bc16b1e43858741a8c9f93be9cc236805c93d9
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67583559"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-2-setup"></a>Basculer vers Microsoft Defender pour point de terminaison - Phase 2 : Configuration

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![Phase 1 : Préparer.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[Phase 1 : préparation](switch-to-mde-phase-1.md)|![Phase 2 : Configurer.](images/phase-diagrams/setup.png#lightbox)<br/>Phase 2 : configuration|[![Phase 3 : Onboard3.](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[Phase 3 : intégration](switch-to-mde-phase-3.md)|
|---|---|---|
||*Vous êtes là !*||

**Bienvenue dans la phase d’installation du [basculement vers Defender pour point de terminaison](switch-to-mde-overview.md#the-migration-process)**. Cette phase comprend les étapes suivantes :

1. [Réinstallez/activez l’Antivirus Microsoft Defender sur vos points de terminaison](#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).
2. [Configurez Defender pour point de terminaison](#configure-defender-for-endpoint).
3. [Ajoutez Defender pour point de terminaison à la liste d’exclusions de votre solution existante](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).
4. [Ajoutez votre solution existante à la liste d’exclusion pour l’Antivirus Microsoft Defender](#add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus).
5. [Configurez vos groupes d’appareils, regroupements d’appareils et unités d’organisation](#set-up-your-device-groups-device-collections-and-organizational-units).

## <a name="reinstallenable-microsoft-defender-antivirus-on-your-endpoints"></a>Réinstaller/activer l’antivirus Microsoft Defender sur vos points de terminaison

Sur certaines versions de Windows, l’antivirus Microsoft Defender a probablement été désinstallé ou désactivé lorsque votre solution antivirus/anti-programme malveillant non Microsoft a été installée. Lorsque les points de terminaison exécutant Windows sont intégrés à Defender pour point de terminaison, l’Antivirus Microsoft Defender peut s’exécuter en mode passif avec une solution antivirus non Microsoft. Pour en savoir plus, consultez [Protection antivirus avec Defender pour point de terminaison](microsoft-defender-antivirus-compatibility.md#antivirus-protection-without-defender-for-endpoint).

Lorsque vous basculez vers Defender pour point de terminaison, vous devrez peut-être prendre certaines mesures pour réinstaller ou activer l’antivirus Microsoft Defender. Le tableau suivant décrit ce qu’il faut faire sur vos clients et serveurs Windows.

|Type de point de terminaison|Procédure|
|---|---|
|Clients Windows (tels que les points de terminaison exécutant Windows 10 et Windows 11)|En général, vous n’avez pas besoin d’effectuer d’action pour les clients Windows (sauf si l’Antivirus Microsoft Defender a été désinstallé). En général, l’antivirus Microsoft Defender doit toujours être installé, mais il est probablement désactivé à ce stade du processus de migration. <br/><br/> Lorsqu’une solution antivirus/anti-programme malveillant non Microsoft est installée et que les clients ne sont pas encore intégrés à Defender pour point de terminaison, l’antivirus Microsoft Defender est désactivé automatiquement. Plus tard, lorsque les points de terminaison clients sont intégrés à Defender pour point de terminaison, si ces points de terminaison exécutent une solution antivirus non Microsoft, l’Antivirus Microsoft Defender passe en mode passif. <br/><br/> Si la solution antivirus non Microsoft est désinstallée, l’Antivirus Microsoft Defender passe automatiquement en mode actif.|
|Serveurs Windows|Sur Windows Server, vous devez réinstaller l’antivirus Microsoft Defender et le définir manuellement en mode passif. Sur les serveurs Windows, lorsqu’un antivirus/logiciel anti-programme malveillant non Microsoft est installé, l’antivirus Microsoft Defender ne peut pas s’exécuter en même temps que la solution antivirus non-Microsoft. Dans ce cas, l’antivirus Microsoft Defender est désactivé ou désinstallé manuellement. <br/><br/> Pour réinstaller ou activer l’antivirus Microsoft Defender sur Windows Server, effectuez les tâches suivantes : <br/>- [Réactiver l’antivirus Defender sur Windows Server s’il a été désactivé](enable-update-mdav-to-latest-ws.md#re-enable-microsoft-defender-antivirus-on-windows-server-if-it-was-disabled)<br/>- [Réactiver l’antivirus Defender sur Windows Server s’il a été désinstallé](enable-update-mdav-to-latest-ws.md#re-enable-microsoft-defender-antivirus-on-windows-server-if-it-was-uninstalled)<br/>- [Définir l’antivirus Microsoft Defender en mode passif sur Windows Server](#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) <br/><br/>Si vous rencontrez des problèmes lors de la réinstallation ou de la réactivation de Microsoft Defender Antivisrus sur Windows Server, consultez [Résolution des problèmes : l’Antivirus Microsoft Defender est désinstallé sur Windows Server](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server).|

> [!TIP]
> Pour en savoir plus sur les états de l’Antivirus Microsoft Defender avec protection antivirus non-Microsoft, consultez [Compatibilité de l’antivirus Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>Définir l’antivirus Microsoft Defender en mode passif sur Windows Server

> [!TIP]
> Vous pouvez maintenant exécuter l’Antivirus Microsoft Defender en mode passif sur Windows Server 2012 R2 et 2016. Pour plus d’informations, consultez [Options pour installer Microsoft Defender pour point de terminaison](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

1. Ouvrez l’Éditeur du Registre, puis accédez à `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. Modifiez (ou créez) une entrée DWORD appelée **ForceDefenderPassiveMode** et spécifiez les paramètres suivants :

   - Définissez la valeur du DWORD sur **1**.

   - Sous **Base**, sélectionnez **Hexadecimal**.

> [!NOTE]
> Après l’intégration à Defender pour point de terminaison, vous devrez peut-être définir l’antivirus Microsoft Defender en mode passif sur Windows Server. Pour vérifier que le mode passif a été défini comme prévu, recherchez **l’événement 5007** dans le journal **des opérations Microsoft-Windows-Windows Defender** (situé à `C:\Windows\System32\winevt\Logs`) et vérifiez que les clés de Registre **ForceDefenderPassiveMode** ou **PassiveMode** ont été définies sur **0x1**.

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Utilisez-vous Windows Server 2012 R2 ou Windows Server 2016 ?

Vous pouvez maintenant exécuter l’Antivirus Microsoft Defender en mode passif sur Windows Server 2012 R2 et 2016 à l’aide de la méthode ci-dessus. Pour plus d’informations, consultez [Options pour installer Microsoft Defender pour point de terminaison](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

## <a name="configure-defender-for-endpoint"></a>Configurer Microsoft Defender pour point de terminaison

Cette étape du processus de migration implique la configuration de l’antivirus Microsoft Defender pour vos points de terminaison. Nous vous recommandons d’utiliser Intune ; toutefois, vous pouvez utiliser l’une des méthodes répertoriées dans le tableau suivant :

|Méthode|Procédure|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **REMARQUE** : Intune fait désormais partie de Microsoft Endpoint Manager.|1. Accédez au [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) et connectez-vous.<br/><br/>2. Sélectionnez les **profils de configuration** **des appareils**\>, puis sélectionnez le type de profil que vous souhaitez configurer. Si vous n’avez pas encore créé de type de profil **de restrictions** d’appareil ou si vous souhaitez en créer un, consultez [Configurer les paramètres de restriction d’appareil dans Microsoft Intune](/intune/device-restrictions-configure).<br/><br/>3. Sélectionnez **Propriétés**, puis sélectionnez **Paramètres de configuration : Modifier**<br/><br/>4. Développez **l’antivirus Microsoft Defender**.<br/><br/>5. Activer la **protection fournie par le cloud**.<br/><br/>6. Dans la liste **déroulante Inviter les utilisateurs avant la soumission d’exemples** , sélectionnez **Envoyer tous les exemples automatiquement**.<br/><br/>7. Dans la liste **déroulante Détecter les applications potentiellement indésirables** , sélectionnez **Activer** ou **auditer**.<br/><br/>8. Sélectionnez **Vérifier + enregistrer**, puis **sélectionnez Enregistrer**. <br/><br/> **CONSEIL** : Pour plus d’informations sur Intune profils d’appareil, notamment sur la création et la configuration de leurs paramètres, voir [Que sont Microsoft Intune profils d’appareil ?](/intune/device-profiles)|
|[Microsoft Endpoint Configuration Manager](/mem/configmgr)|Consultez [Créer et déployer des stratégies anti-programme malveillant pour Endpoint Protection dans Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies). <br/><br/> Lorsque vous créez et configurez vos stratégies anti-programme malveillant, veillez à passer en revue les [paramètres de protection en temps réel](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) et [à activer le blocage à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md).
|Panneau de configuration dans Windows|Suivez les instructions ici : [Activez l’antivirus Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows). (Vous pouvez voir *Antivirus Windows Defender* au lieu de *l’antivirus Microsoft Defender* dans certaines versions de Windows.)|
|[Advanced stratégie de groupe Management](/microsoft-desktop-optimization-pack/agpm/) <br/><br/> ou <br/><br/> [Console de gestion des stratégies de groupe ](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)|1. Accédez aux **modèles d’administration** de **configuration** \> de l’ordinateur **composants** \> \> Windows **Antivirus Microsoft Defender**.<br/><br/>2. Recherchez une stratégie appelée **Désactiver l’antivirus Microsoft Defender**.<br/><br/>3. Choisissez **Modifier le paramètre de stratégie** et assurez-vous que la stratégie est désactivée. Cette action active l’antivirus Microsoft Defender. <br/>(Vous pouvez voir *Antivirus Windows Defender* au lieu de *l’antivirus Microsoft Defender* dans certaines versions de Windows.)|

> [!TIP]
> Vous pouvez déployer les stratégies avant l’intégration des appareils de votre organisation.

## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution"></a>Ajouter Microsoft Defender pour point de terminaison à la liste d’exclusions pour votre solution existante

Cette étape du processus d’installation implique l’ajout de Defender pour point de terminaison à la liste d’exclusions pour votre solution de protection de point de terminaison existante et tous les autres produits de sécurité que votre organisation utilise.

> [!TIP]
> Pour obtenir de l’aide sur la configuration des exclusions, reportez-vous à la documentation de votre fournisseur de solutions.

Les exclusions spécifiques à configurer dépendent de la version de Windows que vos points de terminaison ou appareils exécutent et sont répertoriées dans le tableau suivant.

| Système d’exploitation |Exclusions |
|:--|:--|
|[Windows 11](/windows/whats-new/windows-11-overview) <br/><br/>Windows 10, [version 1803](/lifecycle/announcements/windows-server-1803-end-of-servicing) ou ultérieure (voir [Windows 10 informations de publication](/windows/release-health/release-information))<br/><br/>Windows 10, version 1703 ou 1709 avec [KB4493441](https://support.microsoft.com/help/4493441) installé <br/><br/> [Windows Server 2022](/windows/release-health/status-windows-server-2022)<br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019) <br/><br/>[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows Server, version 1803](/windows-server/get-started/whats-new-in-windows-server-1803) | `C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\DataCollection`<br/><br/> En outre, sur Windows Server 2012 R2 et 2016 exécutant la solution unifiée moderne, les exclusions suivantes sont requises après la mise à jour du composant Sense EDR à l’aide [de KB5005292](https://support.microsoft.com/en-us/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) :<br/> <br/> `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\MsSense.exe` <br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCnCProxy.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseIR.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCE.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseSampleUploader.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCM.exe`|
|[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<br/><br/>**REMARQUE** : La surveillance des fichiers temporaires de l’hôte 6\45 peut être des sous-dossiers numérotées différents.<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>Ajouter votre solution existante à la liste d’exclusion pour l’antivirus Microsoft Defender

Au cours de cette étape du processus d’installation, vous ajoutez votre solution existante à la liste d’exclusion de l’antivirus Microsoft Defender. Vous pouvez choisir parmi plusieurs méthodes pour ajouter vos exclusions à l’antivirus Microsoft Defender, comme indiqué dans le tableau suivant : 

|Méthode|Procédure|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **REMARQUE** : Intune fait désormais partie de Microsoft Endpoint Manager.|1. Accédez au [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) et connectez-vous.<br/><br/>2. Sélectionnez les **profils de configuration** **des appareils**\>, puis sélectionnez le profil que vous souhaitez configurer.<br/><br/>3. Sous **Gérer**, sélectionnez **Propriétés**.<br/><br/>4. Sélectionnez **Paramètres de configuration : Modifier**.<br/><br/>5. Développez **l’antivirus Microsoft Defender**, puis développez **les exclusions antivirus Microsoft Defender**.<br/><br/>6. Spécifiez les fichiers et dossiers, extensions et processus à exclure des analyses antivirus Microsoft Defender. Pour plus d’informations, consultez [les exclusions de l’Antivirus Microsoft Defender](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions).<br/><br/>7. Choisissez **Vérifier + enregistrer**, puis **sélectionnez Enregistrer**.|
|[Microsoft Endpoint Configuration Manager](/mem/configmgr/)|1. À l’aide de la [console Configuration Manager](/mem/configmgr/core/servers/manage/admin-console), accédez à **Assets and Compliance** \> **Endpoint Protection** \> **Antimalware Policies**, puis sélectionnez la stratégie à modifier.<br/><br/>2. Spécifiez les paramètres d’exclusion pour les fichiers et dossiers, les extensions et les processus à exclure des analyses antivirus Microsoft Defender.|
|[Objet de stratégie de groupe](/previous-versions/windows/desktop/Policy/group-policy-objects)|1. Sur votre ordinateur de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](https://technet.microsoft.com/library/cc731212.aspx), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.<br/><br/>2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à Configuration de l’ordinateur et sélectionnez **Modèles d’administration**.<br/><br/>3. Développez l’arborescence sur **les composants Windows exclusions \> de l’antivirus \> Microsoft Defender**. (Vous pouvez voir *Antivirus Windows Defender* au lieu de *l’antivirus Microsoft Defender* dans certaines versions de Windows.)<br/><br/>4. Double-cliquez sur le paramètre **Exclusions de chemin** et ajoutez les exclusions.<br/><br/>5. Définissez l’option **sur Activé**.<br/><br/>6. Dans la section **Options** , **sélectionnez Afficher...**.<br/><br/>7. Spécifiez chaque dossier sur sa propre ligne sous la colonne **Nom de** la valeur. Si vous spécifiez un fichier, veillez à entrer un chemin d’accès complet au fichier, y compris la lettre de lecteur, le chemin d’accès au dossier, le nom de fichier et l’extension. Entrez **0** dans la colonne **Valeur** .<br/><br/>8. Sélectionnez **OK**.<br/><br/>9. Double-cliquez sur le paramètre **Exclusions d’extension** et ajoutez les exclusions.<br/><br/>10. Définissez l’option **sur Activé**.<br/><br/>11. Sous la section **Options** , **sélectionnez Afficher...**.<br/><br/>12. Entrez chaque extension de fichier sur sa propre ligne sous la colonne **Nom de** valeur. Entrez **0** dans la colonne **Valeur** .<br/><br/>13. Sélectionnez **OK**.|
|Objet de stratégie de groupe local|1. Sur le point de terminaison ou l’appareil, ouvrez l’éditeur de stratégie de groupe local.<br/><br/>2. Accédez à Computer **Configuration** \> **Administrative Templates** \> **Windows Components** \> **Microsoft Defender Antivirus** \> **Exclusions**. (Vous pouvez voir *Antivirus Windows Defender* au lieu de *l’antivirus Microsoft Defender* dans certaines versions de Windows.)<br/><br/>3. Spécifiez vos exclusions de chemin d’accès et de processus.|
|Clé du Registre|1. Exportez la clé de Registre suivante : `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions`.<br/><br/>2. Importez la clé de Registre. Voici deux exemples :<br/>- Chemin d’accès local : `regedit.exe /s c:\temp\MDAV_Exclusion.reg`<br/>- Partage réseau : `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg`|

### <a name="keep-the-following-points-about-exclusions-in-mind"></a>Gardez à l’esprit les points suivants concernant les exclusions

Lorsque vous ajoutez [des exclusions aux analyses de l’Antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus), vous devez ajouter des exclusions de chemin d’accès et de processus.

Gardez à l’esprit les points suivants :

- *Les exclusions de chemin d’accès* excluent des fichiers spécifiques et n’importe quel accès à ces fichiers.
- *Les exclusions* de processus excluent tout ce qu’un processus touche, mais n’excluent pas le processus lui-même.
- Répertoriez vos exclusions de processus en utilisant leur chemin d’accès complet et non par leur nom uniquement. (La méthode name-only est moins sécurisée.)
- Si vous répertoriez chaque exécutable (.exe) comme une exclusion de chemin d’accès et une exclusion de processus, le processus et tout ce qu’il touche sont exclus.

## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>Configurer vos groupes d’appareils, regroupements d’appareils et unités d’organisation

Les groupes d’appareils, les regroupements d’appareils et les unités d’organisation permettent à votre équipe de sécurité de gérer et d’affecter des stratégies de sécurité de manière efficace et efficace. Le tableau suivant décrit chacun de ces groupes et comment les configurer. Votre organisation peut ne pas utiliser les trois types de collections.

|Type de collection|Procédure|
|---|---|
|[Les groupes d’appareils](/microsoft-365/security/defender-endpoint/machine-groups) (anciennement *appelés groupes d’ordinateurs*) permettent à votre équipe chargée des opérations de sécurité de configurer des fonctionnalités de sécurité, telles que l’examen et la correction automatisés. <br/><br/> Les groupes d’appareils sont également utiles pour attribuer l’accès à ces appareils afin que votre équipe des opérations de sécurité puisse prendre des mesures de correction si nécessaire. <br/><br/> Les groupes d’appareils sont créés pendant que l’attaque a été détectée et arrêtée, des alertes, telles qu’une « alerte d’accès initial », ont été déclenchées et affichées dans le [portail Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).|1. Accédez au portail Microsoft 365 Defender (<https://security.microsoft.com>).<br/><br/>2. Dans le volet de navigation à gauche, choisissez **Paramètres Points** \> de **terminaison Autorisations** \>  \> Groupes **d’appareils**.<br/><br/>3. Choisissez **+ Ajouter un groupe d’appareils**.<br/><br/>4. Spécifiez un nom et une description pour le groupe d’appareils.<br/><br/>5. Dans la liste des **niveaux Automation** , sélectionnez une option. (Nous vous recommandons **d’effectuer une correction complète des menaces automatiquement**.) Pour en savoir plus sur les différents niveaux d’automatisation, consultez [comment les menaces sont corrigées](/microsoft-365/security/defender-endpoint/automated-investigations#how-threats-are-remediated).<br/><br/>6. Spécifiez les conditions d’une règle de correspondance pour déterminer quels appareils appartiennent au groupe d’appareils. Par exemple, vous pouvez choisir un domaine, des versions du système d’exploitation ou même utiliser [des balises d’appareil](/microsoft-365/security/defender-endpoint/machine-tags).<br/><br/>7. Sous **l’onglet Accès utilisateur** , spécifiez les rôles qui doivent avoir accès aux appareils inclus dans le groupe d’appareils.<br/><br/>8. Choisissez **Terminé**.|
|[Les regroupements d’appareils](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) permettent à votre équipe chargée des opérations de sécurité de gérer les applications, de déployer des paramètres de conformité ou d’installer des mises à jour logicielles sur les appareils de votre organisation. <br/><br/> Les collections d’appareils sont créées à l’aide [de Configuration Manager](/mem/configmgr/).|Suivez les étapes décrites dans [Créer une collection](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create).|
|[Les unités organisationnelles](/azure/active-directory-domain-services/create-ou) vous permettent de regrouper logiquement des objets tels que des comptes d’utilisateur, des comptes de service ou des comptes d’ordinateur. <br/><br/> Vous pouvez ensuite affecter des administrateurs à des unités d’organisation spécifiques et appliquer une stratégie de groupe pour appliquer des paramètres de configuration ciblés. <br/><br/> Les unités organisationnelles sont définies dans [Azure services de domaine Active Directory](/azure/active-directory-domain-services).|Suivez les étapes décrites dans [Créer une unité organisationnelle dans un domaine managé Azure services de domaine Active Directory](/azure/active-directory-domain-services/create-ou).|

## <a name="next-step"></a>Étape suivante

**Félicitations**! Vous avez terminé la phase d’installation [du basculement vers Defender pour point de terminaison](switch-to-mde-overview.md#the-migration-process) !

- [Passer à la phase 3 : Intégration à Defender pour point de terminaison](switch-to-mde-phase-3.md)
