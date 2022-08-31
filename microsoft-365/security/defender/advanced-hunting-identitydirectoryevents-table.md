---
title: Table IdentityDirectoryEvents dans le schéma de chasse avancé
description: En savoir plus sur le contrôleur de domaine et les événements Active Directory dans la table IdentityDirectoryEvents du schéma de chasse avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, IdentityDirectoryEvents, contrôleur de domaine, Active Directory, Microsoft Defender pour Identity, identités
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
ms.collection: m365-security-compliance
ms.topic: article
ms.openlocfilehash: 9665ff301396d9b3c4f31ed51f17ffbd45f06113
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67481303"
---
# <a name="identitydirectoryevents"></a>IdentityDirectoryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La `IdentityDirectoryEvents` table du schéma de [chasse avancé](advanced-hunting-overview.md) contient des événements impliquant un contrôleur de domaine local exécutant Active Directory (AD). Ce tableau capture différents événements liés à l’identité, tels que les modifications de mot de passe, l’expiration du mot de passe et les modifications de nom d’utilisateur principal (UPN). Il capture également les événements système sur le contrôleur de domaine, tels que la planification des tâches et l’activité PowerShell. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (`ActionType` valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible dans Defender pour cloud.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `ActionType` | `string` | Type d’activité qui a déclenché l’événement. Pour plus [d’informations, consultez la référence du schéma dans le portail](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) |
| `Application` | `string` | Application qui a effectué l’action enregistrée |
| `TargetAccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte auquel l’action enregistrée a été appliquée |
| `TargetAccountDisplayName` | `string` | Nom d’affichage du compte auquel l’action enregistrée a été appliquée |
| `TargetDeviceName` | `string` | Nom de domaine complet (FQDN) de l’appareil auquel l’action enregistrée a été appliquée |
| `DestinationDeviceName` | `string` | Nom de l’appareil exécutant l’application serveur qui a traité l’action enregistrée |
| `DestinationIPAddress` | `string` | Adresse IP de l’appareil exécutant l’application serveur qui a traité l’action enregistrée |
| `DestinationPort` | `string` | Port de destination de l’activité |
| `Protocol` | `string` | Protocole utilisé pendant la communication |
| `AccountName` | `string` | Nom d’utilisateur du compte |
| `AccountDomain` | `string` | Domaine du compte |
| `AccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte |
| `AccountSid` | `string` | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | `string` | Identificateur unique du compte dans Azure Active Directory |
| `AccountDisplayName` | `string` | Nom de l’utilisateur de compte affiché dans le carnet d’adresses. En règle générale, il s’agit d’une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de l’appareil |
| `IPAddress` | `string` | Adresse IP affectée à l’appareil pendant la communication |
| `Port` | `string` | Port TCP utilisé pendant la communication |
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
