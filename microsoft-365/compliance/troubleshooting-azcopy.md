---
title: Résoudre les problèmes d’AzCopy dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Résoudre les erreurs pour Azure AzCopy lors du chargement de données non Office 365 pour la correction des erreurs dans eDiscovery (Premium).
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 0ca4d0b661a4588512d7abd44140b64f57ec432b
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67826640"
---
# <a name="troubleshoot-azcopy-in-ediscovery-premium"></a>Résoudre les problèmes d’AzCopy dans eDiscovery (Premium)

Lors du chargement de données ou de documents non Microsoft 365 à des fins de correction d’erreur dans Microsoft Purview eDiscovery (Premium), l’interface utilisateur fournit une commande Azure AzCopy qui contient des paramètres avec l’emplacement où les fichiers que vous souhaitez charger sont stockés et l’emplacement de stockage Azure vers lequel les fichiers seront chargés. Pour charger vos documents, copiez cette commande, puis exécutez-la dans une invite de commandes sur votre ordinateur local.  La capture d’écran suivante montre un exemple de commande AzCopy :

![Chargez des fichiers non-Microsoft 365.](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

En règle générale, la commande fournie fonctionne quand vous l’exécutez. Toutefois, il peut arriver que la commande affichée ne s’exécute pas correctement. Voici quelques raisons possibles.

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>La version prise en charge d’AzCopy n’est pas installée sur l’ordinateur local

À ce stade, vous devez utiliser AzCopy v8.1 pour charger des données non-Microsoft 365 dans eDiscovery (Premium). La commande AzCopy affichée sur la page **Charger des fichiers** affichée dans la capture d’écran précédente renvoie une erreur si vous n’utilisez pas AzCopy v8.1. Pour installer cette version, consultez [Transférer des données avec AzCopy v8.1 sur Windows](/previous-versions/azure/storage/storage-use-azcopy).

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>AzCopy n’est pas installé sur l’ordinateur local ou n’est pas installé à l’emplacement par défaut

Si AzCopy n’est pas installé ou s’il est installé dans un emplacement autre que l’emplacement d’installation par défaut (autrement `%ProgramFiles(x86)%`dit), vous pouvez recevoir l’erreur suivante lorsque vous exécutez la commande AzCopy :

> Le système ne trouve pas le chemin d’accès spécifié.

Si AzCopy n’est pas installé sur l’ordinateur local, vous trouverez des informations d’installation dans [Transférer des données avec AzCopy v8.1 sur Windows](/previous-versions/azure/storage/storage-use-azcopy). Veillez à l’installer à l’emplacement par défaut.

Si AzCopy est installé, mais qu’il est installé dans un emplacement différent de l’emplacement par défaut, vous pouvez copier la commande, la coller dans un fichier texte, puis modifier le chemin d’accès à l’emplacement où AzCopy est installé. Par exemple, si Azcopy se trouve dans `%ProgramFiles%`, vous pouvez remplacer la première partie de la commande `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe` `%ProgramFiles%\Microsoft SDKs\Azure\AzCopy`par . Après avoir apporté cette modification, copiez-la à partir du fichier texte, puis exécutez-la à l’invite de commandes.

> [!TIP]
> Si AzCopy est installé dans un autre emplacement, envisagez de le désinstaller, puis de le réinstaller à l’emplacement par défaut. Cela permettra d’éviter ce problème à l’avenir.