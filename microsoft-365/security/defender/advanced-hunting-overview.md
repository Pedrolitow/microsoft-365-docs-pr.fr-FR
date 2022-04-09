---
title: Vue d’ensemble - Repérage avancé
description: En savoir plus sur les requêtes de repérage avancés dans Microsoft 365 et leur utilisation pour rechercher de manière proactive les menaces et faiblesses de votre réseau
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto
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
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: 1ee8d8fbd3b1a56f83106ffaf6be937fa984c272
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731436"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-365-defender"></a>Recherche proactive des menaces avec repérage avancé dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La chasse avancée est un outil de chasse aux menaces basé sur une requête qui vous permet d’explorer jusqu’à 30 jours de données brutes. Vous pouvez inspecter de manière proactive les événements de votre réseau pour localiser les indicateurs et entités de menace. L’accès flexible aux données permet de rechercher sans contrainte les menaces connues et potentielles.
<br><br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4G6DO]

Vous pouvez utiliser les mêmes requêtes de chasse aux menaces pour créer des règles de détection personnalisées. Ces règles s’exécutent automatiquement pour rechercher et répondre aux activités suspectes de violation, aux machines mal configurées et à d’autres résultats.

Cette fonctionnalité est similaire à la [chasse avancée dans Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) et prend en charge les requêtes qui vérifient un jeu de données plus large à partir de :

- Microsoft Defender pour point de terminaison
- Microsoft Defender pour Office 365
- Microsoft Defender for Cloud Apps
- Microsoft Defender pour l’identité

Pour utiliser la chasse avancée, [activez Microsoft 365 Defender](m365d-enable.md).

Pour plus d’informations sur la chasse avancée dans Microsoft Defender for Cloud Apps données, consultez la [vidéo](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa). 

## <a name="get-started-with-advanced-hunting"></a>Prise en main du repérage avancé

Nous vous recommandons d’effectuer plusieurs étapes pour commencer rapidement avec la chasse avancée.

| Objectif d’apprentissage | Description | Ressource |
|--|--|--|
| **Apprendre la langue** | La chasse avancée est basée sur [Kusto langage de requête](/azure/kusto/query/), prenant en charge la même syntaxe et les mêmes opérateurs. Commencez à découvrir le langage de requête en exécutant votre première requête. | [Vue d'ensemble du language de requête](advanced-hunting-query-language.md) |
| **Découvrez comment utiliser les résultats de la requête** | Découvrez les graphiques et les différentes façons d’afficher ou d’exporter vos résultats. Découvrez comment modifier rapidement les requêtes, explorer les détails pour obtenir des informations plus détaillées et prendre des mesures de réponse. | - [Utiliser les résultats de la requête](advanced-hunting-query-results.md)<br /> - [Agir sur les résultats de la requête](advanced-hunting-take-action.md) |
| **Comprendre le schéma** | Obtenez une compréhension optimale des tableaux du schéma et de leurs colonnes. Découvrez où rechercher des données lors de la construction de vos requêtes. | - [Référence de schéma](advanced-hunting-schema-tables.md) <br />- [Transition à partir de Microsoft Defender pour point de terminaison](advanced-hunting-migrate-from-mde.md) |
| **Obtenir des conseils et des exemples d’experts** | Entraînez-vous gratuitement avec des guides d’experts Microsoft. Explorez les collections de requêtes prédéfinies couvrant différents scénarios de repérage de menaces. | - [Obtenir une formation d’expert](advanced-hunting-expert-training.md) <br />- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md) <br />- [Aller à la chasse](advanced-hunting-go-hunt.md) <br />- [Rechercher les menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md) |
| **Optimiser les requêtes et gérer les erreurs** | Découvrez comment créer des requêtes efficaces et sans erreur. | - [Meilleures pratiques de requête](advanced-hunting-best-practices.md)<br />- [Gérer les erreurs](advanced-hunting-errors.md) |
| **Créer les règles de détection personnalisées** | Découvrez comment utiliser des requêtes de chasse avancées pour déclencher des alertes et effectuer automatiquement des actions de réponse. | - [Vue d’ensemble des détections personnalisées](custom-detections-overview.md) <br />- [Règles de détection personnalisées](custom-detection-rules.md) |

## <a name="get-access"></a>Obtenir l’accès
Pour utiliser la chasse avancée ou d’autres fonctionnalités [de Microsoft 365 Defender](microsoft-365-defender.md), vous avez besoin d’un rôle approprié dans Azure Active Directory. [Découvrez les rôles et autorisations requis pour la chasse avancée](custom-roles.md).

En outre, votre accès aux données de point de terminaison est déterminé par les paramètres de contrôle d’accès en fonction du rôle (RBAC) dans Microsoft Defender pour point de terminaison. [Découvrez la gestion de l’accès à Microsoft 365 Defender](m365d-permissions.md).


## <a name="data-freshness-and-update-frequency"></a>Actualisation des données et fréquence de mise à jour
Les données de recherche avancée peuvent être classées en deux types distincts, chacun consolidé différemment.

- **Données d’événement ou d’activité** : remplit des tables sur les alertes, les événements de sécurité, les événements système et les évaluations de routine. Le recherche avancée reçoit ces données presque immédiatement après que les capteurs qui les collectent les transmettent avec succès aux services cloud correspondants. Par exemple, vous pouvez interroger des données d’événement à partir de capteurs sains sur des stations de travail ou des contrôleurs de domaine presque immédiatement après qu’elles sont disponibles sur Microsoft Defender pour point de terminaison et Microsoft Defender pour Identity.
- **Données d’entité** : remplit les tables avec des informations sur les utilisateurs et les appareils. Ces données proviennent à la fois de sources de données relativement statiques et de sources dynamiques, telles que les entrées Active Directory et les journaux d’événements. Pour fournir des données actualisées, les tables sont mises à jour avec de nouvelles informations toutes les 15 minutes, en ajoutant des lignes qui risquent de ne pas être entièrement remplies. Toutes les 24 heures, les données sont consolidées pour insérer un enregistrement qui contient le jeu de données le plus récent et le plus complet sur chaque entité.

## <a name="time-zone"></a>Fuseau horaire
Les informations de temps dans la chasse avancée se trouve dans le fuseau horaire UTC.

## <a name="related-topics"></a>Sujets associés
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Obtenir une formation spécialisée](advanced-hunting-expert-training.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)
