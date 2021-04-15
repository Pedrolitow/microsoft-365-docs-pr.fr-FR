---
title: Utiliser la ligne de commande pour gérer l'Antivirus Microsoft Defender
description: Exécutez les analyses de l'Antivirus Microsoft Defender et configurez la protection nouvelle génération avec un utilitaire de ligne de commande dédié.
keywords: exécuter l'analyse windows defender, exécuter l'analyse antivirus à partir de la ligne de commande, exécuter l'analyse windows defender à partir de la ligne de commande, mpcmdrun, defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.date: 03/19/2021
ms.technology: mde
ms.openlocfilehash: 1b357f7c1e02211f3949383a380666cb7444f814
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51764626"
---
# <a name="configure-and-manage-microsoft-defender-antivirus-with-the-mpcmdrunexe-command-line-tool"></a>Configurer et gérer l'Antivirus Microsoft Defender à l'aide de lmpcmdrun.exe de ligne de commande Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez effectuer différentes fonctions de l'Antivirus Microsoft Defender avec l'outil de ligne de commande **dédiémpcmdrun.exe**. Cet utilitaire est utile lorsque vous souhaitez automatiser l'utilisation de l'Antivirus Microsoft Defender. Vous pouvez trouver l'utilitaire dans `%ProgramFiles%\Windows Defender\MpCmdRun.exe` . Vous devez l'exécuter à partir d'une invite de commandes.

> [!NOTE]
> Vous devrez peut-être ouvrir une version de niveau administrateur de l'invite de commandes. Lorsque vous recherchez **l'invite de commandes** dans le menu Démarrer, choisissez **Exécuter en tant qu'administrateur.**
> Si vous exécutez une version mise à jour de la plateforme Microsoft Defender, exécutez-la à `**MpCmdRun**` partir de l'emplacement suivant : `C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`

L'utilitaire dispose des commandes suivantes :

```console
MpCmdRun.exe [command] [-options]
```
Voici un exemple :

```console
MpCmdRun.exe -Scan -ScanType 2
``` 

| Command  | Description   |
|:----|:----|
| `-?` **ou** `-h`   | Affiche toutes les options disponibles pour cet outil |
| `-Scan [-ScanType [0\|1\|2\|3]] [-File <path> [-DisableRemediation] [-BootSectorScan] [-CpuThrottling]] [-Timeout <days>] [-Cancel]` | Recherche les logiciels malveillants. Les valeurs de **ScanType** sont les suivants : **0** Par défaut, en fonction de votre configuration, **-1** Analyse rapide, **-2** Analyse complète, **-3** Analyse personnalisée de fichier et d'annuaire.  CpuThrottling respectera la limitation de l'UC configurée à partir de la stratégie |
| `-Trace [-Grouping #] [-Level #]` | Démarre le suivi des diagnostics |
| `-GetFiles [-SupportLogLocation <path>]` | Collecte des informations de support. Voir «[Collecte des données de diagnostic](collect-diagnostic-data.md)»  |
| `-GetFilesDiagTrack`  | Identique à `-GetFiles` , mais sorties dans le dossier DiagTrack temporaire |
| `-RemoveDefinitions [-All]` | Restaure l'intelligence de sécurité installée sur une copie de sauvegarde précédente ou sur l'ensemble par défaut d'origine |
| `-RemoveDefinitions [-DynamicSignatures]` | Supprime uniquement l'intelligence de sécurité téléchargée dynamiquement |
| `-RemoveDefinitions [-Engine]` | Restaure le moteur installé précédent |
| `-SignatureUpdate [-UNC \| -MMPC]` | Recherche les nouvelles mises à jour de l'intelligence de la sécurité |
| `-Restore  [-ListAll \| [[-Name <name>] [-All] \| [-FilePath <filePath>]] [-Path <path>]]` | Restaure ou répertorie les éléments mis en quarantaine |
| `-AddDynamicSignature [-Path]` | Charge l'intelligence de sécurité dynamique |
| `-ListAllDynamicSignatures` | Répertorie l'intelligence de sécurité dynamique chargée |
| `-RemoveDynamicSignature [-SignatureSetID]` | Supprime l'intelligence de sécurité dynamique |
| `-CheckExclusion -path <path>` | Vérifie si un chemin d'accès est exclu |
| `-ValidateMapsConnection` | Vérifie que votre réseau peut communiquer avec le service cloud de l'Antivirus Microsoft Defender. Cette commande ne fonctionne que sur Windows 10, version 1703 ou supérieure.|


## <a name="common-errors-in-running-commands-via-mpcmdrunexe"></a>Erreurs courantes lors de l'exécution de commandes via mpcmdrun.exe 

|Message d’erreur | Raison possible
|:----|:----|
| `ValidateMapsConnection failed (800106BA) or 0x800106BA` | Le service Antivirus Microsoft Defender est désactivé. Activez le service et essayez à nouveau. <br>   **Remarque :**  Dans Windows 10 1909 ou une ancienne, et Windows Server 2019 ou une ancienne, le service était appelé service « antivirus Windows Defender ».|
| `0x80070667` | Vous exécutez la commande à partir d'un ordinateur qui est `-ValidateMapsConnection` Windows 10 version 1607 ou antérieure, ou Windows Server 2016 ou une version antérieure. Exécutez la commande à partir d'un ordinateur windows 10 version 1703 ou plus récente, ou windows Server 2019 ou version plus récente.|
| `'MpCmdRun' is not recognized as an internal or external command, operable program or batch file.` | L'outil doit être exécuté à partir de : ou (où peut différer étant donné que les mises à jour de plateforme `%ProgramFiles%\Windows Defender` `C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2012.4-0` sont `2012.4-0` mensuelles à l'exception de mars)|
| `ValidateMapsConnection failed to establish a connection to MAPS (hr=80070005 httpcode=450)` | Privilèges insuffisants. Utilisez l'invite de commandes (cmd.exe) en tant qu'administrateur.|
| `ValidateMapsConnection failed to establish a connection to MAPS (hr=80070006 httpcode=451)` | Le pare-feu bloque la connexion ou effectue une inspection SSL. |
| `ValidateMapsConnection failed to establish a connection to MAPS (hr=80004005 httpcode=450)` | Problèmes éventuels liés au réseau, tels que les problèmes de résolution de noms|
| `ValidateMapsConnection failed to establish a connection to MAPS (hr=0x80508015` | Le pare-feu bloque la connexion ou effectue une inspection SSL. |
| `ValidateMapsConnection failed to establish a connection to MAPS (hr=800722F0D` | Le pare-feu bloque la connexion ou effectue une inspection SSL. |
| `ValidateMapsConnection failed to establish a connection to MAPS (hr=80072EE7 httpcode=451)` | Le pare-feu bloque la connexion ou effectue une inspection SSL. |

## <a name="see-also"></a>Voir aussi

- [Configurer les fonctionnalités de l'Antivirus Microsoft Defender](configure-microsoft-defender-antivirus-features.md)
- [Gérer l'Antivirus Microsoft Defender dans votre entreprise](configuration-management-reference-microsoft-defender-antivirus.md)
- [Rubriques de référence pour les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)