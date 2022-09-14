---
title: Vue d’ensemble de la chasse avancée dans Microsoft Defender pour point de terminaison
description: Utiliser les fonctionnalités de repérage des menaces dans Microsoft Defender pour point de terminaison pour créer des requêtes qui recherchent des menaces et des faiblesses dans votre réseau
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, mdatp, microsoft defender atp, microsoft defender pour point de terminaison, wdatp, recherche, requête, télémétrie, détections personnalisées, schéma, kusto, fuseau horaire, UTC
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 4995e9b2090b3de237581bb2200304a7a37db7f1
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67679414"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting"></a>Chasse proactive pour les menaces avec repérage avancé

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhunting-abovefoldlink)

Le repérage avancé est un outil de repérage de menaces basé sur des requêtes qui vous permet d’explorer jusqu’à 30 jours de données brutes. Vous pouvez inspecter de manière proactive les événements de votre réseau pour localiser les indicateurs et entités de menace. L’accès flexible aux données permet de rechercher sans contrainte les menaces connues et potentielles.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide de la chasse avancée et un court didacticiel qui vous aidera à démarrer rapidement.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqo]

Vous pouvez utiliser les mêmes requêtes de repérage de menaces pour créer des règles de détection personnalisées. Ces règles s’exécutent automatiquement pour rechercher et répondre aux activités suspectes de violation, aux machines mal configurées et à d’autres résultats.

> [!TIP]
> Utilisez [la chasse avancée dans Microsoft 365 Defender](/microsoft-365/security/defender/advanced-hunting-overview) pour rechercher des menaces à l’aide des données de Defender pour point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender for Cloud Apps et Microsoft Defender pour Identity. [Activez Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable).

En savoir plus sur le déplacement de vos flux de travail de chasse avancés de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender dans [Migrer des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde).

## <a name="get-started-with-advanced-hunting"></a>Prise en main du repérage avancé

Suivez les étapes suivantes pour augmenter vos connaissances avancées en matière de chasse.

Nous vous recommandons de suivre plusieurs étapes pour devenir rapidement opérationnel avec le repérage avancé.

<br>

****

|Objectif d’apprentissage|Description|Ressource|
|---|---|---|
|**Apprendre la langue**|La chasse avancée est basée sur le [langage de requête Kusto](/azure/kusto/query/), prenant en charge la même syntaxe et les mêmes opérateurs. Commencez à découvrir le langage de requête en exécutant votre première requête.|[Vue d'ensemble du language de requête](advanced-hunting-query-language.md)|
|**Découvrez comment utiliser les résultats de la requête**|Découvrez les graphiques et les différentes façons d’afficher ou d’exporter vos résultats. Découvrez comment modifier rapidement les requêtes et explorer les détails pour obtenir des informations plus détaillées.|[Utiliser les résultats d’une requête](advanced-hunting-query-results.md)|
|**Comprendre le schéma**|Obtenez une compréhension optimale des tableaux du schéma et de leurs colonnes. Découvrez où rechercher des données lors de la construction de vos requêtes.|[Référence de schéma](advanced-hunting-schema-reference.md)|
|**Utiliser des requêtes prédéfinies**|Explorez les collections de requêtes prédéfinies couvrant différents scénarios de repérage de menaces.|[Requêtes partagées](advanced-hunting-shared-queries.md)|
|**Optimiser les requêtes et gérer les erreurs**|Découvrez comment créer des requêtes efficaces et sans erreur.|[Meilleures pratiques en matière de requête](advanced-hunting-best-practices.md) <p> [Gestion des erreurs](advanced-hunting-errors.md)|
|**Obtenir la couverture la plus complète**|Utilisez les paramètres d’audit pour fournir une meilleure couverture des données pour votre organisation.|[Étendre la couverture de chasse avancée](advanced-hunting-extend-data.md)|
|**Exécuter une enquête rapide**|Exécutez rapidement une requête de chasse avancée pour examiner les activités suspectes.|[Rechercher rapidement des informations d’entité ou d’événement avec *go hunt*](advanced-hunting-go-hunt.md)|
|**Contenir des menaces et résoudre les compromissions**|Répondre aux attaques en mettant en quarantaine des fichiers, en limitant l’exécution de l’application et d’autres actions|[Prendre des mesures sur les résultats de la requête de chasse avancée](advanced-hunting-take-action.md)|
|**Créer les règles de détection personnalisées**|Découvrez comment utiliser des requêtes de chasse avancées pour déclencher des alertes et effectuer automatiquement des actions de réponse.|[Vue d’ensemble des détections personnalisées](overview-custom-detections.md) <p> [Règles de détection personnalisée](custom-detection-rules.md)|
|

## <a name="data-freshness-and-update-frequency"></a>Fréquence d’actualisation et de mise à jour des données

Les données de recherche avancée peuvent être classées en deux types distincts, chacun consolidé différemment.

- **Données d’événement ou d’activité** : remplit des tables sur les alertes, les événements de sécurité, les événements système et les évaluations de routine. Le repérage avancé reçoit ces données presque immédiatement après que les capteurs qui les collectent les ont transmises à Defender pour point de terminaison.
- **Données d’entité** : remplit les tables avec des informations consolidées sur les utilisateurs et les appareils. Ces données proviennent à la fois de sources de données relativement statiques et de sources dynamiques, telles que les entrées Active Directory et les journaux d’événements. Pour fournir des données actualisées, les tables sont mises à jour avec de nouvelles informations toutes les 15 minutes, en ajoutant des lignes qui peuvent ne pas être entièrement remplies. Toutes les 24 heures, les données sont consolidées pour insérer un enregistrement qui contient le jeu de données le plus récent et le plus complet sur chaque entité.

## <a name="time-zone"></a>Fuseau horaire

Les informations de temps dans la chasse avancée se trouve actuellement dans le fuseau horaire UTC.

## <a name="related-topics"></a>Sujets associés

- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](overview-custom-detections.md)
- [Vue d’ensemble du compte de stockage](/azure/storage/common/storage-account-overview)
- [Azure Event Hubs : plateforme de streaming Big Data et service d’ingestion d’événements](/azure/event-hubs/event-hubs-about)
