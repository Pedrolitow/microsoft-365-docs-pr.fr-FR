---
title: Changements de nommage dans le schéma de recherche avancée Microsoft 365 Defender
description: Suivre et passer en revue les tables et colonnes de modifications d’attribution de noms dans le schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, data, naming changes, rename, Microsoft Threat Protection
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
ms.technology: m365d
ms.openlocfilehash: 3f03543b03dca5fe426700ffff4f5c6edb8fa3c7
ms.sourcegitcommit: c550c1b5b9e67398fd95bfb0256c4f5c7930b2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2021
ms.locfileid: "50066868"
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
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailAction` | `EmailAction` | Commentaires des clients. |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicy` | `EmailActionPolicy` | Commentaires des clients. |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicyGuid` | `EmailActionPolicyGuid` | Commentaires des clients. |

## <a name="january-2021"></a>Janvier 2021

| Nom de colonne | Nom de la valeur d’origine | Nouveau nom de valeur | Raison du changement
|--|--|--|--|
| `DetectionSource` | MCAS |    Microsoft Cloud App Security | Changement de nom |
| `DetectionSource` | WindowsDefenderAtp|   EDR| Changement de nom |
| `DetectionSource` | WindowsDefenderAv | Antivirus | Changement de nom |
| `DetectionSource` | WindowsDefenderSmartScreen |  SmartScreen | Changement de nom |
| `DetectionSource` | CustomerTI |  Ti personnalisée | Changement de nom |
| `DetectionSource` | OfficeATP | Microsoft Defender pour Office 365 | Changement de nom |
| `DetectionSource` | MTP   | Microsoft 365 Defender | Changement de nom |
| `DetectionSource` | AzureATP |    Microsoft Defender pour l’identité | Changement de nom |
| `DetectionSource` | CustomDetection   | Détection personnalisée | Changement de nom |
| `DetectionSource` | AutomatedIgoigation |Examen automatisé | Changement de nom |
| `DetectionSource` | ThreatExperts | Spécialistes des menaces Microsoft | Changement de nom |
| `DetectionSource` | Ti tiers | Capteurs tiers | Changement de nom |
| `ServiceSource` | Microsoft Defender ATP| Microsoft Defender pour point de terminaison | Changement de nom |
|`ServiceSource` |Protection Microsoft contre les menaces   | Microsoft 365 Defender | Changement de nom |
| `ServiceSource` | Office 365 – Protection avancée contre les menaces  |Microsoft Defender pour Office 365 | Changement de nom |
| `ServiceSource` |Azure ATP    |Microsoft Defender pour l’identité | Changement de nom |

`DetectionSource`est disponible dans la table [AlertInfo.](advanced-hunting-alertinfo-table.md) `ServiceSource`est disponible dans les tables [AlertEvidence](advanced-hunting-alertevidence-table.md) et [AlertInfo.](advanced-hunting-alertinfo-table.md) 
## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)