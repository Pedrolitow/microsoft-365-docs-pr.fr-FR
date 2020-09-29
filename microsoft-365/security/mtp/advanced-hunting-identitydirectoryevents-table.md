---
title: Table IdentityDirectoryEvents dans le schéma de chasse avancé
description: En savoir plus sur le contrôleur de domaine et les événements Active Directory dans la table IdentityDirectoryEvents du schéma de chasse avancé
keywords: recherche avancée, recherche de menace, recherche de menace informatique, protection de Microsoft contre les menaces, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, IdentityDirectoryEvents, contrôleur de domaine, Active Directory, Azure ATP, identités
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
ms.openlocfilehash: 118d96b797e9d46b4a9912f919cafbba680a9609
ms.sourcegitcommit: 888b9355ef7b933c55ca6c18639c12426ff3fbde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "48305281"
---
# <a name="identitydirectoryevents"></a>IdentityDirectoryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

Le `IdentityDirectoryEvents` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des événements impliquant un contrôleur de domaine local exécutant Active Directory (AD). Ce tableau capture différents événements liés à l’identité, tels que les modifications de mot de passe, l’expiration du mot de passe et les modifications de nom d’utilisateur principal (UPN). Il capture également les événements système sur le contrôleur de domaine, comme la planification des tâches et l’activité PowerShell. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements ( `ActionType` valeurs) pris en charge par un tableau, utilisez la [référence de schéma intégrée](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) disponible dans le centre de sécurité.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `ActionType` | string | Type d’activité qui a déclenché l’événement. Pour plus d’informations, consultez la [référence de schéma dans le portail](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) . |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `TargetAccountUpn` | string | Nom d’utilisateur principal (UPN) du compte auquel l’action enregistrée a été appliquée |
| `TargetAccountDisplayName` | string | Nom d’affichage du compte auquel l’action enregistrée a été appliquée |
| `TargetDeviceName` | string | Nom de domaine complet (FQDN) de l’appareil sur lequel l’action enregistrée a été appliquée. |
| `DestinationDeviceName` | string | Nom de l’appareil exécutant l’application serveur qui a traité l’action enregistrée. |
| `DestinationIPAddress` | string | Adresse IP de l’appareil exécutant l’application serveur qui a traité l’action enregistrée |
| `DestinationPort` | string | Port de destination de l’activité |
| `Protocol` | string | Protocole utilisé pendant la communication |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountDomain` | string | Domaine du compte |
| `AccountUpn` | string | Nom d’utilisateur principal (UPN) du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure Active Directory |
| `AccountDisplayName` | string | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. Il s’agit généralement d’une combinaison d’un nom donné, d’une initiation au milieu et d’un nom de famille ou nom. |
| `DeviceName` | string | Nom de domaine complet (FQDN) du périphérique |
| `IPAddress` | string | Adresse IP attribuée au périphérique lors de la communication |
| `Port` | string | Port TCP utilisé pendant la communication |
| `Location` | string | Ville, pays ou autre emplacement géographique associé à l’événement |
| `ISP` | string | Fournisseur de services Internet associé à l’adresse IP |
| `ReportId` | long | Identificateur unique de l’événement |
| `AdditionalFields` | string | Informations supplémentaires sur l’entité ou l’événement |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les emails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
