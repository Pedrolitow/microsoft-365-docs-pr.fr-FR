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
ms.openlocfilehash: da9712d1f3465c28d2ba880997a52434723a297d
ms.sourcegitcommit: 0ad0092d9c5cb2d69fc70c990a9b7cc03140611b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "40808669"
---
# <a name="emailurlinfo"></a>EmailUrlInfo

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

La table `EmailUrlInfo` dans le schéma de [repérage avancé](advanced-hunting-overview.md) contient des informations sur les URL et les pièces jointes des e-mails traités par Office 365 - Protection avancée contre les menaces. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
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