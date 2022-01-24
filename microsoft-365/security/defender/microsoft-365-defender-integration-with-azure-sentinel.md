---
title: intégration de Microsoft 365 Defender à Microsoft Sentinel
description: Utilisez Microsoft Sentinel comme SIEM pour Microsoft 365 Defender incident et événements.
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 0c00ecdde6f94d7737cb4dc8d503b83469821fb5
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2022
ms.locfileid: "62171889"
---
# <a name="microsoft-365-defender-integration-with-microsoft-sentinel"></a>intégration de Microsoft 365 Defender à Microsoft Sentinel

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Le connecteur Microsoft 365 Defender pour Microsoft Sentinel (prévisualisation) envoie tous les incidents Microsoft 365 Defender et alertes à Microsoft Sentinel et maintient les incidents synchronisés. 

Une fois que vous avez ajouté le connecteur, Microsoft 365 Defender incidents qui incluent toutes les alertes associées, entités et informations pertinentes reçues de Microsoft Defender pour le point de &mdash; terminaison, Microsoft Defender pour l’identité, Microsoft Defender pour Office 365 et Microsoft Defender pour les applications cloud &mdash; sont diffusés à Microsoft Sentinel en tant qu’informations de sécurité et données de gestion des événements (SIEM), ce qui vous fournit un contexte pour effectuer un tri et une réponse aux incidents avec Microsoft Sentinel. 

Une fois dans Microsoft Sentinel, les incidents restent synchronisés de manière bi-direction avec Microsoft 365 Defender, ce qui vous permet de tirer parti des avantages du portail Microsoft 365 Defender et de Microsoft Sentinel dans le portail Azure pour l’examen et la réponse aux incidents.

Regardez cette courte vue d’ensemble de l’intégration de Microsoft Sentinel Microsoft 365 Defender (4 minutes).

<br>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRo]


Voici comment cela fonctionne.

:::image type="content" source="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png" alt-text="Flux et partage des données d’incident entre Microsoft 365 Defender et Microsoft Sentinel.":::

## <a name="next-steps"></a>Prochaines étapes

1. Obtenez une compréhension approfondie de [l’intégration Microsoft 365 Defender avec Microsoft Sentinel.](/azure/sentinel/microsoft-365-defender-sentinel-integration)
2. [Connecter données de Microsoft 365 Defender à Microsoft Sentinel.](/azure/sentinel/connect-microsoft-365-defender)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents dans Microsoft 365 Defender](incidents-overview.md)
- [Examiner les incidents avec Microsoft Sentinel](/azure/sentinel/tutorial-investigate-cases)
