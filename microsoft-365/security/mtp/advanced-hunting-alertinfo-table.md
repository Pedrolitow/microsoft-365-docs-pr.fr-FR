---
title: Table AlertInfo dans le schéma de chasse avancé
description: En savoir plus sur les événements de génération d’alerte dans la table AlertInfo du schéma de chasse avancé
keywords: chasse aux menaces, recherche de menace, recherche de menace, protection contre les menaces Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, AlertInfo, alerte, gravité, catégorie, MITRE, ATT&CK, Microsoft Defender ATP, MDATP, Office 365 ATP, Microsoft Cloud App Security, MCAS et Azure ATP
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
ms.openlocfilehash: 739ee33b162c1e701603a17e59f0d0c2611c064c
ms.sourcegitcommit: de600339b08951d6dd3933288a8da2327a4b6ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48430174"
---
# <a name="alertinfo"></a>AlertInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces



Le `AlertInfo` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les alertes à partir de Microsoft Defender atp, Office 365 ATP, Microsoft Cloud App Security et Azure ATP. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `AlertId` | string | Identificateur unique de l’alerte |
| `Title` | string | Titre de l'alerte |
| `Category` | string | Type d’indicateur de menace ou d’activité de violation identifié par l’alerte |
| `Severity` | string | Indique l’impact potentiel (élevé, moyen ou faible) de l’indicateur de menace ou de la violation identifié(e) par l’alerte |
| `ServiceSource` | string | Produit ou service qui a fourni les informations d’alerte |
| `DetectionSource` | string | Technologie ou capteur de détection qui a identifié le composant ou l’activité notable |
| `AttackTechniques` | string | MITRE ATT&CK techniques associées à l’activité qui a déclenché l’alerte |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les emails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
