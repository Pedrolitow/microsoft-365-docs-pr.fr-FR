---
title: Obtenir une formation expert sur la chasse avancée
description: Formation et conseils gratuits des experts de la chasse avancée
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, langue, formation, scénarios, de base à avancé, vidéos, étape par étape
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
ms.openlocfilehash: 23f35c087d55208f7251a6b921cfe7532616742a
ms.sourcegitcommit: 62a8c226422eac9c085cc886b4836b037f95ef6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "47840758"
---
# <a name="get-expert-training-on-advanced-hunting"></a>Obtenir une formation expert sur la chasse avancée

**S’applique à :**
- Protection Microsoft contre les menaces

Dynamisez vos connaissances de _la recherche avancée avec le suivi de l’adversaire_, une série de présentations techniques en ligne pour les nouveaux analystes de sécurité et les Hunters de menaces éprouvées. La série vous guide tout au long du processus de création de vos propres requêtes complexes. Commencez par la première vidéo sur Fundamentals ou accédez à des vidéos plus avancées qui répondent à votre niveau d’expérience.


| Titre | Description | Surveillance | Requêtes | 
|--|--|--|--|
| Épisode 1 : notions de base de KQL | Cet épisode couvre les notions de base de la chasse avancée dans la protection contre les menaces Microsoft. Découvrez les données de chasse avancées et les opérateurs et la syntaxe de KQL de base. | [YouTube](https://youtu.be/0D9TkGjeJwM?t=351) (54:14) | [Fichier CSL](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%201%20-%20KQL%20Fundamentals.csl) |
| Épisode 2 : jointures | Continuez à en savoir plus sur les données dans la chasse avancée et sur la façon de joindre des tables ensemble. Découvrez `inner` ,, `outer` `unique` et `semi` Joignez et comprenez les nuances de la jointure Kusto par défaut `innerunique` . | [YouTube](https://youtu.be/LMrO6K5TWOU?t=297) (53:33) | [Fichier CSL](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%202%20-%20Joins.csl) |
| Épisode 3 : résumé, glissement et visualisation des données | À présent que vous avez appris à filtrer, manipuler et joindre des données, il est temps de les résumer, de les quantifier, de les faire pivoter et de les visualiser. Cet épisode décrit l' `summarize` opérateur et différents calculs, tout en introduisant des tables supplémentaires dans le schéma. Vous apprendrez également à transformer des jeux de données en graphiques qui peuvent vous aider à extraire de l’aperçu. | [YouTube](https://youtu.be/UKnk9U1NH6Y?t=296) (48:52) | [Fichier CSL](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%203%20-%20Summarizing%2C%20Pivoting%2C%20and%20Joining.csl) |
| Épisode 4 : allons-nous ! Application de KQL au suivi des incidents | Dans cet épisode, vous apprendrez à effectuer le suivi de certaines activités d’agresseur. Nous utilisons notre compréhension améliorée de Kusto et de la recherche avancée pour suivre une attaque. Découvrez les astuces utilisées dans le domaine, y compris l’ABC de Cybersecurity et la façon de les appliquer à la réponse aux incidents. | [YouTube](https://youtu.be/2EUxOc_LNd8?t=291) (59:36) | [Fichier CSL](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%204%20-%20Lets%20Hunt.csl)

## <a name="how-to-use-the-csl-file"></a>Comment utiliser le fichier CSL
Avant de commencer un épisode, accédez au [fichier Kusto CSL correspondant sur GitHub](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/tree/master/Webcasts/TrackingTheAdversary) et copiez son contenu dans l’éditeur de requête de recherche avancée. À mesure que vous regardez un épisode, vous pouvez utiliser le contenu copié pour suivre le haut-parleur et exécuter des requêtes. 

L’extrait suivant d’un fichier CSL montre un ensemble complet de conseils marqués sous forme de commentaires avec `//` .

```kusto
// DeviceLogonEvents
// A table containing a row for each logon a device enrolled in Defender ATP
// Contains
// - Account information associated with the logon
// - The device which the account logged onto
// - The process which performed the logon
// - Network information (for network logons)
// - Timestamp
```

Le même fichier CSL inclut les requêtes avant et après les commentaires, comme indiqué ci-dessous. Pour exécuter une requête spécifique avec [plusieurs requêtes dans l’éditeur](advanced-hunting-query-language.md#work-with-multiple-queries-in-the-editor), déplacez le curseur sur cette requête et sélectionnez **exécuter la requête**.   

```kusto
DeviceLogonEvents
| count

// DeviceLogonEvents
// A table containing a row for each logon a device enrolled in Defender ATP
// Contains
// - Account information associated with the logon
// - The device which the account logged onto
// - The process which performed the logon
// - Network information (for network logons)
// - Timestamp

AppFileEvents
| take 100
| sort by Timestamp desc
```
     
## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Découvrir le langage de requête de repérage avancé](advanced-hunting-query-language.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les emails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)