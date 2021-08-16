---
title: Table DeviceNetworkInfo dans le schéma de recherche avancé
description: En savoir plus sur les informations de configuration réseau dans le tableau DeviceNetworkInfo du schéma de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, machinenetworkinfo, DeviceNetworkInfo, device, machine, mac, ip, adapter, dns, dhcp, gateway, tunnel
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 478ea1b605c4aeda5b1a6b5aec26b6abb57723ff7f82e5684a42af742afee3d2
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53863462"
---
# <a name="devicenetworkinfo"></a>DeviceNetworkInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison



Le tableau du schéma de recherche avancé contient des informations sur la configuration réseau des ordinateurs, notamment les cartes réseau, les adresses IP et MAC, ainsi que les réseaux ou `DeviceNetworkInfo` domaines connectés. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | string | Identificateur unique de la machine dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `NetworkAdapterName` | string | Nom de la carte réseau |
| `MacAddress` | string | Adresse MAC de la carte réseau |
| `NetworkAdapterType` | string | Type de carte réseau. Pour les valeurs possibles, reportez-vous [à cette éumération](/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `NetworkAdapterStatus` | string | État opérationnel de la carte réseau. Pour les valeurs possibles, reportez-vous [à cette éumération](/dotnet/api/system.net.networkinformation.operationalstatus) |
| `TunnelType` | string | Protocole tunneling, si l’interface est utilisée à cet effet, par exemple 6to4, Teredo, ISATAP, PPTP, SSTP et SSH |
| `ConnectedNetworks` | string | Réseaux connectés à l’adaptateur. Chaque tableau JSON contient le nom du réseau, la catégorie (public, privé ou domaine), une description et un indicateur indiquant s’il est connecté publiquement à Internet |
| `DnsAddresses` | string | Adresses de serveur DNS au format de tableau JSON |
| `IPv4Dhcp` | string | Adresse IPv4 du serveur DHCP |
| `IPv6Dhcp` | string | Adresse IPv6 du serveur DHCP |
| `DefaultGateways` | string | Adresses de passerelle par défaut au format de tableau JSON |
| `IPAddresses` | string | Tableau JSON contenant toutes les adresses IP affectées à l’adaptateur, ainsi que leur préfixe de sous-réseau et espace d’adressace IP respectifs, tels que public, privé ou liaison locale |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp |

## <a name="related-topics"></a>Sujets connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)