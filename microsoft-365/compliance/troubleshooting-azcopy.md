---
title: Résoudre les problèmes d’AzCopy dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Résolution des erreurs pour Azure AzCopy lors du chargement de données autres qu’Office 365 pour la correction des erreurs dans Advanced eDiscovery.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: f34b47762601a3cc66b46fd8a2691c0fb87d3354
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50919290"
---
# <a name="troubleshoot-azcopy-in-advanced-ediscovery"></a>Résoudre les problèmes d’AzCopy dans Advanced eDiscovery

Lors du chargement de données ou de documents non-Microsoft 365 pour la correction des erreurs dans Advanced eDiscovery, l’interface utilisateur fournit une commande Azure AzCopy qui contient des paramètres avec l’emplacement de stockage des fichiers que vous souhaitez télécharger et l’emplacement de stockage Azure vers lequel les fichiers seront téléchargés. Pour télécharger vos documents, copiez cette commande, puis exécutez-la dans une invite de commandes sur votre ordinateur local.  La capture d’écran ci-dessous montre un exemple de commande AzCopy :

![Télécharger des fichiers autres que Microsoft 365](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

En règle générale, la commande fournie fonctionne lorsque vous l’exécutez. Toutefois, dans certains cas, la commande affichée ne s’exécute pas correctement. Voici quelques raisons possibles.

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>La version prise en charge d’AzCopy n’est pas installée sur l’ordinateur local

Pour l’instant, vous devez utiliser AzCopy v8.1 pour charger des données autres que Microsoft 365 dans Advanced eDiscovery. La commande AzCopy qui s’affiche sur la **page** Télécharger les fichiers de la capture d’écran précédente renvoie une erreur si vous n’utilisez pas AzCopy v8.1. Pour installer cette version, voir Transférer des données [avec AzCopy v8.1 sur Windows.](/previous-versions/azure/storage/storage-use-azcopy)

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>AzCopy n’est pas installé sur l’ordinateur local ou n’est pas installé à l’emplacement par défaut

Si AzCopy n’est pas installé ou s’il est installé à un emplacement autre que l’emplacement d’installation par défaut (autrement dit), vous pouvez recevoir l’erreur suivante lorsque vous exécutez la commande `%ProgramFiles(x86)%` AzCopy :

> Le système ne peut pas trouver le chemin d’accès spécifié.

Si AzCopy n’est pas installé sur l’ordinateur local, vous pouvez trouver des informations d’installation dans Transférer des données avec [AzCopy v8.1 sur Windows](/previous-versions/azure/storage/storage-use-azcopy). Assurez-vous de l’installer à l’emplacement par défaut.

Si AzCopy est installé, mais qu’il est installé à un emplacement différent de l’emplacement par défaut, vous pouvez copier la commande, la coller dans un fichier texte, puis modifier le chemin d’accès à l’emplacement où AzCopy est installé. Par exemple, si Azcopy se trouve dans , vous pouvez modifier la première partie de la `%ProgramFiles%` commande de `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe` `%ProgramFiles%\Microsoft SDKs\Azure\AzCopy` . Après avoir fait cette modification, copiez-la à partir du fichier texte, puis exécutez une invite de commandes.

> [!TIP]
> Si AzCopy est installé à un autre emplacement que l’emplacement d’installation par défaut, envisagez de le désinstaller, puis de le réinstaller à l’emplacement par défaut. Cela permettra d’éviter ce problème à l’avenir.