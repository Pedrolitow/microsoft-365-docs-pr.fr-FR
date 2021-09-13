---
title: Table IdentityDirectoryEvents dans le schéma de recherche avancé
description: En savoir plus sur le contrôleur de domaine et les événements Active Directory dans la table IdentityDirectoryEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, IdentityDirectoryEvents, domain controller, Active Directory, Microsoft Defender for Identity, identities
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: b42ff09f1e363f115ecc06c361c8386b328b0bcb
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59163658"
---
# <a name="identitydirectoryevents"></a>IdentityDirectoryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le tableau du schéma de recherche avancée contient des événements impliquant un contrôleur de domaine local exécutant `IdentityDirectoryEvents` Active Directory [](advanced-hunting-overview.md) (AD). Ce tableau capture différents événements liés à l’identité, tels que les modifications de mot de passe, l’expiration du mot de passe et les modifications de nom d’utilisateur principal (UPN). Il capture également les événements système sur le contrôleur de domaine, tels que la planification des tâches et l’activité PowerShell. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible `ActionType` dans le centre de sécurité.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `ActionType` | chaîne | Type d’activité qui a déclenché l’événement. Pour plus [d’informations, voir](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) la référence du schéma dans le portail |
| `Application` | chaîne | Application qui a effectué l’action enregistrée |
| `TargetAccountUpn` | chaîne | Nom d’utilisateur principal (UPN) du compte à qui l’action enregistrée a été appliquée |
| `TargetAccountDisplayName` | chaîne | Nom complet du compte à qui l’action enregistrée a été appliquée |
| `TargetDeviceName` | chaîne | Nom de domaine complet (FQDN) de l’appareil à qui l’action enregistrée a été appliquée |
| `DestinationDeviceName` | chaîne | Nom de l’appareil exécutant l’application serveur qui a traitée l’action enregistrée |
| `DestinationIPAddress` | chaîne | Adresse IP de l’appareil exécutant l’application serveur qui a traitée l’action enregistrée |
| `DestinationPort` | chaîne | Port de destination de l’activité |
| `Protocol` | chaîne | Protocole utilisé pendant la communication |
| `AccountName` | chaîne | Nom d’utilisateur du compte |
| `AccountDomain` | chaîne | Domaine du compte |
| `AccountUpn` | chaîne | Nom d’utilisateur principal (UPN) du compte |
| `AccountSid` | chaîne | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | chaîne | Identificateur unique du compte dans Azure Active Directory |
| `AccountDisplayName` | chaîne | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. En règle générale, une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `DeviceName` | chaîne | Nom de domaine complet (FQDN) de l’appareil |
| `IPAddress` | chaîne | Adresse IP attribuée à l’appareil lors de la communication |
| `Port` | chaîne | Port TCP utilisé pendant la communication |
| `Location` | chaîne | Ville, pays ou autre emplacement géographique associé à l’événement |
| `ISP` | chaîne | Fournisseur de services Internet associé à l’adresse IP |
| `ReportId` | long | Identificateur unique de l’événement |
| `AdditionalFields` | chaîne | Informations supplémentaires sur l’entité ou l’événement |

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
