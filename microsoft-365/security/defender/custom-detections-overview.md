---
title: Vue d’ensemble des détections personnalisées dans Microsoft 365 Defender
description: Comprendre comment utiliser la chasse avancée pour créer des détections personnalisées et générer des alertes
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m - m365-security - tier2
ms.topic: conceptual
ms.openlocfilehash: 8cf385296243556ce9e131a47e5b00dca42e5864
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68640673"
---
# <a name="custom-detections-overview"></a>Vue d’ensemble des détections personnalisées

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

Avec les détections personnalisées, vous pouvez surveiller et répondre de manière proactive à différents événements et états système, y compris les activités de violation suspectes et les points de terminaison mal configurés. Cela est rendu possible par des règles de détection personnalisables qui déclenchent automatiquement des alertes ainsi que des actions de réponse.

Les détections personnalisées fonctionnent avec la [chasse avancée](advanced-hunting-overview.md), qui fournit un langage de requête puissant et flexible qui couvre un large ensemble d’événements et d’informations système à partir de votre réseau. Vous pouvez les définir pour qu’ils s’exécutent à intervalles réguliers, en générant des alertes et en effectuant des actions de réponse chaque fois qu’il y a des correspondances.

Les détections personnalisées fournissent les éléments suivants :
- Alertes pour les détections basées sur des règles générées à partir de requêtes de chasse avancées
- Actions de réponse automatique

## <a name="see-also"></a>Voir aussi
- [Créer et gérer des règles de détection personnalisées](custom-detection-rules.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Migrer des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison](advanced-hunting-migrate-from-mde.md)
