---
title: Obtenir une formation spécialisée sur le chasse avancée
description: Formation gratuite et conseils d’experts de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, language, training, scenarios, basic to advanced, videos, step-by-step
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
ms.openlocfilehash: df96b57b9898dd973fab053918d763d1972bd50d
ms.sourcegitcommit: ef98b8a18d275e5b5961e63d2b0743d046321737
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2021
ms.locfileid: "51382804"
---
# <a name="get-expert-training-on-advanced-hunting"></a>Obtenir une formation spécialisée sur le chasse avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Améliorez rapidement vos connaissances en matière de repérage avancé avec le suivi _de_ l’adversaire, une série de webcasts pour les nouveaux analystes de sécurité et les observateurs de menaces. La série vous guide tout au long des principes de base pour créer vos propres requêtes sophistiquées. Commencez par la première vidéo sur les principes de base ou découvrez des vidéos plus avancées qui conviennent à votre niveau d’expérience.

| Titre | Description | Surveillance | Requêtes | 
|--|--|--|--|
| Épisode 1 : Principes de base du langage KQL | Cet épisode aborde les principes de base du recherche avancée dans Microsoft 365 Defender. Découvrez les données de recherche avancées disponibles, ainsi que la syntaxe et les opérateurs KQL de base. | [YouTube](https://youtu.be/0D9TkGjeJwM?t=351) (54:14) | [Fichier CSL](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%201%20-%20KQL%20Fundamentals.csl) |
| Épisode 2 : Joints | Poursuivez l’apprentissage sur les données dans le recherche avancée et sur la façon de joindre des tables. En savoir plus sur , et joint, et comprendre les nuances de la jointe `inner` `outer` `unique` `semi` Kusto par `innerunique` défaut. | [YouTube](https://youtu.be/LMrO6K5TWOU?t=297) (53:33) | [Fichier CSL](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%202%20-%20Joins.csl) |
| Épisode 3 : Synthèse, pivotation et visualisation des données | Maintenant que vous avez appris à filtrer, manipuler et joindre des données, il est temps de synthétiser, quantifier, pivoter et visualiser. Cet épisode décrit l’opérateur et divers calculs, tout en introduisant des `summarize` tableaux supplémentaires dans le schéma. Vous allez également apprendre à transformer les jeux de données en graphiques qui peuvent vous aider à extraire des informations. | [YouTube](https://youtu.be/UKnk9U1NH6Y?t=296) (48:52) | [Fichier CSL](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%203%20-%20Summarizing%2C%20Pivoting%2C%20and%20Joining.csl) |
| Épisode 4 : Nous allons faire la recherche ! Application de KQL au suivi des incidents | Dans cet épisode, vous allez apprendre à suivre certaines activités de l’attaquant. Nous utilisons notre compréhension améliorée de Kusto et la recherche avancée pour suivre une attaque. Découvrez les astuces réelles utilisées dans le champ, y compris les stratégies de sécurité en cas de cyber-sécurité et comment les appliquer à la réponse aux incidents. | [YouTube](https://youtu.be/2EUxOc_LNd8?t=291) (59:36) | [Fichier CSL](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%204%20-%20Lets%20Hunt.csl) 


Obtenez une formation plus spécialisée avec *L33TSP3AK*: recherche avancée dans Microsoft 365 Defender , série de présentations en ligne pour les analystes qui cherchent à développer leurs connaissances techniques et leurs compétences pratiques dans la conduite d’enquêtes de sécurité à l’aide de la recherche avancée dans Microsoft 365 Defender. 

| Titre | Description | Surveillance | Requêtes | 
|--|--|--|--|
| Épisode 1  | Dans cet épisode, vous découvrirez différentes meilleures pratiques en matière d’exécution de requêtes de recherche avancées. Parmi les rubriques traitées figurent : comment optimiser vos requêtes, utiliser la recherche avancée pour les ransomware, gérer JSON en tant que type dynamique et travailler avec des opérateurs de données externes. | [YouTube](https://www.youtube.com/watch?v=nMGbK-ALaVg&feature=youtu.be) (56:34) | [Fichier CSL](https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries/blob/master/Webcasts/l33tSpeak/Performance%2C%20Json%20and%20dynamics%20operator%2C%20external%20data.csl)


## <a name="how-to-use-the-csl-file"></a>Utilisation du fichier CSL
Avant de commencer un épisode, accédez au fichier [CSL Kusto](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/tree/master/Webcasts/TrackingTheAdversary) correspondant sur GitHub et copiez son contenu dans l’éditeur de requête de recherche avancée. Lorsque vous regardez un épisode, vous pouvez utiliser le contenu copié pour suivre le haut-parleur et exécuter des requêtes. 

L’extrait suivant d’un fichier CSL présente un ensemble complet de conseils marqués comme commentaires avec `//` .

```kusto
// DeviceLogonEvents
// A table containing a row for each logon a device enrolled in Microsoft Defender for Endpoint
// Contains
// - Account information associated with the logon
// - The device which the account logged onto
// - The process which performed the logon
// - Network information (for network logons)
// - Timestamp
```

Le même fichier CSL inclut des requêtes avant et après les commentaires, comme illustré ci-dessous. Pour exécuter une requête [](advanced-hunting-query-language.md#work-with-multiple-queries-in-the-editor)spécifique avec plusieurs requêtes dans l’éditeur, déplacez le curseur vers cette requête et sélectionnez **Exécuter la requête.**   

```kusto
DeviceLogonEvents
| count

// DeviceLogonEvents
// A table containing a row for each logon a device enrolled in Microsoft Defender for Endpoint
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
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
