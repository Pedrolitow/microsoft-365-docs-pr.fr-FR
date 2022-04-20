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
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Lorsqu’un consignateur est ajouté à un cas eDiscovery (Premium), tout contenu considéré comme partiellement indexé est retraité pour le rendre entièrement consultable.
ms.openlocfilehash: 8b7dbbb13b9a667a7b5a50a5535634414c0caec5
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993619"
---
# <a name="advanced-indexing-of-custodian-data"></a>Indexation avancée des données des consignataires

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Lorsqu’un consignateur est ajouté à un cas eDiscovery (Premium), tout contenu considéré comme partiellement indexé ou ayant eu des erreurs d’indexation est réindexé. Ce processus de réindexation est appelé *indexation avancée*. Il existe de nombreuses raisons pour lesquelles le contenu est partiellement indexé ou comporte des erreurs d’indexation. Cela inclut les fichiers image ou la présence d’images dans un fichier, les types de fichiers non pris en charge ou les limites d’indexation de taille de fichier. Pour SharePoint fichiers, l’indexation avancée s’exécute uniquement sur les éléments qui sont marqués comme partiellement indexés ou qui ont des erreurs d’indexation. Dans Exchange, les messages électroniques qui ont des pièces jointes d’image ne sont pas marqués comme partiellement indexés ou avec des erreurs d’indexation. Cela signifie que ces fichiers ne seront pas réindexés par le processus d’indexation avancé.

Pour en savoir plus sur la prise en charge du traitement et les éléments partiellement indexés, consultez :

- [Types de fichiers pris en charge dans eDiscovery (Premium)](supported-filetypes-ediscovery20.md)

- [Éléments partiellement indexés dans eDiscovery](partially-indexed-items-in-content-search.md)

- [Formats de fichier indexés par le service de recherche Exchange](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [Extensions de nom de fichier et types de fichier analysés par défaut dans SharePoint Server](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>Affichage des résultats de l’indexation avancée

Une fois le processus d’indexation avancé terminé, vous pouvez comprendre l’efficacité du retraitement.  Dans la vue Résultats de l’indexation avancée sous l’onglet **Traitement** d’un cas, le graphique répertorie le nombre d’éléments ajoutés à *l’index hybride*.  L’index hybride est l’emplacement où eDiscovery (Premium) stocke le contenu retraité.

Cette vue inclut également le nombre d’éléments qui nécessitent une correction et un autre graphique d’erreurs par type de fichier. Pour plus d’informations, voir :

- [Correction d’erreur lors du traitement des données](error-remediation-when-processing-data-in-advanced-ediscovery.md)

- [Correction d’erreur sur élément unique](single-item-error-remediation.md)

## <a name="updating-the-advanced-index-for-custodians"></a>Mise à jour de l’index avancé pour les consignatateurs

Lorsqu’un consignateur est ajouté à un cas eDiscovery (Premium), tous les éléments partiellement indexés sont retraités. Toutefois, à mesure que le temps passe, des éléments partiellement indexés peuvent être ajoutés à la boîte aux lettres ou au compte OneDrive d’un utilisateur.  Si nécessaire, vous pouvez mettre à jour l’index pour un consignateur spécifique. Pour plus d’informations, consultez [Gérer les consignatateurs dans un cas eDiscovery (Premium).](manage-new-custodians.md#reindex-custodian-data) Vous pouvez également mettre à jour l’index de tous les consignats dans un cas en cliquant sur **l’index De mise à jour** sous l’onglet **Traitement** .

> [!NOTE]
> La mise à jour des index de consignation est un processus long. Il est recommandé de ne pas mettre à jour les index plusieurs fois par jour dans un cas.
