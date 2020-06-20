---
title: Résolution des problèmes liés à AzCopy dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Résoudre les erreurs liées à Azure AzCopy lors du chargement de données non Office 365 pour la correction d’erreur dans Advanced eDiscovery.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 0185c179039b7aec72bc400709225ef42489f620
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44819144"
---
# <a name="troubleshoot-azcopy-in-advanced-ediscovery"></a>Résolution des problèmes liés à AzCopy dans Advanced eDiscovery

Lors du chargement de données ou de documents non-Microsoft 365 pour la correction d’erreur dans Advanced eDiscovery, l’interface utilisateur fournit une commande AzCopy Azure qui contient les paramètres de l’emplacement où les fichiers que vous souhaitez télécharger sont stockés et l’emplacement de stockage Azure dans lequel les fichiers seront téléchargés. Pour télécharger vos documents, copiez cette commande, puis exécutez-la dans une invite de commandes sur votre ordinateur local.  La capture d’écran suivante illustre un exemple de commande AzCopy :

![Télécharger des fichiers non-Microsoft 365](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

En règle générale, la commande fournie fonctionne lorsque vous l’exécutez. Toutefois, il peut arriver que la commande affichée ne s’exécute pas correctement. Voici quelques raisons possibles.

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>La version prise en charge d’AzCopy n’est pas installée sur l’ordinateur local

Pour le moment, vous devez utiliser AzCopy v 8.1 pour charger des données non-Microsoft 365 dans Advanced eDiscovery. La commande AzCopy affichée sur la page **Télécharger les fichiers** indiquée dans la capture d’écran précédente renvoie une erreur si vous n’utilisez pas AzCopy v 8.1. Pour installer cette version, voir [transférer des données avec le AzCopy v 8.1 sous Windows](https://docs.microsoft.com/previous-versions/azure/storage/storage-use-azcopy).

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>AzCopy n’est pas installé sur l’ordinateur local ou il n’est pas installé à l’emplacement par défaut

Si AzCopy n’est pas installé ou s’il est installé à un emplacement autre que l’emplacement d’installation par défaut (c’est-à-dire `%ProgramFiles(x86)%` ), il se peut que vous receviez le message d’erreur suivant lorsque vous exécutez la commande AzCopy :

    The system cannot find the path specified.

Si AzCopy n’est pas installé sur l’ordinateur local, vous pouvez trouver des informations relatives à l’installation dans [le transfert de données avec le AzCopy v 8.1 sous Windows](https://docs.microsoft.com/previous-versions/azure/storage/storage-use-azcopy). Veillez à l’installer à l’emplacement par défaut.

Si AzCopy est installé, mais qu’il est installé à un emplacement différent de l’emplacement par défaut, vous pouvez copier la commande, la coller dans un fichier texte, puis modifier le chemin d’accès à l’emplacement où AzCopy est installé. Par exemple, si Azcopy se trouve dans `%ProgramFiles%` , vous pouvez remplacer la première partie de la commande par `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe` `%ProgramFiles%\Microsoft SDKs\Azure\AzCopy` . Une fois que vous avez effectué cette modification, copiez-la à partir du fichier texte, puis exécutez-la dans une invite de commandes.

> [!TIP]
> Si AzCopy est installé à un emplacement autre que l’emplacement d’installation par défaut, envisagez de le désinstaller, puis de le réinstaller à l’emplacement par défaut. Cela vous permettra d’éviter ce problème à l’avenir.
