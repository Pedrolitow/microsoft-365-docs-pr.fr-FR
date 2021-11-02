---
title: Quotas de recherche avancés et paramètres d’utilisation dans Microsoft 365 Defender
description: Comprendre les différents quotas et paramètres d’utilisation (limites de service) qui conservent la réactivité du service de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema, kusto, CPU limit, query limit, resources, maximum results, quota, parameters, allocation
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: fe0ad42ac0ebfc7f6816e412ab6ffb0ac9291b44
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60643162"
---
# <a name="advanced-hunting-quotas-and-usage-parameters"></a>Quotas de recherche avancés et paramètres d’utilisation

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Pour que le service reste performant et réactif, le service de recherche avancée définit différents quotas et paramètres d’utilisation (également appelés « limites de service »). Ces quotas et paramètres s’appliquent séparément aux requêtes qui s’exécutent manuellement et aux requêtes qui s’exécutent à l’aide de [règles de détection personnalisées.](custom-detection-rules.md) Les clients qui exécutent plusieurs requêtes régulièrement doivent tenir compte de ces limites et appliquer les meilleures [pratiques](advanced-hunting-best-practices.md) d’optimisation pour minimiser les perturbations.

Reportez-vous au tableau suivant pour comprendre les quotas et paramètres d’utilisation existants.

| Quota ou paramètre | Size | Cycle d’actualisation | Description |
|--|--|--|--|
| Plage de données | 30 jours | Chaque requête | Chaque requête peut rechercher des données depuis les 30 derniers jours. |
| Jeu de résultats | 10 000 lignes | Chaque requête | Chaque requête peut retourner jusqu’à 10 000 enregistrements. |
| Délai d’expiration | 10 minutes | Chaque requête | Chaque requête peut s’exécuter pendant 10 minutes. S’il ne se termine pas dans les 10 minutes, le service affiche une erreur.
| Ressources processeur | En fonction de la taille du client | Toutes les 15 minutes | Le [portail affiche une erreur](advanced-hunting-errors.md) chaque fois qu’une requête s’exécute et que le client a consommé plus de 10 % des ressources allouées. Les requêtes sont bloquées si le client a atteint 100 % jusqu’au terme du cycle de 15 minutes suivant. |

>[!NOTE] 
>Un ensemble distinct de quotas et de paramètres s’applique aux requêtes de recherche avancées effectuées via l’API. [En savoir plus sur les API de recherche avancée](./api-advanced-hunting.md)

## <a name="related-topics"></a>Rubriques connexes

- [Meilleures pratiques de recherche avancée](advanced-hunting-best-practices.md)
- [Gérer les erreurs de recherche avancée](advanced-hunting-errors.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)