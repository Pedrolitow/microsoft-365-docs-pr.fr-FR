---
title: Table DeviceNetworkInfo dans le schéma de chasse avancé
description: En savoir plus sur les informations de configuration réseau dans la table DeviceNetworkInfo du schéma de chasse avancé
keywords: chasse aux menaces, recherche de menace, recherche sur les menaces de la cybercriminalité, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, machinenetworkinfo, DeviceNetworkInfo, appareil, ordinateur, Mac, IP, adaptateur, DNS, DHCP, passerelle, tunnel
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
ms.openlocfilehash: 25349328cd128113de7846cba5c7c9ad74631092
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41600411"
---
# <a name="devicenetworkinfo"></a>DeviceNetworkInfo

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le `DeviceNetworkInfo` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur la configuration réseau des ordinateurs, y compris les cartes réseau, les adresses IP et Mac, ainsi que les réseaux ou domaines connectés. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | chaîne | Identificateur unique de la machine dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et timestamp |
| `NetworkAdapterName` | string | Nom de la carte réseau |
| `MacAddress` | string | Adresse MAC de la carte réseau |
| `NetworkAdapterType` | string | Type de carte réseau. Pour les valeurs possibles, reportez-vous à [cette énumération](https://docs.microsoft.com/dotnet/api/system.net.networkinformation.networkinterfacetype?view=netframework-4.7.2) |
| `NetworkAdapterStatus` | string | État opérationnel de la carte réseau. Pour les valeurs possibles, reportez-vous à [cette énumération](https://docs.microsoft.com/dotnet/api/system.net.networkinformation.operationalstatus?view=netframework-4.7.2) |
| `TunnelType` | string | Protocole de tunneling, si l’interface est utilisée à cet effet, par exemple 6to4, Teredo, ISATAP, PPTP, SSTP et SSH |
| `ConnectedNetworks` | string | Réseaux auxquels la carte est connectée. Chaque tableau JSON contient le nom de réseau, la catégorie (public, Private ou Domain), une description et un indicateur qui indique s’il est connecté publiquement à Internet. |
| `DnsAddresses` | string | Adresses de serveur DNS au format de tableau JSON |
| `IPv4Dhcp` | string | Adresse IPv4 du serveur DHCP |
| `IPv6Dhcp` | string | Adresse IPv6 du serveur DHCP |
| `DefaultGateways` | string | Adresses de passerelle par défaut au format de tableau JSON |
| `IPAddresses` | string | Tableau JSON contenant toutes les adresses IP affectées à la carte, ainsi que le préfixe de sous-réseau respectif et l’espace d’adressage IP, tels que public, Private ou Link-local. |

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
