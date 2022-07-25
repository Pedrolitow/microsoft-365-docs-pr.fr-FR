---
title: Exporter la file d’attente d’incidents vers des fichiers CSV
description: En savoir plus sur le bouton Exporter qui vient d’être introduit pour migrer des données liées à la file d’attente d’incidents vers des fichiers CSV
keywords: incident, file d’attente, exportation, csv
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: v-smandalika
author: v-smandalika
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 1ea738bfec4f9779bae87a769b784f399e165a07
ms.sourcegitcommit: e852dafda3c0d1dfdde492600093aa17a3dcf5a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2022
ms.locfileid: "67002447"
---
# <a name="export-incidents-queue-to-csv-files"></a>Exporter la file d’attente d’incidents vers des fichiers CSV

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La fonctionnalité **d’exportation** vous permet d’exporter les données dans la file d’attente d’incidents qui s’affiche en fonction des filtres appliqués et des intervalles de temps. Il est disponible sous la forme d’un bouton nommé **Exporter**, comme illustré dans la capture d’écran suivante :

:::image type="content" source="../../media/defender/incidents-queue-with-export-button.png" alt-text="Affiche le bouton Exporter dans la page Incidents du portail Microsoft 365 Defender":::

Lorsque vous cliquez sur le bouton **Exporter** , les données sont exportées vers un fichier CSV. Vous pouvez appliquer différents filtres et intervalles de temps à la file d’attente d’incidents (pas seulement dans le contexte de l’exportation des données, mais dans un contexte générique). Lorsque vous sélectionnez **Exporter**, quels que soient les filtres et/ou les intervalles de temps appliqués à la file d’attente d’incidents, ces données sont exportées vers le fichier CSV.

Une fois que vous avez exporté les données liées à la file d’attente d’incidents dans le fichier CSV, vous pouvez analyser les données et les filtrer davantage, en fonction de vos besoins.

Par exemple, pour les données du fichier CSV, vous pouvez appliquer des filtres pour afficher les données suivantes :
- Données concernant le nombre d’incidents de gravité élevée que vous avez rencontrés au cours des 30 derniers jours.
- Données concernant qui est votre analyste le plus productif.

> [!NOTE]
> Le nombre maximal d’enregistrements que vous pouvez exporter vers un fichier CSV est de 10 000. 

Si vous avez des idées ou des suggestions sur la nouvelle fonctionnalité **d’exportation** (le bouton **Exporter**) pour la file d’attente d’incidents, contactez l’équipe Microsoft ou envoyez vos commentaires via le portail Microsoft 365 Defender.
