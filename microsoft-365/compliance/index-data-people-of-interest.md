---
title: Indexation avancée des données pour une enquête
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
ms.openlocfilehash: 278985aa93f8802f78bd632a5fc90dd6be846b21
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43637906"
---
# <a name="advanced-indexing-of-data-for-an-investigation"></a>Indexation avancée des données pour une enquête

Le contenu du système réel peut être partiellement indexé pour plusieurs raisons, notamment l’existence d’images, de types de fichiers non pris en charge ou lorsque des limites de taille de fichier d’indexation sont rencontrées. Lorsque vous traitez des données à risque élevé, vous devez vous assurer que votre recherche a capturé toutes les données que vous souhaitez analyser. Lorsqu’une personne concernée est ajoutée à une enquête de données, tout contenu considéré comme partiellement indexé est retraité afin de le faire entièrement chercher. Ce processus est appelé *indexation avancée*. 

Pour en savoir plus sur le traitement de la prise en charge et des éléments partiellement indexés, voir :

- [Types de fichiers pris en charge dans les enquêtes de données](supported-filetypes-datainvestigations.md)

- [Éléments partiellement indexés dans la recherche de contenu dans Office 365](partially-indexed-items-in-content-search.md)

- [Formats de fichier indexés par le service de recherche Exchange](https://docs.microsoft.com/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [Extensions de nom de fichier et types de fichier analysés par défaut dans SharePoint Server](https://docs.microsoft.com/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>Affichage des résultats de l’indexation avancée

Une fois le processus d’indexation avancé terminé, vous pouvez comprendre l’efficacité du nouveau traitement.  Dans l’affichage indexation des personnes à intérêt, le graphique répertorie tous les éléments ajoutés à l' *index hybride*.  L’index hybride permet aux enquêtes de données (préversion) de stocker le contenu retraité.

Le graphique inclut également le nombre d’éléments nécessitant une correction et un autre graphique d’erreurs par type de fichier. Pour plus d’informations, consultez la rubrique [erreur de correction lors du traitement des données](error-remediation.md).

## <a name="updating-advanced-indexes-for-people-of-interest"></a>Mise à jour des index avancés pour les personnes concernées

Lorsqu’une personne d’intérêt est ajoutée à une enquête de données, tous les éléments partiellement indexés sont retraités. Toutefois, dans le temps, des éléments indexés plus partiellement peuvent être ajoutés à la boîte aux lettres ou au compte OneDrive d’un utilisateur.  Si nécessaire, vous pouvez mettre à jour les index.

> [!NOTE]
> La mise à jour des index de personnes d’intérêt est un processus de longue durée. Il est recommandé de ne pas mettre à jour les index plus d’une fois par jour dans une enquête.
