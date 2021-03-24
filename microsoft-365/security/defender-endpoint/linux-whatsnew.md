---
title: Nouveautés de Microsoft Defender pour Endpoint pour Linux
description: Liste des principales modifications apportées à Microsoft Defender ATP pour Linux.
keywords: microsoft, defender, atp, linux, whatsnew, release
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
ms.openlocfilehash: 43324b0f3a0d5d351d7164bb05415899bf7d181c
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51062449"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-for-linux"></a>Nouveautés de Microsoft Defender pour Endpoint pour Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

## <a name="1011853"></a>101.18.53

- EDR pour Linux est désormais [généralement disponible](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/edr-for-linux-is-now-is-generally-available/ba-p/2048539)
- Ajout d’un nouveau commutateur de ligne de commande ( ) pour ignorer les exclusions av lors `--ignore-exclusions` des analyses personnalisées ( `mdatp scan custom` )
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

- Ajout de la prise en charge des types de système de fichiers suivants `ecryptfs` : , , , , , , , `fuse` `fuseblk` `jfs` `nfs` `overlay` `ramfs` `reiserfs` `udf` et `vfat`
- Nouvelle syntaxe pour [l’outil en ligne de commande.](linux-resources.md#configure-from-the-command-line)
- Améliorations des performances & résolutions de bogues

## <a name="1009070"></a>100.90.70

> [!WARNING]
> Lors de la mise à niveau du package installé à partir d’une version antérieure à la version 100.90.70, la mise à jour peut échouer sur les distributions Basées sur Red Hat et SLES. Cela est dû à un changement majeur dans le chemin d’accès d’un fichier. Une solution temporaire consiste à supprimer l’ancien package, puis à installer le nouveau. Ce problème n’existe pas dans les versions plus récentes.

- Les [exclusions antivirus désormais prise en charge les caractères génériques](linux-exclusions.md#supported-exclusion-types)
- Ajout de la possibilité de résoudre [les problèmes](linux-support-perf.md) de performances via l’outil en ligne `mdatp` de commande
- Améliorations pour rendre l’installation du package plus robuste
- Améliorations des performances & résolutions de bogues
