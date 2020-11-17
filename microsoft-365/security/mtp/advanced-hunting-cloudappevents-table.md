---
title: Table CloudAppEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements des applications et services Cloud dans le tableau CloudAppEvents du schéma de chasse avancé
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, CloudAppEvents, sécurité des applications Cloud, MCAS
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
ms.openlocfilehash: 3cb4498e5db6a7752e99b8c677bc8936d2c975ef
ms.sourcegitcommit: e7bf23df4852b78912229d1d38ec475223597f34
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "49087765"
---
# <a name="cloudappevents"></a>CloudAppEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Actuellement disponible en aperçu, le `CloudAppEvents` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les activités dans les différents services et applications Cloud, en particulier Microsoft teams et Exchange Online. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Cette table s’étendra pour inclure plus d’activités surveillées par la sécurité des applications Cloud de Microsoft. Cette table inclut finalement l’activité de fichier actuellement stockée dans la table [AppFileEvents](advanced-hunting-appfileevents-table.md) . Microsoft fournira des conseils supplémentaires au fur et à mesure que des données seront déplacées vers ce tableau.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `ActionType` | string | Type d’activité qui a déclenché l’événement |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `ApplicationId` | string | Identificateur unique de l’application |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure Active Directory |
| `AccountDisplayName` | string | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. Il s’agit généralement d’une combinaison d’un nom donné, d’une initiation au milieu et d’un nom de famille ou nom. |
| `IsAdminOperation` | string | Indique si l’activité a été effectuée par un administrateur. |
| `DeviceType` | string | Type d’appareil basé sur l’objectif et les fonctionnalités, tels que « périphérique réseau », « station de travail », « serveur », « mobile », « console de jeu » ou « imprimante » | 
| `OSPlatform` | string | Plateforme du système d’exploitation s’exécutant sur l’appareil. Cette colonne indique les systèmes d’exploitation spécifiques, y compris les variantes au sein de la même famille, telles que Windows 10 et Windows 7. |
| `IPAddress` | string | Adresse IP affectée au point de terminaison et utilisée pendant les communications réseau associées |
| `IsAnonymousProxy` | string | Indique si l’adresse IP appartient à un proxy anonyme connu. |
| `CountryCode` | string | Code à deux lettres indiquant le pays où se trouve l’adresse IP du client |
| `City` | string | Ville où se trouve l’adresse IP du client |
| `Isp` | string | Fournisseur de services Internet (ISP) associé à l’adresse IP |
| `UserAgent` | string | Informations de l’agent utilisateur à partir du navigateur Web ou d’une autre application cliente |
| `ActivityType` | string | Type d’activité qui a déclenché l’événement |
| `ActivityObjects` | string | Liste d’objets, tels que des fichiers ou des dossiers, qui ont été impliqués dans l’activité enregistrée |
| `ObjectName` | string | Nom de l’objet auquel l’action enregistrée a été appliquée. |
| `ObjectType` | string | Type d’objet, tel qu’un fichier ou un dossier, auquel l’action enregistrée a été appliquée |
| `ObjectId` | string | Identificateur unique de l’objet auquel l’action enregistrée a été appliquée. |
| `ReportId` | string | Identificateur unique de l’événement |
| `RawEventData` | string | Informations d’événements brutes à partir de l’application ou du service source au format JSON |
| `AdditionalFields` | string | Informations supplémentaires sur l’entité ou l’événement |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
