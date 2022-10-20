---
title: Table AlertEvidence dans le schéma de chasse avancé
description: En savoir plus sur les informations associées aux alertes dans la table AlertEvidence du schéma de chasse avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, AlertInfo, alerte, entités, preuve, fichier, adresse IP, appareil, machine, utilisateur, compte
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
ms.topic: conceptual
ms.openlocfilehash: 731d72ff5e42b85a5ddc68ed58e8914e142cea9f
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68636977"
---
# <a name="alertevidence"></a>AlertEvidence

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le `AlertEvidence` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les différentes entités (fichiers, adresses IP, URL, utilisateurs ou appareils) associées aux alertes de Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender for Cloud Apps et Microsoft Defender pour Identity. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `AlertId` | `string` | Identificateur unique de l’alerte |
| `ServiceSource` | `string` | Produit ou service qui a fourni les informations d’alerte |
| `EntityType` | `string` | Type d’objet, tel qu’un fichier, un processus, un appareil ou un utilisateur |
| `EvidenceRole` | `string` | Comment l’entité est impliquée dans une alerte, indiquant si elle est impactée ou simplement liée |
| `EvidenceDirection` | `string` | Indique si l’entité est la source ou la destination d’une connexion réseau |
| `FileName` | `string` | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | `string` | Dossier contenant le fichier auquel l’action enregistrée a été appliquée |
| `SHA1` | `string` | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | `string` | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli : utilisez la colonne SHA1 lorsqu’elle est disponible. |
| `FileSize` | `int` | Taille du fichier en octets |
| `ThreatFamily` | `string` | Famille de programmes malveillants sous laquelle le fichier ou processus suspect ou malveillant a été classé sous |
| `RemoteIP` | `string` | Adresse IP à laquelle la connexion était en cours |
| `RemoteUrl` | `string` | URL ou nom de domaine complet (FQDN) à laquelle/auquel la connexion était en cours |
| `AccountName` | `string` | Nom d’utilisateur du compte |
| `AccountDomain` | `string` | Domaine du compte |
| `AccountSid` | `string` | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | `string` | Identificateur unique du compte dans Azure Active Directory |
| `AccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte |
| `DeviceId` | `string` | Identificateur unique de l’appareil dans le service |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de la machine |
| `LocalIP` | `string` | Adresse IP affectée à l’appareil local utilisé pendant la communication |
| `NetworkMessageId` | `string` | Identificateur unique d’e-mail, généré par Office 365 |
| `EmailSubject` | `string` | Objet de l’e-mail |
| `ApplicationId` | `string` | Identificateur unique de l’application |
| `Application` | `string` | Application qui a effectué l’action enregistrée |
| `ProcessCommandLine` | `string` | Ligne de commande utilisée pour créer le nouveau processus |
| `AdditionalFields` | `string` | Informations supplémentaires sur l’événement au format tableau JSON |
| `RegistryKey` |`string` | Clé de Registre à laquelle l’action enregistrée a été appliquée |
| `RegistryValueName` |`string` | Nom de la valeur de Registre à laquelle l’action enregistrée a été appliquée |
| `RegistryValueData` |`string` | Données de la valeur de Registre à laquelle l’action enregistrée a été appliquée |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
