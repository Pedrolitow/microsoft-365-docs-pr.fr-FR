---
title: Table AlertEvidence dans le schéma de chasse avancé
description: En savoir plus sur les informations associées aux alertes dans la table AlertEvidence du schéma de chasse avancé
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, AlertInfo, alerte, entités, preuve, fichier, adresse IP, appareil, ordinateur, utilisateur, compte
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.openlocfilehash: 7f6a4f7592e6a8fde0b7ae6269f07ce7f76a5730
ms.sourcegitcommit: de600339b08951d6dd3933288a8da2327a4b6ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48430162"
---
# <a name="alertevidence"></a>AlertEvidence

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

Le `AlertEvidence` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les différentes entités (fichiers, adresses IP, URL, utilisateurs ou périphériques) associées aux alertes de Microsoft Defender atp, Office 365 ATP, Microsoft Cloud App Security et Azure ATP. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `AlertId` | string | Identificateur unique de l’alerte |
| `ServiceSource` | string | Produit ou service qui a fourni les informations d’alerte |
| `EntityType` | string | Type d’objet, tel qu’un fichier, un processus, un périphérique ou un utilisateur |
| `EvidenceRole` | string | La manière dont l’entité est impliquée dans une alerte, indiquant si elle est affectée ou si elle est simplement liée |
| `EvidenceDirection` | string | Indique si l’entité est la source ou la destination d’une connexion réseau. |
| `FileName` | string | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | string | Dossier contenant le fichier auquel l’action enregistrée a été appliquée |
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | string | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli : utilisez la colonne SHA1 quand elle est disponible. |
| `FileSize` | int | Taille du fichier en octets |
| `ThreatFamily` | string | Famille de programmes malveillants dans laquelle le fichier ou le processus suspect ou malveillant a été classé sous |
| `RemoteIP` | string | Adresse IP à laquelle la connexion était en cours |
| `RemoteUrl` | string | URL ou nom de domaine complet (FQDN) à laquelle/auquel la connexion était en cours |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountDomain` | string | Domaine du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure Active Directory |
| `DeviceId` | string | Identificateur unique de l’appareil dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `LocalIP` | string | Adresse IP affectée au périphérique local utilisé pendant la communication |
| `NetworkMessageId` | string | Identificateur unique d’e-mail, généré par Office 365 |
| `EmailSubject` | chaîne | Objet de l’e-mail |
| `ApplicationId` | chaîne | Identificateur unique de l’application |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `ProcessCommandLine` | string | Ligne de commande utilisée pour créer le nouveau processus |
| `AdditionalFields` | string | Informations supplémentaires sur l’événement au format de tableau JSON |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les emails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
