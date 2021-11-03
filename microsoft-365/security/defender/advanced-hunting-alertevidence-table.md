---
title: Table AlertEvidence dans le schéma de recherche avancé
description: En savoir plus sur les informations associées aux alertes dans la table AlertEvidence du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, AlertInfo, alert, entities, evidence, file, IP address, device, machine, user, account
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
ms.openlocfilehash: 2edd6bf9f713ea93c2bddcbca39acd333293718a
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60700348"
---
# <a name="alertevidence"></a>AlertEvidence

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le tableau du schéma de recherche avancée contient des informations sur différentes `AlertEvidence` entités (fichiers, adresses IP, URL, utilisateurs ou appareils) associées aux alertes de Microsoft Defender pour point de terminaison, Microsoft Defender pour [](advanced-hunting-overview.md) Office 365, Microsoft Cloud App Security et Microsoft Defender pour l’identité. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `AlertId` | string | Identificateur unique de l’alerte |
| `ServiceSource` | chaîne | Produit ou service qui a fourni les informations d’alerte |
| `EntityType` | chaîne | Type d’objet, tel qu’un fichier, un processus, un appareil ou un utilisateur |
| `EvidenceRole` | chaîne | Comment l’entité est impliquée dans une alerte, indiquant si elle est concernée ou simplement liée |
| `EvidenceDirection` | chaîne | Indique si l’entité est la source ou la destination d’une connexion réseau |
| `FileName` | string | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | string | Dossier contenant le fichier à lequel l’action enregistrée a été appliquée |
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | string | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli ; utilisez la colonne SHA1 lorsqu’elle est disponible. |
| `FileSize` | int | Taille du fichier en octets |
| `ThreatFamily` | chaîne | Famille de programmes malveillants sous qui le fichier ou processus suspect ou malveillant a été classé |
| `RemoteIP` | string | Adresse IP à laquelle la connexion était en cours |
| `RemoteUrl` | string | URL ou nom de domaine complet (FQDN) à laquelle/auquel la connexion était en cours |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountDomain` | chaîne | Domaine du compte |
| `AccountSid` | chaîne | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | chaîne | Identificateur unique du compte dans Azure Active Directory |
| `AccountUpn` | chaîne | Nom d’utilisateur principal (UPN) du compte |
| `DeviceId` | chaîne | Identificateur unique de l’appareil dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `LocalIP` | string | Adresse IP attribuée à l’appareil local utilisé lors de la communication |
| `NetworkMessageId` | chaîne | Identificateur unique d’e-mail, généré par Office 365 |
| `EmailSubject` | chaîne | Objet de l’e-mail |
| `ApplicationId` | chaîne | Identificateur unique de l’application |
| `Application` | chaîne | Application qui a effectué l’action enregistrée |
| `ProcessCommandLine` | chaîne | Ligne de commande utilisée pour créer le nouveau processus |
| `AdditionalFields` | chaîne | Informations supplémentaires sur l’événement au format de tableau JSON |
| `RegistryKey` |chaîne | Clé de Registre à qui l’action enregistrée a été appliquée |
| `RegistryValueName` |chaîne | Nom de la valeur de Registre à qui l’action enregistrée a été appliquée |
| `RegistryValueData` |chaîne | Données de la valeur de Registre à l’application de l’action enregistrée |

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
