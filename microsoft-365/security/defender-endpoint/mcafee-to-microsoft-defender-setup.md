---
title: Mc Antivirus vers Microsoft Defender pour le point de terminaison - Configuration
description: Il s’agit de la phase 2, le programme d’installation, pour la migration de Mc Antivirus vers Microsoft Defender pour Endpoint.
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
- m365solution-mcafeemigrate
- m365solution-scenario
ms.topic: article
ms.custom: migrationguides
ms.date: 03/03/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 0145f48a5bcf53cd06c70b18e9c48aa6e5e5c06c
ms.sourcegitcommit: 68383240ef7a673d5f28e2ecfab9f105bf1d8c8f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "52327585"
---
# <a name="migrate-from-mcafee---phase-2-set-up-microsoft-defender-for-endpoint"></a>Migrer à partir de Mc Antivirus - Phase 2 : Configurer Microsoft Defender pour le point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![Phase 1 : préparation](images/phase-diagrams/prepare.png)](mcafee-to-microsoft-defender-prepare.md)<br/>[Phase 1 : préparation](mcafee-to-microsoft-defender-prepare.md) |![Phase 2 : configuration](images/phase-diagrams/setup.png)<br/>Phase 2 : configuration |[![Phase 3 : intégration](images/phase-diagrams/onboard.png)](mcafee-to-microsoft-defender-onboard.md)<br/>[Phase 3 : intégration](mcafee-to-microsoft-defender-onboard.md) |
|--|--|--|
||*Vous êtes là !* | |

**Bienvenue dans la phase d’installation de la migration de [Mc Antivirus Endpoint Security (Mc Antivirus)](mcafee-to-microsoft-defender-migration.md#the-migration-process)** vers Microsoft Defender pour Endpoint . Cette phase comprend les étapes suivantes :
1. [Activez l’Antivirus Microsoft Defender et confirmez qu’il est en mode passif.](#enable-microsoft-defender-antivirus-and-confirm-its-in-passive-mode)
2. [Obtenir les mises à jour de l’Antivirus Microsoft Defender.](#get-updates-for-microsoft-defender-antivirus)
3. [Ajoutez Microsoft Defender pour le point de terminaison à la liste d’exclusions pour Mc Antivirus.](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-mcafee)
4. [Ajoutez Mc Antivirus à la liste d’exclusions de l’Antivirus Microsoft Defender.](#add-mcafee-to-the-exclusion-list-for-microsoft-defender-antivirus)
5. [Ajoutez Mc Antivirus à la liste d’exclusions de Microsoft Defender pour le point de terminaison.](#add-mcafee-to-the-exclusion-list-for-microsoft-defender-for-endpoint)
6. [Configurer vos groupes d’appareils, collections d’appareils et unités d’organisation.](#set-up-your-device-groups-device-collections-and-organizational-units)
7. [Configurer des stratégies de logiciel anti-programme malveillant et une protection en temps réel.](#configure-antimalware-policies-and-real-time-protection)

## <a name="enable-microsoft-defender-antivirus-and-confirm-its-in-passive-mode"></a>Activer l’Antivirus Microsoft Defender et vérifier qu’il est en mode passif

Sur certaines versions de Windows, telles que Windows Server, l’Antivirus Microsoft Defender a peut-être été désinstallé ou désactivé lors de l’installation de votre solution Mc Antivirus. En effet, l’Antivirus Microsoft Defender n’entre pas en mode passif ou désactivé lorsque vous installez un produit antivirus tiers, tel que Mc Antivirus. (Pour en savoir plus à ce sujet, consultez la compatibilité [de l’Antivirus Microsoft Defender.)](microsoft-defender-antivirus-compatibility.md)

Cette étape du processus de migration comprend les tâches suivantes :
- [Définition de DisableAntiSpyware sur false sur Windows Server](#set-disableantispyware-to-false-on-windows-server)
- [Réinstaller l’Antivirus Microsoft Defender sur Windows Server](#reinstall-microsoft-defender-antivirus-on-windows-server);
- [Définition de l’Antivirus Microsoft Defender en mode passif sur Windows Server](#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server)
- [Activation de l’Antivirus Microsoft Defender sur vos appareils clients Windows](#enable-microsoft-defender-antivirus-on-your-windows-client-devices); et
- [Confirmant que l’Antivirus Microsoft Defender est en mode passif](#confirm-that-microsoft-defender-antivirus-is-in-passive-mode).  

### <a name="set-disableantispyware-to-false-on-windows-server"></a>Définir DisableAntiSpyware sur false sur Windows Server

La clé de Registre [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) a été utilisée dans le passé pour désactiver l’Antivirus Microsoft Defender et déployer un autre produit antivirus, tel que Mc Antivirus. En règle générale, vous ne devez pas avoir cette clé de Registre sur vos appareils et points de terminaison Windows ; toutefois, si vous avez configuré, voici comment définir sa valeur `DisableAntiSpyware` sur false :

1. Sur votre appareil Windows Server, ouvrez l’Éditeur du Registre.

2. Accédez à la page `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`.

3. Dans ce dossier, recherchez une entrée DWORD appelée **DisableAntiSpyware**.

   - Si vous ne voyez pas cette entrée, tout est prêt.

   - Si vous voyez **DisableAntiSpyware,** procédez à l’étape 4.

4. Cliquez avec le bouton droit sur la DWORD DisableAntiSpyware, puis choisissez **Modifier**.

5. Définissez la valeur sur `0` . (Cela définit la valeur de la clé de Registre sur *false*.)

> [!TIP]
> Pour en savoir plus sur cette clé de Registre, voir [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware).

### <a name="reinstall-microsoft-defender-antivirus-on-windows-server"></a>Réinstaller l’Antivirus Microsoft Defender sur Windows Server

> [!NOTE]
> La procédure suivante s’applique uniquement aux points de terminaison ou aux appareils exécutant les versions suivantes de Windows :
> - Windows Server 2019
> - Windows Server, version 1803 (mode principal uniquement)
> - Windows Server 2016

1. En tant qu’administrateur local sur le point de terminaison ou l’appareil, ouvrez Windows PowerShell.

2. Exécutez les cmdlets PowerShell suivantes : <br/>
   
   `Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender-Features` <br/>
   
   `Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender` <br/>

> [!NOTE]
> Lorsque vous utilisez la commande DISM dans une séquence de tâches exécutant PS, le chemin d’accès cmd.exe est requis.
> Exemple :<br/>
> `c:\windows\sysnative\cmd.exe /c Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender-Features`<br/>
> `c:\windows\sysnative\cmd.exe /c Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender`<br/>

3. Pour vérifier que l’Antivirus Microsoft Defender est en cours d’exécution, utilisez l’cmdlet PowerShell suivante : <br/>
   
   `Get-Service -Name windefend`

#### <a name="are-you-using-windows-server-2016"></a>Utilisez-vous Windows Server 2016 ?

Si vous utilisez Windows Server 2016 et que vous avez des difficultés à activer l’Antivirus Microsoft Defender, utilisez l’cmdlet PowerShell suivante :

`mpcmdrun -wdenable`

> [!TIP]
> Vous avez encore besoin d’aide ? Voir [Antivirus Microsoft Defender sur Windows Server 2016 et 2019.](microsoft-defender-antivirus-on-windows-server.md)

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>Définir l’Antivirus Microsoft Defender en mode passif sur Windows Server

Étant donné que votre organisation utilise toujours Mc Antivirus, vous devez définir l’Antivirus Microsoft Defender sur le mode passif. De cette façon, Mc Antivirus Et Microsoft Defender peuvent s’exécuter côte à côte jusqu’à ce que vous avez terminé l’intégration à Microsoft Defender pour endpoint.

1. Ouvrez l’Éditeur du Registre, puis accédez à <br/>
   `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. Modifiez (ou créez) une entrée DWORD appelée **ForcePassiveMode** et spécifiez les paramètres suivants :
   
   - Définissez la valeur DWORD sur **1**.
   
   - Sous **Base,** **sélectionnez Hexadécimal**.

> [!NOTE]
> Vous pouvez utiliser d’autres méthodes pour définir la clé de Registre, telles que les suivantes :
>- [Préférence de stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn581922(v=ws.11))
>- [Un package dans Configuration Manager](/mem/configmgr/apps/deploy-use/packages-and-programs)

### <a name="enable-microsoft-defender-antivirus-on-your-windows-client-devices"></a>Activer l’Antivirus Microsoft Defender sur vos appareils clients Windows

Étant donné que votre organisation utilise Mc Antivirus comme solution antivirus principale, l’Antivirus Microsoft Defender est probablement désactivé sur les appareils Windows de votre organisation. Cette étape du processus de migration implique l’activation de l’Antivirus Microsoft Defender. 

Pour activer l’Antivirus Microsoft Defender, nous vous recommandons d’utiliser Intune. Toutefois, vous pouvez utiliser n’importe quelle méthode répertoriée dans le tableau suivant :

|Méthode  |Procédure  |
|---------|---------|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <p>**REMARQUE**: Intune est désormais Microsoft Endpoint Manager. |1. Go to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and sign in.<p>2. Sélectionnez les  >  **profils de configuration des** appareils, puis sélectionnez le type de profil que vous souhaitez configurer. <br/>Si vous n’avez pas encore créé de type de profil de **restrictions** d’appareil, ou si vous souhaitez en créer un nouveau, voir Configurer les paramètres de restriction d’appareil [dans Microsoft Intune.](/intune/device-restrictions-configure)<p>3. Sélectionnez **propriétés,** puis sélectionnez **Paramètres de configuration : Modifier**.<p>4. Développez **l’Antivirus Microsoft Defender.** <p>5. Activez **la protection cloud.**<p>6. Dans la demande **d’utilisateurs** avant la soumission d’exemples, sélectionnez Envoyer tous **les exemples automatiquement.**<p>7. Dans la dropdown **Détecter les applications potentiellement indésirables,** sélectionnez **Activer** ou **Auditer.**<p>8. Sélectionnez **Révision + Enregistrer,** puis sélectionnez **Enregistrer.**<p>Pour plus d’informations sur les profils d’appareil Intune, notamment sur la création et la configuration de leurs paramètres, voir Les profils d’appareil [Microsoft Intune.](/intune/device-profiles)|
|Panneau de commande dans Windows     |Suivez les instructions ci-après [: activer l’Antivirus Microsoft Defender.](/mem/intune/user-help/turn-on-defender-windows) <p>**REMARQUE**: il se peut que *vous Windows Defender antivirus Microsoft* Defender à la place de l’Antivirus Microsoft *Defender* dans certaines versions de Windows.        |
|[Gestion avancée des stratégies de groupe](/microsoft-desktop-optimization-pack/agpm/) <br/>ou<br/>[Console de gestion des stratégies de groupe ](use-group-policy-microsoft-defender-antivirus.md)  |1. Allez à `Computer configuration > Administrative templates > Windows components > Microsoft Defender Antivirus` . <p>2. Recherchez une stratégie appelée **Désactiver l’Antivirus Microsoft Defender.**<br/> <br/>3. Choisissez **Modifier le paramètre de stratégie** et assurez-vous que la stratégie est désactivée. Cela active l’Antivirus Microsoft Defender. <p>**REMARQUE**: il se peut que *vous Windows Defender antivirus Microsoft* Defender à la place de l’Antivirus Microsoft *Defender* dans certaines versions de Windows. |

### <a name="confirm-that-microsoft-defender-antivirus-is-in-passive-mode"></a>Vérifier que l’Antivirus Microsoft Defender est en mode passif

Antivirus Microsoft Defender peut s’exécuter avec Mc Antivirus si vous Antivirus Microsoft Defender le mode passif. Vous pouvez utiliser l’invite de commandes ou PowerShell pour effectuer cette tâche, comme décrit dans le tableau suivant :

|Méthode  |Procédure  |
|---------|---------|
|Invite de commandes     |1. Sur un Windows, ouvrez l’invite de commandes en tant qu’administrateur. <p>2. `sc query windefend` Tapez, puis appuyez sur Entrée.<p>3. Examinez les résultats pour vérifier que Antivirus Microsoft Defender est en cours d’exécution en mode passif.         |
|PowerShell     |1. Sur un appareil Windows, ouvrez Windows PowerShell en tant qu’administrateur.<p>2. Exécutez la cmdlet [Get-MpComputerStatus.](/powershell/module/defender/Get-MpComputerStatus) <p>3. Dans la liste des résultats, recherchez **AMRunningMode : Mode passif** ou **AMRunningMode : Mode passif SxS**.|

> [!NOTE]
> Vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender *dans* certaines versions de Windows.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Obtenir les mises à jour de Antivirus Microsoft Defender

Maintenir Antivirus Microsoft Defender à jour est essentiel pour garantir que vos appareils disposent des dernières technologies et fonctionnalités nécessaires pour se protéger contre les nouveaux programmes malveillants et les nouvelles techniques d’attaque, même si Antivirus Microsoft Defender s’exécute en [mode passif.](microsoft-defender-antivirus-compatibility.md)

Il existe deux types de mises à jour liées à la mise Antivirus Microsoft Defender jour :
- Mises à jour de l’intelligence de la sécurité
- Mises à jour de produit

Pour obtenir vos mises à jour, suivez les instructions de la Antivirus Microsoft Defender mises à jour [et appliquez les lignes de base.](manage-updates-baselines-microsoft-defender-antivirus.md)

## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-mcafee"></a>Ajouter Microsoft Defender pour le point de terminaison à la liste d’exclusions pour Mc Antivirus

Cette étape du processus de configuration implique l’ajout de Microsoft Defender for Endpoint à la liste d’exclusions pour Mc Antivirus et tous les autres produits de sécurité que votre organisation utilise. 

> [!TIP]
> Pour obtenir de l’aide sur la configuration des exclusions, reportez-vous à la documentation Mc Antivirus, telle que l’article suivant : [Mc Antivirus Endpoint Security 10.5.0 - Threat Prevention Module Product Guide (Mc Antivirus ePolicy Orchestrator) - Windows: Configuring exclusions](https://docs.mcafee.com/bundle/endpoint-security-10.5.0-threat-prevention-product-guide-epolicy-orchestrator-windows/page/GUID-71C5FB4B-A143-43E6-8BF0-8B2C16ABE6DA.html).

Les exclusions spécifiques à configurer dépendent de la version de Windows vos points de terminaison ou appareils en cours d’exécution et sont répertoriées dans le tableau suivant :

|SYSTÈME D’EXPLOITATION |Exclusions |
|--|--|
|- Windows 10, [version 1803](/windows/release-health/status-windows-10-1803) ou ultérieure (voir [Windows 10 de publication)](/windows/release-health/release-information)<br/>- Windows 10, version 1703 ou [1709](/windows/release-health/status-windows-10-1709) avec [KB4493441](https://support.microsoft.com/help/4493441) installé <br/>- [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/>- [Windows Serveur, version 1803](/windows-server/get-started/whats-new-in-windows-server-1803) |`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<p>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<p>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<p>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`<br/>  |
|- [Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2) <br/>- [Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/>- [Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/>- [Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/>- [Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<p>**REMARQUE**: les fichiers temporaires de l’hôte de surveillance 6\45 peuvent être des sous-dossiers numérotés différents.<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-mcafee-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>Ajouter Mc Antivirus à la liste d’exclusions pour Antivirus Microsoft Defender

Au cours de cette étape du processus de configuration, vous ajoutez Mc Antivirus et vos autres solutions de sécurité à la Antivirus Microsoft Defender exclusion. 

Lorsque vous ajoutez [des exclusions Antivirus Microsoft Defender analyses,](configure-exclusions-microsoft-defender-antivirus.md)vous devez ajouter des exclusions de chemin d’accès et de processus. Gardez les points suivants à l’esprit :
- Les exclusions de chemin d’accès excluent des fichiers spécifiques et tout ce à quoi ces fichiers ont accès.
- Les exclusions de processus excluent tout ce qui touche un processus, mais n’excluent pas le processus lui-même.
- Si vous listez chaque exécutable (.exe) en tant qu’exclusion de chemin d’accès et exclusion de processus, le processus et tout ce qu’il touche sont exclus.
- List your process exclusions using their full path and not by their name only. (La méthode de nom uniquement est moins sécurisée.)

Vous pouvez choisir parmi plusieurs méthodes pour ajouter vos exclusions à Antivirus Microsoft Defender, comme répertorié dans le tableau suivant :

|Méthode | Procédure|
|--|--|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <p>**REMARQUE**: Intune est désormais Microsoft Endpoint Manager. |1. Go to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and sign in.<p>2. Sélectionnez les  >  **profils de configuration des** appareils, puis sélectionnez le profil à configurer.<p>3. Sous **Gérer,** sélectionnez **Propriétés.** <p>4. Sélectionnez **les paramètres de configuration : Modifier.**<p>5. Développez **Antivirus Microsoft Defender,** puis développez **Antivirus Microsoft Defender exclusions.**<p>6. Spécifiez les fichiers et dossiers, extensions et processus à exclure de Antivirus Microsoft Defender analyses. Pour référence, voir [Antivirus Microsoft Defender exclusions.](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions)<p>7. Choisissez **Révision + Enregistrer,** puis **Enregistrer.**  |
|[Microsoft Endpoint Configuration Manager](/mem/configmgr/) |1. À l’aide de la [console Configuration Manager,](/mem/configmgr/core/servers/manage/admin-console)go to **Assets and Compliance**  >  **Endpoint Protection**  >  **Antimalware Policies,** and then select the policy that you want to modify. <p>2. Spécifiez les paramètres d’exclusion pour les fichiers et dossiers, les extensions et les processus à exclure de Antivirus Microsoft Defender analyses. |
|[Objet de stratégie de groupe](/previous-versions/windows/desktop/Policy/group-policy-objects) | 1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](https://technet.microsoft.com/library/cc731212.aspx)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**<p>2. Dans l’Éditeur de gestion des **stratégies** de groupe, allez à **Configuration** ordinateur et cliquez sur **Modèles d’administration.**<p>3. Développez l’arborescence **pour Windows composants > Antivirus Microsoft Defender > exclusions**.<br/>**REMARQUE**: vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender dans certaines versions de Windows. <p>4. Double-cliquez sur le paramètre **Exclusions** de chemin d’accès et ajoutez les exclusions.<br/>- Définissez l’option **sur Activé.**<br/>- Sous la section **Options,** cliquez sur **Afficher...**.<br/>- Spécifiez chaque dossier sur sa propre ligne sous la **colonne Nom de** la valeur.<br/>- Si vous spécifiez un fichier, veillez à entrer un chemin d’accès complet au fichier, y compris la lettre de lecteur, le chemin d’accès au dossier, le nom de fichier et l’extension. Entrez **0 dans** la **colonne** Valeur.<p>5. Cliquez sur **OK.**<p>6. Double-cliquez sur le paramètre **Exclusions d’extensions** et ajoutez les exclusions.<br/>- Définissez l’option **sur Activé.**<br/>- Sous la section **Options,** cliquez sur **Afficher...**.<br/>- Entrez chaque extension de fichier sur sa propre ligne sous la **colonne Nom de** la valeur.  Entrez **0 dans** la **colonne** Valeur.<p>7. Cliquez sur **OK.** |
|Objet de stratégie de groupe local |1. Sur le point de terminaison ou l’appareil, ouvrez l’Éditeur de stratégie de groupe local. <p>2. Go to **Computer Configuration**  >  **Administrative Templates** Windows  >  **Components**  >  **Antivirus Microsoft Defender**  >  **Exclusions**. <br/>**REMARQUE**: vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender dans certaines versions de Windows. <p>3. Spécifiez votre chemin d’accès et les exclusions de processus. |
|Clé du Registre |1. Exporte la clé de Registre suivante : `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions` .<p>2. Importez la clé de Registre. Voici deux exemples :<br/>- Chemin d’accès local : `regedit.exe /s c:\temp\ MDAV_Exclusion.reg` <br/>- Partage réseau : `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg` |

## <a name="add-mcafee-to-the-exclusion-list-for-microsoft-defender-for-endpoint"></a>Ajouter Mc Antivirus à la liste d’exclusions de Microsoft Defender pour le point de terminaison

> [!IMPORTANT]
> En règle générale, vous ne devez pas ajouter d’exclusions pour Defender for Endpoint, en particulier si vous avez déjà défini des exclusions pour Antivirus Microsoft Defender. Toutefois, si vous êtes face à des problèmes Antivirus Microsoft Defender ne reste pas en mode passif, effectuez la tâche suivante. Dans le cas contraire, ignorez cette section et passez à La mise en place de vos groupes [d’appareils, collections d’appareils et unités d’organisation.](#set-up-your-device-groups-device-collections-and-organizational-units)

Pour ajouter des exclusions à Microsoft Defender pour le point de terminaison, vous créez [des indicateurs.](indicator-file.md)

1. Go to the Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ) and sign in.

2. Dans le volet de navigation, choisissez **Paramètres**  >  **indicateurs de**  >  **règles.**

3.  Sous **l’onglet Hchéths fichier,** choisissez **Ajouter un indicateur.**

3. Sous **l’onglet** Indicateur, spécifiez les paramètres suivants :
   - Hachage de fichier (besoin d’aide ? Voir [Rechercher un hachage de fichier à l’aide de CMPivot](#find-a-file-hash-using-cmpivot) dans cet article.)
   - Under **Expires on (UTC)**, choose **Never**.

4. Sous **l’onglet Action,** spécifiez les paramètres suivants :
   - **Action de réponse**: **Autoriser**
   - Titre et description

5. Sous **l’onglet Étendue,** sous **Groupes d’appareils,** sélectionnez **Tous les appareils** de mon étendue ou Sélectionner dans **la liste.**

6. Sous **l’onglet Résumé,** examinez les paramètres, puis cliquez sur **Enregistrer.**

### <a name="find-a-file-hash-using-cmpivot"></a>Rechercher un hachage de fichier à l’aide de CMPivot

CMPivot est un utilitaire de console pour Configuration Manager. CMPivot permet d’accéder à l’état en temps réel des appareils dans votre environnement. Il exécute immédiatement une requête sur tous les appareils actuellement connectés dans la collection cible et renvoie les résultats. Pour en savoir plus, consultez [la vue d’ensemble de CMPivot.](/mem/configmgr/core/servers/manage/cmpivot-overview)

Pour utiliser CMPivot afin d’obtenir le hachage de votre fichier, suivez les étapes suivantes :

1. Examinez les [conditions préalables.](/mem/configmgr/core/servers/manage/cmpivot#prerequisites)

2. [Démarrez CMPivot](/mem/configmgr/core/servers/manage/cmpivot#start-cmpivot). 

3. Connecter configuration Manager ( `SCCM_ServerName.DomainName.com` ).

4. Sélectionnez **l’onglet** Requête.
 
5. Dans la liste **Device Collection,** choisissez **Tous les systèmes (par défaut).**

6. Dans la zone de requête, tapez la requête suivante :<br/>

```kusto
File(c:\\windows\\notepad.exe)
| project Hash
```
> [!NOTE]
> Dans la requête ci-dessus, *remplaceznotepad.exe* par le nom de votre processus de produit de sécurité tiers. 

## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>Configurer vos groupes d’appareils, collections d’appareils et unités d’organisation

| Type de collection | Procédure |
|--|--|
|[Les groupes d’appareils](machine-groups.md) (anciennement appelés groupes d’ordinateurs) permettent à votre équipe des opérations de sécurité de configurer des fonctionnalités de sécurité, telles que l’examen et la correction automatisés.<p> Les groupes d’appareils sont également utiles pour attribuer l’accès à ces appareils afin que votre équipe des opérations de sécurité puisse prendre des mesures correctives si nécessaire. <p>Les groupes d’appareils sont créés dans le Centre de sécurité Microsoft Defender. |1. Go to the Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ).<p>2. Dans le volet de navigation sur la gauche, choisissez Paramètres groupes d’appareils  >  **Autorisations.**  >    <p>3. Choisissez **+ Ajouter un groupe d’appareils.**<p>4. Spécifiez un nom et une description pour le groupe d’appareils.<p>5. Dans la liste de **niveau Automation,** sélectionnez une option. (Nous vous recommandons **de corriger les menaces automatiquement.** Pour en savoir plus sur les différents niveaux d’automatisation, voir [comment les menaces sont corrigés.](automated-investigations.md#how-threats-are-remediated)<p>6. Spécifiez les conditions d’une règle correspondante pour déterminer quels appareils appartiennent au groupe d’appareils. Par exemple, vous pouvez choisir un domaine, des versions de système d’exploitation ou même utiliser des [balises d’appareil.](machine-tags.md) <p>7. Sous **l’onglet** Accès utilisateur, spécifiez les rôles qui doivent avoir accès aux appareils inclus dans le groupe d’appareils. <p>8. Choisissez **Terminé**. |
|[Les collections d’appareils](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) permettent à votre équipe des opérations de sécurité de gérer les applications, de déployer les paramètres de conformité ou d’installer des mises à jour logicielles sur les appareils de votre organisation. <p>Les collections d’appareils sont créées à l’aide [de Configuration Manager.](/mem/configmgr/) |Suivez les étapes de [la procédure de création d’une collection.](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create) |
|[Les unités d’organisation](/azure/active-directory-domain-services/create-ou) vous permettent de grouper logiquement des objets tels que des comptes d’utilisateur, des comptes de service ou des comptes d’ordinateur. Vous pouvez ensuite affecter des administrateurs à des unités d’organisation spécifiques et appliquer une stratégie de groupe pour appliquer des paramètres de configuration ciblés.<p> Les unités d’organisation sont définies [dans Azure Active Directory Services de domaine.](/azure/active-directory-domain-services) | Suivez les étapes de la section Créer une unité [d’organisation dans Azure Active Directory domaine](/azure/active-directory-domain-services/create-ou)géré des services de domaine. |

## <a name="configure-antimalware-policies-and-real-time-protection"></a>Configurer les stratégies de logiciel anti-programme malveillant et la protection en temps réel

À l’aide de Configuration Manager et de vos collections d’appareils, configurez vos stratégies anti-programme malveillant.

- Voir [Créer et déployer des stratégies de logiciel anti-programme malveillant pour Endpoint Protection dans Configuration Manager.](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies)

- Pendant que vous créez et configurez vos stratégies de logiciel [anti-programme](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) malveillant, veillez à passer en revue les paramètres de protection en temps réel et à activer [bloquer à la première vue.](configure-block-at-first-sight-microsoft-defender-antivirus.md)

> [!TIP]
> Vous pouvez déployer les stratégies avant les appareils de votre organisation sur les appareils intégrés.

## <a name="next-step"></a>Étape suivante

**Félicitations**! Vous avez terminé la phase d’installation [de la migration de Mc Antivirus vers Microsoft Defender pour Endpoint](mcafee-to-microsoft-defender-migration.md#the-migration-process)!

- [Passer à la phase 3 : intégration à Microsoft Defender pour endpoint](mcafee-to-microsoft-defender-onboard.md)
