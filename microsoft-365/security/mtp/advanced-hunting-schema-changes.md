---
title: Changements d’appellation dans le schéma de recherche avancée Microsoft 365 Defender
description: Suivre et passer en revue les tables et les colonnes des modifications d’attribution de noms dans le schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, data, naming changes, rename, Microsoft Threat Protection
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
ms.openlocfilehash: 0bef5f4abcaf0d57af9c160ff31f859c2536ccd2
ms.sourcegitcommit: ec293978e951b09903b79e6642aa587824935e0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "49780785"
---
# <a name="advanced-hunting-schema---naming-changes"></a>Schéma de recherche avancé : modifications d’attribution de noms

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le [schéma de recherche avancée est mis à jour](advanced-hunting-schema-tables.md) régulièrement pour ajouter de nouvelles tables et colonnes. Dans certains cas, les noms des colonnes existantes sont renommés ou remplacés pour améliorer l’expérience utilisateur. Reportez-vous à cet article pour passer en revue les modifications d’attribution de noms qui peuvent avoir un impact sur vos requêtes.

Les modifications d’attribution de noms sont automatiquement appliquées aux requêtes enregistrées dans le centre de sécurité, y compris les requêtes utilisées par les règles de détection personnalisées. Vous n’avez pas besoin de mettre à jour ces requêtes manuellement. Toutefois, vous devrez mettre à jour les requêtes suivantes :
- Requêtes qui sont exécutés à l’aide de l’API
- Requêtes enregistrées ailleurs en dehors du centre de sécurité

## <a name="december-2020"></a>Décembre 2020

| Nom du tableau | Nom de colonne d’origine | Nouveau nom de colonne | Raison du changement
|--|--|--|--|
| [EmailEvents](advanced-hunting-emailevents-table.md) | FinalEmailAction | EmailAction | Commentaires des clients. |
| [EmailEvents](advanced-hunting-emailevents-table.md) | FinalEmailActionPolicy | EmailActionPolicy | Commentaires des clients. |
| [EmailEvents](advanced-hunting-emailevents-table.md) | FinalEmailActionPolicyGuid | EmailActionPolicyGuid | Commentaires des clients. |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)