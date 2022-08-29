---
title: Configurer les exclusions de l’Antivirus Microsoft Defender sur Windows Server
ms.reviewer: pahuijbr
manager: dansimp
description: Windows Server inclut des exclusions automatiques, en fonction du rôle serveur. Vous pouvez également ajouter des exclusions personnalisées.
keywords: exclusions, serveur, exclusions automatiques, automatique, personnalisée, analyses, Antivirus Microsoft Defender
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.collection: M365-security-compliance
ms.openlocfilehash: 7205a612954dfbd283b61ca377c81c5f78243f58
ms.sourcegitcommit: d09eb780dc41a01796eb8137fbe9267231af6746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2022
ms.locfileid: "67388680"
---
# <a name="configure-microsoft-defender-antivirus-exclusions-on-windows-server"></a>Configurer les exclusions de l’Antivirus Microsoft Defender sur Windows Server


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

L’Antivirus Microsoft Defender sur Windows Server 2016 et Windows Server 2019 vous inscrit automatiquement dans certaines exclusions, comme défini par votre rôle serveur spécifié. Ces exclusions n’apparaissent pas dans les listes d’exclusion standard affichées dans [l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md).

Outre les exclusions automatiques définies par le rôle serveur, vous pouvez ajouter ou supprimer des exclusions personnalisées. Pour ce faire, reportez-vous aux articles suivants :
- [Configurer et valider des exclusions en fonction du nom de fichier, de l’extension et de l’emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider les exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="a-few-points-to-keep-in-mind"></a>Quelques points à garder à l’esprit

- Les exclusions personnalisées sont prioritaires sur les exclusions automatiques.
- Les exclusions automatiques s’appliquent uniquement à l’analyse de [protection en temps réel (RTP](configure-protection-features-microsoft-defender-antivirus.md) ). 
- Les exclusions automatiques ne sont pas respectées lors d’une [analyse complète, rapide ou à la demande](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan).
- Les exclusions personnalisées et en double ne sont pas en conflit avec les exclusions automatiques.
- L’Antivirus Microsoft Defender utilise les outils DISM (Deployment Image Servicing and Management) pour déterminer les rôles installés sur votre ordinateur.
- Les exclusions appropriées doivent être définies pour les logiciels qui ne sont pas inclus dans le système d’exploitation.
- Windows Server 2012 R2 ne dispose pas de l’antivirus Microsoft Defender comme fonctionnalité installable. Lorsque vous intégrerez ces serveurs à Defender pour point de terminaison, vous installez l’Antivirus Microsoft Defender et les exclusions par défaut pour les fichiers du système d’exploitation sont appliquées. Toutefois, les exclusions pour les rôles serveur (comme spécifié ci-dessous) ne s’appliquent pas automatiquement, et vous devez configurer ces exclusions comme il convient. Pour plus d’informations, consultez [Intégrer des serveurs Windows au service Microsoft Defender pour point de terminaison](configure-server-endpoints.md).

Cet article fournit une vue d’ensemble des exclusions pour l’Antivirus Microsoft Defender sur Windows Server 2016 ou version ultérieure.

Étant donné que l’Antivirus Microsoft Defender est intégré à Windows Server 2016 et versions ultérieures, les exclusions pour les fichiers de système d’exploitation et les rôles serveur se produisent automatiquement. Toutefois, vous pouvez définir des exclusions personnalisées. Vous pouvez également refuser les exclusions automatiques si nécessaire.

Le présent article contient les sections suivantes :

|Section|Description|
|---|---|
|[Exclusions automatiques sur Windows Server 2016 ou version ultérieure](#automatic-exclusions-on-windows-server-2016-or-later)|Décrit les deux principaux types d’exclusions automatiques et inclut une liste détaillée des exclusions automatiques|
|[Refus des exclusions automatiques](#opting-out-of-automatic-exclusions)|Inclut des considérations et procédures importantes décrivant comment refuser les exclusions automatiques|
|[Définition d’exclusions personnalisées](#defining-custom-exclusions)|Fournit des liens vers des informations de procédure pour définir des exclusions personnalisées|

## <a name="automatic-exclusions-on-windows-server-2016-or-later"></a>Exclusions automatiques sur Windows Server 2016 ou version ultérieure

Sur Windows Server 2016 ou version ultérieure, vous n’avez pas besoin de définir les exclusions suivantes :

- Fichiers du système d’exploitation
- Rôles de serveur et fichiers ajoutés par le biais de rôles serveur

Étant donné que l’antivirus Microsoft Defender est intégré, il ne nécessite pas d’exclusions pour les fichiers de système d’exploitation sur Windows Server 2016 ou version ultérieure. En outre, lorsque vous exécutez Windows Server 2016 ou une version ultérieure et installez un rôle, l’Antivirus Microsoft Defender inclut des exclusions automatiques pour le rôle serveur et tous les fichiers ajoutés lors de l’installation du rôle.

Les exclusions de système d’exploitation et les exclusions de rôle de serveur n’apparaissent pas dans les listes d’exclusions standard affichées dans [l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md).

> [!NOTE]
> Les exclusions automatiques pour les rôles serveur et les fichiers de système d’exploitation ne s’appliquent pas aux Windows Server 2012. Des exclusions automatiques peuvent s’appliquer si vos serveurs exécutant Windows Server 2012 R2 sont intégrés à Defender pour point de terminaison. (Consultez [Intégrer des serveurs Windows au service Microsoft Defender pour point de terminaison](configure-server-endpoints.md).)


### <a name="the-list-of-automatic-exclusions"></a>Liste des exclusions automatiques

Les sections suivantes contiennent les exclusions fournies avec les chemins d’accès et les types de fichiers des exclusions automatiques.

#### <a name="default-exclusions-for-all-roles"></a>Exclusions par défaut pour tous les rôles

Cette section répertorie les exclusions par défaut pour tous les rôles dans Windows Server 2016, Windows Server 2019 et Windows Server 2022.

> [!IMPORTANT]
> - Les emplacements par défaut peuvent être différents des emplacements décrits dans cet article.
> - Pour définir des exclusions pour les logiciels qui ne sont pas inclus en tant que fonctionnalité Windows ou rôle serveur, reportez-vous à la documentation du fabricant du logiciel.

##### <a name="windows-tempedb-files"></a>Fichiers Windows « temp.edb »

- `%windir%\SoftwareDistribution\Datastore\*\tmp.edb`
- `%ProgramData%\Microsoft\Search\Data\Applications\Windows\windows.edb`

##### <a name="windows-update-files-or-automatic-update-files"></a>fichiers Windows Update ou fichiers de mise à jour automatique

- `%windir%\SoftwareDistribution\Datastore\*\Datastore.edb`
- `%windir%\SoftwareDistribution\Datastore\*\edb.chk`
- `%windir%\SoftwareDistribution\Datastore\*\edb\*.log`
- `%windir%\SoftwareDistribution\Datastore\*\Edb\*.jrs`
- `%windir%\SoftwareDistribution\Datastore\*\Res\*.log`

##### <a name="windows-security-files"></a>fichiers Sécurité Windows

- `%windir%\Security\database\*.chk`
- `%windir%\Security\database\*.edb`
- `%windir%\Security\database\*.jrs`
- `%windir%\Security\database\*.log`
- `%windir%\Security\database\*.sdb`

##### <a name="group-policy-files"></a>fichiers stratégie de groupe

- `%allusersprofile%\NTUser.pol`
- `%SystemRoot%\System32\GroupPolicy\Machine\registry.pol`
- `%SystemRoot%\System32\GroupPolicy\User\registry.pol`

##### <a name="wins-files"></a>Fichiers WINS

- `%systemroot%\System32\Wins\*\*.chk`
- `%systemroot%\System32\Wins\*\*.log`
- `%systemroot%\System32\Wins\*\*.mdb`
- `%systemroot%\System32\LogFiles\`
- `%systemroot%\SysWow64\LogFiles\`

##### <a name="file-replication-service-frs-exclusions"></a>Exclusions du service de réplication de fichiers (FRS)

- Fichiers dans le dossier de travail du service de réplication de fichiers (FRS). Le dossier de travail FRS est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Working Directory`

  - `%windir%\Ntfrs\jet\sys\*\edb.chk`
  - `%windir%\Ntfrs\jet\*\Ntfrs.jdb`
  - `%windir%\Ntfrs\jet\log\*\*.log`

- Fichiers journaux de la base de données FRS. Le dossier du fichier journal de la base de données FRS est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Ntfrs\Parameters\DB Log File Directory`

  - `%windir%\Ntfrs\*\Edb\*.log`

- Dossier de préproduction FRS. Le dossier intermédiaire est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Replica Sets\GUID\Replica Set Stage`

  - `%systemroot%\Sysvol\*\Ntfrs_cmp*\`

- Dossier de préinstallation FRS. Ce dossier est spécifié par le dossier `Replica_root\DO_NOT_REMOVE_NtFrs_PreInstall_Directory`

  - `%systemroot%\SYSVOL\domain\DO_NOT_REMOVE_NtFrs_PreInstall_Directory\*\Ntfrs*\`

- Base de données de réplication du système de fichiers distribué (DFSR) et dossiers de travail. Ces dossiers sont spécifiés par la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DFSR\Parameters\Replication Groups\GUID\Replica Set Configuration File`

  > [!NOTE]
  > Pour les emplacements personnalisés, consultez [Désactivation des exclusions automatiques](#opting-out-of-automatic-exclusions).

  - `%systemdrive%\System Volume Information\DFSR\$db_normal$`
  - `%systemdrive%\System Volume Information\DFSR\FileIDTable_*`
  - `%systemdrive%\System Volume Information\DFSR\SimilarityTable_*`
  - `%systemdrive%\System Volume Information\DFSR\*.XML`
  - `%systemdrive%\System Volume Information\DFSR\$db_dirty$`
  - `%systemdrive%\System Volume Information\DFSR\$db_clean$`
  - `%systemdrive%\System Volume Information\DFSR\$db_lostl$`
  - `%systemdrive%\System Volume Information\DFSR\Dfsr.db`
  - `%systemdrive%\System Volume Information\DFSR\*.frx`
  - `%systemdrive%\System Volume Information\DFSR\*.log`
  - `%systemdrive%\System Volume Information\DFSR\Fsr*.jrs`
  - `%systemdrive%\System Volume Information\DFSR\Tmp.edb`

##### <a name="process-exclusions"></a>Exclusions de processus

- `%systemroot%\System32\dfsr.exe`
- `%systemroot%\System32\dfsrs.exe`

##### <a name="hyper-v-exclusions"></a>Exclusions Hyper-V

Le tableau suivant répertorie les exclusions de type de fichier, les exclusions de dossier et les exclusions de processus qui sont fournies automatiquement lorsque vous installez le rôle Hyper-V.

|Type d’exclusion|Détails|
|---|---|
|Types de fichiers|`*.vhd` <br/> `*.vhdx` <br/> `*.avhd` <br/> `*.avhdx` <br/> `*.vsv` <br/> `*.iso` <br/> `*.rct` <br/> `*.vmcx` <br/> `*.vmrs`|
|Folders|`%ProgramData%\Microsoft\Windows\Hyper-V` <br/> `%ProgramFiles%\Hyper-V` <br/> `%SystemDrive%\ProgramData\Microsoft\Windows\Hyper-V\Snapshots` <br/> `%Public%\Documents\Hyper-V\Virtual Hard Disks`|
|Processus|`%systemroot%\System32\Vmms.exe` <br/> `%systemroot%\System32\Vmwp.exe`|

##### <a name="sysvol-files"></a>Fichiers SYSVOL

- `%systemroot%\Sysvol\Domain\*.adm`
- `%systemroot%\Sysvol\Domain\*.admx`
- `%systemroot%\Sysvol\Domain\*.adml`
- `%systemroot%\Sysvol\Domain\Registry.pol`
- `%systemroot%\Sysvol\Domain\*.aas`
- `%systemroot%\Sysvol\Domain\*.inf`
- `%systemroot%\Sysvol\Domain\*Scripts.ini`
- `%systemroot%\Sysvol\Domain\*.ins`
- `%systemroot%\Sysvol\Domain\Oscfilter.ini`


#### <a name="active-directory-exclusions"></a>Exclusions Active Directory

Cette section répertorie les exclusions qui sont remises automatiquement lorsque vous installez services de domaine Active Directory (AD DS).

##### <a name="ntds-database-files"></a>Fichiers de base de données NTDS

Les fichiers de base de données sont spécifiés dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Database File`

- `%windir%\Ntds\ntds.dit`
- `%windir%\Ntds\ntds.pat`

##### <a name="the-ad-ds-transaction-log-files"></a>Fichiers journaux des transactions AD DS

Les fichiers journaux des transactions sont spécifiés dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\Database Log Files Path`

- `%windir%\Ntds\EDB*.log`
- `%windir%\Ntds\Res*.log`
- `%windir%\Ntds\Edb*.jrs`
- `%windir%\Ntds\Ntds*.pat`
- `%windir%\Ntds\TEMP.edb`

##### <a name="the-ntds-working-folder"></a>Dossier de travail NTDS

Ce dossier est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Working Directory`

- `%windir%\Ntds\Temp.edb`
- `%windir%\Ntds\Edb.chk`

##### <a name="process-exclusions-for-ad-ds-and-ad-ds-related-support-files"></a>Traiter les exclusions pour les fichiers de support AD DS et AD DS

- `%systemroot%\System32\ntfrs.exe`
- `%systemroot%\System32\lsass.exe`

#### <a name="dhcp-server-exclusions"></a>Exclusions du serveur DHCP

Cette section répertorie les exclusions qui sont remises automatiquement lorsque vous installez le rôle serveur DHCP. Les emplacements des fichiers du serveur DHCP sont spécifiés par les paramètres *DatabasePath*, *DhcpLogFilePath* et *BackupDatabasePath* dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DHCPServer\Parameters`

- `%systemroot%\System32\DHCP\*\*.mdb`
- `%systemroot%\System32\DHCP\*\*.pat`
- `%systemroot%\System32\DHCP\*\*.log`
- `%systemroot%\System32\DHCP\*\*.chk`
- `%systemroot%\System32\DHCP\*\*.edb`

#### <a name="dns-server-exclusions"></a>Exclusions du serveur DNS

Cette section répertorie les exclusions de fichiers et de dossiers, ainsi que les exclusions de processus qui sont remises automatiquement lorsque vous installez le rôle serveur DNS.

##### <a name="file-and-folder-exclusions-for-the-dns-server-role"></a>Exclusions de fichiers et de dossiers pour le rôle serveur DNS

- `%systemroot%\System32\Dns\*\*.log`
- `%systemroot%\System32\Dns\*\*.dns`
- `%systemroot%\System32\Dns\*\*.scc`
- `%systemroot%\System32\Dns\*\BOOT`

##### <a name="process-exclusions-for-the-dns-server-role"></a>Exclusions de processus pour le rôle serveur DNS

- `%systemroot%\System32\dns.exe`

#### <a name="file-and-storage-services-exclusions"></a>Exclusions des services de fichiers et de stockage

Cette section répertorie les exclusions de fichiers et de dossiers qui sont remises automatiquement lorsque vous installez le rôle Services de fichiers et de stockage. Les exclusions répertoriées ci-dessous n’incluent pas d’exclusions pour le rôle de clustering.

- `%SystemDrive%\ClusterStorage`
- `%clusterserviceaccount%\Local Settings\Temp`
- `%SystemDrive%\mscs`

#### <a name="print-server-exclusions"></a>Exclusions du serveur d’impression

Cette section répertorie les exclusions de type de fichier, les exclusions de dossiers et les exclusions de processus qui sont remises automatiquement lorsque vous installez le rôle Serveur d’impression.

##### <a name="file-type-exclusions"></a>Exclusions de type de fichier

- `*.shd`
- `*.spl`

##### <a name="folder-exclusions"></a>Exclusions de dossiers

Ce dossier est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Printers\DefaultSpoolDirectory`

- `%system32%\spool\printers\*`

##### <a name="process-exclusions"></a>Exclusions de processus

- `spoolsv.exe`

#### <a name="web-server-exclusions"></a>Exclusions de serveur web

Cette section répertorie les exclusions de dossier et les exclusions de processus qui sont remises automatiquement lorsque vous installez le rôle serveur web.

##### <a name="folder-exclusions"></a>Exclusions de dossiers

- `%SystemRoot%\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\ASP Compiled Templates`
- `%systemDrive%\inetpub\logs`
- `%systemDrive%\inetpub\wwwroot`

##### <a name="process-exclusions"></a>Process exclusions

- `%SystemRoot%\system32\inetsrv\w3wp.exe`
- `%SystemRoot%\SysWOW64\inetsrv\w3wp.exe`
- `%SystemDrive%\PHP5433\php-cgi.exe`

##### <a name="turning-off-scanning-of-files-in-the-sysvolsysvol-folder-or-the-sysvol_dfsrsysvol-folder"></a>Désactivation de l’analyse des fichiers dans le dossier Sysvol\Sysvol ou le dossier SYSVOL_DFSR\Sysvol

L’emplacement actuel du ou `SYSVOL_DFSR\Sysvol` du `Sysvol\Sysvol` dossier et tous les sous-dossiers est la cible d’analyse du système de fichiers de la racine du jeu de réplicas. Les `Sysvol\Sysvol` dossiers et `SYSVOL_DFSR\Sysvol` les emplacements utilisent les emplacements suivants par défaut :

- `%systemroot%\Sysvol\Domain`
- `%systemroot%\Sysvol_DFSR\Domain`

Le chemin d’accès à l’actif `SYSVOL` actif est référencé par le partage NETLOGON et peut être déterminé par le nom de la valeur SysVol dans la sous-clé suivante : `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Netlogon\Parameters`

Excluez les fichiers suivants de ce dossier et de tous ses sous-dossiers :

- `*.adm`
- `*.admx`
- `*.adml`
- `Registry.pol`
- `Registry.tmp`
- `*.aas`
- `*.inf`
- `Scripts.ini`
- `*.ins`
- `Oscfilter.ini`

#### <a name="windows-server-update-services-exclusions"></a>exclusions Windows Server Update Services

Cette section répertorie les exclusions de dossier qui sont remises automatiquement lorsque vous installez le rôle Windows Server Update Services (WSUS). Le dossier WSUS est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\Software\Microsoft\Update Services\Server\Setup`

- `%systemroot%\WSUS\WSUSContent`
- `%systemroot%\WSUS\UpdateServicesDBFiles`
- `%systemroot%\SoftwareDistribution\Datastore`
- `%systemroot%\SoftwareDistribution\Download`

## <a name="opting-out-of-automatic-exclusions"></a>Refus des exclusions automatiques

Dans Windows Server 2016 et versions ultérieures, les exclusions prédéfinies fournies par les mises à jour du renseignement de sécurité excluent uniquement les chemins par défaut d’un rôle ou d’une fonctionnalité. Si vous avez installé un rôle ou une fonctionnalité dans un chemin d’accès personnalisé, ou si vous souhaitez contrôler manuellement l’ensemble des exclusions, veillez à désactiver les exclusions automatiques fournies dans les mises à jour du renseignement de sécurité. Toutefois, gardez à l’esprit que les exclusions fournies automatiquement sont optimisées pour Windows Server 2016 et versions ultérieures. Consultez [Recommandations pour définir des exclusions](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) avant de définir vos listes d’exclusions.

> [!WARNING]
> La désactivation des exclusions automatiques peut avoir un impact négatif sur les performances ou entraîner une altération des données. Les exclusions fournies automatiquement sont optimisées pour les rôles Windows Server 2016, Windows Server 2019 et Windows Server 2022.

Étant donné que les exclusions prédéfinies excluent uniquement les **chemins d’accès par défaut**, si vous déplacez les dossiers NTDS et SYSVOL vers un autre lecteur ou chemin *différent du chemin d’accès d’origine*, vous devez ajouter des exclusions manuellement. Consultez [Configurer la liste des exclusions en fonction du nom du dossier ou de l’extension de fichier](configure-extension-file-exclusions-microsoft-defender-antivirus.md#configure-the-list-of-exclusions-based-on-folder-name-or-file-extension).

Vous pouvez désactiver les listes d’exclusion automatique avec stratégie de groupe, les applets de commande PowerShell et WMI.

### <a name="use-group-policy-to-disable-the-auto-exclusions-list-on-windows-server-2016-windows-server-2019-and-windows-server-2022"></a>Utilisez stratégie de groupe pour désactiver la liste des exclusions automatiques sur Windows Server 2016, Windows Server 2019 et Windows Server 2022

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725752(v=ws.11)). Cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**, puis sélectionnez **Modèles d’administration**.

3. Développez l’arborescence vers **les composants Windows exclusions** \> **de l’antivirus** \> Microsoft Defender.

4. Double-cliquez sur **Désactiver les exclusions automatiques** et définissez l’option **sur Activé**. Puis sélectionnez **OK**.

### <a name="use-powershell-cmdlets-to-disable-the-auto-exclusions-list-on-windows-server"></a>Utiliser des applets de commande PowerShell pour désactiver la liste des exclusions automatiques sur Windows Server

Utilisez les applets de commande suivantes :

```PowerShell
Set-MpPreference -DisableAutoExclusions $true
```

Pour en savoir plus, consultez les ressources suivantes :

- [Utilisez les applets de commande PowerShell pour configurer et exécuter l’antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md).
- [Utilisez PowerShell avec l’antivirus Microsoft Defender](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-disable-the-auto-exclusions-list-on-windows-server"></a>Utiliser l’instruction de gestion Windows (WMI) pour désactiver la liste d’exclusions automatiques sur Windows Server

Utilisez la méthode **Set** de la classe [MSFT_MpPreference](/previous-versions/windows/desktop/defender/msft-mppreference) pour les propriétés suivantes :

```WMI
DisableAutoExclusions
```

Pour plus d’informations et les paramètres autorisés, consultez les rubriques suivantes :

- [WINDOWS DEFENDER API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="defining-custom-exclusions"></a>Définition d’exclusions personnalisées

Si nécessaire, vous pouvez ajouter ou supprimer des exclusions personnalisées. Pour ce faire, consultez les articles suivants :

- [Configurer et valider des exclusions en fonction du nom de fichier, de l’extension et de l’emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider les exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="see-also"></a>Voir aussi

- [Configurer et valider les exclusions pour les analyses antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions en fonction du nom de fichier, de l’extension et de l’emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider les exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Erreurs courantes à éviter lors de la définition d’exclusions](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Personnaliser, lancer et passer en revue les résultats des analyses et des corrections de l’Antivirus Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
