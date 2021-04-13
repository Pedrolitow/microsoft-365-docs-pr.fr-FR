---
title: Vue d’ensemble des détections personnalisées dans Microsoft 365 Defender
description: Comprendre comment utiliser le repérage avancé pour créer des détections personnalisées et générer des alertes
keywords: repérage avancé, repérage de menace, repérage de cybermenace, protection microsoft contre les menaces, microsoft 365, mtp, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto, microsoft 365, Protection Microsoft contre les menaces
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
ms.openlocfilehash: 589a15aa456a96a5eef8042d922d338f056a882d
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51498832"
---
# <a name="custom-detections-overview"></a>Vue d’ensemble des détections personnalisées

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Grâce aux détections personnalisées, vous pouvez surveiller et répondre de manière proactive à divers événements et états système, y compris les activités suspectées de violation et les points de terminaison mal configurés. Cela est rendu possible par des règles de détection personnalisables qui déclenchent automatiquement des alertes, ainsi que des actions de réponse.

Les détections personnalisées fonctionnent avec le repérage [avancé,](advanced-hunting-overview.md)qui fournit un langage de requête puissant et flexible qui couvre un large éventail d’événements et d’informations système à partir de votre réseau. Vous pouvez les configurer pour qu’ils s’exécutent à intervalles réguliers, générant des alertes et prenant des mesures de réponse chaque fois qu’il existe des correspondances.

Les détections personnalisées fournissent :
- Alertes pour les détections basées sur des règles conçues à partir de requêtes de repérage avancé
- Actions de réponse automatique

## <a name="see-also"></a>Voir aussi
- [Créer et gérer des règles de détection personnalisées](custom-detection-rules.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Migrer des requêtes de recherche avancée à partir de Microsoft Defender pour le point de terminaison](advanced-hunting-migrate-from-mde.md)