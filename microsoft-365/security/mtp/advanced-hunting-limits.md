---
title: Quotas de chasse et paramètres d’utilisation avancés dans Microsoft 365 Defender
description: Comprendre les différents quotas et paramètres d’utilisation (limites de service) qui assurent la réactivité avancée du service de chasse
keywords: chasse aux menaces, recherche de menace, recherche de menace, protection contre les menaces Microsoft 365, MTP, M365, recherche, requête, télémétrie, schéma, Kusto, limite du processeur, limite de requête, ressources, résultats maximaux, quota, paramètres, allocation
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.openlocfilehash: bab63d9e5939f87f6a1edbf62d256b82552e4fe9
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48847367"
---
# <a name="advanced-hunting-quotas-and-usage-parameters"></a>Quotas de chasse et paramètres d’utilisation avancés

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Pour maintenir le service de manière efficace et réactive, la chasse avancée définit différents quotas et paramètres d’utilisation (également appelés « limites de service »). Ces quotas et paramètres s’appliquent aux requêtes exécutées manuellement et par les [règles de détection personnalisées](custom-detection-rules.md). Les clients qui exécutent régulièrement plusieurs requêtes doivent suivre la consommation et [appliquer les meilleures pratiques en matière d’optimisation](advanced-hunting-best-practices.md) afin de minimiser les interruptions.

Reportez-vous au tableau suivant pour comprendre les quotas et les paramètres d’utilisation existants.

| Quota ou paramètre | Size | Cycle d’actualisation | Description |
|--|--|--|--|
| Plage de données | 30 jours | Chaque requête | Chaque requête peut rechercher des données depuis au cours des 30 derniers jours. |
| Jeu de résultats | 10 000 lignes | Chaque requête | Chaque requête peut renvoyer jusqu’à 10 000 enregistrements. |
| Timeout | 10 minutes | Chaque requête | Chaque requête peut être exécutée pendant 10 minutes maximum. Si elle ne se termine pas dans les 10 minutes, le service affiche une erreur.
| Ressources du processeur | En fonction de la taille du client | -Sur l’heure, puis toutes les 15 minutes<br>-Tous les jours à 12 minuit | Le service applique le quota quotidien et 15 minutes séparément. Pour chaque quota, le [portail affiche une erreur](advanced-hunting-errors.md) chaque fois qu’une requête s’exécute et que le client a consommé plus de 10% des ressources allouées. Les requêtes sont bloquées si le client a atteint 100% jusqu’au prochain cycle quotidien ou 15 minutes. |

>[!NOTE] 
>Un ensemble distinct de quotas et de paramètres s’applique aux requêtes de chasse avancée effectuées via l’API. [En savoir plus sur les API de chasse avancées](https://docs.microsoft.com/microsoft-365/security/mtp/api-advanced-hunting)

## <a name="related-topics"></a>Voir aussi

- [Meilleures pratiques pour la chasse avancée](advanced-hunting-best-practices.md)
- [Gérer les erreurs de chasse avancées](advanced-hunting-errors.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)