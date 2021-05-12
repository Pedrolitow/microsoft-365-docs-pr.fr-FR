---
title: Symantec vers Microsoft Defender pour le point de terminaison - Phase 2, Configuration
description: Il s’agit de la phase 2 du programme d’installation de la migration de Symantec vers Microsoft Defender pour endpoint
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
- m365solution-symantecmigrate
ms.topic: article
ms.date: 05/10/2021
ms.custom: migrationguides
ms.reviewer: depicker, yongrhee, chriggs
ms.openlocfilehash: aff6439c08a4f8540a10589a436893c62e48d756
ms.sourcegitcommit: 68383240ef7a673d5f28e2ecfab9f105bf1d8c8f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "52327401"
---
# <a name="migrate-from-symantec---phase-2-set-up-microsoft-defender-for-endpoint"></a>Migrer à partir de Symantec - Phase 2 : Configurer Microsoft Defender pour le point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![Phase 1 : préparation](images/phase-diagrams/prepare.png)](symantec-to-microsoft-defender-atp-prepare.md)<br/>[Phase 1 : préparation](symantec-to-microsoft-defender-atp-prepare.md) |![Phase 2 : configuration](images/phase-diagrams/setup.png)<br/>Phase 2 : configuration |[![Phase 3 : intégration](images/phase-diagrams/onboard.png)](symantec-to-microsoft-defender-atp-onboard.md)<br/>[Phase 3 : intégration](symantec-to-microsoft-defender-atp-onboard.md) |
|--|--|--|
||*Vous êtes là !* | |


**Bienvenue dans la phase d’installation [de la migration de Symantec vers Microsoft Defender pour Point de terminaison.](symantec-to-microsoft-defender-endpoint-migration.md#the-migration-process)** Cette phase comprend les étapes suivantes :
1. [Activez ou réinstallez Antivirus Microsoft Defender (pour certaines versions de Windows)](#enable-or-reinstall-microsoft-defender-antivirus-for-certain-versions-of-windows).
2. [Activez Antivirus Microsoft Defender](#enable-microsoft-defender-antivirus).
3. [Obtenir les mises à jour de Antivirus Microsoft Defender](#get-updates-for-microsoft-defender-antivirus).
4. [Ajoutez Microsoft Defender pour le point de terminaison à la liste d’exclusions de Symantec.](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-symantec)
5. [Ajoutez Symantec à la liste d’exclusions Antivirus Microsoft Defender](#add-symantec-to-the-exclusion-list-for-microsoft-defender-antivirus).
6. [Configurer vos groupes d’appareils, collections d’appareils et unités d’organisation.](#set-up-your-device-groups-device-collections-and-organizational-units)
7. [Configurer des stratégies de logiciel anti-programme malveillant et une protection en temps réel.](#configure-antimalware-policies-and-real-time-protection)

## <a name="enable-or-reinstall-microsoft-defender-antivirus-for-certain-versions-of-windows"></a>Activer ou réinstaller Antivirus Microsoft Defender (pour certaines versions de Windows)

> [!TIP]
> Si vous exécutez Windows 10, vous n’avez pas besoin d’effectuer cette tâche. Continuez à **[Activer Antivirus Microsoft Defender](#enable-microsoft-defender-antivirus)**.

Sur certaines versions de Windows, Antivirus Microsoft Defender ont peut-être été désinstallées ou désactivées. En effet, Antivirus Microsoft Defender n’entre pas en mode passif ou désactivé lorsque vous installez un produit antivirus tiers, tel que Symantec. Pour plus d’informations, [voir Antivirus Microsoft Defender compatibilité.](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility) 

Maintenant que vous êtes en train de passer de Symantec à Microsoft Defender pour point de terminaison, vous devez activer ou réinstaller Antivirus Microsoft Defender et le définir en mode passif. 

### <a name="reinstall-microsoft-defender-antivirus-on-windows-server"></a>Réinstaller Antivirus Microsoft Defender sur Windows Server

> [!NOTE]
> La procédure suivante s’applique uniquement aux points de terminaison ou appareils qui exécutent les versions de Windows :
> - Windows Server 2019
> - Windows Serveur, version 1803 (mode principal uniquement)
> - Windows Server 2016
> 
> Antivirus Microsoft Defender est intégré à Windows 10, mais il peut être désactivé. Dans ce cas, procédez à [l’Antivirus Microsoft Defender](#enable-microsoft-defender-antivirus).

1. En tant qu’administrateur local sur le point de terminaison ou l’appareil, ouvrez Windows PowerShell.

1. Exécutez les cmdlets PowerShell suivantes :<br/>
   `Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender-Features` <br/>
   `Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender`

    > [!NOTE]
    > Lorsque vous utilisez la commande DISM dans une séquence de tâches exécutant PS, le chemin d’accès cmd.exe est requis.
    > Exemple :<br/>
    > `c:\windows\sysnative\cmd.exe /c Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender-Features`<br/>
    > `c:\windows\sysnative\cmd.exe /c Dism /online /Get-FeatureInfo /FeatureName:Windows-Defender`<br/>

3. Pour vérifier Antivirus Microsoft Defender est en cours d’exécution, utilisez l’cmdlet PowerShell suivante : <br/>
   `Get-Service -Name windefend`

#### <a name="are-you-using-windows-server-2016"></a>Utilisez-vous Windows Server 2016 ?

Si vous utilisez Windows Server 2016 et que vous avez des difficultés à activer Antivirus Microsoft Defender, utilisez l’cmdlet PowerShell suivante :

`mpcmdrun -wdenable`

> [!TIP]
> Vous avez encore besoin d’aide ? Voir [Antivirus Microsoft Defender sur Windows Server 2016 et 2019](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-on-windows-server-2016).

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>Définir Antivirus Microsoft Defender en mode passif sur Windows Server

Étant donné que votre organisation utilise toujours Symantec, vous devez définir Antivirus Microsoft Defender en mode passif. De cette façon, Symantec et Antivirus Microsoft Defender peuvent s’exécuter côte à côte jusqu’à ce que vous avez terminé l’intégration à Microsoft Defender pour Endpoint.

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

## <a name="enable-microsoft-defender-antivirus"></a>Activer Antivirus Microsoft Defender

Étant donné que votre organisation utilise Symantec comme solution antivirus principale, Antivirus Microsoft Defender est probablement désactivée sur les appareils Windows de votre organisation. Cette étape du processus de migration implique l’activation Antivirus Microsoft Defender. 

Pour activer Antivirus Microsoft Defender, nous vous recommandons d’utiliser Intune. Toutefois, vous pouvez utiliser n’importe quelle méthode répertoriée dans le tableau suivant :

|Méthode  |Procédure  |
|---------|---------|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/>**REMARQUE**: Intune est désormais Microsoft Endpoint Manager. |1. Go to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and sign in.<p>2. Sélectionnez les  >  **profils de configuration des** appareils, puis sélectionnez le type de profil que vous souhaitez configurer. Si vous n’avez pas encore créé de type de profil de **restrictions** d’appareil, ou si vous souhaitez en créer un nouveau, voir Configurer les [paramètres](/intune/device-restrictions-configure)de restriction d’appareil dans Microsoft Intune .<p>3. Sélectionnez **propriétés,** puis sélectionnez **Paramètres de configuration : Modifier**.<p>4. **Développez Antivirus Microsoft Defender**. <p>5. Activez **la protection cloud.**<p>6. Dans la demande **d’utilisateurs** avant la soumission d’exemples, sélectionnez Envoyer tous **les exemples automatiquement.**<p>7. Dans la dropdown **Détecter les applications potentiellement indésirables,** sélectionnez **Activer** ou **Auditer.**<p>8. Sélectionnez **Révision + Enregistrer,** puis sélectionnez **Enregistrer.**<br/>Pour plus d’informations sur les profils d’appareil Intune, notamment sur la création et la configuration de leurs paramètres, consultez la Microsoft Intune [profils d’appareil .](/intune/device-profiles)|
|Panneau de Windows     |Suivez les instructions ci-après [: Antivirus Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows). <br/>**REMARQUE**: vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender dans certaines versions de Windows.         |
|[Gestion avancée des stratégies de groupe](/microsoft-desktop-optimization-pack/agpm/) <br/>ou<br/>[Console de gestion des stratégies de groupe ](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)  |1. Allez à `Computer configuration > Administrative templates > Windows components > Microsoft Defender Antivirus` . <p>2. Recherchez une stratégie appelée **Désactiver Antivirus Microsoft Defender**.<p>3. Choisissez **Modifier le paramètre de stratégie** et assurez-vous que la stratégie est désactivée. Cela permet d’Antivirus Microsoft Defender. <p>**REMARQUE**: vous pouvez voir *Antivirus Windows Defender* de Antivirus Microsoft Defender dans certaines versions de Windows.  |

### <a name="verify-that-microsoft-defender-antivirus-is-in-passive-mode"></a>Vérifier que Antivirus Microsoft Defender est en mode passif

Antivirus Microsoft Defender peut s’exécuter avec Symantec si vous Antivirus Microsoft Defender le mode passif. Vous pouvez utiliser l’invite de commandes ou PowerShell pour effectuer cette tâche, comme décrit dans le tableau suivant :

|Méthode  |Procédure  |
|---------|---------|
|Invite de commandes     |1. Sur un Windows, ouvrez l’invite de commandes en tant qu’administrateur. <p>2. `sc query windefend` Tapez, puis appuyez sur Entrée.<p>3. Examinez les résultats pour vérifier que Antivirus Microsoft Defender est en cours d’exécution en mode passif.         |
|PowerShell     |1. Sur un appareil Windows, ouvrez Windows PowerShell en tant qu’administrateur.<p>2. Exécutez la cmdlet [Get-MpComputerStatus.](/powershell/module/defender/Get-MpComputerStatus)<p>3. Dans la liste des résultats, recherchez **AMRunningMode : Mode passif** ou **AMRunningMode : Mode passif SxS**.|

> [!NOTE]
> Vous pouvez voir *Windows Defender antivirus au* lieu de *l’Antivirus Microsoft Defender* dans certaines versions de Windows.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Obtenir les mises à jour de l’Antivirus Microsoft Defender

Maintenir l’Antivirus Microsoft Defender à jour est essentiel pour garantir que vos appareils disposent des dernières technologies et fonctionnalités nécessaires pour se protéger contre les nouveaux programmes malveillants et les nouvelles techniques d’attaque, même si l’Antivirus Microsoft Defender s’exécute en [mode passif.](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility)

Il existe deux types de mises à jour liées à la mise à jour de l’Antivirus Microsoft Defender :
- Mises à jour de l’intelligence de la sécurité
- Mises à jour de produit

Pour obtenir vos mises à jour, suivez les instructions dans Gérer les mises à jour [de l’Antivirus Microsoft Defender et appliquez les lignes de base.](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus)

## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-symantec"></a>Ajouter Microsoft Defender pour le point de terminaison à la liste d’exclusions pour Symantec

Cette étape du processus de configuration implique l’ajout de Microsoft Defender for Endpoint à la liste d’exclusions de Symantec et de tous les autres produits de sécurité que votre organisation utilise. Les exclusions spécifiques à configurer dépendent de la version de Windows en cours d’exécution de vos points de terminaison ou appareils et sont répertoriées dans le tableau suivant :

|SYSTÈME D’EXPLOITATION |Exclusions |
|--|--|
|- Windows 10, [version 1803 ou](/windows/release-health/status-windows-10-1803) ultérieure (voir les informations de publication [de Windows 10)](/windows/release-health/release-information)<br/>- Windows 10, version 1703 ou 1709 avec [KB4493441](https://support.microsoft.com/help/4493441) installé <br/>- [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/>- [Windows Server, version 1803](/windows-server/get-started/whats-new-in-windows-server-1803) |`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<p>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<p>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<p>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`<p>  |
|- [Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2) <p>- [Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<p>- [Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<p>- [Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<p>- [Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<p>**REMARQUE**: les fichiers temporaires de l’hôte de surveillance 6\45 peuvent être des sous-dossiers numérotés différents.<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<p>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-symantec-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>Ajouter Symantec à la liste d’exclusions pour l’Antivirus Microsoft Defender

Au cours de cette étape du processus de configuration, vous ajoutez Symantec et vos autres solutions de sécurité à la liste d’exclusions de l’Antivirus Microsoft Defender. 

> [!NOTE]
> Pour avoir une idée des processus et services à exclure, voir Processus et services broadcom utilisés par [Endpoint Protection 14.](https://knowledge.broadcom.com/external/article/170706/processes-and-services-used-by-endpoint.html)

Lorsque vous ajoutez des exclusions aux analyses de [l’Antivirus Microsoft Defender,](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus)vous devez ajouter des exclusions de chemin d’accès et de processus. Gardez les points suivants à l’esprit :
- Les exclusions de chemin d’accès excluent des fichiers spécifiques et tout ce à quoi ces fichiers ont accès.
- Les exclusions de processus excluent tout ce qui touche un processus, mais n’excluent pas le processus lui-même.
- Si vous listez chaque exécutable (.exe) en tant qu’exclusion de chemin d’accès et exclusion de processus, le processus et tout ce qu’il touche sont exclus.
- List your process exclusions using their full path and not by their name only. (La méthode de nom uniquement est moins sécurisée.)

Vous pouvez choisir parmi plusieurs méthodes pour ajouter vos exclusions à l’Antivirus Microsoft Defender, comme répertorié dans le tableau suivant :

|Méthode | Procédure|
|--|--|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/>**REMARQUE**: Intune est désormais Microsoft Endpoint Manager. |1. Go to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and sign in.<p>2. Sélectionnez les  >  **profils de configuration des** appareils, puis sélectionnez le profil à configurer.<p>3. Sous **Gérer,** sélectionnez **Propriétés.** <p>4. Sélectionnez **les paramètres de configuration : Modifier.**<p>5. Développez **l’Antivirus Microsoft Defender,** puis développez Les **exclusions de l’antivirus Microsoft Defender.**<p>6. Spécifiez les fichiers et dossiers, extensions et processus à exclure des analyses de l’Antivirus Microsoft Defender. Pour plus d’actualités, [consultez les exclusions de l’Antivirus Microsoft Defender.](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions)<p>7. Choisissez **Révision + Enregistrer,** puis **Enregistrer.**  |
|[Microsoft Endpoint Configuration Manager](/mem/configmgr/) |1. À l’aide de la [console Configuration Manager,](/mem/configmgr/core/servers/manage/admin-console)sélectionnez Stratégies anti-programme malveillant **Assets and Compliance**  >  **Endpoint Protection,** puis sélectionnez la stratégie à  >  modifier. <p>2. Spécifiez les paramètres d’exclusion pour les fichiers et dossiers, les extensions et les processus à exclure des analyses de l’Antivirus Microsoft Defender. |
|[Objet de stratégie de groupe](/previous-versions/windows/desktop/Policy/group-policy-objects) | 1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](https://technet.microsoft.com/library/cc731212.aspx)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**<p>2. Dans l’Éditeur de gestion des **stratégies** de groupe, allez à **Configuration** ordinateur et cliquez sur **Modèles d’administration.**<p>3. Développez l’arborescence des **composants Windows > Exclusions**> Antivirus Microsoft Defender.<br/>**REMARQUE**: il se peut que *vous Windows Defender antivirus Microsoft* Defender à la place de l’Antivirus Microsoft *Defender* dans certaines versions de Windows.<p>4. Double-cliquez sur le paramètre **Exclusions** de chemin d’accès et ajoutez les exclusions.<p>- Définissez l’option **sur Activé.**<p>- Sous la section **Options,** cliquez sur **Afficher...**.<p>- Spécifiez chaque dossier sur sa propre ligne sous la **colonne Nom de** la valeur.<p>- Si vous spécifiez un fichier, veillez à entrer un chemin d’accès complet au fichier, y compris la lettre de lecteur, le chemin d’accès au dossier, le nom de fichier et l’extension. Entrez **0 dans** la **colonne** Valeur.<p>5. Cliquez sur **OK.**<p>6. Double-cliquez sur le paramètre **Exclusions d’extensions** et ajoutez les exclusions.<p>- Définissez l’option **sur Activé.**<p>- Sous la section **Options,** cliquez sur **Afficher...**.<p>- Entrez chaque extension de fichier sur sa propre ligne sous la **colonne Nom de** la valeur.  Entrez **0 dans** la **colonne** Valeur.<br/>7. Cliquez sur **OK.** |
|Objet de stratégie de groupe local |1. Sur le point de terminaison ou l’appareil, ouvrez l’Éditeur de stratégie de groupe local. <p>2. Go to **Computer Configuration**  >  **Administrative Templates** Windows  >  **Components** Microsoft Defender  >  **Antivirus**  >  **Exclusions**. <br/>**REMARQUE**: il se peut que *vous Windows Defender antivirus Microsoft* Defender à la place de l’Antivirus Microsoft *Defender* dans certaines versions de Windows.<p>3. Spécifiez votre chemin d’accès et les exclusions de processus. |
|Clé du Registre |1. Exporte la clé de Registre suivante : `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions` .<p>2. Importez la clé de Registre. Voici deux exemples :<br/>- Chemin d’accès local : `regedit.exe /s c:\temp\ MDAV_Exclusion.reg` <br/>- Partage réseau : `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg` |

## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>Configurer vos groupes d’appareils, collections d’appareils et unités d’organisation

| Type de collection | Procédure |
|--|--|
|[Les groupes d’appareils](/microsoft-365/security/defender-endpoint/machine-groups) (anciennement appelés groupes d’ordinateurs) permettent à votre équipe des opérations de sécurité de configurer des fonctionnalités de sécurité, telles que l’examen et la correction automatisés.<br/> Les groupes d’appareils sont également utiles pour attribuer l’accès à ces appareils afin que votre équipe des opérations de sécurité puisse prendre des mesures correctives si nécessaire. <br/>Les groupes d’appareils sont créés dans le Centre de sécurité Microsoft Defender. |1. Go to the Microsoft Defender Security Center ( [https://aka.ms/MDATPportal](https://aka.ms/MDATPportal) ).<p>2. Dans le volet de navigation de gauche, sélectionnez **Groupes** d’appareils  >  **Paramètres Autorisations.**  >    <p>3. Choisissez **+ Ajouter un groupe d’appareils.**<p>4. Spécifiez un nom et une description pour le groupe d’appareils.<p>5. Dans la liste de **niveau Automation,** sélectionnez une option. (Nous vous recommandons **de corriger les menaces automatiquement.** Pour en savoir plus sur les différents niveaux d’automatisation, voir [comment les menaces sont corrigés.](/microsoft-365/security/defender-endpoint/automated-investigations#how-threats-are-remediated)<p>6. Spécifiez les conditions d’une règle correspondante pour déterminer quels appareils appartiennent au groupe d’appareils. Par exemple, vous pouvez choisir un domaine, des versions de système d’exploitation ou même utiliser des [balises d’appareil.](/microsoft-365/security/defender-endpoint/machine-tags)<br/> <br/>7. Sous **l’onglet** Accès utilisateur, spécifiez les rôles qui doivent avoir accès aux appareils inclus dans le groupe d’appareils. <p>8. Choisissez **Terminé**. |
|[Les collections d’appareils](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) permettent à votre équipe des opérations de sécurité de gérer les applications, de déployer les paramètres de conformité ou d’installer des mises à jour logicielles sur les appareils de votre organisation. <br/>Les collections d’appareils sont créées à l’aide [de Configuration Manager.](/mem/configmgr/) |Suivez les étapes de [la procédure de création d’une collection.](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create) |
|[Les unités d’organisation](/azure/active-directory-domain-services/create-ou) vous permettent de grouper logiquement des objets tels que des comptes d’utilisateur, des comptes de service ou des comptes d’ordinateur. Vous pouvez ensuite affecter des administrateurs à des unités d’organisation spécifiques et appliquer une stratégie de groupe pour appliquer des paramètres de configuration ciblés.<br/> Les unités d’organisation sont définies dans les services de [domaine Azure Active Directory.](/azure/active-directory-domain-services) | Suivez les étapes de [création d’une unité d’organisation](/azure/active-directory-domain-services/create-ou)dans un domaine géré Azure Active Directory Domain Services. |

## <a name="configure-antimalware-policies-and-real-time-protection"></a>Configurer les stratégies de logiciel anti-programme malveillant et la protection en temps réel

À l’aide de Configuration Manager et de vos collections d’appareils, configurez vos stratégies anti-programme malveillant.

- Voir [Créer et déployer des stratégies anti-programme malveillant pour Endpoint Protection dans Configuration Manager.](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies)

- Pendant que vous créez et configurez vos stratégies de logiciel [anti-programme](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) malveillant, veillez à passer en revue les paramètres de protection en temps réel et à activer [bloquer à la première vue.](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus)

> [!TIP]
> Vous pouvez déployer les stratégies avant les appareils de votre organisation sur les appareils intégrés.

## <a name="next-step"></a>Étape suivante

**Félicitations**! Vous avez terminé la phase d’installation [de la migration de Symantec vers Microsoft Defender pour Endpoint](symantec-to-microsoft-defender-endpoint-migration.md#the-migration-process)!
- [Passer à la phase 3 : intégration à Microsoft Defender pour endpoint](symantec-to-microsoft-defender-atp-onboard.md)
