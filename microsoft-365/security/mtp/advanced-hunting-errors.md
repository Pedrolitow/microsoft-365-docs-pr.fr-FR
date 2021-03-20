---
title: Gérer les erreurs de recherche avancée pour Microsoft 365 Defender
description: Comprendre les erreurs affichées lors de l’utilisation du chasse avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema, kusto, timeout, resources, errors, unknown error, limits, quota, parameter, allocation
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 23123b2ee96e1aa2b20499e66a180ba65832ba40
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50917115"
---
# <a name="handle-advanced-hunting-errors"></a>Gérer les erreurs de recherche avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


Le recherche avancée affiche des erreurs pour signaler les erreurs de syntaxe et chaque fois que les requêtes touchent des quotas et des [paramètres d’utilisation prédéfinies.](advanced-hunting-limits.md) Reportez-vous au tableau ci-dessous pour obtenir des conseils sur la façon de résoudre ou d’éviter les erreurs.

| Type d’erreur | Cause | Résolution | Exemples de messages d’erreur |
|--|--|--|--|
| Erreurs de syntaxe | La requête contient des noms non reconnus, y compris des références à des opérateurs, des colonnes, des fonctions ou des tableaux inexistants. | Assurez-vous que les [références aux opérateurs et fonctions Kusto sont correctes.](/azure/data-explorer/kusto/query/) Vérifiez [le schéma pour les](advanced-hunting-schema-tables.md) colonnes, fonctions et tableaux de recherche avancés corrects. Insérablez des chaînes variables entre guillemets afin qu’elles soient reconnues. Lors de l’écriture de vos requêtes, utilisez les suggestions de mise en IntelliSense. | `A recognition error occurred.` |
| Erreurs sémantiques | Bien que la requête utilise des noms d’opérateur, de colonne, de fonction ou de table valides, il existe des erreurs dans sa structure et sa logique résultante. Dans certains cas, le hunting avancé identifie l’opérateur spécifique à l’origine de l’erreur. | Recherchez les erreurs dans la structure de la requête. Reportez-vous [à la documentation Kusto pour](/azure/data-explorer/kusto/query/) obtenir des conseils. Lors de l’écriture de vos requêtes, utilisez les suggestions de mise en IntelliSense. |  `'project' operator: Failed to resolve scalar expression named 'x'`|
| Timeouts | Une requête peut uniquement s’exécuter dans un délai [limité avant la date d’attente.](advanced-hunting-limits.md) Cette erreur peut se produire plus fréquemment lors de l’exécution de requêtes complexes. | [Optimiser la requête](advanced-hunting-best-practices.md) | `Query exceeded the timeout period.` |
| Limitation du processeur | Les requêtes dans le même client ont dépassé les ressources [processeur](advanced-hunting-limits.md) qui ont été allouées en fonction de la taille du client. | Le service vérifie l’utilisation quotidienne des ressources du processeur toutes les 15 minutes et affiche des avertissements lorsque l’utilisation dépasse 10 % du quota alloué. Si vous atteignez une utilisation de 100 %, le service bloque les requêtes jusqu’au prochain cycle quotidien ou de 15 minutes. [Optimiser vos requêtes pour éviter d’atteindre les quotas de processeur](advanced-hunting-best-practices.md) | - `This query used X% of your organization's allocated resources for the current 15 minutes.`<br>- `You have exceeded processing resources allocated to this tenant. You can run queries again in <duration>.` |
| Limite de taille de résultat dépassée  | La taille agrégée du jeu de résultats pour la requête a dépassé la taille maximale. Cette erreur peut se produire si le jeu de résultats est si grand que la troncation à 10 000 enregistrement limite ne peut pas la réduire à une taille acceptable. Les résultats qui ont plusieurs colonnes avec un contenu important sont plus susceptibles d’être touchés par cette erreur. | [Optimiser la requête](advanced-hunting-best-practices.md) | `Result size limit exceeded. Use "summarize" to aggregate results, "project" to drop uninteresting columns, or "take" to truncate results.` |
| Consommation excessive de ressources | La requête a consommé des quantités excessives de ressources et a été arrêtée de se terminer. Dans certains cas, le hunting avancé identifie l’opérateur spécifique qui n’a pas été optimisé. | [Optimiser la requête](advanced-hunting-best-practices.md) | -`Query stopped due to excessive resource consumption.`<br>-`Query stopped. Adjust use of the <operator name> operator to avoid excessive resource consumption.` |
| Erreurs inconnues | La requête a échoué pour une raison inconnue. | Recommencez l’exécution de la requête. Contactez Microsoft via le portail si les requêtes continuent à renvoyer des erreurs inconnues. | `An unexpected error occurred during query execution. Please try again in a few minutes.`

## <a name="related-topics"></a>Rubriques connexes
- [Meilleures pratiques de recherche avancée](advanced-hunting-best-practices.md)
- [Paramètres d’utilisation et de quotas](advanced-hunting-limits.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Vue d’ensemble du langage de requête Kusto](/azure/data-explorer/kusto/query/)