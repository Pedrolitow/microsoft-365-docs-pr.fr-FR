---
title: intégration de Microsoft 365 Defender à Azure Sentinel
description: Utilisez Azure Sentinel comme SIEM pour Microsoft 365 Defender incident et les événements.
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
ms.openlocfilehash: ac151ec33943a4d6c93b8bec08999931e867fb114fc36ce98695e7a976545cdd
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53884154"
---
# <a name="microsoft-365-defender-integration-with-azure-sentinel"></a>intégration de Microsoft 365 Defender à Azure Sentinel

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Le connecteur Microsoft 365 Defender pour Azure Sentinel (prévisualisation) envoie tous les incidents Microsoft 365 Defender et les informations d’alerte à Azure Sentinel et maintient les incidents synchronisés. 

Une fois que vous avez ajouté le connecteur, les incidents Microsoft 365 Defender qui incluent toutes les alertes associées, entités et informations pertinentes reçues de Microsoft Defender pour le point de terminaison, Microsoft Defender pour l’identité, Microsoft Defender pour Office 365 et Microsoft Cloud App Security sont diffusés vers Azure Sentinel en tant qu’informations de sécurité et données de gestion des événements &mdash; (SIEM), ce qui vous offre un contexte pour effectuer un tri et une réponse aux incidents avec &mdash; Azure Sentinel. 

Une fois dans Azure Sentinel, les incidents restent synchronisés bi-directionnaux avec Microsoft 365 Defender, ce qui vous permet de tirer parti des avantages du portail Microsoft 365 Defender et d’Azure Sentinel dans le portail Azure pour l’examen et la réponse aux incidents.

Regardez cette courte vue d’ensemble de l’intégration d’Azure Sentinel Microsoft 365 Defender (4 minutes).

<br>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRo]


Voici comment cela fonctionne.

:::image type="content" source="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png" alt-text="Le flux et le partage des données d’incident entre Microsoft 365 Defender et Azure Sentinel":::

## <a name="next-steps"></a>Étapes suivantes

1. Obtenez une compréhension plus approfondie de [l Microsoft 365 Defender’intégration à Azure Sentinel.](/azure/sentinel/microsoft-365-defender-sentinel-integration)
2. [Connecter données de Microsoft 365 Defender à Azure Sentinel](/azure/sentinel/connect-microsoft-365-defender).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents dans Microsoft 365 Defender](incidents-overview.md)
- [Examiner les incidents avec Azure Sentinel](/azure/sentinel/tutorial-investigate-cases)
