---
title: Microsoft 365 Intégration de Defender à Azure Sentinel
description: Utilisez Azure Sentinel comme SIEM pour Microsoft 365 incident et événements Defender.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, courrier électronique, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: b5a53131733d1c7c539676c1d45abe7eabbe2de7
ms.sourcegitcommit: 76c91e7b0d3172de57988eb4576d2b91c2f9ce18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "52707331"
---
# <a name="microsoft-365-defender-integration-with-azure-sentinel"></a>Microsoft 365 Intégration de Defender à Azure Sentinel

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Le connecteur Microsoft 365 Defender pour Azure Sentinel (prévisualisation) envoie tous les incidents Microsoft 365 Defender et les informations d’alerte à Azure Sentinel et maintient les incidents synchronisés. 

Une fois que vous avez ajouté le connecteur, les incidents Microsoft 365 Defender qui incluent toutes les alertes associées, entités et informations pertinentes reçues de Microsoft Defender pour le point de terminaison, Microsoft Defender pour l’identité, Microsoft Defender pour Office 365 et Microsoft Cloud App Security sont diffusés à Azure Sentinel en tant que données d’informations de sécurité et de gestion des événements &mdash; (SIEM), ce qui vous offre un contexte pour effectuer un tri et une réponse aux incidents avec &mdash; Azure Sentinel. 

Une fois dans Azure Sentinel, les incidents restent synchronisés de façon bi-direction avec Microsoft 365 Defender, ce qui vous permet de tirer parti des avantages du centre de sécurité Microsoft 365 et d’Azure Sentinel dans le portail Azure pour l’examen et la réponse aux incidents.

Voici comment cela fonctionne.

:::image type="content" source="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png" alt-text="Flux et partage des données d’incident entre Microsoft 365 Defender et Azure Sentinel":::

## <a name="next-steps"></a>Étapes suivantes

1. Obtenez une meilleure compréhension de [l’intégration Microsoft 365 Defender à Azure Sentinel.](/azure/sentinel/microsoft-365-defender-sentinel-integration)
2. [Connecter données de Microsoft 365 Defender à Azure Sentinel](/azure/sentinel/connect-microsoft-365-defender).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents dans Microsoft 365 Defender](incidents-overview.md)
- [Examiner les incidents avec Azure Sentinel](/azure/sentinel/tutorial-investigate-cases)
