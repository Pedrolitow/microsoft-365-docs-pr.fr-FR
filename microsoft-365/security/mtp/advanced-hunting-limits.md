---
title: Limites de chasse avancée dans la protection contre les menaces Microsoft
description: Comprendre les différentes limites de service qui maintiennent le service de chasse dynamique
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, schéma, Kusto, limite d’UC, limite de requête, ressources, résultats maximaux
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
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: e3fbe29076d541df68dc39754960386fe935c7bc
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47950923"
---
# <a name="advanced-hunting-service-limits"></a>Limites de service de la chasse avancée

**S’applique à :**
- Protection Microsoft contre les menaces

Pour maintenir le service de façon efficace et réactive, la chasse avancée définit différentes limites pour les requêtes exécutées manuellement et par les [règles de détection personnalisées](custom-detection-rules.md). Reportez-vous au tableau suivant pour comprendre ces limites.

| Limite | Size | Cycle d’actualisation | Description |
|--|--|--|--|
| Plage de données | 30 jours | Chaque requête | Chaque requête peut rechercher des données depuis au cours des 30 derniers jours. |
| Jeu de résultats | 10 000 lignes | Chaque requête | Chaque requête peut renvoyer jusqu’à 10 000 enregistrements. |
| Timeout | 10 minutes | Chaque requête | Chaque requête peut être exécutée pendant 10 minutes maximum. Si elle ne se termine pas dans les 10 minutes, le service affiche une erreur.
| Ressources du processeur | En fonction de la taille du client | -Sur l’heure, puis toutes les 15 minutes<br>-Tous les jours à 12 minuit | Le service applique la limite quotidienne et la limite de 15 minutes séparément. Pour chaque limite, le [portail affiche une erreur](advanced-hunting-errors.md) chaque fois qu’une requête s’exécute et que le client a consommé plus de 10% des ressources allouées. Les requêtes sont bloquées si le client a atteint 100% jusqu’au prochain cycle quotidien ou 15 minutes. |

>[!NOTE] 
>Un ensemble distinct de limites s’applique aux requêtes de chasse avancée effectuées via l’API. [En savoir plus sur les API de chasse avancées](https://docs.microsoft.com/microsoft-365/security/mtp/api-advanced-hunting)

Les clients qui exécutent régulièrement plusieurs requêtes doivent suivre la consommation et [appliquer les meilleures pratiques en matière d’optimisation](advanced-hunting-best-practices.md) afin de minimiser la perturbation résultant du dépassement de ces limites.

## <a name="related-topics"></a>Voir aussi

- [Meilleures pratiques pour la chasse avancée](advanced-hunting-best-practices.md)
- [Gérer les erreurs de chasse avancées](advanced-hunting-errors.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)
