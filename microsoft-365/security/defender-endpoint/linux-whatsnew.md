---
title: Nouveautés de Microsoft Defender pour Endpoint sur Linux
description: Liste des principales modifications apportées à Microsoft Defender pour Endpoint sur Linux.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, whatsnew, release
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: f79f851f108d38e7900420ed9e6a9ccb9a2164f1
ms.sourcegitcommit: b3c4816b55657b87ed4a5f6a4abe3d505392218e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2021
ms.locfileid: "53726283"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-linux"></a>Nouveautés de Microsoft Defender pour Endpoint sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

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
- Nous avons résolu un problème dans lequel l’utilisation de Microsoft Defender pour endpoint sur Linux sur des systèmes avec des systèmes de fichiers LINUX a conduit à un arrêt du système d’exploitation
- Améliorations des performances & d’autres résolutions de bogues

## <a name="1012563-30121022125630"></a>101.25.63 (30.121022.12563.0)

- Améliorations des performances & résolutions de bogues

## <a name="1012364-30121021123640"></a>101.23.64 (30.121021.12364.0)

- Amélioration des performances pour la situation où un point de montage entier est ajouté à la liste d’exclusion antivirus. Avant cette version, l’activité de fichier provenant du point de montage était toujours traitée par le produit. À partir de cette version, l’activité de fichier pour les points de montage exclus est supprimée, ce qui améliore les performances du produit
- Ajout d’une nouvelle option à l’outil en ligne de commande pour afficher les informations sur la dernière analyse à la demande. Pour afficher des informations sur la dernière analyse à la demande, exécutez `mdatp health --details antivirus`
- Autres améliorations en matière de performances & résolutions de bogues

## <a name="1011853"></a>101.18.53

- PEPT linux est désormais [généralement disponible](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/edr-for-linux-is-now-is-generally-available/ba-p/2048539)
- Ajout d’un nouveau commutateur de ligne de commande ( ) pour ignorer les exclusions antivirus lors des `--ignore-exclusions` analyses personnalisées ( `mdatp scan custom` )
- Étendu avec un nouveau paramètre ( ) qui permet d’enregistrer les journaux de diagnostic dans `mdatp diagnostic create` `--path [directory]` un autre répertoire
- Améliorations des performances & résolutions de bogues

## <a name="1011299"></a>101.12.99

- Améliorations des performances & résolutions de bogues

## <a name="1010476"></a>101.04.76

- Résolutions de bogues

## <a name="1010348"></a>101.03.48

- Résolutions de bogues

## <a name="1010255"></a>101.02.55

- Correction d’un problème dans lequel le produit ne démarre parfois pas après un redémarrage/mise à niveau
- Correction d’un problème dans lequel les paramètres proxy ne sont pas persistants entre les mises à niveau de produits

## <a name="1010075"></a>101.00.75

- Prise en charge supplémentaire pour les types de système de fichiers suivants `ecryptfs` : , , , , , , , `fuse` `fuseblk` `jfs` `nfs` `overlay` `ramfs` `reiserfs` `udf` et `vfat`
- Nouvelle syntaxe de [l’outil en ligne de commande.](linux-resources.md#configure-from-the-command-line)
- Améliorations des performances & résolutions de bogues

## <a name="1009070"></a>100.90.70

> [!WARNING]
> Lors de la mise à niveau du package installé à partir d’une version de produit antérieure à la version 100.90.70, la mise à jour peut échouer sur les distributions Basées sur Red Hat et SLES. Cela est dû à un changement majeur dans le chemin d’accès d’un fichier. Une solution temporaire consiste à supprimer l’ancien package, puis à installer le nouveau. Ce problème n’existe pas dans les versions plus récentes.

- Les [exclusions antivirus désormais prise en charge les caractères génériques](linux-exclusions.md#supported-exclusion-types)
- Ajout de la possibilité de résoudre [les problèmes](linux-support-perf.md) de performances via l’outil en ligne `mdatp` de commande
- Améliorations pour rendre l’installation du package plus robuste
- Améliorations des performances & résolutions de bogues
