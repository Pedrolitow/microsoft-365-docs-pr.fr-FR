---
title: Table IdentityQueryEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements de requête Active Directory dans la table IdentityQueryEvents du schéma de chasse avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, IdentityQueryEvents, Azure AD, Active Directory, Microsoft Defender pour Identity, identités, requêtes LDAP
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.collection:
- m365-security
- tier3
ms.topic: article
ms.openlocfilehash: 1f5d1d35a673f3ba93f82961353e0fc9c83297d5
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68051759"
---
# <a name="identityqueryevents"></a>IdentityQueryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La `IdentityQueryEvents` table du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les requêtes effectuées sur des objets Active Directory, tels que des utilisateurs, des groupes, des appareils et des domaines. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (`ActionType` valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible dans Defender pour cloud.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `ActionType` | `string` | Type d’activité qui a déclenché l’événement. Pour plus [d’informations, consultez la référence du schéma dans le portail](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) |
| `Application` | `string` | Application qui a effectué l’action enregistrée |
| `QueryType` | `string` | Type de requête, tel que QueryGroup, QueryUser ou EnumerateUsers |
| `QueryTarget` | `string` | Nom de l’utilisateur, du groupe, de l’appareil, du domaine ou de tout autre type d’entité interrogé |
| `Query` | `string` | Chaîne utilisée pour exécuter la requête |
| `Protocol` | `string` | Protocole utilisé pendant la communication |
| `AccountName` | `string` | Nom d’utilisateur du compte |
| `AccountDomain` | `string` | Domaine du compte |
| `AccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte |
| `AccountSid` | `string` | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | `string` | Identificateur unique du compte dans Azure AD |
| `AccountDisplayName` | `string` | Nom de l’utilisateur de compte affiché dans le carnet d’adresses. En règle générale, il s’agit d’une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) du point de terminaison |
| `IPAddress` | `string` | Adresse IP affectée au point de terminaison et utilisée lors des communications réseau associées |
| `Port` | `string` | Port TCP utilisé pendant la communication |
| `DestinationDeviceName` | `string` | Nom de l’appareil exécutant l’application serveur qui a traité l’action enregistrée |
| `DestinationIPAddress` | `string` | Adresse IP de l’appareil exécutant l’application serveur qui a traité l’action enregistrée |
| `DestinationPort` | `string` | Port de destination des communications réseau associées |
| `TargetDeviceName` | `string` | Nom de domaine complet (FQDN) de l’appareil auquel l’action enregistrée a été appliquée |
| `TargetAccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte auquel l’action enregistrée a été appliquée |
| `TargetAccountDisplayName` | `string` | Nom d’affichage du compte auquel l’action enregistrée a été appliquée |
| `Location` | `string` | Ville, pays ou autre emplacement géographique associé à l’événement |
| `ReportId` | `long` | Identificateur unique de l’événement |
| `AdditionalFields` | `string` | Informations supplémentaires sur l’entité ou l’événement |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
