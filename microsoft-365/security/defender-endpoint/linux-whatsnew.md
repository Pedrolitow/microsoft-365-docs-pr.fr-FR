---
title: Nouveautés de Microsoft Defender pour Endpoint sur Linux
description: Liste des principales modifications apportées à Microsoft Defender pour Endpoint sur Linux.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, whatsnew, release
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: 48b278d23cd724cade823d2a6b052b11d02a3a13
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63401089"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-linux"></a>Nouveautés de Microsoft Defender pour Endpoint sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="1016093-30122012160930"></a>101.60.93 (30.122012.16093.0)

- Cette version contient une mise à jour de sécurité [pour CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)

## <a name="1016005-30122012160050"></a>101.60.05 (30.122012.16005.0)

- Prise en charge supplémentaire de la version du noyau 2.6.32-754.43.1.el6.x86_64 RHEL 6.10
- Correctifs de bogue

## <a name="1015880-30122012158800"></a>101.58.80 (30.122012.15880.0)

- L’outil en ligne de commande prend désormais en charge la restauration des fichiers mis en quarantaine à un emplacement autre que celui où le fichier a été détecté à l’origine. Cela peut être effectué par le biais `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`de .
- Correctifs de bogue

## <a name="1015662-30121122156620"></a>101.56.62 (30.121122.15662.0)

- Correction d’un incident de produit introduit dans la 101.53.02 et qui a eu un impact sur plusieurs clients

## <a name="1015302-30121112153020"></a>101.53.02 (30.121112.15302.0)

- Améliorations des performances & résolutions de bogues

## <a name="1015257-30121092152570"></a>101.52.57 (30.121092.15257.0)

- Ajout d’une fonctionnalité pour détecter les fioles log4j vulnérables en cours d’utilisation Java applications. L’ordinateur est régulièrement inspecté pour l’exécution Java processus avec des jais log4j chargés. Les informations sont signalées au système principal de Microsoft Defender for Endpoint et sont exposées dans la zone Gestion des vulnérabilités du portail.

## <a name="1014776-30121092147760"></a>101.47.76 (30.121092.14776.0)

- Ajout d’un nouveau commutateur à l’outil en ligne de commande pour contrôler si les archives sont analysées pendant les analyses à la demande. Cela peut être configuré via `mdatp config scan-archives --value [enabled/disabled]`. Par défaut, cette valeur est définie sur `enabled`.
- Correctifs de bogue

## <a name="1014513-30121082145130"></a>101.45.13 (30.121082.14513.0)

- À partir de cette version, nous apportons la prise en charge de Microsoft Defender for Endpoint aux distros suivantes : 
  - Versions RHEL6.7-6.10 et CentOS6.7-6.10.
  - Amazon Linux 2
  - Fedora 33 ou supérieure
- Correctifs de bogue


## <a name="1014500-30121072145000"></a>101.45.00 (30.121072.14500.0)

- Ajout de nouveaux commutateurs à l’outil en ligne de commande :
  - Contrôler le degré de parallélisme pour les analyses à la demande. Cela peut être configuré via `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Par défaut, un degré de parallélisme est `2` utilisé.
  - Contrôler si les analyses après l’actualisation des informations de sécurité sont activées ou désactivées. Cela peut être configuré via `mdatp config scan-after-definition-update --value [enabled/disabled]`. Par défaut, cette valeur est définie sur `enabled`.
- La modification du niveau du journal des produits nécessite désormais une élévation
- Correctifs de bogue

## <a name="1013998-30121062139980"></a>101.39.98 (30.121062.13998.0)

- Améliorations des performances & résolutions de bogues

## <a name="1013427-30121052134270"></a>101.34.27 (30.121052.13427.0)

- Améliorations des performances & résolutions de bogues

## <a name="1012964-30121042129640"></a>101.29.64 (30.121042.12964.0)

- À partir de cette version, les menaces détectées lors des analyses antivirus à la demande déclenchées via le client de ligne de commande sont automatiquement corrigés. Les menaces détectées lors des analyses déclenchées via l’interface utilisateur nécessitent toujours une action manuelle.
- `mdatp diagnostic real-time-protection-statistics` prend désormais en charge deux commutateurs supplémentaires :
  - `--sort`: trie la sortie décroit par nombre total de fichiers analysés
  - `--top N`: affiche les N premiers résultats (fonctionne uniquement si `--sort` elle est également spécifiée)
- Améliorations des performances & résolutions de bogues

## <a name="1012572-30121022125630"></a>101.25.72 (30.121022.12563.0)

- Microsoft Defender pour endpoint sur Linux est désormais disponible en prévisualisation pour les clients du gouvernement des États-Unis. Pour plus d’informations, [voir Microsoft Defender for Endpoint for US Government customers](gov.md).
- Nous avons résolu un problème dans lequel l’utilisation de Microsoft Defender pour endpoint sur Linux sur des systèmes avec des systèmes de fichiers LINUX a conduit au se bloquer du système d’exploitation
- Améliorations des performances & autres correctifs de bogues

## <a name="1012563-30121022125630"></a>101.25.63 (30.121022.12563.0)

- Améliorations des performances & résolutions de bogues

## <a name="1012364-30121021123640"></a>101.23.64 (30.121021.12364.0)

- Amélioration des performances pour la situation où un point de montage entier est ajouté à la liste d’exclusion antivirus. Avant cette version, l’activité de fichier provenant du point de montage était toujours traitée par le produit. À partir de cette version, l’activité de fichier pour les points de montage exclus est supprimée, ce qui améliore les performances du produit
- Ajout d’une nouvelle option à l’outil en ligne de commande pour afficher les informations sur la dernière analyse à la demande. Pour afficher des informations sur la dernière analyse à la demande, exécutez `mdatp health --details antivirus`
- Autres améliorations en matière de performances & résolutions de bogues

## <a name="1011853"></a>101.18.53

- PEPT linux est désormais [généralement disponible](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/edr-for-linux-is-now-is-generally-available/ba-p/2048539)
- Ajout d’un nouveau commutateur de ligne de commande (`--ignore-exclusions`) pour ignorer les exclusions av pendant les analyses personnalisées (`mdatp scan custom`)
- Étendu avec `mdatp diagnostic create` un nouveau paramètre (`--path [directory]`) qui permet d’enregistrer les journaux de diagnostic dans un autre répertoire
- Améliorations des performances & résolutions de bogues

## <a name="1011299"></a>101.12.99

- Améliorations des performances & résolutions de bogues

## <a name="1010476"></a>101.04.76

- Correctifs de bogue

## <a name="1010348"></a>101.03.48

- Correctifs de bogue

## <a name="1010255"></a>101.02.55

- Correction d’un problème dans lequel le produit ne démarre parfois pas après un redémarrage/mise à niveau
- Correction d’un problème dans lequel les paramètres proxy ne sont pas persistants entre les mises à niveau de produits

## <a name="1010075"></a>101.00.75

- Ajout de la prise en charge des types de système de fichiers suivants `ecryptfs`: , `fuse`, , `fuseblk`, `jfs`, `overlay``nfs`, `ramfs`, `reiserfs`et `udf``vfat`
- Nouvelle syntaxe de [l’outil en ligne de commande](linux-resources.md#configure-from-the-command-line).
- Améliorations des performances & résolutions de bogues

## <a name="1009070"></a>100.90.70

> [!WARNING]
> Lors de la mise à niveau du package installé à partir d’une version antérieure à la version 100.90.70, la mise à jour peut échouer sur les distributions Basées sur Red Hat et SLES. Cela est dû à un changement majeur dans le chemin d’accès d’un fichier. Une solution temporaire consiste à supprimer l’ancien package, puis à installer le nouveau. Ce problème n’existe pas dans les versions plus récentes.

- Les [exclusions antivirus désormais prise en charge les caractères génériques](linux-exclusions.md#supported-exclusion-types)
- Ajout de la possibilité de résoudre [les problèmes de performances](linux-support-perf.md) via l’outil `mdatp` en ligne de commande
- Améliorations pour rendre l’installation du package plus robuste
- Améliorations des performances & résolutions de bogues
