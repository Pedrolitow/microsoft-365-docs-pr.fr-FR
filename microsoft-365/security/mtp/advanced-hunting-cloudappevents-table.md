---
title: Table CloudAppEvents dans le schéma de recherche avancé
description: En savoir plus sur les événements des applications et services cloud dans la table CloudAppEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, CloudAppEvents, Cloud App Security, MCAS
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
ms.openlocfilehash: 021a8210bbe5886021e980b33ade0b9e2ded7b5b
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49928452"
---
# <a name="cloudappevents"></a>CloudAppEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Actuellement disponible en prévisualisation, le tableau du schéma de recherche avancé contient des informations sur les activités dans différentes applications et services cloud, en particulier `CloudAppEvents` Microsoft Teams et Exchange Online. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Ce tableau s’étend pour inclure d’autres activités surveillées par Microsoft Cloud App Security. Finalement, cette table inclut l’activité de fichier actuellement stockée dans la table [AppFileEvents.](advanced-hunting-appfileevents-table.md) Microsoft fournit des conseils supplémentaires à mesure que d’autres données sont déplacer vers ce tableau.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `ActionType` | string | Type d’activité qui a déclenché l’événement |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `ApplicationId` | string | Identificateur unique de l’application |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure Active Directory |
| `AccountDisplayName` | string | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. En règle générale, une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `IsAdminOperation` | string | Indique si l’activité a été effectuée par un administrateur |
| `DeviceType` | string | Type d’appareil en fonction de l’objectif et des fonctionnalités, tels que « Périphérique réseau », « Station de travail », « Serveur », « Mobile », « Console de jeu » ou « Imprimante » | 
| `OSPlatform` | string | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cette colonne indique des systèmes d’exploitation spécifiques, y compris des variantes au sein de la même famille, telles que Windows 10 et Windows 7. |
| `IPAddress` | string | Adresse IP attribuée au point de terminaison et utilisée lors des communications réseau associées |
| `IsAnonymousProxy` | string | Indique si l’adresse IP appartient à un proxy anonyme connu |
| `CountryCode` | string | Code à deux lettres indiquant le pays où l’adresse IP du client est géolocalisé |
| `City` | string | Ville où l’adresse IP du client est géolocalisé |
| `Isp` | string | Fournisseur de services Internet (ISP) associé à l’adresse IP |
| `UserAgent` | string | Informations sur l’agent utilisateur à partir du navigateur web ou d’une autre application cliente |
| `ActivityType` | string | Type d’activité qui a déclenché l’événement |
| `ActivityObjects` | string | Liste des objets, tels que des fichiers ou des dossiers, qui ont été impliqués dans l’activité enregistrée |
| `ObjectName` | string | Nom de l’objet à qui l’action enregistrée a été appliquée |
| `ObjectType` | string | Type d’objet, tel qu’un fichier ou un dossier, à qui l’action enregistrée a été appliquée |
| `ObjectId` | string | Identificateur unique de l’objet à qui l’action enregistrée a été appliquée |
| `ReportId` | string | Identificateur unique de l’événement |
| `RawEventData` | string | Informations d’événement brutes de l’application ou du service source au format JSON |
| `AdditionalFields` | string | Informations supplémentaires sur l’entité ou l’événement |

## <a name="related-topics"></a>Rubriques associées
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
