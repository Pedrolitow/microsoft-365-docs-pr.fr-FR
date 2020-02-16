---
title: Table DeviceInfo dans le schéma de chasse avancé
description: En savoir plus sur le système d’exploitation, le nom de l’ordinateur et d’autres informations sur l’ordinateur dans le tableau DeviceInfo du schéma de chasse avancé
keywords: chasse avancée, recherche de menace, recherche dans les menaces de la cybercriminalité, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, MachineInfo, DeviceInfo, appareil, ordinateur, se, plateforme , les utilisateurs
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
ms.openlocfilehash: 58fd70ce62fc2e15f703063d1f8efe62df02c57d
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42087973"
---
# <a name="deviceinfo"></a>DeviceInfo

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le `DeviceInfo` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les ordinateurs de l’organisation, y compris la version du système d’exploitation, les utilisateurs actifs et le nom de l’ordinateur. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | chaîne | Identificateur unique de la machine dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `ClientVersion` | string | Version de l’agent de point de terminaison ou du capteur exécuté sur l’ordinateur |
| `PublicIP` | string | Adresse IP publique utilisée par l’ordinateur intégré pour se connecter au service ATP de Microsoft Defender. Il peut s’agir de l’adresse IP de l’ordinateur lui-même, d’un périphérique NAT ou d’un proxy. |
| `OSArchitecture` | string | Architecture du système d’exploitation s’exécutant sur la machine |
| `OSPlatform` | string | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique les systèmes d’exploitation spécifiques, y compris les variantes au sein de la même famille, telles que Windows 10 et Windows 7 |
| `OSBuild` | string | Version du système d’exploitation en cours d’exécution sur l’ordinateur |
| `IsAzureADJoined` | booléen | Indicateur booléen indiquant si l’ordinateur est joint à Azure Active Directory |
| `LoggedOnUsers` | string | Liste de tous les utilisateurs qui ont ouvert une session sur l’ordinateur au moment de l’événement au format de tableau JSON |
| `RegistryDeviceTag` | string | Balise d’ordinateur ajoutée via le registre |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et timestamp |
| `OSVersion` | string | Version du système d’exploitation s’exécutant sur la machine |
| `MachineGroup` | string | Groupe d’ordinateurs de l’ordinateur. Ce groupe est utilisé par le contrôle d’accès basé sur un rôle pour déterminer l’accès à l’ordinateur. |

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
