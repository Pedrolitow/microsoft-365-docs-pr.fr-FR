---
title: Table AlertEvidence dans le schéma de chasse avancé
description: Découvrez les informations relatives aux fichiers, aux adresses réseau, aux utilisateurs ou aux appareils associés à des alertes générées dans la table AlertEvidence du schéma de chasse avancé.
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
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: a0f2ae36752a4415da7c1bc39ce35bd7f744a764
ms.sourcegitcommit: ab10c042e5e9c6a7b2afef930ab0d247a6aa275d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "44899350"
---
# <a name="alertevidence"></a>AlertEvidence

**S’applique à :**
- Protection Microsoft contre les menaces

Le `AlertEvidence` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les différentes entités (fichiers, adresses IP, URL, utilisateurs ou périphériques) associées aux alertes de Microsoft Defender atp, Office 365 ATP, Microsoft Cloud App Security et Azure ATP. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `AlertId` | chaîne | Identificateur unique de l’alerte |
| `EntityType` | string | Type d’objet, tel qu’un fichier, un processus, un périphérique ou un utilisateur |
| `EvidenceRole` | string | La manière dont l’entité est impliquée dans une alerte, indiquant si elle est affectée ou si elle est simplement liée |
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | string | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `RemoteIP` | string | Adresse IP à laquelle la connexion était en cours |
| `RemoteUrl` | string | URL ou nom de domaine complet (FQDN) à laquelle/auquel la connexion était en cours |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountDomain` | string | Domaine du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure AD |
| `DeviceId` | string | Identificateur unique de la machine dans le service |
| `ThreatFamily` | string | Famille de programmes malveillants dans laquelle le fichier ou le processus suspect ou malveillant a été classé sous |
| `EvidenceDirection` | string | Indique si l’entité est la source ou la destination d’une connexion réseau. |
| `AdditionalFields` | string | Informations supplémentaires sur l’événement au format de tableau JSON |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
