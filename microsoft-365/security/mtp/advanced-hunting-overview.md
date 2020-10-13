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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a059c4dd1f09bc5101f5ebb027c92e6551ca8dd6
ms.sourcegitcommit: de600339b08951d6dd3933288a8da2327a4b6ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48430420"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-threat-protection"></a>Repérage proactive de menaces avec repérage avancé dans la Protection Microsoft contre les menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

Le repérage avancé est un outil de repérage de menaces basé sur des requêtes qui vous permet d’explorer jusqu’à 30 jours de données brutes. Vous pouvez inspecter de manière proactive les événements de votre réseau afin de localiser les indicateurs de menace et les entités. L’accès flexible aux données permet une chasse libre aux menaces connues et potentielles.
<p></p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bp7O]

Vous pouvez utiliser les mêmes requêtes de repérage de menaces pour créer des règles de détection personnalisées. Ces règles s’exécutent automatiquement pour vérifier, puis répondre à une activité de violation présumée, des ordinateurs mal configurés et d’autres résultats.

Cette fonctionnalité est similaire à la [chasse avancée dans Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview). Disponible dans le centre de sécurité Microsoft 365, cette fonctionnalité prend en charge les requêtes qui vérifient un ensemble de données plus large à partir des éléments suivants :

- Microsoft Defender – Protection avancée contre les menaces
- Office 365 – Protection avancée contre les menaces
- Microsoft Cloud App Security
- Azure Advanced Threat Protection

Pour utiliser le repérage avancé, [activez Protection Microsoft contre les menaces](mtp-enable.md).

## <a name="get-started-with-advanced-hunting"></a>Prise en main du repérage avancé

Nous vous recommandons de suivre plusieurs étapes pour commencer rapidement à utiliser la chasse avancée.

| Objectif d’apprentissage | Description | Ressource |
|--|--|--|
| **En savoir plus sur la langue** | La chasse avancée est basée sur le [langage de requête Kusto](https://docs.microsoft.com/azure/kusto/query/), qui prend en charge les mêmes syntaxe et opérateurs. Commencez à découvrir le langage de requête en exécutant votre première requête. | [Vue d'ensemble du language de requête](advanced-hunting-query-language.md) |
| **En savoir plus sur l’utilisation des résultats de la requête** | Découvrez les graphiques et les différentes façons d’afficher ou d’exporter les résultats. Découvrez comment affiner rapidement les requêtes, extraire des informations plus riches et prendre des mesures de réponse. | - [Utiliser les résultats de la requête](advanced-hunting-query-results.md)<br>- [Effectuer une action sur les résultats de la requête](advanced-hunting-take-action.md) |
| **Comprendre le schéma** | Obtenez une compréhension optimale des tableaux du schéma et de leurs colonnes. Découvrez où rechercher des données lors de la construction de vos requêtes. | - [Référence du schéma](advanced-hunting-schema-tables.md)<br>- [Transition de Microsoft Defender ATP](advanced-hunting-migrate-from-mdatp.md) |
| **Obtenir des conseils et des exemples d’experts** | Formation gratuite aux guides des experts Microsoft. Explorez les collections de requêtes prédéfinies couvrant différents scénarios de repérage de menaces. | - [Obtenir une formation expert](advanced-hunting-expert-training.md)<br>- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)<br>- [Aller-retour](advanced-hunting-go-hunt.md)<br>- [Recherche de menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md) |
| **Optimiser les requêtes et gérer les erreurs** | Découvrez comment créer des requêtes efficaces et sans erreur. | - [Meilleures pratiques en matière de requêtes](advanced-hunting-best-practices.md)<br>- [Gérer les erreurs](advanced-hunting-errors.md) |
| **Créer des règles de détection personnalisées** | Découvrez comment utiliser les requêtes de chasse avancées pour déclencher des alertes et effectuer des actions de réponse automatiquement. | - [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)<br>- [Règles de détection personnalisées](custom-detection-rules.md) |

## <a name="get-access"></a>Obtenir l’accès
Pour utiliser la chasse avancée ou d’autres fonctionnalités de [protection contre les menaces Microsoft](microsoft-threat-protection.md) , vous avez besoin d’un rôle approprié dans Azure Active Directory. De plus, votre accès aux données de point de terminaison est déterminé par les paramètres de contrôle d’accès basé sur un rôle (RBAC) dans Microsoft Defender ATP. [En savoir plus sur la gestion de l’accès à Microsoft Threat Protection](mtp-permissions.md)

## <a name="data-freshness-and-update-frequency"></a>Actualisation et fréquence de mise à jour des données
Les données de chasse avancées peuvent être classées en deux types distincts, chacune étant consolidée différemment.

- **Données d’événement ou d’activité**: renseigne des tableaux sur les alertes, les événements de sécurité, les événements système et les évaluations de routine. La chasse avancée reçoit ces données presque immédiatement après que les capteurs qui les recueillent les transmettent aux services Cloud correspondants. Par exemple, vous pouvez interroger des données d’événement à partir de capteurs sains sur des stations de travail ou des contrôleurs de domaine presque immédiatement après qu’ils sont disponibles sur Microsoft Defender ATP et Azure ATP.
- **Données d’entité**: renseigne des tables avec des informations sur les utilisateurs et les appareils. Ces données proviennent de sources de données relativement statiques et de sources dynamiques, telles que les entrées et les journaux des événements Active Directory. Pour fournir des données actualisées, les tableaux sont mis à jour avec les nouvelles informations toutes les 15 minutes, ajoutant des lignes qui ne sont peut-être pas entièrement renseignées. Toutes les 24 heures, les données sont consolidées pour insérer un enregistrement qui contient le jeu de données le plus complet et le plus complet sur chaque entité.

## <a name="time-zone"></a>Fuseau horaire
Les informations de temps dans la chasse avancée se trouvent dans le fuseau horaire UTC.

## <a name="related-topics"></a>Sujets associés
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Obtenir une formation spécialisée](advanced-hunting-expert-training.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)

