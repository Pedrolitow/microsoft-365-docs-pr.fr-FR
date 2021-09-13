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
description: Lorsqu’un dépositaire est ajouté à un cas Advanced eDiscovery, tout contenu considéré comme partiellement indexé est réprocessé pour le rendre entièrement utilisable dans une recherche.
ms.openlocfilehash: 8a43b0cd9b7fcac1745b917dc5a1c198fa2a1e61
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59175851"
---
# <a name="advanced-indexing-of-custodian-data"></a>Indexation avancée des données des consignataires

Lorsqu’un dépositaire est ajouté à un cas Advanced eDiscovery, tout contenu considéré comme partiellement indexé ou avec des erreurs d’indexation est réindexé pour le rendre entièrement utilisable dans une recherche.  Ce processus de réindexation est appelé *indexation avancée.* Il existe de nombreuses raisons pour lesquelles le contenu est partiellement indexé ou présente des erreurs d’indexation. Cela inclut les fichiers image ou la présence d’images dans un fichier, les types de fichiers non pris en compte ou les limites d’indexation de taille de fichier. Pour SharePoint fichiers, l’indexation avancée s’exécute uniquement sur les éléments qui sont marqués comme partiellement indexés ou qui ont des erreurs d’indexation. Dans Exchange, les messages électroniques qui ont des pièces jointes d’image ne sont pas marqués comme partiellement indexés ou avec des erreurs d’indexation. Cela signifie que ces fichiers ne seront pas réindexés par le processus d’indexation avancée.

Pour en savoir plus sur le traitement de la prise en charge et des éléments partiellement indexés, voir :

- [Types de fichiers pris en charge dans Advanced eDiscovery](supported-filetypes-ediscovery20.md)

- [Éléments partiellement indexés dans eDiscovery](partially-indexed-items-in-content-search.md)

- [Formats de fichier indexés par le service de recherche Exchange](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [Extensions de nom de fichier et types de fichier analysés par défaut dans SharePoint Server](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>Affichage des résultats de l’indexation avancée

Une fois le processus d’indexation avancé terminé, vous pouvez comprendre l’efficacité du nouveau traitement.  Dans l’affichage Des résultats  d’indexation avancée sous l’onglet Traitement d’un cas, le graphique répertorie le nombre d’éléments ajoutés à *l’index hybride.*  L’index hybride est l’emplacement où Advanced eDiscovery stocke le contenu retraite.

Cette vue inclut également le nombre d’éléments qui nécessitent une correction et un autre graphique d’erreurs par type de fichier. Pour plus d’informations, consultez :

- [Correction d’erreur lors du traitement des données](error-remediation-when-processing-data-in-advanced-ediscovery.md)

- [Correction d’erreur sur élément unique](single-item-error-remediation.md)

## <a name="updating-the-advanced-index-for-custodians"></a>Mise à jour de l’index avancé pour les dépositaires

Lorsqu’un dépositaire est ajouté à un Advanced eDiscovery, tous les éléments partiellement indexés sont retraités. Toutefois, au fil du temps, des éléments partiellement indexés peuvent être ajoutés à la boîte aux lettres ou au compte OneDrive utilisateur.  Si nécessaire, vous pouvez mettre à jour l’index pour un dépositaire spécifique. Pour plus d’informations, [voir Gérer les dépositaires dans Advanced eDiscovery cas.](manage-new-custodians.md#re-index-custodian-data) Vous pouvez également mettre à jour l’index pour tous les dépositaires dans un cas en cliquant sur **l’index** de mise à jour sous **l’onglet Traitement.**

> [!NOTE]
> La mise à jour des index des dépositaires est un processus de longue durée. Il est recommandé de ne pas mettre à jour les index plus d’une fois par jour dans un cas.
