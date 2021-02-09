---
title: Table IdentityQueryEvents dans le schéma de recherche avancé
description: En savoir plus sur les événements de requête Active Directory dans la table IdentityQueryEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, IdentityQueryEvents, Azure AD, Active Directory, Azure ATP, identities, LDAP queries
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
ms.openlocfilehash: 48a1520e9fc6239fd3105f01a32a03e5e58df174
ms.sourcegitcommit: 005028af7c5a6b2e95f17a0037958131484d9e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "50145284"
---
# <a name="identityqueryevents"></a>IdentityQueryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le tableau du schéma de recherche avancée contient des informations sur les requêtes effectuées sur des objets Active Directory, tels que des utilisateurs, des groupes, des appareils et `IdentityQueryEvents` des domaines. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible `ActionType` dans le centre de sécurité. [](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center)

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `ActionType` | string | Type d’activité qui a déclenché l’événement. Pour plus [d’informations, voir](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) la référence du schéma dans le portail |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `QueryType` | string | Type de requête, tel que QueryGroup, QueryUser ou EnumerateUsers |
| `QueryTarget` | string | Nom de l’utilisateur, du groupe, de l’appareil, du domaine ou tout autre type d’entité interrogé |
| `Query` | string | Chaîne utilisée pour exécuter la requête |
| `Protocol` | string | Protocole utilisé pendant la communication |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountDomain` | string | Domaine du compte |
| `AccountUpn` | string | Nom d’utilisateur principal (UPN) du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure AD |
| `AccountDisplayName` | string | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. En règle générale, une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `DeviceName` | string | Nom de domaine complet (FQDN) du point de terminaison |
| `IPAddress` | string | Adresse IP attribuée au point de terminaison et utilisée lors des communications réseau associées |
| `Port` | string | Port TCP utilisé pendant la communication |
| `DestinationDeviceName` | string | Nom de l’appareil exécutant l’application serveur qui a traitée l’action enregistrée |
| `DestinationIPAddress` | string | Adresse IP de l’appareil exécutant l’application serveur qui a traitée l’action enregistrée |
| `DestinationPort` | string | Port de destination des communications réseau associées |
| `TargetDeviceName` | string | Nom de domaine complet (FQDN) de l’appareil à qui l’action enregistrée a été appliquée |
| `TargetAccountUpn` | string | Nom d’utilisateur principal (UPN) du compte à qui l’action enregistrée a été appliquée |
| `TargetAccountDisplayName` | string | Nom complet du compte à qui l’action enregistrée a été appliquée |
| `Location` | string | Ville, pays ou autre emplacement géographique associé à l’événement |
| `ReportId` | long | Identificateur unique de l’événement |
| `AdditionalFields` | string | Informations supplémentaires sur l’entité ou l’événement |

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
