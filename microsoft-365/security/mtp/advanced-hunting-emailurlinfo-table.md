---
title: Table EmailUrlInfo dans le schéma de repérage avancé
description: En savoir plus sur les URL ou les liens dans la table EmailUrlInfo du schéma de repérage avancé
keywords: repérage avancé, repérage de menace, repérage de cybermenace, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, EmailUrlInfo, id message réseau, id, url, lien
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
ms.openlocfilehash: 10cf82667fd97eebe66c376e0539db000f20b1c2
ms.sourcegitcommit: 0c9c28a87201c7470716216d99175356fb3d1a47
ms.translationtype: MT + HT Review
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2019
ms.locfileid: "39911038"
---
# <a name="emailurlinfo"></a>EmailUrlInfo

**S’applique à :**
- Protection Microsoft contre les menaces

[!include[Prerelease information](prerelease.md)]

La table `EmailUrlInfo` dans le schéma de [repérage avancé](advanced-hunting-overview.md) contient des informations sur les URL et les pièces jointes des e-mails traités par Office 365 - Protection avancée contre les menaces. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `EventTime` | DateHeure | Date et heure d’enregistrement de l’événement |
| `UrlId` | string | Identificateur unique de l’URL dans l’objet, le corps ou la pièce jointe de l’e-mail |
| `NetworkMessageId` | string | Identificateur unique d’e-mail, généré par Office 365 |
| `Url` | string | URL complète dans l’objet, le corps ou la pièce jointe de l’e-mail |

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)