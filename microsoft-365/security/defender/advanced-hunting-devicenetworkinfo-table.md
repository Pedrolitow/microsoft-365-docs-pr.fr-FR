---
title: Table DeviceNetworkInfo dans le schéma de chasse avancé
description: En savoir plus sur les informations de configuration réseau dans la table DeviceNetworkInfo du schéma de repérage avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, machinenetworkinfo, DeviceNetworkInfo, appareil, machine, mac, ip, adaptateur, dns, dhcp, passerelle, tunnel
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
ms.topic: article
ms.openlocfilehash: 91f6d12619a698028974616ffe6628ea9d4f3116
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68083008"
---
# <a name="devicenetworkinfo"></a>DeviceNetworkInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison



Le `DeviceNetworkInfo` tableau du schéma de [repérage avancé](advanced-hunting-overview.md) contient des informations sur la configuration réseau des machines, notamment les cartes réseau, les adresses IP et MAC, ainsi que les réseaux ou domaines connectés. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `DeviceId` | `string` | Identificateur unique de la machine dans le service |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de la machine |
| `NetworkAdapterName` | `string` | Nom de la carte réseau |
| `MacAddress` | `string` | Adresse MAC de la carte réseau |
| `NetworkAdapterType` | `string` | Type de carte réseau. Pour connaître les valeurs possibles, reportez-vous à [cette énumération](/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `NetworkAdapterStatus` | `string` | État opérationnel de la carte réseau. Pour connaître les valeurs possibles, reportez-vous à [cette énumération](/dotnet/api/system.net.networkinformation.operationalstatus) |
| `TunnelType` | `string` | Protocole de tunneling, si l’interface est utilisée à cet effet, par exemple 6to4, Teredo, ISATAP, PPTP, SSTP et SSH |
| `ConnectedNetworks` | `string` | Réseaux auxquels l’adaptateur est connecté. Chaque tableau JSON contient le nom du réseau, la catégorie (public, privé ou domaine), une description et un indicateur indiquant s’il est connecté publiquement à Internet |
| `DnsAddresses` | `string` | Adresses de serveur DNS au format tableau JSON |
| `IPv4Dhcp` | `string` | Adresse IPv4 du serveur DHCP |
| `IPv6Dhcp` | `string` | Adresse IPv6 du serveur DHCP |
| `DefaultGateways` | `string` | Adresses de passerelle par défaut au format tableau JSON |
| `IPAddresses` | `string` | Tableau JSON contenant toutes les adresses IP affectées à l’adaptateur, ainsi que leur préfixe de sous-réseau et leur espace d’adressage IP respectifs, tels que public, privé ou local de liaison |
| `ReportId` | `long` | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)