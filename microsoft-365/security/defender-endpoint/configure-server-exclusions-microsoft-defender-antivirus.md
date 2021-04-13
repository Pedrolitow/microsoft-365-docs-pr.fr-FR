---
title: Configurer les exclusions de l'Antivirus Microsoft Defender sur Windows Server
ms.reviewer: ''
manager: dansimp
description: Windows Server inclut des exclusions automatiques, basées sur le rôle serveur. Vous pouvez également ajouter des exclusions personnalisées.
keywords: exclusions, serveur, exclusions automatiques, automatique, personnalisé, analyses, Antivirus Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.technology: mde
ms.date: 02/10/2021
ms.openlocfilehash: 555daac32b202b0b9f46c4f19fa6e4b04bcadda3
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690316"
---
# <a name="configure-microsoft-defender-antivirus-exclusions-on-windows-server"></a>Configurer les exclusions de l'Antivirus Microsoft Defender sur Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

L'Antivirus Microsoft Defender sur Windows Server 2016 et Windows Server 2019 vous inscrit automatiquement dans certaines exclusions, telles que définies par votre rôle serveur spécifié. Ces exclusions n'apparaissent pas dans les listes d'exclusions standard affichées dans [l'application Sécurité Windows.](microsoft-defender-security-center-antivirus.md)

> [!NOTE]
> Les exclusions automatiques s'appliquent uniquement à l'analyse de la protection en temps réel (RTP). Les exclusions automatiques ne sont pas honorées lors d'une analyse complète/rapide ou à la demande.

Outre les exclusions automatiques définies par le rôle serveur, vous pouvez ajouter ou supprimer des exclusions personnalisées. Pour ce faire, reportez-vous aux articles suivants :
- [Configurer et valider des exclusions en fonction du nom de fichier, de l'extension et de l'emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="a-few-points-to-keep-in-mind"></a>Quelques points à garder à l'esprit

Gardez les points importants suivants à l'esprit :

- Les exclusions personnalisées prévalent sur les exclusions automatiques.
- Les exclusions automatiques s'appliquent uniquement à l'analyse de la protection en temps réel (RTP). Les exclusions automatiques ne sont pas honorées lors d'une analyse complète/rapide ou à la demande.
- Les exclusions personnalisées et dupliquées ne sont pas en conflit avec les exclusions automatiques.
- L'Antivirus Microsoft Defender utilise les outils gestion et maintenance des images de déploiement (DISM) pour déterminer les rôles installés sur votre ordinateur.

## <a name="opt-out-of-automatic-exclusions"></a>Refuser les exclusions automatiques

Dans Windows Server 2016 et Windows Server 2019, les exclusions prédéfines délivrées par les mises à jour de l'intelligence de sécurité excluent uniquement les chemins d'accès par défaut pour un rôle ou une fonctionnalité. Si vous avez installé un rôle ou une fonctionnalité dans un chemin d'accès personnalisé, ou si vous souhaitez contrôler manuellement l'ensemble des exclusions, veillez à refuser les exclusions automatiques délivrées dans les mises à jour de l'intelligence de sécurité. Mais n'oubliez pas que les exclusions qui sont automatiquement livrées sont optimisées pour les rôles Windows Server 2016 et 2019. Voir [Recommandations pour définir des exclusions avant](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) de définir vos listes d'exclusions.

> [!WARNING]
> Le fait de refuser les exclusions automatiques peut avoir un impact négatif sur les performances ou entraîner une altération des données. Les exclusions qui sont livrées automatiquement sont optimisées pour les rôles Windows Server 2016 et Windows Server 2019.

Étant donné que les exclusions prédéfinie excluent uniquement les chemins d'accès par **défaut,** si vous déplacez NTDS et SYSVOL vers un autre lecteur ou chemin d'accès différent du chemin d'accès d'origine, vous devez ajouter des exclusions manuellement à l'aide des informations [ici.](configure-extension-file-exclusions-microsoft-defender-antivirus.md#configure-the-list-of-exclusions-based-on-folder-name-or-file-extension)

Vous pouvez désactiver les listes d'exclusion automatique avec la stratégie de groupe, les cmdlets PowerShell et WMI.

### <a name="use-group-policy-to-disable-the-auto-exclusions-list-on-windows-server-2016-and-windows-server-2019"></a>Utiliser une stratégie de groupe pour désactiver la liste d'exclusions automatiques sur Windows Server 2016 et Windows Server 2019

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725752(v=ws.11)) Cliquez avec le bouton droit sur l'objet de stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier.**
2. Dans **l'Éditeur de gestion des stratégies** de groupe, allez à **Configuration** ordinateur, puis cliquez sur **Modèles d'administration.**
3. Développez l'arborescence **des composants Windows**  >  **Exclusions de l'Antivirus Microsoft Defender.**  >  
4. Double-cliquez **sur Désactiver les exclusions automatiques** et définissez l'option sur **Activé.** Cliquez ensuite sur **OK**. 

### <a name="use-powershell-cmdlets-to-disable-the-auto-exclusions-list-on-windows-server-2016-and-2019"></a>Utiliser les cmdlets PowerShell pour désactiver la liste d'exclusions automatiques sur Windows Server 2016 et 2019

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -DisableAutoExclusions $true
```

Pour en savoir plus, consultez les ressources suivantes :

- [Utilisez les cmdlets PowerShell pour configurer et exécuter l'Antivirus Microsoft Defender.](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Utilisez PowerShell avec l'Antivirus Microsoft Defender.](/powershell/module/defender/)

### <a name="use-windows-management-instruction-wmi-to-disable-the-auto-exclusions-list-on-windows-server-2016-and-windows-server-2019"></a>Utiliser Windows Management Instruction (WMI) pour désactiver la liste d'exclusions automatiques sur Windows Server 2016 et Windows Server 2019

Utilisez la **méthode Set** de la [classe MSFT_MpPreference](/previous-versions/windows/desktop/defender/msft-mppreference) pour les propriétés suivantes :

```WMI
DisableAutoExclusions
```

Pour plus d'informations et les paramètres autorisés, voir les informations suivantes :
- [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="list-of-automatic-exclusions"></a>Liste des exclusions automatiques

Les sections suivantes contiennent les exclusions qui sont livrées avec des chemins d'accès et des types de fichiers d'exclusions automatiques.

### <a name="default-exclusions-for-all-roles"></a>Exclusions par défaut pour tous les rôles

Cette section répertorie les exclusions par défaut pour tous les rôles Windows Server 2016 et 2019.

> [!NOTE]
> Les emplacements par défaut peuvent être différents de ceux répertoriés dans cet article.

#### <a name="windows-tempedb-files"></a>Fichiers « temp.edb » Windows

- `%windir%\SoftwareDistribution\Datastore\*\tmp.edb`
- `%ProgramData%\Microsoft\Search\Data\Applications\Windows\*\*.log`

#### <a name="windows-update-files-or-automatic-update-files"></a>Fichiers Windows Update ou fichiers de mise à jour automatique

- `%windir%\SoftwareDistribution\Datastore\*\Datastore.edb`
- `%windir%\SoftwareDistribution\Datastore\*\edb.chk`
- `%windir%\SoftwareDistribution\Datastore\*\edb\*.log`
- `%windir%\SoftwareDistribution\Datastore\*\Edb\*.jrs`
- `%windir%\SoftwareDistribution\Datastore\*\Res\*.log`

#### <a name="windows-security-files"></a>Fichiers de sécurité Windows

- `%windir%\Security\database\*.chk`
- `%windir%\Security\database\*.edb`
- `%windir%\Security\database\*.jrs`
- `%windir%\Security\database\*.log`
- `%windir%\Security\database\*.sdb`

#### <a name="group-policy-files"></a>Fichiers de stratégie de groupe

- `%allusersprofile%\NTUser.pol`
- `%SystemRoot%\System32\GroupPolicy\Machine\registry.pol`
- `%SystemRoot%\System32\GroupPolicy\User\registry.pol`

#### <a name="wins-files"></a>Fichiers WINS

- `%systemroot%\System32\Wins\*\*.chk`
- `%systemroot%\System32\Wins\*\*.log`
- `%systemroot%\System32\Wins\*\*.mdb`
- `%systemroot%\System32\LogFiles\`
- `%systemroot%\SysWow64\LogFiles\`

#### <a name="file-replication-service-frs-exclusions"></a>Exclusions du service de réplication de fichiers (FRS)

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
  > Pour les emplacements personnalisés, voir [Refuser les exclusions automatiques.](#opt-out-of-automatic-exclusions)

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

#### <a name="process-exclusions"></a>Exclusions de processus

- `%systemroot%\System32\dfsr.exe`
- `%systemroot%\System32\dfsrs.exe`

#### <a name="hyper-v-exclusions"></a>Exclusions Hyper-V

Le tableau suivant répertorie les exclusions de types de fichiers, les exclusions de dossiers et les exclusions de processus qui sont automatiquement livrées lorsque vous installez le rôle Hyper-V.

|Exclusions de types de fichiers |Exclusions de dossiers  | Process exclusions |
|:--|:--|:--|
| `*.vhd` <br/> `*.vhdx` <br/> `*.avhd` <br/> `*.avhdx` <br/> `*.vsv` <br/> `*.iso` <br/> `*.rct` <br/> `*.vmcx` <br/> `*.vmrs` | `%ProgramData%\Microsoft\Windows\Hyper-V` <br/> `%ProgramFiles%\Hyper-V` <br/> `%SystemDrive%\ProgramData\Microsoft\Windows\Hyper-V\Snapshots` <br/> `%Public%\Documents\Hyper-V\Virtual Hard Disks` | `%systemroot%\System32\Vmms.exe` <br/> `%systemroot%\System32\Vmwp.exe` |

#### <a name="sysvol-files"></a>Fichiers SYSVOL

- `%systemroot%\Sysvol\Domain\*.adm`
- `%systemroot%\Sysvol\Domain\*.admx`
- `%systemroot%\Sysvol\Domain\*.adml`
- `%systemroot%\Sysvol\Domain\Registry.pol`
- `%systemroot%\Sysvol\Domain\*.aas`
- `%systemroot%\Sysvol\Domain\*.inf`
- `%systemroot%\Sysvol\Domain\*Scripts.ini`
- `%systemroot%\Sysvol\Domain\*.ins`
- `%systemroot%\Sysvol\Domain\Oscfilter.ini`


### <a name="active-directory-exclusions"></a>Exclusions Active Directory

Cette section répertorie les exclusions qui sont automatiquement livrées lorsque vous installez les services de domaine Active Directory.

#### <a name="ntds-database-files"></a>Fichiers de base de données NTDS

Les fichiers de base de données sont spécifiés dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Database File`

- `%windir%\Ntds\ntds.dit`
- `%windir%\Ntds\ntds.pat`

#### <a name="the-ad-ds-transaction-log-files"></a>Fichiers journaux des transactions AD DS

Les fichiers journaux des transactions sont spécifiés dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\Database Log Files Path`

- `%windir%\Ntds\EDB*.log`
- `%windir%\Ntds\Res*.log`
- `%windir%\Ntds\Edb*.jrs`
- `%windir%\Ntds\Ntds*.pat`
- `%windir%\Ntds\TEMP.edb`

#### <a name="the-ntds-working-folder"></a>Dossier de travail NTDS

Ce dossier est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Working Directory`

- `%windir%\Ntds\Temp.edb`
- `%windir%\Ntds\Edb.chk`

#### <a name="process-exclusions-for-ad-ds-and-ad-ds-related-support-files"></a>Exclusions de processus pour les fichiers de support liés aux services AD DS et AD DS

- `%systemroot%\System32\ntfrs.exe`
- `%systemroot%\System32\lsass.exe`

### <a name="dhcp-server-exclusions"></a>Exclusions de serveur DHCP

Cette section répertorie les exclusions qui sont automatiquement livrées lorsque vous installez le rôle serveur DHCP. Les emplacements de fichiers DHCP Server sont spécifiés par les paramètres *DatabasePath,* *DhcpLogFilePath* et *BackupDatabasePath* dans la clé de Registre `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DHCPServer\Parameters`

- `%systemroot%\System32\DHCP\*\*.mdb`
- `%systemroot%\System32\DHCP\*\*.pat`
- `%systemroot%\System32\DHCP\*\*.log`
- `%systemroot%\System32\DHCP\*\*.chk`
- `%systemroot%\System32\DHCP\*\*.edb`

### <a name="dns-server-exclusions"></a>Exclusions de serveur DNS

Cette section répertorie les exclusions de fichiers et de dossiers, ainsi que les exclusions de processus qui sont automatiquement livrées lorsque vous installez le rôle serveur DNS.

#### <a name="file-and-folder-exclusions-for-the-dns-server-role"></a>Exclusions de fichiers et de dossiers pour le rôle serveur DNS

- `%systemroot%\System32\Dns\*\*.log`
- `%systemroot%\System32\Dns\*\*.dns`
- `%systemroot%\System32\Dns\*\*.scc`
- `%systemroot%\System32\Dns\*\BOOT`

#### <a name="process-exclusions-for-the-dns-server-role"></a>Exclusions de processus pour le rôle serveur DNS

- `%systemroot%\System32\dns.exe`

### <a name="file-and-storage-services-exclusions"></a>Exclusions des services de fichiers et de stockage

Cette section répertorie les exclusions de fichiers et de dossiers qui sont automatiquement livrées lorsque vous installez le rôle Services de fichiers et de stockage. Les exclusions répertoriées ci-dessous n'incluent pas d'exclusions pour le rôle de clustering.

- `%SystemDrive%\ClusterStorage`
- `%clusterserviceaccount%\Local Settings\Temp`
- `%SystemDrive%\mscs`

### <a name="print-server-exclusions"></a>Exclusions du serveur d'impression

Cette section répertorie les exclusions de types de fichiers, les exclusions de dossiers et les exclusions de processus qui sont automatiquement livrées lorsque vous installez le rôle serveur d'impression.

#### <a name="file-type-exclusions"></a>Exclusions de types de fichiers

- `*.shd`
- `*.spl`

#### <a name="folder-exclusions"></a>Exclusions de dossiers

Ce dossier est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Printers\DefaultSpoolDirectory`

- `%system32%\spool\printers\*`

#### <a name="process-exclusions"></a>Exclusions de processus

- `spoolsv.exe`

### <a name="web-server-exclusions"></a>Exclusions de serveur web

Cette section répertorie les exclusions de dossiers et les exclusions de processus qui sont automatiquement livrées lorsque vous installez le rôle serveur Web.

#### <a name="folder-exclusions"></a>Exclusions de dossiers

- `%SystemRoot%\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\ASP Compiled Templates`
- `%systemDrive%\inetpub\logs`
- `%systemDrive%\inetpub\wwwroot`

#### <a name="process-exclusions"></a>Process exclusions

- `%SystemRoot%\system32\inetsrv\w3wp.exe`
- `%SystemRoot%\SysWOW64\inetsrv\w3wp.exe`
- `%SystemDrive%\PHP5433\php-cgi.exe`

#### <a name="turning-off-scanning-of-files-in-the-sysvolsysvol-folder-or-the-sysvol_dfsrsysvol-folder"></a>La non-analyse des fichiers dans le dossier Sysvol\Sysvol ou le dossier SYSVOL_DFSR\Sysvol

L'emplacement actuel du ou des dossiers et tous les sous-dossiers est la cible d'examen du système de fichiers de la racine du jeu `Sysvol\Sysvol` `SYSVOL_DFSR\Sysvol` de réplicas. Les `Sysvol\Sysvol` `SYSVOL_DFSR\Sysvol` dossiers et les dossiers utilisent les emplacements suivants par défaut :

- `%systemroot%\Sysvol\Domain`
- `%systemroot%\Sysvol_DFSR\Domain`

Le chemin d'accès au chemin d'accès actif est référencé par le partage NETLOGON et peut être déterminé par le nom de la valeur SysVol dans la `SYSVOL` sous-clé suivante : `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Netlogon\Parameters`

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

### <a name="windows-server-update-services-exclusions"></a>Exclusions de Windows Server Update Services

Cette section répertorie les exclusions de dossiers qui sont automatiquement livrées lorsque vous installez le rôle Windows Server Update Services (WSUS). Le dossier WSUS est spécifié dans la clé de Registre `HKEY_LOCAL_MACHINE\Software\Microsoft\Update Services\Server\Setup`

- `%systemroot%\WSUS\WSUSContent`
- `%systemroot%\WSUS\UpdateServicesDBFiles`
- `%systemroot%\SoftwareDistribution\Datastore`
- `%systemroot%\SoftwareDistribution\Download`

## <a name="see-also"></a>Voir aussi

- [Configurer et valider des exclusions pour les analyses de l'Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions en fonction du nom de fichier, de l'extension et de l'emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer et valider des exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Erreurs courantes à éviter lors de la définition d'exclusions](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Personnaliser, lancer et passer en revue les résultats des analyses et des corrections de l'Antivirus Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)