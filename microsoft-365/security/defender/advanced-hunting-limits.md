---
title: Quotas de recherche avancés et paramètres d’utilisation dans Microsoft 365 Defender
description: Comprendre les différents quotas et paramètres d’utilisation (limites de service) qui conservent la réactivité du service de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema, kusto, CPU limit, query limit, resources, maximum results, quota, parameters, allocation
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 19606b06ff1a1369614bab533a949bc383c90ad3
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064734"
---
# <a name="advanced-hunting-quotas-and-usage-parameters"></a>Quotas de recherche avancés et paramètres d’utilisation

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Pour que le service reste performant et réactif, le service de recherche avancée définit différents quotas et paramètres d’utilisation (également appelés « limites de service »). Ces quotas et paramètres s’appliquent aux requêtes qui s’exécutent manuellement et par des [règles de détection personnalisées.](custom-detection-rules.md) Les clients qui exécutent plusieurs requêtes régulièrement doivent suivre la consommation et appliquer les meilleures [pratiques](advanced-hunting-best-practices.md) d’optimisation pour minimiser les interruptions.

Reportez-vous au tableau suivant pour comprendre les quotas et paramètres d’utilisation existants.

| Quota ou paramètre | Size | Cycle d’actualisation | Description |
|--|--|--|--|
| Plage de données | 30 jours | Chaque requête | Chaque requête peut rechercher des données depuis les 30 derniers jours. |
| Jeu de résultats | 10 000 lignes | Chaque requête | Chaque requête peut renvoyer jusqu’à 10 000 enregistrements. |
| Timeout | 10 minutes | Chaque requête | Chaque requête peut s’exécuter pendant 10 minutes. S’il ne se termine pas dans les 10 minutes, le service affiche une erreur.
| Ressources processeur | En fonction de la taille du client | - À l’heure, puis toutes les 15 minutes<br>- Tous les jours à minuit | Le service applique le quota quotidien et le quota de 15 minutes séparément. Pour chaque quota, [le](advanced-hunting-errors.md) portail affiche une erreur chaque fois qu’une requête s’exécute et que le client a consommé plus de 10 % des ressources allouées. Les requêtes sont bloquées si le client a atteint 100 % jusqu’au terme du cycle quotidien suivant ou de 15 minutes. |

>[!NOTE] 
>Un ensemble distinct de quotas et de paramètres s’applique aux requêtes de recherche avancées effectuées via l’API. [En savoir plus sur les API de recherche avancée](./api-advanced-hunting.md)

## <a name="related-topics"></a>Voir aussi

- [Meilleures pratiques de recherche avancée](advanced-hunting-best-practices.md)
- [Gérer les erreurs de recherche avancée](advanced-hunting-errors.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)