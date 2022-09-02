---
title: Microsoft Defender pour point de terminaison indicateurs d’événements de chronologie de l’appareil
description: Utiliser Microsoft Defender pour point de terminaison indicateurs d’événements de chronologie de l’appareil pour
keywords: Chronologie de l’appareil Defender pour point de terminaison, indicateurs d’événements
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 8ff91c002f555920a6a73d2070b688bc5d5f5961
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67523399"
---
# <a name="microsoft-defender-for-endpoint-device-timeline-event-flags"></a>Microsoft Defender pour point de terminaison indicateurs d’événements de chronologie de l’appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Les indicateurs d’événements dans la chronologie de l’appareil Defender pour point de terminaison vous aident à filtrer et organiser des événements spécifiques lorsque vous examinez des attaques potentielles.

La chronologie de l’appareil Defender pour point de terminaison fournit une vue chronologique des événements et des alertes associées observées sur un appareil. Cette liste d’événements offre une visibilité complète des événements, fichiers et adresses IP observés sur l’appareil. La liste peut parfois être longue. Les indicateurs d’événements de chronologie de l’appareil vous aident à suivre les événements qui peuvent être liés.

Une fois que vous avez parcouru une chronologie d’appareil, vous pouvez trier, filtrer et exporter les événements spécifiques que vous avez signalés.

Lors de la navigation dans la chronologie de l’appareil, vous pouvez rechercher et filtrer des événements spécifiques. Vous pouvez définir des indicateurs d’événements en :

- Mise en évidence des événements les plus importants
- Marquage des événements qui nécessitent une immersion approfondie
- Création d’une chronologie de violation propre

## <a name="flag-an-event"></a>Marquer un événement

1. Rechercher l’événement que vous souhaitez marquer

2. Cliquez sur l’icône d’indicateur dans la colonne Indicateur. 

:::image type="content" source="images/device-flags.png" alt-text="Indicateur de chronologie de l’appareil" lightbox="images/device-flags.png":::

## <a name="view-flagged-events"></a>Afficher les événements avec indicateur

1. Dans la section **Filtres de** chronologie, activez les **événements avec indicateur**.
2. Cliquez sur **Appliquer**. Seuls les événements avec indicateur sont affichés.

Vous pouvez appliquer des filtres supplémentaires en cliquant sur la barre de temps. Cela n’affichera que les événements antérieurs à l’événement marqué.  

:::image type="content" source="images/device-flag-filter.png" alt-text="Indicateur de chronologie de l’appareil avec le filtre activé" lightbox="images/device-flag-filter.png":::