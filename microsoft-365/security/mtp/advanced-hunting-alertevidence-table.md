---
title: Table AlertEvidence dans le schéma de recherche avancé
description: En savoir plus sur les informations associées aux alertes dans la table AlertEvidence du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, AlertInfo, alert, entities, evidence, file, IP address, device, machine, user, account
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
ms.openlocfilehash: c01b0aae1eff3d9b4add632aff0f13cb56941a30
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49932303"
---
# <a name="alertevidence"></a>AlertEvidence

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le tableau du schéma de recherche avancée contient des informations sur différentes `AlertEvidence` entités (fichiers, adresses IP, URL, utilisateurs ou appareils) associées aux alertes de Microsoft Defender pour endpoint, Microsoft Defender pour Office 365, Microsoft Cloud App Security et Microsoft Defender pour l’identité. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `AlertId` | string | Identificateur unique de l’alerte |
| `ServiceSource` | string | Produit ou service qui a fourni les informations d’alerte |
| `EntityType` | string | Type d’objet, tel qu’un fichier, un processus, un appareil ou un utilisateur |
| `EvidenceRole` | string | Comment l’entité est impliquée dans une alerte, indiquant si elle est concernée ou simplement liée |
| `EvidenceDirection` | string | Indique si l’entité est la source ou la destination d’une connexion réseau |
| `FileName` | string | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | string | Dossier contenant le fichier à lequel l’action enregistrée a été appliquée |
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | string | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli ; utilisez la colonne SHA1 lorsqu’elle est disponible. |
| `FileSize` | int | Taille du fichier en octets |
| `ThreatFamily` | string | Famille de programmes malveillants sous qui le fichier ou processus suspect ou malveillant a été classé |
| `RemoteIP` | string | Adresse IP à laquelle la connexion était en cours |
| `RemoteUrl` | string | URL ou nom de domaine complet (FQDN) à laquelle/auquel la connexion était en cours |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountDomain` | string | Domaine du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure Active Directory |
| `DeviceId` | string | Identificateur unique de l’appareil dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `LocalIP` | string | Adresse IP attribuée à l’appareil local utilisé lors de la communication |
| `NetworkMessageId` | string | Identificateur unique d’e-mail, généré par Office 365 |
| `EmailSubject` | chaîne | Objet de l’e-mail |
| `ApplicationId` | chaîne | Identificateur unique de l’application |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `ProcessCommandLine` | string | Ligne de commande utilisée pour créer le nouveau processus |
| `AdditionalFields` | string | Informations supplémentaires sur l’événement au format de tableau JSON |

## <a name="related-topics"></a>Rubriques associées
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
