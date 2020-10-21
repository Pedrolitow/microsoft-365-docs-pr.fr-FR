---
title: Gérer les erreurs de la chasse avancée pour la protection contre les menaces Microsoft
description: Comprendre les erreurs affichées lors de l’utilisation de la chasse avancée
keywords: chasse aux menaces, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, schéma, Kusto, délai d’attente, ressources, erreurs, erreur inconnue, limites, quota, paramètre, allocation
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
ms.openlocfilehash: 8b9c46e312d28c7a08efbfa74f96dc33b90fee0a
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48636892"
---
# <a name="handle-advanced-hunting-errors"></a>Gérer les erreurs de chasse avancées

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


La chasse avancée affiche les erreurs pour signaler les erreurs de syntaxe et chaque fois que les requêtes ont des [quotas prédéfinis et des paramètres d’utilisation](advanced-hunting-limits.md). Reportez-vous au tableau ci-dessous pour obtenir des conseils sur la façon de résoudre ou d’éviter des erreurs.

| Type d’erreur | Cause | Résolution | Exemples de messages d’erreur |
|--|--|--|--|
| Erreurs de syntaxe | La requête contient des noms non reconnus, y compris des références à des opérateurs, des colonnes, des fonctions ou des tables inexistants. | Assurez-vous que les références aux [opérateurs et fonctions Kusto](https://docs.microsoft.com/azure/data-explorer/kusto/query/) sont correctes. Vérifiez [le schéma](advanced-hunting-schema-tables.md) pour les colonnes, fonctions et tableaux de recherche avancée corrects. Placez les chaînes variables entre guillemets afin qu’elles soient reconnues. Lors de l’écriture de vos requêtes, utilisez les suggestions de saisie semi-automatique d’IntelliSense. | `A recognition error occurred.` |
| Erreurs sémantiques | Bien que la requête utilise des noms de table, de colonne, de fonction ou de table valides, sa structure et sa logique résultante contiennent des erreurs. Dans certains cas, la chasse avancée identifie l’opérateur spécifique à l’origine de l’erreur. | Recherchez les erreurs dans la structure de la requête. Reportez-vous à [la documentation Kusto](https://docs.microsoft.com/azure/data-explorer/kusto/query/) pour obtenir des instructions. Lors de l’écriture de vos requêtes, utilisez les suggestions de saisie semi-automatique d’IntelliSense. |  `'project' operator: Failed to resolve scalar expression named 'x'`|
| Délais | Une requête ne peut être exécutée qu’au cours d’une [période limitée avant](advanced-hunting-limits.md)le dépassement du délai d’expiration. Cette erreur peut se produire plus fréquemment lors de l’exécution de requêtes complexes. | [Optimiser la requête](advanced-hunting-best-practices.md) | `Query exceeded the timeout period.` |
| Limitation de l’UC | Les requêtes dans le même client ont dépassé les [ressources processeur](advanced-hunting-limits.md) allouées en fonction de la taille du client. | Le service vérifie l’utilisation des ressources de l’UC toutes les 15 minutes et tous les jours et affiche des avertissements une fois l’utilisation dépassant 10% du quota alloué. Si vous atteignez 100% d’utilisation, le service bloque les requêtes jusqu’au prochain cycle quotidien ou 15 minutes. [Optimiser vos requêtes afin d’éviter de heurter les quotas d’UC](advanced-hunting-best-practices.md) | - `This query used X% of your organization's allocated resources for the current 15 minutes.`<br>- `You have exceeded processing resources allocated to this tenant. You can run queries again in <duration>.` |
| Limite de taille des résultats dépassée  | La taille d’agrégation du jeu de résultats pour la requête a dépassé la taille maximale. Cette erreur peut se produire si le jeu de résultats est si important que la troncation au niveau de la limite de 10 000 enregistrements ne permet pas de le réduire à une taille acceptable. Les résultats qui comportent plusieurs colonnes avec un contenu dimensionnable sont plus susceptibles d’être affectés par cette erreur. | [Optimiser la requête](advanced-hunting-best-practices.md) | `Result size limit exceeded. Use "summarize" to aggregate results, "project" to drop uninteresting columns, or "take" to truncate results.` |
| Consommation excessive de ressources | La requête a consommé une quantité excessive de ressources et a été interrompue. Dans certains cas, la chasse avancée identifie l’opérateur spécifique qui n’a pas été optimisé. | [Optimiser la requête](advanced-hunting-best-practices.md) | -`Query stopped due to excessive resource consumption.`<br>-`Query stopped. Adjust use of the <operator name> operator to avoid excessive resource consumption.` |
| Erreurs inconnues | La requête a échoué en raison d’une raison inconnue. | Essayez de réexécuter la requête. Contactez Microsoft via le portail si les requêtes continuent à renvoyer des erreurs inconnues. | `An unexpected error occurred during query execution. Please try again in a few minutes.`

## <a name="related-topics"></a>Voir aussi
- [Meilleures pratiques pour la chasse avancée](advanced-hunting-best-practices.md)
- [Quotas et paramètres d’utilisation](advanced-hunting-limits.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Vue d’ensemble du langage de requête Kusto](https://docs.microsoft.com/azure/data-explorer/kusto/query/)
