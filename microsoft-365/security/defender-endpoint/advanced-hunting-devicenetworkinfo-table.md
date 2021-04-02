---
title: Table DeviceNetworkInfo dans le schéma de recherche avancé
description: En savoir plus sur les informations de configuration réseau dans le tableau DeviceNetworkInfo du schéma de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, search, query, telemetry, schema reference, kusto, table, column, data type, description, devicenetworkinfo, device, device, device, mac, ip, adapter, dns, dhcp, gateway, tunnel, DeviceNetworkInfo
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: e63af4153804a09424c36fb03ac715da5f6d9485
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51499136"
---
# <a name="devicenetworkinfo"></a>DeviceNetworkInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

Le tableau du schéma de recherche avancé contient des informations sur la configuration réseau des appareils, notamment les cartes réseau, les adresses IP et MAC, ainsi que les réseaux ou `DeviceNetworkInfo` domaines connectés. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tableaux du schéma de chasse avancé, voir [la référence du schéma de chasse avancé.](advanced-hunting-schema-reference.md)

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | string | Identificateur unique de l’appareil dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de l’appareil |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les `DeviceName` colonnes et les `Timestamp` événements |
| `NetworkAdapterName` | string | Nom de la carte réseau |
| `MacAddress` | string | Adresse MAC de la carte réseau |
| `NetworkAdapterType` | string | Type de carte réseau. Pour les valeurs possibles, reportez-vous [à cette éumération](https://docs.microsoft.com/dotnet/api/system.net.networkinformation.networkinterfacetype?view=netframework-4.7.2&preserve-view=true) |
| `NetworkAdapterStatus` | string | État opérationnel de la carte réseau. Pour les valeurs possibles, reportez-vous [à cette éumération](https://docs.microsoft.com/dotnet/api/system.net.networkinformation.operationalstatus?view=netframework-4.7.2&preserve-view=true) |
| `TunnelType` | string | Protocole tunneling, si l’interface est utilisée à cet effet, par exemple 6to4, Teredo, ISATAP, PPTP, SSTP et SSH |
| `ConnectedNetworks` | string | Réseaux connectés à l’adaptateur. Chaque tableau JSON contient le nom du réseau, la catégorie (public, privé ou domaine), une description et un indicateur indiquant s’il est connecté publiquement à Internet |
| `DnsAddresses` | string | Adresses de serveur DNS au format de tableau JSON |
| `IPv4Dhcp` | string | Adresse IPv4 du serveur DHCP |
| `IPv6Dhcp` | string | Adresse IPv6 du serveur DHCP |
| `DefaultGateways` | string | Adresses de passerelle par défaut au format de tableau JSON |
| `IPAddresses` | string | Tableau JSON contenant toutes les adresses IP affectées à l’adaptateur, ainsi que leur préfixe de sous-réseau et espace d’adressace IP respectifs, tels que public, privé ou liaison locale |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
