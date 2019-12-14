---
title: Table AlertEvents dans le schéma de repérage avancé
description: En savoir plus sur les événements de génération d’alertes dans la table AlertEvents du schéma de repérage avancé
keywords: repérage avancé, repérage de menace, repérage de cybermenace, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, alertevents, alerte, gravité, catégorie
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 4d83b659a98c56cc59e88f9777aa73ca2e25b745
ms.sourcegitcommit: 0c9c28a87201c7470716216d99175356fb3d1a47
ms.translationtype: MT + HT Review
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2019
ms.locfileid: "39911024"
---
# <a name="alertevents"></a>AlertEvents

**S’applique à :**
- Protection Microsoft contre les menaces

[!include[Prerelease information](prerelease.md)]

La table `AlertEvents` dans le schéma de [repérage avancé](advanced-hunting-overview.md) contient des informations sur les pièces jointes des alertes Microsoft Defender - Protection avancée contre les menaces. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `AlertId` | string | Identificateur unique de l’alerte |
| `EventTime` | DateHeure | Date et heure d’enregistrement de l’événement |
| `MachineId` | string | Identificateur unique de la machine dans le service |
| `ComputerName` | string | Nom de domaine complet (FQDN) de la machine |
| `Severity` | string | Indique l’impact potentiel (élevé, moyen ou faible) de l’indicateur de menace ou de la violation identifié(e) par l’alerte |
| `Category` | string | Type d’indicateur de menace ou d’activité de violation identifié par l’alerte |
| `Title` | string | Titre de l'alerte |
| `FileName` | string | Nom du fichier auquel l’action enregistrée a été appliquée |
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `RemoteUrl` | string | URL ou nom de domaine complet (FQDN) à laquelle/auquel la connexion était en cours |
| `RemoteIP` | string | Adresse IP à laquelle la connexion était en cours |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes ComputerName et EventTime |
| `Table` | string | Table qui contient les détails de l’événement |

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
