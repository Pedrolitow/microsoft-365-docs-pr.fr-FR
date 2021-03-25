---
title: Table DeviceInfo dans le schéma de recherche avancée
description: En savoir plus sur le système d’exploitation, le nom de l’ordinateur et d’autres informations sur l’appareil dans la table DeviceInfo du schéma de recherche avancée
keywords: recherche avancée, recherche de cybermenace, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, deviceinfo, appareil, système d’exploitation, plateforme, utilisateurs, DeviceInfo
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: e86cba39663e96beffc00aa94d6cbcdf7a6e1e42
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51067065"
---
# <a name="deviceinfo"></a>DeviceInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)


>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

Le tableau du schéma de recherche avancée contient des informations sur les appareils de l’organisation, notamment leur version du système d’exploitation, les utilisateurs `DeviceInfo` actifs et le nom de l’ordinateur. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tableaux du schéma de chasse avancé, voir [la référence du schéma de chasse avancé.](advanced-hunting-schema-reference.md)

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | string | Identificateur unique de l’appareil dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de l’appareil |
| `ClientVersion` | string | Version de l’agent de point de terminaison ou du capteur en cours d’exécution sur l’appareil |
| `PublicIP` | string | Adresse IP publique utilisée par l’appareil intégré pour se connecter au service Defender for Endpoint. Il peut s’agit de l’adresse IP de l’appareil lui-même, d’un périphérique NAT ou d’un proxy. |
| `OSArchitecture` | string | Architecture du système d’exploitation en cours d’exécution sur l’appareil |
| `OSPlatform` | string | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein de la même famille, tels que Windows 10 et Windows 7 |
| `OSBuild` | string | Version de build du système d’exploitation en cours d’exécution sur l’appareil |
| `IsAzureADJoined` | booléen | Indicateur booléen pour savoir si l’appareil est joint à Azure Active Directory |
| `LoggedOnUsers` | string | Liste de tous les utilisateurs connectés à l’appareil au moment de l’événement au format de tableau JSON |
| `RegistryDeviceTag` | string | Balise d’appareil ajoutée via le Registre |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp |
| `OSVersion` | string | Version du système d’exploitation en cours d’exécution sur l’appareil |
| `MachineGroup` | string | Groupe d’ordinateurs de l’ordinateur. Ce groupe est utilisé par le contrôle d’accès basé sur un rôle pour déterminer l’accès à l’ordinateur |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
