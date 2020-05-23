---
title: Vue d’ensemble-chasse avancée
description: En savoir plus sur les requêtes de repérage avancés dans Microsoft 365 et leur utilisation pour rechercher de manière proactive les menaces et faiblesses de votre réseau
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, détections personnalisées, schéma, Kusto, Microsoft 365, protection contre les menaces Microsoft
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
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3e8f83b943e83c37ecf13af1221c043d413bd6b5
ms.sourcegitcommit: 8d9509e617ede7cc5ba933c54fb9300d2d1c6344
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "44347830"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-threat-protection"></a>Repérage proactive de menaces avec repérage avancé dans la Protection Microsoft contre les menaces

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le repérage avancé est un outil de repérage de menaces basé sur des requêtes qui vous permet d’explorer jusqu’à 30 jours de données brutes. Vous pouvez inspecter de manière proactive les événements de votre réseau pour localiser les indicateurs et entités intéressants. L’accès flexible aux données facilite le repérage sans contrainte pour les menaces connues et potentielles.

Vous pouvez utiliser les mêmes requêtes de recherche de menace pour créer des règles de détection personnalisées. Ces règles s’exécutent automatiquement pour vérifier et répondre à divers événements et États du système, y compris l’activité de violation présumée et les machines mal configurées.

Dans le centre de sécurité Microsoft 365, la recherche avancée prend en charge les requêtes qui examinent des données provenant de différents espaces de travail, notamment des données sur les appareils, les e-mails, les applications et les identités de Microsoft Defender ATP, Office 365 ATP, sécurité des applications Cloud Microsoft et Azure ATP. Pour utiliser le repérage avancé, [activez Protection Microsoft contre les menaces](mtp-enable.md).

## <a name="get-started-with-advanced-hunting"></a>Prise en main du repérage avancé

Nous vous recommandons de suivre plusieurs étapes pour devenir rapidement opérationnel avec le repérage avancé.

| Objectif d’apprentissage | Description | Ressource |
|--|--|--|
| **Prise en main du langage** | La fonction de repérage avancé est basée sur le [langage de requête Kusto](https://docs.microsoft.com/azure/kusto/query/), prenant en charge les mêmes syntaxe et opérateurs. Commencez à découvrir le langage de requête en exécutant votre première requête. | [Vue d'ensemble du language de requête](advanced-hunting-query-language.md) |
| **En savoir plus sur l’utilisation des résultats de la requête** | Découvrez les graphiques et les différentes façons d’afficher ou d’exporter les résultats. Découvrez comment affiner rapidement les requêtes et approfondir pour obtenir des informations plus détaillées. | [Travailler avec les résultats de la requête](advanced-hunting-query-results.md) |
| **Comprendre le schéma** | Obtenez une compréhension optimale des tableaux du schéma et de leurs colonnes. Cela vous permet de déterminer où rechercher des données et comment construire vos requêtes. | [Référence de schéma](advanced-hunting-schema-tables.md) |
| **Utiliser les requêtes prédéfinies** | Explorez les collections de requêtes prédéfinies couvrant différents scénarios de repérage de menaces. | [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md) |
| **Optimiser les requêtes** | Découvrez comment créer des requêtes et des requêtes efficaces qui combinent des données provenant des e-mails et d’appareils. | - [Meilleures pratiques en matière de requêtes](advanced-hunting-shared-queries.md) <br>- [Recherche sur les appareils et les e-mails](advanced-hunting-best-practices.md) |
| **Créer des règles de détection personnalisées** | Découvrez comment utiliser les requêtes de chasse avancées pour déclencher des alertes et appliquer les actions de réponse automatiquement. | - [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)<br>- [Règles de détection personnalisées](custom-detection-rules.md) |

## <a name="get-access"></a>Obtenir l’accès
Pour utiliser la chasse avancée ou d’autres fonctionnalités de [protection contre les menaces Microsoft](microsoft-threat-protection.md) , vous devez disposer d’un rôle approprié dans Azure ad. Notez que votre accès aux données de point de terminaison est influencé par les paramètres de contrôle d’accès basé sur un rôle dans Microsoft Defender ATP. [En savoir plus sur la gestion de l’accès à Microsoft Threat Protection](mtp-permissions.md)

## <a name="get-help-as-you-write-queries"></a>Obtenez de l’aide lorsque vous rédigez des requêtes
Tirez parti des fonctionnalités suivantes pour rédiger des requêtes plus rapidement :
- **Suggestion** automatique : lors de l’écriture de requêtes, la recherche avancée fournit des suggestions d’IntelliSense. 
- **Référence de schéma** : une référence de schéma qui inclut la liste des tableaux et leurs colonnes est fournie à côté de votre espace de travail. Si vous souhaitez en savoir plus, veuillez placer le pointeur sur un élément. Double-cliquez sur un élément pour l’insérer dans l’éditeur de requête.

## <a name="related-topics"></a>Sujets associés
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)
