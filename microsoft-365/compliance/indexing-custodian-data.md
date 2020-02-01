---
title: Indexation avancée des données des consignataires
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: ''
ms.openlocfilehash: 5ab54e84de7434a16bdf7eb7d04fad7b9af05440
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41600631"
---
# <a name="advanced-indexing-of-custodian-data"></a>Indexation avancée des données des consignataires

Lorsqu’un dépositaire est ajouté à un cas avancé de découverte électronique, tout contenu dans Office 365 considéré comme partiellement indexé est retraité afin de le faire entièrement chercher.  Ce processus est appelé *indexation avancée*. Le contenu peut être partiellement indexé pour plusieurs raisons, notamment l’existence d’images, de types de fichiers non pris en charge ou lorsque des limites de taille de fichier d’indexation sont rencontrées.

Pour en savoir plus sur le traitement de la prise en charge dans Office 365 et les éléments partiellement indexés, voir :

- [Types de fichiers pris en charge dans Advanced eDiscovery](supported-filetypes-ediscovery20.md)
- [Éléments partiellement indexés dans la recherche de contenu dans Office 365](partially-indexed-items-in-content-search.md)
- [Formats de fichier indexés par le service de recherche Exchange](https://docs.microsoft.com/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)
- [Extensions de nom de fichier et types de fichier analysés par défaut dans SharePoint Server](https://docs.microsoft.com/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>Affichage des résultats de l’indexation avancée

Une fois le processus d’indexation avancé terminé, vous pouvez comprendre l’efficacité du nouveau traitement.  Dans la vue d’indexation dépositaire, le graphique répertorie tous les éléments ajoutés à l' *index hybride*.  L’index hybride est l’emplacement où eDiscovery avancée stocke le contenu retraité.

Le graphique inclut également le nombre d’éléments nécessitant une correction et un autre graphique d’erreurs par type de fichier. Pour plus d’informations, voir :

- [Correction d’erreur lors du traitement des données](error-remediation.md)
- [Correction d’erreur sur élément unique](single-item-error-remediation.md)

## <a name="updating-advanced-indexes-for-custodians"></a>Mise à jour des index avancés pour les dépositaires

Lorsqu’un dépositaire est ajouté à un cas avancé eDiscovery, tous les éléments partiellement indexés sont retraités. Toutefois, dans le temps, des éléments indexés plus partiellement peuvent être ajoutés à la boîte aux lettres ou au compte OneDrive d’un utilisateur.  Si nécessaire, vous pouvez mettre à jour les index.

> [!NOTE]
> La mise à jour des index de dépositaire est un processus de longue durée. Il est recommandé de ne pas mettre à jour les index plus d’une fois par jour dans un cas.
