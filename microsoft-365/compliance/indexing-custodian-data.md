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
description: Lorsqu’un dépositaire est ajouté à un cas avancé de découverte électronique, tout contenu considéré comme partiellement indexé est retraité afin de le faire entièrement chercher.
ms.openlocfilehash: 0618af5bcc18622ee8091782f55648f455230b6b
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43637896"
---
# <a name="advanced-indexing-of-custodian-data"></a>Indexation avancée des données des consignataires

Lorsqu’un dépositaire est ajouté à un cas avancé de découverte électronique, tout contenu considéré comme partiellement indexé est retraité afin de le faire entièrement chercher.  Ce processus est appelé *indexation avancée*. Le contenu peut être partiellement indexé pour plusieurs raisons, notamment l’existence d’images, de types de fichiers non pris en charge ou lorsque des limites de taille de fichier d’indexation sont rencontrées.

Pour en savoir plus sur le traitement de la prise en charge et des éléments partiellement indexés, voir :

- [Types de fichiers pris en charge dans Advanced eDiscovery](supported-filetypes-ediscovery20.md)

- [Éléments partiellement indexés dans la recherche de contenu dans Office 365](partially-indexed-items-in-content-search.md)

- [Formats de fichier indexés par le service de recherche Exchange](https://docs.microsoft.com/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [Extensions de nom de fichier et types de fichier analysés par défaut dans SharePoint Server](https://docs.microsoft.com/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>Affichage des résultats de l’indexation avancée

Une fois le processus d’indexation avancé terminé, vous pouvez comprendre l’efficacité du nouveau traitement.  Dans l’affichage des résultats d’indexation avancés, sous l’onglet **traitement** d’un cas, le graphique indique le nombre d’éléments ajoutés à l' *index hybride*.  L’index hybride est l’emplacement où eDiscovery avancée stocke le contenu retraité.

Cette vue inclut également le nombre d’éléments nécessitant une correction et un autre graphique d’erreurs par type de fichier. Si vous souhaitez en savoir plus, consultez les articles : 

- [Correction d’erreur lors du traitement des données](error-remediation.md)

- [Correction d’erreur sur élément unique](single-item-error-remediation.md)

## <a name="updating-the-advanced-index-for-custodians"></a>Mise à jour de l’index avancé pour les dépositaires

Lorsqu’un dépositaire est ajouté à un cas avancé eDiscovery, tous les éléments partiellement indexés sont retraités. Toutefois, dans le temps, des éléments indexés plus partiellement peuvent être ajoutés à la boîte aux lettres ou au compte OneDrive d’un utilisateur.  Si nécessaire, vous pouvez mettre à jour l’index pour un dépositaire spécifique. Pour plus d’informations, consultez la rubrique [Manage dépositaires in an Advanced eDiscovery case](manage-new-custodians.md#re-index-custodian-data). Vous pouvez également mettre à jour l’index de tous les dépositaires dans un cas en cliquant sur l' **index de mise à jour** sous l’onglet **traitement** .

> [!NOTE]
> La mise à jour des index de dépositaire est un processus de longue durée. Il est recommandé de ne pas mettre à jour les index plus d’une fois par jour dans un cas.
