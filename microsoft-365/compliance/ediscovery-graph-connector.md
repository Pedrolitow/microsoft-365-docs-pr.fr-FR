---
title: connecteurs Graph Microsoft Purview eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 07/15/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- m365-security-compliance
- m365solution-ediscovery
- m365initiative-compliance
- m365solution-overview
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
description: Les clients Microsoft 365 peuvent effectuer des recherches eDiscovery sur le contenu ingéré pour la recherche d’entreprise.
ms.openlocfilehash: df6f948f60b74da6868f4f3877ee3a39e97c2a46
ms.sourcegitcommit: 180da7b39cfda7263a89bda0c3b93d9d6e55f3c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2022
ms.locfileid: "66992532"
---
# <a name="use-graph-connectors-with-ediscovery-premium"></a>Utiliser des connecteurs Graph avec eDiscovery (Premium)

Les clients Microsoft 365 peuvent effectuer des recherches eDiscovery sur le contenu ingéré pour la recherche d’entreprise. Cela aidera les organisations à améliorer leur posture de conformité aux sources de contenu externes en les intégrant dans la portée des solutions de conformité Microsoft.

Avec les connecteurs Graph, vous pouvez activer le contenu provenant de sources de données externes pour qu’il soit disponible pour Microsoft Purview eDiscovery solution Premium. En savoir plus sur l’établissement de connecteurs Graph pour votre organisation ici : [Vue d’ensemble des connecteurs Microsoft Graph pour Recherche Microsoft](/microsoftsearch/connectors-overview).

## <a name="add-graph-connector-as-a-data-source-within-a-case"></a>Ajouter le connecteur Graph en tant que source de données dans un cas

Une fois que les connecteurs Graph sont établis pour une organisation et qu’eDiscovery est activé, l’option permettant d’ajouter la source de données Graph Connector au cas est disponible dans des emplacements autres que Microsoft 365. Seuls les connecteurs qui ont été établis et activés seront disponibles pour le gestionnaire eDiscovery pour inclusion dans un cas.

:::image type="content" source="../media/ediscovery-graph-new.png" alt-text="Vous pouvez sélectionner Graph comme source de données.":::

## <a name="collect-graph-connectors-content"></a>Collecter le contenu des connecteurs Graph

Lors de l’ajout de contenu Graph Connectors en tant que source de données, ce contenu est ensuite disponible pour la recherche et la collecte. Dans l’Assistant Collecte, sélectionnez le contenu du connecteur Graph en tant que source de données non gardienne, utilisez des conditions telles que la plage de dates, les mots clés et bien plus encore pour rechercher dans le contenu connecté pour collecter uniquement le contenu qui vous intéresse. À la fin de l’Assistant, obtenez des estimations pour la quantité de contenu qui contient les accès à vos critères de recherche, puis validez la collection dans le jeu de révisions.  

## <a name="review-content"></a>Passer en revue le contenu

Une fois collectés dans un jeu de révision, les gestionnaires eDiscovery peuvent passer en revue le contenu des connecteurs Graph pour en savoir plus sur le contenu et travailler pour évaluer si les informations sont critiques et pertinentes pour le cas.  

## <a name="export-content"></a>Exporter le contenu

Une fois validé que le contenu collecté dans la révision est le contenu correct, ce contenu est alors disponible pour l’exportation à partir du jeu de révision directement. Sélectionnez les options d’exportation et envoyez le travail d’exportation pour le contenu connecteurs à exporter à partir du jeu de révision.
