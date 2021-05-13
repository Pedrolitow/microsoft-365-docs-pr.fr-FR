---
title: Basculer vers Microsoft Defender pour le point de terminaison - Installation
description: Phase 2, le processus d’installation, lors du basculement vers Microsoft Defender pour point de terminaison.
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
ms.topic: article
ms.custom: migrationguides
ms.date: 05/11/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 2b0032ff03ac58e9ea311af9f0f74abd6092646d
ms.sourcegitcommit: 94e64afaf12f3d8813099d8ffa46baba65772763
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52345823"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-2-setup"></a>Basculer vers Microsoft Defender pour le point de terminaison - Phase 2 : Installation

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![Phase 1 : préparation](images/phase-diagrams/prepare.png)](switch-to-microsoft-defender-prepare.md)<br/>[Phase 1 : préparation](switch-to-microsoft-defender-prepare.md) |![Phase 2 : configuration](images/phase-diagrams/setup.png)<br/>Phase 2 : configuration |[![Phase 3 : Intégration3](images/phase-diagrams/onboard.png)](switch-to-microsoft-defender-onboard.md)<br/>[Phase 3 : intégration](switch-to-microsoft-defender-onboard.md) |
|--|--|--|
||*Vous êtes là !* | |

**Bienvenue dans la phase d’installation [du basculement vers Microsoft Defender pour le point de terminaison.](switch-to-microsoft-defender-migration.md#the-migration-process)** Cette phase comprend les étapes suivantes :

1. [Activez Antivirus Microsoft Defender et confirmez qu’il est en mode passif.](#enable-microsoft-defender-antivirus-and-confirm-its-in-passive-mode)

2. [Obtenir les mises à jour de Antivirus Microsoft Defender](#get-updates-for-microsoft-defender-antivirus).

3. [Ajoutez Microsoft Defender pour le point de terminaison à la liste d’exclusions de votre solution de point de terminaison existante.](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution)

4. [Ajoutez votre solution existante à la liste d’exclusions pour Antivirus Microsoft Defender](#add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus).

5. [Configurer vos groupes d’appareils, collections d’appareils et unités d’organisation.](#set-up-your-device-groups-device-collections-and-organizational-units)

6. [Configurer des stratégies de logiciel anti-programme malveillant et une protection en temps réel.](#configure-antimalware-policies-and-real-time-protection)

## <a name="enable-microsoft-defender-antivirus-and-confirm-its-in-passive-mode"></a>Activer Antivirus Microsoft Defender et vérifier qu’il est en mode passif

Sur certaines versions de Windows, telles que Windows Server, Antivirus Microsoft Defender a peut-être été désinstallé ou désactivé lors de l’installation de votre solution Mc Antivirus. Lorsque vous êtes prêt à intégrer vos points de terminaison à Defender pour le point de terminaison, Antivirus Microsoft Defender n’entre pas en mode passif ou désactivé automatiquement. En outre, sur Windows Server, vous ne pouvez pas avoir de Antivirus Microsoft Defender en mode actif à côté d’une solution antivirus/anti-programme malveillant non Microsoft, telle que Mc Symantec, etc. Pour en savoir plus sur ce qui se passe avec Defender pour les solutions de point de terminaison et antivirus, [voir Antivirus Microsoft Defender compatibilité.](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility)

Pour vous assurer que la Antivirus Microsoft Defender est activée et en mode passif, complétez les tâches suivantes décrites dans cet article :

- [Définition de DisableAntiSpyware sur false sur Windows Server](#set-disableantispyware-to-false-on-windows-server)

- [Réinstaller Antivirus Microsoft Defender sur Windows Server ;](#reinstall-microsoft-defender-antivirus-on-windows-server)

- [Définition Antivirus Microsoft Defender mode passif sur Windows Server](#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server)

- [Activation de Antivirus Microsoft Defender sur vos Windows clients ;](#enable-microsoft-defender-antivirus-on-your-windows-client-devices) et

- [Confirmant que le Antivirus Microsoft Defender est en mode passif.](#confirm-that-microsoft-defender-antivirus-is-in-passive-mode)  

### <a name="set-disableantispyware-to-false-on-windows-server"></a>Définir DisableAntiSpyware sur false sur Windows Server

La clé de Registre [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) a été utilisée dans le passé pour désactiver Antivirus Microsoft Defender et déployer un autre produit antivirus, tel que Mc Antivirus. En règle générale, vous ne devez pas avoir cette clé de Registre sur vos Windows et points de terminaison ; Toutefois, si vous avez configuré, voici comment définir sa valeur `DisableAntiSpyware` sur false :

1. Sur votre Windows server, ouvrez l’Éditeur du Registre.

2. Accédez à la page `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`.

3. Dans ce dossier, recherchez une entrée DWORD appelée **DisableAntiSpyware**.
   - Si vous ne voyez pas cette entrée, tout est prêt.
   - Si vous voyez **DisableAntiSpyware,** procédez à l’étape 4.

4. Cliquez avec le bouton droit sur la DWORD DisableAntiSpyware, puis choisissez **Modifier**.

5. Définissez la valeur sur `0` . (Cette action définit la valeur de la clé de Registre sur *false*.)

> [!TIP]
> Pour en savoir plus sur cette clé de Registre, voir [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware).

### <a name="reinstall-microsoft-defender-antivirus-on-windows-server"></a>Réinstaller Antivirus Microsoft Defender sur Windows Server

> [!NOTE]
> La procédure suivante s’applique uniquement aux points de terminaison ou appareils qui exécutent les versions de Windows :
> - Windows Server 2019
> - Windows Serveur, version 1803 (mode principal uniquement)
> - Windows Server 2016 (voir les informations importantes dans [l’Windows Server 2016 ?](#are-you-using-windows-server-2016))

1. En tant qu’administrateur local sur le point de terminaison ou l’appareil, ouvrez Windows PowerShell.

2. Exécutez les cmdlets PowerShell suivantes : <br/>   
   `Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender-Features` <p>
   `Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender` <br/>
 
    > [!NOTE]
    > Lorsque vous utilisez la commande DISM dans une séquence de tâches exécutant PS, le chemin d’accès cmd.exe est requis.
    > Exemple :<br/>
    > `c:\windows\sysnative\cmd.exe /c Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender-Features`<p>
    > `c:\windows\sysnative\cmd.exe /c Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender`<br/>

3. Pour vérifier Antivirus Microsoft Defender est en cours d’exécution, utilisez l’cmdlet PowerShell suivante : <br/>
   `Get-Service -Name windefend`

#### <a name="are-you-using-windows-server-2016"></a>Utilisez-vous Windows Server 2016 ?

Si vous avez des points de terminaison Windows Server 2016, vous ne pouvez pas exécuter Antivirus Microsoft Defender à côté d’une solution antivirus/anti-programme malveillant non-Microsoft. Antivirus Microsoft Defender ne peut pas s’exécuter en mode passif sur Windows Server 2016. Dans ce cas, vous devrez désinstaller la solution antivirus/anti-programme malveillant non Microsoft et installer/activer Antivirus Microsoft Defender à la place. Pour en savoir plus, [consultez la compatibilité des solutions antivirus avec Defender pour Endpoint.](microsoft-defender-antivirus-compatibility.md)

Si vous utilisez Windows Server 2016 et que vous avez des difficultés à activer Antivirus Microsoft Defender, utilisez l’cmdlet PowerShell suivante :

`mpcmdrun -wdenable`

> [!TIP]
> Vous avez encore besoin d’aide ? Voir [Antivirus Microsoft Defender sur Windows Server.](microsoft-defender-antivirus-on-windows-server.md)

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>Définir Antivirus Microsoft Defender en mode passif sur Windows Server

> [!IMPORTANT]
> Vous pouvez Antivirus Microsoft Defender le mode passif sur Windows Server, version 1803 ou plus récente, ou Windows Server 2019. Toutefois, le mode passif n’est pas pris en charge Windows Server 2016. Pour en savoir plus, [consultez la compatibilité des solutions antivirus avec Microsoft Defender pour Endpoint.](defender-compatibility.md)

Étant donné que votre organisation utilise toujours votre solution de protection de point de terminaison existante, vous devez Antivirus Microsoft Defender le mode passif. Ainsi, votre solution et votre Antivirus Microsoft Defender peuvent s’exécuter côte à côte jusqu’à ce que vous avez terminé l’intégration à Microsoft Defender pour endpoint.

1. Ouvrez l’Éditeur du Registre, puis accédez à <br/>
   `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. Modifiez (ou créez) une entrée DWORD appelée **ForcePassiveMode** et spécifiez les paramètres suivants :
   - Définissez la valeur DWORD sur **1**.
   - Sous **Base,** **sélectionnez Hexadécimal**.

> [!NOTE]
> Vous pouvez utiliser d’autres méthodes pour définir la clé de Registre, telles que les suivantes :
>- [Préférence de stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn581922(v=ws.11))
>- [Outil d’objet de stratégie de groupe local](/windows/security/threat-protection/security-compliance-toolkit-10#what-is-the-local-group-policy-object-lgpo-tool)
>- [Un package dans Configuration Manager](/mem/configmgr/apps/deploy-use/packages-and-programs)

### <a name="enable-microsoft-defender-antivirus-on-your-windows-client-devices"></a>Activer Antivirus Microsoft Defender sur vos appareils clients Windows client

Étant donné que votre organisation utilise une solution antivirus non Microsoft, Antivirus Microsoft Defender est probablement désactivée sur les appareils Windows de votre organisation. Cette étape du processus de migration implique l’activation Antivirus Microsoft Defender. 

Pour activer Antivirus Microsoft Defender, nous vous recommandons d’utiliser Intune. Toutefois, vous pouvez utiliser n’importe quelle méthode répertoriée dans le tableau suivant :

|Méthode  |Procédure  |
|---------|---------|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/>**REMARQUE**: Intune est désormais Microsoft Endpoint Manager. | 1. Go to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and sign in.<p> 2. Sélectionnez les  >  **profils de configuration des** appareils, puis sélectionnez le type de profil que vous souhaitez configurer. Si vous n’avez pas encore créé de type de profil de **restrictions** d’appareil, ou si vous souhaitez en créer un nouveau, voir Configurer les [paramètres](/intune/device-restrictions-configure)de restriction d’appareil dans Microsoft Intune .<p> 3. Sélectionnez **propriétés,** puis sélectionnez **Paramètres de configuration : Modifier**.<p> 4. **Développez Antivirus Microsoft Defender**. <p> 5. Activez **la protection cloud.**<p> 6. Dans la demande **d’utilisateurs** avant la soumission d’exemples, sélectionnez Envoyer tous **les exemples automatiquement.**<p> 7. Dans la dropdown **Détecter les applications potentiellement indésirables,** **sélectionnez Activer** ou **Auditer.**<p> 8. **Sélectionnez Révision + Enregistrer,** puis sélectionnez **Enregistrer.**<p>**CONSEIL**: pour plus d’informations sur les profils d’appareil Intune, notamment sur la création et la configuration de leurs paramètres, consultez les Microsoft Intune [profils d’appareil .](/intune/device-profiles)|
|Panneau de Windows     |Suivez les instructions ci-après [: Antivirus Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows). <p>**REMARQUE**: vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender dans certaines versions de Windows.         |
|[Gestion avancée des stratégies de groupe](/microsoft-desktop-optimization-pack/agpm/) <br/>ou<br/>[Console de gestion des stratégies de groupe ](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)  | 1. Go to **Computer configuration**  >  **Administrative templates** Windows  >  **components**  >  **Antivirus Microsoft Defender**. <p> 2. Recherchez une stratégie appelée **Désactiver Antivirus Microsoft Defender**.<p> 3. Choisissez **Modifier le paramètre de stratégie** et assurez-vous que la stratégie est désactivée. Cette action active la Antivirus Microsoft Defender. <p>**REMARQUE**: vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender dans certaines versions de Windows.  |


### <a name="confirm-that-microsoft-defender-antivirus-is-in-passive-mode"></a>Vérifier que Antivirus Microsoft Defender est en mode passif

Antivirus Microsoft Defender peut s’exécuter avec votre solution de protection de point de terminaison existante si vous Antivirus Microsoft Defender le mode passif. Vous pouvez utiliser l’invite de commandes ou PowerShell pour effectuer cette tâche, comme décrit dans le tableau suivant :

|Méthode  |Procédure  |
|---------|---------|
|Invite de commandes     | 1. Sur un Windows, ouvrez l’invite de commandes en tant qu’administrateur.<p>2. `sc query windefend` Tapez, puis appuyez sur Entrée.<p>3. Examinez les résultats pour vérifier que Antivirus Microsoft Defender est en cours d’exécution en mode passif.         |
|PowerShell     | 1. Sur un appareil Windows, ouvrez Windows PowerShell en tant qu’administrateur.<p>2. Exécutez la cmdlet [Get-MpComputerStatus.](/powershell/module/defender/Get-MpComputerStatus) <p>3. Dans la liste des résultats, recherchez **AMRunningMode : Mode passif** ou **AMRunningMode : Mode passif SxS**.          |

> [!NOTE]
> Vous pouvez voir *Antivirus Windows Defender* au lieu de *Antivirus Microsoft Defender* dans certaines versions de Windows.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Obtenir les mises à jour de Antivirus Microsoft Defender

Maintenir Antivirus Microsoft Defender à jour est essentiel pour garantir que vos appareils disposent des dernières technologies et fonctionnalités nécessaires pour se protéger contre les nouveaux programmes malveillants et les nouvelles techniques d’attaque, même si Antivirus Microsoft Defender s’exécute en [mode passif.](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility)

Il existe deux types de mises à jour liées à la mise Antivirus Microsoft Defender jour :
- Mises à jour de l’intelligence de la sécurité
- Mises à jour de produit

Pour obtenir vos mises à jour, suivez les instructions de la Antivirus Microsoft Defender mises à jour [et appliquez les lignes de base.](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus)

## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution"></a>Ajouter Microsoft Defender pour le point de terminaison à la liste d’exclusions de votre solution existante

Cette étape du processus de configuration implique l’ajout de Microsoft Defender for Endpoint à la liste d’exclusions de votre solution de protection de point de terminaison existante et de tous les autres produits de sécurité que votre organisation utilise. 

> [!TIP]
> Pour obtenir de l’aide sur la configuration des exclusions, reportez-vous à la documentation de votre fournisseur de solutions.

Les exclusions spécifiques à configurer dépendent de la version de Windows vos points de terminaison ou appareils en cours d’exécution et sont répertoriées dans le tableau suivant :

|SYSTÈME D’EXPLOITATION |Exclusions |
|--|--|
|Windows 10, [version 1803 ou](/windows/release-health/status-windows-10-1803) ultérieure (voir Windows 10 de [publication)](/windows/release-health/release-information)<p>Windows 10, version 1703 ou 1709 avec [KB4493441](https://support.microsoft.com/help/4493441) installé <p>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<p>[Windows Serveur, version 1803](/windows-server/get-started/whats-new-in-windows-server-1803) |`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<p>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<p>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<p>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`<p>  |
|[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2) <p>[Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<p>[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<p>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<p>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<p>**REMARQUE**: les fichiers temporaires de l’hôte de surveillance 6\45 peuvent être des sous-dossiers numérotés différents. <p>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>Ajoutez votre solution existante à la liste d’exclusions Antivirus Microsoft Defender

Au cours de cette étape du processus de configuration, vous ajoutez votre solution existante à la liste d Antivirus Microsoft Defender exclusion. 

Lorsque vous ajoutez [des exclusions Antivirus Microsoft Defender analyses,](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus)vous devez ajouter des exclusions de chemin d’accès et de processus. Gardez les points suivants à l’esprit :

- Les exclusions de chemin d’accès excluent des fichiers spécifiques et tout ce à quoi ces fichiers ont accès.

- Les exclusions de processus excluent tout ce qui touche un processus, mais n’excluent pas le processus lui-même.

- Si vous listez chaque exécutable (.exe) en tant qu’exclusion de chemin d’accès et exclusion de processus, le processus et tout ce qu’il touche sont exclus.

- List your process exclusions using their full path and not by their name only. (La méthode de nom uniquement est moins sécurisée.)

Vous pouvez choisir parmi plusieurs méthodes pour ajouter vos exclusions à Antivirus Microsoft Defender, comme répertorié dans le tableau suivant :

|Méthode | Procédure|
|--|--|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/>**REMARQUE**: Intune est désormais Microsoft Endpoint Manager. | 1. Go to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and sign in.<p> 2. Sélectionnez les  >  **profils de configuration des** appareils, puis sélectionnez le profil à configurer.<p> 3. Sous **Gérer,** sélectionnez **Propriétés.**<p> 4. Sélectionnez **paramètres de configuration : Modifier.**<p> 5. **Développez Antivirus Microsoft Defender,** puis développez **Antivirus Microsoft Defender exclusions.**<p> 6. Spécifiez les fichiers et dossiers, extensions et processus à exclure de Antivirus Microsoft Defender analyses. Pour référence, voir [Antivirus Microsoft Defender exclusions.](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions)<p> 7. Choisissez **Révision + Enregistrer,** puis **Enregistrer.**  |
|[Microsoft Endpoint Configuration Manager](/mem/configmgr/) | 1. À l’aide de la [console Configuration Manager,](/mem/configmgr/core/servers/manage/admin-console)go to **Assets and Compliance**  >  **Endpoint Protection**  >  **Antimalware Policies,** and then select the policy that you want to modify. <p> 2. Spécifiez les paramètres d’exclusion pour les fichiers et les dossiers, les extensions et les processus à exclure de Antivirus Microsoft Defender analyses. |
|[Objet de stratégie de groupe](/previous-versions/windows/desktop/Policy/group-policy-objects) | 1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](https://technet.microsoft.com/library/cc731212.aspx)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier.**<p> 2. Dans l’Éditeur de gestion des **stratégies** de groupe, sélectionnez **Configuration** ordinateur et **sélectionnez Modèles d’administration.**<p> 3. Développez l’arborescence **pour Windows composants > Antivirus Microsoft Defender > exclusions**.<br/>**REMARQUE**: vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender dans certaines versions de Windows. <p> 4. Double-cliquez sur le paramètre **Exclusions** de chemin d’accès et ajoutez les exclusions.<br/>- Définissez l’option **sur Activé.**<br/>- Sous la section **Options,** sélectionnez **Afficher...**.<br/>- Spécifiez chaque dossier sur sa propre ligne sous la **colonne Nom de** la valeur.<br/>- Si vous spécifiez un fichier, veillez à entrer un chemin d’accès complet au fichier, y compris la lettre de lecteur, le chemin d’accès au dossier, le nom de fichier et l’extension. Entrez **0 dans** la **colonne** Valeur.<p> 5. Sélectionnez **OK**.<p> 6. Double-cliquez sur le paramètre **Exclusions d’extensions** et ajoutez les exclusions.<br/>- Définissez l’option **sur Activé.**<br/>- Sous la section **Options,** sélectionnez **Afficher...**.<br/>- Entrez chaque extension de fichier sur sa propre ligne sous la **colonne Nom de** la valeur.  Entrez **0 dans** la **colonne** Valeur.<p> 7. Sélectionnez **OK**. |
|Objet de stratégie de groupe local |1. Sur le point de terminaison ou l’appareil, ouvrez l’Éditeur de stratégie de groupe local. <p>2. Go to **Computer Configuration**  >  **Administrative Templates** Windows  >  **Components**  >  **Antivirus Microsoft Defender**  >  **Exclusions**.<p>**REMARQUE**: vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender dans certaines versions de Windows. <p>3. Spécifiez votre chemin d’accès et les exclusions de processus. |
|Clé du Registre |1. Exporte la clé de Registre suivante : `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions` .<p>2. Importez la clé de Registre. Voici deux exemples :<br/>- Chemin d’accès local : `regedit.exe /s c:\temp\ MDAV_Exclusion.reg` <br/>- Partage réseau : `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg` |

## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>Configurer vos groupes d’appareils, collections d’appareils et unités d’organisation

| Type de collection | Procédure |
|--|--|
|[Les groupes d’appareils](/microsoft-365/security/defender-endpoint/machine-groups) (anciennement appelés groupes d’ordinateurs) permettent à votre équipe des opérations de sécurité de configurer des fonctionnalités de sécurité, telles que l’examen et la correction automatisés.<p>Les groupes d’appareils sont également utiles pour attribuer l’accès à ces appareils afin que votre équipe des opérations de sécurité puisse prendre des mesures correctives si nécessaire. <p>Les groupes d’appareils sont créés dans le Centre de sécurité Microsoft Defender. |1. Go to the Centre de sécurité Microsoft Defender ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ).<p>2. Dans le volet de navigation sur la gauche, choisissez Paramètres groupes d’appareils  >  **Autorisations.**  >    <p>3. Choisissez **+ Ajouter un groupe d’appareils.**<p>4. Spécifiez un nom et une description pour le groupe d’appareils.<p>5. Dans la liste de **niveau Automation,** sélectionnez une option. (Nous vous recommandons **de corriger les menaces automatiquement.** Pour en savoir plus sur les différents niveaux d’automatisation, voir [comment les menaces sont corrigés.](/microsoft-365/security/defender-endpoint/automated-investigations#how-threats-are-remediated)<p>6. Spécifiez les conditions d’une règle correspondante pour déterminer quels appareils appartiennent au groupe d’appareils. Par exemple, vous pouvez choisir un domaine, des versions de système d’exploitation ou même utiliser des [balises d’appareil.](/microsoft-365/security/defender-endpoint/machine-tags)<p>7. Sous **l’onglet** Accès utilisateur, spécifiez les rôles qui doivent avoir accès aux appareils inclus dans le groupe d’appareils. <p>8. Choisissez **Terminé**. |
|[Les collections d’appareils](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) permettent à votre équipe des opérations de sécurité de gérer les applications, de déployer les paramètres de conformité ou d’installer des mises à jour logicielles sur les appareils de votre organisation.<p>Les collections d’appareils sont créées à l’aide [de Configuration Manager.](/mem/configmgr/) |Suivez les étapes de [la procédure de création d’une collection.](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create) |
|[Les unités d’organisation](/azure/active-directory-domain-services/create-ou) vous permettent de grouper logiquement des objets tels que des comptes d’utilisateur, des comptes de service ou des comptes d’ordinateur. Vous pouvez ensuite affecter des administrateurs à des unités d’organisation spécifiques et appliquer une stratégie de groupe pour appliquer des paramètres de configuration ciblés.<p> Les unités d’organisation sont définies [dans Azure Active Directory Services de domaine.](/azure/active-directory-domain-services) | Suivez les étapes de la section Créer une unité [d’organisation dans Azure Active Directory domaine](/azure/active-directory-domain-services/create-ou)géré des services de domaine. |

## <a name="configure-antimalware-policies-and-real-time-protection"></a>Configurer les stratégies de logiciel anti-programme malveillant et la protection en temps réel

À l’aide de Configuration Manager et de vos collections d’appareils, configurez vos stratégies anti-programme malveillant.

- Voir [Créer et déployer des stratégies de logiciel anti-programme malveillant pour Endpoint Protection dans Configuration Manager.](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies)

- Pendant que vous créez et configurez vos stratégies de logiciel [anti-programme](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) malveillant, veillez à passer en revue les paramètres de protection en temps réel et à activer [bloquer à la première vue.](configure-block-at-first-sight-microsoft-defender-antivirus.md)

> [!TIP]
> Vous pouvez déployer les stratégies avant les appareils de votre organisation sur les appareils intégrés.

## <a name="next-step"></a>Étape suivante

**Félicitations**! Vous avez terminé la phase d’installation [du basculement vers Microsoft Defender pour le point de terminaison](switch-to-microsoft-defender-migration.md#the-migration-process)!

- [Passer à la phase 3 : intégration à Microsoft Defender pour endpoint](switch-to-microsoft-defender-onboard.md)
