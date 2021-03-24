---
title: Vue d’ensemble des détections personnalisées dans Microsoft Defender ATP
ms.reviewer: ''
description: Comprendre comment utiliser le repérage avancé pour créer des détections personnalisées et générer des alertes
keywords: détections personnalisées, alertes, règles de détection, repérage avancé, recherche, requête, actions de réponse, intervalle, mdatp, microsoft defender atp
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 6c9befcc4b1224cacb2ab4eb8530e30a397aab49
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51056737"
---
# <a name="custom-detections-overview"></a>Vue d’ensemble des détections personnalisées

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


Grâce aux détections personnalisées, vous pouvez surveiller et répondre de manière proactive à divers événements et états système, y compris les activités suspectées de violation et les appareils mal configurés. Vous pouvez le faire avec des règles de détection personnalisables qui déclenchent automatiquement des alertes et des actions de réponse.

Les détections personnalisées fonctionnent avec le repérage [avancé,](advanced-hunting-overview.md)qui fournit un langage de requête puissant et flexible qui couvre un large éventail d’événements et d’informations système à partir de votre réseau. Vous pouvez les configurer pour qu’ils s’exécutent à intervalles réguliers, générant des alertes et prenant des mesures de réponse chaque fois qu’il existe des correspondances.

Les détections personnalisées fournissent :
- Alertes pour les détections basées sur des règles conçues à partir de requêtes de repérage avancé
- Actions de réponse automatique qui s’appliquent aux fichiers et appareils

## <a name="related-topics"></a>Voir aussi
- [Créer des règles de détection](custom-detection-rules.md)
- [Afficher et gérer les règles de détection](custom-detections-manage.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
