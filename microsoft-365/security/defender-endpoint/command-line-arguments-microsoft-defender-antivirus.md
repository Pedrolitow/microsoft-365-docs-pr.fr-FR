---
title: Utiliser la ligne de commande pour gérer Microsoft Defender Antivirus
description: Exécutez Microsoft Defender analyses antivirus et configurez la protection de nouvelle génération avec un utilitaire de ligne de commande dédié.
keywords: exécuter l’analyse windows defender, exécuter l’analyse antivirus à partir de la ligne de commande, exécuter l’analyse windows defender à partir de la ligne de commande, mpcmdrun, defender
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.date: 05/24/2021
ms.subservice: mde
ms.topic: how-to
ms.collection:
- m365-security
- tier3
search.appverid: met150
ms.openlocfilehash: 57fc2406410b3a24394ae6a11d5c06b0e6110418
ms.sourcegitcommit: b9282493c371d59c2e583b9803825096499b5e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68153254"
---
# <a name="configure-and-manage-microsoft-defender-antivirus-with-the-mpcmdrunexe-command-line-tool"></a>Configurer et gérer Microsoft Defender Antivirus avec l’outil en ligne de commande mpcmdrun.exe

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender 

**Plateformes**
- Windows

Vous pouvez effectuer différentes fonctions dans Microsoft Defender Antivirus à l’aide de l’outil en ligne de commande dédié **mpcmdrun.exe**. Cet utilitaire est utile lorsque vous souhaitez automatiser Microsoft Defender tâches antivirus. Vous pouvez trouver l’utilitaire dans `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. Exécutez-le à partir d’une invite de commandes.

> [!TIP]
> Vous devrez peut-être ouvrir une version au niveau de l’administrateur de l’invite de commandes. Lorsque vous **recherchez l’invite de commandes** dans le menu Démarrer, choisissez **Exécuter en tant qu’administrateur**. Si vous exécutez une version mise à jour Microsoft Defender plateforme anti-programme malveillant, exécutez-la `MpCmdRun` à partir de l’emplacement suivant : `C:\ProgramData\Microsoft\Windows Defender\Platform\<antimalware platform version>`. Pour plus d’informations sur la plateforme anti-programme malveillant, consultez [Microsoft Defender mises à jour antivirus et les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).

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
|`-?` **ou** `-h`|Affiche toutes les options disponibles pour l’outil MpCmdRun|
|`-Scan [-ScanType [<value>]] [-File <path> [-DisableRemediation] [-BootSectorScan] [-CpuThrottling]] [-Timeout <days>] [-Cancel]`|Recherche des logiciels malveillants. Les valeurs de **ScanType** sont les suivantes :<p>**0** Par défaut, en fonction de votre configuration<p>**1** Analyse rapide<p>**2** Analyse complète<p>**3** Analyse personnalisée du fichier et du répertoire.<p>CpuThrottling s’exécute en fonction des configurations de stratégie|
|`-Trace [-Grouping #] [-Level #]`|Démarre le suivi des diagnostics|
|`-GetFiles [-SupportLogLocation <path>]`|Collecte des informations de support. Voir « [Collecte des données de diagnostic](collect-diagnostic-data.md) »|
|`-GetFilesDiagTrack`|Identique à `-GetFiles`, mais sorties vers le dossier DiagTrack temporaire|
|`-RemoveDefinitions [-All]`|Restaure l’intelligence de sécurité installée sur une copie de sauvegarde précédente ou sur le jeu par défaut d’origine|
|`-RemoveDefinitions [-DynamicSignatures]`|Supprime uniquement le renseignement de sécurité téléchargé dynamiquement|
|`-RemoveDefinitions [-Engine]`|Restaure le moteur installé précédent|
|`-SignatureUpdate [-UNC \|-MMPC]`|Recherche de nouvelles mises à jour du renseignement de sécurité|
|`-Restore  [-ListAll \|[[-Name <name>] [-All] \|[-FilePath <filePath>]] [-Path <path>]]`|Restaure ou répertorie les éléments mis en quarantaine|
|`-AddDynamicSignature [-Path]`|Charge l’intelligence de sécurité dynamique|
|`-ListAllDynamicSignatures`|Répertorie les informations de sécurité dynamiques chargées|
|`-RemoveDynamicSignature [-SignatureSetID]`|Supprime l’intelligence de sécurité dynamique|
|`-CheckExclusion -path <path>`|Vérifie si un chemin d’accès est exclu|
|`-ValidateMapsConnection`|Vérifie que votre réseau peut communiquer avec le service cloud antivirus Microsoft Defender. Cette commande fonctionne uniquement sur Windows 10, version 1703 ou ultérieure.|

## <a name="common-errors-in-running-commands-via-mpcmdrunexe"></a>Erreurs courantes lors de l’exécution de commandes via mpcmdrun.exe

Le tableau suivant répertorie les erreurs courantes qui peuvent se produire lors de l’utilisation de l’outil MpCmdRun.

|Message d’erreur|Raison possible|
|---|---|
|**ValidateMapsConnection a échoué (800106BA)** ou **0x800106BA**|Le service antivirus Microsoft Defender est désactivé. Activez le service et réessayez. Si vous avez besoin d’aide pour réactiver Microsoft Defender Antivirus, consultez [Réinstaller/activer Microsoft Defender Antivirus sur vos points de terminaison](switch-to-mde-phase-2.md#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).<p> **CONSEIL** : Dans Windows 10 1909 ou version antérieure, et Windows Server 2019 ou version antérieure, le service était auparavant appelé *antivirus Windows Defender*.|
|**0x80070667**|Vous exécutez la `-ValidateMapsConnection` commande à partir d’un ordinateur Windows 10 version 1607 ou ultérieure, ou Windows Server 2016 ou une version antérieure. Exécutez la commande à partir d’un ordinateur qui est Windows 10 version 1703 ou ultérieure, ou Windows Server 2019 ou version ultérieure.|
|**MpCmdRun n’est pas reconnu comme une commande interne ou externe, un programme opérable ou un fichier batch.**|L’outil doit être exécuté à partir de l’un ou de l’autre `%ProgramFiles%\Windows Defender` ou `C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2012.4-0` (où `2012.4-0` peut différer étant donné que les mises à jour de la plateforme sont mensuelles à l’exception de mars)|
|**ValidateMapsConnection n’a pas pu établir de connexion à MAPS (hr=80070005 httpcode=450)**|La commande a été tentée en utilisant des privilèges insuffisants. Utilisez l’invite de commandes (cmd.exe) en tant qu’administrateur.|
|**ValidateMapsConnection n’a pas pu établir de connexion à MAPS (hr=80070006 httpcode=451)**|Le pare-feu bloque la connexion ou effectue une inspection SSL.|
|**ValidateMapsConnection n’a pas pu établir de connexion à MAPS (hr=80004005 httpcode=450)**|Problèmes potentiels liés au réseau, tels que les problèmes de résolution de noms|
|**ValidateMapsConnection n’a pas pu établir de connexion à MAPS (hr=0x80508015**|Le pare-feu bloque la connexion ou effectue une inspection SSL.|
|**ValidateMapsConnection n’a pas pu établir de connexion à MAPS (hr=800722F0D)**|Le pare-feu bloque la connexion ou effectue une inspection SSL.|
|**ValidateMapsConnection n’a pas pu établir de connexion à MAPS (hr=80072EE7 httpcode=451)**|Le pare-feu bloque la connexion ou effectue une inspection SSL.|

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

- [Configurer les fonctionnalités antivirus Microsoft Defender](configure-microsoft-defender-antivirus-features.md)
- [Configurer et valider les connexions réseau à un antivirus Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md)
- [Rubriques de référence sur les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
