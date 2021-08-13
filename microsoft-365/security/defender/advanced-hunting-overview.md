---
title: Vue d’ensemble - Recherche avancée
description: En savoir plus sur les requêtes de repérage avancés dans Microsoft 365 et leur utilisation pour rechercher de manière proactive les menaces et faiblesses de votre réseau
keywords: repérage avancé, repérage de menace, repérage de cybermenace, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: 564afed2c10d232076bf6875e035bcf03ea7712ada2b430729f4a936a675b8bb
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53833194"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-365-defender"></a>Recherchez de manière proactive les menaces avec le recherche avancée dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

> Vous voulez essayer Microsoft 365 Defender ? Vous pouvez [l’évaluer dans un environnement de laboratoire](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) ou [exécuter votre projet pilote en production](m365d-pilot.md?ocid=cx-evalpilot).
>

Le recherche avancée est un outil de recherche de menace basé sur une requête qui vous permet d’explorer jusqu’à 30 jours de données brutes. Vous pouvez inspecter de manière proactive les événements de votre réseau pour localiser les indicateurs et entités de menace. L’accès flexible aux données permet un recherche sans contraintes pour les menaces connues et potentielles.
<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bp7O]

Vous pouvez utiliser les mêmes requêtes de repérage de menaces pour créer des règles de détection personnalisées. Ces règles s’exécutent automatiquement pour vérifier et répondre aux activités suspectées de violation, aux ordinateurs mal configurés et à d’autres conclusions.

Cette fonctionnalité est similaire au recherche avancée [dans Microsoft Defender pour point](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) de terminaison et prend en charge les requêtes qui vérifient un jeu de données plus large à partir de :

- Microsoft Defender pour point de terminaison
- Microsoft Defender pour Office 365
- Microsoft Cloud App Security
- Microsoft Defender pour l’identité

Pour utiliser le hunting avancé, [Microsoft 365 Defender](m365d-enable.md).

Pour plus d’informations sur le Microsoft Cloud App Security avancé, voir la [vidéo.](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa) 

## <a name="get-started-with-advanced-hunting"></a>Prise en main du repérage avancé

Nous vous recommandons de suivre plusieurs étapes pour commencer rapidement le recherche avancée.

| Objectif d’apprentissage | Description | Ressource |
|--|--|--|
| **Découvrir la langue** | La recherche avancée est basée sur le langage de requête [Kusto,](/azure/kusto/query/)en charge de la même syntaxe et des mêmes opérateurs. Commencez à découvrir le langage de requête en exécutant votre première requête. | [Vue d'ensemble du language de requête](advanced-hunting-query-language.md) |
| **Découvrez comment utiliser les résultats de la requête** | Découvrez les graphiques et les différentes façons d’afficher ou d’exporter vos résultats. Découvrez comment modifier rapidement les requêtes, explorer pour obtenir des informations plus riches et prendre des mesures de réponse. | - [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)<br /> - [Prendre des mesures sur les résultats de la requête](advanced-hunting-take-action.md) |
| **Comprendre le schéma** | Obtenez une compréhension optimale des tableaux du schéma et de leurs colonnes. Découvrez où rechercher des données lors de la construction de vos requêtes. | - [Référence de schéma](advanced-hunting-schema-tables.md) <br />- [Transition de Microsoft Defender pour le point de terminaison](advanced-hunting-migrate-from-mde.md) |
| **Obtenir des conseils et des exemples d’experts** | Formez gratuitement avec des guides d’experts Microsoft. Explorez les collections de requêtes prédéfinies couvrant différents scénarios de repérage de menaces. | - [Obtenir une formation d’expert](advanced-hunting-expert-training.md) <br />- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md) <br />- [Aller à la recherche](advanced-hunting-go-hunt.md) <br />- [Recherchez les menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md) |
| **Optimiser les requêtes et gérer les erreurs** | Comprendre comment créer des requêtes efficaces et sans erreur. | - [Meilleures pratiques en matière de requête](advanced-hunting-best-practices.md)<br />- [Gérer les erreurs](advanced-hunting-errors.md) |
| **Créer des règles de détection personnalisées** | Comprendre comment utiliser des requêtes de recherche avancées pour déclencher des alertes et prendre des actions de réponse automatiquement. | - [Vue d’ensemble des détections personnalisées](custom-detections-overview.md) <br />- [Règles de détection personnalisées](custom-detection-rules.md) |

## <a name="get-access"></a>Obtenir l’accès
Pour utiliser la recherche avancée ou [d Microsoft 365 Defender](microsoft-365-defender.md) fonctionnalités de recherche, vous avez besoin d’un rôle approprié dans Azure Active Directory. [En savoir plus sur les rôles et autorisations requis pour le chasse avancée](custom-roles.md).

En outre, votre accès aux données de point de terminaison est déterminé par les paramètres de contrôle d’accès basé sur un rôle (RBAC) dans Microsoft Defender for Endpoint. [En savoir plus sur la gestion de l’accès Microsoft 365 Defender](m365d-permissions.md).


## <a name="data-freshness-and-update-frequency"></a>Actualisation des données et fréquence de mise à jour
Les données de recherche avancée peuvent être classées en deux types distincts, chacun consolidé différemment.

- **Données d’événement ou** d’activité : remplit des tableaux sur les alertes, les événements de sécurité, les événements système et les évaluations de routine. Le recherche avancée reçoit ces données presque immédiatement après que les capteurs qui les collectent les transmettent avec succès aux services cloud correspondants. Par exemple, vous pouvez interroger des données d’événements à partir de capteurs sains sur des stations de travail ou des contrôleurs de domaine presque immédiatement après qu’elles soient disponibles sur Microsoft Defender for Endpoint et Microsoft Defender for Identity.
- **Données d’entité**: remplit les tableaux avec des informations sur les utilisateurs et les appareils. Ces données proviennent à la fois de sources de données relativement statiques et de sources dynamiques, telles que les entrées Active Directory et les journaux d’événements. Pour fournir des données actualisées, les tableaux sont mis à jour avec de nouvelles informations toutes les 15 minutes, en ajoutant des lignes qui peuvent ne pas être entièrement remplies. Toutes les 24 heures, les données sont consolidées pour insérer un enregistrement qui contient le jeu de données le plus récent et le plus complet sur chaque entité.

## <a name="time-zone"></a>Fuseau horaire
Les informations de temps dans le hunting avancé se trouve dans le fuseau horaire UTC.

## <a name="related-topics"></a>Sujets associés
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Obtenir une formation spécialisée](advanced-hunting-expert-training.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)
