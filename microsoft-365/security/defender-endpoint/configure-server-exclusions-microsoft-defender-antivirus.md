---
title: Configurer des exclusions Antivirus Microsoft Defender sur Windows Server
ms.reviewer: pahuijbr
manager: dansimp
description: Windows Le serveur inclut des exclusions automatiques, basées sur le rôle serveur. Vous pouvez également ajouter des exclusions personnalisées.
keywords: exclusions, serveur, exclusions automatiques, automatiques, personnalisées, analyses, Antivirus Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 08/17/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 3766c78e1c2af55f9e785d73cf639d9a6b1bf2a7
ms.sourcegitcommit: 6968594dc8cf8b30a4c958df6d65dfd0cd2cfae1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2021
ms.locfileid: "59491228"
---
# <a name="configure-microsoft-defender-antivirus-exclusions-on-windows-server"></a>Configurer des exclusions Antivirus Microsoft Defender sur Windows Server


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)
- Antivirus Microsoft Defender

## <a name="summary"></a>Résumé

Cet article fournit une vue d’ensemble des exclusions Antivirus Microsoft Defender sur Windows Server 2016 ou ultérieure.

Comme Antivirus Microsoft Defender est intégré à Windows Server 2016 et ultérieures, les exclusions pour les fichiers du système d’exploitation et les rôles serveur se produisent automatiquement. Toutefois, vous pouvez définir des exclusions personnalisées. Vous pouvez également refuser les exclusions automatiques si nécessaire.

Le présent article contient les sections suivantes :

<br/><br/>

|Section|Description|
|---|---|
|[Exclusions automatiques sur Windows Server 2016 ou ultérieure](#automatic-exclusions-on-windows-server-2016-or-later)|Décrit les deux principaux types d’exclusions automatiques et inclut une liste détaillée des exclusions automatiques|
|[Refuser les exclusions automatiques](#opting-out-of-automatic-exclusions)|Comprend des considérations et des procédures importantes décrivant comment refuser les exclusions automatiques|
|[Définition d’exclusions personnalisées](#defining-custom-exclusions)|Fournit des liens vers des procédures pour définir des exclusions personnalisées|

> [!IMPORTANT]
> Gardez les points suivants à l’esprit :
>
> - Les exclusions personnalisées prévalent sur les exclusions automatiques.
> - Les exclusions automatiques s’appliquent uniquement à l’analyse de la protection en temps réel (RTP). Les exclusions automatiques ne sont pas honorées lors d’une analyse complète, d’une analyse rapide ou d’une analyse à la demande.
> - Les exclusions personnalisées et dupliquées ne sont pas en conflit avec les exclusions automatiques.
> - Antivirus Microsoft Defender utilise les outils gestion et maintenance des images de déploiement (DISM) pour déterminer les rôles installés sur votre ordinateur.

## <a name="automatic-exclusions-on-windows-server-2016-or-later"></a>Exclusions automatiques sur Windows Server 2016 ou ultérieure

> [!NOTE]
> Les exclusions automatiques s’appliquent uniquement à l’analyse de protection en temps réel (RTP). Les exclusions automatiques ne sont pas honorées lors d’une analyse complète, d’une analyse rapide ou d’une analyse à la demande.

Sur Windows Server 2016 ou ultérieure, vous ne devez pas définir les exclusions suivantes :

- Fichiers du système d’exploitation
- Rôles serveur et fichiers ajoutés par le biais des rôles serveur

Comme Antivirus Microsoft Defender est intégré, il ne nécessite pas d’exclusions pour les fichiers du système d’exploitation Windows Server 2016 ou ultérieure. En outre, lorsque vous exécutez Windows Server 2016 ou une ultérieure et installez un rôle, Antivirus Microsoft Defender inclut des exclusions automatiques pour le rôle serveur et tous les fichiers ajoutés lors de l’installation du rôle.

Les exclusions de système d’exploitation et les exclusions de rôles de serveur n’apparaissent pas dans les listes d’exclusions standard affichées dans [l Sécurité Windows app.](microsoft-defender-security-center-antivirus.md)

Les exclusions automatiques pour les rôles serveur et les fichiers du système d’exploitation ne s’appliquent Windows Server 2012 ou Windows Server 2012 R2.

### <a name="the-list-of-automatic-exclusions"></a>Liste des exclusions automatiques

Les sections suivantes contiennent les exclusions qui sont livrées avec des chemins d’accès et des types de fichiers d’exclusions automatiques.

#### <a name="default-exclusions-for-all-roles"></a>Exclusions par défaut pour tous les rôles

Cette section répertorie les exclusions par défaut pour tous les rôles dans Windows Server 2016 et Windows Server 2019.

> [!NOTE]
> Les emplacements par défaut peuvent être différents de ceux répertoriés dans cet article.

##### <a name="windows-tempedb-files"></a>Windows Fichiers « temp.edb »

- `%windir%\SoftwareDistribution\Datastore\*\tmp.edb`
- `%ProgramData%\Microsoft\Search\Data\Applications\Windows\*\*.log`

##### <a name="windows-update-files-or-automatic-update-files"></a>Windows Mettre à jour des fichiers ou des fichiers de mise à jour automatique

- `%windir%\SoftwareDistribution\Datastore\*\Datastore.edb`
- `%windir%\SoftwareDistribution\Datastore\*\edb.chk`
- `%windir%\SoftwareDistribution\Datastore\*\edb\*.log`
- `%windir%\SoftwareDistribution\Datastore\*\Edb\*.jrs`
- `%windir%\SoftwareDistribution\Datastore\*\Res\*.log`

##### <a name="windows-security-files"></a>Sécurité Windows fichiers

- `%windir%\Security\database\*.chk`
- `%windir%\Security\database\*.edb`
- `%windir%\Security\database\*.jrs`
- `%windir%\Security\database\*.log`
- `%windir%\Security\database\*.sdb`

##### <a name="group-policy-files"></a>Fichiers de stratégie de groupe

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

- Fichiers journaux de base de données FRS. Le dossier du fichier journal de la base de données FRS est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Ntfrs\Parameters\DB Log File Directory`

  - `%windir%\Ntfrs\*\Edb\*.log`

- Dossier intermédiaire FRS. Le dossier de transit est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Replica Sets\GUID\Replica Set Stage`

  - `%systemroot%\Sysvol\*\Ntfrs_cmp*\`

- Dossier de préinstallation FRS. Ce dossier est spécifié par le dossier `Replica_root\DO_NOT_REMOVE_NtFrs_PreInstall_Directory`

  - `%systemroot%\SYSVOL\domain\DO_NOT_REMOVE_NtFrs_PreInstall_Directory\*\Ntfrs*\`

- La base de données de réplication du système de fichiers distribués (DFSR) et les dossiers de travail. Ces dossiers sont spécifiés par la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DFSR\Parameters\Replication Groups\GUID\Replica Set Configuration File`

  > [!NOTE]
  > Pour les emplacements personnalisés, voir [Refuser les exclusions automatiques.](#opting-out-of-automatic-exclusions)

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

Le tableau suivant répertorie les exclusions de types de fichiers, les exclusions de dossiers et les exclusions de processus qui sont automatiquement livrées lorsque vous installez le rôle Hyper-V.

<br><br/>

|Type d’exclusion|Spécificités|
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

Cette section répertorie les exclusions qui sont automatiquement livrées lorsque vous installez les services de domaine Active Directory (AD DS).

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

##### <a name="process-exclusions-for-ad-ds-and-ad-ds-related-support-files"></a>Exclusions de processus pour les fichiers de support liés aux services AD DS et AD DS

- `%systemroot%\System32\ntfrs.exe`
- `%systemroot%\System32\lsass.exe`

#### <a name="dhcp-server-exclusions"></a>Exclusions de serveur DHCP

Cette section répertorie les exclusions qui sont automatiquement livrées lorsque vous installez le rôle serveur DHCP. Les emplacements de fichiers DHCP Server sont spécifiés par les paramètres *DatabasePath,* *DhcpLogFilePath* et *BackupDatabasePath* dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DHCPServer\Parameters`

- `%systemroot%\System32\DHCP\*\*.mdb`
- `%systemroot%\System32\DHCP\*\*.pat`
- `%systemroot%\System32\DHCP\*\*.log`
- `%systemroot%\System32\DHCP\*\*.chk`
- `%systemroot%\System32\DHCP\*\*.edb`

#### <a name="dns-server-exclusions"></a>Exclusions de serveur DNS

Cette section répertorie les exclusions de fichiers et de dossiers, ainsi que les exclusions de processus qui sont automatiquement livrées lorsque vous installez le rôle serveur DNS.

##### <a name="file-and-folder-exclusions-for-the-dns-server-role"></a>Exclusions de fichiers et de dossiers pour le rôle serveur DNS

- `%systemroot%\System32\Dns\*\*.log`
- `%systemroot%\System32\Dns\*\*.dns`
- `%systemroot%\System32\Dns\*\*.scc`
- `%systemroot%\System32\Dns\*\BOOT`

##### <a name="process-exclusions-for-the-dns-server-role"></a>Exclusions de processus pour le rôle serveur DNS

- `%systemroot%\System32\dns.exe`

#### <a name="file-and-storage-services-exclusions"></a>Exclusions de Stockage services de fichiers et de fichiers

Cette section répertorie les exclusions de fichiers et de dossiers qui sont automatiquement livrées lorsque vous installez le rôle De fichiers Stockage Services. Les exclusions répertoriées ci-dessous n’incluent pas d’exclusions pour le rôle de clustering.

- `%SystemDrive%\ClusterStorage`
- `%clusterserviceaccount%\Local Settings\Temp`
- `%SystemDrive%\mscs`

#### <a name="print-server-exclusions"></a>Exclusions du serveur d’impression

Cette section répertorie les exclusions de types de fichiers, les exclusions de dossiers et les exclusions de processus qui sont automatiquement livrées lorsque vous installez le rôle serveur d’impression.

##### <a name="file-type-exclusions"></a>Exclusions de types de fichiers

- `*.shd`
- `*.spl`

##### <a name="folder-exclusions"></a>Exclusions de dossiers

Ce dossier est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Printers\DefaultSpoolDirectory`

- `%system32%\spool\printers\*`

##### <a name="process-exclusions"></a>Exclusions de processus

- `spoolsv.exe`

#### <a name="web-server-exclusions"></a>Exclusions de serveur web

Cette section répertorie les exclusions de dossiers et les exclusions de processus qui sont automatiquement livrées lorsque vous installez le rôle serveur Web.

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

##### <a name="turning-off-scanning-of-files-in-the-sysvolsysvol-folder-or-the-sysvol_dfsrsysvol-folder"></a>La non-analyse des fichiers dans le dossier Sysvol\Sysvol ou le dossier SYSVOL_DFSR\Sysvol

L’emplacement actuel du ou des dossiers et tous les sous-dossiers est la cible d’examen du système de fichiers de la racine du jeu `Sysvol\Sysvol` `SYSVOL_DFSR\Sysvol` de réplicas. Les `Sysvol\Sysvol` `SYSVOL_DFSR\Sysvol` dossiers et les dossiers utilisent les emplacements suivants par défaut :

- `%systemroot%\Sysvol\Domain`
- `%systemroot%\Sysvol_DFSR\Domain`

Le chemin d’accès au chemin d’accès actif est référencé par le partage NETLOGON et peut être déterminé par le nom de la valeur SysVol dans la `SYSVOL` sous-clé suivante : `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Netlogon\Parameters`

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

#### <a name="windows-server-update-services-exclusions"></a>Windows Server Update Services exclusions

Cette section répertorie les exclusions de dossiers qui sont automatiquement livrées lorsque vous installez le rôle Windows Server Update Services (WSUS). Le dossier WSUS est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\Software\Microsoft\Update Services\Server\Setup`

- `%systemroot%\WSUS\WSUSContent`
- `%systemroot%\WSUS\UpdateServicesDBFiles`
- `%systemroot%\SoftwareDistribution\Datastore`
- `%systemroot%\SoftwareDistribution\Download`

## <a name="opting-out-of-automatic-exclusions"></a>Refuser les exclusions automatiques

Dans Windows Server 2016 et ultérieures, les exclusions prédéfines livrées par les mises à jour de l’intelligence de sécurité excluent uniquement les chemins d’accès par défaut pour un rôle ou une fonctionnalité. Si vous avez installé un rôle ou une fonctionnalité dans un chemin d’accès personnalisé, ou si vous souhaitez contrôler manuellement l’ensemble d’exclusions, veillez à refuser les exclusions automatiques délivrées dans les mises à jour d’informations de sécurité. Toutefois, gardez à l’esprit que les exclusions qui sont livrées automatiquement sont optimisées pour Windows Server 2016 et ultérieures. Voir [Recommandations pour définir des exclusions](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) avant de définir vos listes d’exclusions.

> [!WARNING]
> Le fait de refuser les exclusions automatiques peut avoir un impact négatif sur les performances ou entraîner une altération des données. Les exclusions qui sont livrées automatiquement sont optimisées pour les rôles Windows Server 2016 et Windows Server 2019.

Étant donné que les exclusions prédéfinie excluent uniquement les chemins d’accès par **défaut,** si vous déplacez les dossiers NTDS et SYSVOL vers un autre lecteur ou chemin différent du chemin d’accès d’origine, vous devez ajouter des exclusions manuellement. Voir [Configurer la liste des exclusions en fonction du nom du dossier ou de l’extension de fichier.](configure-extension-file-exclusions-microsoft-defender-antivirus.md#configure-the-list-of-exclusions-based-on-folder-name-or-file-extension)

Vous pouvez désactiver les listes d’exclusion automatique avec la stratégie de groupe, les cmdlets PowerShell et WMI.

### <a name="use-group-policy-to-disable-the-auto-exclusions-list-on-windows-server-2016-and-windows-server-2019"></a>Utiliser la stratégie de groupe pour désactiver la liste d’exclusions automatiques sur Windows Server 2016 et Windows Server 2019

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725752(v=ws.11)). Cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, sélectionnez **Configuration** ordinateur, puis sélectionnez **Modèles d’administration.**

3. Développez l’arborescence **Windows composants** \> **Antivirus Microsoft Defender** \> **exclusions.**

4. Double-cliquez **sur Désactiver les exclusions automatiques** et définissez l’option sur **Activé.** Puis sélectionnez **OK**.

### <a name="use-powershell-cmdlets-to-disable-the-auto-exclusions-list-on-windows-server"></a>Utiliser les cmdlets PowerShell pour désactiver la liste d’exclusions automatiques sur Windows Server

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -DisableAutoExclusions $true
```

Pour en savoir plus, consultez les ressources suivantes :

- [Utilisez les cmdlets PowerShell pour configurer et exécuter Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md).
- [Utilisez PowerShell avec Antivirus Microsoft Defender](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-disable-the-auto-exclusions-list-on-windows-server"></a>Utiliser Windows Management Instruction (WMI) pour désactiver la liste d’exclusions automatiques sur Windows Server

Utilisez la **méthode Set** de la [classe MSFT_MpPreference](/previous-versions/windows/desktop/defender/msft-mppreference) pour les propriétés suivantes :

```WMI
DisableAutoExclusions
```

Pour plus d’informations et les paramètres autorisés, voir les informations suivantes :

- [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="defining-custom-exclusions"></a>Définition d’exclusions personnalisées

Si nécessaire, vous pouvez ajouter ou supprimer des exclusions personnalisées. Pour ce faire, consultez les articles suivants :

- [Configurer et valider des exclusions en fonction du nom de fichier, de l’extension et de l’emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="see-also"></a>Voir aussi

- [Configurer et valider des exclusions pour Antivirus Microsoft Defender analyses](configure-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions en fonction du nom de fichier, de l’extension et de l’emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Erreurs courantes à éviter lors de la définition d’exclusions](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Personnaliser, lancer et passer en revue les résultats des analyses et Antivirus Microsoft Defender correction](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
