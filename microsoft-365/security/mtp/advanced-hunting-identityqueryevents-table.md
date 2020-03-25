---
title: Table IdentityQueryEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements de requête Active Directory dans la table IdentityQueryEvents du schéma de chasse avancé
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, IdentityQueryEvents, Azure AD, Active Directory, Azure ATP, identités, requêtes LDAP
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
ms.openlocfilehash: b2fc94d6ac6606c97b4824bc556b7299a2bd8ec7
ms.sourcegitcommit: 3b2fdf159d7dd962493a3838e3cf0cf429ee2bf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "42929165"
---
# <a name="identityqueryevents"></a>IdentityQueryEvents

**S’applique à :**
- Protection Microsoft contre les menaces

Le `IdentityQueryEvents` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les requêtes exécutées sur des objets Active Directory, tels que les utilisateurs, les groupes, les appareils et les domaines. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `ActionType` | string | Type d’activité qui a déclenché l’événement |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `Query` | string | Type de requête : QueryGroup, QueryUser ou EnumerateUsers |
| `QueryObject` | string | Nom de l’utilisateur, du groupe, de l’appareil, du domaine ou de tout autre type d’entité interrogé. |
| `Protocol` | string | Protocole utilisé pendant la communication |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountDomain` | string | Domaine du compte |
| `AccountUpn` | string | Nom d’utilisateur principal (UPN) du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure AD |
| `AccountDisplayName` | string | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. Il s’agit généralement d’une combinaison d’un nom donné, d’une initiation au milieu et d’un nom de famille ou nom. |
| `DeviceName` | string | Nom de domaine complet (FQDN) du point de terminaison |
| `IPAddress` | string | Adresse IP affectée au point de terminaison et utilisée pendant les communications réseau associées |
| `Location` | string | Ville, pays ou autre emplacement géographique associé à l’événement |

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
