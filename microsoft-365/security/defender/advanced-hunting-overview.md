---
title: Vue d’ensemble - Repérage avancé
description: En savoir plus sur les requêtes de repérage avancés dans Microsoft 365 et leur utilisation pour rechercher de manière proactive les menaces et faiblesses de votre réseau
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto
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
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.custom: seo-marvel-apr2020
search.appverid: met150
ms.openlocfilehash: aaf1ab874eddaae385cf3eaf3f0e3fb0bea8d877
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67741563"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-365-defender"></a>Recherche proactive des menaces avec repérage avancé dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La chasse avancée est un outil de chasse aux menaces basé sur une requête qui vous permet d’explorer jusqu’à 30 jours de données brutes. Vous pouvez inspecter de manière proactive les événements de votre réseau pour localiser les indicateurs et entités de menace. L’accès flexible aux données permet de rechercher sans contrainte les menaces connues et potentielles.

La chasse avancée prend en charge deux modes, guidé et avancé. Utilisez le [mode guidé](advanced-hunting-query-builder.md) si vous n’êtes pas encore familiarisé avec Langage de requête Kusto (KQL) ou si vous préférez la commodité d’un générateur de requêtes. Utilisez le [mode avancé](advanced-hunting-query-language.md) si vous êtes à l’aise avec KQL pour créer des requêtes à partir de zéro. 

**Pour commencer la chasse, lisez [Choisir entre les modes guidés et avancés de chasse dans Microsoft 365 Defender](advanced-hunting-modes.md).**
<br><br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4G6DO]

Vous pouvez utiliser les mêmes requêtes de chasse aux menaces pour créer des règles de détection personnalisées. Ces règles s’exécutent automatiquement pour rechercher et répondre aux activités suspectes de violation, aux machines mal configurées et à d’autres résultats.

Cette fonctionnalité est similaire à la [chasse avancée dans Pertahanan Microsoft untuk Titik Akhir](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) et prend en charge les requêtes qui vérifient un jeu de données plus large provenant de :

- Microsoft Defender pour point de terminaison
- Microsoft Defender pour Office 365
- Microsoft Defender for Cloud Apps
- Microsoft Defender pour l’identité

Pour utiliser la chasse avancée, [activez Microsoft 365 Defender](m365d-enable.md).

Pour plus d’informations sur la chasse avancée dans Microsoft Defender for Cloud Apps données, consultez la [vidéo](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa). 



## <a name="get-access"></a>Obtenir l’accès
Pour utiliser la chasse avancée ou d’autres fonctionnalités [de Microsoft 365 Defender](microsoft-365-defender.md), vous avez besoin d’un rôle approprié dans Azure Active Directory. [Découvrez les rôles et autorisations requis pour la chasse avancée](custom-roles.md).

En outre, votre accès aux données de point de terminaison est déterminé par les paramètres de contrôle d’accès en fonction du rôle (RBAC) dans Pertahanan Microsoft untuk Titik Akhir. [Découvrez la gestion de l’accès à Microsoft 365 Defender](m365d-permissions.md).


## <a name="data-freshness-and-update-frequency"></a>Fréquence d’actualisation et de mise à jour des données
Les données de recherche avancée peuvent être classées en deux types distincts, chacun consolidé différemment.

- Données —**d’événement ou d’activité** remplit des tables sur les alertes, les événements de sécurité, les événements système et les évaluations de routine. Le recherche avancée reçoit ces données presque immédiatement après que les capteurs qui les collectent les transmettent avec succès aux services cloud correspondants. Par exemple, vous pouvez interroger des données d’événements à partir de capteurs sains sur des stations de travail ou des contrôleurs de domaine presque immédiatement après qu’elles sont disponibles sur Pertahanan Microsoft untuk Titik Akhir et Microsoft Defender pour Identity.
- **Données d’entité** : remplit les tables avec des informations sur les utilisateurs et les appareils. Ces données proviennent à la fois de sources de données relativement statiques et de sources dynamiques, telles que les entrées Active Directory et les journaux d’événements. Pour fournir des données actualisées, les tables sont mises à jour avec de nouvelles informations toutes les 15 minutes, en ajoutant des lignes qui peuvent ne pas être entièrement remplies. Toutes les 24 heures, les données sont consolidées pour insérer un enregistrement qui contient le jeu de données le plus récent et le plus complet sur chaque entité.

## <a name="time-zone"></a>Fuseau horaire
Les informations de temps dans la chasse avancée se trouve dans le fuseau horaire UTC (Universal Time Coordinated).

## <a name="related-topics"></a>Voir aussi
- [Choisir entre les modes de chasse guidés et avancés](advanced-hunting-modes.md)
- [Générer des requêtes de chasse à l’aide du mode guidé](advanced-hunting-query-builder.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)
