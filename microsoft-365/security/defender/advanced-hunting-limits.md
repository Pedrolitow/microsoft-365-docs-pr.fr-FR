---
title: Quotas de chasse et paramètres d’utilisation avancés dans Microsoft 365 Defender
description: Comprendre les différents quotas et paramètres d’utilisation (limites de service) qui maintiennent le service de chasse avancé réactif
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, schéma, kusto, limite du processeur, limite de requête, ressources, résultats maximum, quota, paramètres, allocation
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
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.openlocfilehash: 479495a5d0026283622cc1c42db6ab0b730c3652
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68633568"
---
# <a name="advanced-hunting-quotas-and-usage-parameters"></a>Quotas de chasse avancés et paramètres d’utilisation

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Pour que le service reste performant et réactif, la chasse avancée définit différents quotas et paramètres d’utilisation (également appelés « limites de service »). Ces quotas et paramètres s’appliquent séparément aux requêtes exécutées manuellement et aux requêtes exécutées à l’aide de [règles de détection personnalisées](custom-detection-rules.md). Les clients qui exécutent régulièrement plusieurs requêtes doivent tenir compte de ces limites et [appliquer les meilleures pratiques d’optimisation](advanced-hunting-best-practices.md) pour réduire les interruptions.

Reportez-vous au tableau suivant pour comprendre les quotas et les paramètres d’utilisation existants.

| Quota ou paramètre | Size | Cycle d’actualisation | Description |
|--|--|--|--|
| Plage de données | 30 jours | Chaque requête | Chaque requête peut rechercher des données depuis les 30 derniers jours. |
| Jeu de résultats | 10 000 lignes | Chaque requête | Chaque requête peut retourner jusqu’à 10 000 enregistrements. |
| Délai d’expiration | 10 minutes | Chaque requête | Chaque requête peut s’exécuter pendant 10 minutes. S’il ne se termine pas dans les 10 minutes, le service affiche une erreur.
| Ressources processeur | En fonction de la taille du client | Toutes les 15 minutes | Le [portail affiche une erreur](advanced-hunting-errors.md) chaque fois qu’une requête s’exécute et que le locataire a consommé plus de 10 % des ressources allouées. Les requêtes sont bloquées si le client a atteint 100 % jusqu’au terme du cycle de 15 minutes suivant. |

>[!NOTE] 
>Un ensemble distinct de quotas et de paramètres s’applique aux requêtes de chasse avancées effectuées via l’API. [En savoir plus sur les API de chasse avancées](./api-advanced-hunting.md)

## <a name="related-topics"></a>Voir aussi

- [Meilleures pratiques de chasse avancées](advanced-hunting-best-practices.md)
- [Gérer les erreurs de repérage avancées](advanced-hunting-errors.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)