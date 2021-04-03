---
title: Gérer les erreurs de recherche avancée pour Microsoft Defender ATP
description: Comprendre les erreurs affichées lors de l’utilisation du chasse avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, mdatp, microsoft defender atp, wdatp, m365, search, query, telemetry, schema, kusto, timeout, resources, errors, unknown error
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
ms.openlocfilehash: b27ef34d465832bdf0eee3841385d64158553a6c
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51500199"
---
# <a name="handle-advanced-hunting-errors"></a>Gérer les erreurs de recherche avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)


>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedhunting-abovefoldlink)

Le recherche avancée affiche des erreurs pour signaler les erreurs de syntaxe et chaque fois que les requêtes touchent [des limites prédéfinies.](advanced-hunting-limits.md) Reportez-vous au tableau ci-dessous pour obtenir des conseils sur la façon de résoudre ou d’éviter les erreurs. 

| Type d’erreur | Cause | Résolution | Exemples de messages d’erreur |
|--|--|--|--|
| Erreurs de syntaxe | La requête contient des noms non reconnus, y compris des références à des opérateurs, des colonnes, des fonctions ou des tableaux inexistants. | Assurez-vous que les [références aux opérateurs et fonctions Kusto sont correctes.](https://docs.microsoft.com/azure/data-explorer/kusto/query/) Vérifiez [le schéma pour les](advanced-hunting-schema-reference.md) colonnes, fonctions et tableaux de recherche avancés corrects. Insérablez des chaînes variables entre guillemets afin qu’elles soient reconnues. Lors de l’écriture de vos requêtes, utilisez les suggestions de la mise à IntelliSense. | `A recognition error occurred.` |
| Erreurs sémantiques | Bien que la requête utilise des noms d’opérateur, de colonne, de fonction ou de table valides, il existe des erreurs dans sa structure et sa logique résultante. Dans certains cas, le hunting avancé identifie l’opérateur spécifique à l’origine de l’erreur. | Recherchez les erreurs dans la structure de la requête. Reportez-vous [à la documentation Kusto pour](https://docs.microsoft.com/azure/data-explorer/kusto/query/) obtenir des conseils. Lors de l’écriture de vos requêtes, utilisez les suggestions de la mise à IntelliSense. |  `'project' operator: Failed to resolve scalar expression named 'x'`|
| Timeouts | Une requête peut uniquement s’exécuter dans un délai [limité avant la date d’attente.](advanced-hunting-limits.md) Cette erreur peut se produire plus fréquemment lors de l’exécution de requêtes complexes. | [Optimiser la requête](advanced-hunting-best-practices.md) | `Query exceeded the timeout period.` |
| Limitation du processeur | Les requêtes dans le même client ont dépassé les ressources [processeur](advanced-hunting-limits.md) qui ont été allouées en fonction de la taille du client. | Le service vérifie l’utilisation quotidienne des ressources du processeur toutes les 15 minutes et affiche des avertissements lorsque l’utilisation dépasse 10 % de la limite allouée. Si vous atteignez une utilisation de 100 %, le service bloque les requêtes jusqu’au prochain cycle quotidien ou de 15 minutes. [Optimiser vos requêtes pour éviter d’atteindre les limites de processeur](advanced-hunting-best-practices.md) | - `This query used X% of your organization's allocated resources for the current 15 minutes.`<br>- `You have exceeded processing resources allocated to this tenant. You can run queries again in <duration>.` |
| Limite de taille de résultat dépassée  | La taille agrégée du jeu de résultats pour la requête a dépassé la limite maximale. Cette erreur peut se produire si le jeu de résultats est si grand que la troncation à 10 000 enregistrement limite ne peut pas la réduire à une taille acceptable. Les résultats qui ont plusieurs colonnes avec un contenu important sont plus susceptibles d’être touchés par cette erreur. | [Optimiser la requête](advanced-hunting-best-practices.md) | `Result size limit exceeded. Use "summarize" to aggregate results, "project" to drop uninteresting columns, or "take" to truncate results.` |
| Consommation excessive de ressources | La requête a consommé des quantités excessives de ressources et a été arrêtée de se terminer. Dans certains cas, le hunting avancé identifie l’opérateur spécifique qui n’a pas été optimisé. | [Optimiser la requête](advanced-hunting-best-practices.md) | -`Query stopped due to excessive resource consumption.`<br>-`Query stopped. Adjust use of the <operator name> operator to avoid excessive resource consumption.` |
| Erreurs inconnues | La requête a échoué pour une raison inconnue. | Recommencez l’exécution de la requête. Contactez Microsoft via le portail si les requêtes continuent de renvoyer des erreurs inconnues. | `An unexpected error occurred during query execution. Please try again in a few minutes.`

## <a name="related-topics"></a>Voir aussi
- [Meilleures pratiques de recherche avancée](advanced-hunting-best-practices.md)
- [Limites de service](advanced-hunting-limits.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
- [Vue d’ensemble du langage de requête Kusto](https://docs.microsoft.com/azure/data-explorer/kusto/query/)