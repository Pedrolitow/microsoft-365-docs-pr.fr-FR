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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: b7d880e0865ebeaf09e40fc543abba37566d2081
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61531809"
---
# <a name="identitydirectoryevents"></a>IdentityDirectoryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le tableau du schéma de recherche avancée contient des événements impliquant un contrôleur de domaine local exécutant `IdentityDirectoryEvents` Active Directory [](advanced-hunting-overview.md) (AD). Ce tableau capture différents événements liés à l’identité, tels que les modifications de mot de passe, l’expiration du mot de passe et les modifications de nom d’utilisateur principal (UPN). Il capture également les événements système sur le contrôleur de domaine, tels que la planification des tâches et l’activité PowerShell. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (valeurs) pris en charge par un tableau, utilisez la référence de schéma intégrée disponible dans `ActionType` Defender for Cloud.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `ActionType` | `string` | Type d’activité qui a déclenché l’événement. Pour plus [d’informations, voir](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) la référence du schéma dans le portail |
| `Application` | `string` | Application qui a effectué l’action enregistrée |
| `TargetAccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte à qui l’action enregistrée a été appliquée |
| `TargetAccountDisplayName` | `string` | Nom complet du compte à qui l’action enregistrée a été appliquée |
| `TargetDeviceName` | `string` | Nom de domaine complet (FQDN) de l’appareil à qui l’action enregistrée a été appliquée |
| `DestinationDeviceName` | `string` | Nom de l’appareil exécutant l’application serveur qui a traitée l’action enregistrée |
| `DestinationIPAddress` | `string` | Adresse IP du périphérique exécutant l’application serveur qui a traitée l’action enregistrée |
| `DestinationPort` | `string` | Port de destination de l’activité |
| `Protocol` | `string` | Protocole utilisé pendant la communication |
| `AccountName` | `string` | Nom d’utilisateur du compte |
| `AccountDomain` | `string` | Domaine du compte |
| `AccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte |
| `AccountSid` | `string` | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | `string` | Identificateur unique du compte dans Azure Active Directory |
| `AccountDisplayName` | `string` | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. En règle générale, une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de l’appareil |
| `IPAddress` | `string` | Adresse IP attribuée à l’appareil lors de la communication |
| `Port` | `string` | Port TCP utilisé lors de la communication |
| `Location` | `string` | Ville, pays ou autre emplacement géographique associé à l’événement |
| `ISP` | `string` | Fournisseur de services Internet associé à l’adresse IP |
| `ReportId` | `long` | Identificateur unique de l’événement |
| `AdditionalFields` | `string` | Informations supplémentaires sur l’entité ou l’événement |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
