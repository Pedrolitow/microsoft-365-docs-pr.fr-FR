---
title: Table EmailUrlInfo dans le schéma de repérage avancé
description: En savoir plus sur les URL ou les liens dans la table EmailUrlInfo du schéma de repérage avancé
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, EmailUrlInfo, ID de message réseau, URL, lien
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
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 47486f34f9926d83e52ba206f63d3e85286527dc
ms.sourcegitcommit: eee4f651bd51d5aedd64e42d02bfed8ccb9be4cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "44515818"
---
# <a name="emailurlinfo"></a>EmailUrlInfo

**S’applique à :**
- Protection Microsoft contre les menaces

La table `EmailUrlInfo` dans le schéma de [repérage avancé](advanced-hunting-overview.md) contient des informations sur les URL et les pièces jointes des e-mails traités par Office 365 - Protection avancée contre les menaces. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `UrlId` | string | Identificateur unique de l’URL dans l’objet, le corps ou la pièce jointe de l’e-mail |
| `NetworkMessageId` | string | Identificateur unique pour le courrier électronique, généré par Microsoft 365 |
| `Url` | string | URL complète dans l’objet, le corps ou la pièce jointe de l’e-mail |

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
