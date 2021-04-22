---
title: Vue d'ensemble des détections personnalisées dans Microsoft 365 Defender
description: Comprendre comment utiliser le repérage avancé pour créer des détections personnalisées et générer des alertes
keywords: repérage avancé, repérage de menace, repérage de cybermenace, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: bf635ed03cb0d99d54fc94b622bf244447b32a80
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51935700"
---
# <a name="custom-detections-overview"></a>Vue d’ensemble des détections personnalisées

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Grâce aux détections personnalisées, vous pouvez surveiller et répondre de manière proactive à divers événements et états système, y compris les activités suspectées de violation et les points de terminaison mal configurés. Cela est rendu possible par des règles de détection personnalisables qui déclenchent automatiquement des alertes, ainsi que des actions de réponse.

Les détections personnalisées fonctionnent avec le repérage [avancé,](advanced-hunting-overview.md)qui fournit un langage de requête puissant et flexible qui couvre un large éventail d'événements et d'informations système à partir de votre réseau. Vous pouvez les configurer pour qu'ils s'exécutent à intervalles réguliers, générant des alertes et prenant des mesures de réponse chaque fois qu'il existe des correspondances.

Les détections personnalisées fournissent :
- Alertes pour les détections basées sur des règles conçues à partir de requêtes de repérage avancé
- Actions de réponse automatique

## <a name="see-also"></a>Articles associés
- [Créer et gérer des règles de détection personnalisées](custom-detection-rules.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Migrer des requêtes de recherche avancée à partir de Microsoft Defender pour le point de terminaison](advanced-hunting-migrate-from-mde.md)
