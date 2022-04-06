---
title: Obtenir une formation d’expert sur la chasse avancée
description: Formation gratuite et conseils d’experts de chasse avancés
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, langue, formation, scénarios, de base à avancé, vidéos, étape par étape
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 2036f0b1e749250d42066fc5ea742c550a2f756e
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664103"
---
# <a name="get-expert-training-on-advanced-hunting"></a>Obtenir une formation d’expert sur la chasse avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

Améliorez rapidement vos connaissances de la chasse avancée avec _Tracking the adversary_, une série web destinée aux nouveaux analystes de sécurité et aux chasseurs de menaces expérimentés. La série vous guide tout au long des principes de base pour créer vos propres requêtes sophistiquées. Commencez par la première vidéo sur les principes de base ou accédez à des vidéos plus avancées qui correspondent à votre niveau d’expérience.

| Titre | Description | Regarder | Requêtes |
|---|---|---|---|
| Episode 1: KQL notions de base | Cet épisode aborde les principes de base de la chasse avancée dans Microsoft 365 Defender. Découvrez les données de chasse avancées disponibles et la syntaxe et les opérateurs KQL de base. | [YouTube](https://youtu.be/0D9TkGjeJwM?t=351) (54:14) | [Fichier texte](https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%201%20-%20KQL%20Fundamentals.txt) |
| Episode 2: Joins | Continuez à en savoir plus sur les données de repérage avancé et sur la façon de joindre des tables. En savoir plus sur `inner`, `outer`, `unique`et `semi` les jointures, et comprendre les nuances de la jointure par défaut Kusto`innerunique`. | [YouTube](https://youtu.be/LMrO6K5TWOU?t=297) (53:33) | [Fichier texte](https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%202%20-%20Joins.txt) |
| Épisode 3 : Résumé, tableau croisé dynamique et visualisation des données | Maintenant que vous avez appris à filtrer, manipuler et joindre des données, il est temps de synthétiser, quantifier, pivoter et visualiser. Cet épisode décrit l’opérateur `summarize` et les différents calculs, tout en introduisant des tables supplémentaires dans le schéma. Vous allez également apprendre à transformer des jeux de données en graphiques qui peuvent vous aider à extraire des insights. | [YouTube](https://youtu.be/UKnk9U1NH6Y?t=296) (48:52) | [Fichier texte](https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%203%20-%20Summarizing%2C%20Pivoting%2C%20and%20Joining.txt) |
| Episode 4: Nous allons chasser! Application de KQL au suivi des incidents | Dans cet épisode, vous allez apprendre à suivre certaines activités des attaquants. Nous utilisons notre meilleure compréhension des Kusto et de la chasse avancée pour suivre une attaque. Découvrez les astuces réelles utilisées dans le domaine, y compris les AAC de la cybersécurité et comment les appliquer à la réponse aux incidents. | [YouTube](https://youtu.be/2EUxOc_LNd8?t=291) (59:36) | [Fichier texte](https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%204%20-%20Lets%20Hunt.txt)

Obtenez une formation plus experte avec *L33TSP3AK : Repérage avancé dans Microsoft 365 Defender*, une série de diffusion web destinée aux analystes qui cherchent à développer leurs connaissances techniques et leurs compétences pratiques dans la conduite d’enquêtes de sécurité à l’aide de la chasse avancée dans Microsoft 365 Defender.

| Titre | Description | Regarder | Requêtes |
|---|---|---|---|
| Épisode 1  | Dans cet épisode, vous allez découvrir différentes meilleures pratiques pour exécuter des requêtes de chasse avancées. Parmi les sujets abordés, citons la façon d’optimiser vos requêtes, d’utiliser la chasse avancée pour les ransomware, de gérer JSON en tant que type dynamique et d’utiliser des opérateurs de données externes. | [YouTube](https://www.youtube.com/watch?v=nMGbK-ALaVg&feature=youtu.be) (56:34) | [Fichier texte](https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries/blob/master/Webcasts/l33tSpeak/Performance%2C%20Json%20and%20dynamics%20operator%2C%20external%20data.txt) |
| Épisode 2 | Dans cet épisode, vous allez apprendre à examiner et à répondre aux emplacements d’ouverture de session suspects ou inhabituels et à l’exfiltration de données via des règles de transfert de boîte de réception. Sébastien Molendijk, responsable de programme principal pour Cloud Security CxE, explique comment utiliser la chasse avancée pour examiner les incidents à plusieurs étapes avec des données Microsoft Defender for Cloud Apps. | [YouTube](https://www.youtube.com/watch?v=QaUxdtNfbd8) (57:07) | [Fichier texte](https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries/blob/master/Webcasts/l33tSpeak/MCAS%20-%20The%20Hunt.txt)
| Épisode 3 | Dans cet épisode, nous allons aborder les dernières améliorations apportées à la chasse avancée, comment importer une source de données externe dans votre requête et comment utiliser le partitionnement pour segmenter les résultats de requête volumineux en jeux de résultats plus petits afin d’éviter d’atteindre les limites d’API. | [YouTube](https://www.youtube.com/watch?v=vd5lgIJKmYs) (40:59) | [Fichier texte](https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries/blob/master/Webcasts/l33tSpeak/l33tspeak%2011%20Oct%202021%20-%20externaldata%20and%20query%20partitioning.csl)

## <a name="how-to-use-the-csl-file"></a>Utilisation du fichier CSL

Avant de commencer un épisode, accédez au [fichier texte correspondant sur GitHub](https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries/tree/master/Webcasts) et copiez son contenu dans l’éditeur de requête de chasse avancé. Lorsque vous regardez un épisode, vous pouvez utiliser le contenu copié pour suivre l’orateur et exécuter des requêtes.

L’extrait suivant d’un fichier texte contenant les requêtes montre un ensemble complet de conseils marqués comme des commentaires avec `//`.

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

Le même fichier texte inclut des requêtes avant et après les commentaires, comme indiqué ci-dessous. Pour exécuter une requête spécifique avec [plusieurs requêtes dans l’éditeur](advanced-hunting-query-language.md#work-with-multiple-queries-in-the-editor), déplacez le curseur vers cette requête et sélectionnez **Exécuter la requête**.

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

CloudAppEvents
| take 100
| sort by Timestamp desc
```

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Découvrir le langage de requête de repérage avancé](advanced-hunting-query-language.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
