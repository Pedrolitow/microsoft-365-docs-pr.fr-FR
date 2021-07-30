---
title: Vue d’ensemble du chasse avancée dans Microsoft Defender pour point de terminaison
description: Utiliser les fonctionnalités de recherche de menaces dans Microsoft Defender pour point de terminaison pour créer des requêtes qui trouvent des menaces et des faiblesses dans votre réseau
keywords: repérage avancé, repérage de menace, repérage de cybermenace, mdatp, microsoft defender atp, microsoft defender pour le point de terminaison, wdatp, recherche, requête, télémétrie, détections personnalisées, schéma, kusto, fuseau horaire, UTC
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
ms.openlocfilehash: c106e76486854817c87f290f060999020beae5fd
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53655454"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting"></a>Recherche proactive des menaces avec le chasse avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhunting-abovefoldlink)

Le repérage avancé est un outil de repérage de menaces basé sur des requêtes qui vous permet d’explorer jusqu’à 30 jours de données brutes. Vous pouvez inspecter de manière proactive les événements de votre réseau pour localiser les indicateurs et entités de menace. L’accès flexible aux données permet un recherche sans contraintes pour les menaces connues et potentielles.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide de la recherche avancée et un bref didacticiel qui vous aidera à démarrer rapidement.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqo]

Vous pouvez utiliser les mêmes requêtes de repérage de menaces pour créer des règles de détection personnalisées. Ces règles s’exécutent automatiquement pour vérifier et répondre aux activités suspectées de violation, aux ordinateurs mal configurés et à d’autres conclusions.

> [!TIP]
> Utilisez la recherche avancée [dans Microsoft 365 Defender](/microsoft-365/security/defender/advanced-hunting-overview) pour la recherche de menaces à l’aide des données de Defender pour endpoint, Microsoft Defender pour Office 365, Microsoft Cloud App Security et Microsoft Defender pour l’identité. [Activer Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable).

En savoir plus sur la façon de déplacer vos flux de travail de recherche avancée de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender dans Migrer des requêtes de recherche avancée à partir de [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde).

## <a name="get-started-with-advanced-hunting"></a>Prise en main du repérage avancé

Pour accélérer vos connaissances en matière de recherche avancée, vous suivrez les étapes suivantes.

Nous vous recommandons de suivre plusieurs étapes pour devenir rapidement opérationnel avec le repérage avancé.

<br>

****

|Objectif d’apprentissage|Description|Ressource|
|---|---|---|
|**Découvrir la langue**|La recherche avancée est basée sur le langage de requête [Kusto,](/azure/kusto/query/)en charge de la même syntaxe et des mêmes opérateurs. Commencez à découvrir le langage de requête en exécutant votre première requête.|[Vue d'ensemble du language de requête](advanced-hunting-query-language.md)|
|**Découvrez comment utiliser les résultats de la requête**|Découvrez les graphiques et les différentes façons d’afficher ou d’exporter vos résultats. Découvrez comment modifier rapidement les requêtes et explorer les détails pour obtenir des informations plus riches.|[Utiliser les résultats d’une requête](advanced-hunting-query-results.md)|
|**Comprendre le schéma**|Obtenez une compréhension optimale des tableaux du schéma et de leurs colonnes. Découvrez où rechercher des données lors de la construction de vos requêtes.|[Référence de schéma](advanced-hunting-schema-reference.md)|
|**Utiliser des requêtes prédéfinies**|Explorez les collections de requêtes prédéfinies couvrant différents scénarios de repérage de menaces.|[Requêtes partagées](advanced-hunting-shared-queries.md)|
|**Optimiser les requêtes et gérer les erreurs**|Comprendre comment créer des requêtes efficaces et sans erreur.|- [Meilleures pratiques en matière de requête](advanced-hunting-best-practices.md)<br>- [Gérer les erreurs](advanced-hunting-errors.md)|
|**Obtenir la couverture la plus complète**|Utilisez les paramètres d’audit pour fournir une meilleure couverture des données à votre organisation.|- [Étendre la couverture de recherche avancée](advanced-hunting-extend-data.md)|
|**Exécuter un examen rapide**|Exécutez rapidement une requête de recherche avancée pour examiner les activités suspectes.|- [Recherche rapide des informations sur l’entité ou les événements avec *la recherche de go*](advanced-hunting-go-hunt.md)|
|**Contenir des menaces et résoudre les compromissions**|Répondre aux attaques en mettre en quarantaine des fichiers, en limitant l’exécution de l’application et d’autres actions|- [Prendre des mesures sur les résultats de requête de recherche avancée](advanced-hunting-take-action.md)|
|**Créer des règles de détection personnalisées**|Comprendre comment utiliser des requêtes de recherche avancées pour déclencher des alertes et prendre des actions de réponse automatiquement.|- [Vue d’ensemble des détections personnalisées](overview-custom-detections.md)<br>- [Règles de détection personnalisées](custom-detection-rules.md)|
|


## <a name="data-freshness-and-update-frequency"></a>Actualisation des données et fréquence de mise à jour

Les données de recherche avancée peuvent être classées en deux types distincts, chacun consolidé différemment.

- **Données d’événement ou d’activité**: remplit les tableaux sur les alertes, les événements de sécurité, les événements système et les évaluations de routine. Le recherche avancée reçoit ces données presque immédiatement après que les capteurs qui les collectent les transmettent avec succès à Defender for Endpoint.
- **Données d’entité**: remplit les tables avec des informations consolidées sur les utilisateurs et les appareils. Ces données proviennent à la fois de sources de données relativement statiques et de sources dynamiques, telles que les entrées Active Directory et les journaux d’événements. Pour fournir des données actualisées, les tableaux sont mis à jour avec de nouvelles informations toutes les 15 minutes, en ajoutant des lignes qui peuvent ne pas être entièrement remplies. Toutes les 24 heures, les données sont consolidées pour insérer un enregistrement qui contient le jeu de données le plus récent et le plus complet sur chaque entité.

## <a name="time-zone"></a>Fuseau horaire

Les informations de temps dans le hunting avancé se trouve actuellement dans le fuseau horaire UTC.

## <a name="related-topics"></a>Sujets associés

- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](overview-custom-detections.md)
