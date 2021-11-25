---
title: Utiliser la ligne de commande pour gérer les Antivirus Microsoft Defender
description: Exécutez Antivirus Microsoft Defender analyse et configurez la protection nouvelle génération avec un utilitaire de ligne de commande dédié.
keywords: exécuter l’analyse windows defender, exécuter l’analyse antivirus à partir de la ligne de commande, exécuter l’analyse windows defender à partir de la ligne de commande, mpcmdrun, defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.date: 05/24/2021
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 0d9a2d84febb15dd626fb603faecc2bb0ba74af1
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2021
ms.locfileid: "61171035"
---
# <a name="configure-and-manage-microsoft-defender-antivirus-with-the-mpcmdrunexe-command-line-tool"></a>Configurer et gérer les Antivirus Microsoft Defender l’outil mpcmdrun.exe ligne de commande

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Vous pouvez effectuer différentes fonctions dans Antivirus Microsoft Defender à l’aide de l’outil en ligne de commande **dédiémpcmdrun.exe**. Cet utilitaire est utile lorsque vous souhaitez automatiser Antivirus Microsoft Defender tâches. Vous trouverez l’utilitaire dans `%ProgramFiles%\Windows Defender\MpCmdRun.exe` . Exécutez-le à partir d’une invite de commandes.

> [!TIP]
> Vous devrez peut-être ouvrir une version de niveau administrateur de l’invite de commandes. Lorsque vous recherchez **l’invite de** commandes sur le menu Démarrer, choisissez **Exécuter en tant qu’administrateur.** Si vous exécutez une version mise à jour de la plateforme anti-programme malveillant De Microsoft Defender, exécutez-la à `MpCmdRun` partir de l’emplacement suivant : `C:\ProgramData\Microsoft\Windows Defender\Platform\<antimalware platform version>` Pour plus d’informations sur la plateforme anti-programme malveillant, voir Antivirus Microsoft Defender mises à jour [et les lignes de base.](manage-updates-baselines-microsoft-defender-antivirus.md)

L’utilitaire MpCmdRun utilise la syntaxe suivante :

```console
MpCmdRun.exe [command] [-options]
```

Voici un exemple :

```console
MpCmdRun.exe -Scan -ScanType 2
```

Dans notre exemple, l’utilitaire MpCmdRun démarre une analyse antivirus complète sur l’appareil.

## <a name="commands"></a>Commandes

|Command|Description|
|---|---|
|`-?`**ou** `-h`|Affiche toutes les options disponibles pour l’outil MpCmdRun|
|`-Scan [-ScanType [<value>]] [-File <path> [-DisableRemediation] [-BootSectorScan] [-CpuThrottling]] [-Timeout <days>] [-Cancel]`|Recherche les logiciels malveillants. Les valeurs **de ScanType** sont :<p>**0 Par** défaut, en fonction de votre configuration<p>**1 Analyse** rapide<p>**2 Analyse** complète<p>**3 Analyse** personnalisée de fichier et d’annuaire.<p>CpuThrottling s’exécute en fonction des configurations de stratégie|
|`-Trace [-Grouping #] [-Level #]`|Démarre le suivi des diagnostics|
|`-GetFiles [-SupportLogLocation <path>]`|Collecte des informations de support. Voir «[Collecte des données de diagnostic](collect-diagnostic-data.md)»|
|`-GetFilesDiagTrack`|Identique à `-GetFiles` , mais sorties dans le dossier DiagTrack temporaire|
|`-RemoveDefinitions [-All]`|Restaure l’intelligence de sécurité installée sur une copie de sauvegarde précédente ou sur l’ensemble par défaut d’origine|
|`-RemoveDefinitions [-DynamicSignatures]`|Supprime uniquement l’intelligence de sécurité téléchargée dynamiquement|
|`-RemoveDefinitions [-Engine]`|Restaure le moteur installé précédent|
|`-SignatureUpdate [-UNC \|-MMPC]`|Recherche les nouvelles mises à jour de l’intelligence de la sécurité|
|`-Restore  [-ListAll \|[[-Name <name>] [-All] \|[-FilePath <filePath>]] [-Path <path>]]`|Restaure ou répertorie les éléments mis en quarantaine|
|`-AddDynamicSignature [-Path]`|Charge l’intelligence de sécurité dynamique|
|`-ListAllDynamicSignatures`|Répertorie l’intelligence de sécurité dynamique chargée|
|`-RemoveDynamicSignature [-SignatureSetID]`|Supprime l’intelligence de sécurité dynamique|
|`-CheckExclusion -path <path>`|Vérifie si un chemin d’accès est exclu|
|`-ValidateMapsConnection`|Vérifie que votre réseau peut communiquer avec le service Antivirus Microsoft Defender cloud. Cette commande ne fonctionne que sur Windows 10 version 1703 ou supérieure.|

## <a name="common-errors-in-running-commands-via-mpcmdrunexe"></a>Erreurs courantes lors de l’exécution de commandes via mpcmdrun.exe

Le tableau suivant répertorie les erreurs courantes qui peuvent se produire lors de l’utilisation de l’outil MpCmdRun.

|Message d’erreur|Raison possible|
|---|---|
|**ValidateMapsConnection a échoué (800106BA)** **ou 0x800106BA**|Le service Antivirus Microsoft Defender est désactivé. Activez le service et essayez à nouveau. Si vous avez besoin d’aide pour réactiver Antivirus Microsoft Defender, voir [Réinstaller/activer Antivirus Microsoft Defender sur vos points de terminaison.](switch-to-microsoft-defender-setup.md#reinstallenable-microsoft-defender-antivirus-on-your-endpoints)<p> **CONSEIL**: dans Windows 10 1909 ou plus, et Windows Server 2019 ou plus ancien, le service était auparavant appelé *Antivirus Windows Defender*.|
|**0x80070667**|Vous exécutez la commande à partir d’un ordinateur qui Windows 10 version 1607 ou antérieure, ou qui `-ValidateMapsConnection` Windows Server 2016 ou une version antérieure. Exécutez la commande à partir d’un ordinateur Windows 10 version 1703 ou plus récente, ou Windows Server 2019 ou version plus récente.|
|**MpCmdRun n’est pas reconnu comme une commande interne ou externe, un programme opérable ou un fichier de commandes.**|L’outil doit être exécuté à partir de l’un ou l’autre des deux ou (où il peut être différent étant donné que les mises à jour de plateforme `%ProgramFiles%\Windows Defender` `C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2012.4-0` sont `2012.4-0` mensuelles à l’exception de mars)|
|**ValidateMapsConnection n’a pas pu établir de connexion à MAPS (hr=80070005 httpcode=450)**|La commande a été tentée à l’aide de privilèges insuffisants. Utilisez l’invite de commandes (cmd.exe) en tant qu’administrateur.|
|**ValidateMapsConnection n’a pas pu établir de connexion à MAPS (hr=80070006 httpcode=451)**|Le pare-feu bloque la connexion ou effectue une inspection SSL.|
|**ValidateMapsConnection n’a pas pu établir de connexion à MAPS (hr=80004005 httpcode=450)**|Problèmes éventuels liés au réseau, tels que les problèmes de résolution de noms|
|**ValidateMapsConnection n’a pas pu établir de connexion à MAPS (hr=0x80508015**|Le pare-feu bloque la connexion ou effectue une inspection SSL.|
|**ValidateMapsConnection n’a pas pu établir de connexion à MAPS (hr=800722F0D**|Le pare-feu bloque la connexion ou effectue une inspection SSL.|
|**ValidateMapsConnection n’a pas pu établir de connexion à MAPS (hr=80072EE7 httpcode=451)**|Le pare-feu bloque la connexion ou effectue une inspection SSL.|

## <a name="see-also"></a>Voir aussi

- [Configurer les fonctionnalités antivirus Microsoft Defender](configure-microsoft-defender-antivirus-features.md)
- [Configurer et valider les connexions réseau à un antivirus Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md)
- [Rubriques de référence pour les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
