---
title: Basculer vers Microsoft Defender pour le point de terminaison - Installation
description: Phase 2, le processus de configuration, lors du basculement vers Microsoft Defender pour point de terminaison.
keywords: migration, Microsoft Defender pour point de terminaison, edr, Windows Defender
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
ms.topic: article
ms.custom: migrationguides
ms.date: 08/11/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 98aaf120b2c9357f53bbc21b2e6e994a76877e8d
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58247461"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-2-setup"></a>Basculer vers Microsoft Defender pour le point de terminaison - Phase 2 : Installation

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![Phase 1 : préparation](images/phase-diagrams/prepare.png)](switch-to-microsoft-defender-prepare.md)<br/>[Phase 1 : préparation](switch-to-microsoft-defender-prepare.md) |![Phase 2 : configuration](images/phase-diagrams/setup.png)<br/>Phase 2 : configuration |[![Phase 3 : Intégration3](images/phase-diagrams/onboard.png)](switch-to-microsoft-defender-onboard.md)<br/>[Phase 3 : intégration](switch-to-microsoft-defender-onboard.md) |
|--|--|--|
||*Vous êtes là !* | |

**Bienvenue dans la phase d’installation [du basculement vers Defender pour endpoint.](switch-to-microsoft-defender-migration.md#the-migration-process)** Cette phase comprend les étapes suivantes :

1. [Réinstallez/activez Antivirus Microsoft Defender sur vos points de terminaison.](#reinstallenable-microsoft-defender-antivirus-on-your-endpoints)
2. [Configurez Defender pour le point de terminaison.](#configure-defender-for-endpoint)
3. [Ajoutez Defender pour le point de terminaison à la liste d’exclusions de votre solution existante.](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution)
4. [Ajoutez votre solution existante à la liste d’exclusions pour Antivirus Microsoft Defender](#add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus).
5. [Configurer vos groupes d’appareils, collections d’appareils et unités d’organisation.](#set-up-your-device-groups-device-collections-and-organizational-units)


## <a name="reinstallenable-microsoft-defender-antivirus-on-your-endpoints"></a>Réinstaller/activer Antivirus Microsoft Defender sur vos points de terminaison

Sur certaines versions de Windows, Antivirus Microsoft Defender a probablement été désinstallé ou désactivé lors de l’installation de votre solution antivirus/anti-programme malveillant non-Microsoft. Sauf et jusqu’à ce que les appareils soient intégrés à Defender for Endpoint, Antivirus Microsoft Defender ne s’exécute pas en mode actif avec une solution antivirus non Microsoft. Pour plus d’informations, consultez [Compatibilité Antivirus Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

Maintenant que vous envisagez de basculer vers Defender pour le point de terminaison, vous devrez peut-être prendre certaines mesures pour réinstaller ou activer Antivirus Microsoft Defender. 


| Type de point de terminaison  | Procédure  |
|---------|---------|
| Windows clients (tels que les points de terminaison Windows 10)     | En règle générale, vous n’avez pas besoin d’agir pour Windows clients (sauf si Antivirus Microsoft Defender a été désinstallé). Voici pourquoi : <br/><br/>Antivirus Microsoft Defender doit toujours être installé, mais est probablement désactivé à ce stade du processus de migration.<br/><br/> Lorsqu’une solution antivirus/anti-programme malveillant non-Microsoft est installée et que les clients ne sont pas encore intégrés à Defender for Endpoint, Antivirus Microsoft Defender est désactivé automatiquement. <br/><br/>Plus tard, lorsque les points de terminaison clients sont intégrés à Defender pour point de terminaison, si ces points de terminaison exécutent une solution antivirus non Microsoft, Antivirus Microsoft Defender passe en mode passif. <br/><br/>Si la solution antivirus non-Microsoft est désinstallée, Antivirus Microsoft Defender passe automatiquement en mode actif.  |
| Windows serveurs     | Sur Windows Server, vous devez réinstaller Antivirus Microsoft Defender et le définir manuellement en mode passif. Voici pourquoi : <br/><br/>Sur Windows serveurs, lorsqu’un antivirus/logiciel anti-programme malveillant non-Microsoft est installé, Antivirus Microsoft Defender ne peut pas s’exécuter avec la solution antivirus non Microsoft. Dans ce cas, Antivirus Microsoft Defender est désactivé ou désinstallé manuellement. <br/><br/>Pour réinstaller ou activer Antivirus Microsoft Defender sur Windows Server, effectuez les tâches suivantes : <br/><br/>- [Définir DisableAntiSpyware sur false sur Windows Server](#set-disableantispyware-to-false-on-windows-server) (uniquement si nécessaire)<br/>- [Réinstaller Antivirus Microsoft Defender sur Windows Server](#reinstall-microsoft-defender-antivirus-on-windows-server)<br/>- [Définir Antivirus Microsoft Defender en mode passif sur Windows Server](#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server)       |


> [!TIP]
> Pour en savoir plus sur Antivirus Microsoft Defender états avec la protection antivirus non Microsoft, voir [Antivirus Microsoft Defender compatibilité.](microsoft-defender-antivirus-compatibility.md)

### <a name="set-disableantispyware-to-false-on-windows-server"></a>Définir DisableAntiSpyware sur false sur Windows Server

La clé de Registre [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) a été utilisée dans le passé pour désactiver Antivirus Microsoft Defender et déployer un autre produit antivirus, tel que Mc Symantec, etc. **En règle générale, vous ne devez pas avoir cette** clé de Registre sur vos Windows et points de terminaison ; toutefois, si *vous avez* configuré, voici comment définir sa valeur `DisableAntiSpyware` sur false :

1. Sur votre Windows server, ouvrez l’Éditeur du Registre.

2. Naviguer vers`HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`.

3. Dans ce dossier, recherchez une entrée DWORD appelée **DisableAntiSpyware**.
   - Si vous ne voyez pas cette entrée, vous êtes prêt.
   - Si vous voyez **DisableAntiSpyware,** procédez à l’étape 4.

4. Cliquez avec le bouton droit sur la DWORD DisableAntiSpyware, puis choisissez **Modifier**.

5. Définissez la valeur sur `0` . (Cette action définit la valeur de la clé de Registre sur *false*.)

> [!TIP]
> Pour en savoir plus sur cette clé de Registre, voir [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware).

### <a name="reinstall-microsoft-defender-antivirus-on-windows-server"></a>Réinstaller Antivirus Microsoft Defender sur Windows Server

> [!IMPORTANT]
> La procédure suivante s’applique uniquement aux points de terminaison ou appareils qui exécutent les versions de Windows :
> - Windows Server 2019
> - Windows Serveur, version 1803 (mode principal uniquement)
> - Windows Server 2016 (voir la section suivante, [Utilisez-vous Windows Server 2016 ?](#are-you-using-windows-server-2016))

1. En tant qu’administrateur local sur le point de terminaison ou l’appareil, ouvrez Windows PowerShell.

2. Exécutez les cmdlets PowerShell suivantes : <br/>   

   `Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender-Features` <br/>
   `Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender` <br/>
 
   Lorsque vous utilisez la commande DISM dans une séquence de tâches exécutant PowerShell, le chemin d’accès cmd.exe suivant est requis.
   Exemple :<br/>
   
   `c:\windows\sysnative\cmd.exe /c Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender-Features`<br/>
   `c:\windows\sysnative\cmd.exe /c Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender`<br/>

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>Définir Antivirus Microsoft Defender en mode passif sur Windows Server

1. Ouvrez l’Éditeur du Registre, puis accédez à <br/>
   `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. Modifiez (ou créez) une entrée DWORD appelée **ForceDefenderPassiveMode** et spécifiez les paramètres suivants :

   - Définissez la valeur DWORD sur **1**.
   - Sous **Base,** **sélectionnez Hexadécimal**.

> [!NOTE]
> Après l’intégration à Defender pour le point de terminaison, vous de Antivirus Microsoft Defender le mode passif sur Windows Server. Pour valider que le mode passif a été définie comme prévu, recherchez l’événement *5007* dans le journal des opérations **de Microsoft-Windows-Windows Defender** (situé à l’emplacement ), et confirmez que les clés de Registre `C:\Windows\System32\winevt\Logs` **ForceDefenderPassiveMode** ou **PassiveMode** ont été définies sur **0x1**.

### <a name="are-you-using-windows-server-2016"></a>Utilisez-vous Windows Server 2016 ?

Actuellement, vous ne pouvez pas exécuter Antivirus Microsoft Defender en mode passif sur Windows Server 2016. Désinstallez la solution antivirus/anti-programme malveillant non Microsoft et installez/activez Antivirus Microsoft Defender. Si vous avez des difficultés à activer Antivirus Microsoft Defender sur Windows Server 2016, suivez les étapes suivantes :

1. Sur l’appareil, ouvrez PowerShell en tant qu’administrateur.

2. Tapez l’cmdlet PowerShell suivante : `mpcmdrun -wdenable` .

> [!TIP]
> Pour plus d’informations, voir les articles suivants:
> - [Antivirus Microsoft Defender sur Windows Server](microsoft-defender-antivirus-on-windows-server.md)
> - [Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité](microsoft-defender-antivirus-compatibility.md)

### <a name="confirm-that-microsoft-defender-antivirus-is-enabled"></a>Vérifier que Antivirus Microsoft Defender est activé

Vous pouvez utiliser l’une des méthodes suivantes pour confirmer l’état Antivirus Microsoft Defender, comme décrit dans le tableau suivant :

| Méthode | Procedure |
|:---|:---|
| Sécurité Windows application | 1. Sur un appareil Windows, ouvrez l’application Sécurité Windows’application. <br/>2. Sélectionnez **Protection contre & virus**.<br/>3. Under **Qui’s protecting me?** select **Manage providers**. <br/>4. Dans la page **Fournisseurs de sécurité,** sous **Antivirus,** vous devez voir Antivirus Microsoft Defender **est allumé.** |
| Gestionnaire des tâches | 1. Sur un appareil Windows, ouvrez l’application Gestionnaire des tâches. <br/>2. Sélectionnez **l’onglet Détails.**<br/>3. Recherchez les **MsMpEng.exe** dans la liste. |
| Windows PowerShell <br/> (Pour confirmer que le Antivirus Microsoft Defender est en cours d’exécution) | 1. Sur un appareil Windows, ouvrez Windows PowerShell.<br/>2. Exécutez l’cmdlet PowerShell suivante `Get-Process` :<br/>3. Examinez les résultats. Vous devriez voir **MsMpEng.exe** si Antivirus Microsoft Defender est activé. |
| Windows PowerShell <br/> (Pour vérifier que la protection antivirus est en place) | Vous pouvez utiliser [l’cmdlet PowerShell Get-MpComputerStatus.](/powershell/module/defender/get-mpcomputerstatus)<br/>1. Sur un appareil Windows, ouvrez Windows PowerShell.<br/>2. Exécutez l’cmdlet PowerShell suivante `Get-MpComputerStatus | select AMRunningMode` : .<br/>3. Examinez les résultats. Vous devez voir **normal** ou **passif** si Antivirus Microsoft Defender est activé sur le point de terminaison. |

> [!TIP]
> [En savoir plus sur Antivirus Microsoft Defender états.](microsoft-defender-antivirus-compatibility.md#more-details-about-microsoft-defender-antivirus-states)

## <a name="configure-defender-for-endpoint"></a>Configurer Defender pour endpoint

Cette étape du processus de migration implique la configuration de Antivirus Microsoft Defender pour vos points de terminaison. Nous vous recommandons d’utiliser Intune ; Toutefois, vous pouvez utiliser n’importe quelle méthode répertoriée dans le tableau suivant :

|Méthode  |Procédure  |
|---------|---------|
| [Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/>**REMARQUE**: Intune fait désormais partie de Microsoft Endpoint Manager. | 1. Go to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and sign in.<br/> 2. Sélectionnez les  >  **profils de configuration des** appareils, puis sélectionnez le type de profil que vous souhaitez configurer. Si vous n’avez pas encore créé de type de profil de **restrictions** d’appareil, ou si vous souhaitez en créer un nouveau, voir Configurer les [paramètres](/intune/device-restrictions-configure)de restriction d’appareil dans Microsoft Intune .<br/> 3. Sélectionnez **propriétés,** puis sélectionnez **Paramètres de configuration : Modifier**.<br/>4. **Développez Antivirus Microsoft Defender**. <br/>5. Activez **la protection cloud.**<br/>6. Dans la demande **d’utilisateurs** avant la soumission d’exemples, sélectionnez Envoyer tous **les exemples automatiquement.**<br/> 7. Dans la dropdown **Détecter les applications potentiellement indésirables,** sélectionnez **Activer** ou **Auditer.**<br/>8. Sélectionnez **Révision + Enregistrer,** puis sélectionnez **Enregistrer.**<br/><br/>**CONSEIL**: pour plus d’informations sur les profils d’appareil Intune, notamment sur la création et la configuration de leurs paramètres, consultez les Microsoft Intune [profils d’appareil .](/intune/device-profiles)|
| Microsoft Endpoint Configuration Manager    | Voir [Créer et déployer des stratégies de logiciel anti-programme malveillant pour Endpoint Protection dans Configuration Manager.](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies) <br/><br/> Lorsque vous créez et configurez vos stratégies de logiciel [anti-programme](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) malveillant, veillez à passer en revue les paramètres de protection en temps réel et à activer [bloquer à la première vue.](configure-block-at-first-sight-microsoft-defender-antivirus.md)
| Panneau de Windows     |Suivez les instructions ci-après [: Antivirus Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows). (Vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender *dans* certaines versions de Windows.)        |
| [Gestion avancée des stratégies de groupe](/microsoft-desktop-optimization-pack/agpm/) <br/>ou<br/>[Console de gestion des stratégies de groupe ](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)  | 1. Go to **Computer configuration**  >  **Administrative templates** Windows  >  **components**  >  **Antivirus Microsoft Defender**. <br/> 2. Recherchez une stratégie appelée **Désactiver Antivirus Microsoft Defender**.<br/> 3. Choisissez **Modifier le paramètre de stratégie** et assurez-vous que la stratégie est désactivée. Cette action active la Antivirus Microsoft Defender. (Vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender *dans* certaines versions de Windows.) |

> [!TIP]
> Vous pouvez déployer les stratégies avant l’intégration des appareils de votre organisation.
  
## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution"></a>Ajouter Microsoft Defender pour le point de terminaison à la liste d’exclusions de votre solution existante

Cette étape du processus de configuration implique l’ajout de Defender for Endpoint à la liste d’exclusions de votre solution de protection de point de terminaison existante et de tous les autres produits de sécurité que votre organisation utilise. 

> [!TIP]
> Pour obtenir de l’aide sur la configuration des exclusions, reportez-vous à la documentation de votre fournisseur de solutions.

Les exclusions spécifiques à configurer dépendent de la version de Windows vos points de terminaison ou appareils en cours d’exécution et sont répertoriées dans le tableau suivant :

|Système d’exploitation |Exclusions |
|--|--|
|Windows 10, [version 1803 ou](/windows/release-health/status-windows-10-1803) ultérieure (voir Windows 10 de [publication)](/windows/release-health/release-information)<br/>Windows 10, version 1703 ou 1709 avec [KB4493441](https://support.microsoft.com/help/4493441) installé <br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/>[Windows Serveur, version 1803](/windows-server/get-started/whats-new-in-windows-server-1803) |`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`  |
|[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2) <br/>[Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/>[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<br/><br/>**REMARQUE**: La surveillance des fichiers temporaires de l’hôte 6\45 peut être un sous-dossier numéroté différent. <br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>Ajoutez votre solution existante à la liste d’exclusions Antivirus Microsoft Defender

Au cours de cette étape du processus d’installation, vous ajoutez votre solution existante à la Antivirus Microsoft Defender exclusion. Vous pouvez choisir parmi plusieurs méthodes pour ajouter vos exclusions à Antivirus Microsoft Defender, comme répertorié dans le tableau suivant :

|Méthode | Procédure|
|:---|:---|
| [Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/>**REMARQUE**: Intune fait désormais partie de Microsoft Endpoint Manager. | 1. Go to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and sign in.<br/> 2. Sélectionnez les  >  **profils de configuration des** appareils, puis sélectionnez le profil à configurer.<br/>3. Sous **Gérer,** sélectionnez **Propriétés.**<br/> 4. Sélectionnez **les paramètres de configuration : Modifier.**<br/> 5. **Développez Antivirus Microsoft Defender,** puis développez **Antivirus Microsoft Defender exclusions.**<br/> 6. Spécifiez les fichiers et dossiers, extensions et processus à exclure de Antivirus Microsoft Defender analyses. Pour référence, voir [Antivirus Microsoft Defender exclusions.](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions)<br/> 7. Choisissez **Révision + Enregistrer,** puis **Enregistrer.**  |
| [Microsoft Endpoint Configuration Manager](/mem/configmgr/) | 1. À l’aide de la [console Configuration Manager,](/mem/configmgr/core/servers/manage/admin-console)go to **Assets and Compliance**  >  **Endpoint Protection**  >  **Antimalware Policies,** and then select the policy that you want to modify. <br/>2. Spécifiez les paramètres d’exclusion pour les fichiers et dossiers, les extensions et les processus à exclure de Antivirus Microsoft Defender analyses. |
| [Objet de stratégie de groupe](/previous-versions/windows/desktop/Policy/group-policy-objects) | 1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](https://technet.microsoft.com/library/cc731212.aspx)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier.**<br/> 2. Dans l’Éditeur de gestion **des stratégies** de groupe, sélectionnez **Configuration** ordinateur et **sélectionnez Modèles d’administration.**<br/> 3. Développez l’arborescence **pour Windows composants > Antivirus Microsoft Defender > exclusions.** (Vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender *dans* certaines versions de Windows.)<br/>4. Double-cliquez sur le paramètre **Exclusions** de chemin d’accès et ajoutez les exclusions.<br/>- Définissez l’option **sur Activé.**<br/>- Sous la section **Options,** sélectionnez **Afficher...**.<br/>- Spécifiez chaque dossier sur sa propre ligne sous la **colonne Nom de** la valeur.<br/>- Si vous spécifiez un fichier, veillez à entrer un chemin d’accès complet au fichier, y compris la lettre de lecteur, le chemin d’accès au dossier, le nom de fichier et l’extension. Entrez **0 dans** la **colonne** Valeur.<br/>5. Sélectionnez **OK**.<br/>6. Double-cliquez sur le paramètre **Exclusions d’extensions** et ajoutez les exclusions.<br/>- Définissez l’option **sur Activé.**<br/>- Sous la section **Options,** sélectionnez **Afficher...**.<br/>- Entrez chaque extension de fichier sur sa propre ligne sous la **colonne Nom de** la valeur.  Entrez **0 dans** la **colonne** Valeur.<br/>7. Sélectionnez **OK**. |
| Objet de stratégie de groupe local |1. Sur le point de terminaison ou l’appareil, ouvrez l’Éditeur de stratégie de groupe local. <br/>2. Go to **Computer Configuration**  >  **Administrative Templates** Windows  >  **Components**  >  **Antivirus Microsoft Defender**  >  **Exclusions**. (Vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender *dans* certaines versions de Windows.)<br/>3. Spécifiez votre chemin d’accès et les exclusions de processus. |
| Clé du Registre |1. Exporte la clé de Registre suivante : `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions` .<br/>2. Importez la clé de Registre. Voici deux exemples :<br/>- Chemin d’accès local : `regedit.exe /s c:\temp\ MDAV_Exclusion.reg` <br/>- Partage réseau : `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg` |

### <a name="keep-the-following-points-about-exclusions-in-mind"></a>Gardez les points suivants à l’esprit sur les exclusions

Lorsque vous ajoutez [des exclusions Antivirus Microsoft Defender analyses,](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus)vous devez ajouter des exclusions de chemin d’accès et de processus. 

Gardez les points suivants à l’esprit :

- *Les exclusions de chemin d’accès* excluent des fichiers spécifiques et tout ce à quoi ces fichiers ont accès.
- *Les exclusions de processus* excluent tout ce qui touche un processus, mais n’excluent pas le processus lui-même.
- List your process exclusions using their full path and not by their name only. (La méthode de nom uniquement est moins sécurisée.)
- Si vous listez chaque exécutable (.exe) en tant qu’exclusion de chemin d’accès et exclusion de processus, le processus et tout ce qu’il touche sont exclus.


## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>Configurer vos groupes d’appareils, collections d’appareils et unités d’organisation

Les groupes d’appareils, les collections d’appareils et les unités d’organisation permettent à votre équipe de sécurité de gérer et d’attribuer des stratégies de sécurité efficacement. Le tableau suivant décrit chacun de ces groupes et explique comment les configurer. Il se peut que votre organisation n’utilise pas les trois types de collection.

| Type de collection | Procédure |
|--|--|
|[Les groupes d’appareils](/microsoft-365/security/defender-endpoint/machine-groups) (anciennement appelés groupes d’ordinateurs) permettent à votre équipe des opérations de sécurité de configurer des fonctionnalités de sécurité, telles que l’examen et la correction automatisés.<br/><br/>Les groupes d’appareils sont également utiles pour attribuer l’accès à ces appareils afin que votre équipe des opérations de sécurité puisse prendre des mesures correctives si nécessaire. <br/><br/>Les groupes d’appareils sont créés dans [Microsoft 365 Defender portail.](microsoft-defender-security-center.md) |1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ).<br/>2. Dans le volet de navigation sur la gauche, choisissez Paramètres  >  **groupes d’appareils Endpoints**  >  **Permissions**  >  .  <br/>3. Choisissez **+ Ajouter un groupe d’appareils.**<br/>4. Spécifiez un nom et une description pour le groupe d’appareils.<br/>5. Dans la liste de **niveau Automation,** sélectionnez une option. (Nous vous recommandons **de corriger les menaces automatiquement.** Pour en savoir plus sur les différents niveaux d’automatisation, voir [comment les menaces sont corrigés.](/microsoft-365/security/defender-endpoint/automated-investigations#how-threats-are-remediated)<br/>6. Spécifiez les conditions d’une règle correspondante pour déterminer quels appareils appartiennent au groupe d’appareils. Par exemple, vous pouvez choisir un domaine, des versions de système d’exploitation ou même utiliser des [balises d’appareil.](/microsoft-365/security/defender-endpoint/machine-tags)<br/>7. Sous **l’onglet** Accès utilisateur, spécifiez les rôles qui doivent avoir accès aux appareils inclus dans le groupe d’appareils. <br/>8. Choisissez **Terminé**. |
|[Les collections d’appareils](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) permettent à votre équipe des opérations de sécurité de gérer les applications, de déployer les paramètres de conformité ou d’installer des mises à jour logicielles sur les appareils de votre organisation.<br/><br/>Les collections d’appareils sont créées à l’aide [de Configuration Manager.](/mem/configmgr/) |Suivez les étapes de [la procédure de création d’une collection.](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create) |
|[Les unités d’organisation](/azure/active-directory-domain-services/create-ou) vous permettent de grouper logiquement des objets tels que des comptes d’utilisateur, des comptes de service ou des comptes d’ordinateur.<br/><br/> Vous pouvez ensuite affecter des administrateurs à des unités d’organisation spécifiques et appliquer une stratégie de groupe pour appliquer des paramètres de configuration ciblés.<br/><br/> Les unités d’organisation sont définies [dans Azure Active Directory Services de domaine.](/azure/active-directory-domain-services) | Suivez les étapes de la section Créer une unité [d’organisation dans Azure Active Directory domaine](/azure/active-directory-domain-services/create-ou)géré des services de domaine. |


## <a name="next-step"></a>Étape suivante

**Félicitations**! Vous avez terminé la phase d’installation [du basculement vers Defender pour Endpoint](switch-to-microsoft-defender-migration.md#the-migration-process)!

- [Passer à la phase 3 : intégration à Defender pour endpoint](switch-to-microsoft-defender-onboard.md)
