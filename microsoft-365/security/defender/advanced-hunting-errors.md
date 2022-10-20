---
title: Gérer les erreurs de repérage avancé pour Microsoft 365 Defender
description: Comprendre les erreurs affichées lors de l’utilisation de la chasse avancée
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, schéma, kusto, délai d’expiration, ressources, erreurs, erreurs inconnues, limites, quota, paramètre, allocation
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
ms.openlocfilehash: 66bce3514890b579668c6f8104b38b54c95adfb0
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68631499"
---
# <a name="handle-advanced-hunting-errors"></a>Gérer les erreurs de repérage avancées

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison


La chasse avancée affiche les erreurs à signaler pour les erreurs de syntaxe et chaque fois que les requêtes atteignent [des quotas et des paramètres d’utilisation prédéfinis](advanced-hunting-limits.md). Reportez-vous au tableau ci-dessous pour obtenir des conseils sur la façon de résoudre ou d’éviter les erreurs.

| Type d’erreur | Cause | Résolution | Exemples de messages d’erreur |
|--|--|--|--|
| Erreurs de syntaxe | La requête contient des noms non reconnus, y compris des références à des opérateurs, des colonnes, des fonctions ou des tableaux inexistants. | Vérifiez que les références aux [opérateurs et aux fonctions Kusto](/azure/data-explorer/kusto/query/) sont correctes. Vérifiez [le schéma](advanced-hunting-schema-tables.md) pour les colonnes, fonctions et tables de chasse avancées correctes. Placez les chaînes variables entre guillemets afin qu’elles soient reconnues. Lors de l’écriture de vos requêtes, utilisez les suggestions de la mise à IntelliSense. | `A recognition error occurred.` |
| Erreurs sémantiques | Bien que la requête utilise des noms d’opérateur, de colonne, de fonction ou de table valides, il existe des erreurs dans sa structure et sa logique résultante. Dans certains cas, le repérage avancé identifie l’opérateur spécifique à l’origine de l’erreur. | Recherchez les erreurs dans la structure de la requête. Reportez-vous à la [documentation kusto](/azure/data-explorer/kusto/query/) pour obtenir des conseils. Lors de l’écriture de vos requêtes, utilisez les suggestions de la mise à IntelliSense. |  `'project' operator: Failed to resolve scalar expression named 'x'`|
| Délais d’expiration | Une requête ne peut s’exécuter qu’au cours d’une [période limitée avant expiration du délai d’attente](advanced-hunting-limits.md). Cette erreur peut se produire plus fréquemment lors de l’exécution de requêtes complexes. | [Optimiser la requête](advanced-hunting-best-practices.md) | `Query exceeded the timeout period.` |
| Limitation du processeur | Les requêtes dans le même locataire ont dépassé les [ressources UC](advanced-hunting-limits.md) qui ont été allouées en fonction de la taille du locataire. | Le service vérifie l’utilisation quotidienne des ressources du processeur toutes les 15 minutes et affiche des avertissements lorsque l’utilisation dépasse 10 % du quota alloué. Si vous atteignez une utilisation de 100 %, le service bloque les requêtes jusqu’au prochain cycle routinier ou de 15 minutes. [Optimiser vos requêtes pour éviter d’atteindre les quotas d’UC](advanced-hunting-best-practices.md) | - `This query used X% of your organization's allocated resources for the current 15 minutes.`<br>- `You have exceeded processing resources allocated to this tenant. You can run queries again in <duration>.` |
| Limite de taille de résultat dépassée  | La taille agrégée du jeu de résultats pour la requête a dépassé la taille maximale. Cette erreur peut se produire si le jeu de résultats est si grand que la limite de troncation à 10 000 enregistrements ne peut pas être réduit à une taille acceptable. Les résultats qui ont plusieurs colonnes avec un contenu important sont plus susceptibles d’être touchés par cette erreur. | [Optimiser la requête](advanced-hunting-best-practices.md) | `Result size limit exceeded. Use "summarize" to aggregate results, "project" to drop uninteresting columns, or "take" to truncate results.` |
| Consommation excessive de ressources | La requête a consommé des quantités excessives de ressources et a été arrêtée. Dans certains cas, le repérage avancé identifie l’opérateur spécifique qui n’a pas été optimisé. | [Optimiser la requête](advanced-hunting-best-practices.md) | -`Query stopped due to excessive resource consumption.`<br>-`Query stopped. Adjust use of the <operator name> operator to avoid excessive resource consumption.` |
| Erreurs inconnues | La requête a échoué pour une raison inconnue. | Réessayez d’exécuter la requête. Contactez Microsoft via le portail si les requêtes continuent de renvoyer des erreurs inconnues. | `An unexpected error occurred during query execution. Please try again in a few minutes.`



## <a name="related-topics"></a>Voir aussi
- [Meilleures pratiques de chasse avancées](advanced-hunting-best-practices.md)
- [Paramètres d’utilisation et de quotas](advanced-hunting-limits.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Langage de requête Kusto vue d’ensemble](/azure/data-explorer/kusto/query/)