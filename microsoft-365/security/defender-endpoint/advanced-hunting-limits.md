---
title: Limites de recherche avancées dans Microsoft Defender ATP
description: Comprendre les différentes limites de service qui conservent la réactivité du service de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, mdatp, microsoft defender atp, wdatp, search, query, telemetry, schema, kusto, CPU limit, query limit, resources, maximum results
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8a9279d1dd2a6465553b576609bb81cdf4e03fa0
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51499528"
---
# <a name="advanced-hunting-service-limits"></a>Limites du service de recherche avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedhunting-abovefoldlink)

Pour que le service reste performant et réactif, le repérage avancé définit différentes limites pour les requêtes qui s’exécutent manuellement et par des [règles de détection personnalisées.](custom-detection-rules.md) Reportez-vous au tableau suivant pour comprendre ces limites.

| Limite | Size | Cycle d’actualisation | Description |
|--|--|--|--|
| Plage de données | 30 jours | Chaque requête | Chaque requête peut rechercher des données depuis les 30 derniers jours. |
| Jeu de résultats | 10 000 lignes | Chaque requête | Chaque requête peut renvoyer jusqu’à 10 000 enregistrements. |
| Timeout | 10 minutes | Chaque requête | Chaque requête peut s’exécuter pendant 10 minutes. S’il ne se termine pas dans les 10 minutes, le service affiche une erreur.
| Ressources processeur | En fonction de la taille du client | - À l’heure, puis toutes les 15 minutes<br>- Tous les jours à minuit | Le service applique séparément les limites quotidiennes et de 15 minutes. Pour chaque limite, [le](advanced-hunting-errors.md) portail affiche une erreur chaque fois qu’une requête s’exécute et que le client a consommé plus de 10 % des ressources allouées. Les requêtes sont bloquées si le client a atteint 100 % jusqu’au prochain cycle quotidien ou de 15 minutes. |

>[!NOTE] 
>Un ensemble distinct de limites s’applique aux requêtes de recherche avancées effectuées via l’API. [En savoir plus sur les API de recherche avancée](run-advanced-query-api.md)

Les clients qui exécutent plusieurs [](advanced-hunting-best-practices.md) requêtes régulièrement doivent suivre la consommation et appliquer les meilleures pratiques d’optimisation afin de minimiser les perturbations résultant du dépassement de ces limites.

## <a name="related-topics"></a>Voir aussi

- [Meilleures pratiques de recherche avancée](advanced-hunting-best-practices.md)
- [Gérer les erreurs de recherche avancée](advanced-hunting-errors.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Règles de détection personnalisées](custom-detection-rules.md)
