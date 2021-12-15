---
title: Table AlertInfo dans le schéma de recherche avancé
description: En savoir plus sur les événements de génération d’alertes dans la table AlertInfo du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, AlertInfo, alert, severity, category, MITRE, ATT&CK, Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Cloud App Security, MCAS et Microsoft Defender pour l’identité
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
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 0298b4f83ac748048215af4f5b1f8261a2a8c67c
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61530786"
---
# <a name="alertinfo"></a>AlertInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender



Le tableau du schéma de recherche avancée contient des informations sur les alertes de Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender pour les applications cloud et `AlertInfo` Microsoft Defender pour l’identité. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `AlertId` | `string` | Identificateur unique de l’alerte |
| `Title` | `string` | Titre de l'alerte |
| `Category` | `string` | Type d’indicateur de menace ou d’activité de violation identifié par l’alerte |
| `Severity` | `string` | Indique l’impact potentiel (élevé, moyen ou faible) de l’indicateur de menace ou de la violation identifié(e) par l’alerte |
| `ServiceSource` | `string` | Produit ou service qui a fourni les informations d’alerte |
| `DetectionSource` | `string` | Technologie ou capteur de détection qui a identifié le composant ou l’activité notable |
| `AttackTechniques` | `string` | MITRE ATT&techniques CK associées à l’activité ayant déclenché l’alerte |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
